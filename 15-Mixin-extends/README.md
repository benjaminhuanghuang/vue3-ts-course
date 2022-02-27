## Mixin
```
  import {demoMixin} from "./demoMixin"

  export default {
    mixins: [demoMixin]
  }
``` 

## Merge Rule
- 情况一 如果是data函数的 回值对象
  - 返回值对象默认·情况下会行合并 
  - 如果data 回值对象的属性发生了冲突，保留组件自身的数据 

- 情况二 如何生命周期 子函数
生命周期的钩子函数会被合并到数组中，都会被调用 

- 情况三 值为对象的 项 例如methods、components 和directives 将 合并为同一个对象。
  - 比如都有methods 项 并且 定义了方法  么它们都会生效 
  - 但是如果对象的key相同，那么会取组件对象的键值对 


  ## 全局混入Mixin
  混入所有对象
  ```
    app.mixin({
      created() {

      }
    })
  ```

## extends
extends, mixin 都被composition 取代

```
  import BasePage from './BasePage.vue';

  export default {
    extends: BasePage

  }
```