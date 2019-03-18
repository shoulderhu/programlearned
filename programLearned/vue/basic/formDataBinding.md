## 表單雙向綁定

#### 應用
- 利用v-model進行資料綁定

```html
<div id="app">
  <h4>字串</h4>
  {{ text }}
  <input type="text" class="form-control" v-model="text">
  <hr>
  <pre>{{ textarea }}</pre>
  <textarea cols="30" rows="3" class="form-control" v-model="textarea"></textarea>
  <hr>
  <h4>Checkbox 與 Radio</h4>
  <div class="form-check">
    <input type="checkbox" class="form-check-input" id="check1" v-model="checkbox1">
    <label class="form-check-label" for="check1"> ... </label>
  </div>
  <hr>
  <!-- 這邊會將input value 帶給 checkboxArray-->
  <div class="form-check">
    <input type="checkbox" class="form-check-input" id="check2" v-model="checkboxArray" value="雞">
    <label class="form-check-label" for="check2">雞</label>
  </div>
  <div class="form-check">
    <input type="checkbox" class="form-check-input" id="check3" v-model="checkboxArray" value="豬">
    <label class="form-check-label" for="check3">豬</label>
  </div>
  <div class="form-check">
    <input type="checkbox" class="form-check-input" id="check4" v-model="checkboxArray" value="牛">
    <label class="form-check-label" for="check4">牛</label>
  </div>
  <p>晚餐火鍋裡有 <span v-for="item in checkboxArray">{{item}}.</span>。</p>
  <hr>
  <!-- 這邊會將input value 帶給 singleRadio-->
  <div class="form-check">
    <input type="radio" class="form-check-input" id="radio2" v-model="singleRadio" value="雞">
    <label class="form-check-label" for="radio2">雞</label>
  </div>
  <div class="form-check">
    <input type="radio" class="form-check-input" id="radio3" v-model="singleRadio" value="豬">
    <label class="form-check-label" for="radio3">豬</label>
  </div>
  <div class="form-check">
    <input type="radio" class="form-check-input" id="radio4" v-model="singleRadio" value="牛">
    <label class="form-check-label" for="radio4">牛</label>
  </div>
  <p>晚餐火鍋裡有 {{singleRadio}}...。</p>
  <hr>
  <h4>Select</h4>
  <select name="" id="" class="form-control" v-model="selected">
    <option disabled value="">請選擇</option>
    <option value="小美">小美</option>
    <option value="阿姨">阿姨</option>
  </select>
</div>

<script>
var app = new Vue({
  el: '#app',
  data: {
    text: '',
    textarea: '',
    checkbox1: false,
    checkboxArray: [],
    singleRadio: '',
    selected: '',
  },
});
</script>
```
