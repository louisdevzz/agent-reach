<h1 align="center">👁️ Agent Reach</h1>

<p align="center">
  <strong>Trang bị khả năng truy cập internet cho AI Agent của bạn chỉ với một câu lệnh</strong>
</p>

<p align="center">
  Phương thức truy cập ổn định nhất hiện tại, được chọn sẵn, cài sẵn, kiểm tra sẵn — phương thức có thể thay đổi theo thời gian, bạn không cần lo
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="MIT License"></a>
  <a href="https://www.python.org/"><img src="https://img.shields.io/badge/Python-3.10+-green.svg?style=for-the-badge&logo=python&logoColor=white" alt="Python 3.10+"></a>
  <a href="https://github.com/Panniantong/agent-reach/stargazers"><img src="https://img.shields.io/github/stars/Panniantong/agent-reach?style=for-the-badge" alt="GitHub Stars"></a>
  <a href="https://atomgit.com/qq_51337814/Agent-Reach"><img src="https://atomgit.com/qq_51337814/Agent-Reach/star/badge.svg" alt="AtomGit Stars"></a>
</p>

<p align="center">
  🇨🇳 Truy cập trong nước: Dự án cũng được lưu trữ tại <a href="https://atomgit.com/qq_51337814/Agent-Reach">AtomGit mirror</a> (đồng bộ tự động với GitHub, clone nhanh hơn)
</p>

<p align="center">
  <a href="#bắt-đầu-nhanh">Bắt đầu nhanh</a> · <a href="README.en.md">English</a> · <a href="README.md">中文</a> · <a href="#nền-tảng-hỗ-trợ">Nền tảng hỗ trợ</a> · <a href="#triết-lý-thiết-kế">Triết lý thiết kế</a>
</p>

---

## Tại sao cần Agent Reach?

AI Agent đã có thể giúp bạn viết code, sửa tài liệu, quản lý dự án — nhưng khi bạn bảo nó tìm kiếm trên mạng, nó lại bó tay:

- 📺 "Xem giúp tôi video YouTube này nói về gì" → **Không xem được**, không lấy được phụ đề
- 🐦 "Tìm giúp tôi trên Twitter mọi người đánh giá sản phẩm này thế nào" → **Không tìm được**, Twitter API mất phí
- 📖 "Lên Reddit xem có ai gặp bug giống mình không" → **403 bị chặn**, IP máy chủ bị từ chối
- 📕 "Xem giúp tôi trên Xiaohongshu đánh giá về sản phẩm này" → **Không mở được**, phải đăng nhập mới xem được
- 📺 "Trên B站 có video kỹ thuật, tóm tắt giúp tôi" → **Không lấy được**, công cụ tải chung bị B站 chặn toàn diện
- 🔍 "Tìm giúp tôi trên mạng so sánh các LLM framework mới nhất" → **Không có công cụ tìm kiếm tốt**, hoặc mất phí hoặc chất lượng kém
- 🌐 "Đọc giúp tôi trang web này viết gì" → **Trả về một đống thẻ HTML**, không đọc được
- 📦 "Repo GitHub này làm gì? Issue nói gì?" → Dùng được, nhưng cấu hình xác thực phức tạp
- 📡 "Đăng ký giúp tôi vài nguồn RSS, có cập nhật thì báo" → Phải tự cài thư viện viết code

**Những việc này không khó, nhưng mất công tự mày mò cấu hình**

Mỗi nền tảng đều có rào cản riêng — API mất phí, tường lửa phải vượt, tài khoản phải đăng nhập, dữ liệu phải làm sạch. Bạn phải tự mình dò dẫm, cài công cụ, chỉnh cấu hình, chỉ riêng việc để Agent đọc được Twitter cũng mất nửa ngày.

**Agent Reach biến tất cả thành một câu lệnh:**

```
Cài Agent Reach cho tôi: https://raw.githubusercontent.com/Panniantong/agent-reach/main/docs/install.md
```

Copy cho Agent của bạn, vài phút sau nó đã có thể đọc Twitter, tìm Reddit, xem YouTube, lướt Xiaohongshu.

**Đã cài rồi? Cập nhật cũng chỉ một câu:**

```
Cập nhật Agent Reach cho tôi: https://raw.githubusercontent.com/Panniantong/agent-reach/main/docs/update.md
```

