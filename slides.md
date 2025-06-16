---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
author: Dave
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
  sans: DotGothic16
  serif: Zen Kurenaido
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

<div class="ml-auto py-8">
  <span class="px-2 py-1 rounded cursor-pointer text-yellow-300 block text-end" @click="$slidev.nav.next">
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

<style>
  p {
    color:rgb(239, 181, 21)
  }
</style>

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
  course.typecode = typecode1; // 這是什麼？數字？字串？物件？
  // course 無法得知他是甚麼或是裡面有甚麼，必須要往上翻檔案
  sendToApi(course); // 送出後只能祈禱伺服器不炸
}

// 每次送出 API，小龍都得重啟伺服器、打開 DevTools 慢慢試，效率低筆電又燙！
```

</div>

<div
  class="mx-auto text-center mt-8 p-6 rounded-lg bg-gray-800 bg-opacity-60 shadow-lg "
  v-motion
  v-click="[4]"
  :initial="{ x: 100, y: -200, opacity: 0 }"
  :enter="{ x: 0, opacity: 1, transition: { delay: 200 } }"
  :leave="{ x:100, opacity:0 }"
>
  <h3 class="text-2xl font-bold mb-4 text-blue-300">小龍的痛點 📱</h3>
  <ul class="text-left text-base leading-relaxed space-y-2 text-gray-200 mx-auto max-w-2xl">
    <li>
      <span class="font-semibold text-yellow-300">🎲 變數來源不明：</span>
      沒有型別提示，只能靠 <code>console.log</code> 或送出 API 才知道資料對不對
    </li>
    <li>
      <span class="font-semibold text-pink-300">😰 開發效率低下：</span>
      少打一個欄位或拼錯 key，只有在執行時才爆錯，還得重啟伺服器排查
    </li>
    <li>
      <span class="font-semibold text-red-400">💥 Bug 頻發：</span>
      資料結構錯誤、參數型別錯誤，讓程式無法正常運作
    </li>
    <li>
      <span class="font-semibold text-green-300">🔍 80% 時間在 Debug：</span>
      小龍寫完還要對著網頁反覆測試、來回修正，快被搞瘋 🌀
    </li>
    <li>
      <span class="font-semibold text-blue-300">🤝 團隊溝通障礙：</span>
      沒有明確型別，參數要怎麼傳、回傳什麼都只能慢慢往回找或問人
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
<br/>
「Ado 救人啊」
</div>

<!--
Here is another comment.
-->

---
transition: slide-up
layout: center
---

<div class="max-w-3xl px-1 text-gray-300 font-serif">

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

````md magic-move {at:4, lines:true}
```javascript
$('#btnDelete').click(deleteMember);
```

```javascript {*|3,10,17}
function deleteMember() {
  // 取值
  var memNo = $('#input').data('memno');
  var course = $('course').val();
  var description = $('#description').val();
  var memName = $('#name').val();
  var depNo = $('#select').data('code');
  // 建檔人
  var account = sessionStorage.getItem('ma');
  var memNo = sessionStorage.getItem('memno');
  var bMemName = sessionStorage.getItem('memName');
  var type = WebUI.GetQueryString('type');
  if (!depNo) alert('請選擇單位');
  if (!memName) alert('請選擇人員');
  // ...其他檢查

  var inParam = $.param({memNo, account, bMemName, memName, depNo, description});
  var data = sendDeleteRequest(inParam); // 送出刪除請求
  if (!data.ErrorMessage) alert('儲存成功');
}
```
````

</div>

<arrow v-click="[5]" x1="545" y1="200" x2="380" y2="230" color="#953" width="2" arrowSize="1" />
<arrow v-click="[5]" x1="585" y1="310" x2="420" y2="358" color="#953" width="2" arrowSize="1" />

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

<div class="max-w-3xl px-1 text-gray-300 font-serif">
<h3 class="text-yellow-300">"The quality of your code determines the cost of future maintenance." — Martin Fowler</h3>

> _程式碼的品質決定了未來的維護成本。_

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
:enter="{ y: 0, opacity: 1, transition: {delay: 500} }">
  小龍接手一個同事留下的專案，但是裡面光是條件判斷就有 n 種寫法
</div>

<div class="text-gray-300" 
v-motion
:initial="{ y: 40, opacity: 0 }"
:enter="{ y: 0, opacity: 1, transition: {delay: 600} }">


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
  if (score > 90) return 'A';
  else if (score > 80) {
    return 'B';
  } else if (score > 70) {
    return 'C';
  }


  return "F";
}
```

