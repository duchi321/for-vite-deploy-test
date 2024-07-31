<script setup>
import { ref } from 'vue'

const num = ref(0)
const htmltemplate = '<h2>thie is paragrpah</h2>'
function addNum() {
  num.value++
}
// ------ 分隔線 ------
const text = ref('this is paragraph')
const city = ref('台北市')
// ------ 分隔線 ------
const isChecked = ref(true)
const arrayCheckbox = ref([])
// ------ 分隔線 ------
const radioValue = ref('male')
// ------ 分隔線 ------
const count = ref(0)
setInterval(() => {
  count.value++
}, 1000)
const htmltext = ref('<h4>This is paragraph</h4>')
const imgUrl = ref(
  'https://plus.unsplash.com/premium_photo-1663853489900-3f24ea776dea?w=200&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxmZWF0dXJlZC1waG90b3MtZmVlZHwyfHx8ZW58MHx8fHx8'
)
// ------ 分隔線 ------
const isbindChecked = ref(true)
const isbindCheckedtwo = ref(true)
// ------ 分隔線 -----
const handleClick = () => {
  console.log('touch')
}
const submitForm = () => {
  console.log('send out')
}
const hint = ref('hello')
// ------ 分隔線 ------
const forArray = ref([
  {
    id: '1',
    name: 'jeff',
    age: 16
  },
  {
    id: '2',
    name: 'tonny',
    age: 20
  },
  {
    id: '3',
    name: 'jsion',
    age: 32
  }
])
const checkitem = ref(false)
</script>

