# 小飛俠高階飛行傘網站｜逆向詳細規格

> 來源檔案：`WebPage_11515122/outline/index.html`  
> 文件用途：依據已實作完成之小飛俠高階飛行傘一頁式推廣網站，讀取架構、樣式、視覺組件與互動腳本，逆向產出完整技術規格文件，以利後續精確修改與擴充。  
> 來源版本 SHA-256：`14C35C0F5EA3C0F23B6A42672C16FCA9726F066F7B5EBA0932F9DC54F10E1A59`

---

## 1. 專案概述

| 項目 | 規格內容 |
|---|---|
| **品牌名稱** | 小飛俠（PETER PAN PARAGLIDING） |
| **網站類型** | 高階極限運動／飛行傘俱樂部形象宣傳、體驗方案推廣與在線預約試算之一頁式網站（Single-Page Website） |
| **語系設定** | 繁體中文，HTML `lang="zh-Hant"`，編碼 UTF-8 |
| **目標受眾** | 跳傘愛好者、極限運動追求者、嚮往壯闊高空視角與深度旅遊體驗之消費客群 |
| **主要用途** | 全面推廣飛行傘極限運動、展示歐洲進口頂規傘具與專業教練團陣容、促成飛行體驗消費與在線預約轉換 |
| **網頁架構** | 單一 `index.html` 整合 HTML5、內嵌 CSS3 樣式與原生 JavaScript，無外部編譯器或後端依賴 |
| **核心標語** | 「御風而行，征服天際・開啟您的頂級高空冒險」 |

### 1.1 品牌語調與視覺風格

- **語調定調**：自信、專業、冒險、尊爵、安全。文字突顯千米巡航熱氣流、特技離心力感受與嚴謹安全認證，強調「跳傘愛好者指定」之專業高階地位。
- **視覺定調**：採用深空黑藍（`#0A0E17`、`#111827`）為底色，搭配高飽和度的空氣動力活力金黃（`#FFC700`）作為核心品牌識別色，創造出如超跑與高階戶外極限裝備般的高級黑金運動質感。

---

## 2. 技術邊界與規範

1. **核心技術**：HTML5 語意化標籤、純原生 CSS3（CSS Custom Properties、Flexbox、CSS Grid）、原生 ES6+ JavaScript。
2. **單檔架構**：整頁包含 1 個 `<style>` 與 1 個 `<script>` 標籤，不需 Node.js 或打包工具，支援開箱即用。
3. **外部字型資源**：
   - 英文/數字/數據：Google Fonts `Montserrat` (400, 600, 700, 800, 900)
   - 繁體中文內文與標題：Google Fonts `Noto Sans TC` (300, 400, 500, 700, 900)
4. **圖像與圖示規範**：
   - 全頁不依賴未授權之外部外部點陣圖，所有品牌標誌、飛行傘視覺、HUD 儀表板、安全盾牌及操作圖示均採用手繪向量 SVG 及純 CSS 形狀漸層生成，確保超快載入速度與高解析度適應性。
5. **導覽與捲動**：所有導覽錨點均為同頁平滑捲動（`html { scroll-behavior: smooth; }`），錨點包含 `#home`、`#about`、`#packages`、`#safety`、`#booking`、`#faq`。

---

## 3. SEO 與基礎中繼資料（Meta）

```html
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>小飛俠 PARAGLIDING｜頂級高階飛行傘體驗・御風翱翔</title>
  <meta name="description" content="小飛俠飛行傘俱樂部——專為熱愛高空冒險與跳傘愛好者打造的頂級飛行品牌。配備歐洲進口頂規傘具、FAI認證教練團、雙備傘安全系統與4K全景影像紀錄，帶您俯瞰壯闊山海。">
</head>
```

---

## 4. 視覺系統與 Design Tokens

### 4.1 色彩變數 Token（`:root`）

