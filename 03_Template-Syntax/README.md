# [The Vue Instance](https://vuejs.org/v2/guide/syntax.html)

## Interpolations

```html
<span>Message: {{ msg }}</span>
```

> `msg` can be changed

```html
<span v-once>This will never change: {{ msg }}</span>
```

> `v-once`: never chnaged

## Raw HTML

```html
<p>Using mustaches: {{ rawHtml }}</p>
<p>Using v-html directive: <span v-html="rawHtml"></span></p>
```

> with out `v-html`, data is presented as plain text but `v-html` makes real HTML  
> > Dynamically rendering arbitrary HTML on your website can be very dangerous because it can easily lead to **XSS vulnerabilities**. Only use HTML interpolation on trusted content and **never** on user-provided content.

## Attributes

```html
<div v-bind:id="dynamicId"></div>
```

```html
<button v-bind:disabled="isButtonDisabled">Button</button>
```

> isButtonDisabled: `null, undefined, false, disabled` -> will not render

## Using JavaScript Expressions

```html
{{ number + 1 }}

{{ ok ? 'YES' : 'NO' }}

{{ message.split('').reverse().join('') }}

<div v-bind:id="'list-' + id"></div>
```

each binding can only contain one single expression,  
following will **NOT** word:

```html
<!-- this is a statement, not an expression: -->
{{ var a = 1 }}

<!-- flow control won't work either, use ternary expressions -->
{{ if (ok) { return message } }}
```

## Directives

Directives are special attributes with the v- prefix.  
Directive attrivute values are **single JavaScript expression**

## Arguments

Some directives can take an “argument." For example, `v-bind` is used to reactively update an HTML attribute.

```html
<a v-bind:href="url"> ... </a>
```

Another example: `v-on` listens event.

```html
<a v-on:click="doSomething"> ... </a>
```

## Dynamic Arguments

> New in 2.6.0+

```html
<a v-bind:[attributeName]="url"> ... </a>
```

Possible to use a JavaScript expression in a directive argument by wrapping it with square brackets

```html
<a v-on:[eventName]="doSomething"> ... </a>
```

Similarly, when `eventName`‘s value is `"focus"`, for example, `v-on:[eventName]` will be equivalent to `v-on:focus`.

## Modifiers

```html
<form v-on:submit.prevent="onSubmit"> ... </form>
```

`v-on` and `v-model`