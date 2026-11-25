# Ý nghĩa các cột 87–139 

Nguồn: `schema.csv` (mã câu hỏi `qid`, tên trường `qname`, kiểu câu hỏi `type` và lời dẫn gốc), đối chiếu với bảng dữ liệu khảo sát thực tế (`results.csv`).

**Lưu ý đối chiếu chỉ số cột & tên file:**
- Trong `schema.csv` (tổng 139 dòng, đánh số từ `1` đến `139`), cột thứ **87** là `PlatformWantEntry` (`QID57`), ngay sau `PlatformHaveEntry` (cột 86 trong `schema.csv`) và tiếp nối nhóm web framework (`WebframeChoice` ở cột 88).
- Trong file dữ liệu khảo sát thực tế (`results.csv`, 172 cột; hoặc file dữ liệu khảo sát của nhóm sau khi giải nén), các câu hỏi dạng ma trận (`Matrix`) như `Webframe`, `DevEnvs`, `SOTags`, `OpSys`, `OfficeStackAsync`, `CommPlatform`, `AIModels`, `AITool`, `AIAgentImpact`, `AIAgentChallenges` được tách thành nhiều cột con tương ứng với từng chiều đánh giá (ví dụ `*HaveWorkedWith`, `*WantToWorkWith`, `*Admired` hoặc từng mức độ đồng ý). Khi làm việc trên file dữ liệu đã tách cột, cần lọc/khớp theo `qname` và tiền tố/hậu tố cột con thay vì chỉ dựa vào số dòng trong `schema.csv`.
- Các ô trống (`NaN`) xuất hiện do người trả lời không thuộc nhánh được hỏi (ví dụ chọn `No` ở câu `*Choice` hoặc không sử dụng AI agents) hoặc bỏ qua câu hỏi.

---

## A. Nhóm hoàn tất Cloud/Platform & Web Framework (cột 87–91 trong `schema.csv`)

### 87. `PlatformWantEntry` (`QID57`) — Gõ tay: nền tảng cloud / công cụ hạ tầng muốn dùng
- **Lời dẫn (schema):** "Was the cloud platforms, containerization/orchestration tools, package managers, build tools, and infrastructure as code solutions you want to use not listed above? List below, separated by a comma and a space for each, what you want to use next year."
  - Dịch: Những nền tảng cloud, công cụ container/điều phối, trình quản lý gói, công cụ build hoặc hạ tầng dưới dạng mã (IaC) bạn muốn dùng nhưng chưa liệt kê ở trên là gì? Liệt kê bên dưới, cách nhau bởi dấu phẩy và dấu cách.
- **Kiểu:** văn bản tự do (`TE`) · người trả lời tự nhập chuỗi cách nhau bằng `, `.
- **Lưu ý:** Dữ liệu rời rạc, nhiều cách viết hoa/thường và chính tả khác nhau, tỷ lệ thiếu dữ liệu rất cao.

### 88. `WebframeChoice` (`QID47`) — Có làm việc hoặc dự định làm việc với web framework không
- **Lời dẫn (schema):** "Did you work with web frameworks and web technologies in the last year or do you plan to in the year to come? Here, we are referring to technology that helps website and web apps materialize."
  - Dịch: Bạn có làm việc với các web framework và công nghệ web trong năm qua hoặc có kế hoạch làm việc trong năm tới không? Ở đây đề cập đến công nghệ giúp hiện thực hóa website và ứng dụng web.
- **Kiểu:** chọn **một** đáp án (`MC`) · thường gồm `Yes` / `No`.
- **Lưu ý:** Là câu hỏi rẽ nhánh điều hướng cho khối câu hỏi `Webframe` phía sau; nếu chọn `No` thì các cột `Webframe*` tương ứng sẽ trống.

### 89. `Webframe` (`QID37`) — Web framework và công nghệ web đã dùng / muốn dùng
- **Lời dẫn (schema):** "Which web frameworks and web technologies have you done extensive development work in over the past year, and which do you want to work in over the next year? (If you both worked with the framework and want to continue to do so, please check both boxes in that row.)"
  - Dịch: Bạn đã phát triển chuyên sâu với những web framework và công nghệ web nào trong năm qua, và muốn làm việc với công nghệ nào trong năm tới? (Nếu vừa đã làm vừa muốn tiếp tục làm, hãy chọn cả hai ô trên dòng đó.)
