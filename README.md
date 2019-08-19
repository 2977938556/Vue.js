# Vue 语法入门
Vue 各种语法 入门讲解

从零开始掌握大型互联网公司NodeJS实际使用

[【视频地址】Vue2.5开发去哪儿网App 从零基础入门到实战项目](https://coding.imooc.com/class/203.html)

课程出品时间：2017.x ~ 2018.4

看视频整理要点笔记：

----

**目录**
- [第2章 Vue 起步](#第1章-导学)
    - [2-2 hello world](#2-2-hello-world)
    - [2-3 开发TodoList（v-model、v-for、v-on）](#2-3-开发todolistv-modelv-forv-on)
    - [2-4 MVVM模式](#2-4-mvvm模式)
    - [2-5 前端组件化](#2-5-前端组件化)
    - [2-6 父组件传值给子组件](#2-6-父组件传值给子组件)
    - [2-7 子组件传值给父组件](#2-7-子组件传值给父组件)
- [第3章 Vue 基础精讲](#第3章-Vue-基础精讲)
    - [3-1 Vue实例](#3-1-Vue实例)
    - [3-2 Vue实例生命周期](#3-2-Vue实例生命周期)
    - [3-3 Vue的模版语法](#3-3-Vue的模版语法)
    - [3-4 计算属性,方法与侦听器](#3-4-计算属性,方法与侦听器)
    - [3-5 计算属性的 getter 和 setter](#3-5-计算属性的-getter-和-setter)
    - [3-6 Vue中的样式绑定](#3-6-Vue中的样式绑定)
    - [3-7 Vue中的条件渲染](#3-7-Vue中的条件渲染)
    - [3-8 Vue中的列表渲染](#3-8-Vue中的列表渲染)
    - [3-9 Vue中的set方法](#3-9-Vue中的set方法)
- [第4章 深入理解 Vue 组件](#第4章-深入理解-Vue-组件)
    - [4-1 使用组件的细节点](#4-1-使用组件的细节点)
        - [is=""]()
        - [子组件的 data，必须是 **函数返回值**]()
        - [ref Vue中如何操作DOM]()
    - [4-2 父子组件间的数据传递](#4-2-父子组件间的数据传递)
        - [4-2-1 父组件 如何向 子组件 传递数据](#4-2-1-父组件-如何向-子组件-传递数据)
        - [单向数据流](#单向数据流)
        - [4-2-2 子组件 如何向 父组件 传递数据](#4-2-2-子组件-如何向-父组件-传递数据)
    - [4-3 组件参数校验与非 props 特性](#4-3-组件参数校验与非-props-特性)
    - [4-4 给组件绑定原生事件](#4-4-给组件绑定原生事件)
    - [4-5 非父子组件间的传值](#4-5-非父子组件间的传值)
    - [4-6 在Vue中使用插槽](#4-6-在Vue中使用插槽)
    - [4-7 作用域插槽](#4-7-作用域插槽)
    - [4-8 动态组件与 v-once 指令](#4-8-动态组件与-v-once-指令)
- [第5章 Vue 中的动画特效](#第5章-Vue-中的动画特效)
    - []()
    - []()
    - []()
    - []()

----


## Vue 和 React 相同点
- 利用虚拟 DOM 实现快速渲染
- 轻量级 (对比 angluar)
- 响应式组件
- 服务器端渲染 - SSR (server side rander)
- 易于集成路由工具，打包工具以及状态管理工具
- 优秀的支持和社区


## 什么是虚拟DOM ?
- 什么是 DOM ？
    - DOM 是文档对象模型
    - 可以简单理解为，存放在磁盘中的文件，如 ```.html``` 文件
- 为什么需要虚拟 DOM ？
    - 在过去，我们做开发，都是直接操作 DOM ？
    - 如：改变节点，名字，改变节点文本
    - 缺点：直接操作 DOM 是 **非常耗费资源、非常昂贵的**
- ### 虚拟 DOM
    - 在 JS 内存里面，构建一个类似于 DOM 的对象
    - 通过 JS 定义一个 Object，用这个 Object 来模拟 DOM，**拼装数据**
    - 拼装完后，把这个整体做一个解析渲染，最后 把这个 Object 一次性的插入到 DOM 里面去
    - 这就形成了一个虚拟 DOM
- 优点
    - 由于基本都在内存中操作，这整个过程是非常快、非常省资源的

## 前端JS框架
- Jquery
    - 主要是针对 DOM 操作的函数库
- 传统的 MVC 框架
    - Model 和 View 解耦
    - Controller 控制 DOM
        - Controller 是核心控制器，一切用户的行为，都会通过 Controller 来进行触发、渲染视图
- 基于 MV* 模式的 Vue 框架
    <!-- - ![MV* 示意图](https://github.com/946629031/Vue.js/blob/master/img/1.jpg) -->
    - Model 绑定 View - (双向数据绑定)
    - 没有控制器概念
    - 数据驱动，状态管理，组件化 (核心思想)
        - 因此，在 MV* 模式下，不会操作 DOM, 不会操作 class
        - 更多的去关注我们的数据，通过改变变量 来控制视图



## 第2章 Vue 起步
- ### 2-2 hello world
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
</head>
<body>
    <div id="app">{{message}}</div>
    <script>
        var app = new Vue({
            el: '#app',
            data: {
                message: 'hello world'
            }
        })

        // 2s后 将'hello world' 改为 'bye world'
        setTimeout(function(){
            app.$data.message = 'bye world'
        }, 2000)
    </script>
</body>
</html>
```

- ### 2-3 开发TodoList（v-model、v-for、v-on）
    - 数据双向绑定
        - 这个案例里
            - v-model='inputValue'，的意思是
            - 将该input 的数据与 Vue实例中 app.$data.inputValue 绑定
        - 只要 该input 值改变，app.$data.inputValue 也会跟着改变
        - 验证方法：
            - 在控制台里app.$data.inputValue = '123...', 则该input 值也同步变成了 '123...'
            - 或者，在该input里输入'666', 则 Vue实例中 app.$data.inputValue 也等于 '666'
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
</head>
<body>
    <div id="app">
        <input type="text" v-model='inputValue'>
        <button v-on:click="handleBtnClick">提交</button>
        <ul>
            <li v-for="item in list">{{item}}</li>
        </ul>
    </div>
    <script>
        var app = new Vue({
            el: '#app',
            data: {
                list: ['第一课内容','第二课内容','2333'],
                inputValue: ''
            },
            methods: {
                handleBtnClick: function(){
                    this.list.push(this.inputValue)
                    this.inputValue = ''
                }
            }
        })
    </script>
</body>
</html>
```

- ### 2-4 MVVM模式
    - 在 MVP / MVC 模式下
        - 名词解释
            - Model - 数据层
            - Control - 控制层
            - View - 视图层
        - 在这种模式下，Control / Presenter 层，其实有大量的代码都是在操作 DOM，而恰好这种直接操作 DOM 的模式，是非常耗费资源的

    <!-- ![vue-mvvm](https://github.com/946629031/Vue.js/blob/master/img/2.vue-mvvm.jpg) -->

    - 在 MVVM 模式下
        - 我们不需要关注 VM 层是怎么实现的，因为这个 Vue 已经帮我们实现了
        - 我们只需要关注，Model 数据层、View 视图层 即可
        - MVVM 这种模式下 最重的一层 是 Model 层
            - 以前，我们使用 jquery 开发时候，我们是面向 DOM 做开发
            - 现在，我们使用 MVVM 这种模式开发的时候，我们是 **面向 Model 数据层 做开发**
    - 在 Vue 中
        - Model - 就是 Vue 实例中的 data
        - View - 就是 html 文件中的 html 结构
        - vue 实例中的 function 都是在对数据进行操作
        - VM 层 - 当数据变化的时候，View 层自动跟着变化，这 VM 层是 Vue 帮我们实现的

- ### 2-5 前端组件化
    <!-- ![美团外卖app](https://github.com/946629031/Vue.js/blob/master/img/3.meituan.jpg) -->

    - 看上面的例子
    - 如果没有组件化，我们需要把这个页面的所有逻辑都写在 这个页面上，如果这个页面的逻辑非常的多，那之后**维护起来就会很困难**
    - **组件化**
        <!-- - ![美团外卖app](https://github.com/946629031/Vue.js/blob/master/img/4.components.png) -->
        - 合理拆分组件，我们可以把一个大型的项目，像拼积木一样拼接起来
        - 一个大型的项目可能非常的复杂，拆分成组件之后，就会变得非常的精巧
        - 每一个组件的**维护就会相对更容易些，降低维护成本**


- ### 2-6 父组件传值给子组件
    - 下面我们 使用组件改造TodoList
    - 在 [2-3](#2-3-开发todolistv-modelv-forv-on) 中，里面的 List 是通过 li 标签来循环的
    - 现在，我们要把 li 标签变成一个组件，来看看应该怎么做
    ```html
    <div id="app">
        <input type="text" v-model='inputValue'>
        <button v-on:click="handleBtnClick">提交</button>
        <ul>
            <!-- <li v-for="item in list">{{item}}</li> -->

            <todo-item v-bind:content="item" v-for="item in list"></todo-item>
        </ul>
    </div>

    <script>
        Vue.component('TodoItem', {
            props: ['content'],
            template: "<li>{{content}}</li>"
        })

        var app = new Vue({
            el: '#app',
            data: {
                list: ['第一课内容','第二课内容','2333'],
                inputValue: ''
            },
            methods: {
                handleBtnClick: function(){
                    this.list.push(this.inputValue)
                    this.inputValue = ''
                }
            }
        })
    </script>
    ```

    - ```Vue.component()``` - 全局组件注册方法
        ```html
        Vue.component('TodoItem', {
            props: ['content'],
            template: "<li>{{content}}</li>"
        })
        ```
    - #### 通过 ```v-bind``` 传递内容给子组件 ( 父组件传值给子组件 )
        - 1.```v-for="item in list"``` list 数组的个数决定循环出多少个 item
        - 2.```v-bind:content="item"``` 将 ```item``` 赋值 给 ```content```
        - 3.在子组件注册的地方，通过 ```props: ['content'],``` 接收 ```content``` 变量
        - 4.最后，在 ```template: "<li>{{content}}</li>"``` 通过插值表达式插入 组件内容中

    - 局部组件注册方法
        - 1.注册局部组件
            ```js
                var TodoItem = {
                    props: ['content'],
                    template: "<li>{{content}}</li>"
                }
            ```
        - 2.在 Vue 实例中，接收该 局部组件
            ```js
            var app = new Vue({
                el: '#app',
                components: {
                    TodoItem: TodoItem
                }
            })
            ```
        ```html
        <div id="app">
            <input type="text" v-model='inputValue'>
            <button v-on:click="handleBtnClick">提交</button>
            <ul>
                <todo-item v-bind:content="item" v-for="item in list"></todo-item>
            </ul>
        </div>

        <script>
            var TodoItem = {
                props: ['content'],
                template: "<li>{{content}}</li>"
            }

            var app = new Vue({
                el: '#app',
                components: {
                    TodoItem: TodoItem
                },
                data: {
                    list: ['第一课内容','第二课内容','2333'],
                    inputValue: ''
                },
                methods: {
                    handleBtnClick: function(){
                        this.list.push(this.inputValue)
                        this.inputValue = ''
                    }
                }
            })
        </script>
        ```

- ### 2-7 子组件传值给父组件
    - [上一节](#通过-v-bind-传递内容给子组件--父组件传值给子组件-)，我们讲解了，父组件如何传值给子组件
    - 那么，子组件如何传值给父组件呢？
    - 我们先来看，如何实现这样的一个功能
        - 在我们点击 TodoList 中的每一项时，就把该项删除掉
        - 这时候，就涉及到 子组件向父组件传值的问题了

    > ```@click="handleBtnClick"``` 是 ```v-on:click="handleBtnClick"``` 的简写<br>
    > ```:content="item"``` 是 ```v-bind:content="item"``` 的简写

    - 数据放在父组件里 ( ```app.$data.list``` )，父组件决定子组件显示多少个
    - 所以删除子组件的时候，我们点击子组件，子组件把绑定的内容传给父组件，让父组件去改变数据，父组件的数据改变了，子组件就会消失
    
    - #### 子组件如何传值给父组件呢？
        - 1.子组件传值，我们可以通过 ```this.$emit("delete")``` 的方式来向外触发事件
            ```js
            var TodoItem = {
                template: "<li>content</li>",
                methods: {
                    handleItemClick: function(){
                        this.$emit('delete', this.index)    // 触发 delete 事件的同时，将 参数 this.index 带出去
                    }
                }
            }
            ```
        - 2.在子组件上，监听 delete 事件， ```<todo-item @delete="handleItemDelete"></todo-item>```
            - 一但监听到 ```delete``` 事件，就会执行父组件里 ```handleItemDelete``` 方法
        - 3.在父组件里定义 handleItemDelete 方法
            ```js
            var app = new Vue({
                el: '#app',
                methods: {
                    handleItemDelete: function(index){
                        this.list.splice(index, 1)
                    }
                }
            })
            ```
    - 完整代码
    ```html
    <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
    <div id="app">
        <input type="text" v-model='inputValue'>
        <button v-on:click="handleBtnClick">提交</button>
        <ul>
            <todo-item v-bind:content="item" 
                        v-bind:index="index"
                        v-for="(item, index) in list" 
                        @delete="handleItemDelete"></todo-item>
        </ul>
    </div>
    <script>
        var TodoItem = {
            props: ['content', 'index'],
            template: "<li @click='handleItemClick'>{{content}}</li>",
            methods: {
                handleItemClick: function(){
                    this.$emit('delete', this.index)    // 触发 delete 事件的同时，将 参数 this.index 带出去
                }
            }
        }

        var app = new Vue({
            el: '#app',
            components: {
                TodoItem: TodoItem
            },
            data: {
                list: ['第一课内容','第二课内容','2333'],
                inputValue: ''
            },
            methods: {
                handleBtnClick: function(){
                    this.list.push(this.inputValue)
                    this.inputValue = ''
                },
                handleItemDelete: function(index){
                    this.list.splice(index, 1)
                }
            }
        })
    </script>
    ```

    
## 第3章 Vue 基础精讲
- ### 3-1 Vue实例
    ```js
    var vm = new Vue({
        el: '#app',
        data: {
            message: 'hello'
        }
    })
    ```
    - ```vm.$data.message```
    - 凡是已 $ 开头的符号，都是指 Vue 实例的 **实例属性/实例方法**

- ### 3-2 Vue实例生命周期
    <!-- ![lifecycle](https://github.com/946629031/Vue.js/blob/master/img/5.lifecycle.jpg) -->
    - 生命周期函数，就是 Vue 实例在某一个时间点会自动执行的函数
    ```html
    <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
    <div id="app"></div>
    <script>
        var vm = new Vue({
            el: '#app',
            template: '<div>{{message}}</div>',
            data: {
                message: 'hello world'
            },
            beforeCreate: function(){
                console.log('beforeCreate')
            },
            created: function(){
                console.log('created')
            },
            beforeMount: function(){
                console.log(this.$el)
                console.log('beforeMount')
            },
            mounted: function(){
                console.log(this.$el)
                console.log('mounted')
            },
            beforeDestroy: function(){          // vm.$destroy()
                console.log('beforeDestroy')
            },
            destroyed: function(){
                console.log('destroyed')
            },
            beforeUpdate: function(){           // 当改变 vm.$data 里面的数据时
                console.log('beforeUpdate')
            },
            updated: function(){
                console.log('updated')
            }
        })
    </script>
    ```

- ### 3-3 Vue的模版语法
    ```html
    <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

    <div id="app">
        {{msg}}
        <div v-text='msg'></div>
        <div v-html='msg'></div>
    </div>
    <script>
        var vm = new Vue({
            el: '#app',
            data: {
                msg: '<h1>Dell</h1>'
            }
        })
    </script>
    ```
    - 执行结果
    <!-- ![Vue的模版语法](https://github.com/946629031/Vue.js/blob/master/img/3-3.jpg) -->
    - 凡是 像 ```v-text='msg'```  ```v-html='msg'``` 以 v-什么 开头的指令，后面引号内都是 跟JS表达式


- ### 3-4 计算属性,方法与侦听器
    - 需求：根据给定的元数据 ```firstName, lastName```，在页面中自动生成 ```fullName``` ( fullName = firstName + lastName)。并且，如果元数据改变，fullName 也跟着改变

    - 实现方法一
        ```html
        <div id="app">
            {{firstName + ' ' + lastName}}
        </div>
        <script>
            var vm = new Vue({
                el: '#app',
                data: {
                    firstName: 'Dell',
                    lastName: 'Lee'
                }
            })
        </script>
        ```
        - 分析：这种方式虽然能实现，但是，在你的模板里面却包含了逻辑，一般情况下，我们不希望在模版里面 写表达式，而是直接展示结果就好
    - 实现方法二 - computed
        ```html
        <div id="app">
            {{fullName}}
        </div>
        <script>
            var vm = new Vue({
                el: '#app',
                data: {
                    firstName: 'Dell',
                    lastName: 'Lee'
                },
                // 计算属性
                computed: {
                    fullName: function(){
                        return this.firstName + ' ' + this.lastName
                    }
                }
            })
        </script>
        ```
        - #### 计算属性缓存
            - computed 计算属性 是有缓存的，只要他依赖的变量不改变，系统就会一直用他已经计算好的缓存，来提高性能
    - 实现方法三 - methods
        ```html
        <div id="app">
            {{fullName()}}
            {{age}}
        </div>
        <script>
            var vm = new Vue({
                el: '#app',
                data: {
                    firstName: 'Dell',
                    lastName: 'Lee',
                    age: 27
                },
                methods: {
                    fullName: function(){
                        console.log('计算了一次')
                        return this.firstName + ' ' + this.lastName
                    }
                }
            })
        </script>
        ```
        - 分析：这种方式虽然也能实现需求，但是这种方式是没有缓存的，如果我改变 ```age: 27``` 页面被重新渲染，则 methods 也被重新执行了一次，而不是像 computed 一样继续读取缓存
        - **很明显 methods 的方法实现，没有 computed 的性能好**

    - 实现方法四 - watch
        ```html
        <div id="app">
            {{fullName}}
            {{age}}
        </div>
        <script>
            var vm = new Vue({
                el: '#app',
                data: {
                    firstName: 'Dell',
                    lastName: 'Lee',
                    fullName: 'Dell Lee',
                    age: 27
                },
                watch: {
                    firstName: function(){
                        console.log('计算了一次')
                        this.fullName = this.firstName + ' ' + this.lastName
                    },
                    lastName: function(){
                        console.log('计算了一次')
                        this.fullName = this.firstName + ' ' + this.lastName
                    }
                }
            })
        </script>
        ```
        - 分析：虽然 watch 这种方式也能实现需求，但是却造成了代码冗余，所以还是 computed 比较好
    - 总结：如果一个功能，可以通过 watch, methods, computed 这三种方法实现，那么优先使用 computed 来实现

- ### 3-5 计算属性的 getter 和 setter
    - 计算属性默认只有 getter 
        - 默认写法
            ```js
            var vm = new Vue({
                el: '#app',
                data: {
                    firstName: 'Dell',
                    lastName: 'Lee'
                },
                computed: {
                    fullName: function(){
                        return this.firstName + ' ' + this.lastName
                    }
                }
            })
            ```
        - 完整写法
            ```js
            var vm = new Vue({
                el: '#app',
                data: {
                    firstName: 'Dell',
                    lastName: 'Lee'
                },
                computed: {
                    fullName: {
                        // getter
                        get: function(){
                            return this.firstName + ' ' + this.lastName
                        }
                    }
                }
            })
            ```
        - 这两种写法是完全一模一样的
    - 计算属性中的 setter
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

        <div id="app">
            {{fullName}}
        </div>
        <script>
            var vm = new Vue({
                el: '#app',
                data: {
                    firstName: 'Dell',
                    lastName: 'Lee'
                },
                computed: {
                    fullName: {
                        // getter 当读取 fullName值 的时候，执行 getter function
                        get: function(){
                            return this.firstName + ' ' + this.lastName
                        },
                        // setter 当设置 fullName值 的时候，执行 setter function
                        set: function(value){
                            let arr = value.split(' ');
                            this.firstName = arr[0];
                            this.lastName = arr[1];
                        }
                    }
                }
            })
        </script>
        ```
        - 当改变 fullName ( vm.fullName = 'Mike Wang' ), 即执行 setter function 时
        - setter function 里的 ```this.firstName``` 和 ```this.lastName``` 都被改变了
        - 而 firstName 和 lastName 又是 getter funciton 的依赖变量
        - 所以，引发了 getter function 重新执行，更新缓存
        - 最后，得到的结果重新渲染到页面上

- ### 3-6 Vue中的样式绑定
    - Vue 中如何绑定 class?
        - 需求：点击一下 toggle 字体颜色
    - #### 绑定方式一 - 对象语法
        ```html
        <style> .red{ color: red;} </style>
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
    
        <div id="app">
            <div v-bind:class="{red: isActivated}" @click="handleClick">hello</div>
        </div>
        <script>
            var app = new Vue({
                el: '#app',
                data: {
                    isActivated: false
                },
                methods: {
                    handleClick: function(){
                        this.isActivated = !this.isActivated
                    }
                }
            })
        </script>
        ```
        - 绑定class
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
        
        <div id="app">
            <div v-bind:class="{}">hello</div>
        </div>
        <script>
            var app = new Vue({
                el: '#app'
            })
        </script>
        ```
    <!-- ![绑定 class](https://github.com/946629031/Vue.js/blob/master/img/6.bind_class.jpg) -->
    - #### 绑定方式二 - 数组语法
        ```html
        <style> .activated{ color: red;} </style>
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
    
        <div id="app">
            <div v-bind:class="[activated, bold]" @click="handleClick">hello</div>
        </div>
        <script>
            var app = new Vue({
                el: '#app',
                data: {
                    activated: '',
                    bold: 'bold'
                },
                methods: {
                    handleClick: function(){
                        this.activated = this.activated === 'activated' ? '' : 'activated'
                    }
                }
            })
        </script>
        ```
    - #### 绑定方式三 - 绑定内联样式 style - 对象语法
        ```html
        <style> .activated{ color: red;} </style>
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
    
        <div id="app">
            <div v-bind:style="styleObj" @click="handleClick">hello</div>
        </div>
        <script>
            var app = new Vue({
                el: '#app',
                data: {
                    styleObj: {
                        color: 'black',
                        display: 'block'
                    }
                },
                methods: {
                    handleClick: function(){
                        this.styleObj.color = this.styleObj.color === 'red' ? 'black' : 'red'
                    }
                }
            })
        </script>
        ```
    - #### 绑定方式四 - 绑定内联样式 style - 数组语法
        ```html
        <style> .activated{ color: red;} </style>
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
        
        <div id="app">
            <div v-bind:style="[styleObj, {fontSize: '20px'}]" @click="handleClick">hello</div>
        </div>
        <script>
            var app = new Vue({
                el: '#app',
                data: {
                    styleObj: {
                        color: 'black',
                        display: 'block'
                    }
                },
                methods: {
                    handleClick: function(){
                        this.styleObj.color = this.styleObj.color === 'red' ? 'black' : 'red'
                    }
                }
            })
        </script>
        ```
        - 注意： v-bind:style="[styleObj, {fontSize: '20px'}]"
        - 由于这里不能写：{font-size: '20px'}
        - 所以 要写成：{fontSize: '20px'}

- ### 3-7 Vue中的条件渲染
    - 条件渲染 v-if
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
        
        <div id="app">
            <div v-if="show">{{message}}</div>
        </div>
        <script>
            var app = new Vue({
                el: '#app',
                data: {
                    show: false,
                    message: 'hello world'
                }
            })
        </script>
        ```
        - 这里，```<div v-if="show">{{message}}</div>``` 这个标签的渲染与否，是由 ```show``` 决定的
            - ```show: false``` 为不渲染
            - ```show: true``` 为渲染

    - 条件渲染 v-show
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
    
        <div id="app">
            <div v-if="show" data-test="v-if">{{message}}</div>
            <div v-show="show" data-test="v-show">{{message}}</div>
        </div>
        <script>
            var app = new Vue({
                el: '#app',
                data: {
                    show: false,
                    message: 'hello world'
                }
            })
        </script>
        ```
    - 总结：
        - ```v-if``` 和 ```v-show``` 都能控制元素是否显示
        - 但是，```v-if``` 为 false 时，该标签压根不存在于 DOM 之上了
        - 而，```v-show``` 为 false 时，该标签存在于 DOM 之上，只是 ```display: none;``` 了而已
        - 而且，```v-show``` 的性能更优，因为 ```v-if``` 是直接操作 DOM 的

    - 条件渲染 v-if v-else-if v-else
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
        
        <div id="app">
            <div v-if="show === 'a'">This is A</div>
            <div v-else-if="show === 'b'">This is B</div>
            <div v-else>This is Others</div>
        </div>
        <script>
            var app = new Vue({
                el: '#app',
                data: {
                    show: 'a'
                }
            })
        </script>
        ```
    - Vue 中的key值
        - 用 key 管理可复用的元素
        - Vue 会尽可能高效地渲染元素，通常会复用已有元素而不是从头开始渲染。
        - 存在的问题：
            ```html
            <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
    
            <div id="app">
                <div v-if="show">
                    用户名：<input />
                </div>
                <div v-else>
                    邮箱名：<input />
                </div>
            </div>
            <script>
                var app = new Vue({
                    el: '#app',
                    data: {
                        show: true
                    }
                })
            </script>
            ```
            - 如上面这个例子，当我们 在 input 中输入内容，如 "123" 时
            - 我们将 ```app.show = false``` 改为了 false 时，我们的预期：显示 v-else 的内容，并清空 input 框
            - 但是，我们实际得到的结果：显示了 "邮箱名："，但是 input 框没有清空
            - 那么，如果解决这个问题呢？
        - 解决问题
            ```html
            <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
    
            <div id="app">
                <div v-if="show">
                    用户名：<input key="username"/>
                </div>
                <div v-else>
                    邮箱名：<input key="password"/>
                </div>
            </div>
            <script>
                var app = new Vue({
                    el: '#app',
                    data: {
                        show: true
                    }
                })
            </script>
            ```
            - 当你给 **标签** 加上 **key值** 后
            - vue 就会对比 key值 是否相同，只有相同的 key值 的标签，才会被复用
            - tips: key值 的内容可以随便取
- ### 3-8 Vue中的列表渲染
    - 1.在使用 key值 的时候，每个循环项上最好都带一个 key值，来提高性能
        - 如何性能能达到最优呢？
            - **key值 要唯一，同时不要使用 index 作为 key值**
            - 虽然使用 index 昨晚 key值，也不会报错，但是性能没有那么好
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
        
        <div id="app">
            <div v-for="(item, index) of list" :key="item.id">
                {{item.text}} --- {{index}}
            </div>
        </div>
        <script>
            var app = new Vue({
                el: '#app',
                data: {
                    list: [{
                            id: '231123',
                            text: 'hello'
                        },{
                            id: '231124',
                            text: 'Dell'
                        },{
                            id: '231125',
                            text: 'Lee'
                        }
                    ]
                }
            })
        </script>
        ```
    - 2.数组的变异方法
        - 不能通过下标的方式来改变数组内容，这样不会更新到页面上
            - 如：```app.list[4] = {id: '001', text: '2'}```
        - 要通过 **数组变异方法** 来改变数组内容，这样才能更新到页面上
            - 如：```app.list.push({id: '001', text: '2'})```
            - **数组变异方法**：push, pop, shift, unshift, splice, sort, reverse
    - 3.除了通过数组变异方法 可以改变页面上的内容，还可以通过**改变数组的引用**，来更新页面上的内容
        - 改变数组的引用 即 重新赋值
        - 如：
            ```js
            app.list = [{
                            id: '231123',
                            text: 'hello'
                        },{
                            id: '2311241111',
                            text: 'Dellxxxxx'
                        },{
                            id: '231125',
                            text: 'Lee'
                        }
                    ]
            ```
    - 4.循环中的 template 占位符
        - 先看存在的问题
            ```html
            <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
    
            <div id="app">
                <div v-for="(item, index) of list" :key="item.id">
                    <div>
                        {{item.text}} --- {{index}}
                    </div>
                    <span>{{item.text}}</span>
                </div>
            </div>
            <script>
                var app = new Vue({
                    el: '#app',
                    data: {
                        list: [{
                                id: '231123',
                                text: 'hello'
                            },{
                                id: '231124',
                                text: 'Dell'
                            },{
                                id: '231125',
                                text: 'Lee'
                            }
                        ]
                    }
                })
            </script>
            ```
        <!-- - 渲染结果 ![循环中的 template 占位符](https://github.com/946629031/Vue.js/blob/master/img/7.v-for_template.jpg) -->
        - 渲染结果，每个循环项里，都被一个 div 标签包裹着
        - 但是，如果我不希望，循环项被这一个多余的标签包裹着，怎么办呢？
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
        
        <div id="app">
            <template v-for="(item, index) of list" :key="item.id">
                <div>
                    {{item.text}} --- {{index}}
                </div>
                <span>{{item.text}}</span>
            </template>
        </div>
        <script>
            var app = new Vue({
                el: '#app',
                data: {
                    list: [{
                            id: '231123',
                            text: 'hello'
                        },{
                            id: '231124',
                            text: 'Dell'
                        },{
                            id: '231125',
                            text: 'Lee'
                        }
                    ]
                }
            })
        </script>
        ```
        <!-- - 渲染结果 ![循环中的 template 占位符](https://github.com/946629031/Vue.js/blob/master/img/8.v-for_template.jpg) -->
        - 把包裹的 div 改成 template 即可，其中 template 只是占位符，不会被渲染到页面上
    - 5.对象循环
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
        
        <div id="app">
            <div v-for="(item, key, index) of userInfo">
                {{item}} -- {{key}} -- {{index}}
            </div>
        </div>
        <script>
            var app = new Vue({
                el: '#app',
                data: {
                    userInfo: {
                        name: "Dell",
                        age: 28,
                        gander: "male",
                        salary: "secret"
                    }
                }
            })
        </script>
        ```
        - 1.修改对象已有的信息，```app.userInfo.name = 'Dell Lee'```, 这种方法是可以修改的
        - 2.新增对象内容
            - ```app.userInfo.address = 'Beijing'```, 这种方法虽然不会报错，但是新增内容没有被更新到页面上
            - 通过修改对象的引用 - 重新赋值
                ```js
                app.userInfo = {
                        name: "Dell",
                        age: 28,
                        gander: "male",
                        salary: "secret",
                        address: "Beijing"
                    }
                ```
                - 通过重新赋值的方法，会被自动更新到页面上
        
- ### 3-9 Vue中的set方法
    - #### 1.对象的 set方法
        - 存在的问题
            - 在上一节[3-8 Vue中的列表渲染](#3-8-Vue中的列表渲染) 中, 我们提到，如果要修改 Object 对象的内容，只能通过 重新赋值 (修改引用) 的方法
            - 其实，还可以通过 ```Vue.set()``` 方法，来修改 Object 对象的内容
        - ```Vue.set()``` 例子
            ```html
            <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
            
            <div id="app">
                <div v-for="(item, key, index) of userInfo">
                    {{item}} -- {{key}} -- {{index}}
                </div>
            </div>
            <script>
                var app = new Vue({
                    el: '#app',
                    data: {
                        userInfo: {
                            name: "Dell",
                            age: 28,
                            gander: "male",
                            salary: "secret"
                        }
                    }
                })
            </script>
            ```
        - ```Vue.set()``` 全局方法
            - 然后在 控制台里输入 ```Vue.set(app.userInfo, 'address', 'beijing')```
            - 对象内容新增成功，页面也同时更新
        - ```app.$set()``` 实例方法
            - ```app.$set(app.userInfo, 'address', 'beijing')```
            - 对象内容新增成功，页面也同时更新
            - ```Vue.set()``` 和 ```app.$set()``` 是完全一模一样的
    
    - #### 2.数组的 set方法
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
    
        <div id="app">
            <div v-for="(item, index) of userInfo">
                {{item}}
            </div>
        </div>
        <script>
            var app = new Vue({
                el: '#app',
                data: {
                    userInfo: [0,1,2,3,4]
                }
            })
        </script>
        ```
        - ```app.$set(app.userInfo, 1, 5)```, 实例方法
            - 数组内容新增成功，页面也同时更新  
        - ```Vue.set(app.userInfo, 1, 5)```, 全局方法
            - 数组内容新增成功，页面也同时更新

## 第4章 深入理解 Vue 组件
- ### 4-1 使用组件的细节点
    - #### 4-1-1 问题1 - is=""
        - 1.存在问题
            ```html
            <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
        
            <div id="app">
                <table>
                    <tbody>
                        <row></row>
                        <row></row>
                        <row></row>
                    </tbody>
                </table>
            </div>
            <script>
                Vue.component('row', {
                    template: '<tr><td>this is a row</td></tr>'
                })

                var vm = new Vue({
                    el: '#app'
                })
            </script>
            ```
            <!-- - ![存在问题](https://github.com/946629031/Vue.js/blob/master/img/9.Component_problems.jpg) -->

            - 原本我们的预期：row子组件，被包含于 tbody 中
            - 但是我们得到的：row子组件，跑到 tbody 外面去了
        - 2.如何解决这个问题？ is=""
            - H5规范 规定，tbody 里只能写 tr
            - 然后，我们使用 ```is="row"``` 使其绑定 子组件即可
            ```html
            <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>
        
            <div id="app">
                <table>
                    <tbody>
                        <tr is="row"></tr>
                        <tr is="row"></tr>
                        <tr is="row"></tr>
                    </tbody>
                </table>
            </div>
            <script>
                Vue.component('row', {
                    template: '<tr><td>this is a row</td></tr>'
                })

                var vm = new Vue({
                    el: '#app'
                })
            </script>
            ```
            <!-- - ![存在问题](https://github.com/946629031/Vue.js/blob/master/img/9-1.Component_problems.jpg) -->
            - 同理，以下标签 里面，如果要放子组件，也是同理
                ```html
                <ul>
                    <li is="row"></li>
                    <li is="row"></li>
                    <li is="row"></li>
                </ul>
                ```
                ```html
                <ol>
                    <li is="row"></li>
                    <li is="row"></li>
                    <li is="row"></li>
                </ol>
                ```
                ```html
                <select>
                    <option is="row"></option>
                    <option is="row"></option>
                    <option is="row"></option>
                </select>
                ```
    - #### 4-1-2 问题2 - 子组件的 data，必须是 **函数返回值**
        - 1.先看代码
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

        <div id="app">
            <table>
                <tbody>
                    <tr is="row"></tr>
                    <tr is="row"></tr>
                    <tr is="row"></tr>
                </tbody>
            </table>
        </div>
        <script>
            Vue.component('row', {
                data: {
                    content: 'this is a row'
                },
                template: '<tr><td>{{content}}</td></tr>'
            })

            var vm = new Vue({
                el: '#app'
            })
        </script>
        ```
        - 2.报错 ```[Vue warn]: The "data" option should be a function that returns a per-instance value in component definitions.```
            - data 应该是一个 function 
            - 而不是
                ```js
                Vue.component('row', {
                    data: {
                        content: 'this is a row'
                    },
                    template: '<tr><td>{{content}}</td></tr>'
                })
                ```
        - 3.原因
            - 1.在根组件里 ```new Vue({})``` , 如果定义 ```data: {}``` 这样不会任何的问题
            - 2.但是，如果你在非根组件 ( 子组件 ) 里，定义 data 时，就不能这样定义了。子组件里定义 data 时，要求data 必须是 **函数的返回值**
                ```js
                Vue.component('row', {
                    data: function(){
                        return {
                            content: 'this is a row'
                        }
                    },
                    template: '<tr><td>{{content}}</td></tr>'
                })
                ```
            - 3.之所以这么设计，是因为
                - 一个子组件 不会像 根组件只会被调用一次，子组件可能会被调用多次。
                - 那么，每一个子组件的数据，我不希望他 和其他子组件产生冲突, 希望他是**独立的数据**
                - 通过 **函数返回值** 的方式，就可以做到，每个子组件拥有独立的数据存储
        - 4.正确的完整代码
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

        <div id="app">
            <table>
                <tbody>
                    <tr is="row"></tr>
                    <tr is="row"></tr>
                    <tr is="row"></tr>
                </tbody>
            </table>
        </div>
        <script>
            Vue.component('row', {
                data: function(){
                    return {
                        content: 'this is a row'
                    }
                },
                template: '<tr><td>{{content}}</td></tr>'
            })

            var vm = new Vue({
                el: '#app'
            })
        </script>
        ```
    - #### 4-1-3 问题3 - ref Vue中如何操作DOM
        - 存在的问题：单靠Vue中的数据绑定这种方式，在某些及其复杂的情况下，是处理不了的。所以，在有些必要的情况下仍然需要操作DOM
        - 1.先看一段代码
            ```html
            <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

            <div id="app">
                <div ref='hello' @click='handleClick'>hello world</div>
            </div>
            <script>
                var vm = new Vue({
                    el: '#app',
                    methods: {
                        handleClick: function(){
                            console.log(this.$refs.hello.innerHTML)
                        }
                    }
                })
            </script>
            ```
            - ref 引用
                - 给该标签，起一个引用的名字，叫做 'hello'
                - ```this.$refs``` 指的是 Vue实例 中所有的引用
                - ```this.$refs.hello``` 获得 名叫 'hello' 的DOM节点
                    - 如果 ref 写在组件上，如 ```<com ref='demo'></com>```，则是获取组件的引用
        - 2.案例2
            - 需求：实现一个计数器，每点击一次 i++，然后把所有的计数器实时计算总和
            ```html
            <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

            <div id="app">
                <counter ref='one' @change='handleChange'></counter>
                <counter ref='two' @change='handleChange'></counter>
                <div>{{total}}</div>
            </div>
            <script>
                Vue.component('counter', {
                    data: function(){
                        return {
                            number: 0
                        }
                    },
                    template: '<div @click="handle">{{number}}</div>',
                    methods: {
                        handle: function(){
                            this.number++;
                            this.$emit('change')
                        }
                    }
                })

                var vm = new Vue({
                    el: '#app',
                    data: {
                        total: 0
                    },
                    methods: {
                        handleChange: function(){
                            this.total = this.$refs.one.number + this.$refs.two.number
                        }
                    }
                })
            </script>
            ```
- ### 4-2 父子组件间的数据传递
    - 现在我们继续实现一个需求：
        - 实现一个计数器，每点击一次 i++，然后把所有的计数器实时计算总和
    - #### 4-2-1 父组件 如何向 子组件 传递数据
        - ##### 父组件通过属性的方式，向子组件传递数据
            - 这种方式传递给子组件的 0 或 1 会变成一个 **字符串**
                ```html
                <div id="app">
                    <counter count='0'></counter>
                    <counter count='1'></counter>
                </div>
                ```

            - 这种方式传递给子组件的 0 或 1 会变成一个 **数字**
                - 加了 : 冒号后，引号里面的内容就变成 **js表达式** 了，而不是一个字符串了
                ```html
                <div id="app">
                    <counter :count='0'></counter>
                    <counter :count='1'></counter>
                </div>
                ```
        - ##### 然后 子组件 通过 props 接收数据
            ```html
            <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

            <div id="app">
                <counter count='2'></counter>
                <counter count='1'></counter>
            </div>
            <script>
                let counter = {
                    props: ['count'],
                    template: '<div>{{count}}</div>'
                }

                var vm = new Vue({
                    el: '#app',
                    components: {
                        counter: counter
                    }
                })
            </script>
            ```
        - ##### 单向数据流
            - 先看问题
                ```html
                <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

                <div id="app">
                    <counter count='2'></counter>
                    <counter count='1'></counter>
                </div>
                <script>
                    let counter = {
                        props: ['count'],
                        template: '<div @click="handleClick">{{count}}</div>',
                        methods: {
                            handleClick: function(){
                                this.count ++
                            }
                        }
                    }

                    var vm = new Vue({
                        el: '#app',
                        components: {
                            counter: counter
                        }
                    })
                </script>
                ```
            - 这样写，虽然能实现点击就 i++ 的功能，但是 控制台会报错
                - [Vue warn]: Avoid mutating a prop directly since the value will be overwritten whenever the parent component re-renders. Instead, use a data or computed property based on the prop's value. Prop being mutated: "count"
                - 意思是说，你**子组件 不要直接修改 父组件传递过来的数据**
                - 因为，如果父组件传递过来的 是非基础类型的数据，而是引用类型的数据，如 {}
                    - 你在子组件里改变了数据的内容，而这个数据有可能 被其他子组件所使用
                    - 这样的话，你的修改 不仅影响了你自己，还有可能影响其他 子组件
                - 那我们又确实要改变 父组件传过来的数据，改怎么办呢？
                    - 在子组件里，写个变量 接收一下
                ```html
                <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

                <div id="app">
                    <counter count='2'></counter>
                    <counter count='1'></counter>
                </div>
                <script>
                    let counter = {
                        props: ['count'],
                        data: function(){
                            return {
                                number: this.count  // 写个变量 接收一下 父组件传过来的数据
                            }
                        },
                        template: '<div @click="handleClick">{{number}}</div>',
                        methods: {
                            handleClick: function(){
                                this.number ++
                            }
                        }
                    }

                    var vm = new Vue({
                        el: '#app',
                        components: {
                            counter: counter
                        }
                    })
                </script>
                ```
    - #### 4-2-2 子组件 如何向 父组件 传递数据
        - 1.子组件向外触发事件的方式，向外传递数据
            ```js
            this.$emit('change', 2)    // 向外触发一个change事件，并且可以携带多个参数
            ```
        - 2.父组件监听该事件
            ```html
            <div id="app">
                <counter count='2' @change='handleChange'></counter>
                <counter count='1'></counter>
            </div>
            ```
            - 一但监听到 change 事件，我就执行 handleChange 方法
        - 3.在父组件里 接收参数
            ```js
            methods: {
                handleChange: function(number){
                    console.log(number)
                }
            }
            ```
        - 完整代码
            ```html
            <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

            <div id="app">
                <counter count='0' @change='handleChange'></counter>
                <counter count='0' @change='handleChange'></counter>
                <div>{{total}}</div>
            </div>
            <script>
                let counter = {
                    props: ['count'],
                    data: function(){
                        return {
                            number: this.count
                        }
                    },
                    template: '<div @click="handleClick">{{number}}</div>',
                    methods: {
                        handleClick: function(){
                            this.number ++;
                            this.$emit('change', 1, this.number)    // 向外触发一个change事件，并且可以携带多个参数
                        }
                    }
                }

                var vm = new Vue({
                    el: '#app',
                    data: {
                        total: 0
                    },
                    components: {
                        counter: counter
                    },
                    methods: {
                        handleChange: function(step, number){
                            this.total += step
                            console.log(number)
                        }
                    }
                })
            </script>
            ```
- ### 4-3 组件参数校验与非 props 特性
    - 1.组件参数校验
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

        <div id="app">
            <child parent-msg='hello world'></child>
        </div>
        <script>
            Vue.component('child', {
                props: {
                    parentMsg: null,	// null 代表不验证类别
                    propA: Number,	  // 限定数字
                    propB: [String, Number],	// 多重条件可用 [] 隔开
                    propC: {
                        type: String,
                        require: true	// 为true时，意思是必须要传，不传就报错
                    },
                    propD: {
                        // 数字类型，且有预设值
                        type: Number,
                        default: 100
                    },
                    propE: {
                        // Object 类型，代表可接受的是对象或者数组
                        type: Object,
                        default: function(){
                            return {
                                message: 'hello'
                            }
                        }
                    },
                    propF: {
                        // 自定义的条件验证
                        validator: function(value){
                            return value > 10
                        }
                    }
                },
                template: '<div>{{parentMsg}}</div>'
            })

            var vm = new Vue({
                el: '#app',
            })
        </script>
        ```
    - 2.非 props 特性
        - #### 什么是 props 特性？
            ```html
            <div id="app">
                <child content='hello world'></child>
            </div>
            <script>
                Vue.component('child', {
                    props: ['content'],
                    template: '<div>{{content}}</div>'
                })

                var vm = new Vue({
                    el: '#app'
                })
            </script>
            ```
            - 1.props 特性1 - 不显示在 DOM 上
                - 1.你在 html 中写了 ```content='hello world'```
                - 2.但是，由于你在子组件上 props 接收了 content
                - 3.所以， ```content='hello world'``` 不会在最终渲染完后 显示在　DOM 上
            - 2.props 特性2
                - 当你 ```props: ['content']``` 接收了 content 以后
                - 你就可以直接在 ```template: '<div>{{content}}</div>'``` 中使用该值了
        - #### 什么是 非 props 特性？
            ```html
            <div id="app">
                <child content='hello world'></child>
            </div>
            <script>
                Vue.component('child', {
                    // props: ['content'],
                    template: '<div>{{content}}</div>'
                })

                var vm = new Vue({
                    el: '#app'
                })
            </script>
            ```
            - 当你父组件传递属性 ```content='hello world'``` 的时候
            - 你没有用 ```props: ['content']``` 去接收
            - 非 props 特性1：
                - 这时候，```content='hello world'``` 就会被渲染显示在  最终的 DOM 上
            - 非 props 特性2：
                - 而且，在 ```template: '<div>{{content}}</div>'``` 这里也没法用，因为没有接收
                
- ### 4-4 给组件绑定原生事件
    - 存在的问题
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

        <div id="app">
            <div @click='clickx'>div</div>
            <child @click='clickx'></child>
        </div>
        <script>
            Vue.component('child', {
                template: '<div>child</div>'
            })

            var vm = new Vue({
                el: '#app',
                methods: {
                    clickx: function(){
                        alert(12)
                    }
                }
            })
        </script>
        ```
        - 执行代码发现
            - 绑在原生节点上的 ```<div @click='clickx'>div</div>``` 事件可以被正常触发
            - 但是，同一个事件，绑在组件上 却**不能触发**
    - 分析
        - 当我给组件绑定一个事件的时候，```<child @click='clickx'></child>```，这个 click 实际上是一个自定义的事件
        - 如果你要触发 组件上的自定义事件，就要这样
            - 1.先触发子组件的 div 上的 ```@click="handleChildClick"``` 事件 
            - 2.handleChildClick 再去向外触发这个自定义的 click 事件 ```this.$emit('click')```
            ```html
            <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

            <div id="app">
                <div @click='clickxx'>div</div>
                <child @click='clickxx'></child>
            </div>
            <script>
                Vue.component('child', {
                    template: '<div @click="handleChildClick">child</div>',
                    methods: {
                        handleChildClick: function(){
                            alert('handleChildClick')
                            this.$emit('click')
                        }
                    }
                })

                var vm = new Vue({
                    el: '#app',
                    methods: {
                        clickxx: function(){
                            alert(12)
                        }
                    }
                })
            </script>
            ```
    - #### 总结 - 给组件绑定原生事件
        - 你会发现，用上面的方法来实现该功能，会显得非常复杂
        - 所以，我们要用更简洁的方法， **给组件绑定原生事件**
        - 给绑在组件上的原生事件后，加个 ```.native``` 即可
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

        <div id="app">
            <div @click='clickx'>div</div>
            <child @click.native='clickx'></child>
        </div>
        <script>
            Vue.component('child', {
                template: '<div>child</div>'
            })

            var vm = new Vue({
                el: '#app',
                methods: {
                    clickx: function(){
                        alert(12)
                    }
                }
            })
        </script>
        ```
- ### 4-5 非父子组件间的传值
    - 存在的问题
    <!-- - ![非父子组件间的传值](https://github.com/946629031/Vue.js/blob/master/img/4-5.jpg) -->
    - 如上图所示
        - 根据我们前面学习的内容，父子组件间传值，是可以实现的
            - 父传子，通过 ```props```
            - 子传父，通过 ```this.$emit()```
        - 但是，如果我们要实现 ```1 跟 3``` 或者 ```3 跟 3``` 之间的传值，该怎么办呢？
            - 显然，如果通过一层层往上传，然后再一层层往下传，这种方式虽然可以实现，但是非常复杂，这不是个好的解决方案
    - 解决方法
        - 1.借助 Vuex
        - 2.发布订阅模式 ( Bus / 总线机制 / 观察者模式 )
    - 解决方法 - Bus
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

        <div id="app">
            <child content='Dell'></child>
            <child content='Lee'></child>
        </div>
        <script>
            Vue.component('child', {
                props: {
                    content: String
                },
                template: '<div>{{content}}</div>'
            })

            var vm = new Vue({
                el: '#app',
                methods: {
                    clickxx: function(){
                        alert(12)
                    }
                }
            })
        </script>
        ```
        - 看上面的代码，如何才能实现这样一个功能？
            - 当我点击 Dell 的时候，其他的都变成 Dell
            - 当我点击 Lee 的时候，其他的都变成 Lee
        - 分析
            - 如果要实现这个功能，那么就意味着，他们之间不是 父子组件的关系，而是兄弟组件的关系
            - 如何才能实现，非父子组件间的传值问题呢？
        - 1.```Vue.prototype.bus = new Vue()```
            - 第一步，我先创建一个 vue实例，然后挂载到 Vue 这个类的 prototype 上，并且取名为 bus
                - 这样做的话，后面，不管我使用哪一个 vue实例，上面都会有 bus 这个属性
        - 2.在子组件上绑定点击事件
            ```js
            template: '<div @click="handleClick">{{content}}</div>',
			methods: {
				handleClick: function(){
					alert(this.content)
				}
			}
            ```
        - 3.接下来，我要把我的内容，传递给另外一个组件，该怎么传？
            - ```this.bus.$emit('change', this.content)```
            - 在自己这个组件上，向自己 vue实例 的bus 上触发 change事件，并且带去一个 this.content 参数
            ```js
            template: '<div @click="handleClick">{{content}}</div>',
			methods: {
				handleClick: function(){
					this.bus.$emit('change', this.content)
				}
			}
            ```
        - 4.我这个组件触发事件，另外的组件是不是应该监听呀？
            - 监听事件
            ```js
            mounted: function(){
				this.bus.$on('change', function(msg){
					alert(msg)
				})
			}
            ```
            - 到当前这一步的完整代码
            ```html
            <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

            <div id="app">
                <child content='Dell'></child>
                <child content='Lee'></child>
            </div>
            <script>
                Vue.prototype.bus = new Vue()

                Vue.component('child', {
                    props: {
                        content: String
                    },
                    template: '<div @click="handleClick">{{content}}</div>',
                    methods: {
                        handleClick: function(){
                            this.bus.$emit('change', this.content)
                        }
                    },
                    mounted: function(){
                        this.bus.$on('change', function(msg){
                            alert(msg)
                        })
                    }
                })

                var vm = new Vue({
                    el: '#app'
                })
            </script>
            ```
            - 当你点击子组件的时候，之所以 ```alert(msg)``` 被弹出两次，是因为有两个组件都在监听
        - 5.第五步，监听并接收到 msg 后，是不是应该 把自己的内容都改成 msg 呢？
            ```js
            mounted: function(){
				this.bus.$on('change', function(msg){
					this.content = msg  // 如果你这样写
				})
			}
            ```
            - 如果你这样写，你会发现，你修改不了
            - 原因：function 里面的 this 作用域发生了变化
            ```js
            mounted: function(){
				var this_ = this;  // 将 this 保存一份
				this.bus.$on('change', function(msg){
					this_.content = msg
				})
			}
            ```
            - 这样写了之后，你会发现，功能就实现了
                - 当我点击 Dell 的时候，其他的都变成 Dell
                - 当我点击 Lee 的时候，其他的都变成 Lee
        - 6.但是，真的实现了吗？
            - 打开控制台后，你会发现，Vue 报了警告
            - [Vue warn]: Avoid mutating a prop directly since the value will be overwritten whenever the parent component re-renders. Instead, use a data or computed property based on the prop's value. Prop being mutated: "content"
            - 报错原因，违反了 **单向数据流** 的原则
            - 解决办法，在组件中，新建一个变量，接收该变量就行
            ```js
            Vue.component('child', {
                data: function(){
                    return {
                        selfContent: this.content
                    }
                },
                props: {
                    content: String
                }
            })
            ```
    - 最终完整代码
        ```html
        <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

        <div id="app">
            <child content='Dell'></child>
            <child content='Lee'></child>
        </div>
        <script>
            Vue.prototype.bus = new Vue()

            Vue.component('child', {
                data: function(){
                    return {
                        selfContent: this.content
                    }
                },
                props: {
                    content: String
                },
                template: '<div @click="handleClick">{{selfContent}}</div>',
                methods: {
                    handleClick: function(){
                        this.bus.$emit('change', this.selfContent)
                    }
                },
                mounted: function(){
                    var this_ = this;  // 将 this 保存一份
                    this.bus.$on('change', function(msg){
                        this_.selfContent = msg
                    })
                }
            })

            var vm = new Vue({
                el: '#app'
            })
        </script>
        ```
- ### 4-6 在Vue中使用插槽 slot
    - 存在的问题
        - 先来看这段代码
            ```html
            <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

            <div id="app">
                <child></child>
            </div>
            <script>
                Vue.component('child', {
                    template: '<div><p>hello</p></div>'
                })

                var vm = new Vue({
                    el: '#app'
                })
            </script>
            ```
        - 现在有这么一个问题
            - 现在子组件内，除了展示 ```<p>hello</p>``` 以外
            - **我还需要展示一段内容，但是这段内容不是我子组件所决定的，而是父组件传递过来的**
        - 尝试解决问题
            - 按照我们过去的方法，可能会想到这样
            ```html
            <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

            <div id="app">
                <child content='<p>Dell</p>'></child>
            </div>
            <script>
                Vue.component('child', {
                    props: ['content'],
                    template: `<div>
                                    <p>hello</p>
                                    <div v-html='this.content'></div>
                            </div>`
                })

                var vm = new Vue({
                    el: '#app'
                })
            </script>
            ```
            - 分析
                - 虽然这样 好像能解决问题了
                - 问题1：
                    - 但是 ```<p>Dell</p>``` 的外层多了一个 div 标签
                        - 有的同学会想到这样 ```<template v-html='this.content'></template>```
                        - 把 div 改成 template 模板占位符
                        - 但是执行结果发现，这样并不能实现功能
                        - 所以，还是得多包一层 div ```<div v-html='this.content'></div>```
                - 问题2：
                    - 当你这样传递的内容很少的时候还行
                    - 如果传递的内容很多的时候，就会变成这样
                        ```html
                        <div id="app">
                            <child content='<p>Dell</p><p>Dell</p><p>Dell</p><p>Dell</p><p>Dell</p><p>Dell</p><p>Dell</p><p>Dell</p><p>Dell</p>'></child>
                        </div>
                        ```
                    - 就会代码变得非常难以阅读
    - 插槽 slot
        - 什么是 插槽 slot？
            - 由于 上面案例中 的解决方法存在的问题，所以 我们引入了 **插槽slot** 的概念
            - 用于 **将父组件传递 DOM内容 给子组件的** 优雅解决方案
        - 插槽 slot 的使用方法
            - 第一步
                - 在子组件的标签之间，写入 DOM内容，如 ```<p>Dell</p>```
                ```html
                <div id="app">
                    <child>
                        <p>Dell</p>
                    </child>
                </div>
                ```
            - 第二步
                - 在子组件的 template 中，用 ```<slot></slot>``` 标签接收内容即可
                ```html
                Vue.component('child', {
                    template: `<div>
                                    <slot></slot>
                                    <p>hello</p>
                            </div>`
                })
                ```
            - 完整代码
                ```html
                <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

                <div id="app">
                    <child>
                        <p>Dell</p>
                    </child>
                </div>
                <script>
                    Vue.component('child', {
                        template: `<div>
                                        <slot></slot>
                                        <p>hello</p>
                                </div>`
                    })

                    var vm = new Vue({
                        el: '#app'
                    })
                </script>
                ```
        - 插槽 slot 的一些特性
            - 特性1 - 默认值
                - 当你 父组件不传入任何内容的时候，在子组件的 slot插槽可以定义默认内容，如 ```<slot>默认内容</slot>```
                - 这样子的话，就会显示插槽内的默认内容
                ```html
                <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

                <div id="app">
                    <child></child>
                </div>
                <script>
                    Vue.component('child', {
                        template: `<div>
                                        <slot>默认内容</slot>
                                        <p>hello</p>
                                </div>`
                    })

                    var vm = new Vue({
                        el: '#app'
                    })
                </script>
                ```
            - 特性2 - **具名插槽**
                - 具名插槽
                    - 给插槽取名字，然后根据名字取用插槽内容
                ```html
                <script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.10/vue.js'></script>

                <div id="app">
                    <child>
                        <div class="headerx" slot="header">header</div>
                        <div class="footerx" slot="footer">footer</div>
                    </child>
                </div>
                <script>
                    Vue.component('child', {
                        template: `<div>
                                        <slot name="header">默认内容</slot>
                                        <p>hello</p>
                                        <slot name="footer"></slot>
                                </div>`
                    })

                    var vm = new Vue({
                        el: '#app'
                    })
                </script>
                ```
- ### 4-7 作用域插槽