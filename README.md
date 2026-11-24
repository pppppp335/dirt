# 竹南蛇窯｜動態數位博物館

以純 HTML、CSS 與原生 JavaScript 製作的響應式互動原型，無 npm 套件、建置流程或伺服器端依賴。可以直接在瀏覽器開啟 `index.html`，也可部署為 Render Static Site。

## 專案結構

```text
陶藝/
├── index.html     # 單頁資訊架構與各區塊
├── styles.css     # 色彩變數、工藝紋理、桌機與行動版樣式
├── app.js         # 語系、藝廊、預約試算與 localStorage 示範流程
└── README.md      # 啟動與部署說明
```

## 本機預覽

直接以瀏覽器開啟 `index.html` 即可。若想使用本機 HTTP 伺服器，在專案資料夾執行：

```bash
python -m http.server 8000
```

然後瀏覽 `http://localhost:8000`。此專案無需 `npm install`，也沒有 build 指令。

## GitHub 推送

先在 GitHub 建立空白 repository，於專案資料夾執行（將網址替換為自己的 repo）：

```bash
git init
git add index.html styles.css app.js README.md
git commit -m "Build Zhunan Snake Kiln digital museum prototype"
git branch -M main
git remote add origin https://github.com/<帳號>/<repository>.git
git push -u origin main
```

## Render 部署

1. 登入 Render，選 **New → Static Site**，連接 `pppppp335/dirt` repository。
2. Branch 選 `main`；Root Directory 填 `陶藝`；Build Command 留空；Publish Directory 填 `.`。
3. 按 **Create Static Site**。每次推送到 `main` 後，Render 會重新發布。
4. 網站使用單頁錨點（例如 `/#gallery`），沒有前端路由，無須新增 SPA rewrite 規則。若不設定 Root Directory，則將 Publish Directory 填 `陶藝`。

## 原型互動

- 繁中、English、日本語語系切換（核心導覽與主要標題）。
- 藝廊分類、作品數位履歷 Modal，以及作品放大與拖曳檢視。
- 團體導覽、假日參訪、三種課程的表單與價格試算；導覽要求至少提前三天預約。
- 模擬訂單、課程名額扣減、候補、末五碼回報及本機重設；資料保存在瀏覽器 `localStorage`。
- 行動版漢堡選單、電話與 Google 地圖快捷入口。

## 正式上線前替換

`app.js` 的帳號資料為示範資訊，頁面已標明不可實際匯款；`index.html` 中電話使用 `037-XXXXXX` 佔位。作品圖像目前是 CSS 陶器示意，正式版可替換為取得授權的實拍多角度影像。預約流程僅存在訪客自己的瀏覽器，不會傳送通知、跨裝置同步或由園方確認付款；正式 O2O 預約需連接後端資料庫、金流／匯款核帳及通知服務。外部 Google Fonts 需有網路才能載入，字體失效時會使用系統字型。