- **Kiểu:** ma trận đa lựa chọn (`Matrix`) · trong dữ liệu khảo sát tách thành các cột thành phần (đã làm việc chuyên sâu `HaveWorkedWith`, muốn làm việc `WantToWorkWith`, và nhóm giao `Admired`), các lựa chọn nối nhau bằng dấu `;`.
- **Lưu ý:** Giữ chiều đã làm việc thực tế (`HaveWorkedWith`, nếu đạt ngưỡng độ phủ sau lọc đối tượng) và **loại bỏ** `WantToWorkWith` (nguyện vọng tương lai) cũng như `Admired` (trùng lặp) khi xây dựng đặc trưng dự đoán thu nhập.

### 90. `WebframeHaveEntry` (`QID58`) — Gõ tay: web framework đã dùng nhưng chưa có trong danh sách
- **Lời dẫn (schema):** "Were the web frameworks and web technologies you use not listed above? List below, separated by a comma and a space for each, what you used in the past year."
  - Dịch: Những web framework và công nghệ web bạn sử dụng chưa có trong danh sách trên là gì? Liệt kê bên dưới những gì bạn đã dùng trong năm qua, cách nhau bởi dấu phẩy và dấu cách.
- **Kiểu:** văn bản tự do (`TE`).

### 91. `WebframeWantEntry` (`QID59`) — Gõ tay: web framework muốn dùng nhưng chưa có trong danh sách
- **Lời dẫn (schema):** "Were the web frameworks and web technologies you want to use not listed above? List below, separated by a comma and a space for each, what you want to use next year."
  - Dịch: Những web framework và công nghệ web bạn muốn dùng chưa có trong danh sách trên là gì? Liệt kê bên dưới những gì bạn muốn dùng trong năm tới, cách nhau bởi dấu phẩy và dấu cách.
- **Kiểu:** văn bản tự do (`TE`).

---

## B. Môi trường phát triển (IDE / AI Editors) & Tag mới trên Stack Overflow (cột 92–98)

### 92. `DevEnvsChoice` (`QID48`) — Có dùng môi trường phát triển / công cụ chỉnh sửa mã AI không
- **Lời dẫn (schema):** "Did you work with development environments or AI-enabled code editing tools in the last year or do you plan to in the year to come? Here, we are referring to programs like VS Code that allow you to write, edit and save code easily and help you share code with other developers or AI agents."
  - Dịch: Bạn có làm việc với các môi trường phát triển hoặc công cụ chỉnh sửa mã hỗ trợ AI trong năm qua hoặc có kế hoạch trong năm tới không? Ở đây đề cập đến các phần mềm như VS Code giúp viết, chỉnh sửa, lưu mã dễ dàng và chia sẻ mã với lập trình viên khác hoặc AI agents.
- **Kiểu:** chọn **một** đáp án (`MC`).
- **Lưu ý:** Câu hỏi rẽ nhánh cho nhóm `DevEnvs`.

### 93. `DevEnvs` (`QID38`) — Môi trường phát triển & công cụ chỉnh sửa mã AI đã dùng / muốn dùng
- **Lời dẫn (schema):** "Which development environments and AI-enabled code editing tools did you use regularly over the past year, and which do you want to work with over the next year? Please check all that apply."
  - Dịch: Bạn đã sử dụng thường xuyên những môi trường phát triển và công cụ chỉnh sửa mã hỗ trợ AI nào trong năm qua, và muốn làm việc với công cụ nào trong năm tới? Chọn tất cả đáp án phù hợp.
- **Kiểu:** ma trận đa lựa chọn (`Matrix`), nối nhau bằng dấu `;`.
- **Lưu ý:** Phản ánh bộ công cụ lập trình hằng ngày thực tế (IDE truyền thống lẫn AI code editors); giữ chiều sử dụng thực tế, bỏ chiều nguyện vọng/trùng lặp.

### 94. `DevEnvHaveEntry` (`QID60`) — Gõ tay: IDE / công cụ chỉnh sửa mã AI đã dùng
- **Lời dẫn (schema):** "Was the developer environment or AI-enabled code editing tool you use not listed above? List below, separated by a comma and a space for each, what you used in the past year."
  - Dịch: Môi trường phát triển hoặc công cụ chỉnh sửa mã AI bạn dùng chưa liệt kê ở trên là gì? Liệt kê những công cụ đã dùng trong năm qua.
- **Kiểu:** văn bản tự do (`TE`).

