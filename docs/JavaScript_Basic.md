# Javascript basic

## Các kiểu dữ liệu

### Number type

```js
var a = 1;
var b = 2;
var c = 1.5;
```

### String type

```js
var fullName = "Tran Tien Quoc";
```

### Boolean type

```js
var isSuccess = true;
```

### Undifined type

```js
var age;
```

### Null

```js
var isNull = null; //rổng
```

### Object Type

```js
var myObj = {
  name: "Son Tung MTP",
  age: 29,
  address: "Bac Ninh",
  myFunction: function () {},
};

var myArray = ["JavaScript", "Ruby", "Java"];
```

### Tạo chuỗi Template String

```jsx live noInline
var firstName = "Tran Tien";
var lastName = "Quoc";

//console.log(`Tôi là: ${firstName} ${lastName}`);
render(<p>{`Tôi là: ${firstName} ${lastName}`}</p>);
```

### Cách truyền tham số vào hàm

```jsx live noInline
function writeLog(message) {
  render(<p>{message}</p>);
}
writeLog(20); //có thể truyền bất cứ thứ gì
```

## Các loại function

### Declaration function

```jsx live noInline
//có thể gọi trước khi được định nghĩa
showMessage();
function showMessage() {
  //console.log("Declaration function");
  render(<p>{"Declaration function"}</p>);
}
```

### Expresstion function

```jsx live noInline
//không thể gọi khi không được định nghĩa trước
//showMessage2(); error
var showMessage2 = function () {
  //console.log("Expression function");
  render(<p>{"Expression function"}</p>);
};

showMessage2();
```

## Object trong javascript

```jsx live noInline
var emailKey = "email";

var myInfo = {
  name: "Tran Tien Quoc",
  age: 26,
  address: "TP. Hồ Chí Minh",
  [emailKey]: "trantienquoc0208@gmail.com",
  getName: function () {
    return this.name;
  },
}; //delete myInfo.age;

var myKey = "address";
//console.log(myInfo[myKey]);
//console.log(myInfo);
//console.log(myInfo.getName());
render(<p>{`Name: ${myInfo.name}, Address: ${myInfo[myKey]}`}</p>);
```

## Vòng lặp

### Vòng lặp for

```jsx
for (var i = 1; i <= 10; i++) {
  console.log(i);
}
```

### Vòng lặp for mảng

```js
var myArray = ["Javascript", "PHP", "Java", "Python"];

var arrayLenght = myArray.length;

for (var i = 0; i < arrayLenght; i++) {
  console.log(myArray[i]);
}
```

### Vòng lặp for/in

trị sẽ không thể gán lại được khi dùng const, nên trong vòng lặp for/in biến key sẽ bị gán lại mỗi lần lặp với (key mới) nên sẽ gây lỗi.

```js
var myInfo = {
  name: "Tran Tien Quoc",
  age: 19,
  address: "TP.HCM",
};

for (var key in myInfo) {
  console.log(myInfo[key]);
}

//let có giới hạn phạm vi ( block scope ) nên biến key ở đây sẽ chỉ được dùng ở trong vòng lặp, khi ra khỏi dấu {} sẽ không thể dùng được nữa.
//var có giới hạn phạm vi function ( function scope ) nên biến key vẫn có thể sử dụng được ở bên ngoài vòng lặp nên nó có thể gây lỗi.
//const giá trị sẽ không thể gán lại được khi dùng const, nên trong vòng lặp for/in biến key sẽ bị gán lại mỗi lần lặp với (key mới) nên sẽ gây lỗi. Tuy nhiên trong for...in JS vẫn cho phép const vì mỗi lần lặp là một binding mới.
```

### Vòng lặp for/of

```js
function writesmallLog() {
  var myString = "";
  for (var param of arguments) {
    myString += `${param} - `;
  }
  console.log(myString);
}

writesmallLog("Log 1", "Log 2");
```

## Các loại class

### Class Declaration

```js
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
```

### Class Expression

```js
const Rectangle = class {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
```

## Sync /Async

```js
//setTimeout, set Interval, fetch,
//XMLHttpRequest, file reading, request animation frame
```

### Call Back

```js
// 1. Là hàm
// 2. Truyền qua đối số
// 3. Được gọi lại(trong hàm nhận đối số)

// Demo call back
function oderPizza(callback) {
  console.log("Đã dặt pizza chờ 3s giao");

  setTimeout(function () {
    console.log("Pizza đã được giao");
    callback(); // Gọi hàm callback sau khi pizza được giao
  }, 3000);
}
function eatPizza() {
  console.log("Ăn pizza");
}

oderPizza(eatPizza);
```

### async/await

```js
//1. async biến một hàm thành hàm bất đồng bộ, và tự động trả về Promise.
//2. await dùng để chờ một Promise hoàn thành mà không cần dùng .then().
//3. Giúp viết code bất đồng bộ giống như code tuần tự, dễ đọc, dễ debug.

function deliveryPizza(){
    return new Promise(function(resolve){
        setTimeout(function(){
            resolve('Pizza đã giao');
        },3000);
    });
}
    //Dùng async/await
    async function orderAEPizza() {
        console.log('Đã đặt pizza, chờ 3s giao');
        const result = await deliveryPizza(); //đợi pizza được giao
        console.log(result);
        console.log('Ăn pizza');
    }
    orderAEPizza();

sử dụng try/catch để xử lý lỗi

function deliveryPizza() {
    return new Promise(function (resolve, reject) {
        setTimeout(function () {
            var isSuccess = true;
            if (isSuccess) {
                resolve('Giao Pizza thành công');
            } else {
                reject('Giao pizza thất bại');
            }
        }, 3000);
    });
}
    async function orderAEPizza() {
        try {
            console.log('Đặt Pizza ');
            var result = await deliveryPizza();
            console.log(result);
            console.log('Ăn pizza')
        } catch (error) {
            console.log(error);
        }
    }
    orderAEPizza();
```

### Promise

```js
/**
 * Promise là một đối tượng đại diện cho một giá trị có có bây giờ, trong tương lai, hoặc không bao giờ,
 * Promise xử lý bất đồng bộ gọn hơn CallBack
 *
 * Promise có 3 trạng thái:
 * Pending   - chờ xử lý
 * fulfilled - thành công
 * rejected  - thất bại
 */

function oderPizza() {
  return new Promise(function (resolve) {
    console.log("Đã đặt Pizza, chờ 3s để giao");
    setTimeout(function () {
      console.log("Pizza đã được giao");
      resolve(); //Hoàn tất đơn hàng
    }, 3000);
  });
}
function eatPizza() {
  console.log("Ăn Pizza");
}
oderPizza()
  .then(function () {
    eatPizza();
  })
  .catch(function () {
    console.log("Có lỗi xảy ra khi giao Pizza");
  });
```
