---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: 提升開發效率的利器
info: |
  ## TypeScript + ESLint + Prettier
  讓 JavaScript 開發更安全、更高效的工具組合
# enabled pdf downloading in SPA build, can also be a custom url
download: true
# filename of the export file
exportFilename: frontend structure exported
colorSchema: dark
fonts:
  sans: Roboto
  serif: Roboto Slab
  mono: Fira Code
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# open graph
# seoMeta:
#  ogImage: https://cover.sli.dev
---

# 提升開發效率的前端三本柱

## TypeScript + ESLint + Prettier

_讓 JavaScript 開發更安全、更高效_

<div class="pt-8">
  <span class="px-2 py-1 rounded cursor-pointer" @click="$slidev.nav.next">
    Let's roll. <carbon:arrow-right class="inline"/>
  </span>
</div>

> "Simple code is the best code." — Kent Beck

<div class="abs-br m-6 text-xl">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="slidev-icon-btn">
    <carbon:edit />
  </button>
  <a href="https://github.com/davelin18yufan/typescript_eslint_slide" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
---

# 事情是這樣發生的

<div class="" 
v-motion
v-click="1"
:initial="{ x: -100, y: 40, opacity: 0 }"
:enter="{ x:0, y: 0, opacity: 1, transition: {delay: 200} }">
場景一：神秘的變數危機 🎰
</div>

<div class="text-gray-300" 
v-motion
v-click="2"
:initial="{ y: 40, opacity: 0 }"
:enter="{ y: 0, opacity: 1, transition: {delay: 200} }">
小龍發現在專案中，JS 裡面有使用叫做 <code>typecode1</code> 到 <code>typecode10</code> 的變數，完全不知道它們是什麼，也找不到來源！
</div>

<div 
v-motion
v-click="3"
:initial="{ y: 40, opacity: 0 }"
:enter="{ y: 0, opacity: 1, transition: {delay: 200} }">

```javascript {monaco} { editorOptions: { wordWrap:'on'} }
function addMember(course) {
  course.typecode = typecode1 // 這是什麼？數字？字串？物件？
  // course 無法得知他是甚麼或是裡面有甚麼，必須要往上翻檔案
  sendToApi(course) // 送出後只能祈禱伺服器不炸
}

// 每次送出 API，小龍都得重啟伺服器、打開 DevTools 慢慢試，效率低到像在玩「俄羅斯輪盤」！
```

</div>

<div
  class="mx-auto text-center mt-8 p-6 rounded-lg bg-gray-800 bg-opacity-60 shadow-lg"
  v-motion
  v-click="[4]"
  :initial="{ x: 100, y: -200, opacity: 0 }"
  :enter="{ x: 0, opacity: 1, transition: { delay: 200 } }"
  :leave="{ x:100, opacity:0 }"
>
  <h3 class="text-2xl font-bold mb-4 text-blue-300">小龍的痛點 📱</h3>
  <ul class="text-left text-lg leading-relaxed space-y-2 text-gray-200 mx-auto max-w-2xl">
    <li>
      <span class="font-semibold text-yellow-300">🎲 typecode 來源不明：</span>
      完全靠猜測，塞 console.log 去送出 API 後才知對錯
    </li>
    <li>
      <span class="font-semibold text-pink-300">😰 效率低下：</span>
      每次測試都要重啟伺服器，浪費時間
    </li>
    <li>
      <span class="font-semibold text-red-400">💥 Bug 頻發：</span>
      各式型別錯誤導致API處理失敗
    </li>
    <li>
      <span class="font-semibold text-green-300">🔍 80% 時間在試錯：</span>
      小龍快被逼瘋
    </li>
  </ul>
</div>

<div
  class="text-slate-300 text-center"
  v-motion
  v-click="5"
  :initial="{ x: 100, y: -100, opacity: 0 }"
  :enter="{ x: 0,y:-250, opacity: 1, transition: { delay: 200 } }"
>
小龍的 OS：
「X!^@#$^!!! 這 typecode 到底是誰寫的？為什麼沒人告訴我它是什麼！」
<br/>
「註解哩，我是要通靈嗎？」
</div>

<!--
Here is another comment.
-->

