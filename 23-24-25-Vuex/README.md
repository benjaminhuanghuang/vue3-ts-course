# Vuex的状态管理

## Vuex 5 key components
- State
- getters
- mutations
- actions
- modules


- install
```
  npm install vuex@next
```
## Store
- create store
``` 
  const store = createStore({
    state() {
      return {
        rootCounter: 100
      }
    },
    getters: {
      doubleRootCounter(state) {
        return state.rootCounter * 2
      }
    },
    mutations: {
      increment(state) {
        state.rootCounter++
      }
    },
    modules: {
      home,
      user
    }
  });

  export default store;

```

- use the data in store 
state 是响应式的
```
  createApp(App).use(store).mount('#app')


  {{ $store.state.count }}
```

mapState(['key'])

```
computed: {
    ...mapState(['key'])

    ...mapState({
      counter: (state => state.counter)
    })
} 
```
in setup
```
setup() {
  const store = useStore();
  const sCount = computed(()=> store.state.count);

  return {
    sCount
  }


}
```

- Operate state
```
    this.$store.commit("increment", aregs);
```
mutation 不能有异步请求



# Vuex的状态管理 2

## Getters
```
const store = createStore({
  state(){

  },
  mutations:{

  },
  getters: {
    totalPrice(state, getters){
      ...
      return result;
    }
  }
})
```


```
{{store.getters.totalPrice}}


  computed: {
    ...mapGetter(["name"]),

    ...mapGetters({
      sName: "name"
    })
  }
  
```
use setup()

```
setup() {
  const store = userStore();

  // method 1
  const sName = computed(()=> store.getters.name);

  // method 2
  cosnt storeGettersFns = mapGetters([.....])

  return {
    sName
    ...storeGettersFns
  }
}
```



# Vuex的状态管理 3

异步操作的数据应该交给 state

action可以包含异步操作

## Actions
```
  mutations: {
    increment(state) {
      state.counter++;
    }
  },
  actions: {
    increment(context){
      
      // Api call ...

      context.commit("increment");
    }
  }
```

in Vue component
```
  this.$store.dispatch("incrementAction")
```