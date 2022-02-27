## computed
避免多次执行，代码重复，有缓存

传入函数， 也可以传入对象

```
  cumpunted: {
    fullName: function() {

    }

    fullName: {
      get(){

      },
      set(){

      }
    }
  }
```


## Watch
开发中在data()返回的对象中定义了数据，这个数据被绑定到template中，当数据变化时 template会更新显示最新的数据 
如果希望在代码中监听某个数据的变化

normal Watch
```
  info(newInfo, oldInfo) {
     console.log("newValue:", newInfo, "oldValue:", oldInfo);
  }
  
```
deep watch
```
  info: {
    handler: function(newInfo, oldInfo) {
      console.log("newValue:", newInfo.nba.name, "oldValue:", oldInfo.nba.name);
    },
    deep: true, // 深度侦听
    immediate: true // 第一次加载时立即执行 
  }



  thie.info.name = "abc"
```


## v-model
```
  <input v-model="searchText">

  <imput :value="searchText" @input="searchText=$event.target.value">
```