---
transition: slide-up
layout: center
---
<div class="max-w-3xl px-1 text-gray-300">

<h3 class="text-yellow-300">"Good code should be as clear as prose." — Robert C. Martin</h3>

> _好的程式碼應該像散文一樣清晰。_

</div>
---
transition: fade
---

# 小龍的困擾之二 🤯

<div class="" 
v-motion
v-click="1"
:initial="{ x: -100, y: 40, opacity: 0 }"
:enter="{ x:0, y: 0, opacity: 1, transition: {delay: 200} }">
場景二：使用者操作的詭異 Bug 🔍
</div>

<div class="text-gray-300" 
v-motion
v-click="2"
:initial="{ y: 40, opacity: 0 }"
:enter="{ y: 0, opacity: 1, transition: {delay: 200} }">
小龍收到了一張 Bug 單：按鈕點擊後顯示成功但卻沒有做事 !?
</div>

<div 
v-motion
v-click="3"
:initial="{ y: 40, opacity: 0 }"
:enter="{ y: 0, opacity: 1, transition: {delay: 200} }">

```javascript {*|*|*|*|*|3,10,17}
function deleteMember() {
  // 取值
  var memNo = $("#input").data("memno")
  var course = $("course").val()
  var description = $("#description").val()
  var memName = $("#name").val()
  var depNo = $("#select").data("code")
  // 建檔人
  var account = sessionStorage.getItem("ma")
  var memNo = sessionStorage.getItem("memno")
  var bMemName = sessionStorage.getItem("memName")
  var type = WebUI.GetQueryString("type")
  if (!depNo) alert("請選擇單位")
  if (!memName) alert("請選擇人員")
  // ...其他檢查

  var inParam = $.param({ memNo, account, bMemName,memName, depNo, description})
  var data = sendDeleteRequest(inParam) // 送出刪除請求
  if (!data.ErrorMessage) alert("儲存成功")
}
```

</div>

<arrow v-click="[4]" x1="555" y1="200" x2="360" y2="230" color="#953" width="2" arrowSize="1" />
<arrow v-click="[4]" x1="585" y1="310" x2="400" y2="358" color="#953" width="2" arrowSize="1" />

<div
  class="text-slate-300 text-center bg-slate-800 p-2 max-w-lg rounded-sm"
  v-motion
  v-click="6"
  :initial="{ x: 100, y: -100, opacity: 0 }"
  :enter="{ x: 330,y:-500, opacity: 1, transition: { delay: 200 } }"
>
小龍找了兩小時才發現：<code>var</code> 重複宣告導致 <code>memNo</code> 被覆蓋，API 送出錯誤資料，按鈕功能異常！
</div>

---
transition: slide-left
layout: center
---

<div class="max-w-3xl px-1 text-gray-300">
<h3 class="text-yellow-300">"The quality of your code determines the cost of future maintenance." — Martin Fowler</h3>

> *程式碼的品質決定了未來的維護成本。*

</div>

---
transition: slide-down
---

# 小龍的困擾之三 🤯

<div class="" 
v-motion
:initial="{ y: 40, opacity: 0 }"
:enter="{ x:0, y: 0, opacity: 1, transition: {delay: 400} }">
場景三：接手維護別人的專案 ⚔️
</div>

<div class="text-gray-300" 
v-motion
:initial="{ y: 40, opacity: 0 }"
:enter="{ y: 0, opacity: 1, transition: {delay: 400} }">
  小龍接手一個同事留下的專案，但是裡面光是條件判斷就有 n 種寫法
</div>

````md magic-move {lines:true}
```javascript
function grade(score) {
  var result;

  if (score > 90) {
    result = 'A';
  } else {
    if (score > 80) {
      result = 'B';
    } else {
      if (score > 70) {
        result = 'C';
      } else {
        result = 'F';
      }
    }
  }

  return result;
}

```

