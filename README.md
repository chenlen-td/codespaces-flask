# Alan 個人作品集

以 Flask 建置的個人介紹與作品集網站，包含個人簡介、技能、價值觀與聯絡資訊。頁面使用 Jinja 範本呈現，並由 CSS 和靜態圖片提供視覺樣式。

GitHub 儲存庫：[chenlen-td/codespaces-flask](https://github.com/chenlen-td/codespaces-flask)

## 功能

- 單頁式個人介紹與導覽連結
- 關於我、技能專長及個人價值觀區塊
- 個人頭像與圖片載入失敗時的替代圖片
- Flask 提供頁面路由，使用 Jinja 載入 HTML 範本

## 技術

- Python 3.8 或更新版本
- Flask 2.3.2
- Werkzeug 2.3.3
- HTML、CSS、Jinja

## 專案結構

```text
.
├── app.py                       # Flask 應用程式與首頁路由
├── requirements.txt             # Python 套件版本
├── .devcontainer/
│   └── devcontainer.json        # Codespaces 環境與埠轉送設定
├── static/
│   ├── main.css                 # 網站樣式
│   ├── profile-photo.jpg        # 個人頭像
│   └── Octocat.png              # 頭像載入失敗時的替代圖片
└── templates/
	└── index.html               # 個人介紹頁面
```

## 本機執行

先確認已安裝 Python 3.8 或更新版本，接著在專案根目錄建立並啟用虛擬環境：

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Windows PowerShell 的啟用指令：

```powershell
.venv\Scripts\Activate.ps1
```

安裝相依套件並啟動開發伺服器：

```bash
python -m pip install -r requirements.txt
flask --app app run --debug
```

開啟終端機顯示的本機網址，預設為 <http://127.0.0.1:5000/>。停止伺服器請在終端機按 `Ctrl+C`。

## GitHub Codespaces

此專案的 `.devcontainer/devcontainer.json` 會安裝 `requirements.txt` 中的套件、啟動 Flask，並轉送 `5000` 埠。Codespaces 啟動或重新連線後，若伺服器沒有自動執行，可在終端機手動啟動：

```bash
flask --app app run --debug --host=0.0.0.0 --port=5000
```

在 VS Code 的「連接埠」面板找到 `5000`，再使用該列的轉送網址開啟網站。Private 埠需要 GitHub 登入；若 VS Code 內嵌的簡易瀏覽器無法載入，請改用已登入 GitHub 的外部瀏覽器。Codespaces 停止或 Flask 程序結束時，網站就無法連線。

## 部署注意事項

GitHub 儲存庫只保存原始碼，不會自動執行或部署網站。`flask --debug run` 僅供開發使用，不應用於正式環境；正式部署前，請改用正式的 WSGI 伺服器並依照託管平台設定啟動程序。不要在公開環境啟用 Flask Debugger。