> ⭐ **Star dự án này**, chúng tôi sẽ liên tục theo dõi sự thay đổi của các nền tảng và tích hợp kênh mới. Bạn không cần tự theo dõi — nền tảng chặn thì chúng tôi sửa, có kênh mới thì chúng tôi thêm.

### ✅ Trước khi dùng, bạn có thể muốn biết

| | |
|---|---|
| 💰 **Hoàn toàn miễn phí** | Tất cả công cụ mã nguồn mở, tất cả API miễn phí. Chi phí duy nhất có thể phát sinh là proxy máy chủ ($1/tháng), máy tính cá nhân không cần |
| 🔒 **An toàn bảo mật** | Cookie chỉ lưu trên máy bạn, không upload ra ngoài. Mã nguồn hoàn toàn công khai, có thể kiểm tra bất cứ lúc nào |
| 🔄 **Luôn cập nhật** | Mỗi nền tảng đều có danh sách backend "chính + dự phòng". Một phương thức truy cập hỏng, chúng tôi chuyển sang cái tiếp theo, bạn không cảm thấy gì (tháng 6/2026: yt-dlp bị B站 chặn 412 → đã chuyển sang bili-cli, người dùng không cần làm gì) |
| 🤖 **Tương thích mọi Agent** | Claude Code, OpenClaw, Cursor, Windsurf… bất kỳ Agent nào chạy được dòng lệnh đều dùng được |
| 🩺 **Tích hợp chẩn đoán** | `agent-reach doctor` một câu lệnh cho bạn biết kênh nào thông, kênh nào tắc, cách sửa |

---

## Nền tảng hỗ trợ

| Nền tảng | Dùng ngay sau cài | Mở khóa sau cấu hình | Cách cấu hình |
|------|---------|-----------|-------|
| 🌐 **Web** | Đọc bất kỳ trang web nào | — | Không cần cấu hình |
| 📺 **YouTube** | Trích xuất phụ đề + tìm kiếm video | — | Không cần cấu hình |
| 📡 **RSS** | Đọc bất kỳ nguồn RSS/Atom nào | — | Không cần cấu hình |
| 🔍 **Tìm kiếm toàn mạng** | — | Tìm kiếm ngữ nghĩa toàn mạng | Tự động cấu hình (MCP, miễn phí không cần Key) |
| 📦 **GitHub** | Đọc repo công khai + tìm kiếm | Repo riêng, tạo Issue/PR, Fork | Bảo Agent "giúp tôi đăng nhập GitHub" |
| 🐦 **Twitter/X** | Đọc tweet đơn lẻ | Tìm kiếm tweet, duyệt timeline, đọc bài dài | Bảo Agent "giúp tôi cấu hình Twitter" |
| 📺 **B站** | Tìm kiếm + chi tiết video (bili-cli, không cần đăng nhập) | Phụ đề (OpenCLI) | Bảo Agent "giúp tôi cấu hình B站" |
| 📖 **Reddit** | — (không có đường dẫn không cấu hình: API ẩn danh đã bị chặn) | Tìm kiếm + đọc bài viết và bình luận | Desktop cài OpenCLI dùng trạng thái đăng nhập trình duyệt; hoặc rdt-cli + Cookie |
| 📕 **Xiaohongshu** | — | Tìm kiếm, đọc, bình luận | Desktop cài OpenCLI (đã lướt Xiaohongshu là dùng được); Server dùng xiaohongshu-mcp quét QR |
| 💼 **LinkedIn** | Jina Reader đọc trang công khai | Chi tiết Profile, trang công ty, tìm kiếm việc làm | Bảo Agent "giúp tôi cấu hình LinkedIn" |
| 💻 **V2EX** | Bài hot, bài theo node, chi tiết bài + trả lời, thông tin người dùng | — | Không cần cấu hình |
| 📈 **雪球** | Báo giá cổ phiếu, tìm kiếm cổ phiếu, bài hot, xếp hạng cổ phiếu hot | — | Bảo Agent "giúp tôi cấu hình 雪球" |
| 🎙️ **小宇宙 Podcast** | — | Chuyển âm thanh podcast thành văn bản (Whisper, Key miễn phí) | Bảo Agent "giúp tôi cấu hình 小宇宙" |

