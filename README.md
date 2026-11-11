# 鳥嶼國小教務組網站

| 網址 | 內容 |
|---|---|
| `/` | 教務組入口 |
| `/timetable/` | 課表查詢（全校／班級／個人週課表，含後台） |
| `/textbook/` | 教科書選用系統 |
| `/curriculum/` | 校訂課程手冊（PDF 線上翻頁） |

資料庫：Firebase 專案 `textbook-cf439`（Firestore）。
課表資料在 `tt_days`、`tt_meta`；教科書資料在 `artifacts/...`，互不影響。

## 後台密碼
課表後台與教科書「管理員解鎖」共用同一組密碼。
密碼存在 Firebase Authentication 的使用者 `jiaowu@textbook-cf439.web.app`，不寫在程式碼裡。
要改密碼：Firebase 主控台 → Authentication → Users → 該使用者 → 重設密碼（或刪除後用新密碼重建）。

## 安全規則
`firestore.rules` 是 Firestore 的安全規則。修改後要貼到
Firebase 主控台 → Firestore Database → 規則 → 發布，才會生效（推送到 GitHub 不會自動套用）。

## 新學期
課表後台 → 設定：修改學期名稱、W1 日期、國定假日；換課表時新增一個「基本課表版本」。
