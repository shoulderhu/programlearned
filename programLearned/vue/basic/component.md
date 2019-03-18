## vue 元件(標籤化)

#### 利用元件化可讓同一物件重複使用
- 利用 Vue.component 進行自定義標籤
  - 格式
  ```js
  Vue.component('自定義標籤名稱', {
    data: function () {
      return {
        變數名稱: 變數單位
      }
    },
    template: `
      標籤內的輸出
    `
  })
  ```
- 範例:
```html
<counter-component></counter-component>
<script>
Vue.component('counter-component', {
  data: function () {
    return {
      counter: 0
    }
  },
  template: `
    <div>
      你已經點擊 <button class="btn btn-outline-secondary btn-sm" @click="counter += 1">{{ counter }}</button> 下。
    </div>
  `
})
</script>
```