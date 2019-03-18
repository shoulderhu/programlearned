## v-on 知識

#### 應用範例
- v-on:click="reverseText" 可簡化成:@click="reverseText"
- 若使用@click.prevent 可以避免預設觸發(如a href="#"會回到最上面)
- 步驟
    - 1.先架設vue物件
    - 2.使用v-model接收使用者輸入字串(需先定義變數與接收的變數)
    - 3.利用v-on使用函數reverseText進行反轉
    - 4.若會觸發預設事件(置頂事件)，則使用prevent避免觸發
    - 5.將接收的變數(newText)輸出至文本上
    
```html
<div id="app">
  <input type="text" class="form-control" @keydown.enter="reverseText" v-model="text">
  <button class="btn btn-primary mt-1" v-on:click="reverseText">反轉字串</button>
  <div class="mt-3">
    {{ newText }}
  </div>
  <a :href="link" class="btn btn-primary mt-1" v-on:click.prevent="reverseText">反轉字串</button>
</div>

<script>
var app = new Vue({
  el: '#app',
  data: {
    //這邊需先定義好變數名稱
    text: '',
    newText: '',
    link:'www.google.com'
  },
  methods:{
    reverseText(){
      console.log(this.text);
      this.newText = this.text.split('').reverse().join('');
    }
  }
  // 請在此撰寫 JavaScript
});
</script>
```
