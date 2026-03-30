# Module 1: Infrastructure — Cài đặt & Bảo mật

> **Đối tượng**: Admin only
> **Thời lượng**: 3-4 giờ
> **Prerequisite**: Có Mac mini hoặc máy macOS/Linux chạy 24/7

---

## 1.1 Cài đặt OpenClaw

Làm theo quick-start chính thức. Các bước chính:

```bash
# Cài Homebrew (nếu chưa có)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Cài OpenClaw
brew install openclaw

# Khởi tạo
openclaw init

# Khởi động gateway
openclaw gateway start
```

Sau khi cài xong, tạo Telegram bot qua @BotFather và kết nối vào `openclaw.json`.

### Lưu ý thực tế
- **Luôn dùng** `eval "$(/opt/homebrew/bin/brew shellenv)" && openclaw gateway restart` sau khi sửa `openclaw.json` — không phải chỉ `openclaw gateway restart`
- Gateway chạy nền — nếu máy reboot, cần start lại (hoặc setup launchd/systemd)

---

## 1.2 Quản lý API Key

### Các key cần có
| Key | Dùng cho | Chi phí |
|-----|----------|---------|
| `ANTHROPIC_API_KEY` | Claude models (chính) | Pay-per-use |
| `OPENROUTER_API_KEY` | Gemini, Kimi (rẻ hơn cho task đơn giản) | Pay-per-use |
| Telegram Bot Token | Kênh chat với agent | Miễn phí |

### Nguyên tắc bảo mật — BẮT BUỘC
1. **Không bao giờ commit API key lên Git** — dùng `.gitignore` nghiêm ngặt
2. **Backup phải redact key** trước khi lưu vào repo:
   ```bash
   # backup.sh đã có logic tự redact — luôn chạy qua script, không copy thủ công
   ./backup.sh
   ```
3. **Sau mỗi lần backup**, chạy security scan:
   ```bash
   grep -r "sk-ant\|sk-or\|REDACTED" configs_backup/openclaw.json
   # Tất cả key phải hiện "REDACTED"
   ```
4. Nếu lỡ commit key → rotate key ngay, không chỉ xóa commit

### Bài học từ thực tế
`backup.sh` ban đầu chỉ redact `ANTHROPIC_API_KEY`, bỏ sót `OPENROUTER_API_KEY` và `ZAI_API_KEY`. Key bị lộ mỗi lần backup. Fix: dùng `jq with_entries` để redact **tất cả** key trong `.env` theo pattern `KEY|TOKEN|SECRET|PASSWORD`.

---

## 1.3 Cấu trúc File Quan Trọng

```
~/.openclaw/
├── openclaw.json              ← Config tổng (model, API key, agents, cron)
├── cron/jobs.json             ← Cấu hình cron jobs
├── common-scripts/            ← Scripts dùng chung cho mọi agent
│   ├── facebook/
│   │   ├── fb-group-monitor.py
│   │   └── fb-group-monitor.sh
│   └── ...
└── workspace-<agent-name>/   ← Workspace riêng từng agent
    ├── SOUL.md                ← Personality + rules của agent
    ├── TOOLS.md               ← Danh sách tools agent có thể dùng
    ├── skills/                ← SKILL.md cho từng tool
    └── sessions/              ← Log hội thoại (không backup)
```

### Convention BẮT BUỘC
- **Scripts** → đặt trong `~/.openclaw/common-scripts/<category>/`
- **Không tạo script trong workspace agent** — workspace chỉ chứa config, notes, drafts

---

## 1.4 Backup Định Kỳ

```bash
# Chạy từ repo openclaw-knowledge
cd ~/kioku-workspace/openclaw-knowledge
./backup.sh
```

Script sẽ:
1. Redact tất cả API key trong `openclaw.json`
2. Rsync toàn bộ config (trừ sessions, credentials) vào `configs_backup/`
3. Sau đó commit + push lên Git để lưu lịch sử

**Tần suất khuyến nghị**: Mỗi khi có thay đổi cấu hình lớn, hoặc ít nhất 1 lần/tuần.

---

## 1.5 Các Lệnh Admin Thường Dùng

```bash
# Xem trạng thái gateway
openclaw gateway status

# Restart gateway (áp dụng config mới hoặc khi agent treo)
eval "$(/opt/homebrew/bin/brew shellenv)" && openclaw gateway restart

# Xem log lỗi real-time
tail -f ~/.openclaw/gateway.err.log

# Xem session log của agent (để debug)
tail -n 100 ~/.openclaw/agents/<agent-id>/sessions/<session-id>.jsonl | \
  python3 -c "import sys,json; [print(json.dumps(json.loads(l))[:200]) for l in sys.stdin]"

# Đổi model cho agent cụ thể
jq '.agents["<agent-id>"].model = "openrouter/google/gemini-3-flash-preview"' \
  ~/.openclaw/openclaw.json > /tmp/oc.json && mv /tmp/oc.json ~/.openclaw/openclaw.json
```

---

## 1.6 Troubleshoot Phổ Biến

| Triệu chứng | Nguyên nhân | Fix |
|---|---|---|
| Agent không phản hồi | Gateway chưa start / đang treo | `openclaw gateway restart` |
| Agent lỗi 400 sau nhiều tool calls | Gemini session limit | User gửi `/new` → nếu vẫn treo → restart gateway |
| Agent dùng sai cú pháp tool | SKILL.md thiếu ví dụ | Thêm rule bắt buộc đọc `--help` trước |
| Key bị reject | Key hết hạn hoặc hết quota | Kiểm tra dashboard provider, rotate key |
