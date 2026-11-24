# 約人出街 V1.0.0

## 開啟
將 `index.html` 放到支援 HTTPS 的靜態網站主機（例如 Firebase Hosting），或本機用簡單 HTTP server 開啟。瀏覽器直接以 `file://` 開啟時，Firebase 模組及定位可能受限制。

## Firebase 雲端同步設定
1. 在 Firebase Console 專案 `chan-b4286` 啟用 Authentication → Sign-in method → Anonymous。
2. 建立 Cloud Firestore database。
3. 建立 Storage bucket。
4. 將本資料夾的 `firestore.rules` 貼到 Firestore Rules；`storage.rules` 貼到 Storage Rules。
5. Authentication → Settings → Authorized domains 加入你的網站網域。
6. 使用 HTTPS 網址開啟網站，按「設定／雲端」→「連接／重新連接雲端」。

Firebase Web API key 是前端識別設定，不是管理員密碼；真正保護資料要靠 Authentication、Firestore Rules、Storage Rules 及 Firebase Console 權限。

## 功能及限制
- 香港時間：瀏覽器每秒更新，固定 Asia/Hong_Kong。
- 天氣：使用香港天文台公開 weather API（九日預報、即時天氣、警告摘要及分區溫度）。
- 定位：只在使用者按掣並同意瀏覽器權限後取得。
- WhatsApp：產生邀請文字並開啟 WhatsApp 分享／對話選擇；不能由普通網站自動發送到群組。
- 相片：連接 Firebase 後上載 Storage，貼文存 Firestore；未連接時僅暫存本機瀏覽器。
- 交通：九巴、城巴及港鐵查詢入口。使用者需提供官方站點／路線代號；API 跨域、格式或服務狀態可能令查詢失敗。V1.0.0 尚未提供全港站點搜尋器、港鐵全線自動索引及輕鐵 ETA 完整整合。
- 天氣及交通屬參考資料，出行前以官方公告／營辦商資料為準。

## 發佈網站
建議 Firebase Hosting：安裝 Firebase CLI、登入、在此資料夾執行 `firebase init hosting`，public directory 選目前資料夾，然後 `firebase deploy`。請勿把管理員私密金鑰放入前端。
