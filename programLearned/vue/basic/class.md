## v-class 知識

#### 應用1
- 使用 :class="{'rotate':isTransform}" 進行改變
    - 格式: v-bind:class="{'類別名':布林變數}" (v-bind可簡化成:(冒號)) 
    - 可多重增加 > :class="{'rotate':isTransform,'bg-danger':boxColor}"
    - 若本身類別具有意義則可 > :class="{'active','btn-outline-primary'}"
    - 若為true則啟用,false為失效

```html
<div id="app">
  <div class="box" :class="{'rotate':isTransform}"></div>
  <hr>
  <button class="btn btn-outline-primary" @click="isTransform = !isTransform">選轉物件</button>
</div>

<script>
var app = new Vue({
  el: '#app',
  data: {
    isTransform: false,
    boxColor:false
  },
});
</script>

<style>
.box {
  transition: transform .5s;
}
.box.rotate {
  transform: rotate(45deg)
}
</style>
```

#### 應用2:物件寫法

```html
<div class="box" :class="objectClass"></div>
<p>請將此範例改為 "物件" 寫法</p>
<hr>
<button class="btn btn-outline-primary" @click="objectClass.rotate = !objectClass.rotate">選轉物件</button>
<div class="form-check">
    <input type="checkbox" class="form-check-input" id="classToggle2" v-model="objectClass['bg-danger']">
    <label class="form-check-label" for="classToggle2">切換色彩</label>
</div>

<script>
var app = new Vue({
  el: '#app',
  data: {
    isTransform: false,
    boxColor:false,
    objectClass: {
      'rotate': false,
      'bg-danger': false,
    }
  },
});
</script>

<style>
.box {
  transition: all .5s;
}
.box.rotate {
  transform: rotate(45deg)
}
</style>
```

#### 應用3:陣列寫法(動態加入類別)

```html
<button class="btn" :class="arrayClass">請操作本元件</button>
<p>請用陣列呈現此元件 className</p>
<div class="form-check">
    <input type="checkbox" class="form-check-input" id="classToggle3" v-model="arrayClass" value="btn-outline-primary">
    <label class="form-check-label" for="classToggle3">切換樣式</label>
</div>
<div class="form-check">
    <input type="checkbox" class="form-check-input" id="classToggle4" v-model="arrayClass" value="active">
    <label class="form-check-label" for="classToggle4">啟用元素狀態</label>
</div>

<script>
var app = new Vue({
  el: '#app',
  data: {
    isTransform: false,
    boxColor:false,
    // Array 操作
    arrayClass: []
  },
});
</script>
```

#### 綁定行內樣式

```html
<div class="box" :style="{backgroundColor:'red'}"></div>
<div class="box" :style="[{backgroundColor:'red'},{borderWidth:'5px'}]"></div>
<div class="box" :style="styleObject"></div>
<div class="box" :style="[styleObject,styleObject2]"></div>
<hr>
<h5>自動加上 Prefix (依據瀏覽器而增加(ex:-webkit))</h5>
<div class="box" :style="styleObject3"></div>

<script>
var app = new Vue({
  el: '#app',
  data: {
    isTransform: false,
    boxColor:false,
    // Array 操作
   styleObject: {
      backgroundColor: 'red',
      borderWidth: '5px'
    },
    styleObject2: {
      boxShadow: '3px 3px 5px rgba(0, 0, 0, 0.16)'
    },
    styleObject3: {
      userSelect: 'none'
    }
  },
});
</script>
```

