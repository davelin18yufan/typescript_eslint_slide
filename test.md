
theme: seriphbackground: https://images.unsplash.com/photo-1517180102446-f3ece451e9d8?ixlib=rb-4.0.3&auto=format&fit=crop&w=2340&q=80title: 提升開發效率的利器info: |
TypeScript + ESLint + Prettier
  讓 JavaScript 開發更安全、更高效的工具組合class: text-centerdrawings:  persist: falsetransition: slide-leftmdc: true
提升開發效率的利器
TypeScript + ESLint + Prettier
讓 JavaScript 開發更安全、更高效

  
  小龍的程式碼總是「爆炸」，他需要救星！



  
    開始小龍的故事 
  



*“簡單的程式碼是最好的程式碼。” —— Kent Beck*





transition: fade-out
小龍的故事開場 😰




場景一：神秘的 typecode 危機 🎰
小龍在 .NET 專案中，從 HTML <script> 標籤引入了一個 typecode1 到 typecode10，完全不知道它們是什麼，也找不到來源！
<script src="some-mystery-script.js"></script>

function submitOrder(order) {
  order.typecode = typecode1; // 這是什麼？數字？字串？物件？
  sendToApi(order); // 送出後只能祈禱伺服器不炸
}

每次送出 API，小龍都得重啟伺服器、打開 DevTools 慢慢試，效率低到像在玩「俄羅斯輪盤」！




小龍的痛苦日常 📱

🎲 typecode 來源不明：完全靠猜測，API 送出後才知對錯  
😰 效率低下：每次測試都要重啟伺服器，浪費時間  
💥 Bug 頻發：typecode 型別錯誤導致訂單處理失敗  
🔍 80% 時間在試錯：小龍快被神秘程式碼逼瘋


小龍的真實告白：
「這 typecode 到底是誰寫的？為什麼沒人告訴我它是什麼！」
「我只想好好送個 API，為什麼這麼難？🙏」







*“好的程式碼應該像散文一樣清晰。” —— Robert C. Martin*





小龍的第二個困擾 🤯




場景二：會員按鈕的詭異 Bug 🔍
小龍負責一個會員資料更新功能，卻收到 Bug 單：按鈕點擊後 API 送出錯誤的會員編號！
function updateMember() {
  var memNo = getApiMemberNo(); // API 回傳 '123'
  var memNo = $("input").val(); // 表單輸入 '456'
  sendToApi(memNo); // 為什麼總是送出 '456'？
}

小龍找了兩小時才發現：var 重複宣告導致 memNo 被覆蓋，API 送出錯誤資料，按鈕功能異常！




小龍的週五噩夢 😱

🚨 Bug 單：「會員更新按鈕失效」  
🔍 找了兩小時：程式碼看起來沒問題啊！  
💡 原來是 var：重複宣告讓 memNo 被覆蓋  
🤦‍♂️ 週末加班：客戶抱怨，主管要求改進


小龍的內心 OS：
「為什麼 var 可以重複宣告？」
「這 Bug 為什麼藏得這麼深？」
「我只是想更新個會員資料啊！」







*“程式碼的品質決定了未來的維護成本。” —— Martin Fowler*





小龍的第三個困擾 😤




場景三：維護別人的專案 ⚔️
小龍接手一個前同事留下的 .NET 專案，程式碼風格像「程式碼大亂鬥」：
// 前同事的遺作
function getUserInfo(){
    let user={name:"John",age:25};
    if(user.name=="John"){
        return user
    }
}

var getOrderInfo=function(){
var order={'id':123,"status":'pending',}
if(order.status=="pending")
return order
}

命名不一致（userInfo vs. orderInfo）、縮排混亂、var 與 let 混用，簡直是維護地獄！




Code Review 現場實況 🎬
主管：「這縮排是怎麼回事？」小龍：「誰又用 var 了？不是說好用 let？」同事：「單引號雙引號能不能統一？」實習生：「我不知道要跟誰的風格...」
公司血淚史 😭

