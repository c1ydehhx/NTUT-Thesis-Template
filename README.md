🎓 NTUT-Thesis-Template
基於 XeLaTeX 的國立臺北科技大學（北科大）碩博士論文模板。

本專案旨在提供北科大研究生一個符合規範、開箱即用的 LaTeX 撰寫環境，讓你專注於研究內容，而非排版細節。

🚀 快速入門
1. 環境安裝 (`TeX Live`)
編譯 `.tex` 檔案前，請根據您的作業系統安裝對應的發行版本：

* macOS:

```
brew install texlive
```

* Ubuntu/Linux:

```
sudo apt-get update && sudo apt-get install texlive-full
```

* Windows:

1. 下載並安裝 [TeX Live 官方安裝包](https://www.tug.org/texlive/)。
2. 安裝 [Strawberry Perl for Windows](https://strawberryperl.com/)（部分 LaTeX 套件需求）。
3. 設定環境變數：
 ```
  C:\Strawberry\c\bin
  C:\Strawberry\perl\site\bin
  C:\Strawberry\perl\bin
 ```
   
5. 驗證安裝：開啟終端機輸入 `xelatex --version`。

⚙️ 專案設定與自定義
在開始撰寫內容前，請先完成以下參數設定：

📝 個人資訊設定
編輯 `ntut-labels.tex`，填入論文的基本資料：
* 系所名稱
* 論文中英文名稱
* 學位（碩士/博士）
* 研究生與指導教授姓名
* 學年度 學期

🖋️ 字體與內容微調

* 字體設定：預設使用標楷體 (`kaiu.ttf`)。若在 macOS/Linux 環境找不到字體，請於 `main.tex` 修改 CJK 字體路徑。
* 摘要更新：進入 `page/abstract.tex` 與 `page/abstract-en.tex` 更新論文頁數與關鍵字。
* 口委審定書：將掃描後的 PDF 檔命名為 `signpage.pdf` 並放至 `./static-page` 資料夾。

🛠️ 編譯指南

**方法一：VSCode 整合環境（推薦）**

搭配 `LaTeX Workshop` 擴展，可實現「存檔即自動編譯」。

安裝套件： [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)

配置設定：開啟 `settings.json` 並貼入本專案提供的 JSON 配置（包含 `xelatex -> bibtex -> xelatex*2` 的 `Recipe`）。

* 調整前
```
"latex-workshop.latex.recipes": [
    {
        "name": "latexmk",
        "tools": [
            "latexmk"
        ]
    },
    {
        "name": "latexmk (latexmkrc)",
        "tools": [
            "latexmk_rconly"
        ]
    },
    {
        "name": "latexmk (lualatex)",
        "tools": [
            "lualatexmk"
        ]
    },
    {
        "name": "latexmk (xelatex)",
        "tools": [
            "xelatexmk"
        ]
    }
]
```

* 調整後
```
"latex-workshop.latex.recipes": [
    {
        "name": "latexmk (xelatex)",
        "tools": [
            "xelatexmk"
        ]
    },
    {
        "name": "latexmk",
        "tools": [
            "latexmk"
        ]
    },
    {
        "name": "latexmk (latexmkrc)",
        "tools": [
            "latexmk_rconly"
        ]
    },
    {
        "name": "latexmk (lualatex)",
        "tools": [
            "lualatexmk"
        ]
    }
]
```

執行編譯：

* Win/Linux: `Ctrl + Alt + B`
* macOS: `Cmd + Option + B`

**方法二：指令列編譯**

如果您偏好使用終端機，可以使用以下方式：

* Make 指令：`make` (自動執行完整流程)
* 自動化腳本：`./build.sh`
* 原始指令：

```
xelatex main && bibtex main && xelatex main && xelatex main
```

📂 檔案架構說明
本範例採用模組化設計，結構清晰易懂：

```
├── main.tex                 # 主程式入口
├── ntut-reports.cls         # 北科大論文格式定義規範
├── ntut-labels.tex          # 論文變數設定 (標題、姓名等)
├── reference.bib            # 參考文獻資料庫
├── chapter/                 # 論文主體
│   ├── chapter1-intro.tex   # 第一章：緒論
│   └── chapter2-related.tex # 第二章：相關研究
├── page/                    # 前言與後置頁面
│   ├── abstract.tex         # 中文摘要
│   ├── abstract-en.tex      # 英文摘要
│   ├── thanks.tex           # 致謝
│   └── table-of-content.tex # 目錄生成
└── static-page/             # 靜態 PDF 存放 (審定書等)
```

❓ 常見問題 (FAQ)

**Q1: 為什麼編譯後看不到中文字？**

請確保使用 XeLaTeX 作為編譯器，並檢查 `main.tex` 中的 `\setCJKmainfont` 指向的字體檔是否存在於系統中。

**Q2: VSCode 報錯「找不到 xelatex」？**

通常是環境變數（PATH）未設定，請重啟 VSCode 或確認 TeX Live 的 bin 資料夾已加入系統路徑。

🤝 特別感謝

本專案的格式規範與基礎，特別感謝以下教授的指導與協助：

* [孫勤昱 教授](https://academic.ntut.edu.tw/1781/1556/2283/)（國立臺北科技大學 資訊工程系）
* [陳昱圻 教授](https://academic.ntut.edu.tw/1781/1556/2281/)（國立臺北科技大學 資訊工程系）

⭐ 喜歡這個模版嗎？歡迎點擊右上角 Star 給予支持！
