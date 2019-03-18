## v-for 與 v-if 知識

#### 應用範例
- v-if
    - 寫法:v-if="條件判斷式"

- v-for(會重複把此標籤內的所有+自己進行迴圈)
    - 1.寫法:v-for="個 in 群"
    - 2.寫法:v-for="(個,引數(第幾個)) in 群"
    
```html
<div id="app">
    <pre>{{list}}</pre>
    <ul>
        <li v-for="(item,index) in list" v-if="item.age <=25">
            {{index}} - {{item.name}} 年齡是{{item.age}}歲
        </li>
    </ul>  
</div>

<script>
var app = new Vue({
  el: '#app',
  data: {
    list: [
      {
        name: '小明',
        age: 16
      },
      {
        name: '媽媽',
        age: 38,
      },
      {
        name: '漂亮阿姨',
        age: 24
      }
    ]
  }
})
</script>
```
