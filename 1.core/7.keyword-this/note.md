# 1. this là gì?
    this là một từ khóa đặc biệt trong JavaScript.
    Nó đại diện cho đối tượng mà hàm đang được gọi thông qua.
    Giá trị của this không cố định, mà phụ thuộc vào cách hàm được gọi.

2. Các trường hợp cơ bản của this
(1) Dùng trong object method (phương thức của object)
const person = {
  name: "Huy",
  sayHi: function() {
    console.log("Xin chào, tôi là " + this.name);
  }
};

person.sayHi(); // 👉 "Xin chào, tôi là Huy"


👉 Ở đây this chính là object person.

(2) Dùng trong function bình thường
function showThis() {
  console.log(this);
}
showThis();


Trong strict mode ('use strict') → this = undefined.

Trong non-strict mode → this = window (trên trình duyệt).

(3) Dùng trong constructor function
function Car(brand) {
  this.brand = brand;
}
const car1 = new Car("Toyota");
console.log(car1.brand); // 👉 "Toyota"


👉 Khi dùng new, this trỏ đến object mới được tạo ra.

(4) Trong arrow function
const obj = {
  name: "Huy",
  say: () => {
    console.log(this.name);
  }
};
obj.say(); // 👉 undefined


👉 Arrow function không có this riêng, nó sẽ lấy this từ ngữ cảnh bên ngoài (ở đây là window).

(5) Dùng với call, apply, bind
function greet() {
  console.log("Hello " + this.name);
}

const user = { name: "Huy" };

greet.call(user); // 👉 "Hello Huy"


👉 call, apply, bind cho phép ta ép this trỏ đến object mong muốn.

Tóm gọn dễ nhớ

Trong object method → this = object.

Trong function bình thường → this = window (hoặc undefined trong strict).

Trong constructor (new) → this = object mới.

Trong arrow function → this = kế thừa từ scope bên ngoài.

Dùng call/apply/bind → this được set thủ công.