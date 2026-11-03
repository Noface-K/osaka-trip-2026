# 關西漫遊 · 大阪獨旅 2026

一個無框架、免編譯的手機優先旅遊網站。資料根據「11/4-11/13大阪獨旅」Google 試算表，包含 7 張可自由選擇的行程卡、30 間餐廳、967 筆菜單明細，另有 Open-Meteo 未來 12 小時天氣與 Apple／Google 地圖導航。

## GitHub Pages 上線

1. 在 GitHub 建立 public repository（例如 `osaka-trip-2026`）。
2. 將這個資料夾內全部檔案（包括 `assets/`、`index.html` 和 `.nojekyll`）放進儲存庫根目錄。
3. Settings → Pages → Build and deployment，選 `Deploy from a branch`、`main`、`/(root)` 並儲存。
4. Pages 網址通常是 `https://<帳號>.github.io/<儲存庫名稱>/`，待 GitHub 顯示部署完成後確認。

## 同步試算表

- 網站預設先讀 `assets/snapshot.json` 作為離線保底資料。
- 再嘗試 Google Sheets 的 Google Visualization Query JSONP 讀取原始試算表的「工作表2」（行程）、「工作表3」（餐廳）及「菜單明細」。
- 原試算表必須被授予能匿名讀取的權限，否則網站會保留快照、不會顯示錯誤資料。
- **注意**：直接把原試算表設為「知道連結者可查看」，可能連其他分頁也會對外可讀。若不想公開「工作表1」，應另建一份只包含公開資料的鏡像試算表，再修改 `assets/app.js` 的 `SHEET_ID`。
- 公開檢視／發布格式與瀏覽器政策可能更改；可在網站「工具」頁看同步狀態。如果即時讀取失敗，仍可以離線快照使用。
- 資料來源不應包含不願公開的個人資訊。

## 天氣

Open-Meteo 公開 API 取得大阪、京都、奈良、神戶、天橋立逐時預報。無需密鑰，需網路連線，遵守 API 非商業免費使用條款。離線時清楚標示快取或未能更新。

## 本機預覽

在本目錄執行 `python -m http.server 8000`，瀏覽 `http://localhost:8000/`。不使用前端套件，純 HTML + CSS + JavaScript。

## 技術備註

- Apple 地圖：https://maps.apple.com/?daddr=...&dirflg=r
- Google Maps：https://www.google.com/maps/dir/?api=1&destination=...&travelmode=transit
- 不蒐集定位，也不需要使用者登入。
- 旅遊資料的確切更新時間、營業時間與預約資訊仍應以店家公告為準。
