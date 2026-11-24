# Đề xuất giữ / bỏ cột 87–139 

**Quy ước:** *Giữ* = dùng làm đặc trưng huấn luyện/phân tích; *Bỏ* = loại bỏ; *Giữ có chọn lọc* = chỉ giữ chiều dữ liệu phản ánh hành vi/công cụ thực tế hiện tại (`*HaveWorkedWith` hoặc các cột trạng thái đang dùng hiện tại), loại các chiều nguyện vọng tương lai (`*WantToWorkWith` / kế hoạch 3–5 năm), cột trùng lặp (`*Admired`) và các cột con có tỷ lệ thiếu dữ liệu quá cao sau khi lọc đối tượng.

**Tiêu chí lọc (thống nhất với nhóm cột 2–86):**
1. **Bỏ toàn bộ câu hỏi quan điểm, thái độ, cảm nhận, đánh giá chủ quan hoặc dự đoán tương lai cá nhân** (mức độ ủng hộ AI, độ tin cậy AI, mức hài lòng/bực bội, ý kiến về tác động/thách thức AI agents, tình huống hỏi con người...).
2. **Bỏ toàn bộ ô nhập văn bản tự do (`*Entry`, `*Write`, `AIExplain`, `AIOpen`)** vì dữ liệu rời rạc, nhiều nhiễu chính tả, tỷ lệ thiếu dữ liệu rất cao (`> 90%`) và khó chuẩn hóa đồng nhất.
3. **Bỏ các cột lựa chọn nhị phân điều hướng (`*Choice`) và các cột trùng lặp (`*Admired`)**, tương tự nhóm `LanguageChoice` / `LanguageAdmired` ở phần 2–86.
4. **Đánh giá tỷ lệ `NaN >= 50%` trên tập sau khi lọc đối tượng (16.991 / 15.160 dòng)** để không bỏ nhầm các đặc trưng công nghệ thực tế có ý nghĩa (như `WebframeHaveWorkedWith`) và loại bỏ các cột con của câu hỏi ma trận có tỷ lệ thiếu dữ liệu vượt ngưỡng.

**Tổng kết (theo 53 dòng trong `schema.csv` từ cột 87 đến 139):**
- **Giữ / Giữ có chọn lọc:** **8** nhóm cột (`Webframe`, `DevEnvs`, `OpSys`, `OfficeStackAsync`, `AIModels`, `AISelect`, `AITool`, `AIAgents`) — khi áp dụng trên bảng dữ liệu đã tách cột ma trận, chỉ giữ các cột con phản ánh trạng thái/công cụ đang dùng thực tế và có tỷ lệ `NaN < 50%` sau lọc đối tượng (loại bỏ các cột con `*WantToWorkWith`, `*Admired`, kế hoạch 3–5 năm và các cột con có `NaN >= 50%`).
- **Bỏ trực tiếp:** **45** cột/nhóm cột (cộng thêm các cột con sinh ra từ câu hỏi ma trận có tỷ lệ `NaN >= 50%` sau lọc đối tượng).

---

## Bảng đề xuất chi tiết từng cột (87–139 theo `schema.csv`)

