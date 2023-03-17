
### 继承方式

```js
    /**
     * 原型链、借用构造函数、组合式继承、原型式继承、寄生式继承、组合寄生式、ES6, Class
     * 
    */

   /**
    * 原型链继承
    * 优：逻辑简单，易理解
    * 缺：对象实例共享所有继承的属性和方法, 无法传参
    * 
    * 让一个构造函数的原型是另一个类型的实例，那么这个构造函数new出来的实例就具有该实例的属性
    * 
    * 当视图访问一个对象的属性时，它不仅仅在当前的对象上搜寻，还会搜该对象的原型，以及该对象原型的原型，依次层层向上搜索，直到找到一个名字匹配的属性或达到原型链的末尾
   */

    function Parent() {
        this.info = {
            name: 'kevin'
        }
    }
    Parent.prototype.getInfo = function() {
        return this.info
    }

    function Child() {}

    Child.prototype = new Parent()
    let child = new Child()
    
    child.info.name = 'hello world'
    // child.info.name -> hello world

    let child_ = new Child()
    child_.info.name = 'hello world'



    /**
     * 借用构造函数继承
     * 优：解决了原型链继承不能传参的问题 及 父类的原型共享问题
     * 缺：方法都在构造函数中定义，无法实现函数复用，
     * 
     * 
    */

    function Parent(name) {
        this.info = {name: 'kevin'}
    }

    function Child(name) {
        // 子类构造函数的内部调用父类构造函数，使用 apply or call 将父对象的构造函数绑定在子对象
        Parent.call(this, name)
    }

    let child = new Child('kadian')
    child.info.name = 'kakaka'


    /**
     * 组合继承（经典继承）
     * 优：解决了原型链继承和借用构造函数造成的影响
     * 缺：无论在什么情况下，都会调用2次超类的构造函数：一次是创建子类原型，另一次是子类型构造函数内部
     * 
     * 
    */

    function Parent(name) {
        console.log('执行次数')
        this.info = {name: 'kevin'}
    } 
    Parent.prototype.getInfo = function() { // 使用原型链继承原型上的属性和方法
        console.log(this.info.name)
    }


    function Child(name) {
        Parent.call(this, name) // 使用构造函数传参
    }
    Child.prototype = new Person()

    let child = new Child('kaka')
    child.info.name = 'lalalla'
    let child_ = new Child('2222')
    child.info.name = '33333'


    /**
     * 原型式继承
     * 方法 1、借用构造函数在一个函数内部创建一个临时的构造函数，然后将传入的对象作为这个构造函数的原型，最后返回这个临时类型的一个新实例
     * 
     * 方法 2、Object.create()
     * 
     * 优：不需要单独创建构造函数
     * 缺：属性中包含的引用值始终会在相关对象间共享，子类实例不能想父类传参
     * 
    */

    function createObject(obj) {
        function Func() {}
        Func.prototype = obj
        return new Func()
    }

    let person = {
        name: 'kevin',
        showName() {
            console.log('name is', this.name)
        }
    }
    const child = createObject(person)
    child.name = 'xxx'
    const child_ = createObject(person)


    // 方法 2 
    const child = Object.create(person)



    /**
     * 寄生式继承
     * 优：写法简单，不需要单独创建构造函数
     * 缺：
    */
    function  objectCopy(obj) {
        function Func() {}
        Func.prototype = obj
        return new Func()
    }

    function createAnother(obj) {
        const clone = objectCopy(obj)
        clone.showName = function() {
            console.log('name is', this.name)
        }
        return clone
    }

    let person = {
        name: 'kevin',
        showName() {
            console.log('name is', this.name)
        }
    }

    const child = createAnother(person)
```