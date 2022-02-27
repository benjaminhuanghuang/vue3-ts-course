# Vue3组件化开发 二

## 非父子组件的通信

- Provide / Inject

父组件有一个provide选项来提供数据 
父组件不 知道哪些子组件使用它provide 的property

```
export default {
    components: {
      Home
    },
    provide() {
      return {
        name: "why",
        age: 18,
        // computed很重要
        length: computed(() => this.names.length) // ref对象 .value
      }
    },
```

子组件有一个inject选项来开始使用这些数据 
子组件不知道inject 的property 来自哪 

```
export default {
    inject: ["name", "age", "length"],
  }
```


- Mitt 全局事件总线
```
export default {
  created() {
    emitter.on("why", (info) => {
      console.log("why:", info);
    });

    emitter.on("kobe", (info) => {
      console.log("kobe:", info);
    });

    emitter.on("*", (type, info) => {
      console.log("* listener:", type, info);
    })
  }
}
```

export default {
  methods: {
    btnClick() {
      console.log("about按钮的点击");
      emitter.emit("why", {name: "why", age: 18});
      // emitter.emit("kobe", {name: "kobe", age: 30});
    }
  }
}

## Slot
```
<template>
  <div class="nav-bar">
    <div class="left">
      <slot name="left"></slot>
    </div>
    <div class="center">
      <slot name="center"></slot>
    </div>
    <div class="right">
      <slot name="right"></slot>
    </div>
    <div class="addition">
      <slot :name="name"></slot>
    </div>
  </div>
</template>
```

```
<template>
  <div>
    <nav-bar :name="name">
      <template #left>
        <button>左边的按钮</button>
      </template>
      <template #center>
        <h2>我是标题</h2>
      </template>
      <template #right>
        <i>右边的i元素</i>
      </template>
      <template #[name]>
        <i>why内容</i>
      </template>
    </nav-bar>
  </div>
</template>
```

