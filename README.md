# PreservesPitch for Youtube
Tính năng **`preservesPitch = false`** trên thẻ `<video>` của HTML5 dùng để điều khiển cách âm thanh thay đổi khi bạn chỉnh tốc độ phát (`playbackRate`).

* **Khi để mặc định (`true`):** YouTube sẽ tự động giữ nguyên cao độ giọng nói/âm nhạc dù bạn có chỉnh tốc độ phát lên 1.5x hay 2x (tránh tình trạng giọng bị bóp méo thành giọng sóc chuột).
* **Khi đặt thành `false`:** Cao độ của âm thanh sẽ thay đổi trực tiếp theo tốc độ phát (tăng tốc độ thì giọng sẽ bị cao và nhanh hơn, giảm tốc độ thì giọng sẽ trầm và chậm lại — giống như hiệu ứng tua nhanh/chậm của băng cassette cũ).

### Cách áp dụng `preservesPitch = false` cho YouTube bằng Console:

Nếu bạn muốn trải nghiệm hiệu ứng này trên một video YouTube bất kỳ, bạn có thể làm theo các bước sau:

1. Mở video YouTube cần xem trên trình duyệt máy tính.
2. Nhấn phím `F12` (hoặc chuột phải chọn **Inspect / Kiểm tra**) rồi chuyển sang tab **Console**.
3. Dán đoạn mã sau vào và nhấn `Enter`: (nếu console không cho paste thì ghi 'allow pasting' trước khi dán)

```javascript
const video = document.querySelector('video');
if (video) {
    video.preservesPitch = false;
    video.mozPreservesPitch = false;    // Cho một số trình duyệt cũ / Firefox
    video.webkitPreservesPitch = false; // Cho Safari / Chrome cũ
    console.log("Đã tắt preservesPitch thành công!");
}

```

4. Sau đó, mỗi khi bạn thay đổi tốc độ phát trên YouTube (ví dụ chỉnh lên `1.25x` hoặc `1.5x`), âm thanh sẽ thay đổi cả về độ cao lẫn tốc độ.

*Lưu ý:* Mỗi khi chuyển sang video khác hoặc tải lại trang (F5), thẻ video sẽ được tạo mới và bạn sẽ cần chạy lại đoạn mã trên hoặc cài các tiện ích mở rộng (Userscript như Tampermonkey) để tự động hóa việc này nếu muốn dùng thường xuyên.
