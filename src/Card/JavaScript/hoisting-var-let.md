# Variables

## 為什麼 JS 面試會使用 var 而不是 let 來考 Hoisting ?

```js
console.log(a); // undefined

var a = 1;
```

一般來說，我們已經知道上述 print 的結果，是因為 var 會被 hoisting 到最上面，因此在 log 時，會拿到 undefined，同時也可以理解為下述內容：

```js
var a;

console.log(a); // undefined

a = 1;
```

### 如何避免 hoisting ?

hoisting 這種運作方式，在思考上是相對反人類的，因此會希望在哪一行聲明變數，則變數應當只執行在該行，如果書寫不正確，則 return error 讓我們知道。因此可以改使用 let：

```js
console.log(a); // ReferenceError: Cannot access 'a' before initialization

let a = 1;
```

上述中，在聲明變數前，執行 console.log，則會觸發 template dead zone(暫時性死區)，因此會觸發 ReferenceError，這樣就符合人類的思考邏輯。

## let 的奇怪操作

```js
let a = (b = c = 10);
```

這個操作邏輯中，不是由左往右賦值，而是由右往左，可以理解為， c = 10, b = c, a = b。

## 為什麼在看到各種 JS 教學時，多使用 const 而非 let ?

let 聲明的變數，可以 reassign，而這個變數即使寫在 function 內，其 scope 依然會跑到 global，因此如果 function 外若有一個相同名稱的變數，即會遭到污染，雖然我們可能會在書寫時盡力避免這種錯誤，但很多時候可能會在不知情的狀況下污染變數，因此盡可能採用 const。

因此書寫原則是，優先使用 const，其次則是 let，不使用 var。另外，使用 const 將會迫使我們思考，聲明這個變數的情境，未來是否會有變動的可能。

```js
let num = 10;

function changeNum(arg) {
  num = arg;
}

changeNum(50);
console.log(num); // 50
```

- [reference](https://zellwk.com/blog/dont-reassign/)
