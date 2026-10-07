# nova-trial-web — NOVA 前導體驗課收單頁

一頁式 LP：NT$100 = 三堂前導課（通識／實戰／進階）＋ 一次 NOVA 顧問一對一諮詢，導向 NOVA 12 週專案班。

## 正本在哪
- 頁面：`index.html` 單檔（純靜態，沒有 build、沒有 CMS）。
- 視覺 token 照抄 `../nova-web/index.html` 的 `:root`（深底 `#08070a`、主色 `#ff8a32`、Chakra Petch＋Noto Sans TC）。
- 課程內容的正本是 `../前導課程教材`（repo `ai-precourse-materials`）。頁上的頓悟句、工具要求都從那份 README 抄來，**教材改了這頁要跟著改**。
- ⚠️ 時數是 Cindy 2026-10-07 指定的「每堂 60 分、共 180 分」，**跟教材的 68／90／90 不同，不要改回教材數字**。
- `demo/style-a.html`、`demo/style-b.html` 是從教材 `第2堂_實戰課/成品示範_*.html` 複製的，虛構品牌「植燃 VERDA」。
- `assets/analytics.js` 是四站共用那份（GA4 `G-Y3V2G0L41K`），不要在這裡改，改要四站一起改。

## 部署
- repo：https://github.com/cindyhsu-png/nova-trial-web（public，main 分支根目錄）
- Pages：https://cindyhsu-png.github.io/nova-trial-web/ → 之後 iframe 嵌進 Kolable（比照 nova-web / ai-xplore-web，**還沒嵌**）
- 本機預覽：`.claude/launch.json` 的 `nova-trial`，伺服器讀的是 scratchpad 副本（預覽伺服器讀不到 Desktop），改完要 rsync 過去。

## 收單／CTA
- 這頁**不碰金流**。購物車按鈕由 Cindy 掛進 `.cta-slot`，作法見 README。
- 6 個落點：`nav`／`hero-primary`／`game`／`pricing`／`final`／`dock`（手機底部列）。

## 踩過的坑／注意
- 第 0 關的機率是**教學示意**，頁上已標註，不要拿掉那行字。
- 第 2、3 堂要 Claude 付費方案，頁上講明「費用另計」；不要寫具體價格（會變）。
- iframe 內被嵌入時 `html.embedded` 會關掉手機底部列（fixed 在 iframe 裡會黏錯位置）。
