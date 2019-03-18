## TodoList 練習

#### 實現基本結構
- 若下載好資料後可至 basic > todo.html 開始進行修改
- 建立 資料陣列(todos) 與 暫時資料變數(newtodo)

```javascript
<script>
	var app = new Vue({
		el: '#app',
		data: {
			newTodo: '',
			todos: [],
		},
		methods:{},
		computed:{}
	});
</script>
```
- 在 input 使用 v-model 得到使用者輸入字串 
- 在 列表li 建立 v-for循環結構

#### 實現增加資料   
- 增加 methods addTodo 用來增加資料

```javascript
addTodo() {
	var value = this.newTodo.trim();
	var timestamp = Math.floor(Date.now());
	//如果沒有輸入則直接返回
	if (!value) {
		return;
	}
	this.todos.push({
		id: timestamp,
		title: value,
		completed: false							
	});
	//將暫存區資料清除以便下次存取
	this.newTodo = '';
},
```
- 將 addTodo 放入 button(@click="addTodo") 與 input( @keyup.enter) 方便加入列表資料
- 將 {{item.title}} 放入label標籤內顯示資料名稱
- 將 :for="item.id" 與 :id="item.id" 放入label 與 input 方便辨識各個資料
  
#### 實現刪除資料
- 在下面 button(x鍵) 加入 removeTodo 方法並傳入 item 指定刪除此資料
- 建立 removeTodo 方法 來刪除列表資料
  - 傳入 item 並找出在todos對應的正確id 
  - 利用找出的 id 刪除 item

```javascript
removeTodo(todo) {
	let vm = this;
	let newIndex = vm.todos.findIndex(function(item){
		return todo.id === item.id;
	});
	this.todos.splice(newIndex,1);
},
```

  
#### 實現刪除線
- 增加 css

```css
<style>
.completed {
	text-decoration: line-through;
}
</style>
```
- 於input checkbox內增加 v-model="item.completed"(當按下時變為true)
- 於label 增加 :class="{'completed':item.completed}" 來進行切換
  
#### 實現過濾資料
- 增加預設全部顯示 : 在 data 內新增 visibility='all'
- 於連結增加 :class="{'active': visibility =='對應的參數'}" @click="visibility='對應的參數'"

```javascript
<div class="card-header">
	<ul class="nav nav-tabs card-header-tabs">
		<li class="nav-item">
			<a class="nav-link " :class="{'active': visibility =='all'}" @click="visibility='all'" href="#">全部</a>
		</li>
		<li class="nav-item">
			<a class="nav-link " :class="{'active': visibility =='active'}" @click="visibility='active'" href="#">進行中</a>
		</li>
		<li class="nav-item">
			<a class="nav-link" :class="{'active': visibility =='completed'}" @click="visibility='completed'" href="#">已完成</a>
		</li>
	</ul>
</div>
```
- 增加 computed 計算函數 : filteredTodos來回傳顯示的陣列資料

```javascript
computed:{
	filteredTodos(){
		let newTodos = [];
		if(this.visibility == 'all'){
			return this.todos;
		}else if(this.visibility == 'active'){
			//對todos每一項資料進行循環檢測
			this.todos.forEach(function(item){
				if(!item.completed){
					//將未完成資料放入新的陣列
					newTodos.push(item);
				}
			})
			return newTodos;
		}else if(this.visibility == 'completed'){
			//對todos每一項資料進行循環檢測
			this.todos.forEach(function(item){
				if(item.completed){
					//將未完成資料放入新的陣列
					newTodos.push(item);
				}
			})
			return newTodos;
		}
	}
}
```
- 將 v-for 的 todos 改成 filteredTodos 來顯示過濾後資料 即可進行過濾

#### 實現雙擊修改標題功能
- 新增預設變數 cacheTodo,cacheTile 存取更改資料
- 新增修改函數 editTodo 存取使用者欲更改資料 

```javascript
editTodo(item){
	//用來儲存未更改資料
	this.cacheTodo = item;
	this.cacheTitle = item.title;
},
```
- 在 li 新增雙擊事件 @dblclick="editTodo(item)
- 新增 列表資料 與 input輸入框 互相切換顯示 : v-if="item.id !== cacheTodo.id" 與 v-if="item.id === cacheTodo.id"
- 在 input 內增加 v-model="cacheTitle" 來讀取使用者修改資料
- 在 input 內增加 esc離開編輯,enter完成編輯 事件

#### 實現自動計算未完成筆數
- 在 computed 新增 totall 函數

  ```javascript
  totall(){
	let sum = this.todos.length;
	if(sum == 0){
		return sum;
	}else{
		this.todos.forEach(function(item){
			if(item.completed){
				sum--;
			}
		})
		return sum;
	}								
  }
  ```