<template>
  <div>
    <h1 style="color: brown">模板語法 V- 指令</h1>
    <p>單純把 js(script setup)的值,渲染到html(template).</p>
    <h2>click button</h2>
    <p>This is Number: {{ num }}</p>
    <p v-text="num"></p>
    <button type="button" v-on:click="addNum">+</button>
    <hr />
    <p>this is : {{ htmltemplate }}</p>
    <div v-text="htmltemplate"></div>
    <div v-html="htmltemplate"></div>
  </div>
  <hr style="border: 3px solid" />
  <div>
    <h1 style="color: brown">v-model指令</h1>
    <p>使js, html的原始值雙向綁定</p>
    <h2>值與input框內雙向綁定: {{ text }}</h2>
    <input type="text" v-model="text" />
    <hr />
    <!-- 表單 -->
    <h3>表單運用</h3>
    <h2>value的是js,tag option是html</h2>
    {{ city }}
    <select name="" id="" v-model="city">
      <option value="台北市">台北市</option>
      <option value="新竹市">新竹市</option>
      <option value="高雄市">高雄市</option>
    </select>
    <hr />
    <h3>checkbox: ture false</h3>
    <h2>唯一不需要 value存放 值</h2>
    {{ isChecked }}
    <input type="checkbox" v-model="isChecked" />
    <hr />
    <h3>checkbox: array</h3>
    {{ arrayCheckbox }}
    <input type="checkbox" v-model="arrayCheckbox" value="初級" />
    <input type="checkbox" v-model="arrayCheckbox" value="中級" />
    <input type="checkbox" v-model="arrayCheckbox" value="高級" />
    <hr />
    <h3>radio 唯一值</h3>
    <div>{{ radioValue }}</div>
    <input type="radio" v-model="radioValue" value="male" />
    <input type="radio" v-model="radioValue" value="female" />
  </div>
  <hr style="border: 3px solid" />
  <h1 style="color: brown">Vue 常用指令</h1>
  <h2>v-text</h2>
  <h3>v-text 不好用,請使用雙大括號</h3>
  <p>計數: {{ count }}</p>
  <p v-text="count"></p>
  <hr />
  <h2>v-html</h2>
  <h3>很像js的innerHTML、textContent</h3>
  <p>雙括號、v-text渲染出來純文字,html會考慮樣式</p>
  {{ htmltext }}
  <div v-text="htmltext"></div>
  <div v-html="htmltext"></div>
  <hr style="border: 3px solid" />
  <h1 style="color: brown">v-bind</h1>
  <h2>v-bind:屬性, 太常用了所以縮寫為 :屬型</h2>
  <p>正常 v-bind:src</p>
  <div>
    <img v-bind:src="imgUrl" alt="" />
  </div>
  <p>縮寫 :src</p>
  <div>
    <img :src="imgUrl" alt="" />
  </div>
  <hr />
  <h2>可套用在任何屬性上</h2>
  <p>配合checkbox,套用在input text</p>
  <p>disabled 效果: 無法選取</p>
  {{ isbindChecked }}
  <input type="checkbox" v-model="isbindChecked" />
  <input type="text" :disabled="isbindChecked" />
  <h2>可套用在行內樣式</h2>
  <p>行內樣式</p>
  <div class="box" style="transform: rotate(45deg)"></div>
  <p>v-bind的寫法</p>
  <div class="box" :style="{ transform: 'rotate(45deg)' }"></div>
  <hr />
  <p>在transform的值套用變數用法,搭配3位元</p>
  <input type="checkbox" v-model="isbindCheckedtwo" />
  <div class="box" :style="{ transform: isbindCheckedtwo ? 'rotate(45deg)' : null }"></div>
  <p>如果遇到-,改駝峰式寫法. EX: background-color => backgroundColor</p>
  <div class="box" :style="{ backgroundColor: isbindCheckedtwo ? 'red' : 'green' }"></div>
  <h2>可以套用在class上</h2>
  <p>需要套用的className: 變數</p>
  <div class="box" :class="{ colorChange: isbindCheckedtwo }"></div>
  <hr style="border: 3px solid" />
  <h1 style="color: brown">v-on</h1>
  <h2>可理解為事件監聽</h2>
  <h3>notice: button的type預設是submit,所以要主動寫type="button"</h3>
  <form action="" @submit.prevent="submitForm">
    <p>正常寫法</p>
    <button type="button" v-on:click="handleClick">Click Me</button>
    <p>縮寫</p>
    <button type="submit" @click="handleClick">Click Me</button>
  </form>
  <h2>事件修飾符</h2>
  <a href="#" @click.prevent="handleClick">Click Me again</a>
  <h2>按鍵修飾符</h2>
  <input type="text" @keydown.enter="handleClick" v-model="hint" />
  <hr style="border: 3px solid" />
  <h1 style="color: brown">v-for</h1>
  <div>
    <div>
      name: {{ forArray[0].name }} <br />
      age: {{ forArray[0].age }}
      <hr />
    </div>
    <p>v-for 與 v-if 不能寫一起, 寫在外層或內層</p>
    <p>使用v-for時, 一定要加上key</p>
    <div v-for="(item, key) in forArray" :key="item.id">
      id: {{ key }}. <br />
      name: {{ item.name }}. <br />
      age: {{ item.age }}.
      <div v-if="item.age > 18">age 大於 18</div>
      <div v-else>age 小於 18</div>
      <hr />
    </div>
  </div>
  <h1 style="color: brown">v-if & v-else</h1>
  <input type="checkbox" v-model="checkitem" /> {{ checkitem }}
  <p>v-if如果沒觸發 元素會消失</p>
  <h2 v-if="checkitem">checkitem === true, true</h2>
  <h2 v-else>checkitem === false, false</h2>
  <hr />
  <h1 style="color: brown">v-show</h1>
  <p>v-show如果沒觸發 元素還在,樣式表呈現display: none,看不到</p>
  <h2 v-show="checkitem">checkitem === true, display:black</h2>
</template>

<style>
.box {
  margin: 30px;
  height: 100px;
  width: 100px;
  background-color: red;
  transition: 0.3s all;
}
.colorChange {
  background-color: blue;
}
.fourborder {
  border: 10px solid black;
}
</style>
