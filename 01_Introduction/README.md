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