### 95. `DevEnvWantEntry` (`QID61`) — Gõ tay: IDE / công cụ chỉnh sửa mã AI muốn dùng
- **Lời dẫn (schema):** "Was the developer environment or AI-enabled code editing tool you use not listed above? List below, separated by a comma and a space for each, what you want to use next year."
  - Dịch: Môi trường phát triển hoặc công cụ chỉnh sửa mã AI bạn muốn dùng chưa liệt kê ở trên là gì? Liệt kê những công cụ muốn dùng năm tới.
- **Kiểu:** văn bản tự do (`TE`).

### 96. `SOTags` (`QID39`) — Tag / chủ đề công nghệ mới nổi trên Stack Overflow
- **Lời dẫn (schema):** "Which rising technology of the added as new tag or tag subject area on Stack Overflow in the last three years have you used regularly in the past year, and which do you want to work with over the next year? Please check all that apply."
  - Dịch: Công nghệ mới nổi nào được thêm làm tag hoặc nhóm chủ đề mới trên Stack Overflow trong 3 năm qua mà bạn đã dùng thường xuyên trong năm qua và muốn làm việc trong năm tới?
- **Kiểu:** ma trận đa lựa chọn (`Matrix`), nối nhau bằng dấu `;`.
- **Lưu ý:** Thiên về mức độ quan tâm các chủ đề mới trên diễn đàn Stack Overflow, độ phủ thấp và có nhiều giá trị thiếu.

### 97. `SOTagsHaveEntry` (`QID62`) — Gõ tay: tag mới trên Stack Overflow đã dùng
- **Lời dẫn (schema):** "Was the new tag on Stack Overflow (i.e. added in the last 2 - 3 years) you use not listed above? List below, separated by a comma and a space for each, what you used in the past year."
  - Dịch: Tag mới trên Stack Overflow (thêm trong 2–3 năm gần đây) bạn đã dùng nhưng chưa có trong danh sách là gì?
- **Kiểu:** văn bản tự do (`TE`).

### 98. `SOTagsWant Entry` (`QID63`) — Gõ tay: tag mới trên Stack Overflow muốn dùng
- **Lời dẫn (schema):** "Was the new tag on Stack Overflow (i.e. added in the last 2 - 3 years) you want to use not listed above? List below, separated by a comma and a space for each, what you want to use next year."
  - Dịch: Tag mới trên Stack Overflow bạn muốn dùng trong năm tới nhưng chưa có trong danh sách là gì?
- **Kiểu:** văn bản tự do (`TE`) · **lưu ý tên cột gốc trong schema có dấu cách trước `Entry`**.

---

## C. Hệ điều hành, công cụ cộng tác, cộng đồng & mô hình LLM (cột 99–109)

### 99. `OpSys` (`QID40`) — Hệ điều hành làm việc chính
- **Lời dẫn (schema):** "What is the primary operating system in which you work?"
  - Dịch: Hệ điều hành chính mà bạn sử dụng để làm việc là gì?
- **Kiểu:** ma trận / đa lựa chọn (`Matrix`), các hệ điều hành nối nhau bằng dấu `;` (ví dụ Windows, macOS, Ubuntu, Linux...).
- **Lưu ý:** Có liên hệ thực tế với môi trường làm việc và phân khúc công ty/thiết bị.

### 100. `OfficeStackAsync` (`QID41`) — Công cụ quản lý công việc cộng tác & tài liệu mã nguồn
- **Lời dẫn (schema):** "Which collaborative work management and/or code documentation tools did you use regularly over the past year, and which do you want to work with over the next year? Select all that apply"
  - Dịch: Bạn đã sử dụng thường xuyên những công cụ quản lý công việc cộng tác và/hoặc tài liệu mã nguồn nào trong năm qua, và muốn dùng công cụ nào trong năm tới?
- **Kiểu:** ma trận đa lựa chọn (`Matrix`), nối nhau bằng dấu `;` (ví dụ Jira, Confluence, Notion, GitHub Issues...).
- **Lưu ý:** Phản ánh quy trình làm việc nhóm trong doanh nghiệp; chỉ giữ chiều sử dụng thực tế đạt ngưỡng độ phủ, bỏ chiều nguyện vọng/trùng lặp.

### 101. `OfficeStackHaveEntry` (`QID64`) — Gõ tay: công cụ quản lý công việc / tài liệu đã dùng
- **Lời dẫn (schema):** "Was the collaborative work management and/or code documentation tools you use not listed above? List below, separated by a comma and a space for each, what you used in the past year."
  - Dịch: Công cụ quản lý công việc cộng tác / tài liệu mã nguồn bạn đã dùng trong năm qua nhưng chưa liệt kê ở trên.
- **Kiểu:** văn bản tự do (`TE`).