| Token 名稱 | 數值（Hex / RGBA） | 用途說明 |
|---|---|---|
| `--primary-yellow` | `#FFC700` | 主品牌色、CTA 按鈕底色、重要數值、發光焦點、高亮文字 |
| `--primary-yellow-hover` | `#E5B200` | 按鈕 Hover 狀態加深黃 |
| `--yellow-subtle` | `#FFF3C4` | 淺黃輔助點綴色 |
| `--yellow-glow` | `rgba(255, 199, 0, 0.35)` | 陰影光暈、呼吸燈效果 |
| `--bg-dark` | `#0A0E17` | 全站主底色、深黑夜空質感背景 |
| `--bg-surface` | `#111827` | 次要區塊背景（交替對比） |
| `--bg-card` | `#162033` | 卡片、面板、HUD 底色 |
| `--bg-card-hover` | `#1E2B45` | 卡片懸停時的提亮底色 |
| `--text-white` | `#FFFFFF` | 主標題、重要標籤與高亮文字 |
| `--text-main` | `#F1F5F9` | 內文標準文字色 |
| `--text-muted` | `#94A3B8` | 次要段落說明、輔助標註、灰階資訊 |
| `--border-color` | `rgba(255, 255, 255, 0.1)` | 基礎微弱分界線 |
| `--border-yellow` | `rgba(255, 199, 0, 0.4)` | 核心卡片與焦點面板之金色強調邊框 |
| `--shadow-card` | `0 16px 36px rgba(0, 0, 0, 0.35)` | 懸浮深度陰影 |

### 4.2 排版與容器設定

- **主容器**：`.container { width: min(1200px, calc(100% - 2.5rem)); margin-inline: auto; }`
- **大區塊間距**：桌面版主要區塊上下 padding 固定為 `7rem`（約 112px）；手機版自動隨內容彈性縮排。
- **圓角規範**：按鈕圓角為 `8px`（主按鈕）與 `30px`（膠囊 CTA）；卡片圓角為 `16px` 至 `24px`。

---

## 5. 頁面架構與各區塊詳細規格

```text
body
├─ header.header（固定吸頂導覽列）
├─ section.hero#home（首屏主視覺與動態 HUD 儀表板）
├─ section.features-section#about（品牌核心優勢 4 欄卡片）
├─ section.pricing-section#packages（3 大精選飛行方案與消費推廣）
├─ section.safety-section#safety（安全保證規範與 100% 雙備傘認證）
├─ section.booking-section#booking（線上預約表單與即時費用試算小計面板）
├─ section.reviews-section（跳傘愛好者 5 星口碑評價）
├─ section.faq-section#faq（4 組手風琴常見問答）
├─ footer.footer（4 欄式頁尾、空域基地與版權聲明）
└─ div.modal-overlay#bookingModal（預約成功互動彈窗）
```

---

### 5.1 頂部導覽列（Header & Navbar）

- **DOM 結構**：`header.header` > `div.container.nav-container`
- **視覺規範**：
  - 吸頂定位（`position: fixed; top: 0; left: 0; width: 100%; z-index: 1000;`）。
  - 背景色：`rgba(10, 14, 23, 0.85)` 搭配高斯模糊 `backdrop-filter: blur(16px)`。
  - 高度：`76px`，底部附帶 `1px solid var(--border-color)` 分隔線。
- **品牌 Logo 組件**：
  - 左側 `42px * 42px` 金黃漸層圓角形 Icon，內嵌精緻雙翼飛行傘幾何 SVG。
  - 右側雙層標題：上層白字「小飛俠」（`1.35rem`、`font-weight: 900`），下層金黃英文字「PETER PAN PARAGLIDING」（`0.68rem`、`letter-spacing: 0.16em`）。
- **導覽連結清單（`.nav-menu`）**：
  - 項目：品牌優勢 (`#about`)、飛行方案 (`#packages`)、安全認證 (`#safety`)、即時試算 (`#booking`)、常見問題 (`#faq`)。
  - 懸停互動：字色漸變轉為金黃色，底部自左向右滑出 `2px` 金黃動態底線。
- **頂部 CTA 按鈕**：
  - 金黃色膠囊圓角（`border-radius: 30px`），文字「立即預約 →」，直達 `#booking`。
- **行動選單切換鈕（`.mobile-toggle`）**：
  - 預設隱藏，於螢幕寬度 $\le 768\text{px}$ 時顯示 `☰` 漢堡按鈕。

---

