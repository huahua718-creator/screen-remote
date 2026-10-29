# 🚀 班務大屏傳屏助手 (Screen Pusher)

免費、免安裝 App 的跨平台大屏無線互動系統！支援網址推送、多圖/PDF 翻頁標註、實物鏡頭投影、P2P 影片快傳與無線麥克風。

---

## ⚡ 一鍵免費部署屬於您的專屬版本

點擊下方按鈕，即可將本專案免費複製並託管至您的 Vercel 或 Netlify 帳號中（完全免費且內建 HTTPS）：

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/huahua718-creator/screen-remote)
[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/huahua718-creator/screen-remote)

---

## 🛠️ 3 分鐘設定專屬 Firebase（享無限流量）

部署完成後，若想擁有完全獨立、不與他人共用的獨立資料庫，請依以下步驟設定：

1. 前往 [Firebase Console](https://console.firebase.google.com/) 免費建立一個新專案。
2. 進入專案，點擊新增 **Web 應用程式**。
3. 在左側選單點擊 **Build ➔ Realtime Database**，點選「建立資料庫」（地區選擇 `asia-southeast1`）。
4. 在 Realtime Database 的 **Rules (規則)** 頁籤中，將規則修改為允許讀寫：
   ```json
   {
     "rules": {
       ".read": true,
       ".write": true
     }
   }