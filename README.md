# ts

```ts
//1.布尔值
let isBoolean: boolean = false;
//2.数值
let decLiteral: number = 6;
let hexLiteral: number = 0xf00d;
// ES6 中的二进制表示法
let binaryLiteral: number = 0b1010;
// ES6 中的八进制表示法
let octalLiteral: number = 0o744;
let notANumber: number = NaN;
let infinityNumber: number = Infinity;
//3.字符串
let myName: string = "Zxl";
//4.空值
// 没有返回值的函数为void
function alertName(): void {
  alert("My name is Tom");
}
//声明一个 void 类型的只能将它赋值为 undefined 和 null
let unusable: void = undefined;
//undefined,null
let u: undefined = undefined;
let n: null = null;
//5.any
// 顾名思义,可以被任何值赋值
let anyThing: any = "hello";
let anyThing: any = 888;
let anyThing: any = true;
let anyThing: any = null;
let anyThing: any = undefined;

//--联合类型
let myFavoriteNumber: string | number;
myFavoriteNumber = "seven";
myFavoriteNumber = 7;
function getString(something: string | number): string {
  return something.toString();
}

//对象的类型——接口
interface Person {
  name: string;
  age: number;
}
let tom: Person = {
  name: "Tom",
  age: 25
};
function getUserInfo(user: Person): string {
  return user.age + "======" + user.name;
}
//1可选
interface Person {
  name: string;
  age?: number; // 表示这个属性可有可无
}
let tom: Person = {
  name: "Tom"
};
//2希望一个接口允许有任意的属性
interface Person {
  name: string;
  age?: number;
  [propName: string]: any;
}
let tom: Person = {
  name: "Tom",
  gender: "male" // 可以加其他的属性
};
//注意:
interface Person {
  name: string;
  age?: number;
  [propName: string]: string;
}
let tom: Person = {
    name: 'Tom',
    age: 25,❌ //必须是string
    gender: 'male'
};
//只读属性
interface Person {
    readonly id: number;
    name: string;
    age?: number;
    [propName: string]: any;
}

let tom: Person = {
    name: 'Tom',
    gender: 'male'
};

tom.id = 89757;❌ // 不能被二次赋值

//非空断言 !
let s = e.name;//抛出e可能不存在的错误
let s = e!.name;//e肯定存在
```

## vue-ts

vue 中使用 ts 简单示例.

```ts
export default class App extends Vue {
  name: string = "zxl";
  skill: string[] = ["js", "css", "node"];
  ever: Array<object> = [{ w: "10 thousand" }, { j: "build" }, { y: "sheep" }];

  dowhat(): boolean {
    //指定函数必须有返回值且定义类型
    return false;
  }

  getMsg(jjg: number = 250, wxj: string = "wxj"): string {
    //指定传参对应类型&默认值
    return jjg.toString() + wxj;
  }

  get doComputed(): string {
    return this.name + " is " + this.getMsg(250) + " father";
  } //computed()

  render(createElement): VNode {
    return createElement("div", this.greeting);
  }

  mounted() {
    console.log("symple");
  } //life cycle

  //——collecting...
}
```

## 组件交互

```ts
//父组件-->
import { Component, Provide, Vue } from "vue-property-decorator";
@Component({
  // 所有的组件选项都可以放在这里
  template: '<button @click="onClick">Click!</button>'
})
export default class HelloWorld extends Vue {
  @Provide() sendProvide: string = "ts比js长一点啦";
  onClick(): void {
    window.alert(this.message);
  }
}

//子组件-->
import { Component, Prop, Inject, Vue } from "vue-property-decorator";
export default class HelloWorld extends Vue {
  @Prop(String)
  readonly msg: string | undefined;

  @Prop({
    type: Array, //接收数据类型
    required: false, //是否必填
    default: [1, 2] //默认值
  })
  private abc!: number[];

  @Inject()
  ["sendProvide"]: string;

  @Inject()
  readonly foo!: string;
}
```

## 数据交互

```html
collecting...
```

### 待续

[Vue-typescript 介绍]

[官方介绍(vue-property-decorator)](https://github.com/kaorun343/vue-property-decorator)

```css
body {
  background: #58bc58;
}
```