### 5.2 首屏主視覺（Hero Section：`#home`）

| 項目 | 規格內容 |
|---|---|
| **佈局方式** | 兩欄式 CSS Grid（比例 `1.15fr : 0.85fr`），垂直置中，欄距 `3.5rem` |
| **背景效果** | 多重徑向漸層光暈感（右上方金黃光暈 + 左下方深藍光暈），疊加點狀網格光效 `.hero-glow-lines` |
| **左欄內容** | 狀態標籤、H2 主標題、品牌副標、雙 CTA 按鈕、三組關鍵信任數據 |
| **右欄內容** | 科技感 HUD 飛行遙測儀表板卡片（SVG 飛行傘動態視差圖形 + 實時模擬數據） |

- **文案規格**：
  - **狀態膠囊**：金黃邊框膠囊徽章，內含呼吸脈衝圓點（`animation: pulse 1.8s infinite`），文字「高階飛行傘首選品牌・全台最高飛行高度」。
  - **H2 主標**：`御風而行，征服天際 / 開啟您的【頂級高空冒險】`（高亮字套用 `--primary-yellow`）。
  - **副標內文**：介紹小飛俠專為跳傘愛好者打造，採用歐洲最高認證傘具與國家級教練隨行。
  - **CTA 組合**：主按鈕「探索飛行方案 →」（金黃底黑字）＋ 次按鈕「檢視安全防護規格」（白邊框透明底）。
  - **里程碑數據列（`.hero-stats`）**：
    1. `10,000+`｜累積安全起降架次
    2. `1,200m`｜最高盤旋巡航高度
    3. `100%`｜雙備傘獨立防護系統
- **右側 HUD 飛行儀表板（`.flight-hud`）**：
  - 頂部狀態列：右上角浮動標籤「⚡ 2026 最新特技翼型」、綠燈指示「空域暢通」。
  - 中間飛行傘 SVG 幾何插畫：包含黃橘漸層主傘翼（`url(#gliderGrad)`）、傘繩組、飛行員座艙與動態氣流軌跡。
  - 底部數據矩陣（`.hud-metrics` 3 欄）：上升熱氣流 `+4.2 m/s`、當前飛行海拔 `1,080 M`、巡航滑翔時速 `42 km/h`。

---

### 5.3 品牌核心優勢（Features Section：`#about`）

- **區塊標頭**：小標 `PREMIUM STANDARD`，主標「高階飛行標準，重新定義高空體驗」。
- **卡片式網格**：4 欄響應式 Grid（`grid-template-columns: repeat(auto-fit, minmax(260px, 1fr))`）。
- **4 大卡片內容**：
  1. **歐洲 EN-A/B 認證傘具**：全機隊採購瑞士 Advance 及奧地利頂級競技型雙人傘，兼具極致滑翔比與氣流穩定性。
  2. **國際 FAI 認證總教練**：教練團具備 15 年以上高空跳傘與滑翔傘資歷，累積起降破千小時。
  3. **4K 60FPS 全景空拍攝影**：隨行配備最新款 GoPro 與 360 度全景相機，當日即時傳輸檔案。
  4. **專屬越野接駁與起飛貴賓席**：四驅全地形越野車直達山頂起飛平台，並提供起降 VIP 冷氣觀景休息室。

---

### 5.4 飛行專案體驗（Packages Section：`#packages`）

本區塊為**促進消費與業務轉換的核心**，設計三款差異化方案卡片：

