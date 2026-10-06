# NOVA 前導體驗課收單頁

NT$100：三堂 AI 前導課＋NOVA 顧問一對一諮詢。純靜態單檔，走 GitHub Pages，可整頁 iframe 嵌入 Kolable。

## 頁面結構

| 區塊 | id | 內容 |
|---|---|---|
| Hero | `hero` | 「花 100 元，先上船試飛」＋登艦證卡 |
| 第 0 關 | `play` | 「猜下一個字」小遊戲，3 題，玩完解鎖徽章 |
| 任務地圖 | `map` | 三堂課＝三關，每關列出下課帶走的東西 |
| 戰利品 | `loot` | 第 2 堂示範成品（兩種風格切換） |
| 魔王關 | `boss` | 顧問一對一諮詢，五領域羅盤 |
| 解鎖 | `unlock` | NOVA 專案班五領域、進度條 |
| 價格 | `pricing` | 票根式價格卡 |
| FAQ／結尾 | `faq` `final` | |

## 掛購物車按鈕

頁上有 6 個 `.cta-slot`，掛進去之後預設按鈕會自動隱藏：

| `data-cta` | 位置 |
|---|---|
| `nav` | 頂部導覽列 |
| `hero-primary` | 首屏主按鈕 |
| `game` | 第 0 關通關徽章下 |
| `pricing` | 價格卡 |
| `final` | 結尾 |
| `dock` | 手機底部固定列（嵌入 iframe 時自動隱藏） |

兩種掛法擇一：

```js
// A. 用 JS 掛
NovaTrial.mountCTA('pricing', document.querySelector('#myCartBtn'));
NovaTrial.slots(); // 列出所有落點
```

```html
<!-- B. 直接改 HTML：把 .cta-fallback 那顆換掉 -->
<div class="cta-slot" data-cta="pricing">
  <a class="btn btn--primary" href="（購物車連結）">立即報名 NT$100</a>
</div>
```

沿用 `btn btn--primary` 這個 class，就是頁面的橘色按鈕樣式。

## 埋點

共用 `assets/analytics.js`（四站同一份）。這頁另外送：

| 事件 | 參數 |
|---|---|
| `trial_game_answer` | `round`, `correct` |
| `trial_game_complete` | `score` |
| `trial_demo_switch` | `style` (a/b) |
| `trial_cta_click` | `slot`, `filled`（是否已掛真按鈕） |
