## Upgrade from versions [`1.9.*`](https://github.com/autoNumeric/autoNumeric/releases/tag/1.9.46)/[`2.*`](https://github.com/autoNumeric/autoNumeric/releases/tag/v2.0.13) to version [`4.*`](https://github.com/autoNumeric/autoNumeric/tree/v4.6.0)

!!! Attention "Attention!"

	Version `4` has seen a [lots of improvements and new features](https://github.com/autoNumeric/autoNumeric/releases/tag/v4.0.0), but also introduce breaking changes if you are trying to use it with an old `v1.9` or `v2` configuration.

### Initialization

Initialization of an AutoNumeric object [has changed](https://github.com/autoNumeric/autoNumeric/#initialization) a bit.

Since AutoNumeric is now an ES6 module, *`AutoNumeric` being the name of the `class`*, and since ___the [jQuery dependency](dependencies.md) has been dropped___, you now longer need to first select the DOM element with jQuery, then call the `#!js $(yourElement).autoNumeric('init', { options })` method.

Now, you only need to instantiate an `AutoNumeric` object using `#!js new AutoNumeric(yourElement, { options })` (or if you do not already have a reference to the DOM element, use `#!js new AutoNumeric('myCSSSelector', { options })`).

| <= `v2` (Before)          | `v4` (After) |
| :---------------- | :-----------  |
| `#!js $('.myInput').autoNumeric('init', { options });` | If you want to initialize [only one element](https://github.com/autoNumeric/autoNumeric/#initialize-one-autonumeric-object): `#!js new AutoNumeric('.myInput', { options });` |
|  | If you want to initialize [multiple elements](https://github.com/autoNumeric/autoNumeric/#initialize-multiple-autonumeric-objects-at-once): `#!js AutoNumeric.multiple('.myCssClass > input', { options });` |

### Configuration

!!! Warning "Deprecation warning"

	The old option names have changed and are now _deprecated_, in favor of the [new ones](https://github.com/autoNumeric/autoNumeric/#options).


To help you switch to the new names, detailed warning messages are displayed in the console if an old option name is detected.

!!! Info "`mDec` option changes"
    Do note that the option `mDec` (or its new name `decimalPlacesOverride` if you used `v2`) **is no longer used**.

    If you want to specify the number of decimals, instead of relying on the maximum number of decimal places in `minimumValue` or `maximumValue` like before, you can now set `decimalPlaces` to set it globally.
    
    If you wish, you can also specify a different number of decimal places for the formatted value (with `decimalPlacesShownOnFocus` and `decimalPlacesShownOnFocus`) or the `rawValue` (with `decimalPlacesRawValue`).

The following table shows the equilavence between pre and post `v4` version for option names:

| <= `v2` (Before)          | `v4` (After) |
| :---------------- | :-----------  |
| `aSep`          | `digitGroupSeparator` |
| `nSep`          | `showOnlyNumbersOnFocus` |
| `dGroup`        | `digitalGroupSpacing` |
| `aDec`          | `decimalCharacter` |
| `altDec`        | `decimalCharacterAlternative` |
| `aSign`         | `currencySymbol` |
| `pSign`         | `currencySymbolPlacement` |
| `pNeg`          | `negativePositiveSignPlacement` |
| `aSuffix`       | `suffixText` |
| `oLimits`       | `overrideMinMaxLimits` |
| `vMax`          | `maximumValue` |
| `vMin`          | `minimumValue` |
| `mDec`          | `decimalPlacesOverride`<br>(:warning: Deprecated) |
| `eDec`          | `decimalPlacesShownOnFocus` |
| `scaleDecimal`  | `decimalPlacesShownOnBlur` |
| `aStor`         | `saveValueToSessionStorage` |
| `mRound`        | `roundingMethod` |
| `aPad`          | `allowDecimalPadding` |
| `nBracket`      | `negativeBracketsTypeOnBlur` |
| `wEmpty`        | `emptyInputBehavior` |
| `lZero`         | `leadingZero` |
| `aForm`         | `formatOnPageLoad` |
| `sNumber`       | `selectNumberOnly` |
| `anDefault`     | `defaultValueOverride` |
| `unSetOnSubmit` | `unformatOnSubmit` |
| `outputType`    | `outputFormat` |
| `debug`         | `showWarnings` |

If you want more detail about the AutoNumeric options, feel free to browse the [AutoNumeric options source code](https://github.com/autoNumeric/autoNumeric/blob/master/src/AutoNumericOptions.js) which has detailed comment for each one.

???+ Info "Interactive option testing chamber"

	Do note that you can check out the new options on the official website [here](http://autonumeric.org/guide).

### Method calls

Moreover, since we are now using an `AutoNumeric` object, we can now directly call its [methods](../../Documentation/methods) (and [chain](../../Documentation/instantiated methods#function-chaining) them if needed).<br> 
In the following table, the `anElement` variable is created using `#!js const anElement = new AutoNumeric('someSelector', { options })`.

The methods are now called like so:

| <= `v2` (Before)          | `v4` (After) |
| :---------------- | :-----------  |
| `#!js $(someSelector).autoFormat('1234.56', { options });` | `#!js AutoNumeric.format(1234.56, { options });` |
| `#!js $(someSelector).autoUnFormat('1.234,56 €', { options });` | `#!js AutoNumeric.unformat('1.234,56 €', { options });` |
| `#!js $(someSelector).autoValidate({ options });` | `#!js AutoNumeric.validate({ options })` |
| `#!js $.fn.autoNumeric.defaults` | `#!js AutoNumeric.getDefaultConfig()` |
| `#!js $(someSelector).autoNumeric("destroy");` | `#!js anElement.remove();` |
| `#!js $(someSelector).autoNumeric('get');` | `#!js anElement.getNumericString();` |
| `#!js $(someSelector).autoNumeric('getArray');` | `#!js anElement.formArrayNumericString();` |
| `#!js $(someSelector).autoNumeric('getFormatted');` | `#!js anElement.getFormatted();` |
| `#!js $(someSelector).autoNumeric('getLocalized');` | `#!js anElement.getLocalized();` |
| `#!js $(someSelector).autoNumeric('getNumber');` | `#!js anElement.getNumber();` |
| `#!js $(someSelector).autoNumeric('getString');` | `#!js anElement.formNumericString();` |
| `#!js $.fn.autoNumeric.lang` | `#!js AutoNumeric.getPredefinedOptions()` |
| `#!js $(someSelector).autoNumeric('reSet');` | `#!js anElement.reformat();` |
| `#!js $(someSelector).autoNumeric('set', '12345.67');` | `#!js anElement.set(12345.67);` |
| `#!js $(someSelector).autoNumeric('unSet');` | `#!js anElement.unformat();` |
| `#!js $(someSelector).autoNumeric("update", { options });` | `#!js anElement.update({ options });` |
| `#!js $(someSelector).autoNumeric("wipe");` | `#!js anElement.wipe();` |

Check the [methods documentation](../../Documentation/methods) to see how some of those functions signatures changed.


## Need help?

If you encounter any problem upgrading to `v4`, feel free to contacts us on our [Gitter channel](https://gitter.im/autoNumeric/autoNumeric) or on IRC on Libera Chat `#autoNumeric`!

Please check the [contact page](../../Documentation/support) for more information.
