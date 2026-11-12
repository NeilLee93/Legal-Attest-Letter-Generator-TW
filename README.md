# Legal Attest Letter Generator - Taiwan

台灣郵局存證信函產生器：把純文字的信函正文套進郵局存證信函格式，輸出成 PDF。給需要自行繕打存證信函的人使用。

![](./img/sample.png)

---

## 功能特色

- **輸出整齊**：正文逐格排入郵局存證信函用紙，一格一字。
- **多位當事人**：寄件人、收件人、副本收件人的姓名與地址都可以指定多組。
- **保留縮排**：在純文字編輯器排好縮排，輸出時照樣反映，內容不擁擠。
- **離線免費**：全程在本機執行，不上傳任何資料。
- **圖形介面**：除命令列外，另提供 `tw-lal-generator-gui.py`（tkinter）。

---

## 系統需求

| 項目 | 需求 |
|---|---|
| 作業系統 | Windows / macOS / Linux |
| Python | 3.8 以上（已在 3.12 測試） |
| 外部套件 | `pypdf`、`reportlab`（見 `requirements.txt`） |

---

## 快速啟動

```bash
pip install -r requirements.txt
python tw-lal-generator.py 正文.txt --senderName 王小明 --senderAddr 台北市中正區某路1號 --receiverName 李大華 --receiverAddr 新北市板橋區某街2號 --outputFileName out.pdf
```

圖形介面：

```bash
python tw-lal-generator-gui.py
```

---

## 使用方法

| 參數 | 說明 |
|---|---|
| `article_file` | 存證信函正文的純文字檔路徑（UTF-8） |
| `--senderName` / `--senderAddr` | 寄件人姓名／詳細地址，可重複指定多組 |
| `--receiverName` / `--receiverAddr` | 收件人姓名／詳細地址，可重複指定多組 |
| `--ccName` / `--ccAddr` | 副本收件人姓名／詳細地址，可重複指定多組 |
| `--outputFileName` | 輸出的 PDF 檔名，預設 `output.pdf` |
| `--help` | 顯示使用說明 |

更詳細的操作說明見原專案 [Wiki](https://github.com/csterryliu/Legal-Attest-Letter-Generator-TW/wiki/)。

---

## 目錄結構

```
Legal-Attest-Letter-Generator-TW/
├── tw-lal-generator.py       # 命令列進入點
├── tw-lal-generator-gui.py   # 圖形介面進入點
├── requirements.txt          # pip 相依套件
├── lal_modules/
│   ├── core.py               # 產生正文、合併信紙的主流程
│   ├── pdfpage.py            # PDF 頁面挑選與合併（pypdf）
│   ├── pdfpainter.py         # 在 PDF 上寫字（reportlab）
│   ├── gui.py                # tkinter 介面
│   └── constants.py          # 版本號、版面座標等常數
├── res/                      # 存證信函用紙範本、全字庫正楷體字型
└── img/                      # README / Wiki 用圖
```

---

## 注意事項

- 不再內附（vendor）舊版 PyPDF2 與 reportlab，也移除了 `set_pythonpath_*.bat/.sh`；請改用 `pip install -r requirements.txt`。舊版曾用 `setx` 寫入使用者層級的 `PYTHONPATH`，如果你跑過舊的 `set_pythonpath_win.bat`，建議到「環境變數」把它刪掉，以免影響其他 Python 專案。
- 正文檔請存成 UTF-8 編碼。

---

## 相依套件 / 技術棧

| 套件 | 用途 |
|---|---|
| [pypdf](https://github.com/py-pdf/pypdf) | 讀取信紙範本、合併頁面 |
| [reportlab](https://www.reportlab.com/) | 產生正文與當事人資料的 PDF 圖層 |
| [郵局存證信函用紙](http://www.post.gov.tw/post/internet/Download/index.jsp?ID=220301) | 中華郵政提供的信函範本 |
| [全字庫正楷體](http://data.gov.tw/node/5961) | 國家發展委員會提供的繁體中文字型 |

授權：MIT
