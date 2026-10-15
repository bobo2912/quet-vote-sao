# Quẹt Vote Sao

Mini app: khách quẹt thẻ (kiểu Tinder) chọn thử thách mỗi ngày, hoàn thành giao dịch để nhận lượt vote cho nghệ sĩ.

Chạy: mở `index.html` trong trình duyệt (một file, không cần build). Bật GitHub Pages để có link.

## Thử thách
| Loại | Ví dụ | Vote gốc |
|---|---|---|
| Phi tài chính | Xem menu, xem video, đăng nhập, chia sẻ, mời bạn | 1 (tối đa 2/ngày) |
| Tài chính hằng ngày | Chuyển tiền từ 50k, nạp ĐT 100k, hóa đơn, tiết kiệm từ 6 tháng | 2–3 |
| Tài chính theo phân khúc | Vé phim, data, vé concert, QR… | 3 |

## Giới hạn
- Nhận tối đa 3 thử thách/ngày (cuối tuần 5), trần 30 vote/ngày, 20 vote/nghệ sĩ/ngày.

## Thưởng
- Giờ vàng 12–13h, 20–21h: tài chính ×2 · Ngày vàng (15 hằng tháng, 10/10, 11/11): ×2 · Thẻ vàng ×2 · Combo đủ 3 loại +2 · Hệ số tối đa ×3.

## Chống gian lận
- Bộ thẻ sinh từ mã KH + ngày trên máy chủ (không reroll được); giờ theo máy chủ.
- Chỉ tính giao dịch core xác nhận thành công, sau lúc nhận thử thách, đủ giá trị tối thiểu.
- Mỗi mã giao dịch nhận thưởng 1 lần (idempotency); loại chuyển cho chính mình, chuyển vòng.
- Hoàn/hủy giao dịch, tất toán tiết kiệm sớm → thu hồi vote; mời bạn chỉ tính khi bạn eKYC + giao dịch đầu.

> Bản prototype: giao dịch, kiểm tra phía máy chủ và tên nghệ sĩ là giả lập; dữ liệu demo lưu localStorage.

## Cài như app (PWA)
Mở link GitHub Pages trên điện thoại:
- **iPhone (Safari):** nút Chia sẻ → *Thêm vào MH chính*.
- **Android (Chrome):** menu ⋮ → *Cài đặt ứng dụng* / *Thêm vào màn hình chính*.

Khi mở từ màn hình chính, app chạy toàn màn hình (ẩn bảng demo) và vẫn mở được khi mất mạng. Cập nhật code thì đổi `VERSION` trong `sw.js`.
