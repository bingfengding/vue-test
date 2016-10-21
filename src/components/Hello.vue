<template>
  <div id="hello">
      <div id="example-1">
          <button @click="counter += 1">增加 1</button>
          <p>这个按钮被点击了 {{ counter }} 次。</p>
      </div>
      <div id="example-2">
          <!-- `greet` 是在下面定义的方法名 -->
          <button @click="greet">Greet</button>
      </div>
      <button @click="warn('Form cannot be submitted yet.', $event)">Submit</button>
      <!-- 阻止单击事件冒泡 -->
      <a @click.stop="doThis">123</a>
      <!-- 提交事件不再重载页面 -->
      <form @submit.prevent="onSubmit"></form>
      <!-- 修饰符可以串联  -->
      <a @click.stop.prevent="doThat">321</a>
      <!-- 只有修饰符 -->
      <form @submit.prevent></form>
      <!-- 添加事件侦听器时使用 capture 模式 -->
      <div @click.capture="doThis">...</div>
      <!-- 只当事件在该元素本身（而不是子元素）触发时触发回调 -->
      <div @click.self="doThat">...</div>
      <hr/>

<!--
在监听键盘事件时，我们经常需要监测常见的键值。 Vue 允许为 v-on 在监听键盘事件时添加按键修饰符：

只有在 keyCode 是 13 时调用 vm.submit()
      <input @keyup.13="submit">

记住所有的 keyCode 比较困难，所以 Vue 为最常用的按键提供了别名：
      <input @keyup.enter="submit">
      全部的按键别名：
      enter
      tab
      delete (捕获 “删除” 和 “退格” 键)
      esc
      space
      up
      down
      left
      right
      -->
      <input type="checkbox" id="checkbox" v-model="checked">
      <label for="checkbox">{{ checked }}</label>
      <input v-model="message" placeholder="edit me">
      <p>Message is: {{ message }}</p>
  </div>

</template>

<script>
   export default{
        data(){
            return{
                counter:0,
                name: 'Vue.js'
            }
        },
        methods: {
    greet: function (event) {
      // `this` 在方法里指当前 Vue 实例
      alert('Hello ' + this.name + '!')
      // `event` 是原生 DOM 事件
      alert(event.target.tagName)
    },
     warn: function (message, event) {
    // 现在我们可以访问原生事件对象
    if (event) event.preventDefault()
    alert(message)
  }
  }

   }

</script>

<style scoped>


</style>
