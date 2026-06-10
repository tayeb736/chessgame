# 📘 JavaScript: دليل تعلم شامل ومفصل

> من الصفر إلى الاحتراف — كل مفهوم مع شرح + كود + مثال تطبيقي

---

## 📋 المحتويات
1. [المقدمة والمفاهيم الأساسية](#1-المقدمة)
2. [المتغيرات وأنواع البيانات](#2-المتغيرات)
3. [العوامل (Operators)](#3-العوامل)
4. [التحكم في التدفق (Control Flow)](#4-التحكم)
5. [الدوال (Functions)](#5-الدوال)
6. [المصفوفات (Arrays)](#6-المصفوفات)
7. [الكائنات (Objects)](#7-الكائنات)
8. [التحكم في DOM](#8-dom)
9. [الأحداث (Events)](#9-الأحداث)
10. [ES6+ الحديث](#10-es6)
11. [البرمجة غير المتزامنة (Async)](#11-async)
12. [Classes و OOP](#12-oop)
13. [Error Handling](#13-errors)
14. [Modules](#14-modules)
15. [Browser APIs](#15-browser-apis)
16. [أدوات وتطبيقات متقدمة](#16-advanced)

---

<a name="1-المقدمة"></a>
## 1️⃣ المقدمة والمفاهيم الأساسية

### ما هو JavaScript؟
- لغة برمجة عالية المستوى (High-Level)
- تعمل في المتصفح (Client-Side) وعلى السيرفر (Node.js)
- تعتمد على الـ **Event-Driven** و **Non-Blocking I/O**
- ديناميكية typing (لا تحتاج تعريف نوع المتغير)

### كيف تشغل JavaScript؟

```javascript
// 1. في الـ Browser Console (F12 → Console)
console.log("Hello World");

// 2. في ملف HTML
// <script>console.log("Hello");</script>
// <script src="script.js"></script>

// 3. في Node.js
// node script.js
```

### الـ Console
```javascript
console.log("نص");          // طباعة عادية
console.error("خطأ");       // طباعة باللون الأحمر
console.warn("تحذير");      // طباعة باللون الأصفر
console.table([1,2,3]);     // طباعة كجدول
console.time("id");         // بدء计时
console.timeEnd("id");      // إيقاف计时 وطباعة الوقت
console.group("مجموعة");    // تجميع الـ logs
console.groupEnd();
```

---

<a name="2-المتغيرات"></a>
## 2️⃣ المتغيرات وأنواع البيانات

### إعلان المتغيرات

```javascript
// var — قديم، scope عام أو function-level (لا تستخدمه)
var x = 10;

// let — متغير يمكن تغييره، block-scope
let name = "Ahmed";
name = "Ali";  // ✅ مسموح

// const — ثابت لا يمكن إعادة تعيينه، block-scope
const PI = 3.14;
PI = 3;  // ❌ خطأ: Assignment to constant variable

// لكن const يسمح بتعديل محتوى object أو array
const arr = [1, 2, 3];
arr.push(4);  // ✅ مسموح
arr = [5];    // ❌ خطأ
```

### أنواع البيانات (Primitive Types)

```javascript
// String
let s1 = "Hello";
let s2 = 'World';
let s3 = `Hello ${s2}`;  // Template literal — الأفضل

// Number (integer + float — كلهم رقم واحد)
let n1 = 42;
let n2 = 3.14;
let n3 = Infinity;   // ∞
let n4 = NaN;        // Not a Number (نتيجة عملية غير صالحة)

// Boolean
let b1 = true;
let b2 = false;

// Undefined — متغير بدون قيمة
let u;
console.log(u);  // undefined

// Null — قيمة فارغة مقصودة
let nu = null;

// Symbol — معرف فريد
let sym = Symbol("id");

// BigInt — أرقام أكبر من 2^53
let big = 9007199254740991n;
```

### التحقق من الأنواع

```javascript
typeof "Hello"      // "string"
typeof 42           // "number"
typeof true         // "boolean"
typeof undefined    // "undefined"
typeof null         // "object" ← خطأ تاريخي في JS!
typeof Symbol()     // "symbol"
typeof 10n          // "bigint"
typeof []           // "object"
typeof {}           // "object"
typeof function(){} // "function"

// تحقق أفضل للـ null
console.log(null === null);  // true — استخدم === دائماً
```

### Type Coercion (تحويل تلقائي)

```javascript
// JS يحول الأنواع تلقائياً — هذا يسبب أخطاء مشهورة:

"5" + 3   // "53"  (number → string)
"5" - 3   // 2     (string → number)
"5" * "2" // 10
"hello" * 3 // NaN

// === vs ==
5 == "5"   // true  (JS يحول النوع تلقائياً)
5 === "5"  // false (لا يحول — الأفضل دائماً)
```

**القاعدة الذهبية:** استخدم `===` دائماً، ولا تعتمد على `==` أبداً.

---

<a name="3-العوامل"></a>
## 3️⃣ العوامل (Operators)

### العمليات الحسابية
```javascript
let a = 10, b = 3;
a + b   // 13  (جمع)
a - b   // 7   (طرح)
a * b   // 30  (ضرب)
a / b   // 3.333 (قسمة)
a % b   // 1   (باقي القسمة)
a ** b  // 1000 (رفع للأس: 10^3)
a++     // 10 ثم تصبح 11 (زيادة بعد الاستخدام)
++a     // 12 (زيادة قبل الاستخدام)
```

### العمليات المنطقية

```javascript
// AND (&&) — يرجع أول falsy value أو آخر قيمة
true && true    // true
true && false   // false
"hi" && 0 && {} // 0 (أول falsy)
"hi" && 5       // 5 (آخر قيمة لأن كلها truthy)

// OR (||) — يرجع أول truthy value أو آخر قيمة
true || false   // true
false || "hi"   // "hi"
0 || null || 5  // 5

// Nullish Coalescing (??) — يرجع القيمة الثانية لو الأولى null/undefined فقط
0 ?? 5          // 0  (لأن 0 ليس null ولا undefined)
null ?? 5       // 5

// NOT (!)
!true   // false
!0      // true (0 يعتبر falsy)

// الفرق بين || و ??
let x = 0;
let a = x || 10;    // a = 10  (لأن 0 يعتبر falsy)
let b = x ?? 10;    // b = 0   (لأن 0 ليس null/undefined)
```

### المقارنة
```javascript
5 > 3   // true
5 < 3   // false
5 >= 5  // true
5 <= 3  // false
5 === 5 // true  (مساواة تامة)
5 !== 3 // true  (عدم مساواة)
```

### العمليات على النصوص
```javascript
"Hello" + " " + "World"   // "Hello World"
`عدد الأحرف: ${"hi".length}`  // "عدد الأحرف: 2"
"hello".toUpperCase()      // "HELLO"
"hello".includes("ell")    // true
"hello".slice(1, 4)        // "ell"
```

### Optional Chaining (?.) — متقدم
```javascript
const user = { address: { city: "Cairo" } };
console.log(user?.address?.city);   // "Cairo"
console.log(user?.phone?.number);   // undefined (بدون خطأ)
// لو استخدمنا user.phone.number بدون ?. → TypeError!
```

---

<a name="4-التحكم"></a>
## 4️⃣ التحكم في التدفق (Control Flow)

### if / else if / else
```javascript
let age = 20;

if (age >= 18) {
    console.log("بالغ");
} else if (age >= 13) {
    console.log("مراهق");
} else {
    console.log("طفل");
}

// اختصار (Ternary Operator)
const status = age >= 18 ? "بالغ" : "قاصر";
// الشرط ? إذا true : إذا false

// Nesting ternary (ممنوع — صعب القراءة)
const r = a > b ? (a > c ? "a" : "c") : "b";
```

### Truthy vs Falsy
```javascript
// Falsy values (6 فقط):
false, 0, "" (string فارغ), null, undefined, NaN

// كل شيء آخر هو truthy:
"hello", 1, [], {}, Infinity, function(){}
```

### Switch
```javascript
let day = 3;
switch (day) {
    case 1:
        console.log("السبت");
        break;  // لازم break وإلا يستمر للـ case التالي
    case 2:
        console.log("الأحد");
        break;
    case 3:
        console.log("الاثنين");
        break;  // ⬅️ هنا سيطبع "الاثنين" ثم يتوقف
    default:
        console.log("يوم غير معروف");
}
```

### Loops

```javascript
// for — الأكثر استخداماً
for (let i = 0; i < 5; i++) {
    console.log(i);  // 0, 1, 2, 3, 4
}

// while
let i = 0;
while (i < 5) {
    console.log(i);
    i++;
}

// do-while — ينفذ مرة واحدة على الأقل
let j = 0;
do {
    console.log(j);
    j++;
} while (j < 5);

// for...of — للمصفوفات (ES6)
const arr = [10, 20, 30];
for (const value of arr) {
    console.log(value);  // 10, 20, 30
}

// for...in — للكائنات (تجنبه للمصفوفات)
const obj = { a: 1, b: 2 };
for (const key in obj) {
    console.log(key, obj[key]);  // a 1, b 2
}

// break / continue
for (let i = 0; i < 10; i++) {
    if (i === 3) continue;  // يتخطى 3
    if (i === 7) break;     // يتوقف عند 7
    console.log(i);          // 0,1,2,4,5,6
}
```

---

<a name="5-الدوال"></a>
## 5️⃣ الدوال (Functions)

### Function Declaration vs Expression

```javascript
// Declaration — يمكن استدعاؤها قبل تعريفها (Hoisting)
sayHi();  // ✅ يعمل
function sayHi() {
    console.log("Hi!");
}

// Expression — لا يمكن استدعاؤها قبل التعريف
sayBye();  // ❌ TypeError
const sayBye = function() {
    console.log("Bye!");
};
```

### Arrow Functions (ES6) — الأفضل حالياً

```javascript
// شكلها العام
const func = (param) => {
    return param * 2;
};

// إذا كان parameter واحد → أقواس اختيارية
const double = x => x * 2;

// إذا كان سطر واحد → return ضمني
const add = (a, b) => a + b;

// إذا كان الـ return object → لازم أقواس
const createUser = (name) => ({ name, age: 20 });

// الفرق الحاسم: arrow function ليس لها this الخاص بها
const obj = {
    name: "Ali",
    regular: function() {
        console.log(this.name);  // "Ali" (this = obj)
    },
    arrow: () => {
        console.log(this.name);  // undefined (this = الخارج)
    }
};
```

### Parameters

```javascript
// Default parameters
function greet(name = "صديق") {
    return `مرحباً ${name}`;
}
greet();         // "مرحباً صديق"
greet("Ahmed");  // "مرحباً Ahmed"

// Rest parameters (...)
function sumAll(...numbers) {
    return numbers.reduce((acc, n) => acc + n, 0);
}
sumAll(1, 2, 3, 4);  // 10

// Arguments object (قديم — لا تستخدمه)
function oldWay() {
    console.log(arguments);  // Arguments(3) [1,2,3]
}
```

### Return

```javascript
// أي دالة بدون return ترجع undefined
function noReturn() {}
noReturn();  // undefined

// return ينهي الدالة فوراً
function check(x) {
    if (x < 0) return "سالب";
    console.log("هذا لن يطبع لو x < 0");
    return "موجب";
}
```

### Higher-Order Functions (دوال تأخذ دوال)

```javascript
// دالة تأخذ دالة كـ argument
function operate(a, b, fn) {
    return fn(a, b);
}
operate(5, 3, (x, y) => x + y);   // 8
operate(5, 3, (x, y) => x * y);   // 15

// دالة ترجع دالة
function createMultiplier(factor) {
    return (x) => x * factor;
}
const double = createMultiplier(2);
double(5);  // 10

// استخدام عملي: Debounce
function debounce(fn, delay) {
    let timer;
    return function(...args) {
        clearTimeout(timer);
        timer = setTimeout(() => fn(...args), delay);
    };
}
```

### Scope و Closure

```javascript
// Closure: دالة داخلية تتذكر متغيرات الدالة الخارجية حتى بعد انتهائها
function counter() {
    let count = 0;
    return function() {
        count++;
        return count;
    };
}

const myCounter = counter();
myCounter();  // 1
myCounter();  // 2
myCounter();  // 3
// المتغير count لا يزال موجوداً رغم انتهاء counter()!

// مثال عملي: إنشاء معرفات
function createIdGenerator(prefix) {
    let id = 0;
    return () => `${prefix}-${++id}`;
}
const userId = createIdGenerator("USER");
userId();  // "USER-1"
userId();  // "USER-2"

// Block Scope (let/const)
{
    var a = 1;  // var يخرج من الـ block
    let b = 2;  // باقي داخل الـ block
}
console.log(a);  // 1
console.log(b);  // ReferenceError
```

### Immediately Invoked Function Expression (IIFE)

```javascript
// دالة تنفذ فوراً — كانت تستخدم لعزل المتغيرات
(function() {
    const secret = "لا يمكن الوصول من الخارج";
    console.log("نفذت فوراً");
})();

// النسخة الحديثة (لكن نادراً ما نحتاجها الآن مع Modules)
(() => {
    console.log("IIFE مع arrow function");
})();
```

### Callback Functions

```javascript
// دالة تُمرر كـ argument لدالة أخرى لتنفيذها لاحقاً
function fetchData(callback) {
    setTimeout(() => {
        callback("البيانات جاهزة");
    }, 1000);
}

fetchData((result) => {
    console.log(result);  // "البيانات جاهزة" بعد ثانية
});

// Callback Hell — مشكلة callback في callback
fetchData1((data1) => {
    fetchData2(data1, (data2) => {
        fetchData3(data2, (data3) => {
            console.log(data3);
        });
    });
});
// الحل: Promises + async/await (لاحقاً)
```

---

<a name="6-المصفوفات"></a>
## 6️⃣ المصفوفات (Arrays)

### إنشاء المصفوفات
```javascript
const arr1 = [1, 2, 3, 4, 5];
const arr2 = new Array(1, 2, 3);  // نفس الشيء لكن الأفضل []
const arr3 = Array.from("hello");  // ['h', 'e', 'l', 'l', 'o']
const arr4 = Array(5).fill(0);     // [0, 0, 0, 0, 0]
```

### الوصول والتعديل
```javascript
const arr = [10, 20, 30, 40, 50];
arr[0]      // 10 (فهرس يبدأ من 0)
arr[arr.length - 1]  // 50 (آخر عنصر)
arr[-1]     // undefined (لا يدعم الفهارس السالبة — Python يفعل)

arr[2] = 999;   // [10, 20, 999, 40, 50]
arr.length = 3; // [10, 20, 999] (اقتطاع!)
```

### إضافة وحذف العناصر
```javascript
const arr = [1, 2, 3];

// نهاية
arr.push(4);         // [1, 2, 3, 4]  — يضيف في النهاية
arr.pop();           // [1, 2, 3]     — يحذف من النهاية ويعيد المحذوف

// بداية
arr.unshift(0);      // [0, 1, 2, 3]  — يضيف في البداية (بطيء)
arr.shift();         // [1, 2, 3]     — يحذف من البداية (بطيء)

// وسط
arr.splice(1, 1);         // يحذف عنصر واحد من الفهرس 1 → [1, 3]
arr.splice(1, 0, 1.5);    // يضيف 1.5 في الفهرس 1 → [1, 1.5, 3]
arr.splice(1, 1, "a");    // يستبدل الفهرس 1 → [1, "a", 3]
```

### تكرار المصفوفات

```javascript
const arr = [1, 2, 3, 4, 5];

// forEach — ينفذ دالة لكل عنصر (لا يرجع شيء)
arr.forEach((value, index, array) => {
    console.log(`arr[${index}] = ${value}`);
});

// map — يرجع مصفوفة جديدة بنفس الطول
const doubled = arr.map(x => x * 2);   // [2, 4, 6, 8, 10]

// filter — يرجع مصفوفة جديدة تحقق الشرط
const evens = arr.filter(x => x % 2 === 0);   // [2, 4]

// reduce — يدمج المصفوفة في قيمة واحدة
const sum = arr.reduce((acc, x) => acc + x, 0);   // 15
const max = arr.reduce((a, b) => Math.max(a, b));  // 5
const count = arr.reduce((acc, x) => {
    acc[x] = (acc[x] || 0) + 1;
    return acc;
}, {});  // عدّ تكرارات العناصر

// find — يرجع أول عنصر يحقق الشرط (أو undefined)
const firstEven = arr.find(x => x % 2 === 0);   // 2

// findIndex — يرجع فهرس أول عنصر يحقق الشرط
const idx = arr.findIndex(x => x > 3);   // 3

// some — هل يوجد عنصر يحقق الشرط؟
arr.some(x => x > 4);   // true

// every — هل كل العناصر تحقق الشرط؟
arr.every(x => x > 0);  // true

// includes — هل المصفوفة تحتوي على قيمة؟
arr.includes(3);  // true
```

### ترتيب وتحويل
```javascript
const arr = [3, 1, 4, 1, 5, 9];

// sort — يرتب كنصوص (text) افتراضياً!
arr.sort();  // [1, 1, 3, 4, 5, 9] — مصادفة صحيحة هنا
[10, 2, 1].sort();  // [1, 10, 2] ← خطأ!

// sort الصحيح مع مقارن
arr.sort((a, b) => a - b);   // تصاعدي [1, 1, 3, 4, 5, 9]
arr.sort((a, b) => b - a);   // تنازلي [9, 5, 4, 3, 1, 1]

// reverse
arr.reverse();

// join — يحول المصفوفة إلى نص
[1, 2, 3].join(" - ");  // "1 - 2 - 3"

// slice — يستخرج جزءاً من المصفوفة (لا يعدل الأصلية)
arr.slice(1, 4);     // العناصر من فهرس 1 إلى 3
arr.slice(-2);       // آخر عنصرين

// concat — يدمج مصفوفتين
[1, 2].concat([3, 4]);  // [1, 2, 3, 4]

// Spread operator — النسخة الحديثة
[...[1, 2], ...[3, 4]];  // [1, 2, 3, 4]

// flat — يفك المصفوفات المتداخلة
[1, [2, [3]]].flat(2);  // [1, 2, 3]

// flatMap — map + flat في خطوة
["hello world", "foo bar"].flatMap(s => s.split(" "));
// ["hello", "world", "foo", "bar"]
```

### مهم: immutability (عدم تعديل الأصلية)
```javascript
// push يعدل الأصلية — تجنبه إذا أمكن
const original = [1, 2, 3];
const copy1 = [...original, 4];    // [1, 2, 3, 4] ← original لم تتغير
const copy2 = original.concat(4);  // نفس الشيء

// حذف بدون تعديل الأصلية
const removed = original.filter(x => x !== 2);  // [1, 3]

// تحديث عنصر
const updated = original.map(x => x === 2 ? 999 : x);  // [1, 999, 3]
```

### Destructuring (تفكيك المصفوفات)
```javascript
const arr = [1, 2, 3, 4];

const [a, b] = arr;           // a=1, b=2
const [x, , z] = arr;         // x=1, z=3 (تجاهل الثاني)
const [first, ...rest] = arr; // first=1, rest=[2,3,4]
const [p, q, r, s, t = 0] = arr; // t=0 (قيمة افتراضية)

// Swap متغيرين
let m = 1, n = 2;
[m, n] = [n, m];  // m=2, n=1
```

---

<a name="7-الكائنات"></a>
## 7️⃣ الكائنات (Objects)

### إنشاء الكائنات
```javascript
// Object literal — الأكثر استخداماً
const user = {
    name: "Ahmed",
    age: 25,
    "full name": "Ahmed Ali",  // key بمسافة → لازم ""
    greet() {                   // ميثود اختصار (ES6)
        return `Hello, I'm ${this.name}`;
    }
};

// Dynamic keys
const key = "email";
const obj = {
    [key]: "ahmed@email.com"  // المفتاح سيكون "email"
};
```

### الوصول والتعديل
```javascript
user.name         // "Ahmed" — Dot notation
user["full name"] // "Ahmed Ali" — Bracket notation (لازم للمفاتيح بمسافة)
user["age"]       // 25 — bracket مع string

// إضافة/تعديل
user.email = "ahmed@email.com";
user["phone"] = "0123456789";

// حذف
delete user.phone;

// التحقق من وجود مفتاح
"name" in user      // true
user.hasOwnProperty("name")  // true
user.xxx === undefined        // صحيح لكن ليس دقيقاً (القيمة قد تكون undefined)
```

### Object Methods
```javascript
const obj = { a: 1, b: 2, c: 3 };

// المفاتيح والقيم
Object.keys(obj);    // ["a", "b", "c"]
Object.values(obj);  // [1, 2, 3]
Object.entries(obj); // [["a",1], ["b",2], ["c",3]]

// التكرار على الكائن
for (const [key, value] of Object.entries(obj)) {
    console.log(key, value);
}

// دمج الكائنات
const x = { a: 1, b: 2 };
const y = { b: 3, c: 4 };
const merged = { ...x, ...y };  // { a: 1, b: 3, c: 4 }

// Object.assign — الطريقة القديمة
const merged2 = Object.assign({}, x, y);

// تجميد الكائن (منع التعديل)
const frozen = Object.freeze({ a: 1 });
frozen.a = 2;  // Silent failure (في strict mode: TypeError)

// منع الإضافة فقط
const sealed = Object.seal({ a: 1 });
sealed.b = 2;  // ممنوع
sealed.a = 3;  // مسموح
```

### this Keyword
```javascript
// this يشير إلى "من يملك" الدالة وقت التنفيذ

// 1. في دالة عادية → this = global (window في المتصفح)
function show() {
    console.log(this);  // window (غير strict mode)
}

// 2. في object method → this = الكائن
const user = {
    name: "Ali",
    greet() {
        console.log(this.name);  // "Ali"
    }
};

// 3. في arrow function → this من الخارج (Lexical this)
const user2 = {
    name: "Ali",
    greet: () => {
        console.log(this.name);  // undefined (this = window)
    }
};

// 4. في constructor → this = الكائن الجديد
function Person(name) {
    this.name = name;
}

// 5. bind / call / apply — نتحكم بـ this
function sayHi() {
    console.log(this.name);
}
const ali = { name: "Ali" };
sayHi.call(ali);     // "Ali"
sayHi.apply(ali);    // "Ali"
const bound = sayHi.bind(ali);
bound();             // "Ali"
```

### Destructuring الكائنات
```javascript
const user = { name: "Ahmed", age: 25, city: "Cairo" };

const { name, age } = user;           // name = "Ahmed", age = 25
const { name: n, city: c } = user;    // n = "Ahmed", c = "Cairo" (rename)
const { email = "default@email.com" } = user; // قيمة افتراضية

// مع الـ REST
const { name, ...rest } = user;
// name = "Ahmed", rest = { age: 25, city: "Cairo" }

// في Function parameters
function printUser({ name, age, city = "Unknown" }) {
    console.log(`${name}, ${age}, ${city}`);
}
printUser({ name: "Ali", age: 30 });
```

### Shorthand Properties
```javascript
const name = "Ahmed";
const age = 25;

// قديماً
const user1 = { name: name, age: age };

// حديثاً
const user2 = { name, age };  // نفس الشيء
```

---

<a name="8-dom"></a>
## 8️⃣ التحكم في DOM (Document Object Model)

### ما هو DOM؟
- تمثيل هيكلي لصفحة HTML على شكل شجرة
- JS تستطيع قراءة وتعديل وحذف وإضافة أي عنصر

### اختيار العناصر

```javascript
// عنصر واحد
document.getElementById("myId");         // بالـ ID
document.querySelector(".myClass");     // بأي CSS selector (يرجع أول عنصر)

// عدة عناصر
document.getElementsByClassName("cls"); // HTMLCollection (حي — يتغير مع DOM)
document.getElementsByTagName("div");   // HTMLCollection
document.querySelectorAll(".cls");      // NodeList (ثابت — الأفضل)

// الفرق:
// querySelectorAll يرجع NodeList → forEach يعمل عليه
// getElementsByClassName يرجع HTMLCollection → لا يعمل عليه forEach
```

### قراءة وتعديل المحتوى
```javascript
const el = document.querySelector(".myClass");

// textContent — النص فقط (آمن، سريع)
el.textContent = "نص جديد";
console.log(el.textContent);

// innerText — النص مع مراعاة CSS (بطيء)
el.innerText = "نص آخر";

// innerHTML — HTML (⚠️ خطر XSS — تجنبه مع إدخال المستخدم)
el.innerHTML = "<strong>نص عريض</strong>";

// value — لحقول الإدخال
document.querySelector("input").value = "قيمة جديدة";
```

### تعديل الـ Attributes
```javascript
const img = document.querySelector("img");
img.src = "new-image.jpg";
img.alt = "وصف الصورة";
img.getAttribute("src");     // "new-image.jpg"
img.setAttribute("title", "نص عند التمرير");
img.hasAttribute("alt");     // true
img.removeAttribute("alt");
```

### تعديل الـ Classes
```javascript
const el = document.querySelector(".myClass");

el.classList.add("active");          // يضيف class
el.classList.remove("hidden");       // يحذف class
el.classList.toggle("dark-mode");    // يبدل (يضيف لو مش موجود، يحذف لو موجود)
el.classList.replace("old", "new");  // يستبدل
el.classList.contains("active");     // true/false — هل يحتوي على class؟
```

### تعديل الـ Style
```javascript
const el = document.querySelector(".myClass");

// Inline styles
el.style.color = "red";
el.style.backgroundColor = "#333";  // camelCase (بدون -
el.style.fontSize = "16px";
el.style.display = "flex";

// قراءة style المحسوب
getComputedStyle(el).color;  // لون CSS الفعلي بعد تطبيق كل القواعد
```

### إنشاء وإضافة عناصر
```javascript
// إنشاء
const div = document.createElement("div");
div.textContent = "مرحباً";
div.className = "box";
div.dataset.id = "123";  // data-id="123"

// إضافة
document.body.appendChild(div);           // في النهاية
document.body.prepend(div);               // في البداية
document.body.insertBefore(div, ref);     // قبل عنصر معين
document.querySelector(".container").append(div);  // في نهاية container

// HTML الحديث
el.insertAdjacentHTML("beforeend", "<span>نص</span>");
// positions: beforebegin, afterbegin, beforeend, afterend

// clone
const clone = el.cloneNode(true);  // true = مع كل الأطفال
```

### التنقل في DOM
```javascript
const el = document.querySelector(".myClass");

el.parentElement           // الأب
el.children                // كل الأبناء (HTMLCollection)
el.firstElementChild       // أول ابن
el.lastElementChild        // آخر ابن
el.previousElementSibling  // الأخ الذي قبله
el.nextElementSibling      // الأخ الذي بعده
el.closest(".container")   // أقرب أب يحقق الـ selector
```

---

<a name="9-الأحداث"></a>
## 9️⃣ الأحداث (Events)

### إضافة الأحداث
```javascript
const btn = document.querySelector("button");

// 1. addEventListener (الأفضل — يسمح بعدة مستمعين)
btn.addEventListener("click", () => {
    console.log("نقر!");
});

// 2. onclick — خاصية مباشرة (كتابة واحدة فقط)
btn.onclick = () => console.log("نقر!");

// 3. HTML attribute (قديم — تجنبه)
// <button onclick="handleClick()">انقر</button>
```

### Event Object
```javascript
btn.addEventListener("click", (event) => {
    event.target          // العنصر الذي حدث عليه الحدث
    event.currentTarget   // العنصر الذي عليه الـ listener
    event.type            // "click"
    event.preventDefault();  // منع السلوك الافتراضي
    event.stopPropagation(); // منع propagation (الصعود للأب)
});
```

### Propagation (Bubbling vs Capturing)
```javascript
// Bubbling (افتراضي): الحدث يصعد من الابن إلى الأب
parent.addEventListener("click", () => console.log("parent"));
child.addEventListener("click", () => console.log("child"));
// نقر على child → "child" → "parent"

// Capturing: الحدث ينزل من الأب إلى الابن (phase: true)
parent.addEventListener("click", () => console.log("parent"), true);
child.addEventListener("click", () => console.log("child"));
// نقر على child → "parent" → "child"

// stopPropagation يوقف الصعود
child.addEventListener("click", (e) => {
    e.stopPropagation();
    console.log("child فقط");
});
```

### Event Delegation
```javascript
// بدلاً من إضافة listener لكل عنصر، نضيف واحد للأب
const list = document.querySelector("ul");

list.addEventListener("click", (e) => {
    if (e.target.tagName === "LI") {
        console.log("نقرت على:", e.target.textContent);
    }
});
// يفيد مع العناصر المضافة ديناميكياً
```

### أنواع الأحداث الشائعة
```javascript
// Mouse
click, dblclick, mouseover, mouseout, mouseenter, mouseleave, mousemove

// Keyboard
keydown, keyup, keypress (قديم)
input.addEventListener("keydown", (e) => {
    console.log(e.key);    // الحرف المضغوط
    console.log(e.code);   // الكود الفيزيائي (KeyA, ArrowUp)
    console.log(e.ctrlKey, e.shiftKey);  // modifiers
});

// Form
submit, reset, focus, blur, change, input
form.addEventListener("submit", (e) => {
    e.preventDefault();  // منع إعادة تحميل الصفحة
    console.log("تم الإرسال");
});

// Window / Document
DOMContentLoaded, load, resize, scroll, beforeunload
window.addEventListener("resize", () => {
    console.log(window.innerWidth);
});

// Custom Events
const event = new CustomEvent("userLogin", { detail: { name: "Ali" } });
window.dispatchEvent(event);
window.addEventListener("userLogin", (e) => {
    console.log(e.detail.name);  // "Ali"
});
```

### Debounce و Throttle
```javascript
// Debounce — ينفذ بعد توقف المستخدم عن الكتابة
function debounce(fn, delay = 300) {
    let timer;
    return (...args) => {
        clearTimeout(timer);
        timer = setTimeout(() => fn(...args), delay);
    };
}

// استخدام: البحث المباشر
searchInput.addEventListener("input", debounce((e) => {
    fetchResults(e.target.value);  // بعد 300ms من توقف الكتابة
}));

// Throttle — ينفذ مرة كل مدة محددة
function throttle(fn, delay = 100) {
    let last = 0;
    return (...args) => {
        const now = Date.now();
        if (now - last >= delay) {
            last = now;
            fn(...args);
        }
    };
}

// استخدام: الـ scroll أو resize
window.addEventListener("scroll", throttle(() => {
    console.log("مرة كل 100ms");
}));
```

---

<a name="10-es6"></a>
## 🔟 ES6+ الحديث (ES6 → ES2024)

### Let & Const (بدلاً من var)
```javascript
// var: function-scope, hoisting, يمكن إعادة تعريفه
// let: block-scope, hoisting لكن في temporal dead zone
// const: block-scope, لا يمكن إعادة التعيين

// Temporal Dead Zone (TDZ)
console.log(x);  // ReferenceError (في الـ TDZ)
let x = 5;
```

### Template Literals (``)
```javascript
const name = "Ali";
const age = 25;

// قديماً
const msg1 = "اسمي " + name + " وعمري " + age;

// حديثاً
const msg2 = `اسمي ${name} وعمري ${age}`;

// متعدد الأسطر
const html = `
    <div>
        <h1>${name}</h1>
        <p>العمر: ${age}</p>
    </div>
`;

// Tagged Templates — متقدم
function highlight(strings, ...values) {
    return strings.reduce((acc, str, i) =>
        `${acc}${str}<strong>${values[i] || ""}</strong>`, ""
    );
}
const result = highlight`Hello ${name}, age ${age}`;
// "Hello <strong>Ali</strong>, age <strong>25</strong>"
```

### Spread & Rest (...)
```javascript
// Spread — يفك المصفوفات/الكائنات
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combined = [...arr1, ...arr2];  // [1,2,3,4,5,6]

const obj1 = { a: 1, b: 2 };
const obj2 = { c: 3 };
const merged = { ...obj1, ...obj2, b: 99 };  // {a:1, b:99, c:3}

// Rest — يجمع الباقي
const [first, ...rest] = [1, 2, 3, 4];  // first=1, rest=[2,3,4]
const { name, ...details } = { name: "Ali", age: 25, city: "Cairo" };
// name="Ali", details={age:25, city:"Cairo"}

// في الدوال
function logAll(...args) {
    console.log(args);  // [1, 2, 3]
}
logAll(1, 2, 3);

// Math.max مع Spread
Math.max(...[1, 5, 3, 9, 2]);  // 9
```

### Destructuring (تفصيل في الأقسام السابقة)

### Default Parameters
```javascript
function fetchData(url, timeout = 5000, retries = 3) {
    console.log(url, timeout, retries);
}
fetchData("/api");  // "/api", 5000, 3
fetchData("/api", 1000, 0);  // "/api", 1000, 0
```

### Promises (سيأتي تفصيلها في الـ Async)
```javascript
const promise = new Promise((resolve, reject) => {
    // ... عمل غير متزامن
    if (success) resolve(value);
    else reject(error);
});
```

### Optional Chaining & Nullish Coalescing
```javascript
// Optional Chaining ?.
const user = {};
console.log(user?.address?.city);  // undefined (بدون خطأ)

// Nullish Coalescing ??
const value = 0;
console.log(value ?? 10);  // 0 (لأن 0 ليس null/undefined)
console.log(value || 10);  // 10 (لأن 0 falsy)
```

### Logical Assignment (ES2021)
```javascript
let a = null;
let b = 5;

a ||= 10;   // a = a || 10  → a = 10
a &&= 20;   // a = a && 20  → a = 20 (لأن a=10 truthy)
a ??= 30;   // a = a ?? 30  → a = 20 (لأن a ليس null/undefined)
```

### Array Methods الجديدة
```javascript
// at() — يدعم الفهارس السالبة (ES2022)
const arr = [10, 20, 30, 40];
arr.at(-1);  // 40 (آخر عنصر)
arr.at(-2);  // 30

// toSorted, toReversed, toSpliced, toReversed (ES2023) — نسخ آمنة
const sorted = arr.toSorted();  // arr لم يتغير
```

### Records & Tuples (ES2024 — متقدم)
```javascript
// مقترح — deep immutable structures
// const record = #{ a: 1, b: #{ c: 2 } };  // لم يدعم بعد في كل المتصفحات
```

---

<a name="11-async"></a>
## 1️⃣1️⃣ البرمجة غير المتزامنة (Async JavaScript)

### مقدمة: Sync vs Async

```javascript
// Synchronous — تنفيذ تسلسلي
console.log("1");
console.log("2");  // ينتظر حتى تنتهي 1
console.log("3");

// Asynchronous — تنفيذ غير متسلسل
console.log("1");
setTimeout(() => console.log("2"), 1000);  // ينفذ بعد ثانية
console.log("3");
// النتيجة: "1", "3", "2" ← لاحظ: 3 طبعت قبل 2!
```

### لماذا نحتاج Async؟
- طلبات الشبكة (API calls)
- قراءة ملفات
- انتظار المستخدم (setTimeout, events)
- قاعدة بيانات
- الأفضل للمستخدم: الصفحة لا تتجمد أثناء العمل

### Event Loop (حلقة الأحداث)
```
Call Stack (مكدس التنفيذ) ← الكود العادي
     ↓
Web APIs (setTimeout, fetch, DOM events) ← المهام غير المتزامنة
     ↓
Callback Queue (طابور الانتظار)
     ↓
Event Loop: تأكد من أن Call Stack فارغ ثم انقل من Callback Queue
```

```javascript
console.log("1");                    // Call Stack → يطبع فوراً
setTimeout(() => console.log("2"), 0); // Web API → Callback Queue
Promise.resolve().then(() => console.log("3")); // Microtask Queue
console.log("4");                    // Call Stack → يطبع فوراً

// الترتيب: "1", "4", "3", "2"
// الـ Microtasks (Promises) تسبق الـ Macrotasks (setTimeout)
```

### 1. Callbacks (الطريقة القديمة)
```javascript
function getUser(id, callback) {
    setTimeout(() => {
        callback({ id, name: "Ali" });
    }, 1000);
}

function getPosts(userId, callback) {
    setTimeout(() => {
        callback(["Post 1", "Post 2"]);
    }, 500);
}

// Callback Hell
getUser(1, (user) => {
    console.log(user);
    getPosts(user.id, (posts) => {
        console.log(posts);
        // لو احتجنا طلب ثالث → nesting أعمق
    });
});
```

### 2. Promises (ES6) — الحل الحديث
```javascript
// إنشاء Promise
const promise = new Promise((resolve, reject) => {
    const success = true;
    setTimeout(() => {
        if (success) resolve("✅ تم بنجاح");
        else reject("❌ حصل خطأ");
    }, 1000);
});

// استهلاك Promise
promise
    .then((result) => console.log(result))  // عند النجاح
    .catch((error) => console.error(error)) // عند الفشل
    .finally(() => console.log("انتهى"));    // دائماً

// تحويل callback إلى Promise
function getUser(id) {
    return new Promise((resolve) => {
        setTimeout(() => resolve({ id, name: "Ali" }), 1000);
    });
}

function getPosts(userId) {
    return new Promise((resolve) => {
        setTimeout(() => resolve(["Post 1", "Post 2"]), 500);
    });
}

// Chaining (تسلسل) — أسهل بكثير من Callback Hell
getUser(1)
    .then(user => getPosts(user.id))
    .then(posts => console.log(posts))
    .catch(err => console.error(err));
```

### Promise.all, Promise.race, Promise.allSettled

```javascript
const p1 = fetch("/api/data1").then(r => r.json());
const p2 = fetch("/api/data2").then(r => r.json());

// Promise.all — ينتظر كل الـ Promises (أو أول خطأ)
Promise.all([p1, p2])
    .then(([data1, data2]) => {
        console.log(data1, data2);
    })
    .catch(err => console.error("أحد الطلبات فشل", err));

// Promise.allSettled — ينتظر الكل حتى لو بعضها فشل
Promise.allSettled([p1, p2])
    .then(results => {
        results.forEach(r => {
            if (r.status === "fulfilled") console.log(r.value);
            if (r.status === "rejected") console.log(r.reason);
        });
    });

// Promise.race — يرجع أول Promise يكتمل (نجاح أو فشل)
Promise.race([p1, p2]).then(winner => console.log(winner));

// Promise.any — يرجع أول نجاح فقط (يتجاهل الفشل)
Promise.any([p1, p2]).then(firstSuccess => console.log(firstSuccess));
```

### 3. Async/Await (ES2017) — الأفضل والأحدث
```javascript
// async تجعل الدالة ترجع Promise تلقائياً
async function fetchUser(id) {
    // await ينتظر Promise
    const response = await fetch(`/api/user/${id}`);
    const user = await response.json();
    return user;
}

// استخدام
const user = await fetchUser(1);  // في async function فقط
console.log(user);

// Error Handling مع try/catch
async function loadData() {
    try {
        const user = await getUser(1);
        const posts = await getPosts(user.id);
        console.log(user, posts);
    } catch (error) {
        console.error("خطأ:", error);
    }
}

// التنفيذ المتوازي (Parallel) — أسرع
async function loadParallel() {
    const [user, config] = await Promise.all([
        fetch("/api/user/1").then(r => r.json()),
        fetch("/api/config").then(r => r.json())
    ]);
    console.log(user, config);
}
// ⬆️ هذا أسرع 2x من await تسلسلي
```

### مثال تطبيقي: Fetch API

```javascript
// GET
async function getUsers() {
    try {
        const res = await fetch("https://jsonplaceholder.typicode.com/users");
        if (!res.ok) throw new Error(`HTTP ${res.status}`);
        const users = await res.json();
        return users;
    } catch (err) {
        console.error("فشل الطلب:", err);
        throw err;
    }
}

// POST
async function createUser(data) {
    const res = await fetch("https://api.example.com/users", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(data)
    });
    return res.json();
}

// AbortController — إلغاء الطلب
async function fetchWithTimeout(url, timeout = 5000) {
    const controller = new AbortController();
    const id = setTimeout(() => controller.abort(), timeout);

    try {
        const res = await fetch(url, { signal: controller.signal });
        return await res.json();
    } finally {
        clearTimeout(id);
    }
}
```

### Error Handling المتقدم
```javascript
async function safeFetch(url) {
    try {
        const res = await fetch(url);
        if (!res.ok) {
            throw new Error(`فشل الطلب: ${res.status}`);
        }
        return await res.json();
    } catch (err) {
        if (err.name === "AbortError") {
            console.log("تم إلغاء الطلب");
            return null;
        }
        // إعادة الخطأ للـ caller
        throw new NetworkError("تعذر الاتصال", err);
    }
}

// Custom Error Classes
class NetworkError extends Error {
    constructor(message, original) {
        super(message);
        this.name = "NetworkError";
        this.original = original;
    }
}
```

---

<a name="12-oop"></a>
## 1️⃣2️⃣ Classes و OOP

### Class Syntax (ES6)
```javascript
class Animal {
    // Constructor — ينفذ عند إنشاء كائن جديد
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    // Method
    speak() {
        console.log(`${this.name} يصدر صوتاً`);
    }

    // Getter
    get info() {
        return `${this.name}, ${this.age} سنة`;
    }

    // Setter
    set info(value) {
        [this.name, this.age] = value.split(", ");
    }

    // Static method — ينتمي للـ Class نفسه، ليس للكائن
    static createDefault() {
        return new Animal("حيوان", 0);
    }
}

// الاستخدام
const dog = new Animal("كلب", 3);
dog.speak();        // "كلب يصدر صوتاً"
console.log(dog.info);  // "كلب, 3 سنة" (getter)
dog.info = "قط, 2";
console.log(dog.name);  // "قط"

const defaultAnimal = Animal.createDefault();  // static
```

### Inheritance (الوراثة)
```javascript
class Dog extends Animal {
    constructor(name, age, breed) {
        super(name, age);  // لازم نستدعي constructor الأب
        this.breed = breed;
    }

    // Override
    speak() {
        console.log(`${this.name} ينبح: هاو هاو!`);
    }

    // Method جديد
    fetch() {
        console.log(`${this.name} يجلب الكرة`);
    }
}

const myDog = new Dog("Buddy", 2, "Golden");
myDog.speak();  // "Buddy ينبح: هاو هاو!"
myDog.fetch();  // "Buddy يجلب الكرة"
console.log(myDog.info);  // موروث من Animal
```

### Private Fields (#)
```javascript
class BankAccount {
    #balance = 0;  // خاص — لا يمكن الوصول من الخارج

    constructor(owner) {
        this.owner = owner;
    }

    deposit(amount) {
        if (amount <= 0) throw new Error("المبلغ يجب أن يكون موجباً");
        this.#balance += amount;
    }

    withdraw(amount) {
        if (amount > this.#balance) throw new Error("الرصيد غير كافٍ");
        this.#balance -= amount;
    }

    get balance() {
        return this.#balance;
    }
}

const account = new BankAccount("Ali");
account.deposit(1000);
console.log(account.balance);  // 1000
// console.log(account.#balance);  // ❌ SyntaxError
```

### Prototypes (ما وراء الـ Class)
```javascript
// JavaScript تستخدم Prototypal inheritance (ليست class-based حقيقية)

// كل كائن له __proto__ يشير إلى prototype الأب
const arr = [1, 2, 3];
console.log(arr.__proto__ === Array.prototype);  // true
console.log(Array.prototype.__proto__ === Object.prototype);  // true

// Class مجرد سكر تركيبي فوق الـ Prototype
class User {}
console.log(typeof User);  // "function" ← الـ Class مجرد function!

// إضافة method إلى prototype
Array.prototype.last = function() {
    return this[this.length - 1];
};
console.log([1, 2, 3].last());  // 3
// ⚠️ لا تفعل هذا في الإنتاج — يمكن أن يكسر المكتبات الأخرى
```

### Composition vs Inheritance
```javascript
// Inheritance (وراثة):
// class Dog extends Animal → "هو" relationship

// Composition (تجميع):
// const dog = { name: "Buddy", walk: walkFn } → "لديه" relationship

// Composition أفضل في JS لأن الوراثة تسبب مشاكل مع الوقت

// مثال Composition
function canWalk(obj) {
    return {
        ...obj,
        walk: () => console.log(`${obj.name} يمشي`)
    };
}

function canBark(obj) {
    return {
        ...obj,
        bark: () => console.log(`${obj.name} ينبح`)
    };
}

const dog = canBark(canWalk({ name: "Buddy" }));
dog.walk();  // "Buddy يمشي"
dog.bark();  // "Buddy ينبح"
```

---

<a name="13-errors"></a>
## 1️⃣3️⃣ Error Handling

### Try / Catch / Finally
```javascript
try {
    // كود قد يخطئ
    const result = riskyOperation();
    console.log(result);
} catch (error) {
    // ينفذ إذا حدث خطأ
    console.error("حدث خطأ:", error.message);
} finally {
    // ينفذ دائماً (نجاح أو فشل)
    cleanup();
}
```

### أنواع الأخطاء
```javascript
try {
    throw new Error("خطأ عام");
    throw new TypeError("خطأ نوع");
    throw new RangeError("خارج النطاق");
    throw new ReferenceError("مرجع غير موجود");
    throw new SyntaxError("خطأ نحوي");
} catch (e) {
    console.log(e.name);    // نوع الخطأ
    console.log(e.message); // الرسالة
    console.log(e.stack);   // تتبع الاستدعاءات
}
```

### Custom Errors
```javascript
class ValidationError extends Error {
    constructor(field, message) {
        super(message);
        this.name = "ValidationError";
        this.field = field;
    }
}

function validateUser(user) {
    if (!user.name) {
        throw new ValidationError("name", "الاسم مطلوب");
    }
    if (user.age < 0) {
        throw new ValidationError("age", "العمر لا يمكن أن يكون سالباً");
    }
}

try {
    validateUser({ name: "", age: -5 });
} catch (err) {
    if (err instanceof ValidationError) {
        console.log(`حقل ${err.field}: ${err.message}`);
    } else {
        console.log("خطأ غير متوقع:", err);
    }
}
```

### Global Error Handling
```javascript
// في المتصفح
window.onerror = (msg, url, line, col, error) => {
    console.error("خطأ عالمي:", msg);
    // أرسل للسيرفر
    fetch("/api/log-error", { method: "POST", body: JSON.stringify({ msg, url, line, col }) });
    return true;  // يمنع السلوك الافتراضي
};

// للـ Promises غير المعالجة
window.onunhandledrejection = (event) => {
    console.error("Promise غير معالج:", event.reason);
};
```

---

<a name="14-modules"></a>
## 1️⃣4️⃣ Modules (ES Modules)

### Export
```javascript
// utils.js

// Named export
export const PI = 3.14;
export function double(x) { return x * 2; }
export class Calculator { ... }

// أو
const PI = 3.14;
function double(x) { return x * 2; }
export { PI, double };

// Default export (واحد لكل ملف)
export default function multiply(a, b) {
    return a * b;
}

// Re-export
export { double as utilsDouble } from "./math.js";
export * from "./constants.js";
```

### Import
```javascript
// Named import (يجب استخدام exact names)
import { PI, double } from "./utils.js";

// Alias
import { PI as piValue, double as doubler } from "./utils.js";

// Import كل شيء
import * as Utils from "./utils.js";
console.log(Utils.PI);
Utils.double(5);

// Default import
import multiply from "./utils.js";  // الاسم يمكن أن يكون أي شيء
multiply(3, 4);

// Mixed
import multiply, { PI, double } from "./utils.js";
```

### Dynamic Import
```javascript
// Static import في البداية
// import { heavyFunction } from "./heavy.js";

// Dynamic import — يحمل عند الحاجة فقط
async function loadModule() {
    if (needHeavy) {
        const module = await import("./heavy.js");
        module.heavyFunction();
    }
}

// لماذا؟ — تحسين سرعة التحميل الأولي
button.addEventListener("click", async () => {
    const { showChart } = await import("./chart.js");
    showChart();
});
```

### module vs script
```html
<!-- Script عادي → variables عامة -->
<script src="script.js"></script>

<!-- Module → variables داخل module فقط -->
<script type="module" src="main.js"></script>

<!-- Module في HTML inline -->
<script type="module">
    import { something } from "./module.js";
</script>
```

### الفروقات بين Modules و Scripts
| الخاصية | Script عادي | Module |
|---------|-----------|--------|
| الـ Scope | Global | Own scope |
| Strict mode | اختياري | تلقائي |
| import/export | غير مدعوم | مدعوم |
| Defer افتراضي | لا | نعم |
| Multiple scripts | يمنع التكرار | يسمح |

---

<a name="15-browser-apis"></a>
## 1️⃣5️⃣ Browser APIs (واجهات المتصفح)

### localStorage & sessionStorage
```javascript
// localStorage — يبقى حتى يحذفه المستخدم
localStorage.setItem("key", "value");
localStorage.getItem("key");       // "value"
localStorage.removeItem("key");
localStorage.clear();
localStorage.length;               // عدد العناصر

// sessionStorage — يحذف عند إغلاق التبويب
sessionStorage.setItem("key", "value");

// ⚠️ تخزين JSON
const user = { name: "Ali", age: 25 };
localStorage.setItem("user", JSON.stringify(user));
const saved = JSON.parse(localStorage.getItem("user"));

// ⚠️ الحد: 5-10 MB لكل domain
```

### Geolocation API
```javascript
navigator.geolocation.getCurrentPosition(
    (position) => {
        console.log("Latitude:", position.coords.latitude);
        console.log("Longitude:", position.coords.longitude);
    },
    (error) => {
        console.error("خطأ:", error.message);  // user denied, timeout, etc
    },
    { enableHighAccuracy: true, timeout: 10000 }
);
```

### Notifications API
```javascript
async function showNotification(title, body) {
    if (Notification.permission === "granted") {
        new Notification(title, { body, icon: "/icon.png" });
    } else if (Notification.permission !== "denied") {
        const permission = await Notification.requestPermission();
        if (permission === "granted") {
            new Notification(title, { body });
        }
    }
}
```

### Clipboard API
```javascript
async function copyToClipboard(text) {
    try {
        await navigator.clipboard.writeText(text);
        console.log("تم النسخ");
    } catch (err) {
        console.error("فشل النسخ:", err);
    }
}

async function readFromClipboard() {
    try {
        const text = await navigator.clipboard.readText();
        console.log("المحتوى:", text);
    } catch (err) {
        console.error("فشل القراءة:", err);
    }
}
```

### Media Query (CSS في JS)
```javascript
const mq = window.matchMedia("(max-width: 768px)");

// التحقق الحالي
if (mq.matches) {
    console.log("شاشة صغيرة");
}

// الاستماع للتغيير
mq.addEventListener("change", (e) => {
    if (e.matches) console.log("انتقل لشاشة صغيرة");
    else console.log("انتقل لشاشة كبيرة");
});
```

### Intersection Observer (للمشاهدة)
```javascript
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            console.log("العنصر أصبح مرئياً:", entry.target);
            entry.target.classList.add("visible");
            observer.unobserve(entry.target);  // لمرة واحدة
        }
    });
}, { threshold: 0.5 });  // 50% من العنصر مرئي

// استخدمنا
document.querySelectorAll(".lazy-image").forEach(img => observer.observe(img));
```

### Resize Observer
```javascript
const observer = new ResizeObserver(entries => {
    for (const entry of entries) {
        console.log(entry.contentRect.width, entry.contentRect.height);
    }
});
observer.observe(document.querySelector(".container"));
```

### Mutation Observer
```javascript
const observer = new MutationObserver(mutations => {
    mutations.forEach(mutation => {
        if (mutation.type === "childList") {
            console.log("تمت إضافة/حذف عناصر");
        }
        if (mutation.type === "attributes") {
            console.log(`تغير attribute: ${mutation.attributeName}`);
        }
    });
});

observer.observe(document.getElementById("target"), {
    childList: true,    // راقب إضافة/حذف الأبناء
    attributes: true,   // راقب تغير الـ attributes
    subtree: true       // راقب كل الشجرة
});
```

---

<a name="16-advanced"></a>
## 1️⃣6️⃣ أدوات وتطبيقات متقدمة

### Performance Tips
```javascript
// 1. تجنب التعديل المتكرر للـ DOM — استخدم DocumentFragment
const fragment = document.createDocumentFragment();
for (let i = 0; i < 1000; i++) {
    const el = document.createElement("div");
    el.textContent = i;
    fragment.appendChild(el);
}
document.body.appendChild(fragment);  // تعديل DOM واحد فقط

// 2. Debounce و Throttle (شرح سابق)

// 3. Virtual Scrolling (للقوائم الكبيرة جداً)
// بدلاً من render كل 10000 عنصر، render المرئي فقط

// 4. Lazy Loading للصور
// <img loading="lazy" src="image.jpg">

// 5. Web Workers للعمليات الثقيلة
const worker = new Worker("worker.js");
worker.postMessage({ type: "compute", data: bigArray });
worker.onmessage = (e) => {
    console.log("النتيجة:", e.data);
};
```

### Web Workers (خيوط متعددة)
```javascript
// worker.js
self.onmessage = function(e) {
    const result = heavyComputation(e.data);
    self.postMessage(result);
};

function heavyComputation(data) {
    // عمل ثقيل لا يؤثر على الـ UI
    return data.reduce((acc, x) => acc + x, 0);
}

// Main thread
const worker = new Worker("worker.js");
worker.postMessage([1,2,3,4,5]);
worker.onmessage = (e) => console.log("Result:", e.data);
worker.onerror = (err) => console.error("Worker error:", err);
worker.terminate();  // إيقاف العامل
```

### Service Workers (PWA)
```javascript
// تسجيل
if ("serviceWorker" in navigator) {
    navigator.serviceWorker.register("/sw.js")
        .then(() => console.log("SW مسجل"))
        .catch(err => console.error("SW فشل:", err));
}

// sw.js: Cache стратегия
self.addEventListener("fetch", (event) => {
    event.respondWith(
        caches.match(event.request).then(cached => {
            // Cache-first
            return cached || fetch(event.request).then(response => {
                return caches.open("v1").then(cache => {
                    cache.put(event.request, response.clone());
                    return response;
                });
            });
        })
    );
});
```

### Testing JavaScript (أساسيات)

```javascript
// 1. وحدة اختبار بسيطة
function assert(condition, message) {
    if (!condition) {
        throw new Error(`❌ فشل: ${message}`);
    }
    console.log(`✅ نجح: ${message}`);
}

function testAdd() {
    assert(add(2, 3) === 5, "add(2, 3) = 5");
    assert(add(-1, 1) === 0, "add(-1, 1) = 0");
    assert(add(0, 0) === 0, "add(0, 0) = 0");
}

// 2. Vitest (مكتبة اختبار)
// npm install -D vitest
// import { describe, it, expect } from "vitest";
// it("adds 1 + 2 = 3", () => {
//     expect(add(1, 2)).toBe(3);
// });
```

### Debugging Techniques
```javascript
// 1. console.table
console.table([{name:"Ali",age:25},{name:"Sara",age:30}]);

// 2. console.trace — تتبع الاستدعاءات
function a() { b(); }
function b() { console.trace(); }
a();  // يطبع مسار الاستدعاء: a → b

// 3. Breakpoints في DevTools
// debugger;  ← يوقف التنفيذ هناك

// 4. Performance.now()
const start = performance.now();
heavyTask();
console.log(`الوقت: ${performance.now() - start}ms`);

// 5. Error stack
try { throw new Error("test"); } catch (e) { console.log(e.stack); }
```

### Design Patterns في JavaScript

```javascript
// 🔷 Singleton
const Singleton = (function() {
    let instance;
    return {
        getInstance() {
            if (!instance) instance = { id: Math.random() };
            return instance;
        }
    };
})();

// 🔷 Observer
class EventBus {
    constructor() {
        this.listeners = {};
    }
    on(event, fn) {
        (this.listeners[event] ||= []).push(fn);
    }
    emit(event, data) {
        (this.listeners[event] || []).forEach(fn => fn(data));
    }
    off(event, fn) {
        this.listeners[event] = (this.listeners[event] || []).filter(f => f !== fn);
    }
}

// 🔷 Module Pattern
const CounterModule = (function() {
    let count = 0;  // خاص
    return {
        increment() { count++; },
        decrement() { count--; },
        getCount() { return count; }
    };
})();

// 🔷 Factory
function createUser(type) {
    const users = {
        admin: { role: "admin", permissions: ["all"] },
        user: { role: "user", permissions: ["read"] },
        guest: { role: "guest", permissions: [] }
    };
    return { ...users[type], createdAt: new Date() };
}
```

### JavaScript Gotchas (أخطاء شائعة)

```javascript
// 1. مقارنة الكائنات
{} === {}  // false (كل كائن له reference مختلف)

// 2. Floating Point
0.1 + 0.2  // 0.30000000000000004  ← ليس 0.3
// الحل: (0.1 * 10 + 0.2 * 10) / 10

// 3. parseInt
parseInt("08")   // 0 (قديماً قبل ES5)
parseInt("08", 10) // 8 (دائماً حدد الـ radix)

// 4. Semicolons
function getObj() {
    return
    { name: "Ali" };  // يرجع undefined (لأن JS تضيف ; بعد return)
}

// 5. Sort
[1, 10, 2].sort();  // [1, 10, 2] (sort نصي)

// 6. typeof null
typeof null  // "object" ← خطأ تاريخي

// 7. forEach لا يحترم async
[1,2,3].forEach(async (x) => {
    await delay(1000);
    console.log(x);
});
console.log("انتهى");  // يطبع قبل الـ logs
// الحل: for...of

// 8. const مع الكائنات
const x = { a: 1 };
x.a = 2;  // مسموح (المحتوى يتغير، فقط المرجع ثابت)
```

### مشاريع تطبيقية لاختبار JavaScript

| المستوى | المشروع | المهارات المستهدفة |
|---------|--------|-------------------|
| 🟢 مبتدئ | Counter App | DOM, events, state |
| 🟢 مبتدئ | Todo App | CRUD, localStorage, arrays |
| 🟢 مبتدئ | Digital Clock | Date, setInterval, DOM |
| 🟡 متوسط | Weather App | Fetch API, async/await, DOM |
| 🟡 متوسط | Memory Game | Arrays, events, timer |
| 🟡 متوسط | Calculator | DOM, eval/safe evaluation, events |
| 🟡 متوسط | Tic-Tac-Toe | Logic, arrays, AI (minimax basics) |
| 🟡 متوسط | Quiz App | Objects, scoring, timer |
| 🟠 متقدم | Chess Game | Classes, AI, drag&drop, coordination |
| 🟠 متقدم | Chat App | WebSockets, async, users |
| 🔴 محترف | Code Editor | Syntax highlight, undo/redo, File API |
| 🔴 محترف | Excel Clone | Grid, formulas, selection |

---

## ✅ الخلاصة: ترتيب التعلم المقترح

| الأسبوع | الموضوع |
|---------|--------|
| 1 | أساسيات: variables, types, operators |
| 2 | Control flow, loops |
| 3 | Functions (declaration, expression, arrow) |
| 4 | Arrays (methods, iteration) |
| 5 | Objects (creation, methods, destructuring) |
| 6 | DOM manipulation |
| 7 | Events + forms |
| 8 | ES6+ (spread, rest, template literals) |
| 9 | Async: Callbacks + Promises |
| 10 | Async: async/await, fetch |
| 11 | Classes, OOP, Error handling |
| 12 | Modules + Browser APIs |
| 13-16 | مشاريع تطبيقية |

---

> **"JavaScript is the only language that people assume they don't need to learn before using it."**
>
> — مبرمج محترف
