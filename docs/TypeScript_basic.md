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

let arr: number[] = [1, 2];

let tup: [string, number] = ["a", 1];

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
