Options can be added and/or modified after the initialization has been done.

## Adding or modifing options

Either by passing an option object that contains multiple options,
```js
anElement.update({ moreOptions });
anElement.update(AutoNumeric.getPredefinedOptions().NorthAmerican); // Update the settings (and immediately reformat the element accordingly)
```

...by passing multiple option objects, the latter overwriting the settings from the former ones,
```js
anElement.update({ moreOptions1 }, { moreOptions2 }, 'euro');
// or in a single array
anElement.update([{ moreOptions1 }, { moreOptions2 }, 'euro']);
```

...or by changing the options one by one (or by calling a pre-defined option object).
```js
anElement.options.minimumValue('12343567.89');
anElement.options.allowDecimalPadding(false);
```
!!! Info
    Each option can be accessed as a *function* to update its value, ie. `anElement.options.<optionName>()`, where `<optionName>` can be any option name from the [options list](configuration options.md#options).


!!! Success "Hint"
    As soon as the options are modified, the AutoNumeric-managed input content is re-formatted accordingly.

## Resetting options

At any point, you can reset the options by calling the `options.reset()` method.
This effectively drop any previous options you could have set, then load back the [default settings](https://github.com/autoNumeric/autoNumeric/blob/next/src/AutoNumericDefaultSettings.js).
```js title="Reset the options to their default settings"
anElement.options.reset();
```

Lastly, the option object can be accessed directly, thus allowing to query each options globally too.<br>This allows to inspect the current options used.
```js title="Access the current options as an object"
anElement.getSettings(); // Return the options object containing all the current AutoNumeric settings in effect
```
