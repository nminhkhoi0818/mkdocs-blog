## Pass by Value and Pass by Reference in Javascript

- Tham trị: String, Number, Boolean
- Tham chiếu: Object, Array

## What's the difference between a variable that is: `null`, `undefined` or undeclared?

- Khai báo mà không điền giá trị undefined
- Khai báo mà được gán giá trị, giá trị đó chính là null

## What's the difference between `inline` and `inline-block`?

- Block: chiếm toàn bộ width nếu không được set
- Inline: các items sẽ nằm cùng một dòng, không thể set height và width
- Inline-block: các items nằm trên một dòng nhưng có thể set height và width

## Describe the difference between a cookie, `sessionStorage` and `localStorage`.

## LocalStorage

- localStorage giúp lưu trữ dữ liệu vĩnh viễn trên trình duyệt (trừ khi xóa cache)
- Có 2 trường là: key, value
- Lưu trữ dữ liệu trước đó người dùng, settings người dùng (theme)

```
window.LocalStorage.setItem('name', 'value');
window.LocalStorage.getItem('name');
window.LocalStorage.clear();
window.LocalStorage.removeItem('name');
```

- Vấn đề không bảo mật, có thể dễ dàng lưu, lấy và sửa

## SessionStorage

- sessionStorage cũng tương tự localStorage nhưng dữ liệu sẽ mất khi đóng trình duyệt
- Có thể bị cross-site scripting vì thế không nên lưu trữ các thông tin nhạy cảm như password

## Cookie

- Cookie là những tập tin một trang web gửi tới người dùng. Cookie được sử dụng phổ biến để lưu lại phiên đăng nhập
- Request gửi đi server được gửi kèm cookie
- HtttpOnly, code JS ứng dụng bên thứ 3 không thể lấy được dữ liệu cookie
- Cookie có thời gian expire

## BEM (Block, Element, Modifier)

```
<form class="form form--theme-xmas form--simple">
  <input class="form__input" type="text" />
  <input
    class="form__submit form__submit--disabled"
    type="submit" />
</form>
```

## Truthy, Falsy là gì?

- Truthy là những giá trị mà khi encounter in Boolean context thì nó bằng true.
- Falsy là những giá trị mà khi encounter in Boolean context thì nó bằng false.

## Thẻ Span và Div khác nhau như thế nào? Kể tên các thẻ block và inline?

- span là thẻ inline, thường dùng để chứa dữ liệu
- div là thẻ block, thường dùng để phân nội dung thành các đoạn

## Thuộc tính data- là gì?

- Lưu trữ thêm thông tin vào element

## Nguyên lý hoạt động của stack và queue. Các ứng dụng?

- Event loop

## Xử lý ngoại lệ?

- Catch thì nhận được trong exception, làm gì với exception đó. Làm 2 thứ: log lại cái lỗi đó, đẩy lên cái kho lưu trữ, bắn về cái lỗi slack. Return cái lỗi cho người dùng, viết lỗi cho dễ hiểu vì nếu bắn lỗi ra trong code thì các người dùng biết code sẽ biết hệ thống hoạt động ra sao.
- Stack trace áp dụng nguyên lý của stack

## Trong các thuật toán thằng nào nhanh nhất?

- Không có, trường hợp tệ nhất, trung bình, tốt nhất
- Quick sort độ phức tạp O(nlog(n))
- Bubble sort trường hợp best thì O(n)

## Độ phức tạp là gì?

- Độ phức tạp thuật toán là định lượng tương đối số phép toán mà máy tính phải thực hiện.

## Relative và absolute?

- Cho hai thằng absolute nó có mối quan hệ cha con
- Relative dựa vào vị trí ban đầu của nó

## DOM và DOM ảo?

- DOM: Ông Browser nhận được file HTML. Browser dựa trên cái quy chuẩn ông đó dịch HTML thành DOM, dựa vào quy chuẩn W3C tạo ra mô hình dạng cây
- Các dự án lớn, DOM Tree rất lớn, mỗi khi DOM đổi phải tính toán lại CSS -> Tốc độ rendering chậm
- Khi React render, React tạo DOM ảo. Khi có sự thay đổi của state, tạo ra DOM đổi. Chạy thuật toán so sánh giữa DOM cũ và mới để tìm ra thành phần được cập nhật. Sau khi tiến hành so sánh, ReactDOM render lại các thành phần cần cập nhật lên DOM thật.

## Client side và server side?

- CSR (Client side rendering) - SPA (Single Page Application)
- SSR (Server side rendering) - MPA (Multiple Page Application)