### 102. `OfficeStackWantEntry` (`QID65`) — Gõ tay: công cụ quản lý công việc / tài liệu muốn dùng
- **Lời dẫn (schema):** "Was the collaborative work management and/or code documentation tools you want to use not listed above? List below, separated by a comma and a space for each, what you used in the past year."
  - Dịch: Công cụ quản lý công việc cộng tác / tài liệu mã nguồn bạn muốn dùng nhưng chưa liệt kê ở trên (lời dẫn gốc trong schema lặp cụm "what you used in the past year").
- **Kiểu:** văn bản tự do (`TE`).

### 103. `CommPlatform` (`QID42`) — Nền tảng cộng đồng sử dụng
- **Lời dẫn (schema):** "Which community platforms have you utilized considerably or consistently in the past year, and which would you like to use next year? Select all that apply."
  - Dịch: Bạn đã sử dụng đáng kể hoặc đều đặn những nền tảng cộng đồng nào trong năm qua, và muốn sử dụng nền tảng nào trong năm tới?
- **Kiểu:** ma trận đa lựa chọn (`Matrix`), nối nhau bằng dấu `;` (ví dụ Discord, Reddit, Stack Overflow, GitHub Discussions...).
- **Lưu ý:** Thiên về kênh trao đổi/cộng đồng trực tuyến hơn là năng lực chuyên môn trực tiếp quyết định lương.

### 104. `CommPlatformHaveEntr` (`QID66`) — Gõ tay: nền tảng cộng đồng đã dùng
- **Lời dẫn (schema):** "Was the community platform you use not listed above? List below, separated by a comma and a space for each, what you used in the past year."
  - Dịch: Nền tảng cộng đồng bạn đã dùng trong năm qua nhưng chưa liệt kê ở trên.
- **Kiểu:** văn bản tự do (`TE`) · **lưu ý tên cột gốc bị cắt bớt chữ `y` (`HaveEntr`)**.

### 105. `CommPlatformWantEntr` (`QID67`) — Gõ tay: nền tảng cộng đồng muốn dùng
- **Lời dẫn (schema):** "Was the community platform you want to use not listed above? List below, separated by a comma and a space for each, what you used in the past year."
  - Dịch: Nền tảng cộng đồng bạn muốn dùng nhưng chưa liệt kê ở trên.
- **Kiểu:** văn bản tự do (`TE`) · **lưu ý tên cột gốc bị cắt bớt chữ `y` (`WantEntr`)**.

### 106. `AIModelsChoice` (`QID50`) — Có sử dụng / tích hợp mô hình LLM vào công cụ hoặc ứng dụng không
- **Lời dẫn (schema):** "Did you utilize or integrate specific Large Language Models (LLMs) to power your development tools or applications in the last year? Here, we are referring to models like GPT-4, Llama, Claude, etc., within your development environments or solutions."
  - Dịch: Trong năm qua bạn có sử dụng hoặc tích hợp các mô hình ngôn ngữ lớn (LLM như GPT-4, Llama, Claude...) để vận hành công cụ phát triển hoặc ứng dụng của mình không?
- **Kiểu:** chọn **một** đáp án (`MC`).
- **Lưu ý:** Câu hỏi rẽ nhánh cho nhóm `AIModels`.

### 107. `AIModels` (`QID43`) — Các mô hình LLM đã dùng / muốn dùng cho công việc phát triển
- **Lời dẫn (schema):** "Which LLM models for AI tools have you used for development work in the past year, and which would you like to use next year? Select all that apply."
  - Dịch: Bạn đã dùng những mô hình LLM nào phục vụ công việc phát triển trong năm qua, và muốn dùng mô hình nào trong năm tới?
- **Kiểu:** ma trận đa lựa chọn (`Matrix`), nối nhau bằng dấu `;`.
- **Lưu ý:** Cột `HaveWorkedWith` phản ánh việc ứng dụng mô hình AI thực tế trong công việc; các cột `WantToWorkWith` / `Admired` thiên về nguyện vọng và thường thiếu dữ liệu nhiều hơn.

### 108. `AIModelsHaveEntry` (`QID68`) — Gõ tay: mô hình LLM đã dùng
- **Lời dẫn (schema):** "Was the LLM model for AI tools you use not listed above? List below, separated by a comma and a space for each, what you used in the past year."
  - Dịch: Mô hình LLM bạn đã dùng trong năm qua nhưng chưa liệt kê ở trên.
- **Kiểu:** văn bản tự do (`TE`).

