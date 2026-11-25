# CONTEXT_MAP — FD AOI Monitor

一行一個現況＋路徑（細節看 notes/）

- 主程式：`index.html`（單檔，CRLF 換行；改檔要保留 CRLF）；版本 `APP_VER` 目前 v4.12 Kepler
- Beta 轉址：`beta/index.html` → 導回正式版
- 平台 icon（v4.11；v4.11.1 起標題列左上角也用 `icons/favicon.svg`）：`icons/`，設計與檔案清單見 `notes/2026-11-21_FD-平台icon.md`
- 版本類別 × 版本號連動（v4.11）：產線編輯換類別自動帶最新版本號＋版本號清單，見 `notes/2026-11-24_FD-版本類別版本號連動.md`
- 上線後 KPI（v4.12）：漏檢率單位 %、記錄填過檢率／漏檢率／生產 Model，稼動率只設目標（`KPI_DEF`／`KPI_REC`），見 `notes/2026-11-25_FD-KPI漏檢率與生產Model.md`
- 推上線：權杖存 Mac 鑰匙圈，`GIT_ASKPASS=~/.config/fd-aoi-monitor/askpass.sh git -c credential.helper= push`（腳本不在 repo）
