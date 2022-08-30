AutoNumeric can be used in two ways;

- **with event listeners** when used on `<input>` elements or on `contenteditable`-enabled elements making them reactive (in a *read/write* mode), or
- **without event listeners** when used on DOM elements not having the `contenteditable` attribute set to `true`, essentially acting as a *format-once-and-forget* *read only* mode.

## On `<input>` elements
When used on an `<input>` element, you'll be able to interact with its value and get a formatted input value *as-you-type*, using the full power of AutoNumeric.

Please note than due to browser constraints, only the following supported `<input>` *types* are supported:

- `text`,
- `tel`,
- `hidden`, or
- no type specified at all

```html title="Input types examples"
<input type='text' value="1234.56">
<input type='tel' value="1234.56">
<input type='hidden' value="1234.56">
<input value="1234.56">
```

!!! failure "Caveat"
    The `number` type is **not** supported simply because AutoNumeric formats numbers as strings (ie. `'123.456.789,00 &#8364;'`) that this input type does not allow.


## On `contenteditable`-enabled elements
Any element in the following `allowedTagList`[^1] that support the `contenteditable` attribute can be initialized by AutoNumeric.
This means that anywhere on a page, on any DOM element, you can harness the power of AutoNumeric which will allow you to mask and manage the user inputs.

Given the following html code...
```html
<p id="editableDom" contenteditable="true">12345678.9012</p>
```
you can initialize this `<p>` element with AutoNumeric:
```js
new AutoNumeric('#editableDom').french();
```
...and it will act exactly like an `<input>` element controlled by AutoNumeric.

## On other DOM elements

You can use AutoNumeric to format a DOM element value **once** on load.<br>
This means it will then not react to any user interaction nor changes to it's value or formatting.

The following elements are accepted:
!!! example "Allowed tags list"
    `b`, `caption`, `cite`, `code`, `const`, `dd`, `del`, `div`, `dfn`, `dt`, `em`, `h1`, `h2`, `h3`, `h4`, `h5`, `h6`, `ins`, `kdb`, `label`, `li`, `option`, `output`, `p`, `q`, `s`, `sample`, `span`, `strong`, `td`, `th`, `u`

!!! Tip "Tips"
    Since the `number` type is not supported, if you want to display a numeric keyboard when selecting an AutoNumeric-managed element in a mobile browser, you can use the input `tel` type.
    
    In the [future](http://caniuse.com/#search=inputmode), you'll be able to add the `inputmode="numeric"` [Html attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Input) in order to achieve the same effect.

[^1]: The `allowedTagList` contains the following HTML elements : `b`, `caption`, `cite`, `code`, `const`, `dd`, `del`, `div`, `dfn`, `dt`, `em`, `h1`, `h2`, `h3`, `h4`, `h5`, `h6`, `ins`, `kdb`, `label`, `li`, `option`, `output`, `p`, `q`, `s`, `sample`, `span`, `strong`, `td`, `th`, `u`
