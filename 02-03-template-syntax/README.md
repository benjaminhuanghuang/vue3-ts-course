# 02 Vue3基础-模板语法

## Mustache
只能是expression， 不能是statements
```
  {{message}}

  {{coutner * 10}}

  {{message.split(' ').reverse.join(' ')}}

  {{getMessage()}}

    {{ isShow? "" :""}}
```

## v-once
当数据发生变化时 元素 或 组件以及其所有的子元素将 为静态内容并且跳过
用于性能优化 
```
  <div v-once>
    <h2>{{counter}}</h2>
    <h2>{{message}}</h2>
  </div>
```

## v-text
```
  <h2 v-text="message">
```

## v-html
```
```


## v-pre
跳过解析
 
## v-cloak
隐藏未编译的组件
```
<style>
[v-cloak] { display: none }
</style>

<div v-cloak>
</>
```

## v-bind
绑定属性
```
  <img v-bind:src="imgUrl" alt="">
```
简写
```
  <img :src="imgUrl" alt="">
```

绑定class
```
  <div :class="['abc', title]">哈哈哈哈</div>
   
  <div :class="['abc', title, isActive ? 'active': '']">哈哈哈哈</div>
  
  <div :class="['abc', title, {active: isActive}]">哈哈哈哈</div>
```

# v-on 
绑定多个事件()
```
  <div v-on="{click:btnClick, mouseMove:mouseMove}">
```
传递多个参数()
```
  <div @click="bthClick($event, 'arg2')">
```

简写
```
  @click="bthClick"

  @click="count++"
```

修饰符
.stop -  用event.stopPropagation()。
.prevent -  用event.preventDefault()。
.capture - 添加事件侦听器时使用capture 模式。
.self - 只当事件是从侦听器绑定的元素本  发时才 发回 。
.{keyAlias} - 仅当事件是从特定键 发时才 发回 。比如  @keyup.enter="enterKeyup"
.once - 只 发一次回 。
.left - 只当点击鼠标左键时 发。
.right - 只当点击鼠标右键时 发。
.middle - 只当点击鼠标中键时 发。
.passive - { passive: true } 模式添加侦听器


## Condition
``` 
  v-if
  v-else
  v-else-if
  v-show
```
v-show和v-if的区别

- v-show是不支持template
- v-show元素无 是否  显示到浏 器上 它的DOM实际 是有渲染的 只是通过CSS的display属性来进行切换。 v-if 为false时对应的元素不会渲染到DOM中 
- 如果元素需要在显示和隐藏之频繁切换使用v-show, 否则使用v-if 


## v-for
loop on array
```
<v-for="(val, index) in array" >
```

loop on obj
```
<v-for="(val, key, index) in info">
```

loop on num, base on 1
```
<v-for="num in 10">
```

## Key 的作用
没有Key的算法

有Key的算法





