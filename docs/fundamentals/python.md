## Tổng quan về Python

Python là ngôn ngữ lập trình cấp cao, hướng đối tượng và thông dịch. Điểm mạnh của Python là dễ học và đa dụng.

## Data Types

- Text Type: str
- Numeric Types: int, float, complex
- Sequence Types: list, tuple, range
- Mapping Type: dict
- Set Types: set, fronzenset
- Boolean Type: bool
- Binary Types: bytes, bytearray, memoryview
- None Type: NoneType

### Tuple

Mình chỉ nói kĩ về tuple vì các kiểu dữ liệu còn lại khá tương đồng với các ngôn ngữ lập trình khác. Tuple khác biệt ở chỗ nó được sắp xếp và không đổi nghĩa là ta không thể thêm, xóa, sửa các phần tử trong tuple.
Nhưng nếu ta thực muốn làm điều đó thì có 2 cách là chuyển thành list để thao tác và cộng 2 tuple với nhau. Tuy nhiên khi cộng lưu ý rằng (1) và (1, ) hoàn toàn khác nhau. Trong khi (1) vẫn là kiểu dữ liệu int và (1, ) mới là kiểu dữ liệu tuple

**Note:** một điều khá đặc trưng ở Python là kiểu dữ liệu các kiểu dữ liệu list, dict, tuple có thể lưu phần tử bất kể kiểu dữ liệu như (1, "two", True)

## Decorator

Decorator là một design pattern mà đính thêm trách nhiệm vào một object. Trong Python, tất cả đều là object, và hàm hay class đều là callable objects (nhận vào và trả về object).

```
def uppercase_decorator(function):
    def wrapper():
        func = function()
        make_uppercase = func.upper()
        return make_uppercase

    return wrapper

def say_hi():
    return 'hello there'

decorate = uppercase_decorator(say_hi)
print(decorate())
```

Nhìn vào ví dụ trên ta có thể hình dung cách mà một hàm nhận vào hàm khác như là một tham số và có thể sử dụng chúng trong phạm vi toàn hàm (kể cả hàm trong hàm).

```
def uppercase_decorator(function):
    def wrapper():
        func = function()
        make_uppercase = func.upper()
        return make_uppercase

    return wrapper

@uppercase_decorator
def say_hi():
    return 'hello there'

print(say_hi())
```

Và đây chính là cách decorator thực hiện với nhiệm vụ tương tự ví dụ trên. Vậy khi nào thì ta sử dụng decorator? Thường thì chúng được sử dụng cho mục đích logging và time measurement. Ngoài ra khi ta có những tác vụ lặp lại nhau như mỗi khi xử lý dữ liệu phải connect tới database thì ta có thể thêm vào hàm xử lý.
