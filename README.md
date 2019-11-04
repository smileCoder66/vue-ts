# test-ts
vue中使用ts 收集示例.

```ts
export default class App extends Vue {
  name: string = 'zxl'
  skill: string[] = ['js', 'css', 'node']
  arr2: Array<object> = [{ a: '1' }, { b: '2' }]
  dowhat(): boolean {
    return false
  }
  getMsg(jjg: number = 250, wxj: string = 'wxj'): string {
    return jjg.toString() + wxj
  }
  get doComputed(): string {
    return this.name + ' is ' + this.getMsg(250) + ' father'
  }//computed()
}
```
## 组件交互
```ts
import { Component, Prop, Vue } from 'vue-property-decorator'
import HelloWorld from './components/HelloWorld.vue'
@Component({
  components: {
    HelloWorld
  }
})
@Prop({
  type: Array, //接收数据类型
  required: false, //是否必填
  default: [1,2] //默认值
}) 
private abc!: number[]
```
### 待续...
```css
body{
   background:#58bc58; 
}
```