```javascript
function grade(score) {
  if (score > 90) return 'A'
  else if (score > 80) {
    return 'B';
  } else if (score > 70) {
    return 'C';
  }

  return 'F';
}

```
```javascript
const grade = (score) => {
  if (score > 90) return 'A'
  if (score > 80) return 'B'
  if (score > 70) return 'C'
  else {
    return 'F' 
  }
}

```
```javascript
//🔴 版本一：老式寫法
function grade(score) {
  var result; // 使用 var，不是 ES6+

  if (score > 90) {
    result = 'A';
  } else {      
    // 過度巢狀
    if (score > 80) {
      result = 'B';
    } else {
      if (score > 70) {
        result = 'C';
      } else {
        result = 'F'; // 回傳方式固定但可簡化
      }
    }
  }
  return result;
}

```
```javascript
// 🟡 版本二：中期寫法，有改善但風格仍不一致
function grade(score) {
  if (score > 90) return 'A'
  // 還是有巢狀但比之前少
  else if (score > 80) {  
    return 'B';      // 使用 return 時風格不一致（有些單行、有些 block）
  } else if (score > 70) {
    return 'C';
  }

  return 'F';
}

```

```javascript
// 🟠 版本三：箭頭函式但缺乏可讀性與一致性
const grade = (score) => {
  if (score > 90) return 'A'
  if (score > 80) return 'B'
  if (score > 70) return 'C'
  else { // 混合 else 與早期 return
    return 'F' // 有人不喜歡在前面 if 省略 else，這裡反而加了，也不必要
  }
}

```
```javascript
// ✅ 建議最佳寫法：ESLint 推薦風格一致 + 易讀
const grade = (score) => {
  if (score > 90) return 'A';
  if (score > 80) return 'B';
  if (score > 70) return 'C';
  return 'F';
};
// 優點：
//     ✅ 使用 const 宣告（ES6+）
//     ✅ 單一 return style，風格一致
//     ✅ 無不必要巢狀
//     ✅ 簡短易讀

```
````
<div
  class="text-slate-300 bg-slate-800 px-6 py-2 rounded-md text-left leading-relaxed shadow-md space-y-3"
  v-motion
  v-click="7"
  :initial="{ x: 100, y: -80, opacity: 0 }"
  :enter="{ x: 0, y: 0, opacity: 1, transition: { delay: 200 } }"
>
  <p>🔥 <strong class="text-white">衝突不斷：</strong> 每個人有自己的風格</p>
  <p>⏰ <strong class="text-white">效率低落：</strong> 邏輯問題被格式掩蓋</p>
  <p>🤯 <strong class="text-white">新人困惑：</strong> 無從下手、不知道照誰的標準改</p>
</div>

<div
  class="text-slate-300 bg-gray-800 px-6 py-4 rounded-md leading-relaxed space-y-4 shadow-lg"
  v-motion
  v-click="8"
  :initial="{ x: 100, y: -80, opacity: 0 }"
  :enter="{ x: 0, y: -230, opacity: 1, transition: { delay: 200 } }"
>
  <p class="text-lg font-semibold text-yellow-300">👨‍💼 假設是有主管在 Code Review，場面可能是這樣的：</p>

  <ul class="space-y-2 pl-4 list-disc list-inside text-base">
    <li>
      <strong class="text-rose-400">主管：</strong>
      「這縮排是怎麼回事？<code>if-else</code>是要包到隔壁去嗎怎麼這麼深，我眼睛度數已經夠深了 😩」
    </li>
    <li>
      <strong class="text-sky-400">小龍：</strong>
      「誰又用 <code class="text-orange-300">var</code> 了？不是說好用 <code class="text-green-300">const</code>？」
    </li>
    <li>
      <strong class="text-purple-400">小凱：</strong>
      「單引號、雙引號能不能統一一下？」
    </li>
    <li>
      <strong class="text-gray-400">菜鳥：</strong>
      「我不知道要跟誰的風格…… 😥」
    </li>
  </ul>
</div>

---
transition: slide-left
layout: center
---

<div class="max-w-3xl px-1 text-gray-300">

<h3 class="text-yellow-300">"Consistency is the foundation of effective teamwork." — Douglas Crockford</h3>

> _一致性是團隊協作的基石。_

</div>

---
layout: image
class: place-content-center text-center sepia-10 font-bold
image: https://media.istockphoto.com/id/1306697195/photo/space-exploration.webp?a=1&s=612x612&w=0&k=20&c=0W0wSZearwIpiTt3MSDD6EXQZOe2yrnIDmtS_hDu5YI=
---

# Javascript 生態系開發三本柱 

