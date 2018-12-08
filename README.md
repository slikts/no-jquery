# You probably don't need jQuery (in 2018)

## JSON

### [`jQuery.getJSON()`](https://api.jquery.com/jquery.getjson/)
```js
$.getJSON("/example.json", data => { console.log(data); });
```
```js
console.log(await $.getJSON("/example.json"));
```

### [`fetch()`][fetch]

```js
fetch("/example.json").then(response => { console.log(response.json()); });
```
```js
console.log(await (fetch("/example.json")).json());
```

## Post

### [`jQuery.ajax()`](https://api.jquery.com/jquery.ajax/)
```js
$.ajax({
  type: 'POST',
  url: '/example',
  data: data,
});
```

### [`fetch()`][fetch]
```js
fetch('/example', {
  method: 'POST',
  // XXX
  body: JSON.stringify(data),
});
```

[fetch]: https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/fetch
