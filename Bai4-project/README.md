# Bai4-project — sơ đồ Mermaid (.mmd)

Nguồn và bản render cho 3 sơ đồ của Bài 4. Cấu trúc thư mục theo mục N của
`Bai4-Ke-hoach-thiet-ke-OOD.md`.

```
Bai4-project/
├── 02-domain-model/
│   ├── domain-model.mmd          ← nguồn Mermaid
│   ├── domain-model.svg          ← bản vẽ, dán vào báo cáo (nét, phóng to được)
│   └── domain-model.png          ← bản vẽ, dán vào slide
└── 04-design-class-diagram/
    ├── design-class-diagram.mmd
    ├── design-class-diagram.svg
    ├── design-class-diagram.png
    ├── sequence-placeOrder.mmd
    ├── sequence-placeOrder.svg
    └── sequence-placeOrder.png
```

## Nguồn gốc từng file

| File | Nguồn | Ghi chú |
|---|---|---|
| `domain-model.mmd` | mục **F.1** của plan gốc, nguyên văn | Đã có sẵn trong plan |
| `design-class-diagram.mmd` | mục **H.2** của plan gốc, nguyên văn | Đã có sẵn trong plan |
| `sequence-placeOrder.mmd` | **viết mới** từ luồng text ở mục **H.3** | H.3 chỉ có text, chưa có Mermaid |

`sequence-placeOrder.mmd` bám đúng 5 bước và 2 nhánh lỗi của H.3, không thêm
bước nào. Chỗ nào H.3 không nói rõ thì sơ đồ cũng để trống — xem mục dưới.

## Bốn điểm NEED REVIEW chạm vào các sơ đồ này

Cố ý **không tự sửa**. Nhóm chốt theo mục A.5 của file kế hoạch.

| Mã | Ảnh hưởng | Cách nói tạm |
|---|---|---|
| **NR-1** | `domain-model.mmd` vẽ `1..*` theo BR2, nhưng H.3 tạo `new Order()` rồi mới `addOrderLine` → có lúc Order 0 dòng | "Đơn luôn có ít nhất một dòng khi vào quy trình" |
| **NR-2** | Hướng điều hướng `Customer → Order` mâu thuẫn giữa G.2 / H.2 / H.4. Cả hai file giữ nguyên như H.2 | Chỉ nói multiplicity `1 — 0..*`, không nói hướng |
| **NR-3** | `sequence-placeOrder.mmd` **không** vẽ `decreaseStock` chi tiết, vì H.3 không nói reserve trừ kho bằng cách nào | "Reserve = giữ hàng tạm; release = trả lại" |
| **NR-5** | `reserveStock` trả `boolean` nhưng H.3 không xử lý nhánh `false` — sơ đồ cũng không vẽ nhánh đó | "Có khoảng hở giữa check và reserve; đây là hạn chế của nhóm" |

Hai điểm nữa nằm trong `design-class-diagram.mmd` nhưng chỉ là chuyện vẽ/nói,
đã ghi chú trong file: **NR-8** (`Order ..> OrderStatus` nên là association
chứ không phải dependency — trên slide đừng highlight) và **NR-9**
(`Money`, `PaymentInfo` dùng nhưng không khai báo — gọi là "kiểu dữ liệu hỗ trợ").

Các ghi chú này nằm trong `.mmd` dưới dạng `%%` nên **không hiện ra hình**.

## Tự render lại

Cần `mermaid-cli` (đã có sẵn trên máy này, `mmdc` 11.16.0):

```bash
mmdc -i 02-domain-model/domain-model.mmd -o 02-domain-model/domain-model.svg
mmdc -i 02-domain-model/domain-model.mmd -o 02-domain-model/domain-model.png -b white -s 2
```

`-s 2` là scale gấp đôi cho slide. `-b white` để nền trắng thay vì trong suốt.

Hai cách xem nhanh khác, không cần cài gì:

- Dán nội dung `.mmd` vào <https://mermaid.live>
- Đổi tên thành `.md` và bọc trong ` ```mermaid ` — GitHub tự render

## Còn thiếu

Plan mục N định nghĩa 8 thư mục. Hiện có 2:

```
01-requirement-analysis/     00-checklist.md, business-analysis.md        ← Bảo
02-domain-model/             domain-model.md, orderline-analysis.md       ← Tín   (đã có .mmd)
03-responsibility-analysis/  responsibility-*.md, god-class-check.md      ← Khoa
04-design-class-diagram/     design-class-diagram.md                       ← Khang (đã có .mmd)
05-design-comparison/        design-comparison.md                          ← Khoa
06-peer-review/              peer-review-matrix.md, changes-after-review.md
07-report/                   report.md / .docx                             ← Vọng
08-presentation/             slides, qa-bank.md                            ← Vọng
```

Sáu thư mục còn lại là phần viết của từng người — xem
`../Bai4-WORK-BREAKDOWN.md` mục 2 để biết task nào tạo file nào.
