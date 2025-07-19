---

## 📘 1. **Function Typing**

### 🔍 Nima bu?

Function typing — bu funksiyaning kiruvchi (argument) va chiquvchi (return) qiymatlariga aniq `type` belgilash.

### 🎯 Nima uchun kerak?

* Tizimda xatoliklar oldini olish
* Funksiya noto‘g‘ri turdagi qiymatlar bilan chaqilmasligini ta'minlash
* Kodni o‘qish va tushunishni yengillashtiradi (self-documenting code)

### ⚙️ Qayerda ishlatiladi?

* API funksiyalar
* Hisob-kitob (calculation) funksiyalar
* CRUD logika
* Validatsiya funksiyalari

### ✅ To‘g‘ri sintaksis:

```ts
function add(a: number, b: number): number {
  return a + b;
}
```

### ❌ Noto‘g‘ri:

```ts
function add(a, b) {
  return a + b; // No typing: xatoga ochiq
}
```

---

### 🧪 Misollar:

```ts
function greet(name: string): string {
  return `Hello, ${name}!`;
}

function isAdult(age: number): boolean {
  return age >= 18;
}
```

---

### 🧠 Mashqlar:

1. `multiply` nomli function yozing, `number` tipidagi ikkita argument qabul qilib, ularning ko‘paytmasini qaytarsin.
2. `getFullName` funksiyasi `firstname` va `lastname` qabul qilib, `string` tipida to‘liq ism qaytarsin.
3. `isEven` funksiyasi `number` tipidagi argumentni qabul qilib, `true` yoki `false` qaytarsin.
4. `roundToFixed` funksiyasi sonni `number` tipida olsin va 2 kasrga aylantirib `string` tipida qaytarsin.
5. `toUpper` funksiyasi `string` olsin va katta harflarda qaytarsin.

---

## 📘 2. **Optional va Default Parameters**

### 🔍 Nima bu?

Optional — funksiyaga argument topshirilsa ishlaydi, bo‘lmasa `undefined`.
Default — funksiyaga qiymat berilmasa, belgilangan default qiymat ishlaydi.

### 🎯 Nima uchun kerak?

* Har doim berilishi shart bo‘lmagan parametrlar uchun
* Foydalanuvchi interfeyslarda default qiymat belgilash
* Funksiyani yanada moslashuvchan qilish

### ⚙️ Sintaksis:

```ts
function log(message: string, userId?: string) { ... }

function greet(name: string = "Guest") { ... }
```

---

### 🧪 Misollar:

```ts
function register(username: string, role: string = "user") {
  console.log(`${username} is registered as ${role}`);
}

function notify(msg: string, icon?: string) {
  console.log(icon ? `${icon} ${msg}` : msg);
}
```

---

### 🧠 Mashqlar:

1. `calculatePrice(price: number, discount?: number)` – agar `discount` berilsa, chegirmani hisoblab qaytarsin.
2. `logUser(username: string = 'Guest')` – `Guest` deb avtomatik chiqarilsin.
3. `sendEmail(to: string, from?: string)` – agar `from` yo‘q bo‘lsa `noreply@example.com` deb chiqarilsin.
4. `greetUser(name?: string)` – agar `name` yo‘q bo‘lsa `Welcome!` chiqarilsin.
5. `sum(a: number, b: number = 10)` – ikkinchi qiymat kiritilmasa, 10 deb hisoblasin.

---

## 📘 3. **Rest Parameters** (`...args`)

### 🔍 Nima bu?

Rest parameters — funksiyaga noma’lum miqdordagi argumentlarni massiv sifatida olishga imkon beradi.

### 🎯 Nima uchun kerak?

* `Math.max`, `sum` kabi ko‘p qiymatli hisob-kitoblar
* Form/validation qiymatlari
* Massiv elementlar bilan ishlash

### ⚙️ Sintaksis:

```ts
function sum(...nums: number[]): number {
  return nums.reduce((acc, val) => acc + val, 0);
}
```

---

### 🧪 Misollar:

```ts
function joinWords(...words: string[]): string {
  return words.join(" ");
}

function logAll(...args: (string | number)[]) {
  console.log(args);
}
```

---

### 🧠 Mashqlar:

1. `multiplyAll(...nums: number[])` – barcha raqamlarni ko‘paytirib qaytarsin.
2. `countStrings(...args: (string | number)[])` – faqat `string` elementlar sonini hisoblasin.
3. `combine(...arrays: number[][])` – barchasini bitta massivga birlashtirsin.
4. `printUserRoles(username: string, ...roles: string[])` – foydalanuvchi rollarini chiqarish.
5. `logTypes(...args: any[])` – har bir qiymatni tipi bilan chiqarish.

---

## 📘 4. **Function Types & Call Signatures**

### 🔍 Nima bu?

Function types — funksiyaning input va output tipini oldindan aniqlash uchun ishlatiladi.
Call signature — qanday argumentlar qabul qilishini va nima qaytarishini belgilaydi.

### 🎯 Nima uchun kerak?

* Katta tizimlarda aniq struktura uchun
* Type-safe call qilish uchun
* Reusable function interfaces yaratish

---

### ⚙️ Sintaksis:

```ts
type Add = (a: number, b: number) => number;

const add: Add = (a, b) => a + b;
```

---

### 🧪 Misollar:

```ts
type Logger = (message: string) => void;

const consoleLog: Logger = (msg) => console.log(msg);
```

---

### 🧠 Mashqlar:

1. `type Calculator = (a: number, b: number) => number` qilib `divide`, `multiply` yozing.
2. `type Formatter = (text: string) => string` qilib `capitalize` yozing.
3. `type Greeter = (name: string, age: number) => string` qilib salom yozing.
4. `type LengthChecker = (arr: any[]) => number` qilib yozing.
5. `type Validator = (value: string) => boolean` qilib email validatsiya qiling.

---

## 📘 5. **Type Aliases bilan Function Types**

### 🔍 Nima bu?

`type` orqali funktsiyalarni aniq nom bilan belgilanadigan alias qilib e'lon qilish.

### 🎯 Nima uchun kerak?

* Katta loyihalarda struktura va qayta foydalanish uchun
* DRY prinsipiga amal qilish
* Parametr yoki callback funksiyalarni aniq belgilash

### ⚙️ Sintaksis:

```ts
type Transformer = (input: string) => string;

const toUpper: Transformer = (str) => str.toUpperCase();
```

---

### 🧪 Misollar:

```ts
type Comparator = (a: number, b: number) => boolean;

const isGreater: Comparator = (a, b) => a > b;
```

---

### 🧠 Mashqlar:

1. `type Operation = (a: number, b: number) => number` va `add`, `sub` yozing.
2. `type MessageHandler = (msg: string) => void` qilib `sendToConsole` yozing.
3. `type FilterFunc = (item: string) => boolean` qilib `startsWithA` yozing.
4. `type Predicate = (x: number) => boolean` qilib `isOdd` yozing.
5. `type Formatter = (title: string, date: Date) => string` qilib `formatArticleTitle` yozing.

---