| 專案名稱 | 蔚藍經典巡航 | 千米熱氣流深空越野（⭐ 熱門推薦） | 極限特技與進階培訓 |
|---|---|---|---|
| **級別標籤** | `ENTRY LEVEL` | `MOST POPULAR` | `EXTREME ACRO` |
| **定價** | **NT$ 3,200** / 人次 | **NT$ 5,800** / 人次 | **NT$ 8,800** / 人次起 |
| **特殊外觀** | 標準暗色卡片 | 金黃雙層邊框、微放大（`scale(1.04)`）、發光陰影、頂部附「🔥 跳傘玩家力推・熱門首選」浮動標籤 | 標準暗色卡片 |
| **核心權益清單** | 1. 滯空時間 12-18 分鐘<br>2. 頂規雙人傘具全套配備<br>3. 國家級合格教練 1 對 1<br>4. 起飛場越野專車接駁<br>5. 500 萬高額意外責任險 | 1. **滯空 30-40 分鐘（雙倍時長）**<br>2. **盤旋爬升至海拔 1,000m+**<br>3. **贈送 4K 60FPS 空拍影片**<br>4. 雲端俯衝與大角度盤旋體感<br>5. 貴賓專屬起降點冷氣休息室<br>6. 頒發小飛俠專屬越野飛行證書 | 1. 高 G 重力螺旋下降（Spiral Dive）<br>2. 翼尖搖擺極限動態操控（Wingover）<br>3. 360° 雙鏡頭多視角 4K 剪輯<br>4. 獨立飛行執照（P1/P2）專屬諮詢<br>5. 總教練 1 對 1 空氣動力學講解 |
| **按鈕與行為** | Outline 按鈕，點擊觸發 `selectPackage('蔚藍經典巡航', 3200)` | Primary 金黃按鈕，點擊觸發 `selectPackage('千米熱氣流深空越野', 5800)` | Outline 按鈕，點擊觸發 `selectPackage('極限特技與進階培訓', 8800)` |

---

### 5.5 安全保證與認證規格（Safety Section：`#safety`）

- **佈局**：兩欄式佈局（左欄安全清單 1fr、右欄認證面板 1fr）。
- **左欄 3 大安全防護機制**：
  1. **雙重獨立備用副傘系統**：配置經氣動檢驗之最新備用傘，定期由合格傘檢師折疊與保養。
  2. **微型高空氣象雷達即時連線**：實時監控起飛場與空域風速、陣風及熱對流狀況，未達標準絕不起飛。
  3. **五點式防護氣囊保護座袋**：人體工學座袋配備厚實緩衝氣囊，提供起降頂尖防衝擊吸收。
- **右欄安全認證徽章面板（`.safety-badge-panel`）**：
  - 居中黃色盾牌圖示、標題「100% 雙備傘安全承諾」。
  - 雙指標數據：`0 事故`（歷史安全防護紀錄）與 `100%`（傘裝備檢核合格率）。

---

### 5.6 即時預約試算系統（Booking Section：`#booking`）

結合表單輸入與動態計算面板，實現零跳頁之流暢互動體驗：

#### 表單欄位（Form Controls）
1. **飛行專案下拉選單（`#packageName`）**：
   - 選項一：蔚藍經典巡航（NT$ 3,200）
   - 選項二：千米熱氣流深空越野（NT$ 5,800，預設選中）
   - 選項三：極限特技與進階培訓（NT$ 8,800）
2. **預計飛行日期（`#flightDate`）**：
   - 原生 `type="date"`，JavaScript 自動填入明日日期，並綁定 `min` 屬性禁止選擇過去日期。
3. **預約人數（`#passengerCount`）**：
   - 可選 1 位至 4 位同行（選 4 位加註提示贈送專屬空拍剪輯）。
4. **聯絡資訊**：
   - 姓名（`#userName`，`required`）
   - 電話（`#userPhone`，`required`）
5. **升級加值服務核取方塊（Checkboxes）**：
   - `4K 60FPS GoPro 全景錄影空拍包`（每人 +NT$ 800，`#addonGopro`）
   - `高鐵/火車站 VIP 專車來回直達接送`（每人 +NT$ 500，`#addonTransfer`）
   - `精裝版金屬刻字個人高空首飛成就勳章`（每人 +NT$ 300，`#addonCertificate`）

#### 右側即時試算面板（`.summary-panel`）
- **即時連動項目**：
  - 專案項目名稱（`#summaryPackage`）
  - 預約人數（`#summaryCount`）
  - 專案基底費用（`#summaryBasePrice`）
  - 加值項目合計（`#summaryAddons`）
  - 保險與規費標註（綠色標示：已全額內含 NT$ 0）
  - **預估應付金額（`#summaryTotal`）**：大字號金黃色顯示，附帶千分位格式化（如 `NT$ 5,800`）。
- **底端安心提示**：註明因氣候不可抗力取消時，享有全額退款或免費延期保證。