📝 Code Review 耗時：70% 在討論格式  
🔥 衝突不斷：每個人有自己的風格  
⏰ 效率低落：邏輯問題被格式掩蓋  
🤯 新人困惑：無從下手


小龍的觀察：
「這程式碼像考古文物！」
「每個檔案風格都不一樣！」
「Code Review 簡直是解謎遊戲！」







*“一致性是團隊協作的基石。” —— Douglas Crockford*





layout: centerclass: text-center
小龍決定尋找解決方案 🔍
💡

如何讓 JavaScript 開發更安全、更有效率？

*“好的工具能讓複雜的工作變簡單。” —— Linus Torvalds*





解決方案：前端開發三本柱 🏛️

🌟 現代前端開發的基石工具
無論 React、Vue 或 .NET 專案，這三個工具都是必備！





🔷

TypeScript
型別安全

編譯時錯誤檢查
強型別系統
增強 IDE 支援


React、Vue 3、Angular 官方推薦





🔍

ESLint
程式碼品質

統一程式碼風格
檢測潛在問題
推廣最佳實務


Create React App、Vue CLI 內建





✨

Prettier
格式美化

自動格式化
統一程式碼風格
減少格式爭議


GitHub、VS Code 預設整合







三本柱支撐，解決小龍的所有困擾！



TypeScript：型別安全的救星 🛡️




小龍的 JavaScript 🚫
function submitOrder(order) {
  order.typecode = typecode1; // 完全不知道 typecode1 是什麼
  sendToApi(order); // 送出後伺服器可能炸
}

升級到 TypeScript ✅
enum OrderType {
  Standard = 'typecode1',
  Premium = 'typecode2',
  Express = 'typecode3',
}

/** @typedef {Object} Order
 *  @property {OrderType} typecode
 */
function submitOrder(order: Order): void {
  order.typecode = OrderType.Standard; // 型別安全，IDE 提示
  sendToApi(order);
}





與 C# 的相似性 🤝

好消息！
TypeScript 與 C# 由同一人設計
Anders Hejlsberg (微軟首席架構師)


C# 風格
public enum OrderType {
    Standard,
    Premium,
    Express
}

public class Order {
    public OrderType TypeCode { get; set; }
}

TypeScript 風格
enum OrderType {
  Standard,
  Premium,
  Express,
}

interface Order {
  typecode: OrderType;
}

學習成本低，.NET 開發者輕鬆上手！





*“型別是程式設計的基石。” —— Anders Hejlsberg*





ESLint：程式碼品質守護者 🛡️




沒有 ESLint 的痛苦 😰
var memNo = getApiMemberNo();
var memNo = $("input").val();
if (memNo == '123') { // == 可能導致錯誤
  console.log("Member: " + memNo);
}
var tempData = []; // 未使用變數

配置 ESLint 後 ✨
const memNo = getApiMemberNo() || $('input').val();
if (memNo === '123') { // 強制使用 ===
  console.log(`Member: ${memNo}`); // 模板字串
}
// ESLint 警告：tempData 未使用





ESLint 解決的問題
🚫 禁止危險寫法

禁用 var，強制 const/let
禁用 ==，強制 ===
檢測未使用變數

📋 統一程式碼風格

強制 ES6+ 語法
統一命名規則 (camelCase)
強制模板字串

🎯 針對我們的問題
{
  "no-var": "error",
  "prefer-const": "error",
  "eqeqeq": "error",
  "prefer-template": "error"
}






*“品質是每行程式碼的承諾。” —— Ward Cunningham*





Prettier：格式化的藝術家 🎨




格式混亂的專案 😵
function getOrderInfo(){
var order={'id':123,"status":'pending',}
if(order.status=="pending")
return order
}

Prettier 處理後 ✨
function getOrderInfo() {
  const order = {
    id: 123,
    status: 'pending',
  };
  if (order.status === 'pending') {
    return order;
  }
}





