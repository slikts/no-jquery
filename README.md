# You probably don't need jQuery (in 2018)

## Goals
* discussing and linking to polyfills for web APIs
* showing [caniuse.com](https://caniuse.com/) statistics for features
* linking to jQuery and MDN documentation
* using modern practices
* embedding runnable and editable examples
* discussing when component frameworks are preferable to DOM manipulation
* discussing jQuery history and design flaws

## Ajax

### JSON

#### [`jQuery.getJSON()`](https://api.jquery.com/jquery.getjson/)
```js
$.getJSON('/example.json', data => { console.log(data); });
```
```js
console.log(await $.getJSON('/example.json'));
```

#### [`fetch()`][fetch]
```js
fetch('/example.json').then(response => { console.log(response.json()); });
```
```js
console.log(await (fetch('/example.json')).json());
```

### Post

#### [`jQuery.ajax()`](https://api.jquery.com/jquery.ajax/)
```js
$.ajax({
  type: 'POST',
  url: '/example',
  data: data,
});
```

#### [`fetch()`][fetch]
```js
fetch('/example', {
  method: 'POST',
  body: JSON.stringify(data),
});
```

### Request

#### [`jQuery.ajax()`](https://api.jquery.com/jquery.ajax/)
```js
$.ajax({ url: '/example' }) // -> promise
```

#### [`fetch()`][fetch]
```js
fetch('/example') // -> promise
```

## Effects

### Fade in

#### [`jQuery.fadeIn()`](https://api.jquery.com/jquery.ajax/)
```js
$(el).fadeIn();
```

#### CSS transitions
```js
el.classList.add('show');
el.classList.remove('hide');
```
```css
.show {
  transition: opacity 400ms;
}
.hide {
  opacity: 0;
}
```

#### Web animations API
```js
```

### Hide

#### [`jQuery.hide()`](https://api.jquery.com/jquery.hide/)
```js
$(el).hide();
```

#### [`HTMLElement.style`][style]
```js
el.style.display = 'none';
```

### Show

#### [`jQuery.show()`](https://api.jquery.com/jquery.show/)
```js
$(el).show();
```

#### [`HTMLElement.style`][style]
```js
el.style.display = '';
```

## Elements

### Add class

#### [`.addClass`](https://api.jquery.com/addclass/)
```js
$(el).addClass(className);
```

#### [`HTMLElement.classList`][classList]

```js
el.classList.add(className);
```

### Each

#### [`.each`](https://api.jquery.com/each/)
```js
$(selector).each((i, el) => { console.log(i, el); });
```

#### [`Document.querySelectorAll()`][qSA]
```js
[...document.querySelectorAll(selector)].forEach((el, i) => { console.log(i, el); });
```

### Filter

#### [`.filter`](https://api.jquery.com/filter/)
```js
$(selector).filter(filterFn)
```

#### [`Document.querySelectorAll()`][qSA]
```js
[...document.querySelectorAll(selector)].filter(filterFn)
```

### Outer height with margin

#### [`.outerHeight`](https://api.jquery.com/outerHeight/)
```js
$(el).outerHeight(true)
```

#### DOM
```js
```

## Events

### Ready

#### [`.ready`](https://api.jquery.com/ready/)
```js
$(document).ready(() => { console.log("ready"); });
```

#### [`<script defer>`][defer]
```html
<script defer src="..."></script>
```


[fetch]: https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/fetch
[style]: https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/style
[classList]: https://developer.mozilla.org/en-US/docs/Web/API/Element/classList
[qSA]: https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll
[defer]: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script#attr-defer