| # (schema) | Cột (`qname`) | Kiểu | Giữ / Bỏ | Lý do chi tiết & cột con áp dụng |
| :---: | :--- | :---: | :---: | :--- |
| 87 | `PlatformWantEntry` | `TE` | **Bỏ** | Văn bản tự do gõ tay nền tảng muốn dùng; nhiễu, tỷ lệ thiếu dữ liệu rất cao. |
| 88 | `WebframeChoice` | `MC` | **Bỏ** | Chỉ hỏi `Yes/No` có dùng web framework hay không; thông tin trùng lặp với cột danh sách web framework đã dùng. |
| 89 | `Webframe` | `Matrix` | **Giữ (chọn lọc)** | Giữ chiều đã dùng thực tế (`*HaveWorkedWith`, nếu `NaN < 50%` sau lọc đối tượng); bỏ `*WantToWorkWith` (nguyện vọng) và `*Admired` (trùng lặp). |
| 90 | `WebframeHaveEntry` | `TE` | **Bỏ** | Văn bản tự do gõ tay web framework đã dùng, nhiều nhiễu và khó chuẩn hóa. |
| 91 | `WebframeWantEntry` | `TE` | **Bỏ** | Văn bản tự do gõ tay web framework muốn dùng trong tương lai. |
| 92 | `DevEnvsChoice` | `MC` | **Bỏ** | Câu hỏi điều hướng `Yes/No` có dùng môi trường phát triển/AI code editor không; trùng thông tin với `DevEnvs`. |
| 93 | `DevEnvs` | `Matrix` | **Giữ (chọn lọc)** | Giữ các cột con phản ánh IDE/AI editor dùng thực tế (`*HaveWorkedWith`, kiểm tra `NaN < 50%` sau lọc đối tượng); bỏ `*WantToWorkWith` và `*Admired`. |
| 94 | `DevEnvHaveEntry` | `TE` | **Bỏ** | Văn bản tự do gõ tay môi trường phát triển / AI editor đã dùng. |
| 95 | `DevEnvWantEntry` | `TE` | **Bỏ** | Văn bản tự do gõ tay môi trường phát triển / AI editor muốn dùng. |
| 96 | `SOTags` | `Matrix` | **Bỏ** | Tag mới nổi trên Stack Overflow thiên về mức độ quan tâm xu hướng diễn đàn, độ phủ thấp và ít liên hệ trực tiếp với mức lương. |
| 97 | `SOTagsHaveEntry` | `TE` | **Bỏ** | Văn bản tự do gõ tay tag mới trên Stack Overflow đã dùng. |
| 98 | `SOTagsWant Entry` | `TE` | **Bỏ** | Văn bản tự do gõ tay tag mới trên Stack Overflow muốn dùng. |
| 99 | `OpSys` | `Matrix` | **Giữ** | Hệ điều hành làm việc chính; giữ các cột con có độ phủ đạt ngưỡng (`NaN < 50%` sau lọc đối tượng), bỏ cột con thiếu nhiều. |
| 100 | `OfficeStackAsync` | `Matrix` | **Giữ (chọn lọc)** | Công cụ quản lý công việc cộng tác/tài liệu mã nguồn; giữ chiều đang dùng thực tế (`*HaveWorkedWith`, `NaN < 50%` sau lọc), bỏ `*WantToWorkWith` và `*Admired`. |
| 101 | `OfficeStackHaveEntry` | `TE` | **Bỏ** | Văn bản tự do gõ tay công cụ quản lý công việc/tài liệu đã dùng. |
| 102 | `OfficeStackWantEntry` | `TE` | **Bỏ** | Văn bản tự do gõ tay công cụ quản lý công việc/tài liệu muốn dùng. |
| 103 | `CommPlatform` | `Matrix` | **Bỏ** | Nền tảng cộng đồng/mạng xã hội (Discord, Reddit...) mang tính thói quen giao tiếp cá nhân, liên hệ yếu với thu nhập. |
| 104 | `CommPlatformHaveEntr` | `TE` | **Bỏ** | Văn bản tự do gõ tay nền tảng cộng đồng đã dùng. |
| 105 | `CommPlatformWantEntr` | `TE` | **Bỏ** | Văn bản tự do gõ tay nền tảng cộng đồng muốn dùng. |
| 106 | `AIModelsChoice` | `MC` | **Bỏ** | Câu hỏi điều hướng `Yes/No` có tích hợp/dùng mô hình LLM không; trùng thông tin với `AIModels`. |
| 107 | `AIModels` | `Matrix` | **Giữ (chọn lọc)** | Giữ chiều mô hình LLM đã dùng thực tế (`*HaveWorkedWith`, nếu `NaN < 50%` sau lọc đối tượng); bỏ `*WantToWorkWith`, `*Admired` và các cột con vượt ngưỡng `NaN`. |
| 108 | `AIModelsHaveEntry` | `TE` | **Bỏ** | Văn bản tự do gõ tay mô hình LLM đã dùng. |
| 109 | `AIModelsWantEntry` | `TE` | **Bỏ** | Văn bản tự do gõ tay mô hình LLM muốn dùng. |
| 110 | `SOAccount` | `MC` | **Bỏ** | Có tài khoản Stack Overflow hay không là thông tin tài khoản diễn đàn, không phản ánh năng lực hay mức lương. |
| 111 | `SOVisitFreq` | `MC` | **Bỏ** | Tần suất truy cập Stack Overflow là thói quen tra cứu cá nhân. |
| 112 | `SODuration` | `MC` | **Bỏ** | Thời gian dùng tài khoản Stack Overflow kém chính xác hơn nhiều so với `WorkExp` và `YearsCode`. |
| 113 | `SOPartFreq` | `MC` | **Bỏ** | Tần suất tham gia hỏi/đáp/vote trên Stack Overflow là hành vi cộng đồng cá nhân. |
| 114 | `SO_Dev_Content` | `MC` | **Bỏ** | Định dạng nội dung thay thế Q&A ưa thích là sở thích cá nhân. |
| 115 | `SOComm` | `MC` | **Bỏ** | Tự đánh giá có thuộc cộng đồng Stack Overflow hay không là cảm nhận chủ quan. |
| 116 | `SOFriction` | `MC` | **Bỏ** | Tần suất vào Stack Overflow để sửa lỗi do công cụ AI gây ra là trải nghiệm cá nhân khi gỡ lỗi. |
| 117 | `AISelect` | `MC` | **Giữ** | Phản ánh hành vi áp dụng công cụ AI thực tế trong quy trình phát triển (đang dùng, dự định dùng, không dùng). |
| 118 | `AISent` | `MC` | **Bỏ** | Mức độ thiện cảm/ủng hộ dùng AI là quan điểm cá nhân. |
| 119 | `AIAcc` | `MC` | **Bỏ** | Mức độ tin tưởng độ chính xác của đầu ra AI là đánh giá chủ quan. |
| 120 | `AIComplex` | `MC` | **Bỏ** | Đánh giá khả năng xử lý tác vụ phức tạp của công cụ AI là nhận định chủ quan. |
| 121 | `AITool` | `Matrix` | **Giữ (chọn lọc)** | Chỉ giữ các cột con phản ánh khâu **đang tích hợp AI thực tế** hiện nay có `NaN < 50%` sau lọc đối tượng; bỏ các cột con dự định 3–5 năm tới hoặc có `NaN >= 50%`. |
| 122 | `AIFrustration` | `MC` | **Bỏ** | Những khó khăn/bực bội gặp phải khi dùng AI là cảm nhận và trải nghiệm cá nhân. |
| 123 | `AIExplain` | `TE` | **Bỏ** | Câu hỏi mở văn bản tự do giải thích về "vibe coding". |
| 124 | `AIAgents` | `MC` | **Giữ** | Phản ánh việc có đang áp dụng AI agents tự chủ trong công việc thực tế hay không (kiểm tra `NaN < 50%` sau lọc đối tượng). |
| 125 | `AIAgentChange` | `MC` | **Bỏ** | Cảm nhận mức độ thay đổi cách làm việc do AI/AI agents trong năm qua là đánh giá chủ quan. |
| 126 | `AIAgent_Uses` | `MC` | **Bỏ** | Tác vụ cụ thể dùng AI agents chỉ hỏi nhóm nhỏ dùng agent, tỷ lệ `NaN >= 50%` sau lọc. |
| 127 | `AgentUsesGeneral` | `MC` | **Bỏ** | Cột mục đích dùng agent bổ sung, tỷ lệ `NaN >= 50%` sau lọc. |
| 128 | `AIAgentImpact` | `Matrix` | **Bỏ** | Thang đo đồng ý về tác động của AI agents là quan điểm chủ quan và tỷ lệ `NaN >= 50%`. |
| 129 | `AIAgentChallenges` | `Matrix` | **Bỏ** | Thang đo đồng ý về thách thức của AI agents là quan điểm chủ quan và tỷ lệ `NaN >= 50%`. |
| 130 | `AIAgentKnowledge` | `MC` | **Bỏ** | Công cụ quản lý bộ nhớ cho AI agents thuộc tập con rất hẹp, tỷ lệ `NaN` rất cao. |
| 131 | `AIAgentKnowWrite` | `TE` | **Bỏ** | Văn bản tự do gõ tay công cụ bộ nhớ/điều phối AI agents. |
| 132 | `AIAgentOrchestration` | `MC` | **Bỏ** | Công cụ điều phối AI agents thuộc tập con rất hẹp, tỷ lệ `NaN` rất cao. |
| 133 | `AIAgentOrchWrite` | `TE` | **Bỏ** | Văn bản tự do gõ tay công cụ điều phối AI agents. |
| 134 | `AIAgentObserveSecure` | `MC` | **Bỏ** | Công cụ giám sát/bảo mật AI agents thuộc tập con rất hẹp, tỷ lệ `NaN` rất cao. |
| 135 | `AIAgentObsWrite` | `TE` | **Bỏ** | Văn bản tự do gõ tay công cụ giám sát/bảo mật AI agents. |
| 136 | `AIAgentExternal` | `MC` | **Bỏ** | Trợ lý/copilot AI agents đóng gói sẵn thuộc tập con hẹp, tỷ lệ `NaN` rất cao. |
| 137 | `AIAgentExtWrite` | `TE` | **Bỏ** | Văn bản tự do gõ tay trợ lý/copilot AI agents đóng gói sẵn. |
| 138 | `AIHuman` | `MC` | **Bỏ** | Tình huống giả định trong tương lai vẫn muốn nhờ người hỗ trợ là quan điểm/dự đoán cá nhân. |
| 139 | `AIOpen` | `TE` | **Bỏ** | Câu hỏi mở văn bản tự do dự đoán kỹ năng lập trình viên quan trọng trong 3–5 năm tới. |

