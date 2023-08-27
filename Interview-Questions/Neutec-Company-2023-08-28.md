# 日新軟體面試

> Date：2023/08/28

## 環繞前測作業的可能問題延伸

## 二測可能口試問題

### Styles

#### 你如何建立好的 css 命名 ?

早期入行時採用 BEM 的做法，就是典型使用雙 underline(下底線) 間隔，有動態效果才使用雙 dash。但中間部分公司的舊專案，因為維護成本偏高，則單純採用 dash 來間隔進行語義化。不過，目前大多是以 TailwindCSS 來進行開發，除了很少數的需要客製化的區塊，原則上都採用 TailwindCSS 官方的命名規則。

#### 請比較 TailwindCSS 和 SCSS 的使用情境和使用上優劣

假設你希望快速開發一個原型 Demo(可以結合 ChatGPT 快速產出有部分質感的畫面)，使用 TailwindCSS 會是比較好的選擇。你不需要花時間去設計與思考 class，採用官方的一些基礎設計，就可以讓作品快素呈現基本樣式。而且旁人即使接手也可以快速理解樣式的運作模式。

但相對來說，幾乎每個 HTML 標籤都會帶有大量的 class，會讓整個 template 非常臃腫。同時，這個設計情境畢竟是為了快速產出做的，自然無法考慮高度客製化的情境，改動起來不靈活。

反之，SCSS 則是能針對大型項目來設計與擴展，因為整個項目可能需要高度客製化，或者需要遵循團隊內部的某些設計準則，這時就可以透過包含迴圈，變數，函式來創建某些複雜的樣式。但通常這種狀況，也可能是一體兩面的問題，有可能會隨著維護時間的拉長，導致整個樣式變成非常複雜且難以維護(尤其是解 hotfix 後的遺留問題)。

因此簡單來說，雖然兩者各有優劣，但原則上，還是根據團隊的具體方向再決定使用哪一種技術解決問題。

#### 是否在開發上有寫過複雜的動畫？請詳細舉例說明

#### 除了 css 外，是否還有什麼方式可以產生動畫？請詳細列出各種可能性

- 使用 GSAP 動畫 library
- 使用 Canvas 動畫來渲染
- 使用 SVG 動畫來跑一些微動畫，譬如某些狀態的呈現，例如訂單成功(success)狀態打勾
- 如果要處理 3D 的情境，最主流就是使用 Three.js，雖然也有 WebGL 但使用成本太高了
- Web Animation API(實驗性功能)

### JavaScript

#### 請說明 `for in` 和 `for of` 的差異，並舉例說明

#### 請說明 `event target` 和 `event currentTarget` 的差異，並舉例說明

#### 請說明 `event bubbling` 和 `event capturing` 的差異，並舉例說明

#### 請說明 `event delegation` 的概念，並舉例說明

#### 請說明 `event loop` 的概念，並舉例說明

#### 請說明 `event.stopPropagation()` 和 `event.preventDefault()` 的差異，並舉例說明

#### 請比較 `var` 和 `let` 以及 `const` 的差異，並舉例說明

### Vue

### LeetCode

#### 有兩個陣列，請將第二個陣列中的第一個值跳過，再將第一個陣列中的內容乘以第二個陣列的所有數值

- 舉例說明

```js
const array1 = [1, 2, 3, 4]
const array2 = [2, 3, 4, 5]

const result = [array1[0] * 3, array1[0] * 4, array1[0] * 5, array1[1] * 3 ...] // 以此類推
```

- 請提供具體解法與詳細解釋

```js
const array1 = [1, 2, 3, 4];
const array2 = [2, 3, 4, 5];

// 建立一個空陣列用來儲存預期結果
let result: number[] = [];

// 透過 slice() 方法來過濾第二個陣列的第一個元素，重組出新陣列
const modifiedArray = array2.slice(1);

// 遍歷第一個陣列
for (const num1 of array1) {
  // 將第一個陣列中的每一個元素，遍歷重組後的第二個陣列
  for (const num2 of modifiedArray) {
    result.push(num1 * num2);
  }
}

console.log(result);
```