```javascript
const grade = (score) => {
  if (score > 90) return 'A';
  if (score > 80) return 'B';
  if (score > 70) return 'C';
  else {
    return 'F';
  }
};
```

```javascript
// 🔴 版本一：老式寫法
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
  if (score > 90) return 'A';
  // 還是有巢狀但比之前少
  else if (score > 80) {
    return 'B'; // 使用 return 時風格不一致（有些單行、有些 block）
  } else if (score > 70) {
    return 'C';
  }
  // 下方不必要空行過多


  return "F"; // 雙引號單引號沒有統一
}
```

```javascript
// 🟠 版本三：箭頭函式但缺乏可讀性與一致性
const grade = (score) => {
  if (score > 90) return 'A';
  if (score > 80) return 'B';
  if (score > 70) return 'C';
  else {
    // 混合 else 與早期 return
    return 'F'; // 有人不喜歡在前面 if 省略 else，這裡反而加了，也不必要
  }
};
```

```javascript
// ✅ 建議最佳寫法：ESLint 推薦風格 -> 一致 + 易讀
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
//     ✅ 排版乾淨
//     ✅ 簡短易讀
```
````

</div>

<div
  class="text-slate-300 bg-slate-800 px-6 py-2 rounded-md text-left leading-relaxed shadow-md space-y-3"
  v-motion
  v-click="7"
  :initial="{ x: 100, y: -80, opacity: 0 }"
  :enter="{ x: 0, y: -30, opacity: 1, transition: { delay: 200 } }"
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
  :enter="{ x: 0, y: -270, opacity: 1, transition: { delay: 200 } }"
>
  <p class="text-lg font-semibold text-yellow-300">👨‍💼 假設是有主管在 Code Review，場面可能是這樣的：</p>

  <ul class="space-y-2 pl-4 list-disc list-inside text-base">
    <li>
      <strong class="text-rose-400">主管：</strong>
      「這縮排是怎麼回事？<code>if-else</code>是要包到隔壁去嗎怎麼這麼深，我眼睛度數已經夠深了。」
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

<div class="max-w-3xl px-1 text-gray-300 font-serif">

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

無論前端後端，甚麼框架 React、Vue、Laravel 或 .NET 專案，這三個工具不能說必備但都是首選！

<div class="grid grid-cols-1 md:grid-cols-3 gap-6 mt-6" 
v-click
v-motion
:initial="{opacity: 0, y: 100}"
:enter="{y:0, opacity: 100}">
  <!-- TypeScript -->
  <div
    class="bg-slate-800 text-slate-200 p-6 rounded-xl border border-blue-400 shadow-lg animate-glow-blue"
  >
    <div class="text-2xl mb-2 font-serif">🔷 Compiler</div>
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
    class="bg-slate-800 text-slate-200 p-6 rounded-xl border border-emerald-400 shadow-lg animate-glow-green"
  >
    <div class="text-2xl mb-2 font-serif">🔍 Linter</div>
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
    class="bg-slate-800 text-slate-200 p-6 rounded-xl border border-pink-400 shadow-lg animate-glow-pink"
  >
    <div class="text-2xl mb-2 font-serif">✨ Formatter</div>
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

<style>
.card {
  @apply bg-slate-800 text-slate-200 p-6 rounded-xl shadow-lg transition-all duration-500;
}

