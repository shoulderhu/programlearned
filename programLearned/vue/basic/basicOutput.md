## vue格式與輸出

#### 1.輸出格式:
- 步驟:
    - 1.首先先創建js 的vue物件
    - 2.欲使用id與vue進行綁定
    - 3.必須先宣告變數(something)
    - 4.在HTML文本進行輸出
```javascript
var app = new Vue({
    el: '#app',
    data:{
        something:'這裡是一段話',
        text: '這是一段文字',
        rawHtml: `<span class="text-danger">紅色文字</span>`,
        number1: 100,
        number2: 300,
        htmlId: 'HTMLID',
        isDisabled: true
    }
})
```
- 創建vue空間
```html
<!--可做基本運算-->
<div id="app">
  {{something}}
  {{something+text}}
  {{number1*number2}}
</div>
```
- 輸出類型說明
    - 1.text(三種)
        - ```{{something}}```
        - ```<input type="text" v-model="something">```
        - ```<div v-text="something"></div>```
    - 2.html
        - ```<div v-html="something"></div>```

- v-once:只顯示一次並有效防止xss攻擊(利用輸入來攻擊網站)
    - ```<div v-html="something" v-once></div>```



