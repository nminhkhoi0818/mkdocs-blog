## Clean code là gì?

- Cách code dễ đọc, dễ hiểu, dễ bảo trì, dễ hiểu cho tất cả mọi người trong team. Dễ dàng để các lập trình viên khác, hoặc chính mình trong tương lai hiểu và sửa không gặp khó khăn.
- In clean code, bugs cannot hide

## Principles

- Loose Coupling
- High Cohesive (Cohesive is the degree to which elements of a whole belong together). Cohesive là mức độ những phần tử trong một class/module phải thuộc về nhau, có cùng một chức năng. Một class high cohesive sẽ tập trung vào các nhiệm vụ liên quan chặt chẽ
- Mind-sized Components

## Smells

- Rigidity: một thay đổi nhỏ gây ra thay đổi ở nhiều phần khác, khiến cho việc thay đổi trở nên phức tạp và tốn kém
- Fragility: thay đổi nhỏ, nhiều phần khác bị lỗi
- Immobility: không thể tái sử dụng các phần của code

## Class Design

- S (mỗi class nên chỉ có một lý do để thay đổi)
- O (Open for extension, close for modification)
- L (Lớp con có thể thay thế lớp cha mà không làm thay đổi tính đúng đắn của chương trình)
- I (Chia nhỏ interface hợp lý, để một class chỉ implement các interface cần thiết)
- D (Dependency Inversion), (không nên phụ thuộc trực tiếp mà phụ thuộc vào abstractions)

## General

- DRY (Don't repeat your self)
- KISS (Keep it simple, stupid)

## Naming

- Đặt tên biến theo đúng chức năng của function hoặc class
- Use Long Names for Long Scopes (độ dài của tên biến phụ thuộc vào vòng đời của nó)
- Đặt tên biến cho class đặt là danh từ, đặt tên biến cho method động từ + danh từ

## Method

- Method nên làm 1 việc
- Không nên truyền quá nhiều arguments vào method
- Không phù hợp static

## Understandability

- Consistency

## Maintainability Killers

- Không duplicate
- Không sử dụng Magic numbers mà sử dụng constant

## Exception Handling

- Sử dụng Exceptions thay vì return Codes hoặc null
