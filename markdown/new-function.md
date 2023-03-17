### new 构造函数

```js
    /**
        1.新生成对象：new关键字会首先创建一个空对象

        2.链接到原型：将这个空对象的原型对象指向构造函数的原型属性，从而继承原型上的方法

        3.绑定this： 将this指向这个空对象，执行构造函数中的代码，以获取私有属性

        4.返回新对象：如果构造函数返回了一个对象res，就将该返回值res返回，如果返回值不是对象，就将创建的对象返回
    */

    // function $new(Con, ...args) {
    //     const obj = {}
    //     obj.__proto__ = Con.prototype
    //     const res = Con.apply(this, ...args)

    //     return res instanceof Object ? res : obj
    // }


    function $new() {
        let obj = {},
        Constructor = [].shift.call(arguments)
        obj.__proto__ = Constructor.prototype
        let result = Constructor.apply(obj, arguments)
        return result instanceof Object ? result : obj
    }

    function Test() {
        this.name = 'kevin'
    }

    $new(Test).name // kevin
```