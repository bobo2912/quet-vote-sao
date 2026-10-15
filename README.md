# Quẹt Vote Sao

Mini app: khách quẹt thẻ (kiểu Tinder) chọn thử thách mỗi ngày, hoàn thành để nhận lượt vote cho nghệ sĩ.

Chạy: mở `index.html` (không cần build). Link GitHub Pages: https://bobo2912.github.io/quet-vote-sao/

## Hai nhóm khách hàng
| | All user | Upgrade |
|---|---|---|
| Điều kiện | Mọi khách | Gửi tiết kiệm từ 1.000.000đ, kỳ hạn từ 6 tháng |
| Lượt nhận thử thách | 5/ngày (cuối tuần +2), reset 00:00 | Không giới hạn |
| Vote mỗi thử thách | 1 | Thêm thử thách 2–5 vote |

- Mới vào cứ quẹt; hết lượt mới hiện màn mời Upgrade để quẹt không giới hạn.
- Bộ thẻ quay vòng liên tục, không hiện số thẻ còn lại; thẻ đã nhận không quay lại trong ngày.
- **Trần: 50 vote/ngày** cho mọi khách.
- Tối đa 5 thử thách làm dở cùng lúc.
- Sự kiện áp dụng **mọi khách**: giờ vàng (12h, 20h) tài chính ×2, ngày vàng (15 hằng tháng, 10/10, 11/11) ×2, thẻ vàng ×2, cộng dồn tối đa ×3; combo đủ 3 nhóm +3.
- Phi tài chính tối đa 10 vote/ngày.
- Tất toán sổ mở khóa trước hạn → mất quyền Upgrade ngay.

## Màn Cài đặt demo (nút bánh răng)
Chỉnh trực tiếp: lượt/ngày All user, lượt thêm cuối tuần, số thử thách làm dở, trần vote/ngày, trần phi tài chính, hệ số tối đa, thưởng combo, điều kiện mở khóa. Kèm đổi phân khúc, giờ máy chủ và nút thử gian lận. Giá trị mặc định nằm ở `DEFAULT_CFG` trong `index.html`.

## Kho 100 thử thách
Sửa trong `challenges.js` (app đọc trực tiếp). `challenges.csv` là bản để mở bằng Excel/Google Sheets.

| | Phi tài chính | Tài chính hằng ngày | Tài chính theo phân khúc | Tổng |
|---|---|---|---|---|
| All user (1 vote) | 25 | 12 | 8 | 45 |
| Upgrade (2–5 vote) | 10 | 25 | 20 | 55 |

Phân khúc: Gen Z, Gia đình, Dân văn phòng, Hộ kinh doanh, Mê du lịch.

Bộ thẻ: All user quay vòng các thẻ All user hợp phân khúc; Upgrade quay vòng thêm thẻ Upgrade (2 thẻ Upgrade xen 1 thẻ All user).

## Chống gian lận
- Bộ thẻ sinh từ mã KH + ngày + hạng trên máy chủ (không reroll được); giờ theo máy chủ.
- Chỉ tính giao dịch core xác nhận thành công, sau lúc nhận thẻ, đủ giá trị và số lượng.
- Mỗi mã giao dịch dùng 1 lần, kể cả sổ mở khóa (idempotency); loại chuyển cho chính mình, chuyển vòng.
- Hoàn/hủy giao dịch → thu hồi vote; mời bạn chỉ tính khi bạn eKYC + đạt điều kiện.

## Cài như app (PWA)
- **iPhone (Safari):** Chia sẻ → *Thêm vào MH chính*.
- **Android (Chrome):** menu ⋮ → *Cài đặt ứng dụng*.

Mỗi lần cập nhật code, đổi `VERSION` trong `sw.js`.

> Bản prototype: giao dịch, kiểm tra phía máy chủ và tên nghệ sĩ là giả lập; dữ liệu demo lưu localStorage.
