## computed 功能知識

#### 應用
- 與 methods 差別
    - 不須創建變數來返回
    - 可直接輸出至文本
- 利用此函數定義可直接輸出到頁面:{{reverseText}}
- 步驟:
    - 1.創建vue物件
    - 2.利用v-model接收使用者輸入
    - 3.創建computed功能並建立reverseText函數
    - 4.在函數中必須返回參數
    - 5.將此函數直接輸出至文本上    

```html
<div id="app">
  <input type="text" class="form-control" v-model="text">
  <button class="btn btn-primary mt-1">反轉字串</button>
  <div class="mt-3">
    {{ text.split('').reverse().join('') }}
  </div>
  {{reverseText}}
</div>

<script>
var app = new Vue({
  el: '#app',
  data: {
    text: '',
    newText: ''
  },
  computed:{
    reverseText(){
      return this.text.split('').reverse().join('');
    }
  }
});
</script>
```