# 🖥️ 班務大屏傳屏助手 (Screen Remote)

> 免費、免安裝 App、免驅動的跨平台大屏無線互動與傳屏系統！  
> 支援 **雙向 P2P 檔案傳輸**、**網址/YouTube 推送**、**多圖/PDF 簡報翻頁**、**手機無線實物鏡頭** 與 **雙向同步白板標註**。

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/huahua718-creator/screen-remote)
[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/huahua718-creator/screen-remote)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## ✨ 核心亮點

* 📱 **免裝 App、掃碼即用**：任何手機（iOS / Android）或平板開啟相機掃描大屏 QR Code 即可連線。
* 📺 **全平台大屏相容**：教室觸控一體機、智慧電視、會議大屏、Windows / Mac / Linux 電腦瀏覽器皆可作為接收端。
* ⚡ **WebRTC P2P 高速直連**：影音串流與檔案傳輸採用點對點端到端加密，無第三方伺服器儲存，不佔用雲端空間與流量。
* 🔒 **隱私安全與零殘留**：傳輸檔案僅暫存於接收端裝置的執行記憶體（RAM），重整或關閉網頁即自動釋放，無硬碟垃圾殘留。

---

## 🚀 主要功能介紹

### 1. 📁 雙向 P2P 檔案傳輸中心（支援複數多檔）
* **雙向互傳**：支援「手機傳送到大屏」與「大屏傳送到手機」。
* **多檔案批次傳輸**：可一次選取多個檔案（支援照片、影片、PDF、Word/Excel、簡報、ZIP 壓縮檔等任意格式）。
* **大屏端專屬介面**：
  * 左下角常駐半透明毛玻璃「📁 檔案傳輸中心」懸浮按鈕。
  * 收到手機檔案時自動彈出 **即時 Toast 通知橫幅** 與紅點未讀計數。
  * 支援單檔個別下載與「📦 全部下載」功能。
* **傳輸限制與安全機制**：
  * 採用 WebRTC DataChannel 分塊發送與背壓流量控制（Backpressure）。
  * 建議單一檔案小於 **100 MB**，單次多檔總和建議在 **300 MB** 內，避免行動裝置瀏覽器記憶體過載。

### 2. 🌐 網址與雲端資源快速推送
* 支援輸入任意外部網址、線上測驗卷或 YouTube 影片連結，大屏即時全螢幕呈現。
* 內建網址自訂標題與推送歷史下拉選單，方便重複開啟教學資源。

### 3. 🖼️ 多圖與 PDF 課件投影（支援同步翻頁）
* 支援一次選取多張學生作業照片或多頁 PDF 講義上傳。
* 手機遙控端與大屏端具備同步翻頁控制鈕（上一頁 / 下一頁 / 頁碼指示）。
* 支援大屏觸控雙指縮放（Zoom）與拖曳移動（Pan），方便細緻檢視作業細節。

### 4. 🎥 手機實物相機實時投影
* 將手機鏡頭秒變「無線實物投影機」，作業、實驗、實體教材即時全螢幕呈現。
* 支援前後鏡頭快速切換與即時拍照推送到大屏白板功能。

### 5. ✏️ 雙向同步手繪白板標註
* 手機與大屏具備雙向筆跡同步，手機在螢幕上圈點，大屏即時繪出；大屏觸控書寫，手機即時同步。
* 提供多種筆觸顏色、橡皮擦與一鍵清除筆跡。
* 可直接疊加在相片、PDF 或網頁畫面上進行即時批註與講評。

### 6. ⏹️ 遠端一鍵結束返回待機
* 手機端設有「⏹️ 結束大屏投放」按鈕，隨時可讓大屏優雅返回待機 QR Code 畫面。

---

## 🛠️ 3 分鐘設定專屬 Firebase 資料庫（模組化配置）

本專案採用開源模組化架構，將 Firebase 設定檔獨立於 `firebase-config.js`，部署至 Vercel 或 Netlify 後，只需替換該檔案即可擁有完全私有、不與他人共用的即時信令通道：

1. 前往 [Firebase Console](https://console.firebase.google.com/) 免費建立新專案。
2. 進入專案，點擊新增 **Web 應用程式**（`</>` 圖示），並複製 Firebase SDK 設定物件。
3. 在左側選單點擊 **Build ➔ Realtime Database**，點擊「建立資料庫」（地區建議選擇 `asia-southeast1`）。
4. 在 Realtime Database 的 **Rules (規則)** 頁籤中，將規則修改為允許讀寫並發布：
   ```json
   {
     "rules": {
       ".read": true,
       ".write": true
     }
   }
   ```
5. 打開專案目錄下的 `firebase-config.js`，將內容替換為您的金鑰資訊：
   ```javascript
   // firebase-config.js
   export const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
     databaseURL: "https://YOUR_PROJECT_ID-default-rtdb.asia-southeast1.firebasedatabase.app",
     projectId: "YOUR_PROJECT_ID"
   };
   ```

---

## 📂 專案檔案結構

```text
screen-remote/
├── index.html            # 角色導航首頁 (可選擇開啟大屏端或手機端)
├── screen.html           # 大屏多功能接收端 (白板、投屏、檔案中心)
├── mobile.html           # 手機遙控端 (網址、媒體鏡頭、標註、檔案傳輸)
├── firebase-config.js    # 獨立 Firebase 金鑰設定檔 (開源模組化)
└── README.md             # 專案詳細說明文件
```

---

## 💡 使用小訣竅

1. **網路需求**：大屏端與手機端無需在同一個區域網路（區網）或 Wi-Fi 下，只要各自能連上網際網路，透過輸入相同的 6 位數 PIN 碼即可自動建立 P2P 直連。
2. **檔案下載**：檔案傳輸採用瀏覽器臨時記憶體（Blob）機制，收到檔案後請記得點擊「下載」保存至本機硬碟。關閉或重新整理網頁後暫存會自動清空，保護裝置隱私。

---

## 📄 授權條款

本專案採用 [MIT License](LICENSE) 授權開放使用，歡迎自由修改、客製化或部署於各級學校、教學機構與會議場地。