@keyframes glow-blue {
  0% { box-shadow: 0 0 0px #3b82f6; }
  50% { box-shadow: 0 0 16px #3b82f6aa; }
  100% { box-shadow: 0 0 0px #3b82f6; }
}

@keyframes glow-green {
  0% { box-shadow: 0 0 0px #10b981; }
  50% { box-shadow: 0 0 16px #10b981aa; }
  100% { box-shadow: 0 0 0px #10b981; }
}

@keyframes glow-pink {
  0% { box-shadow: 0 0 0px #ec4899; }
  50% { box-shadow: 0 0 16px #ec4899aa; }
  100% { box-shadow: 0 0 0px #ec4899; }
}

.animate-glow-blue {
  animation: glow-blue 2.2s ease-in-out infinite;
}
.animate-glow-green {
  animation: glow-green 2.2s ease-in-out infinite;
}
.animate-glow-pink {
  animation: glow-pink 2.2s ease-in-out infinite;
}
</style>

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
  course.courseType = typecode1; // 完全不知道 courseType, typecode1 是什麼
  sendToApi(course);
}
```

```typescript
// 引入 TypeScript ✅
enum CourseType {
  Required = 1,
  Elective = 2,
  Online = 3,
}

type Course = {
  courseType: CourseType;
  courseId: string;
  title: string;
};

function enrollCourse(course: Course): void {
  course.courseType = CourseType.Required; // 型別安全，IDE 提示
  course.studentName = 'Joe'; // ❌ Error: 'studentName' 不存在
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
};

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
var memNo = getApiMemberNo(); // ESLint 錯誤: 應使用 const
var memNo = $('input').val();

if (memNo == '123') {
  // ESLint 錯誤: 應使用 ===
  console.log('Member: ' + memNo); // ESLint 警告: 使用模板字串
}

var tempData = []; // ESLint 警告：tempData 未使用
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
transition: fade
layout: center
---

<div class="max-w-3xl px-1 text-gray-300">
<h3 class="text-yellow-300">"Quality is a promise in every line of code." — Ward Cunningham</h3>

> 品質是每行程式碼的承諾。

</div>

---

# Prettier：格式化的藝術家 🎨

````md magic-move
```js
// 😵 當格式不統一的時候
function getCourseInfo() {
  var course = { id: 456, title: 'TypeScript 入門' };
  if (course.title == 'TypeScript 入門') return course;
}
```

```js
// ✨ Prettier 處理後
function getCourseInfo() {
  const course = {
    id: 456,
    title: 'TypeScript 入門',
  };

  if (course.title === 'TypeScript 入門') {
    return course;
  }
}
```
````

<div v-click="2" v-motion :enter="{x:0,y:-250, opacity: 50}" :initial="{x:100,y:-500, opacity:100}">

### ⚡ Prettier 的威力

<div class="grid grid-cols-3 gap-4 text-slate-100 text-sm">

<div class="bg-slate-800 p-4 rounded-lg shadow-md border-l-4 border-yellow-400" >
<h4 class="text-yellow-300 font-bold mb-2">⚡ 自動格式化 (optional)</h4>
<ul class="list-disc list-inside space-y-1">
  <li>存檔時自動整理</li>
  <li>統一縮排（2 spaces）</li>
  <li>強制使用單引號</li>
  ...
</ul>
</div>

<div class="bg-slate-800 p-4 rounded-lg shadow-md border-l-4 border-pink-400" >
<h4 class="text-pink-300 font-bold mb-2">🤝 減少爭議</h4>
<ul class="list-disc list-inside space-y-1">
  <li>不再爭論 tab vs. space</li>
  <li>單引號 vs. 雙引號 統一</li>
  <li>Code Review 聚焦邏輯</li>
  ...
</ul>
</div>

<div class="bg-slate-800 p-4 rounded-lg shadow-md border-l-4 border-green-400" >
<h4 class="text-green-300 font-bold mb-2">🚀 提升效率</h4>

```json
{
  "semi": true,
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "es5"
}
```

<p class="mt-2">自行制定規則，全專案統一！</p>
</div>

</div>
</div>

---

### 💡 補充說明：VS formatter 與 Prettier 的差異

<div class="bg-slate-900 border-l-4 border-blue-500 p-4 text-sm text-slate-200 rounded shadow-lg" v-motion :initial="{ opacity: 0, x: 50 }" :enter="{ opacity: 1, x: 0 }">

🛠 <strong>Visual Studio</strong> 使用的是不同的 <code>.editorconfig</code> 或 <code>.vssettings</code> 檔案來格式化程式碼。<br/>
若你在 VS 與 VS Code 混合開發，建議雙方格式化工具都配置一致，避免產生格式衝突。

</div>

<div
  class="mt-4 p-4 rounded-md bg-slate-800 text-slate-100 shadow-md"
  v-click
  v-motion
  :initial="{ scale: 0.95, opacity: 0 }"
  :enter="{ scale: 1, opacity: 1, transition: { duration: 400 } }"
>
  <h3 class="text-lg font-bold text-yellow-300 mb-3">🧪 Prettier vs. ESLint 差異</h3>

  <table class="table-auto w-full text-sm border-collapse border border-slate-600">
    <thead>
      <tr class="bg-slate-700 text-slate-200">
        <th class="border border-slate-600 px-3 py-2 text-left">工具</th>
        <th class="border border-slate-600 px-3 py-2 text-left">用途</th>
        <th class="border border-slate-600 px-3 py-2 text-left">主要功能</th>
      </tr>
    </thead>
    <tbody>
      <tr class="hover:bg-slate-700">
        <td class="border border-slate-600 px-3 py-2 font-semibold text-blue-300">ESLint</td>
        <td class="border border-slate-600 px-3 py-2">程式碼品質檢查</td>
        <td class="border border-slate-600 px-3 py-2">語法錯誤、風格建議、最佳實踐</td>
      </tr>
      <tr class="hover:bg-slate-700">
        <td class="border border-slate-600 px-3 py-2 font-semibold text-pink-300">Prettier</td>
        <td class="border border-slate-600 px-3 py-2">程式碼格式化</td>
        <td class="border border-slate-600 px-3 py-2">排版、縮排、字串格式等</td>
      </tr>
    </tbody>
  </table>

  <div class="mt-4 text-green-300 font-semibold text-sm">
    ✅ 最佳實踐：<span class="text-white">搭配使用，品質與風格兼顧！</span>
  </div>
</div>

---
transtion: slide-up
layout: center
---

<div class="max-w-3xl px-1 text-gray-300">
<h3 class="text-yellow-300">"Consistent formatting makes code more readable." — John Carmack</h3>

> 一致的格式讓程式碼更具可讀性。

</div>

---
transtion: fade-out
---

## 🪄 Before vs After 🎭

<div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm text-slate-100 mt-2">

  <!-- Before -->
  <div
    class="bg-red-900/40 p-3 rounded-md shadow-inner border border-red-600"
    v-motion
    :initial="{ x: -100, opacity: 0 }"
    :enter="{ x: 0, opacity: 1, transition: { duration: 400 } }"
  >
    <h3 class="font-bold text-red-300 text-lg mb-2">😰 改善前</h3>

```js {monaco}
function sendToApi(course, memNo) {
  console.log('課程:', course);
  console.log('成員:', memNo);
}

function addMember(course) {
  var memNo = sessionStorage.getItem('memNo');
  // 過度巢狀
  if (memNo !== '') {
    var memNo = $('input').val(); // 重複宣告，容易覆蓋資料！
    if (typeof memNo === 'string') {
      course.typecode = typecode1; // 不明變數，型別不清楚
      if (course.typecode) {
        sendToApi(course, memNo); // 不知道函數的傳遞位置順序意義
      }
    }
  }
}
addMember(); // 缺少參數
```

  </div>

  <!-- After -->
  <div
    class="bg-green-900/40 p-4 rounded-md shadow-inner border border-green-600 overflow-y-auto max-h-lg"
    v-motion
    v-click
    :initial="{ x: 100, opacity: 0 }"
    :enter="{ x: 0, y: -80, opacity: 1, transition: { duration: 400, delay: 300 } }"
  >
    <h3 class="font-bold text-green-300 text-lg mb-2">😊 改善後</h3>

```ts {monaco}
enum CourseType {
  Required = 1,
  Elective = 2,
  Online = 3,
}

type Course = {
  courseType: CourseType;
  courseId: string;
  title: string;
};

/**
 * @description 傳送API
 * @param course - 課程資料
 * @param memNo - 現在使用者ID
 */
function sendToApi(course: Course, memNo: string) {
  console.log('課程:', course);
  console.log('成員:', memNo);
}

/** 新增成員 */
function addMember(course: Course): void {
  const memNo = sessionStorage.getItem('memNo');
  if (!memNo) return; // 若 memNo 不存在則直接返回
  course.courseType = CourseType.Required; // 型別安全，IDE 提示
  sendToApi(course, memNo);
}
addMember();
```

  </div>
</div>

<!-- 結果 -->
<div
  class="mt-6 px-4 py-3 bg-slate-800 rounded-md shadow max-w-lg mx-auto text-sm text-slate-200"
  v-click
  v-motion
  :initial="{ y:0, scale: 0.9, opacity: 0 }"
  :enter="{ y:-380, scale: 1, opacity: 1, transition: { duration: 300, delay: 300 } }"
>
  🚀 <strong class="text-green-300">結果：</strong>
  <ul class="mt-2 space-y-1">
    <li>🐞 Bug 減少 <span class="font-bold text-yellow-300">70%</span></li>
    <li>⚡ 開發效率提升 <span class="font-bold text-yellow-300">50%</span></li>
    <li>🔍 閱讀時間節省 <span class="font-bold text-yellow-300">80%</span></li>
  </ul>
</div>

<!-- Inline style -->
<style>
.footnotes-sep {
  @apply mt-5 opacity-10;
}
.footnotes {
  @apply text-sm opacity-75;
}
.footnote-backref {
  display: none;
}
</style>

---
transtion: slide-right
---

# Wrap up

<div class="grid grid-cols-1 md:grid-cols-2 gap-6 mt-6 text-slate-200 text-sm">

  <!-- 從前的小龍 -->
  <div
    class="bg-red-900/40 rounded-md p-4 border border-red-500 shadow-inner"
    v-motion
    :initial="{ x: -100, opacity: 0 }"
    :enter="{ x: 0, opacity: 1, transition: { duration: 400 } }"
  >
    <h3 class="text-red-300 text-lg font-bold mb-2">😰 從前的小龍</h3>
    <ul class="list-disc list-inside space-y-1">
      <li>型別錯誤導致錯誤難以維護</li>
      <li>花費大量時間 debug</li>
      <li>程式碼難以維護，大家各寫各的，自己的能跑就好</li>
      <li>團隊協作效率低，基本上是一台可以跑但是很醜的車</li>
      <li>因為錯誤難以掌控所以操作邏輯一律丟給後端</li>
    </ul>
  </div>

  <!-- 現在的小龍 -->
  <div
    class="bg-green-900/40 rounded-md p-4 border border-green-500 text-yellow-500 shadow-inner"
    v-motion
    v-click
    :initial="{ x: 100, opacity: 0 }"
    :enter="{ x: 0, opacity: 1, transition: { duration: 400, delay: 200 } }"
  >
    <h3 class="text-green-300 text-lg font-bold mb-2">😊 現在的小龍</h3>
    <ul class="list-disc list-inside space-y-1">
      <li>開發編譯時就發現問題即使處理</li>
      <li>程式碼穩定可靠，不容易輕易崩潰</li>
      <li>開發維護效率提升，時間更好掌控</li>
      <li>團隊合作順暢，互相運作正常</li>
      <li>前後各司職責</li>
    </ul>
  </div>
</div>

<!-- 結語 -->
<div
  class="mt-6 text-center text-xl text-yellow-300 font-bold"
  v-click
  v-motion
  :initial="{ scale: 0.9, opacity: 0 }"
  :enter="{ scale: 1, opacity: 1, transition: { duration: 300, delay: 300 } }"
>
  🚀 讓我們一起往右側前進！
</div>

---

## layout: center

## 導入計畫：每週工作坊 📚

> 實際操作 Demo • 踩坑經驗分享 • 如何改善現有問題

---
layout: center
class: text-center
---

# 謝謝聆聽

[把 TypeScript、ESLint、Prettier、Alias 摻再一起做沙尿牛丸 ](https://rexhung0302.github.io/2022/11/06/20221106/) ·[為甚麼要有框架](https://developer.mozilla.org/zh-TW/docs/Learn_web_development/Core/Frameworks_libraries/Introduction) · [GitHub](https://github.com/davelin18yufan/typescript_eslint_slide) · [Showcases](https://sli.dev/resources/showcases)

<PoweredBySlidev mt-10 />
