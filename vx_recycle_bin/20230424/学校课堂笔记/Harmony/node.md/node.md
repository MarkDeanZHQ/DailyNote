## 组件
### element
1. 于 common 文件夹下
2. 创建组件文件 .hml , .css , .js
3. 导入语法 `<element name="无所谓" src=""></element>`

#### js文件
```js
export default{
    data：{
        
    }，
    onInit(){
        
    }
}
```



## Html


### 模块

#### router


router 踩坑：
1. can‘t find this page
* 进入config.json， 给src 添加页面路径
* 路径不能 / 开头

```js
import router from '@system.router';

//作用： 跳转页面
//语法:
router.push(){    // 
    uri:"",
    params:{        //传递到 uri 组件中的参数，先于 onInit 函数传参 
        'var':'val',   
    }
}


router.replace(){uri:"",params:{}} //区别：替换页面, 不会创建新页面

router.back();//返回上一页面
router.back({path:''});//返回指定页面
router.clear() // 清空历史页面
router.getLength() // 获取页面数量
router.getState()  // 获取当前页面的信息
    1. ~.index
    2. ~.name
    3. ~.path

```

### 语法




#### 标签
```html
<!-- 滑动选项 -->
<picker-view [options]></picker-view>
```
options:
range="{{array}}"    ----  示意图中的 初中高级
selected="{{num}}"  ----  默认选中
onchange="func"    ----  当改变选中的时候，触发事件
func(obj)   obj.newSelected为新选中值

![picker-view 示意图](vx_images/185693814236651.png)

```html
<!-- 图片标签 -->
<imge src=""></image>
```
#### 变量
```html
<!-- 普通 js 变量 -->
<text>{{value}}</text>


<!-- i18n文件夹中 json变量 -->
<text>{{$t('strings.value')}}</text>
<text>{{$t('Files.value')}}</text>
```


#### 函数
```html
<!-- 自定义函数,在js中定义 -->
<text onclick="func"></text>  


<!-- 内置函数 -->

    <!-- 点击 -->
    <tag onclick=""></tag>

    <!-- 显示/隐藏 -->
    <tag show=""></tag>


```

#### 逻辑结构
```html
<!-- if -->
<text if="{{show}}"></text>
<text elif="{{display}}"></text>
<text else></text>


<!-- 1. for -->
    <text for="{{(key,item) in array}}">
    {{key}} --- {{value.id}} {{value.name}} {{value.age}} {{value.show}}
    </text>
    
<!-- 2. for -->
    <text for="{{array}}">
    {{$item.val}}
    </text>

<!-- show -->
<text show="{{}}"></text>

```

## Js

### 语法

#### 变量, 函数
```js
// data变量

    // 普通变量
    name:"",

    // 对象&数组
    array:[1,2,3],
    obj:{id:4,name:'mark',age:18},
    multiobj:[
    {id:4,name:'baba',age:124},
    {id:5,name:'mom',age:32}
    ]


// 函数
    onInit(){
        
    },
    onClickChange(){
        
    }
    
    // 函数变量
    //使用data中变量
    this.value = sth;

    //以 json 方式查看对象
    JOSN.stringify(obj);
```


