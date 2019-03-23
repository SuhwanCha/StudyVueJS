# [The Vue Instance](https://vuejs.org/v2/guide/instance.html)

## Creating a Vue Instance

Every Vue application starts by creating a new Vue instance with the `Vue` function:

```js
var vm = new Vue({
  // options
});
```

## Data and Methods

```js
// Our data object
var data = { a: 1 }

// The object is added to a Vue instance
var vm = new Vue({
  data: data
})

// Getting the property on the instance
// returns the one from the original data
vm.a == data.a // => true

// Setting the property on the instance
// also affects the original data
vm.a = 2
data.a // => 2

// ... and vice-versa
data.a = 3
vm.a // => 3
```

> It's smiliar with `vm.data` points `data`'s memory

`data` are **only reactive** if they existed when the instance was created.

```js
vm.b = 'hi'
```

> `data.b` will be not changed.

If I need a property later, I need to inital value.

```js
data: {
  newTodoText: '',
  visitCount: 0,
  hideCompletedTodos: false,
  todos: [],
  error: null
}
```

`Object.freeze()` : prevents existing properties from being changed

```js
var obj = {
  foo: 'bar'
}

Object.freeze(obj)

new Vue({
  el: '#app',
  data: obj
})
```

> `Object.freeze(obj)` makes `obj` **read-only** data

```console
Uncaught TypeError: Cannot assign to read only property 'foo' of object '#<Object>'
    at Vue.proxySetter [as foo] (vue.js:4624)
    at <anonymous>:1:7
proxySetter @ vue.js:4624
(anonymous) @ VM266:1
```

started with `$` : not difined from user.

```js
var data = { a: 1 }
var vm = new Vue({
  el: '#example',
  data: data
})

vm.$data === data // => true
vm.$el === document.getElementById('example') // => true

// $watch is an instance method
vm.$watch('a', function (newValue, oldValue) {
  // This callback will be called when `vm.a` changes
})
```

## Instance Lifecycle Hooks

`created` hook can be used to run code after an instance is created

```js
new Vue({
  data: {
    a: 1
  },
  created: function () {
    // `this` points to the vm instance
    console.log('a is: ' + this.a)
  }
})
// => "a is: 1"
```

![lifecycle](https://vuejs.org/images/lifecycle.png)