> **Không biết cấu hình? Không cần đọc tài liệu.** Cứ bảo Agent "giúp tôi cấu hình XXX", nó biết cần gì và sẽ hướng dẫn bạn từng bước.
>
> 🍪 Với nền tảng cần Cookie (Twitter, Xiaohongshu...), **ưu tiên dùng** Chrome extension [Cookie-Editor](https://chromewebstore.google.com/detail/cookie-editor/hlkenndednhfkekhgcdicdfddnkalmdm) để xuất Cookie, gửi cho Agent là cấu hình được. Quy trình thống nhất: đăng nhập trình duyệt → Cookie-Editor xuất → gửi cho Agent. Đơn giản và đáng tin cậy hơn quét QR.
>
> 🔒 Cookie chỉ lưu trên máy bạn, không upload ra ngoài. Mã nguồn hoàn toàn công khai, có thể kiểm tra bất cứ lúc nào.
> 💻 Máy tính cá nhân không cần proxy. Proxy chỉ cần khi triển khai trên máy chủ (~$1/tháng).

---

## Bắt đầu nhanh

> ⚠️ **Người dùng OpenClaw hãy xác nhận quyền exec đã được bật**
>
> Agent Reach phụ thuộc vào Agent thực thi lệnh shell (`pip install`, `mcporter`, `twitter`, v.v.). Nếu OpenClaw của bạn dùng cấu hình `messaging` mặc định, Agent sẽ không thể chạy lệnh. **Hãy bật exec trước khi cài đặt:**
>
> ```bash
> openclaw config set tools.profile "coding"
> ```
> Hoặc đặt `"tools": { "profile": "coding" }` trong `~/.openclaw/openclaw.json`.
> Sau khi đặt, khởi động lại Gateway (`openclaw gateway restart`) và mở cuộc hội thoại mới. Các nền tảng khác (Claude Code, Cursor, Windsurf...) không bị ảnh hưởng.

Copy câu này cho AI Agent của bạn (Claude Code, OpenClaw, Cursor, v.v.):

```
Cài Agent Reach cho tôi: https://raw.githubusercontent.com/Panniantong/agent-reach/main/docs/install.md
```

Chỉ một bước này. Agent sẽ tự hoàn thành mọi việc còn lại.

> 🔄 **Đã cài rồi?** Cập nhật cũng chỉ một câu:
> ```
> Cập nhật Agent Reach cho tôi: https://raw.githubusercontent.com/Panniantong/agent-reach/main/docs/update.md
> ```

> 🛡️ **Lo về bảo mật?** Có thể dùng chế độ an toàn — sẽ không tự động cài gói hệ thống, chỉ cho bạn biết cần gì:
> ```
> Cài Agent Reach cho tôi (chế độ an toàn): https://raw.githubusercontent.com/Panniantong/agent-reach/main/docs/install.md
> Dùng tham số --safe khi cài đặt
> ```

<details>
<summary>Nó sẽ làm gì? (nhấn để mở)</summary>

1. **Cài CLI tool** — `pip install` cài `agent-reach` command line (tích hợp sẵn yt-dlp, feedparser)
2. **Cài hạ tầng hệ thống** — Tự động phát hiện và cài Node.js, gh CLI, mcporter
3. **Cấu hình công cụ tìm kiếm** — Kết nối Exa qua MCP (miễn phí, không cần API Key)
4. **Phát hiện môi trường** — Xác định máy cá nhân hay máy chủ, đưa ra gợi ý cấu hình phù hợp
5. **Đăng ký SKILL.md** — Cài hướng dẫn sử dụng vào thư mục skills của Agent, sau này Agent gặp nhu cầu "nghiên cứu toàn mạng", "tìm Twitter", "xem video" sẽ tự động biết gọi công cụ upstream nào
6. **Hỏi bạn có muốn thêm không** — Mặc định chỉ kích hoạt 6 kênh không cần cấu hình; Xiaohongshu, Twitter, Reddit cần đăng nhập, Agent sẽ liệt kê menu hỏi bạn muốn kênh nào, chọn mới cài

Sau khi cài xong, `agent-reach doctor` một câu lệnh cho bạn biết trạng thái từng kênh, hiện đang đi đường nào.
</details>

---

## Dùng ngay sau khi cài

Không cần bất kỳ cấu hình nào, bảo Agent là được:

- "Đọc giúp tôi link này" → `curl https://r.jina.ai/URL` đọc bất kỳ trang web nào
- "Repo GitHub này làm gì" → `gh repo view owner/repo`
- "Video YouTube này nói về gì" → `yt-dlp` trích xuất phụ đề
- "Tìm trên B站 tutorial AI" → `bili search` (không cần đăng nhập)
- "Tìm toàn mạng so sánh LLM framework" → Exa tìm kiếm ngữ nghĩa
- "Đăng ký RSS này" → `feedparser` phân tích

**Không cần nhớ lệnh.** Agent đọc SKILL.md xong tự biết gọi gì. Nền tảng cần đăng nhập (Xiaohongshu, Twitter, Reddit), bảo Agent "giúp tôi cấu hình XXX" là mở khóa.

---

## Ranh giới năng lực: Đọc nội dung vs Thao tác trang web

Agent Reach giải quyết việc để Agent **đọc và tìm kiếm** nội dung trên internet, không thay thế người dùng thực hiện thao tác trang web sau đăng nhập, gửi form, cách ly đa tài khoản, phiên trình duyệt song song, v.v.

Nếu quy trình tự động hóa gặp phải các khâu ma sát cao như đăng nhập, xác minh, cảnh báo chống bot, cần can thiệp thủ công hoặc phiên trình duyệt thực, có thể kết hợp với [BrowserAct](https://browseract.com) — công cụ tự động hóa trình duyệt với 30+ kỹ năng nền tảng dựng sẵn, hỗ trợ Claude Code / OpenClaw / Cursor và các Agent chính.

---

## Triết lý thiết kế

**Agent Reach là một tầng năng lực (capability layer), không phải một công cụ nữa.**

Nó đứng cao hơn bất kỳ triển khai cụ thể nào — chịu trách nhiệm **lựa chọn, cài đặt, chẩn đoán, định tuyến**, không chịu trách nhiệm đọc dữ liệu bên dưới. Việc đọc do Agent trực tiếp gọi công cụ upstream thực hiện, không có tầng bọc trung gian.

Mỗi lần bạn cài môi trường cho Agent mới, bạn lại mất thời gian tìm công cụ, cài dependency, chỉnh cấu hình — Twitter dùng gì để đọc? Reddit đăng nhập thế nào? CLI Xiaohongshu ngừng cập nhật thì thay bằng gì? Lần nào cũng phải mò lại. Agent Reach làm một việc đơn giản: **phương thức truy cập ổn định nhất hiện tại, chúng tôi chọn sẵn, cài sẵn, kiểm tra sẵn cho bạn. Phương thức truy cập thay đổi (tháng 3/2026 một loạt CLI đơn nền tảng đồng loạt ngừng cập nhật, chúng tôi đã chuyển tuyến), bạn không cần lo.**

### 🔌 Mỗi nền tảng = Danh sách backend ưu tiên (chính + dự phòng)

Thay đổi phương thức truy cập = điều chỉnh thứ tự danh sách, không phải viết lại code. `agent-reach doctor` cho bạn biết mỗi nền tảng **hiện đang dùng backend nào**.

```
channels/
├── web.py          → Jina Reader
├── twitter.py      → twitter-cli ▸ OpenCLI ▸ bird
├── youtube.py      → yt-dlp
├── github.py       → gh CLI
├── bilibili.py     → bili-cli ▸ OpenCLI ▸ API tìm kiếm (yt-dlp đã bị B站 chặn 412, loại bỏ)
├── reddit.py       → OpenCLI ▸ rdt-cli (không có đường không cấu hình, phải có trạng thái đăng nhập)
├── xiaohongshu.py  → OpenCLI ▸ xiaohongshu-mcp ▸ xhs-cli
├── linkedin.py     → linkedin-mcp ▸ Jina Reader
├── rss.py          → feedparser
├── exa_search.py   → Exa qua mcporter
└── __init__.py     → Đăng ký kênh (dùng cho doctor)
```

Mỗi file kênh **thực sự thăm dò** từng backend ứng viên theo thứ tự (không chỉ kiểm tra lệnh tồn tại) — backend đầu tiên hoạt động đầy đủ được chọn; backend hỏng sẽ kèm phương án sửa chữa. Việc đọc và tìm kiếm thực tế do Agent trực tiếp gọi công cụ upstream thực hiện.

### Lựa chọn công cụ hiện tại

| Tình huống | Chính | Dự phòng | Tại sao chọn vậy |
|------|------|------|-----------|
| Đọc web | [Jina Reader](https://github.com/jina-ai/reader) | — | Miễn phí, không cần API Key |
| Đọc tweet | [twitter-cli](https://github.com/public-clis/twitter-cli) | [OpenCLI](https://github.com/jackwener/opencli) | Thực nghiệm tìm kiếm ổn định; OpenCLI dùng trạng thái đăng nhập trình duyệt dự phòng |
| Reddit | [OpenCLI](https://github.com/jackwener/opencli) (desktop) | [rdt-cli](https://github.com/public-clis/rdt-cli) | API ẩn danh đã bị chặn, API chính thức cần phê duyệt — chỉ còn đường trạng thái đăng nhập |
| YouTube phụ đề + tìm kiếm | [yt-dlp](https://github.com/yt-dlp/yt-dlp) | — | 154K Star, YouTube vẫn là tốt nhất (lưu ý: không còn dùng cho B站) |
| B站 | [bili-cli](https://github.com/public-clis/bilibili-cli) | OpenCLI ▸ API tìm kiếm | yt-dlp bị B站 chặn 412 (thực nghiệm 6/2026), bili-cli không cần đăng nhập vẫn tìm và đọc được |
| Tìm kiếm toàn mạng | [Exa](https://exa.ai) qua [mcporter](https://github.com/nicobailon/mcporter) | — | Tìm kiếm ngữ nghĩa AI, MCP không cần Key |
| GitHub | [gh CLI](https://cli.github.com) | — | Công cụ chính thức, đầy đủ năng lực API sau xác thực |
| Đọc RSS | [feedparser](https://github.com/kurtmckee/feedparser) | — | Lựa chọn tiêu chuẩn trong hệ sinh thái Python |
| Xiaohongshu | [OpenCLI](https://github.com/jackwener/opencli) (desktop) | [xiaohongshu-mcp](https://github.com/xpzouying/xiaohongshu-mcp) (server) ▸ xhs-cli | Tác giả xhs-cli đã chuyển sang OpenCLI (24K Star); trạng thái đăng nhập trình duyệt không ma sát |
| LinkedIn | [linkedin-scraper-mcp](https://github.com/stickerdaniel/linkedin-mcp-server) | Jina Reader | Dịch vụ MCP, tự động hóa trình duyệt |

> 📌 Đây đều là "lựa chọn hiện tại", dựa trên thực nghiệm máy thật định kỳ. Đường nào hỏng chúng tôi đổi sang đường tiếp theo — `agent-reach doctor` luôn cho bạn biết hiện đang đi đường nào.

---

## Bảo mật

Agent Reach coi trọng bảo mật trong thiết kế:

| Biện pháp | Mô tả |
|------|------|
| 🔒 **Lưu trữ cục bộ** | Cookie, Token chỉ lưu trên máy bạn `~/.agent-reach/config.yaml`, quyền file 600 (chỉ chủ sở hữu đọc ghi), không upload ra ngoài |
| 🛡️ **Chế độ an toàn** | `agent-reach install --safe` không tự động sửa đổi hệ thống, chỉ liệt kê cần gì, bạn quyết định cài hay không |
| 👀 **Mã nguồn mở hoàn toàn** | Code minh bạch, có thể kiểm tra bất cứ lúc nào. Tất cả công cụ phụ thuộc cũng là dự án mã nguồn mở |
| 🔍 **Dry Run** | `agent-reach install --dry-run` xem trước mọi thao tác, không thay đổi gì |
| 🧩 **Kiến trúc có thể tháo lắp** | Không tin tưởng thành phần nào? Thay file channel tương ứng là được, không ảnh hưởng phần khác |

### 🍪 Khuyến cáo an toàn Cookie

> ⚠️ **Cảnh báo rủi ro khóa tài khoản:** Các nền tảng dùng Cookie đăng nhập (Twitter, Xiaohongshu...), việc gọi qua script/API **có rủi ro bị nền tảng phát hiện và khóa tài khoản**. Hãy dùng **tài khoản phụ chuyên dụng**, không dùng tài khoản chính của bạn.

Với nền tảng cần Cookie (Twitter, Xiaohongshu), khuyến nghị dùng **tài khoản phụ chuyên dụng**, không dùng tài khoản chính. Hai lý do:
1. **Rủi ro khóa tài khoản** — Nền tảng có thể phát hiện hành vi gọi API không giống trình duyệt thông thường, dẫn đến tài khoản bị hạn chế hoặc khóa
2. **Rủi ro bảo mật** — Cookie tương đương với quyền đăng nhập đầy đủ, dùng tài khoản phụ có thể giới hạn phạm vi ảnh hưởng khi thông tin đăng nhập bị rò rỉ

### 📦 Phương thức cài đặt

| Phương thức | Lệnh | Phù hợp |
|------|------|---------|
| Tự động hoàn toàn (mặc định) | `agent-reach install --env=auto` | Máy tính cá nhân, môi trường phát triển |
| Chế độ an toàn | `agent-reach install --env=auto --safe` | Máy chủ production, máy dùng chung |
| Chỉ xem trước | `agent-reach install --env=auto --dry-run` | Xem trước sẽ làm gì |

### 🗑️ Gỡ cài đặt

```bash
agent-reach uninstall
```

Sẽ xóa: `~/.agent-reach/` (bao gồm tất cả token/cookie), file skill của các Agent, cấu hình MCP trong mcporter.

```bash
# Chỉ xem trước, không xóa thực tế
agent-reach uninstall --dry-run

# Chỉ xóa file skill, giữ lại cấu hình token (dùng khi cài lại)
agent-reach uninstall --keep-config
```

Gỡ package Python: `pip uninstall agent-reach`

---

## Đóng góp

Dự án này hoàn toàn được vibe coding 🎸 có thể có một số chỗ chưa hoàn hảo, nếu gặp vấn đề mong bạn thông cảm. Có bug cứ mở [Issue](https://github.com/Panniantong/agent-reach/issues), tôi sẽ sửa nhanh nhất có thể.

**Muốn kênh mới?** Mở Issue đề xuất, hoặc tự tạo PR.

**Muốn tự thêm local?** Bảo Agent clone về sửa là được, mỗi kênh là một file độc lập, thêm vào rất đơn giản.

[PR](https://github.com/Panniantong/agent-reach/pulls) luôn được chào đón!

---

## ⭐ Tại sao đáng Star

Dự án này chính tôi dùng hàng ngày, nên tôi sẽ luôn duy trì nó.

- Có nhu cầu mới hoặc mọi người đề xuất kênh mới, tôi sẽ dần bổ sung
- Mỗi kênh tôi sẽ cố gắng đảm bảo **dùng được, dễ dùng, miễn phí**
- Nền tảng thay đổi chống crawler hoặc API thay đổi, tôi sẽ tìm cách giải quyết

Đóng góp một phần sức lực cho hạ tầng Web 4.0.

Star một cái, lần sau cần là tìm thấy. ⭐

---

## FAQ / Câu hỏi thường gặp

<details>
<summary><strong>AI Agent tìm kiếm Twitter / X thế nào? Không muốn trả phí API</strong></summary>

Agent Reach dùng [twitter-cli](https://github.com/public-clis/twitter-cli) xác thực qua Cookie để truy cập Twitter, hoàn toàn miễn phí. Cài: `pipx install twitter-cli`, đảm bảo trình duyệt đã đăng nhập x.com, Agent có thể dùng `twitter search "từ khóa"` để tìm, `twitter tweet URL` để đọc tweet.
</details>

<details>
<summary><strong>Reddit trả về 403 thì làm sao?</strong></summary>

Reddit yêu cầu trạng thái đăng nhập cho mọi truy cập (API ẩn danh đã bị chặn toàn diện, API chính thức cần phê duyệt thủ công). Desktop ưu tiên **OpenCLI**: trình duyệt đã đăng nhập reddit.com là dùng được ngay `opencli reddit search "từ khóa"`. Dự phòng [rdt-cli](https://github.com/public-clis/rdt-cli): `pipx install 'git+https://github.com/public-clis/rdt-cli.git@5e4fb3720d5c174e976cd425ccc3b879d52cac66'` (phiên bản đóng đinh với code, PyPI chậm hơn), sau đó `rdt login`. Mạng Trung Quốc đại lục cần proxy để truy cập Reddit.
</details>

<details>
<summary><strong>Làm sao để AI Agent đọc Xiaohongshu?</strong></summary>

Desktop ưu tiên **OpenCLI** (`agent-reach install --channels opencli`) — nó tái sử dụng trạng thái đăng nhập trong trình duyệt của bạn, bình thường đã lướt Xiaohongshu là dùng được ngay, không cần cấu hình; cài xong vào Chrome Web Store nhấn "thêm extension" là xong. Sau đó Agent dùng `opencli xiaohongshu search "từ khóa"` để tìm, `opencli xiaohongshu note URL` để đọc bài. Server dùng [xiaohongshu-mcp](https://github.com/xpzouying/xiaohongshu-mcp) (tích hợp trình duyệt không đầu, quét QR đăng nhập). Người dùng cũ đã cài xhs-cli không bị ảnh hưởng, nó vẫn là backend dự phòng (upstream ngừng cập nhật từ 3/2026, không khuyến nghị cài mới).
</details>

<details>
<summary><strong>Tương thích với Claude Code / Cursor / OpenClaw / Windsurf không?</strong></summary>

Có! Agent Reach là công cụ cài đặt + cấu hình — bất kỳ AI coding agent nào chạy được lệnh shell đều dùng được. Hoạt động với Claude Code, Cursor, OpenClaw, Windsurf, Codex, và nhiều hơn nữa. Chỉ cần `pip install agent-reach`, chạy `agent-reach install`, Agent có thể bắt đầu dùng công cụ upstream ngay lập tức.

**Lưu ý OpenClaw:** Nếu OpenClaw dùng profile `messaging` mặc định, Agent sẽ không chạy được lệnh shell. Hãy bật exec trước: `openclaw config set tools.profile "coding"` (hoặc đặt `"tools": { "profile": "coding" }` trong `~/.openclaw/openclaw.json`), sau đó khởi động lại Gateway và mở cuộc hội thoại mới trước khi cài đặt.
</details>

<details>
<summary><strong>Có miễn phí không? Có phí API nào không?</strong></summary>

100% miễn phí. Tất cả backend đều là công cụ mã nguồn mở (OpenCLI, twitter-cli, bili-cli, rdt-cli, yt-dlp, Jina Reader, Exa, xiaohongshu-mcp...) không yêu cầu API key trả phí. Chi phí duy nhất có thể có là residential proxy (~$1/tháng) khi mạng của bạn chặn Reddit/Twitter (ví dụ: Trung Quốc đại lục).
</details>

<details>
<summary><strong>Làm sao lấy phụ đề video YouTube cho AI?</strong></summary>

`yt-dlp --dump-json "https://youtube.com/watch?v=xxx"` trích xuất metadata video; `yt-dlp --write-sub --skip-download "URL"` trích xuất phụ đề. Dùng yt-dlp bên dưới, hỗ trợ nhiều ngôn ngữ. Không cần API key.
</details>

---

## Lời cảm ơn

[OpenCLI](https://github.com/jackwener/opencli) · [twitter-cli](https://github.com/public-clis/twitter-cli) · [rdt-cli](https://github.com/public-clis/rdt-cli) · [xiaohongshu-mcp](https://github.com/xpzouying/xiaohongshu-mcp) · [xhs-cli](https://github.com/jackwener/xiaohongshu-cli) · [bili-cli](https://github.com/public-clis/bilibili-cli) · [yt-dlp](https://github.com/yt-dlp/yt-dlp) · [Jina Reader](https://github.com/jina-ai/reader) · [Exa](https://exa.ai) · [mcporter](https://github.com/nicobailon/mcporter) · [feedparser](https://github.com/kurtmckee/feedparser) · [linkedin-scraper-mcp](https://github.com/stickerdaniel/linkedin-mcp-server)

## Liên hệ

- 📧 **Email:** pnt01@foxmail.com
- 🐦 **Twitter/X:** [@Neo_Reidlab](https://x.com/Neo_Reidlab)

Trao đổi hoặc hợp tác có thể thêm WeChat, kéo bạn vào group:

<p align="center">
  <img src="docs/wechat-group-qr.jpg" width="280" alt="WeChat QR">
</p>

> Báo bug và đề xuất tính năng vui lòng dùng [GitHub Issues](https://github.com/Panniantong/Agent-Reach/issues), dễ theo dõi hơn.

## License

[MIT](LICENSE)

## Liên kết

[Tencent Cloud OpenClaw](https://www.tencentcloud.com/act/pro/intl-openclaw?referral_code=G76Y819A&lang=zh&pg=) — Triển khai OpenClaw trên Tencent Cloud Lighthouse trong vài giây, kết nối Agent Reach qua chat để trang bị khả năng internet.

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=Panniantong/Agent-Reach&type=Date&v=20260309)](https://star-history.com/#Panniantong/Agent-Reach&Date)
