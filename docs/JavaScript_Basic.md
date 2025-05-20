# Javascript basic

## Các kiểu dữ liệu

### Number type
```javascript
var a = 1;
var b = 2;
var c = 1.5;
```
### String type
```javascript
var fullName = 'Tran Tien Quoc';
```
### Boolean type
```javascript
var isSuccess = true;
```
//Undifined type
var age;

//Null
var isNull = null; // rỗng

//Object Type
```
var myObj = {
    name: 'Son Tung MTP',
    age: 29,
    address: 'Bac Ninh',
    myFunction: function () {
    }
};

var myArray = [
    'JavaScript',
    'Ruby',
    'Java'
];
```
//tạo chuỗi Template String

var firstName = 'Tran Tien';
var lastName = 'Quoc';

console.log(`Tôi là: ${firstName} ${lastName}`);


// Cách truyền tham số vào hàm
```
function writeLog(message) {
    console.log(message);
}
```

writeLog(); //có thể truyền bất cứ thứ gì

//các loại function

//1. Declaration function có thể gọi trước khi được định nghĩa
```
showMessage();
function showMessage() {
    console.log('Declaration function');
}
```
//2. Expresstion function không thể gọi khi không được định nghĩa trước
//showMessage2(); error
```
var showMessage2 = function () {
    console.log('Expression function');
};
```
showMessage2();


//Object trong javascript

var emailKey = 'email';
```
var myInfo = {
    name: 'Tran Tien Quoc',
    age: 26,
    address: 'TP. Hồ Chí Minh',
    [emailKey]: 'trantienquoc0208@gmail.com',
    getName: function () {
        return this.name;
    }
}; //delete myInfo.age;

var myKey = 'address';
console.log(myInfo[myKey]);
console.log(myInfo); //console.log(myInfo.getName());


//vòng lặp for of
function writesmallLog() {
    var myString = '';
    for (var param of arguments) {
        myString += `${param} - `;
    }
    console.log(myString);
}

writesmallLog('Log 1', 'Log 2');

//Vòng lặp

for (var i = 1; i <= 10; i++) {
    console.log(i)
}
//Vòng lặp mảng

var myArray = [
    'Javascript',
    'PHP',
    'Java',
    'Python'
];

var arrayLenght = myArray.length;

for (var i = 0; i < arrayLenght; i++) {
    console.log(myArray[i]);
}

//vòng lặp for/in
var myInfo = {
    name: 'Tran Tien Quoc',
    age: 19,
    address: 'TP.HCM'
};

for (var key in myInfo) {
    console.log(myInfo[key]);
}

//class Declaration
class Rectangle {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
}

//class Expression
const Rectangle = class {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
};
```