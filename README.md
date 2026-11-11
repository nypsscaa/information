# 鳥嶼國小教務組網站

| 網址 | 內容 |
|---|---|
| `/` | 教務組入口 |
| `/timetable/` | 課表查詢（全校／班級／個人週課表，含後台） |
| `/textbook/` | 教科書選用系統 |
| `/curriculum/` | 校訂課程手冊（PDF 線上翻頁） |
| `/exam/` | 定期評量：審題分配表、期中／期末監考表 |

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

## 首頁公告（近期重要行事、填報專區）
在課表後台的「公告管理」分頁編輯，儲存後首頁立即更新，不需要改程式。
`notices-seed.js` 只是第一次使用時的預設資料（115 學年度第一學期行事曆）。

## 定期評量頁
審題分配表與監考表的資料寫在 `exam/index.html` 最上方（REVIEW、EXAMS），每學期更新一次。
