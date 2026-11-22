# Khai báo dùng AI — Nguyễn Minh Nam Hải

| # | Công cụ | Bạn hỏi gì (tóm tắt) | Bạn dùng kết quả thế nào | Bạn có kiểm lại không? Bằng gì? |
|---|---|---|---|---|
| 1 | Claude Code (Claude Opus 5.5) | Đọc `disagreement_log.csv`, so `annotations.xml` của mình với của bạn, đề xuất `verdict` / `guideline_rule` / `action` cho từng dòng và liệt kê những chỗ mình cần sửa. Trong lúc đó AI đã mở xem một số ảnh G11 (S01, S03, S04, S05, S08, D01, D02, D03, D05) để đối chiếu. | Dùng làm gợi ý; tự sửa trên CVAT các dòng đồng ý (D01, D03, D05, S02, S03, S04, S07, S08), export `export_final_v2.zip`. Giữ `occupied = yes` theo quyết định của mình. | Có: mở lại từng ảnh trên CVAT, đối chiếu GUIDE §3–§4, thảo luận với bạn review, chạy lại `cabin_check check` trên `export_final_v2.zip`. |