### 109. `AIModelsWantEntry` (`QID69`) — Gõ tay: mô hình LLM muốn dùng
- **Lời dẫn (schema):** "Was the LLM model for AI tools you want to use not listed above? List below, separated by a comma and a space for each, what you want to use next year."
  - Dịch: Mô hình LLM bạn muốn dùng trong năm tới nhưng chưa liệt kê ở trên.
- **Kiểu:** văn bản tự do (`TE`).

---

## D. Tương tác & mức độ gắn bó với Stack Overflow (cột 110–116)

### 110. `SOAccount` (`QID72`) — Có tài khoản Stack Overflow không
- **Lời dẫn (schema):** "Do you have a Stack Overflow account?"
  - Dịch: Bạn có tài khoản Stack Overflow không?
- **Kiểu:** chọn **một** đáp án (`MC`).

### 111. `SOVisitFreq` (`QID70`) — Tần suất truy cập Stack Overflow
- **Lời dẫn (schema):** "How frequently would you say you visit Stack Overflow?"
  - Dịch: Bạn truy cập Stack Overflow với tần suất như thế nào?
- **Kiểu:** chọn **một** đáp án (`MC`).

### 112. `SODuration` (`QID71`) — Thời gian đã sử dụng Stack Overflow
- **Lời dẫn (schema):** "How long have you used Stack Overflow?"
  - Dịch: Bạn đã sử dụng Stack Overflow được bao lâu rồi?
- **Kiểu:** chọn **một** đáp án (`MC`).

### 113. `SOPartFreq` (`QID73`) — Tần suất tham gia Q&A trên Stack Overflow
- **Lời dẫn (schema):** "How frequently would you say you participate in Q&A on Stack Overflow? By participate we mean ask, answer, and vote or comment on questions."
  - Dịch: Bạn tham gia hỏi-đáp (đặt câu hỏi, trả lời, bình chọn hoặc bình luận) trên Stack Overflow thường xuyên thế nào?
- **Kiểu:** chọn **một** đáp án (`MC`).

### 114. `SO_Dev_Content` (`QID75`) — Định dạng nội dung thay thế Q&A ưa thích
- **Lời dẫn (schema):** "Whether it be to solve a problem, for career growth or connecting with a community of developers, is there an alternative to the Q&A format you prefer using today or would like to see on Stack Overflow to get what you need? Select all that apply."
  - Dịch: Dù là để giải quyết vấn đề, phát triển sự nghiệp hay kết nối cộng đồng lập trình viên, có định dạng thay thế nào cho hình thức hỏi-đáp mà bạn thích dùng hiện nay hoặc muốn thấy trên Stack Overflow không?
- **Kiểu:** chọn **nhiều** đáp án (`MC`), nối nhau bằng dấu `;`.
- **Lưu ý:** Sở thích cá nhân về định dạng nội dung trên nền tảng Stack Overflow.

### 115. `SOComm` (`QID77`) — Cảm nhận có thuộc cộng đồng Stack Overflow không
- **Lời dẫn (schema):** "Do you consider yourself a member of the Stack Overflow community?"
  - Dịch: Bạn có tự coi mình là một thành viên của cộng đồng Stack Overflow không?
- **Kiểu:** chọn **một** đáp án (`MC`).
- **Lưu ý:** Cảm nhận chủ quan cá nhân.

### 116. `SOFriction` (`QID97`) — Tần suất vào Stack Overflow do lỗi từ công cụ AI
- **Lời dẫn (schema):** "When you visit Stack Overflow, how often is it a result of encountering issues from AI or AI-enabled tools that require extra time or effort to fix, understand, or debug?"
  - Dịch: Khi bạn truy cập Stack Overflow, mức độ thường xuyên nguyên nhân là do gặp sự cố từ AI hoặc công cụ hỗ trợ AI khiến bạn tốn thêm thời gian/công sức để sửa, hiểu hoặc gỡ lỗi là bao nhiêu?
- **Kiểu:** chọn **một** đáp án (`MC`).
- **Lưu ý:** Trải nghiệm cá nhân khi gỡ lỗi đầu ra AI.

---

## E. Thái độ, mức độ tin cậy & cách sử dụng công cụ AI (cột 117–123)

### 117. `AISelect` (`QID78`) — Có đang sử dụng công cụ AI trong quy trình phát triển không
- **Lời dẫn (schema):** "Do you currently use AI tools in your development process?"
  - Dịch: Hiện tại bạn có sử dụng các công cụ AI trong quy trình phát triển phần mềm của mình không?
