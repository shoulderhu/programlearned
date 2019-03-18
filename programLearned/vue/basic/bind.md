## v-bind 知識

#### 應用範例
- ```v-bind:src="imgSrc" 可簡化成 :src="imgSrc"```

```html
<!-- 創建一個圖片連結，並將src前面使用v-bind綁定 -->
<div id="app">
  <img v-bind:src="imgSrc" v-bind:class="className" alt="">
</div>

<!-- 使用vue data:imgSrc給予資料 -->
<script>
var app = new Vue({
  el: '#app',
  data: {
    imgSrc:'https://images.unsplash.com/photo-1479568933336-ea01829af8de?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=d9926ef56492b20aea8508ed32ec6030&auto=format&fit=crop&w=2250&q=80',
    className:'img-fluid'
  }
})
</script>
```


