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