- **Kiểu:** chọn **một** đáp án (`MC`) · phản ánh mức độ áp dụng công cụ AI thực tế (đang dùng hằng ngày, có kế hoạch dùng, hoặc không dùng).

### 118. `AISent` (`QID79`) — Thái độ / mức độ ủng hộ dùng công cụ AI
- **Lời dẫn (schema):** "How favorable is your stance on using AI tools as part of your development workflow?"
  - Dịch: Quan điểm của bạn ủng hộ việc sử dụng các công cụ AI trong quy trình phát triển ở mức độ nào?
- **Kiểu:** chọn **một** đáp án (`MC`) · **quan điểm/thái độ cá nhân**.

### 119. `AIAcc` (`QID80`) — Mức độ tin tưởng độ chính xác của đầu ra từ công cụ AI
- **Lời dẫn (schema):** "How much do you trust the accuracy of the output from AI tools as part of your development workflow?"
  - Dịch: Bạn tin tưởng mức độ chính xác của kết quả do công cụ AI tạo ra trong quy trình làm việc đến mức nào?
- **Kiểu:** chọn **một** đáp án (`MC`) · **đánh giá chủ quan cá nhân**.

### 120. `AIComplex` (`QID81`) — Đánh giá khả năng xử lý tác vụ phức tạp của công cụ AI
- **Lời dẫn (schema):** "How well do the AI tools you use in your development workflow handle complex tasks?"
  - Dịch: Các công cụ AI bạn dùng trong quy trình phát triển xử lý các tác vụ phức tạp tốt đến mức nào?
- **Kiểu:** chọn **một** đáp án (`MC`) · **đánh giá chủ quan cá nhân**.

### 121. `AITool` (`QID82`) — Các khâu tích hợp công cụ AI trong quy trình phát triển
- **Lời dẫn (schema):** "Which parts of your development workflow are you currently integrating into AI or using AI tools to accomplish or plan to use AI to accomplish over the next 3 - 5 years? Please select one for each scenario."
  - Dịch: Bạn hiện đang tích hợp AI hoặc sử dụng công cụ AI để thực hiện những phần nào trong quy trình phát triển, hoặc dự định dùng AI để thực hiện trong 3–5 năm tới?
- **Kiểu:** ma trận (`Matrix`) · trong dữ liệu khảo sát tách thành nhiều cột con theo từng mức độ sử dụng hiện tại / kế hoạch tương lai.
- **Lưu ý:** Chỉ các cột phản ánh **đang tích hợp AI thực tế** có độ phủ cao và hữu ích; các cột kế hoạch tương lai thường có tỷ lệ `NaN >= 50%`.

### 122. `AIFrustration` (`QID99`) — Các vấn đề / sự khó chịu gặp phải khi dùng AI
- **Lời dẫn (schema):** "When using AI tools, which of the following problems or frustrations have you encountered? Select all that apply."
  - Dịch: Khi sử dụng công cụ AI, bạn đã gặp phải những vấn đề hoặc sự bực bội nào sau đây? Chọn tất cả đáp án phù hợp.
- **Kiểu:** chọn **nhiều** đáp án (`MC`), nối nhau bằng dấu `;`.
- **Lưu ý:** Trải nghiệm và cảm nhận khó khăn cá nhân khi dùng AI.

### 123. `AIExplain` (`QID84`) — Câu hỏi mở: "vibe coding" có nằm trong công việc chuyên môn không
- **Lời dẫn (schema):** "In your own words, is 'vibe coding' part of your professional development work? For this question, we define vibe coding according to the Wikipedia definition, the process of generating software from LLM prompts."
  - Dịch: Bằng lời văn của riêng bạn, "vibe coding" (tạo phần mềm từ các câu lệnh/prompt LLM) có phải là một phần trong công việc phát triển chuyên nghiệp của bạn không?
- **Kiểu:** văn bản tự do (`TE`) · câu trả lời tự luận ngắn/dài của từng người.

---

## F. AI Agents & triển vọng kỹ năng tương lai (cột 124–139)

### 124. `AIAgents` (`QID85`) — Có sử dụng AI agents trong công việc không
- **Lời dẫn (schema):** "Are you using AI agents in your work (development or otherwise)? AI agents refer to autonomous software entities that can operate with minimal to no direct human intervention using artificial intelligence techniques."
  - Dịch: Bạn có đang sử dụng AI agents (các thực thể phần mềm tự chủ có thể hoạt động với rất ít hoặc không cần sự can thiệp trực tiếp của con người bằng kỹ thuật AI) trong công việc không?