---
transition: slide-up
---

# 🌟 現代 Javascript 開發的基石工具
無論前端後端，甚麼框架 React、Vue 或 .NET 專案，這三個工具不能說必備但都是首選！

<div class="grid grid-cols-1 md:grid-cols-3 gap-6 mt-6" 
v-click
v-motion
:initial="{opacity: 0, y: 100}"
:enter="{y:0, opacity: 100}">
  <!-- TypeScript -->
  <div
    class="bg-slate-800 text-slate-200 p-6 rounded-xl border border-blue-400 shadow-lg hover:shadow-blue-500/50 transition-shadow duration-300"
  >
    <div class="text-2xl mb-2 font-mono">🔷 Compiler</div>
    <h3 class="text-xl font-bold mb-1 text-blue-300">TypeScript</h3>
    <p class="text-sm mb-3 text-slate-400">型別安全</p>
    <ul class="list-disc list-inside space-y-1 text-sm" v-mark.circle.orange="2">
      <li>編譯時錯誤檢查</li>
      <li>強型別系統</li>
      <li>增強 IDE 支援</li>
    </ul>
    <div class="mt-4 text-xs text-slate-400">✅ 90% 現代前後端框架官方推薦</div>
  </div>

  <!-- ESLint -->
  <div
    class="bg-slate-800 text-slate-200 p-6 rounded-xl border border-emerald-400 shadow-lg hover:shadow-emerald-500/50 transition-shadow duration-300"
  >
    <div class="text-2xl mb-2 font-mono">🔍 Linter</div>
    <h3 class="text-xl font-bold mb-1 text-emerald-300">ESLint</h3>
    <p class="text-sm mb-3 text-slate-400">程式碼品質</p>
    <ul class="list-disc list-inside space-y-1 text-sm">
      <li v-mark.red="3">統一程式碼風格</li>
      <li v-mark.red="3">檢測潛在問題</li>
      <li>推廣最佳實務</li>
    </ul>
    <div class="mt-4 text-xs text-slate-400">✅ 各開源協作專案必備</div>
  </div>

  <!-- Prettier -->
  <div
    class="bg-slate-800 text-slate-200 p-6 rounded-xl border border-pink-400 shadow-lg hover:shadow-pink-500/50 transition-shadow duration-300"
  >
    <div class="text-2xl mb-2 font-mono">✨ Formatter</div>
    <h3 class="text-xl font-bold mb-1 text-pink-300">Prettier</h3>
    <p class="text-sm mb-3 text-slate-400">格式美化</p>
    <ul class="list-disc list-inside space-y-1 text-sm">
      <li>自動格式化</li>
      <li v-mark.red="3">統一程式碼風格</li>
      <li v-mark.red="4">減少格式爭議</li>
    </ul>
    <div class="mt-4 text-xs text-slate-400">✅ GitHub、VS Code、 Cursor 預設整合</div>
  </div>
</div>


<!--
Presenter note with **bold**, *italic*, and ~~striked~~ text.

-->

---
transition: fade-in
---

# TypeScript：DX (開發者體驗)的救星 🛡️

````md magic-move {at:2, lines:true}
```javascript {*} // [!code hl]
// 小龍的 JavaScript 🚫
function enrollCourse(course) {
  course.courseType = typecode1; // 完全不知道 typecode1 是什麼
  sendToApi(course);
}
```

```typescript
// 升級到 TypeScript ✅
enum CourseType {
  Required = 1,
  Elective = 2,
  Online = 3,
}

type Course = {
  courseType: CourseType;
  courseId: string;
  title: string;
}

function enrollCourse(course: Course): void {
  course.courseType = CourseType.Required; // 型別安全，IDE 提示
  course.studentName = "Joe"; // ❌ Error: 'studentName' 不存在
  sendToApi(course);
}
```

```ts
// 使用 JSDoc 進一步註解說明 ✅
enum CourseType {
  Required = 1,
  Elective = 2,
  Online = 3,
}

type Course = {
  courseType: CourseType;
  courseId: string;
  title: string;
}

/**
 * 處理課程註冊
 * @param {Course} course - 課程物件，包含類型與基本資訊
 * @returns {void}
 */
function enrollCourse(course: Course): void {
  course.courseType = CourseType.Required;
  sendToApi(course);
}
// 以上全部 hover 都會有註解說明
```
````

