## Lịch sử Angular

- 2010: được support bởi Google, SPA, không còn phụ thuộc vào server, Iconic hợp tác
- 2014 - 2015: Angular chạm ngưỡng, chuẩn mới của JS, Angular trở nên tuột hậu, xây dựng lại toàn bộ
- 2016: không biết maintain, làm sao migrate từ Angular.js, cú pháp xa lạ Angular 2.0
- 2018: Improve và ra nhiều bản cập nhật mới

## Module, component

- NgModule là một decorator để xác định một module. Thành phần của NgModule gồm declarations, imports, exports, providers, bootstrap
- NgComponent: quản lý một phần giao diện, chứa logic và sử lý sự kiện. Component có thể lồng nhau. Standalone component giúp component tự quản lý dependencies, loại bỏ sự phụ thuộc vào module.

## Directives

- Component Directive: là component trong angular
- Structural Directive: thay đổi cấu trúc của DOM bằng thêm, xóa hoặc thay đổi phần tử trong DOM
- Attribute Directive: thay đổi giao diện hoặc hành vi HTML, sử dụng với decorator Directive

## Angular lifecycle hooks

- Constructor (khai báo dependency injection)
- ngOnChanges (gọi khi có sự thay đổi giá trị Input của component)
- ngOnInit (gọi duy nhất 1 lần để khởi tạo giá trị cho biến, call api, khởi tạo form, ...)
- ngDoCheck
- ngAfterContentInit
- ngAfterContentChecked
- ngAfterViewInit
- ngAfterViewChecked
- ngOnDestroy

## Binding

- [property-binding]
- (event-binding)

## Routing

- Điều hướng component theo URL
- router-outlet
- routerLink

## Dependency Injection

- DI là một design pattern tách việc khởi tạo ra việc sử dụng, giúp dễ bảo trì. Các thành phần chính trong DI: Provider, Injector, Token, Dependency
- Một class có thể đăng ký sử dụng dependency thông constructor
- Khi component được khởi tạo, Angular sẽ inject một instance của service vào constructor
- Service
- Inject dependencies

# Rxjs (map, of, from)

- Rxjs là một thư viện để làm việc với reactive programming bằng cách sử dụng Observable. Giúp xử lý các luồng sự kiện bất đồng bộ. Rxjs thường được sử dụng trong các ứng dụng Angular.
- Observable: là một đối tượng đại diện cho luồng dữ liệu hoặc sự kiện, có thể được quan sát bởi observer. Observable phá
- Observer: là một đối tượng có ba phương thức next, error, complete
- Subscription: là đối tượng được tạo ra khi subscribe vào một observable
- Operators: là các hàm dùng để biến đổi các giá trị Observable
- Subjects: là một Observable đặc biệt vừa là Observer

- Các operators thường gặp:
- map: chuyển đổi giá trị từ Observable

```js
productPrices$
  .pipe(map((price) => price * exchangeRate))
  .subscribe((vndPrice) => console.log(vndPrice));
```

- filter: lọc các giá trị theo điều kiện
- tap: thực hiện side effect mà không thay đổi giá trị
- mergeMap: chuyển đổi giá trị thành Observable và hợp nhất kết quả
- switchMap: chuyển đổi giá trị thành Observable và hủy bỏ Observable nếu có giá trị mới
- debounceTime: trì hoãn giá trị phát ra sau một khoảng thời gian nhất định. Sử dụng khi search keywords, nếu có một cụm từ hạn chế search từng chữ cái
- catchError: bắt lỗi và xử lý
- concat: kết nối các Observable theo thứ tự
- tap: thực hiện side effect mà không làm thay đổi giá trị (console.log(), ...)
- distinctUntilChanged: phát ra giá trị khi nó khác với giá trị trước đó
- retry: tự động thử lại với số lần nhất định

# Ngrx

- Ngrx là state management solution, state là data thay đổi sử dụng ở nhiều components. Manage complex applications.
- State store: components có thể listen data in there
- Redux pattern
- Actions, Reducers, Store, Selectors, Effects
- State management
- Effects: không trực tiếp liên quan đến update UI, HTTP Request, localStorage, logging là side effect vì không update UI

# Design patterns

- Singleton: quản lý một instance trong suốt ứng dụng
- Observer Pattern: Pub/Sub
