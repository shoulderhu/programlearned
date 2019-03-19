## gitbook 簡易使用方法
#### 基本安裝與製作
- 使用 node 安裝 gitbook 
    - npm install gitbook -g
    - npm install gitbook-cli -g

- 創建依專案資料夾,並進入
- 初始化 gitbook 文件 : gitbook init
- 將會看到 README.md , SUMMARY.md
- gitbook會依照 SUMMARY.md的 縮排 與 排列 順序來編輯電子書
- README.md 範例 :
```markdown
## 我的首頁
#### 看起來還不錯
```

- SUMMARY.md 範例 :

```markdown
# Summary

* [我的首頁](README.md)
    * [我的首頁分頁](my.md)
* [更多內容](content.md)
```

- .gitbook.yaml 為 gitbook設定檔
- .gitbook.yaml 範例 :

```
# Root directory to locate the content
# Default is the root directory of the repository.
root: ./你的專案資料夾名稱/

# Files to use as SUMMARY/README.
# (Relative to <root> directory)
structure:
  readme:  README.md
  summary: SUMMARY.md

# Redirect urls to specific files (relative to the <root> directory)
#redirects:
  #previous/page: new-folder/page.md
```
- 編輯完書籍 : 可用指令 gitbook serve 可隨時觀看是否有誤

#### github 步驟
- 請先在 github 創立一個專案(若不太會git建議起初創立README.md，之後就可以透過 upload files 直接上傳)
- 先將 .gitbook.yaml 設定檔上傳以後，再將專案資料夾上傳即可
- 原本github創建的 README.md 可以用來介紹此專案的目的

#### gitbook 步驟
- 當創建完帳號，一定會創立一個組織
- 名字都可以隨意(因為都可以更改頭像與名字)
- 在組織裡創建一個 space(電子書)
- space 的名字也可自取~最重要的是 與 github 連結(方便上版到gitbook)
- 點選左下方的 藍色方塊按鈕 找到 integrations 可以看到 github
- 點選以後，與當初在github的專案連結起來即可

#### gitbook pdf & 離線網頁版
- 前面的目錄檔案都需準備好
- 安裝 calibre
- 設定book.json檔(注意要放在同一目錄資料夾)
- book.json 範例 : 裡面包含pdf設定 與 plugin 插件

```json
{   
    "title": "Bootstrap 4 指南",
    "description": "<Bootstrap 4 指南>中文版",
    "language": "zh",
    "pluginsConfig": {
        "fontSettings": {
          "theme": "white",
          "family": "msyh",
          "size": 2
        } 
    },
    "plugins": [
      "multipart",
      "yahei",
      "katex",
      "search",
      "splitter",
      "collapsible-chapters"
   ],
  "pdf": {
    "pageNumbers": true, 
    "fontFamily": "Arial",
    "fontSize": 12,
    "paperSize": "a4",
    "margin": {
      "right": 0,
      "left": 0,
      "top": 0,
      "bottom": 0
    }
  }
}
```
- gitbook install : 安裝所有 plugin 插件
- gitbook build : 做出離線網頁板 book
- gitbook serve : 開啟網頁 gitbook
- gitbook pdf : 做出 電子書 pdf