Prettier 的威力
⚡ 自動格式化

存檔時自動整理
統一縮排（2 spaces）
統一單引號

🤝 減少爭議

不再爭論 tab vs. space
單引號 vs. 雙引號統一
Code Review 聚焦邏輯

🚀 提升效率
{
  "semi": true,
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "es5"
}


一鍵美化，全專案統一！







*“一致的格式讓程式碼更具可讀性。” —— John Carmack*





神奇的轉變：Before vs After 🎭




改善前的小龍 😰
function submitOrder(order) {
  var typecode = typecode1;
  var memNo = getApiMemberNo();
  var memNo = $("input").val();
  order.typecode = typecode;
  sendToApi(order);
}





改善後的小龍 😊
enum OrderType {
  Standard = 'typecode1',
  Premium = 'typecode2',
}

interface Order {
  typecode: OrderType;
  memNo: string;
}

function submitOrder(order: Order): void {
  const memNo = getApiMemberNo() || $('input').val();
  order.memNo = memNo;
  sendToApi(order);
}






結果：Bug 減少 70%，開發效率提升 50%，Code Review 時間節省 80%！



導入計畫：每週 30 分鐘工作坊 📚




第 1-2 週：Prettier 工作坊
🎯 主題：「一鍵美化的魔法」
時間：每週五下午 30 分鐘
第一週：基礎安裝

什麼是 Prettier？
VS Code 整合設定
存檔自動格式化

第二週：團隊規範

.prettierrc 設定檔
忽略檔案設定
Git hooks 整合

案例分享：「小龍再也不用手動對齊程式碼了！」




第 3-5 週：ESLint 工作坊
🎯 主題：「程式碼守門員」
時間：每週五下午 30 分鐘
第三週：規則認識

ESLint 是什麼？
常見規則解說
錯誤 vs 警告

第四週：自訂規則

適合我們團隊的規則
禁用危險語法
強制最佳實務

第五週：實戰演練

修正現有專案警告
分享踩坑經驗

案例分享：「週五噩夢不再來！」




第 6-8 週：TypeScript 工作坊
🎯 主題：「型別安全之路」
時間：每週五下午 30 分鐘
第六週：基礎型別

基本型別介紹
與 C# 的對比
interface 與 enum

第七週：進階應用

泛型使用
API 介面定義
型別推導

第八週：實戰整合

現有專案改造
漸進式導入策略

案例分享：「小龍的 API 再也不會爆炸了！」





🎁 每次工作坊都有：
• 實際操作 Demo • 踩坑經驗分享 • Q&A 時間 • 小點心 ☕



小龍的成功轉變 🌟




從前的小龍 😰

型別錯誤頻發
花費大量時間 debug
程式碼難以維護
團隊協作效率低





現在的小龍 😊

編譯時發現問題
程式碼穩定可靠
開發速度提升
團隊合作順暢






🚀
你也可以成為下一個成功案例！



總結：為什麼選擇這個組合？ 🎯




技術優勢 💪

TypeScript：與 C# 相似，學習成本低
ESLint：確保程式碼品質
Prettier：一鍵美化，減少爭議

團隊效益 👥

🔍 錯誤減少：編譯時發現問題
⚡ 效率提升：IDE 提示更準確
🤝 協作改善：統一程式碼風格
📚 維護性：程式碼更易讀懂





投資報酬率 📊



短期（1個月）：
程式碼格式統一，Review 效率提升



中期（3個月）：
Bug 數量減少，開發更有信心



長期（6個月+）：
程式碼品質提升，維護成本降低









讓我們一起提升開發品質，擁抱現代化工具！



Thank You! 🙏
準備好開始你的現代化 JavaScript 之旅了嗎？

  
    TypeScript + ESLint + Prettier = 更好的開發體驗
  



💬 有任何問題歡迎討論！



*“投資於工具，就是投資於未來。” —— Jeff Atwood*


