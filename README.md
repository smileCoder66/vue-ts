# test-ts
vue中使用ts 收集示例.

```ts
export default class App extends Vue {
  name: string = 'zxl'
  skill: string[] = ['js', 'css', 'node']
  ever: Array<object> = [//数组内部类型 不能直接定为Array
    { w: '10 thousand' },
    { j: 'build' },
    { y: 'sheep' }
  ]
  
  dowhat(): boolean {//指定函数必须有返回值且定义类型
    return false
  }

  getMsg(jjg: number = 250, wxj: string = 'wxj'): string {
    //指定传参对应类型&默认值
    return jjg.toString() + wxj
  }

  get doComputed(): string {
    return this.name + ' is ' + this.getMsg(250) + ' father'
  }//computed()

  mounted() {
    console.log('symple')
  }//life cycle

  //——collecting...
}
```
## 组件交互
```ts
//父组件-->
import { Component, Provide, Vue } from 'vue-property-decorator'
export default class HelloWorld extends Vue {
  @Provide() sendProvide: string = 'ts比js长一点啦'
}

//子组件-->
import { Component, Prop, Inject, Vue } from 'vue-property-decorator'
export default class HelloWorld extends Vue {
  @Prop(String)
  readonly msg: string | undefined

  @Prop({
    type: Array, //接收数据类型
    required: false, //是否必填
    default: [1, 2] //默认值
  })
  private abc!: number[];

  @Inject()
  ['sendProvide']: string

  @Inject()
  readonly foo!: string
}
```

## 数据交互
```
collecting...
```

### 待续...
[官方介绍](https://github.com/kaorun343/vue-property-decorator)
```css
body{
   background:#58bc58; 
}
```