---

### 5.7 跳傘愛好者口碑評價（Testimonials：`.reviews-section`）

- 3 欄等寬評價卡片，呈現真實社群信任背書：
  1. **高振邦（USPA 跳傘 C 照愛好者）**：「身為跳傘經驗者，熱氣流盤旋直接爬升超過一千米，特技螺旋離心力讓人血脈賁張，設備教練全台頂尖！」
  2. **林芷芸（極限運動攝影師）**：「Advance 傘具超級平穩，五點式座袋安全感十足，4K 空拍影片畫質好到能當桌布。」
  3. **陳建宏（企業負責人）**：「專屬 VIP 接駁車與休息室貼心，降落平穩得像走下樓梯，追求品質首選。」

---

### 5.8 常見問題手風琴（FAQ Section：`#faq`）

- 4 組獨立問答手風琴組件（`.faq-accordion` > `.faq-item`）：
  - Q1：跳傘與飛行傘有何不同？沒有經驗可以參加嗎？
  - Q2：參加飛行傘活動有體重或年齡限制嗎？（限 30-105kg，7-68 歲）
  - Q3：若遇天候不佳或風速不符標準如何處理？（無條件全額退費或免費延期）
  - Q4：4K 攝影檔案如何領取？需要自行攜帶 SD 卡嗎？（降落現場即時傳輸至手機）
- 互動效果：點擊問答按鈕切換 `.active`，圖示 `+` 旋轉 45 度轉為 `×`，答案面板平滑展開。

---

### 5.9 頁尾（Footer：`.footer`）

- **4 欄式資訊配置**：
  1. **品牌專欄**：飛行傘 Icon、品牌標語、營業時間（週一至週日 06:00 - 18:00）。
  2. **快速連結**：頁內所有錨點快速導覽。
  3. **熱門空域據點**：花蓮萬榮高空起飛場（海拔 680M）、南投埔里虎頭山全景基地（海拔 800M）、宜蘭外澳海景飛行場、屏東賽嘉義熱對流基地。
  4. **專屬預約專線**：免付費電話 `0800-888-007`、Line 官方帳號 `@peterpan_fly`、官方信箱、特許飛行基地許可證。
- **底列**：版權宣告與回到頂部錨點連結（`#home`）。

---

### 5.10 預約成功彈窗 Modal（`#bookingModal`）

- **觸發機制**：預約表單提交時呼叫 `handleBooking(event)`，阻止頁面跳轉並切換 `.modal-overlay.active`。
- **內容規格**：
  - 頂部金黃圓形勾選圖示（`✓`）。
  - 動態合成訂單摘要文字：包含旅客姓名、專案名稱、人數、預定日期與試算總金額。
  - 確認關閉按鈕，點擊後重置表單並關閉 Modal。

---

## 6. JavaScript 互動與計算邏輯規範

```javascript
// 1. 初始化預設預約日期為「明天」
const tomorrow = new Date();
tomorrow.setDate(tomorrow.getDate() + 1);
const dateStr = tomorrow.toISOString().split('T')[0];
dateInput.value = dateStr;
dateInput.min = dateStr;

// 2. 方案與費用動態試算公式
const basePrice = parseInt(packageSelect.value);
const count = parseInt(passengerCountSelect.value);
let addonTotalPerPerson = 0;
if (addonGopro.checked) addonTotalPerPerson += 800;
if (addonTransfer.checked) addonTotalPerPerson += 500;
if (addonCertificate.checked) addonTotalPerPerson += 300;

const totalAddons = addonTotalPerPerson * count;
const finalTotal = (basePrice * count) + totalAddons;

// 3. 方案卡片快速連動下拉選單
function selectPackage(name, price) {
  // 自動比對 options 並設置 selectedIndex，隨後重新執行 updateTotal()
}

// 4. FAQ 手風琴切換 (支援互斥收合)
button.addEventListener('click', () => {
  // 切換目前項目的 active 與 maxHeight，關閉其他展開項
});
```

---

## 7. 響應式斷點規格（RWD）