- **Kiểu:** chọn **một** đáp án (`MC`) · phản ánh mức độ áp dụng công nghệ AI agent thực tế trong công việc.

### 125. `AIAgentChange` (`QID83`) — Công cụ AI / AI agents làm thay đổi cách làm việc thế nào
- **Lời dẫn (schema):** "Have AI tools or AI agents changed how you complete development work in the past year?"
  - Dịch: Các công cụ AI hoặc AI agents đã thay đổi cách bạn hoàn thành công việc phát triển trong năm qua như thế nào?
- **Kiểu:** chọn **một** đáp án (`MC`) · đánh giá cảm nhận mức độ thay đổi cách làm việc.

### 126. `AIAgent_Uses` (`QID86`) — Mục đích ngành nghề / tác vụ cụ thể dùng AI agents
- **Lời dẫn (schema):** "What industry purposes or specific tasks are you using AI agents in your development work? Select all that apply from both lists."
  - Dịch: Bạn đang sử dụng AI agents cho những mục đích ngành nghề hoặc tác vụ cụ thể nào trong công việc phát triển?
- **Kiểu:** chọn **nhiều** đáp án (`MC`), nối nhau bằng dấu `;`.
- **Lưu ý:** Chỉ hỏi nhóm có sử dụng AI agents nên tỷ lệ `NaN` sau lọc đối tượng rất cao (`>= 50%`).

### 127. `AgentUsesGeneral` (`QID106`) — Mục đích sử dụng AI agents tổng quát
- **Lời dẫn (schema):** *(để trống trong `schema.csv`)* · đi liền sau `AIAgent_Uses`, ghi nhận nhóm mục đích tổng quát khi dùng AI agents.
- **Kiểu:** chọn **nhiều** đáp án (`MC`) · tỷ lệ `NaN >= 50%`.

### 128. `AIAgentImpact` (`QID87`) — Mức độ đồng ý về tác động của AI agents
- **Lời dẫn (schema):** "To what extent do you agree with the following statements regarding the impact of AI agents on your work as a developer?"
  - Dịch: Bạn đồng ý ở mức độ nào với các nhận định sau về tác động của AI agents đối với công việc lập trình viên của bạn?
- **Kiểu:** ma trận Likert (`Matrix`) · tách thành các cột mức độ đồng ý (`Strongly agree`, `Somewhat agree`, `Neutral`, `Somewhat disagree`, `Strongly disagree`).
- **Lưu ý:** Ý kiến/quan điểm đánh giá chủ quan và có tỷ lệ thiếu dữ liệu cao.

### 129. `AIAgentChallenges` (`QID88`) — Mức độ đồng ý về thách thức của AI agents
- **Lời dẫn (schema):** "To what extent do you agree with the following statements regarding AI agents?"
  - Dịch: Bạn đồng ý ở mức độ nào với các nhận định sau về thách thức khi sử dụng AI agents?
- **Kiểu:** ma trận Likert (`Matrix`) · tách thành các cột mức độ đồng ý tương tự `AIAgentImpact`.
- **Lưu ý:** Ý kiến/quan điểm đánh giá chủ quan.

### 130. `AIAgentKnowledge` (`QID89`) — Công cụ quản lý bộ nhớ / dữ liệu cho AI agents
- **Lời dẫn (schema):** "You indicated you use or develop AI agents as part of your development work. Have you used any of the following tools for AI agent memory or data management in the past year?"
  - Dịch: Bạn đã sử dụng công cụ nào sau đây để quản lý bộ nhớ hoặc dữ liệu cho AI agents trong năm qua?
- **Kiểu:** chọn **nhiều** đáp án (`MC`), nối nhau bằng dấu `;`.
- **Lưu ý:** Chỉ hỏi nhóm nhỏ phát triển/dùng AI agents, đa số dòng dữ liệu là `NaN`.

### 131. `AIAgentKnowWrite` (`QID107`) — Gõ tay: công cụ bộ nhớ / điều phối AI agents
- **Lời dẫn (schema):** "Was the tool or tools for AI agent orchestration or agent frameworks you used in the past year not listed above? Please write them below separated by a comma and space if there are more than one."
  - Dịch: Công cụ quản lý bộ nhớ / điều phối AI agents đã dùng trong năm qua nhưng chưa liệt kê ở trên (lời dẫn trong schema bị lặp từ câu orchestration).
- **Kiểu:** văn bản tự do (`TE`).

