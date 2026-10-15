# Quẹt Vote Sao

Mini app: khách quẹt thẻ (kiểu Tinder) chọn thử thách mỗi ngày, hoàn thành để nhận lượt vote cho nghệ sĩ.

Chạy: mở `index.html` (không cần build). Link GitHub Pages: https://bobo2912.github.io/quet-vote-sao/

## Hai nhóm khách hàng
| | All user | Upgrade |
|---|---|---|
| Điều kiện | Mọi khách | Gửi tiết kiệm từ 1.000.000đ, kỳ hạn từ 6 tháng |
| Lượt nhận thử thách | 5/ngày (cuối tuần +2), reset 00:00 | Không giới hạn |
| Vote mỗi thử thách | 1 | 2–5 |
| Giờ vàng / ngày vàng / thẻ vàng | Không | Có, cộng dồn tối đa ×3 |
| Combo đủ 3 nhóm | Không | +3 |

- **Trần chung: 50 vote/ngày** cho mọi khách, kể cả khi có hệ số.
- Tối đa 3 thử thách làm dở cùng lúc (chống ôm thẻ chờ giờ vàng).
- Upgrade: phi tài chính tối đa 10 vote/ngày.
- All user thấy xen 3 thẻ Upgrade bị khóa trong bộ bài; quẹt phải để mở màn hình mở khóa, quẹt trái không mất lượt.
- Tất toán sổ mở khóa trước hạn → mất quyền Upgrade ngay.

## Kho 100 thử thách
Sửa trong `challenges.js` (app đọc trực tiếp). `challenges.csv` là bản để mở bằng Excel/Google Sheets.

| | Phi tài chính | Tài chính hằng ngày | Tài chính theo phân khúc | Tổng |
|---|---|---|---|---|
| All user (1 vote) | 25 | 12 | 8 | 45 |
| Upgrade (2–5 vote) | 10 | 25 | 20 | 55 |

Phân khúc: Gen Z, Gia đình, Dân văn phòng, Hộ kinh doanh, Mê du lịch.

Bộ thẻ mỗi ngày: All user 12 thẻ (6 phi tài chính, 4 hằng ngày, 2 phân khúc) + 3 thẻ Upgrade bị khóa. Upgrade: toàn bộ thẻ hợp phân khúc, xếp 2 thẻ Upgrade xen 1 thẻ All user.

Các con số chỉnh tại khối `CFG` đầu script trong `index.html`.

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