| 螢幕斷點 | 適應佈局調整 |
|---|---|
| **桌面版（> 992px）** | - Hero 採 `1.15fr : 0.85fr` 雙欄雙視覺。<br>- 飛行方案採 3 欄並列，推薦款卡片微放大。<br>- 預約試算卡採 `1.1fr : 0.9fr` 雙欄排版。<br>- 頁尾採 4 欄並列。 |
| **平板版（$\le$ 992px）** | - Hero 改為單欄直向排列，文案置中，下方銜接 HUD 儀表。<br>- 方案卡片轉為單欄居中排列（最大寬度 460px）。<br>- 安全保證區與預約試算區轉為垂直堆疊。<br>- 頁尾改為 2 欄 $\times$ 2 列。 |
| **手機版（$\le$ 768px）** | - 隱藏桌面導覽選單與頂部預約按鈕，啟用漢堡選單按鈕（`.mobile-toggle`）。<br>- 行動選單由頂部下拉展開（`transform: translateY(0)`），點擊項目後自動收合。<br>- 預約表單雙欄輸入框改為 100% 滿寬單欄排列。<br>- 頁尾轉為單欄全寬堆疊。 |

---

## 8. 無障礙（A11y）與可用性標準

1. **語意化標籤**：依循 HTML5 階層規範，包含 `<header>`、`<nav>`、`<section>`、`<footer>`，主副標題使用 `<h2>`、`<h3>`、`<h4>`。
2. **輔助標籤**：
   - 品牌連結具備 `aria-label="小飛俠飛行傘首頁"`。
   - 漢堡按鈕具備 `aria-label="切換選單"`。
3. **色彩對比度**：主品牌黃色（`#FFC700`）搭配深黑底（`#0A0E17`）文字或作為深色背景上的高亮標籤，均符合 WCAG AA 級高可讀性標準。
4. **鍵盤與表單友好**：所有輸入框均配置獨立 `<label>`，表單具備原生 HTML5 必填檢驗（`required`），輸入框聚焦時提供 `3px` 黃色光暈提示（`box-shadow: 0 0 0 3px rgba(255, 199, 0, 0.2)`）。

---

## 9. 後續維護與擴充指南

### 9.1 常見內容修改對應位置

| 需求項目 | 原始碼對應修改位置 |
|---|---|
| **調整專案價格或名稱** | 1. `#packages` 內各方案卡片之文字與價格。<br>2. `#packageName` `<select>` 中的 `value` 與 `data-name` 屬性。 |
| **調整加值服務收費** | 1. 表單內核取方塊的 `value` 數值。<br>2. `updateTotal()` 函式內的加總判斷邏輯。 |
| **更換品牌主配色** | 修改 CSS `:root` 中的 `--primary-yellow` 與 `--primary-yellow-hover`。 |
| **增減常見問題** | 直接於 `#faq .faq-accordion` 內新增或刪除 `.faq-item`，手風琴腳本會動態綁定。 |
| **更換基地據點或電話** | 修改 `footer.footer` 內的空域清單與客服聯絡資訊。 |

### 9.2 串接真實後端 API 建議

- 目前 `handleBooking(event)` 函式透過 `event.preventDefault()` 阻止了預設跳轉，並彈出前端預覽 Modal。
- 後續若需串接後端預約系統或金流，只需於 `handleBooking()` 內加入 `fetch('/api/v1/booking', { method: 'POST', body: JSON.stringify(data) })`，並於 Promise `resolve` 後觸發彈窗即可。

---

## 10. 驗收清單

- [x] 檔案儲存於 [WebSpec_11515122/specs/detail.md](file:///d:/Web/WebSpec_11515122/specs/detail.md)，格式完全符合 Markdown 規範。
- [x] 完整記錄來源檔案路徑與 SHA-256 雜湊值。
- [x] 詳細記錄品牌名稱、定位、色彩 Token、字型與版面網格規格。
- [x] 詳細記錄頁首、Hero、4 大優勢、3 大體驗專案、安全認證、預約試算、評價、FAQ 與頁尾規格。
- [x] 完整逆向表單金額動態計算與手風琴互動腳本邏輯。
- [x] 明確標註 RWD 斷點響應佈局與無障礙設計規範。
- [x] 提供維護修改位置對照表與後續 API 串接指南。
