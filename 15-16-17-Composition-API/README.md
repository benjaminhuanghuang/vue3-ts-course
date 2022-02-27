options API的缺点
- 逻辑被拆分到多个属性中，可读性差


# Vue3 Composition API 一 
用option setup()替代别的选项

setup中不能使用this, setup调用之前，data，comoponent，methods 都还没有被解析

constext 包含 attrs, slots, emit


setup的返回值可以在模板template中使用， 也就是可以用setup的返回值来替代data项 

```
  setup(props, context){
    const state = reactive({
      count: 10
    })
    return {
      state,

    }
  }
```

## reactive API
Vue2 会对 data()返回的数据进行包装，使其可以reactive

Vue3 要自己调用reactive

## ref API
不再需要state和reactive
```
  模版中 {{count.value}} 可以简写为 {{count}}, 但只会解包一层

 setup(props, context){
    let count = ref(10);

    const increment = ()=> {
      count.value ++;    
    }

    return {
      count,
      increment
    }
  }
```

## readonly
preadonly会返回原生对象的只读代理 也就是它依然是一个Proxy  是一个proxy的set方法被劫持 并且不能对其进行修改

```
setup(props, context){
  const state = reactive({
      count: 10
  })

  const readOnlyState = readonly(state);
  
  return {
    count,
    increment
  }
}
```
## toRefs， toRef
toRefs() 可以将reactive返回的对象中的属性都转成ref 
toRef() 可以将reactive返回的对象中的一个属性转成ref 

```
  const {name, age} = toRefs(state);
  const name = toRef(state, 'name')
```


# Vue3 Composition API 二 


# Vue3 Composition API 三 高级语法