<div 
  class="absolute right-20 top-40 text-slate-200 text-sm bg-slate-800 p-4 rounded-md shadow-md w-[300px]"
  v-click="[1]"
  v-motion
  :initial="{x:100, opacity: 0}"
  :enter="{x:0, opacity: 1}" 
  :leave="{x:-100, opacity: 0}"
>
  <ul class="list-disc list-inside space-y-1">
    <li>🚫 無法得知變數的型別</li>
    <li>🚫 無法得知 typecode1 是什麼</li>
    <li>🚫 可能傳入錯誤屬性卻沒錯誤提示</li>
  </ul>
</div>

<div 
  class="absolute right-20 top-40  text-slate1200 text-sm bg-green-900 p-4 rounded-md shadow-md w-[320px]"
  v-click="[2]"
  v-motion
  :initial="{x:100, opacity: 0}"
  :enter="{x:0, opacity: 1}" 
  :leave="{x:-100, opacity: 0}"
>
  <ul class="list-disc list-inside space-y-1">
    <li>✅ 型別定義明確，參數、回傳皆可標註</li>
    <li>✅ IDE 自動推斷屬性與自動完成</li>
    <li>✅ 錯誤在開發階段即提示</li>
  </ul>
</div>

<div 
  class="absolute right-20 top-40  text-slate-100 text-sm bg-teal-800 p-4 rounded-md shadow-md w-[320px]"
  v-click="[3]"
  v-motion
  :initial="{x:100, opacity: 0}"
  :enter="{x:0, opacity: 1}" 
  :leave="{x:-100, opacity: 0}"
>
 <ul class="list-disc list-inside space-y-1">
    <li>✅ JSDoc 為程式碼加上自動文件與註解說明</li>
    <li>✅ TypeScript 提供型別檢查與錯誤提示</li>
    <li>✅ 結合兩者讓程式更易懂、易維護</li>
    <li>✅ 增加團隊溝通清晰度與註解一致性</li>
  </ul>
</div>

---
layout: two-cols-header
class: mr-2
---

# 與 C# 的相似性 🤝


<div class="text-lg text-white"
v-motion
:initial="{ opacity: 0, y: -20 }"
:enter="{ opacity: 1, y: 0, transition: { delay: 300 } }"
>

`TypeScript` 與 `C#` 都出自 <strong>Anders Hejlsberg</strong>（微軟首席架構師）<br />
他也是 `Delphi` 與 `C#` 的設計者！
</div>

::left::

<div class=" text-center border border-slate-500 rounded-md p-3 bg-slate-800 shadow-md" v-motion v-click="1" :initial="{opacity: 0, y: 20}" :enter="{opacity: 1, y: 0, transition: { delay: 400 } }">
<h3 class="text-lg text-cyan-400 font-bold mb-2">C# 風格</h3>
</div>

```csharp
public enum OrderType {
    Standard = 1,
    Premium = 2,
    Express = 3
}

public class Order {
    public OrderType TypeCode { get; set; }
}
```

::right::

<div class="text-center border border-slate-500 rounded-md p-3 bg-slate-800 shadow-md" v-motion v-click="1" :initial="{opacity: 0, y: 20}" :enter="{opacity: 1, y: 0, transition: { delay: 500 } }">
 <h3 class="text-lg text-yellow-400 font-bold mb-2">TypeScript 風格</h3>
</div>

```ts
enum OrderType {
  Standard: 1,
  Premium: 2,
  Express: 3,
}

interface Order {
  typecode: OrderType;
}
```

---
transition: fade
layout: center
---

<img 
  class="mx-auto"
  src="https://external-preview.redd.it/kJxuZLpvgM46uUDHbQD3rrl9PNDsQuLIhMZo58LnSJc.jpg?width=320&crop=smart&auto=webp&s=0163003db810819855fc677e60ab7d5e2e9bd129"
/>

<div class="max-w-3xl px-1 text-gray-300">
<h3 class="text-yellow-300">"Types are the foundation of programming." — Anders Hejlsberg</h3>

> 型別是程式設計的基石。

</div>

---

