# 𓃥 白六機械手訊息傳遞 (White6 Robotic Arm Message Conveyor)

一個基於 **Three.js** 打造的高效能 3D 機械手臂動態文字視覺化與動態訊息輪播系統。機械手臂會自動隨機從托盤夾取字盒，並透過逆運動學 (IK) 與輸送帶動態平移配合，將字盒精準排列在輸送帶上，實現極具科技感的訊息展示與傳遞。

🔗 **線上實時展示：** [https://kuochili-ops.github.io/Robotic-arm-message/](https://kuochili-ops.github.io/Robotic-arm-message/)

---

## ✨ 核心特色 (Key Features)

- **🤖 3-DOF 逆運動學與動態旋轉夾爪 (3D Inverse Kinematics & Wrist Yaw Alignment)**
  - 自動計算底座、肩部與肘部的俯仰角度，確保末端夾爪精準到達目標位置。
  - **夾爪角度自適應旋轉**：從兩側托盤抓取字盒時，手指會自動轉動貼合字盒側面，並在放回輸送帶時自動轉正。
  - **雙階段下落放盒**：機械手臂會先將字盒平移至輸送帶正上方（高處懸停），再垂直下降並開夾鬆開，讓字盒自然落入指定位置。

- **🚚 輸送帶動態長句運鏡系統 (Dynamic Conveyor Positioning)**
  - 當文字較長時，輸送帶會主動往前或往後捲動（滾動 `beltTexture` 並同步帶動已放置字盒），將遠端位置拉近至手臂最佳工作範圍內，解決手臂伸展極限問題。

- **📱 超高清大型 UI 與全平台響應式設計 (RWD & Mobile Responsive)**
  - 專為手機直向與各種螢幕尺寸優化，面板具備最大高度限制 (`70vh~75vh`) 與內部滾動機制，絕不被行動裝置導覽列遮擋。
  - 點擊面板外部區域可自動收合設定介面，提供乾淨純粹的 3D 視覺體驗。

- **🎨 豐富的個人化客製選項 (Customization Options)**
  - **多行訊息輪播**：支援輸入多行文字，排版完成展現 1 秒後自動由輸送帶傳送出去，進入下一行。
  - **中文字型選單**：支援黑體 (Noto Sans)、明體 (Noto Serif) 及行書 (Zhi Mang Xing) 等多種字型。
  - **動態顏色選擇器**：自由設定字盒表面的文字顏色，字體大小經比例最大化，貼近盒面邊緣。

- **🔗 專屬網址訊息分享 (URL Parameter Sharing)**
  - 提供內建的 URL 產生器，可將多行文字、字型及顏色設定編碼至 URL 參數中。
  - 面板內提供**實體 URL 輸入框與一鍵複製按鈕**，克服行動裝置（如 iOS Safari）剪貼簿限制，輕鬆分享專屬文字動態。

- **🎥 一鍵自動錄影下載 (Automated Canvas Recording)**
  - 整合 `MediaRecorder` API，點擊開始錄影後會自動從第一行重新排版，並在最後一行播放展示結束後**自動停止錄影並下載 `.webm` 影片檔**。

---

## 🛠️ 技術架構 (Tech Stack)

- **三維繪圖庫**：[Three.js (r128)](https://threejs.org/)
- **鏡頭控制**：`OrbitControls.js`
- **字體渲染**：HTML5 Canvas 2D 轉動態 `THREE.CanvasTexture` 貼圖
- **逆運動學**：解析幾何 3-DOF 垂直 IK 演算法
- **畫面擷取與錄影**：`HTMLCanvasElement.captureStream()` + `MediaRecorder`

---

## 🔗 URL 參數說明 (URL Parameters)

你可以直接在網址後方帶入參數，快速開啟自訂的訊息內容與視覺風格：

| 參數名稱 | 說明 | 範例 |
| :--- | :--- | :--- |
| `msg` | 多行訊息內容 (以換行分隔 `\n`) | `msg=%E6%88%91%E6%98%AF%E7%99%BD%E5%85%AD` |
| `font` | 選用的中文字型 CSS 名稱 | `font='Noto Sans TC', sans-serif` |
| `color` | 十六進位文字顏色值 | `color=%23111111` |

**範例網址：**
```text
[https://kuochili-ops.github.io/Robotic-arm-message/?msg=我是白六%0A機械手臂排字&font='Noto%20Sans%20TC',%20sans-serif&color=%23111111](https://kuochili-ops.github.io/Robotic-arm-message/?msg=我是白六%0A機械手臂排字&font='Noto%20Sans%20TC',%20sans-serif&color=%23111111)
