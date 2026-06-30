<div align="center">

![NYUST Thesis](https://i.postimg.cc/Zqm1hc5G/Books.png)

# 雲科論文LaTeX範本

_Unofficial LaTeX template for your master/doctor thesis at_  
_National Yunlin University of Science & Technology_

[![NYUST-Thesis-Template](https://img.shields.io/badge/NYUST_Thesis_Template-gray?logo=github)](https://github.com/DT227/NYUST-Thesis-LaTeX-Template)
[![License](https://img.shields.io/badge/License-CC_BY--SA_4.0-blue)](https://creativecommons.org/licenses/by-sa/4.0/ "創用CC 姓名標示-相同方式分享 4.0 國際 授權條款")
</div>

## 📑目錄

1. [**使用前注意事項**](#️使用前注意事項)  
2. [**修改項目**](#️修改項目)  
3. [**前置作業**](#前置作業建立local編譯環境)  
4. [**此範本使用方式**](#此範本使用方式)  
5. [**安全性**](#安全性)  
6. [**LaTeX相關使用教學**](#latex相關使用教學)  
7. [**授權**](#️授權)

## ⚠️使用前注意事項

此範本對照格式為雲科教務處/課教組/碩博士論文專區所公告之[**_學位論文格式規範 Thesis Format Sample【114年9月更新】_**](https://aax.yuntech.edu.tw/index.php/ql-ct/student-paper)

> [!CAUTION]
>
>1. 在使用前請檢查學校是否有更改要求之格式
>2. 此範本主要用來編輯 **論文內文**，其餘文件如:  
**_學位考試委員會審定書_**、**_研究生學位論文電子檔上傳同意書_** 等文件  
   請依照課教組公告之規範自行插入
>3. 裝訂規則、書背及封面顏色等細節規定請遵循學校、各系所訂定格式，本範本不包含相關設定
>4. 若有發現格式問題錯誤，歡迎提交 Issue 告知

## 🛠️修改項目

[![Chen-Xuan-Han - NYUST_Thesis](https://img.shields.io/badge/Chen--Xuan--Han-NYUST_Thesis-g?logo=github)](https://github.com/Chen-Xuan-Han/NYUST_Thesis)  
本範本修改自上述Repo，主要修改如下:

1. 整理引用的巨集(改變引用順序以及更換較舊的套件)
2. 更改原範本在格式上的小瑕疵來符合學校格式(如:Abstract要改全大寫ABSTRACT等)
3. 更改範本設定使其能在VS Code進行編譯
4. 刪除額外無用的檔案與資料夾

## 💡前置作業(建立Local編譯環境)

> [!TIP]  
> 此範本主要以VS Code作為編譯環境，若嫌建設環境麻煩可以使用[Overleaf](https://www.overleaf.com/)等免費線上平台取代(不過可能需要更改字型)

1. 下載並安裝[Visual Studio Code](https://code.visualstudio.com/)
2. 下載並安裝[TeX Live](https://www.tug.org/texlive/acquire-netinstall.html) (MikTex和TeX Live大同小異，擇一安裝即可)
    - Windows環境請下載`install-tl-windows.exe`
    - 其他就下載`install-tl-unx.tar.gz`
3. 在VS Code安裝LaTeX Workshop  
在延伸模組頁面搜尋[LaTeX Workshop by James Yu](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)，此模組會直接讓VS Code可以編譯LaTeX
4. VS Code環境設定  
可以展開下方區塊並複製內容到 `settings.json` 中
    <details>
    <summary><b>點擊展開檢視詳細 settings.json 設定</b></summary>

    ```json
    {   
        // 編譯LaTeX的工具設定
        "latex-workshop.latex.tools": [
            {
                "name": "xelatex",
                "command": "xelatex",
                "args":[
                    "-synctex=1",
                    "-interaction=nonstopmode",
                    "-file-line-error",
                    "%DOC%"]},
            {
                "name": "xelatex-with-shell-escape",
                "command": "xelatex",
                "args": [
                    "--shell-escape",
                    "-synctex=1",
                    "-interaction=nonstopmode",
                    "-file-line-error",
                    "%DOC%"]},
            {
                "name": "pdflatex",
                "command": "pdflatex",
                "args": [
                    "-synctex=1",
                    "-interaction=nonstopmode",
                    "-file-line-error",
                    "%DOC%"]},
            {
                "name": "pdflatex-with-shell-escape",
                "command": "pdflatex",
                "args": [
                    "--shell-escape",
                    "-synctex=1",
                    "-interaction=nonstopmode",
                    "-file-line-error",
                    "%DOC%"]},
            {
                "name": "latexmk",
                "command": "latexmk",
                "args": [
                    "-synctex=1",
                    "-interaction=nonstopmode",
                    "-file-line-error",
                    "-pdf",
                    "%DOC%"]},   
            {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"]},
            {
            "name": "makeindex",
            "command": "makeindex",
            "args": [
                "%DOCFILE%"]}],
        // 選擇LaTeX編譯工具的指令，以及工具的順序
        "latex-workshop.latex.recipes": [
            //　目前只使用xelatex和bibtex 
            {
                "name": "xelatex -> bibtex -> xelatex*2",
                "tools": [
                    "xelatex",
                    "bibtex",
                    "xelatex",
                    "xelatex"]},
            {
                "name": "xelatex",
                "tools": [
                    "xelatex"]}, 
            {
                "name": "xelatex with shell escape",
                "tools": [
                    "xelatex-with-shell-escape"]},
            {
                "name": "bibtex",
                "tools": [
                    "bibtex"]}],
        // 選擇pdf瀏覽器，可選browser/tab/external
        "latex-workshop.view.pdf.viewer": "tab",
        // 每次編譯前，刪除之前的output檔
        "latex-workshop.latex.clean.enableed": true,
        "latex-workshop.latex.clean.fileTypes": [
            "*.aux",
            "*.bbl",
            "*.blg",
            "*.idx",
            "*.ind",
            "*.lof",
            "*.lot",
            "*.out",
            "*.toc",
            "*.acn",
            "*.acr",
            "*.alg",
            "*.glg",
            "*.glo",
            "*.gls",
            "*.ist",
            "*.fls",
            "*.log",
            "*.fdb_latexmk"],
    }
    ```

    </details>

5. 下載此範本  
在此範本的GitHub頁面右上角Code的地方(綠色按鈕)，點選**Download Zip**選項下載此範本壓縮包，再將此壓縮檔解壓至編輯目錄下並以VS Code開啟此目錄即可
6. 安裝簡體中文補充字型包  
由於此範本有使用ctex巨集，此巨集預設會搜尋簡體中文字型。儘管論文中沒有使用任何簡體中文，但只要電腦沒有安裝就會報錯而無法編譯文件，大致解法如下
    - Windows環境
        - Win11: 設定→系統→選用功能→檢視或編輯選用功能的檢視功能按鈕→查看可用功能→搜尋中文(簡體)補充字型→勾選並新增即可
        - Win10: 設定→系統→選用功能→上方新增功能→搜尋中文(簡體)補充字型→勾選並新增即可
    - 其他環境則需要自行下載安裝相關字型
        - DengXian(等线)、FangSong(仿宋)、KaiTi(楷体)、SimHei(中易黑体)等簡中字體，具體需要哪些請查閱[ctex字體定義文件](https://zhuanlan.zhihu.com/p/538459335)
        - 或是直接安裝此範本fonts資料夾中zh-cn的字體
7. 到此前置作業基本上就完成了，可以開始論文的編輯嘞~~🎉

以上設定參考自[[1]](https://hackmd.io/@DextinChen/VSCode-LaTeX-setting)、[[2]](https://kuaz.info/posts/2023/01/latex-tutorial-part-ctex/)、[[3]](https://zhuanlan.zhihu.com/p/521256466)

## 📖此範本使用方式

### 🧾檔案結構

```cpp
NYUST-Thesis-LaTeX-Template
├─ backpages
│  ├─ appendix
│  │  └─ 附錄內容檔案
│  ├─ my_appendix.tex       //附錄
│  └─ nyust_backpages.tex
├─ chinese_trans.tex
├─ common_env.tex
├─ figures
│  └─ CH1~CH6的圖片資料夾
│     └─ 各章要插入的圖片檔案   //放置圖片
├─ fonts
│  └─ 各語系之字體
├─ frontpages
│  ├─ my_ackn.tex           //誌謝
│  ├─ my_cabstract.tex      //中文摘要
│  ├─ my_eabstract.tex      //英文摘要
│  ├─ my_names.tex          //個人資料(論文名稱等)
│  ├─ my_symbols.tex        //符號說明
│  └─ nyust_frontpages.tex
├─ my_bib.bib               //放置參考文獻
├─ my_nyust_thesis.pdf      //生成的論文PDF
├─ my_nyust_thesis.tex      //論文主結構
├─ nyust_report.cls
├─ README.md
├─ sections
│  └─ CH1~CH6的.tex檔案     //放置論文主內容
└─ watermark
   ├─ nyust_watermark.eps
   ├─ nyust_watermark.pdf
   └─ nyust_watermark.tex
```

在進行論文寫作時，主要是修改檔名為`my_XXXXXXX.XXX`這些文件的內容  
本tex之主結構檔為`my_nyust_thesis.tex`  
其中需要修改的文件放置於 **_frontpages_** 及 **_backpages_** 目錄中  
論文主內容請分章(Chapter)放置於 **_sections_** 目錄中  
references的bibtex檔請放置於目錄第一層之`my_bib.bib`

> [!TIP]
>
> ### ❓如何把參考文獻放進`my_bib.bib`
>
> 在 **Google Scholar** [網頁](https://scholar.google.com/) 或是 [Chrome插件](https://chromewebstore.google.com/detail/google-scholar-button/ldipcbpaocekfooobnbcddclnhejkcpn?hl=zh-TW) 搜尋你要引用的論文。點擊論文下方的 **引用(Cite)按鈕** (通常是一個引號圖示 ❞ )選擇 **BibTeX**。複製那段代碼，貼到你的`my_bib.bib`檔案裡。
>
> 此範本引用格式參照[IEEE Journals and Conferences](https://www.bibtex.com/s/bibliography-style-ieeetran-ieeetran/)，若有不同可依專業需求更換引用格式，詳細BibTex的格式(Format)與類型(Styles)可至[BibTex官網](https://www.bibtex.com/)查看

## 🔐安全性

如使用 **GitHub**、**GitLab**、**Bitbucket** 等公開的程式碼代管服務管理論文，請注意遠端儲存庫 (Remote Repository) 的存取權限，知識內容請設為私密，以避免防資料外洩等安全性問題。

## 🏫LaTeX相關使用教學

🔗[臺大數學LaTeX教學團隊YouTube頻道](https://www.youtube.com/@latex4703)  
🔗[《大家來學LaTeX》By 李果正老師](https://textw.github.io/LaTeX123/)  
🔗[LaTeX基本使用](https://mycollegenotebook.medium.com/laex-%E5%9F%BA%E6%9C%AC%E4%BD%BF%E7%94%A8%E7%AF%87-37f1986f4d4c)  
🔗[LaTeX數學符號指令](https://hackmd.io/@CynthiaChuang/Basic-LaTeX-Commands)  
🔗[LaTeX對表格表頭斜線分割](https://zhuanlan.zhihu.com/p/688814805)  
🔗[LaTeX插入圖片及多圖排版](https://andy123t.github.io/2020/09/22/LaTeX-Figure/)  
🔗[LaTeX+VSCode：代碼和PDF互相跳轉](https://blog.csdn.net/cz2011301070/article/details/105461416)

## ⚖️授權
  
本著作係採用[創用 CC 姓名標示-相同方式分享 4.0 國際 授權條款](https://creativecommons.org/licenses/by-sa/4.0/)授權

[![創用 CC 授權條款](https://licensebuttons.net/l/by-sa/4.0/88x31.png "創用 CC 授權條款")](https://creativecommons.org/licenses/by-sa/4.0/)
