# TypeScript

## Kiểu dữ liệu

### Kiểu dữ liệu nguyên thuỷ

```ts
let helloWorld: string = "Hello world";

let numberA: number = 5;

let isSuccess: boolean = true;

let rong: null = null;

let undi: undefined = undefined;
```

### Kiểu dữ liệu tham chiếu

```ts
let obj: object = { a: 1 };
```


  <summary>Một số lưu ý</summary>
#### Các cách clone object trong JavaScript

Có nhiều cách để clone một object trong JavaScript, phổ biến nhất gồm:

- **Spread Operator**

  ```js
  let clone = { ...obj };
  ```

- **Object.assign**

  ```js
  let clone = Object.assign({}, obj);
  ```

- **Các phương pháp khác**
  Bao gồm `structuredClone(obj)`, `JSON.parse(JSON.stringify(obj))`, hoặc dùng thư viện như `lodash.cloneDeep(obj)`.

---

#### Nên dùng phương pháp nào?

| Trường hợp                              | Nên dùng                                          |
| --------------------------------------- | ------------------------------------------------- |
| Object đơn giản, không lồng nhau        | Spread operator (`...obj`) hoặc `Object.assign()` |
| Object có cấu trúc lồng nhau (nested)   | `structuredClone(obj)`                            |
| Object chứa `Date`, `Map`, `Set`        | `lodash.cloneDeep(obj)`                           |
| Object có vòng lặp (circular reference) | `lodash.cloneDeep(obj)`                           |
| Yêu cầu hiệu năng cao                   | Tránh sử dụng deep clone nếu không cần thiết      |

> **Ghi nhớ**: Deep clone thường tốn tài nguyên và không cần thiết với các object đơn giản.

---

#### Những lỗi phổ biến khi clone object

- **Clone nông khi cần clone sâu**
  Dễ dẫn đến lỗi logic khi thay đổi object con trong bản clone làm ảnh hưởng đến bản gốc.

- **Dùng `JSON.stringify` với object phức tạp**
  Không thể clone function, `Date`, hoặc object có vòng lặp — dẫn đến mất dữ liệu hoặc throw lỗi.

- **Làm mất prototype**
  Một số phương pháp như `JSON.stringify` hoặc `lodash.cloneDeep` không giữ nguyên prototype, có thể làm sai hành vi object.

- **Circular reference gây lỗi**
Khi dùng `JSON.stringify`, nếu object có vòng lặp sẽ ném lỗi (`TypeError: Converting circular structure to JSON`).
</details>

```ts
let arr: number[] = [1, 2];

let tup: [string, number] = ["a", 1]; //mảng có độ dài cố định

const sum = function (x: number, y: number) {
  return x + y;
};
```

### CallBack trong typescript

```ts showLineNumbers
function oderPizaa(callback: () => void): void {
  console.log("Đã đặt pizza, chờ 3s để giao");
  setTimeout(function () {
    console.log("Pizza đã được giao");
    callback();
  }, 3000);
}
function eatPizza(): void {
  console.log("Ăn pizza");
}
oderPizaa(eatPizza);
```

### Promise trong typescript

```ts showLineNumbers
function oderPizza1(): Promise<void> {
  return new Promise<void>(function (resolve) {
    console.log("Đã đặt Pizza, chờ 3s để giao");
    setTimeout(function () {
      console.log("Pizza đã được giao");
      resolve();
    }, 3000);
  });
}
function eatPizza1(): void {
  console.log("Ăn pizza");
}

oderPizza1()
  .then(function () {
    eatPizza();
  })
  .catch(function () {
    console.log("Có lỗi xảy ra khi giao Pizaa");
  });
```

### async/await trong typescript

```ts showLineNumbers
function deliveryPizza(): Promise<string> {
  return (
    new Promise() <
    string >
    function (resolve, reject) {
      setTimeout(function () {
        let isSucc: boolean = true;
        if (isSucc) {
          resolve("giao pizza thành công");
        } else {
          reject("giao pizza thất bại");
        }
      }, 3000);
    }
  );
}
async function oderPizaa2(): Promise<void> {
  try {
    console.log("Đặt Pizza");
    const result: string = await deliveryPizza(); //chờ promise xử lý
    console.log(result); //Giao pizza thành công
    console.log("Ăn Pizza");
  } catch (error) {
    console.log(error);
  }
}
```

## Kiểu dữ liệu nâng cao

### Union Types - kết hợp nhiều kiểu

```ts
let id: string | number = "9233";
id = 123;
```

### Intersection Types - giao của các kiểu

```ts
type Person = { name: string };
type Employee = { id: number };
type Staff = Person & Employee;
```

### Literal Types - Giá trị cụ thể

```ts
let direction: "up" | "down" | "left" | "right" = "up";
```

### Enum - Tập hợp các hằng số có tên

```ts
enum Color {
  Red,
  Green,
  Blue,
}

let favoriteColor: Color = Color.Blue;
```

### Type Aliases - Đặt tên cho kiểu dữ liệu

```ts
type ID = string | number;
type UserCallback = (user: User) => void;
```

### Generic Types - Kiểu tham số hoá

```ts
function identity<T>(arg: T): T {
  return arg;
}
let result = identity<string>("Hello");
```

## Function trong TypeScript

### Function Declaration

```ts
function add(a: number, b: number): number {
  return a + b;
}
```

### Function Expression

```ts
const add = function (a: number, b: number): number {
  return a + b;
};
```

### Optional Parameters - Tham số tuỳ chọn

```ts
function greet(name: string, greeting?: string): string {
  return `${greeting || "Hello"} ${name}`;
}
greet("john"); // "Hello John"
greet("John", "Hi"); // "Hi John"
```