# ESLint：程式碼品質守護者 🛡️

<div  class="" v-motion v-click="1" :enter="{x:0, opacity: 50}" :initial="{x:100, opacity:100}">

````md magic-move {at:2, lines:true}
```js
var memNo = getApiMemberNo(); // ESLint 警告: 應使用 const
var memNo = $("input").val();

if (memNo == '123') { // ESLint 警告: 應使用 ===
  console.log("Member: " + memNo); // ESLint 警告: 使用模板字串
}

var tempData = []; // ESLint 錯誤：tempData 未使用
```

### ✨ 配置 ESLint 後更優雅

```js
const memNo = getApiMemberNo() || $('input').val(); 

if (memNo === '123') { 
  console.log(`Member: ${memNo}`); 
}

```
````
</div>


<div class="grid grid-cols-3 gap-4 text-sm text-slate-100 mt-4" 
v-motion v-click="3" :enter="{x:0, opacity: 50}" :initial="{x:100, opacity:100}">
<div class="bg-slate-800 p-4 rounded-lg shadow-md border-l-4 border-red-500">
<h4 class="font-bold text-red-400 mb-2">🚫 禁止危險寫法</h4>
<ul class="list-disc list-inside space-y-1">
  <li>禁用 <code>var</code>，強制使用 <code>const</code>/<code>let</code></li>
  <li>禁用 <code>==</code>，強制使用 <code>===</code></li>
  <li>檢查未使用的變數</li>
</ul>
</div>

<div class="bg-slate-800 p-4 rounded-lg shadow-md border-l-4 border-blue-500">
<h4 class="font-bold text-blue-400 mb-2">📋 統一程式碼風格</h4>
<ul class="list-disc list-inside space-y-1">
  <li>強制使用 ES6+ 語法</li>
  <li>統一命名規則（<code>camelCase</code>）</li>
  <li>強制使用模板字串</li>
</ul>
</div>

<div class="bg-slate-800 p-4 rounded-lg shadow-md border-l-4 border-green-500">
<h4 class="font-bold text-green-400 mb-2">🎯 對問題設定規則</h4>

```json
{
  "no-var": "error",
  "prefer-const": "warn",
  "eqeqeq": "error",
  "prefer-template": "error"
}
```

</div>
</div>

---

# Motions

