# [Introduction](https://vuejs.org/v2/guide/)

## Getting Started

### CDN

- Develop version

 ```html
 <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
 ```

- Production version  

 ```html
 <script src="https://cdn.jsdelivr.net/npm/vue"></script>
 ```

## Declarative Rendering

```html
<div id="app">
  {{ message }}
</div>
```

```javascript
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
});
```

If set `app.message`to different value, #app will be changed.  

```js
app.message = "Test2"
```

### Bind element attributes

> bind title attribute of `span`

```html
<div id="app-2">
  <span v-bind:title="message">
    Hover your mouse over me for a few seconds
    to see my dynamically bound title!
  </span>
</div>
```

```js
var app2 = new Vue({
  el: '#app-2',
  data: {
    message: 'You loaded this page on ' + new Date().toLocaleString()
  }
});
```

`v-bind` attribute is called __directive__  
`v-` is special attributes provided by Vue.

```js
app2.message = 'some new message'
```

title arribute will be changed

## Conditionals and Loops

```html
<div id="app-3">
  <span v-if="seen">Now you see me</span>
</div>
```

```js
var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: true
  }
});
```

`app3.seen = false` : disapear message
> I found it is different with `display: none`.  
`app3.seen = false` makes `#app-3` empty: `<!-- -->`

v-for directive can be used for displaying a list of items using the data from an Array

```html
<div id="app-4">
  <ol>
    <li v-for="todo in todos">
      {{ todo.text }}
    </li>
  </ol>
</div>
```

```js
var app4 = new Vue({
  el: '#app-4',
  data: {
    todos: [
      { text: 'Learn JavaScript' },
      { text: 'Learn Vue' },
      { text: 'Build something awesome' }
    ]
  }
});
```

Output

```text
1. Learn JavaScript
2. Learn Vue
3. Build something awesome
```

`app4.todos.push({ text: 'New item' })` : Append New items

> `v-for:"todo in todos"` is similar with foreach(python)

## Handling User Input

```html
<div id="app-5">
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">Reverse Message</button>
</div>
```

```javascript
var app5 = new Vue({
  el: '#app-5',
  data: {
    message: 'Hello Vue.js!'
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  }
});
```

`v-on` is event listener  
`v-model` is two way binding

```html
<div id="app-6">
  <p>{{ message }}</p>
  <input v-model="message">
</div>
```

```js
var app6 = new Vue({
  el: '#app-6',
  data: {
    message: 'Hello Vue!'
  }
});
```

## Composing with Components

```js
// Define a new component called todo-item
Vue.component('todo-item', {
  template: '<li>This is a todo</li>'
});
```

```html
<ol>
  <!-- Create an instance of the todo-item component -->
  <todo-item></todo-item>
</ol>
```

In this situation, same `todo`s is printed

```js
Vue.component('todo-item', {
  // The todo-item component now accepts a
  // "prop", which is like a custom attribute.
  // This prop is called todo.
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})
```

```html
<div id="app-7">
  <ol>
    <!--
      Now we provide each todo-item with the todo object
      it's representing, so that its content can be dynamic.
      We also need to provide each component with a "key",
      which will be explained later.
    -->
    <todo-item
      v-for="item in groceryList"
      v-bind:todo="item"
      v-bind:key="item.id"
    ></todo-item>
  </ol>
</div>
```

```js
Vue.component('todo-item', {
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})

var app7 = new Vue({
  el: '#app-7',
  data: {
    groceryList: [
      { id: 0, text: 'Vegetables' },
      { id: 1, text: 'Cheese' },
      { id: 2, text: 'Whatever else humans are supposed to eat' }
    ]
  }
});
```

> `v-bind:todo="item"` -> `props: ['todo']`