---

## Code loại bỏ cột nhóm 87–139 & kiểm tra tỷ lệ `NaN` sau lọc đối tượng

Đoạn code dưới đây lọc cột theo cả **tên cột chính xác** lẫn **tiền tố/hậu tố cột ma trận**, in ra danh sách cột bị loại để người làm đối chiếu trực tiếp, và tính tỷ lệ `NaN` của các cột giữ lại sau khi lọc đối tượng (ví dụ điều kiện lọc đối tượng của nhóm):

```python
import pandas as pd

# 1. Đọc dữ liệu gốc (chỉnh đường dẫn nếu file đặt ở thư mục khác)
df = pd.read_csv("results.csv", low_memory=False)
print(f"Ban đầu: {df.shape[0]} hàng x {df.shape[1]} cột")

# 2. Danh sách tên cột chính xác cần bỏ trong nhóm 87–139
exact_drop_cols_87_139 = [
    "PlatformWantEntry",
    "WebframeChoice", "WebframeHaveEntry", "WebframeWantEntry",
    "DevEnvsChoice", "DevEnvHaveEntry", "DevEnvWantEntry",
    "SOTagsHaveEntry", "SOTagsWant Entry",
    "OfficeStackHaveEntry", "OfficeStackWantEntry",
    "CommPlatformHaveEntr", "CommPlatformWantEntr",
    "AIModelsChoice", "AIModelsHaveEntry", "AIModelsWantEntry",
    "SOAccount", "SOVisitFreq", "SODuration", "SOPartFreq",
    "SO_Dev_Content", "SOComm", "SOFriction",
    "AISent", "AIAcc", "AIComplex", "AIFrustration", "AIExplain",
    "AIAgentChange", "AIAgent_Uses", "AgentUsesGeneral",
    "AIAgentKnowledge", "AIAgentKnowWrite",
    "AIAgentOrchestration", "AIAgentOrchWrite",
    "AIAgentObserveSecure", "AIAgentObsWrite",
    "AIAgentExternal", "AIAgentExtWrite",
    "AIHuman", "AIOpen",
]

# 3. Tiền tố các nhóm câu hỏi Matrix cần bỏ hẳn và hậu tố nguyện vọng/trùng lặp cần bỏ
drop_prefixes_87_139 = (
    "SOTags",
    "CommPlatform",
    "AIAgentImpact",
    "AIAgentChallenges",
)
redundant_suffixes = ("WantToWorkWith", "Admired")
tech_matrix_prefixes = ("Webframe", "DevEnvs", "OpSys", "OfficeStackAsync", "AIModels", "AITool")

cols_to_drop = []
for col in df.columns:
    if col in exact_drop_cols_87_139:
        cols_to_drop.append(col)
    elif col.startswith(drop_prefixes_87_139):
        cols_to_drop.append(col)
    elif col.startswith(tech_matrix_prefixes) and col.endswith(redundant_suffixes):
        cols_to_drop.append(col)

df_after_87_139 = df.drop(columns=cols_to_drop).copy()
print(f"Đã bỏ {len(cols_to_drop)} cột thuộc nhóm 87–139:")
print(cols_to_drop)
print(f"Sau bước bỏ cột nhóm 87–139: {df_after_87_139.shape[0]} hàng x {df_after_87_139.shape[1]} cột")

# 4. Ví dụ kiểm tra tỷ lệ NaN sau bước lọc đối tượng (chỉnh điều kiện lọc theo đúng step1 của nhóm)
# df_filtered = df_after_87_139[...].copy()
# nan_ratios = df_filtered.isna().mean().sort_values(ascending=False)
# high_nan_cols = nan_ratios[nan_ratios >= 0.50].index.tolist()
# print("Các cột có tỷ lệ NaN >= 50% sau lọc đối tượng:", high_nan_cols)
```
