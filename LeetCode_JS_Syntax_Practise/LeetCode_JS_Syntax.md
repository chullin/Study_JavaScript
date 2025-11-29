<!-- 沒想到 VS Code 裡面的 Agent 這麼厲害的嗎，可以這樣隨便打幾行字，就幫我生出這麼多東西 -->

# LeetCode — JavaScript 語法與常見技巧筆記

目的：記錄在做 LeetCode 時學到或常用到的 JavaScript 語法、範例與解題模式，方便復習與複用。

使用方式：

- 把每題常用到的片段（Template、技巧、Corner Case）貼到相應章節下。
- 每個範例保留簡短說明與時間/空間複雜度（若有）。

---

## 目錄

- Array
- String
- HashMap / Set
- Two Pointers
- Sliding Window
- Recursion / DFS / Backtracking
- BFS
- Sorting / Comparators
- Bit Manipulation
- ES6 實用語法
- Useful Utilities

---

## Array

- Flatten (淺)：`arr.flat()`

```js
const a = [1, [2, 3], [4]];
console.log(a.flat()); // [1,2,3,4]
```

- 去重（Set）

```js
const uniq = (arr) => [...new Set(arr)];
```

- 常用遍歷

```js
arr.forEach((v, i) => {});
const mapped = arr.map((x) => x * 2);
const filtered = arr.filter((x) => x > 0);
```

---

## String

- 反轉字串

```js
const rev = (s) => s.split("").reverse().join("");
```

- 檢查回文

```js
const isPal = (s) => {
  let i = 0,
    j = s.length - 1;
  while (i < j) if (s[i++] !== s[j--]) return false;
  return true;
};
```

---

## HashMap / Set

- 頻率計數

```js
const freq = new Map();
for (const x of arr) freq.set(x, (freq.get(x) || 0) + 1);
```

- 直接用物件

```js
const obj = {};
obj[key] = (obj[key] || 0) + 1;
```

---

## Two Pointers

- 左右指標常見模板

```js
let l = 0, r = arr.length-1;
while(l<r){
  // 處理
  if(/*條件*/) l++; else r--;
}
```

---

## Sliding Window

- 固定大小

```js
let sum = 0;
for (let i = 0; i < k; i++) sum += arr[i];
for (let i = k; i < arr.length; i++) {
  sum += arr[i] - arr[i - k];
}
```

- 可變大小（最長/最短條件）

```js
let l = 0,
  sum = 0,
  best = 0;
for (let r = 0; r < arr.length; r++) {
  sum += arr[r];
  while (sum > target) {
    sum -= arr[l++];
  }
  best = Math.max(best, r - l + 1);
}
```

---

## Recursion / DFS / Backtracking

- 基本 DFS 模板（樹/圖）

```js
function dfs(node) {
  if (!node) return;
  // 處理
  for (const nei of node.neighbors) dfs(nei);
}
```

- 回溯（組合/排列）

```js
function backtrack(path, choices) {
  if (path完成條件) {
    res.push([...path]);
    return;
  }
  for (let i = 0; i < choices.length; i++) {
    path.push(choices[i]);
    backtrack(path, choices);
    path.pop();
  }
}
```

---

## BFS

- 階層遍歷（最短路徑）

```js
const q = [];
q.push(start);
const seen = new Set([start]);
while (q.length) {
  const x = q.shift();
  for (const nei of neighbors(x)) {
    if (!seen.has(nei)) {
      seen.add(nei);
      q.push(nei);
    }
  }
}
```

---

## Sorting / Comparators

- 自訂比較器

```js
arr.sort((a, b) => a.key - b.key); // 升序
```

---

## Bit Manipulation

- 取反與位運算

```js
x & (x - 1); // 移除最低位的 1
x ^ y; // XOR
```

---

## ES6 實用語法

- 展開運算子、解構、默認參數

```js
const a = [...arr];
const { x, y } = obj;
function f(a = 1) {}
```

- arrow 與 lexical `this`

---

## Useful Utilities

- 建立範本函式

```js
// LeetCode 模板：讀入輸入、執行解答、列印結果
function solve(input) {
  // parse input
  // return answer
}

// local test
console.log(solve(/* sample */));
```

---

## 如何貢獻與擴充

- 每做完一題，把關鍵技巧或模板貼在對應章節。
- 若有更好的寫法，保留原解與優化寫法供比較。

---

時間/空間複雜度：請在每個範例下方註記（若已分析）。

最後：這個檔案會持續擴充。若要我把特定題型或題目片段加入，請告訴我題號或想要的章節。