### 132. `AIAgentOrchestration` (`QID90`) — Công cụ điều phối / framework cho AI agents
- **Lời dẫn (schema):** "You indicated you use or develop AI agents as part of your development work. Have you used any of the following tools for AI agent orchestration or agent frameworks in the past year?"
  - Dịch: Bạn đã sử dụng công cụ điều phối hoặc framework nào cho AI agents trong năm qua (ví dụ LangChain, LlamaIndex, CrewAI...)?
- **Kiểu:** chọn **nhiều** đáp án (`MC`), nối nhau bằng dấu `;` · tỷ lệ `NaN` rất cao.

### 133. `AIAgentOrchWrite` (`QID102`) — Gõ tay: công cụ điều phối / framework AI agents
- **Lời dẫn (schema):** "Was the tool or tools for AI agent orchestration or agent frameworks you used in the past year not listed above? Please write them below separated by a comma and space if there are more than one."
  - Dịch: Công cụ điều phối / framework AI agents đã dùng trong năm qua nhưng chưa liệt kê ở trên.
- **Kiểu:** văn bản tự do (`TE`).

### 134. `AIAgentObserveSecure` (`QID91`) — Công cụ quan sát, giám sát & bảo mật cho AI agents
- **Lời dẫn (schema):** "You indicated you use or develop AI agents as part of your development work. Have you used any of the following tools for AI agent observability, monitoring or security in the past year?"
  - Dịch: Bạn đã sử dụng công cụ nào để quan sát (observability), giám sát hoặc bảo mật cho AI agents trong năm qua?
- **Kiểu:** chọn **nhiều** đáp án (`MC`), nối nhau bằng dấu `;` · tỷ lệ `NaN` rất cao.

### 135. `AIAgentObsWrite` (`QID103`) — Gõ tay: công cụ giám sát & bảo mật AI agents
- **Lời dẫn (schema):** "Was the tool or tools for AI agent observability, monitoring or security you used in the past year not listed above? Please write them below separated by a comma and a space if there are more than one."
  - Dịch: Công cụ quan sát, giám sát hoặc bảo mật AI agents đã dùng trong năm qua nhưng chưa liệt kê ở trên.
- **Kiểu:** văn bản tự do (`TE`).

### 136. `AIAgentExternal` (`QID92`) — Tác nhân, copilot hoặc trợ lý AI đóng gói sẵn đã dùng
- **Lời dẫn (schema):** "You indicated you use or develop AI agents as part of your development work. Have you used any of the following out-of-the-box agents, copilots or assistants?"
  - Dịch: Bạn đã sử dụng những tác nhân (agents), copilot hoặc trợ lý AI đóng gói sẵn nào sau đây?
- **Kiểu:** chọn **nhiều** đáp án (`MC`), nối nhau bằng dấu `;` · tỷ lệ `NaN` rất cao.

### 137. `AIAgentExtWrite` (`QID104`) — Gõ tay: agent, copilot hoặc trợ lý AI đóng gói sẵn
- **Lời dẫn (schema):** "Was the out-of-the-box agents, copilots or assistants you used in the past year not listed above? Please write them below separated by a comma and a space if there are more than one."
  - Dịch: Các agent, copilot hoặc trợ lý AI đóng gói sẵn đã dùng trong năm qua nhưng chưa liệt kê ở trên.
- **Kiểu:** văn bản tự do (`TE`).

### 138. `AIHuman` (`QID100`) — Tình huống vẫn muốn nhờ con người hỗ trợ khi AI làm được hầu hết việc code
- **Lời dẫn (schema):** "In the future, if AI can do most coding tasks, in which situations would you still want to ask another person for help? Select all that apply."
  - Dịch: Trong tương lai, nếu AI có thể làm hầu hết các tác vụ lập trình, bạn vẫn muốn nhờ người khác hỗ trợ trong những tình huống nào?
- **Kiểu:** chọn **nhiều** đáp án (`MC`), nối nhau bằng dấu `;` · **quan điểm/dự đoán cá nhân**.

### 139. `AIOpen` (`QID93`) — Câu hỏi mở: kỹ năng nào vẫn có giá trị trong 3–5 năm tới
- **Lời dẫn (schema):** "Looking ahead 3–5 years, what skills do you believe will remain valuable for developers even as AI tools become more capable? Please describe."
  - Dịch: Nhìn về 3–5 năm tới, bạn tin rằng những kỹ năng nào sẽ vẫn giữ được giá trị đối với lập trình viên ngay cả khi các công cụ AI ngày càng mạnh mẽ hơn? Hãy mô tả.
- **Kiểu:** văn bản tự do (`TE`) · câu trả lời tự luận mở, quan điểm cá nhân.
