## Design Pattern là gì?

- Là mẫu giải quyết vấn đề hay gặp do các lập trình viên lúc trước rút ra. Giúp tổ chức code tốt hơn.
- Có 3 loại: creational, structual, behavioural (cách giao tiếp)
- Các design pattern hay dùng: Factory, Facade, Singleton, Observer
- Singleton nếu dùng trong môi trường multithread, bypass private constructor
- Angular (DI, IOC)
- Đừng quá lạm dụng
- Giải quyết vấn đề chứ không phải tăng thêm vấn đề
- Anti-pattern

## Nhóm khởi tạo (Creational Pattern)

## Singleton

- Mỗi class chỉ có tạo một instance
- Sử dụng cho logging, configuration, thread pool, database connections, ...

```ts
class Settings {
  static instance: Settings;
  public readonly mode = "dark";

  private constructor() {}

  static getInstance(): Settings {
    if (!Settings.instance) {
      Settings.instance = new Settings();
    }

    return Settings.instance;
  }
}

const settings = Settings.getInstance();
```

- Tuy nhiên, cách dùng này chỉ sử dụng tốt cho single-thread, trong trường hợp multi-thread thì sẽ không đảm bảo được chỉ có 1 instance. Để khắc phục ta sử dụng Thread Safe Singleton.
- Sử dụng keyword synchronized, tuy nhiên cách này sẽ chậm vì bất kỳ thread nào gọi đến đều phải chờ một thread khác đang sử dụng.

## Factory Method

- Định nghĩa interface cho sử dụng object. Thay vì sử dụng từ khóa new để khởi tạo một object, sử dụng function hoặc method
- Sử dụng khi có nhiều loại đối tượng cần khởi tạo (Ex: các loại column)
- Dễ mở rộng, chỉ cần tạo ra class mới và implement vào factory method

```ts
class IOSButton {}
class AndroidButton {}

const button1 = os === "ios" ? new IOSButton() : new AndroidButton();
const button2 = os === "ios" ? new IOSButton() : new AndroidButton();

class ButtonFactory {
  createButton(os: string): IOSButton | AndroidButton {
    if (os === "ios") {
      return new IOSButton();
    } else {
      return new AndroidButton();
    }
  }
}

const factory = new ButtonFactory();
const button1 = factory.createButton(os);
```

# Abstract Factory

- Factory của factory

# Prototype

- Clone object hiện tại chứ không tạo mới
- Nếu có một object phức tạp và mất nhiều thời gian config. Sử dụng prototype để clone object đó.

```ts
class ConcretePrototype {
  private property: string;

  constructor(property: string) {
    this.property = property;
  }

  clone() {
    return new ConcretePrototype(this.property);
  }
}

const originalObj = new ConcretePrototype("Original");
const clonedObj = originalObj.clone();
```

## Builder

- Truyền vào tham số trong constructor, nhưng nếu có nhiều tham số thì khó keep tracks tất cả các options.
- Với builder pattern giúp tạo step by step sử dụng method
- Vấn đề của Factory Pattern và Abstract Factory Pattern là khi có quá nhiều thuộc tính thì khi truyền vào factory phải truyền tất cả tham số nếu không thì null
- Khi có nhiều constructor, hãy nghĩ tới Builder

```ts
class BanhMi {
  constructor(cha: string, pate: string, rau: string, sot: string) {}

  addCha(cha: string) {
    this.cha = cha;
    return this;
  }

  addPate(pate: string) {
    this.pate = pate;
    return this;
  }

  addRau(rau: string) {
    this.rau = rau;
    return this;
  }

  addSot(sot: string) {
    this.sot = sot;
    return this;
  }
}

new BanhMi("lua", "heo", "can tay", "bo bam");

const banhMi = new BanhMi();

// Method chaining
banhMi.addCha("gan").addSot("ca chua");
```

## Nhóm cấu trúc (Structural Patter)

# Adapter

- Adapter Pattern cho phép các objects với interface không liên quan có thể làm việc cùng nhau. Adapter giữ vai trò trung gian giữa 2 objects. Hữu dụng khi integrate một class với hệ thống có sẵn nhưng interface của class không match với hệ thống.
- Đảm bảo nguyên tác Open/Close của SOLID

```ts
class FileLogger {
  writeToFile(message: string): void {}
}

interface ILogger {
  log(message: string): void {}
}

class LoggerAdapter implements ILogger {
  fileLogger: FileLogger;

  log(message: string): void {
    fileLogger.writeToFile(message);
  }
}
```

# Bridge

- Tách abstraction ra khỏi implementation.

# Composite

- Nhóm đối tượng theo cấu trúc cây

# Decorator

- Cho phép thêm chức năng mới vào đối tượng hiện tại mà không muốn ảnh hưởng tới đối tượng khác. Mỗi khi cần thêm tính năng mới, đối tượng được bọc trong một đối tượng mới.

```ts
interface Coffee() {
  cost(): number;
}

class SimpleCoffee implements Coffee {
  cost(): number {
    return 5;
  }
}

class MilkDecorator implements Coffee {
  private coffee: Coffee;

  constructor(coffee: Coffee) {
    this.coffee = coffee;
  }

  cost(): number {
    return this.coffee.cost() + 1;
  }
}
```

## Facade

Cung cấp một interface đơn giản cho một hệ thống phức tạp class, library hoặc framework. Hide low-level details

## Nhóm tương tác (Behavioural Pattern)

# Chain of Responsibility

Truyền request qua một chain handlers đến khi handle request

## Iterator

Cho phép duyệt tuần tự qua cấu trúc dữ liệu phức tạp không để lộ nội dung bên trong

## Proxy

Cung cấp một object như là bản sao của một đối tượng. Proxy sẽ nhận client requests, làm gì đó xong truyền lại cho object thật

## State

Cho phép một object thay đổi behaviour khi mà state thay đổi. State pattern tách class thành behaviour riêng và giao cho lớp con thực hiện

```ts
class OrderContext {
  state: OrderState;

  constructor() {
    this.state = new PendingState(this);
  }

  setState(state: OrderState) {
    this.state = state;
  }

  processOrder() {
    this.state.processOrder();
  }
}

interface OrderState() {
  processOrder();
}

class PendingState implements OrderState {
  context: OrderContext;

  constructor(context: OrderContext) {
    this.context = context;
  }

  processOrder() {

  }
}
```

# Template method

Định nghĩa khung cho một thuật toán trong một phương thức. Các lớp con có thể thay đổi một số bước mà không làm thay đổi cấu trúc chung

# Observer

- Thông báo đến các objects khác khi state thay đổi
- Sử dụng khi react một sự kiện, eventListener
- Observer Pattern còn gọi là Pub/Sub

```ts
class DataService {
  private data: string;
  private observers: Observer[] = [];

  add(observer: Observer) {
    this.observers.push(observer);
  }

  notify() {
    this.observers.forEach((observer) => observer.update(this.data));
  }
}
```