- 將 ```{{totall}}``` 放入 ```<span>``` 之中即可

#### 完成後程式碼

```html
<div id="app">
	<div class="input-group mb-3">
		<div class="input-group-prepend">
			<span class="input-group-text" id="basic-addon1">待辦事項</span>
		</div>
		<input type="text" class="form-control" placeholder="準備要做的任務" v-model="newTodo" @keyup.enter="addTodo">
		<div class="input-group-append">
			<button class="btn btn-primary" type="button" @click="addTodo">新增</button>
		</div>
	</div>
	<div class="card text-center">
		<div class="card-header">
			<ul class="nav nav-tabs card-header-tabs">
				<li class="nav-item">
					<a class="nav-link " :class="{'active': visibility =='all'}" @click="visibility='all'" href="#">全部</a>
				</li>
				<li class="nav-item">
					<a class="nav-link " :class="{'active': visibility =='active'}" @click="visibility='active'" href="#">進行中</a>
				</li>
				<li class="nav-item">
					<a class="nav-link" :class="{'active': visibility =='completed'}" @click="visibility='completed'" href="#">已完成</a>
				</li>
			</ul>
		</div>
		<ul class="list-group list-group-flush text-left">
			<li class="list-group-item" v-for="(item,key) in filteredTodos" @dblclick="editTodo(item)">
				<div class="d-flex" v-if="item.id !== cacheTodo.id">
					<div class="form-check">
						<input type="checkbox" class="form-check-input" :id="item.id" v-model="item.completed">
						<label class="form-check-label"
						:class="{'completed':item.completed}" 
						:for="item.id">
							{{item.title}}
						</label>
					</div>
					<button type="button" class="close ml-auto" aria-label="Close" @click="removeTodo(item)">
						<span aria-hidden="true">&times;</span>
					</button>
				</div>
				<input type="text" class="form-control" 
				v-model="cacheTitle"
				@keyup.esc="cancelEdit()"
				@blur="cancelEdit()"
				@keyup.enter="doneEdit(item)"
				v-if="item.id === cacheTodo.id">
			</li>
			<li class="list-group-item">
				<input type="text" class="form-control">
			</li>
		</ul>
		<div class="card-footer d-flex justify-content-between">
			<span>還有 {{totall}} 筆任務未完成</span>
			<a href="#" @click="removeAllItem()">清除所有任務</a>
		</div>
	</div>
</div>

<script>
	var app = new Vue({
		el: '#app',
		data: {
			newTodo: '',
			todos: [],
			visibility:'all',
			cacheTodo:{},
			cacheTitle:''
		},
		methods: {
			addTodo() {
				var value = this.newTodo.trim();
				var timestamp = Math.floor(Date.now());
				//如果沒有輸入則直接返回
				if (!value) {
					return;
				}
				this.todos.push({
					id: timestamp,
					title: value,
					completed: false							
				});
				this.newTodo = '';
			},
			removeTodo(todo) {
				let vm = this;
				let newIndex = vm.todos.findIndex(function(item){
					return todo.id === item.id;
				});
				this.todos.splice(newIndex,1);
			},
			editTodo(item){
				this.cacheTodo = item;
				this.cacheTitle = item.title;
			},
			cancelEdit(){
				this.cacheTodo = {};
			},
			doneEdit(item){
				item.title = this.cacheTitle;
				this.cacheTitle = '';
				this.cacheTodo = {};
			},
			removeAllItem(){
				this.todos = [];
				this.totall = 0;
			}
		},
		computed:{
			filteredTodos(){
				let newTodos = [];
				if(this.visibility == 'all'){
					return this.todos;
				}else if(this.visibility == 'active'){
					//對todos每一項資料進行循環檢測
					this.todos.forEach(function(item){
						if(!item.completed){
							//將未完成資料放入新的陣列
							newTodos.push(item);
						}
					})
					return newTodos;
				}else if(this.visibility == 'completed'){
					//對todos每一項資料進行循環檢測
					this.todos.forEach(function(item){
						if(item.completed){
							//將未完成資料放入新的陣列
							newTodos.push(item);
						}
					})
					return newTodos;
				}
			},
			totall(){
				let sum = this.todos.length;
				if(sum == 0){
					return sum;
				}else{
					this.todos.forEach(function(item){
						if(item.completed){
							sum--;
						}
					})
					return sum;
				}								
			}
		}
	});
</script>

<style>
	.completed {
		text-decoration: line-through;
	}
</style>
```
