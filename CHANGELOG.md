# Changelog

所有重要變更都記錄於此。格式參考 [Keep a Changelog](https://keepachangelog.com/zh-TW/1.0.0/)。

---

## [v2.3.0] — 2026-11-12

### 新增
- 新增 `requirements.txt`，相依套件改用 `pip install -r requirements.txt` 安裝。
- 新增 `CHANGELOG.md`。

### 修正
- 修正多頁正文每一頁都疊上所有頁文字的問題：空白信紙 PDF 的各頁共用同一個頁面物件，改成在新的空白頁上依序合併信紙與正文。
- 修正在 Python 3.12 無法執行的問題：內附的舊版 reportlab 使用已移除的 `imp` 模組，系統未安裝 PyPDF2 時也會出現 `ModuleNotFoundError`。

### 變更
- 將 `lal_modules/pdfpage.py` 從 PyPDF2 改為 pypdf（`PdfReader` / `PdfWriter`）。
- 改寫 README 為中文，補上系統需求、快速啟動、參數說明與目錄結構。
- 版本號更新為 v2.3.0。

### 移除
- 移除內附的 `dep/PyPDF2` 與 `dep/reportlab`。
- 移除 `set_pythonpath_win.bat`（Big5 編碼，且會用 `setx` 寫入使用者層級的 `PYTHONPATH`）與 `set_pythonpath_unix.sh`。