Motion animations are powered by [@vueuse/motion](https://motion.vueuse.org/), triggered by `v-motion` directive.

```html
<div
  v-motion
  :initial="{ x: -80 }"
  :enter="{ x: 0 }"
  :click-3="{ x: 80 }"
  :leave="{ x: 1000 }"
>
  Slidev
</div>
```

<div class="w-60 relative">
  <div class="relative w-40 h-40">
    <img
      v-motion
      :initial="{ x: 800, y: -100, scale: 1.5, rotate: -50 }"
      :enter="final"
      class="absolute inset-0"
      src="https://sli.dev/logo-square.png"
      alt=""
    />
    <img
      v-motion
      :initial="{ y: 500, x: -100, scale: 2 }"
      :enter="final"
      class="absolute inset-0"
      src="https://sli.dev/logo-circle.png"
      alt=""
    />
    <img
      v-motion
      :initial="{ x: 600, y: 400, scale: 2, rotate: 100 }"
      :enter="final"
      class="absolute inset-0"
      src="https://sli.dev/logo-triangle.png"
      alt=""
    />
  </div>

  <div
    class="text-5xl absolute top-14 left-40 text-[#2B90B6] -z-1"
    v-motion
    :initial="{ x: -80, opacity: 0}"
    :enter="{ x: 0, opacity: 1, transition: { delay: 2000, duration: 1000 } }">
    Slidev
  </div>
</div>

<!-- vue script setup scripts can be directly used in markdown, and will only affects current page -->
<script setup lang="ts">
const final = {
  x: 0,
  y: 0,
  rotate: 0,
  scale: 1,
  transition: {
    type: 'spring',
    damping: 10,
    stiffness: 20,
    mass: 2
  }
}
</script>

<div
  v-motion
  :initial="{ x:35, y: 30, opacity: 0}"
  :enter="{ y: 0, opacity: 1, transition: { delay: 3500 } }">

[Learn more](https://sli.dev/guide/animations.html#motion)

</div>

---

# LaTeX

LaTeX is supported out-of-box. Powered by [KaTeX](https://katex.org/).

<div h-3 />

Inline $\sqrt{3x-1}+(1+x)^2$

Block

$$
{1|3|all}
\begin{aligned}
\nabla \cdot \vec{E} &= \frac{\rho}{\varepsilon_0} \\
\nabla \cdot \vec{B} &= 0 \\
\nabla \times \vec{E} &= -\frac{\partial\vec{B}}{\partial t} \\
\nabla \times \vec{B} &= \mu_0\vec{J} + \mu_0\varepsilon_0\frac{\partial\vec{E}}{\partial t}
\end{aligned}
$$

[Learn more](https://sli.dev/features/latex)

---

# Diagrams

You can create diagrams / graphs from textual descriptions, directly in your Markdown.

<div class="grid grid-cols-4 gap-5 pt-4 -mb-6">

```mermaid {scale: 0.5, alt: 'A simple sequence diagram'}
sequenceDiagram
    Alice->John: Hello John, how are you?
    Note over Alice,John: A typical interaction
```

```mermaid {theme: 'neutral', scale: 0.8}
graph TD
B[Text] --> C{Decision}
C -->|One| D[Result 1]
C -->|Two| E[Result 2]
```

```mermaid
mindmap
  root((mindmap))
    Origins
      Long history
      ::icon(fa fa-book)
      Popularisation
        British popular psychology author Tony Buzan
    Research
      On effectiveness<br/>and features
      On Automatic creation
        Uses
            Creative techniques
            Strategic planning
            Argument mapping
    Tools
      Pen and paper
      Mermaid
```

```plantuml {scale: 0.7}
@startuml

package "Some Group" {
  HTTP - [First Component]
  [Another Component]
}

node "Other Groups" {
  FTP - [Second Component]
  [First Component] --> FTP
}

cloud {
  [Example 1]
}

database "MySql" {
  folder "This is my folder" {
    [Folder 3]
  }
  frame "Foo" {
    [Frame 4]
  }
}

[Another Component] --> [Example 1]
[Example 1] --> [Folder 3]
[Folder 3] --> [Frame 4]

@enduml
```

</div>

Learn more: [Mermaid Diagrams](https://sli.dev/features/mermaid) and [PlantUML Diagrams](https://sli.dev/features/plantuml)

---

foo: bar
dragPos:
square: 691,32,167,\_,-16

---
dragPos:
  square: 0,-15,0,0
---

# Draggable Elements

Double-click on the draggable elements to edit their positions.

<br>

###### Directive Usage

```md
<img v-drag="'square'" src="https://sli.dev/logo.png">
```

<br>

###### Component Usage

```md
<v-drag text-3xl>
  <div class="i-carbon:arrow-up" />
  Use the `v-drag` component to have a draggable container!
</v-drag>
```

<v-drag pos="663,206,261,_,-15">
  <div text-center text-3xl border border-main rounded>
    Double-click me!
  </div>
</v-drag>

<img v-drag="'square'" src="https://sli.dev/logo.png">

###### Draggable Arrow

```md
<v-drag-arrow two-way />
```

<v-drag-arrow pos="67,452,253,46" two-way op70 />

---

src: ./pages/imported-slides.md
hide: false

---


---

# Monaco Editor

Slidev provides built-in Monaco Editor support.

Add `{monaco}` to the code block to turn it into an editor:

```ts {monaco}
import { ref } from "vue"
import { emptyArray } from "./external"

const arr = ref(emptyArray(10))
```

Use `{monaco-run}` to create an editor that can execute the code directly in the slide:

```ts {monaco-run}
import { version } from "vue"
import { emptyArray, sayHello } from "./external"

sayHello()
console.log(`vue ${version}`)
console.log(
  emptyArray<number>(10).reduce(
    (fib) => [...fib, fib.at(-1)! + fib.at(-2)!],
    [1, 1]
  )
)
```

---

layout: center
class: text-center

---

# Learn More

[Documentation](https://sli.dev) · [GitHub](https://github.com/slidevjs/slidev) · [Showcases](https://sli.dev/resources/showcases)

<PoweredBySlidev mt-10 />
