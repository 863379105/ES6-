## ES6笔记


### 1.let 和 const
##### let 和 var 的差异
- let 允许声明一个在作用域限制在块级中的变量、语句或者表达式块级作用域 {}
- var 声明的变量只能是全局或者整个函数块的
- let 不能重复声明
- let 不会被预解析
- 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/let
##### const 常量
- 常量不能重新赋值
- 不能重复声明
- 块级作用域
- const 不会被预解析
- 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/const

### 2.let、const和var平常怎么区分使用？
- 由于ie低版本不兼容es6新语法，所以在使用时要优先考虑兼容性问题。如果在不考虑兼容性问题时，使用let或者const肯定是要优于var。
 
- 其次，由于const声明常量的特殊性，在声明时一定要注意，如果是需要改变的值，不要用const声明常量，因为当const声明的常量-的值发生变化时，会出现报错并无法更改值的问题。
 
- 所以在不考虑兼容性等问题的情况下，大多时候声明变量都是优先选择let进行声明。
### 3.解构赋值
- 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment

```
        {
            //对象结构赋值
            let obj = {
                tcs : 1,
                b : 3,
                c : 5,
                d : 6
            }
            let {tcs,b,d} = obj 
        }
        {
            //数组结构赋值
            let arr = [1,2,3,4,5]
            let[a1,b1] = arr
            let arr1 = [...arr]//arr赋值给arr1
        }

        {
            //快速交换a，b的值
            let a = 2,b = 3;
            [a,b]  = [b,a]
        }
        {
            //字符串解构
            let str = 'a21dedf'
            let [a,b,c] = str
        }
```
### 4.箭头函数
- 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions
```
    <script>
        function fn (a,b){
            return ...
        }

        let fn = (a,b) => {
            return ...
        }

        //简化：
        let fn = () => {
            return ...
        }

         let fn = () => ...
        
        //不定参数
        let fn1 = (a,b,...agr) => {
            console.log(a,b,agr)
        }
        fn1(1,2,3,4,5,6)
    </script>
```
### 5.展开运算符
```
<script>
        {
            //数组展开符
            let arr = [1,2,3,4,5,6] 
            let arr1 = ["a",...arr,'b']
            let [a,b,...c] = arr1
            console.log(c)// [2,3,4,5,6,"b"]
        }
        {
            //对象展开符
            let obj = {
                a : 1,
                b : 2,
                c : 3,
                d : 4
            }
            let obj1 = {
                ...obj,
                a : 5
            }
            console.log(obj1)//{a:5,b:2,c:3,d:4}
        }
  </script>
```
### 6.Set 对象    
- Set 对象的数据结构
- Set 相关属性与方法
- size 属性
- clear()、delete()、get()、has()、add()    
- 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set

### 7.Map 对象
- Map 对象的数据结构
- Map 相关属性与方法
- size 属性
- clear()、delete()、get()、has()、set()
- 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Map

### 8.arr.forEach(callback(),_this)实现原理
##### forEach不能中途退出，this的默认指向是window

```
    forEach(cb,_this){
        for(let i = 0;i < arr.length; i++){
            cb.call(_this,arr[i],i){
                ······//处理操作
            }
        }
    }
```
