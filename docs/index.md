<p align="center"><a href="http://autonumeric.org"><img src="http://autonumeric.org/statics/icons/apple-icon-152x152.png" alt="autonumeric.org"></a></p>

<p align="center">
<a href="https://npmjs.org/package/autonumeric"><img src="https://img.shields.io/npm/v/autonumeric.svg" alt="Latest Version"></a>
<a href="https://travis-ci.org/autoNumeric/autoNumeric"><img src="https://img.shields.io/travis/autoNumeric/autoNumeric.svg" alt="Build Status"></a>
<a href="https://snyk.io/test/github/autoNumeric/autoNumeric"><img src="https://snyk.io/test/github/autoNumeric/autoNumeric/badge.svg" alt="Known Vulnerabilities"></a>
<a href="https://coveralls.io/github/autoNumeric/autoNumeric?branch=next"><img src="https://coveralls.io/repos/github/autoNumeric/autoNumeric/badge.svg?branch=next" alt="Coverage Status"></a>
<br>
<a href="https://gitter.im/autoNumeric/autoNumeric"><img src="https://img.shields.io/badge/gitter-autoNumeric%2FautoNumeric-brightgreen.svg" alt="Gitter chat"></a>
<a href="http://badge.fury.io/js/autonumeric"><img src="http://img.shields.io/npm/dm/autonumeric.svg" alt="Npm downloads per month"></a>
<a href="https://www.jsdelivr.com/package/npm/autonumeric"><img src="https://data.jsdelivr.com/v1/package/npm/autonumeric/badge?style=rounded" alt="jsDelivr downloads per month"></a>
</p>

## What is [AutoNumeric](http://autonumeric.org)?

AutoNumeric is a standalone Javascript library that provides live *as-you-type* formatting for international numbers and currencies.

### Feature Overview
Our mission is to provide a JS library to create and manage easy-to-use and logical user experience for inputing numeric values in forms.

AutoNumeric main features are:
#### **Easy** to use and configure
```js
// Initialization
new AutoNumeric('.myInput', { currencySymbol : '$' });
```
#### Very **high configurability**
...with more than 40 [options](Documentation/configuration options.md) are available.
```js
// The options are...optional :)
const autoNumericOptionsEuro = {
    digitGroupSeparator        : '.',
    decimalCharacter           : ',',
    decimalCharacterAlternative: '.',
    currencySymbol             : '\u202f€',
    currencySymbolPlacement    : AutoNumeric.options.currencySymbolPlacement.suffix,
    roundingMethod             : AutoNumeric.options.roundingMethod.halfUpSymmetric,
};

// Initialization
new AutoNumeric(domElement, autoNumericOptionsEuro);
```

#### User experience oriented
Using AutoNumeric just **feels right and natural**, specially with the function chaining feature
```js
anElement.french()
         .set(42)
         .update({ options })
         .formSubmitJsonNumericString(callback)
         .clear();
```
#### Supports most **international** numeric formats and currencies
If the one you use is not supported yet, please open an [issue](https://github.com/autoNumeric/autoNumeric/issues/new) and we'll add it as soon as possible!

#### Mobile support
The mobile Android Chrome browser is partially supported.

#### And also...

- Any number of different formats can be used at the same time on the same page.<br>Each input can be configured by either setting the options as HTML5 data attributes, or directly passed as an argument in the Javascript code
- The settings can easily be changed at *any* time using the `update` method or via a callback
- AutoNumeric supports `input` elements as well as most text elements with the `contenteditable` attribute, allowing you to place formatted numbers and currencies on just about any part of your pages
- AutoNumeric elements *can be linked together* allowing you to perform one action on multiple elements at once
- 8 pre-defined [currency options](Documentation/predefined options.md#predefined-language-options) as well as 33 [common options](Documentation/predefined options.md#predefined-common-options) allows you to directly use AutoNumeric by skipping the option configuration step
- 26 built-in [methods](Documentation/methods.md) gives you the flexibility needed to use AutoNumeric to its full potential
- 22 [global methods](Documentation/instantiated methods.md#perform-actions-globally-on-a-shared-init-list-of-autonumeric-elements) that allows to control sets of AutoNumeric-managed elements at once
- 21 additional [methods](Documentation/instantiated methods.md#form-functions) specialized for managing form management and submission
- A [formula mode](Documentation/formula mode.md) that allows to quickly enter and evaluate math expressions inside the element
- 17 [static functions](Documentation/static methods.md) provided by the `AutoNumeric` class
- And more than 50 [options](Documentation/configuration options.md) allowing you to precisely customize your currency format and behavior

With that said, AutoNumeric supports most international numeric formats and currencies including those used in Europe, Asia, and North and South America.

## Try AutoNumeric!

If you want to try AutoNumeric, please check the [demo](Documentation/demo.md) page.

## Which version should I use?

The latest stable branch is always on `master`. Currently this is version [4.2.*](https://github.com/autoNumeric/autoNumeric/tree/master).

However most of the development in done on the `next` [branch](https://github.com/autoNumeric/autoNumeric/tree/next), with `master` being updated sparsely.

If you want to try the new features, you can check out the latest development version in the `next` [branch](https://github.com/autoNumeric/autoNumeric/tree/next). That branch can see changes in the API (check the [semver](http://semver.org/)), however it's still very stable and bug-free (as far as we know) since it's always fully tested for regressions.

!!! tip
    `next` is the preferred branch to use in production. Use `master` only if you do not need fixes quickly.

### Older versions (v1.9 and v2)

If you are still using the old _deprecated_ versions `1.9` and `2`, you can follow our [guide](Developer guide/how to upgrade to v4.md) for easily upgrading from those versions to the current version `4`.

## What's next?

You can check what could be the next features coming to AutoNumeric on the [projects](https://github.com/autoNumeric/autoNumeric/projects) page *(feel free to [participate](Developer guide/how to contribute.md)!)*.
