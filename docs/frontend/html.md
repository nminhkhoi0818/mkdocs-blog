## HTML

HTML (Hyper Text Markup Language) là ngôn ngữ markup dùng để tạo nên những trang Web. HTML là thành phần định nghĩa cấu trúc của một trang Web.

```
<!DOCTYPE html>
```

Khai báo này không phải là HTML tag. Cho phép trình duyệt biết Web đang sử dụng markup language nào.

Thẻ meta được dùng bởi browser (cách hiển thị nội dung), search engines (keywords). Một số thẻ meta: title, description, content-type, view-port,...

### Semantic Elements

- It describes its meaning to both the browser and the developer.
- Non-semantic elements: div and span - Tells nothing about this content.
- Semantic elements: form, table, and article - Clearly defines its content.

### HTML DOM (Document Object Model)

![](../imgs/dom.png)

Khi một trang web được load, browser sẽ tạo ra DOM. HTML DOM model được xây dựng như một cây Objects. Và Javascript có thể access và thay đổi các elements trong HTML.

### Một số cách ẩn element

- Sử dụng display: none - Xóa khỏi DOM
- Sử dụng opacity: 0 - Không bị xóa khỏi DOM, có thể dùng click hoặc hover
- Sử dụng visible: hidden - Không bị xóa khỏi DOM, không thể dùng click hoặc hover

### SEO là gì?

SEO (Search Engine Optimization) nghĩa là tối ưu hóa vị trí tìm kiếm trên các công cụ như: Google, ...

Một số cách sử dụng SEO:

- Sử dụng đầy đủ thẻ meta
- Sử dụng đầy đủ sematic
- Sử dụng nhiều h1 cho tiêu đề
- Image phải có thuộc tính alt
