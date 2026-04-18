# jquery-drawrpalette

JQuery drawrpalette is a jquery plugin to create a color picker that doesn't require any other libraries.
It's built to work on desktop and mobile seamlessly.

Screenshot:

![screenshot of canvas](https://cachecat.io/jquery-drawrpalette/images/sample.jpg "Screenshot of picker")

Usage:

```html
<input type="text" id="picker" value="#770033" />
```

```javascript
$("#picker").drawrpalette();
```

## Options

| Option         | Type       | Default                                | Description |
|----------------|------------|----------------------------------------|-------------|
| `auto_apply`   | `boolean`  | `false`                                | Hides OK/Cancel; every drag commits the color directly. |
| `enable_alpha` | `boolean`  | `false`                                | Adds an alpha slider to the picker and parses/writes alpha-aware color strings. |
| `format`       | `string`   | `"hex"` (or `"hex8"` when `enable_alpha`) | Output format: `"hex"`, `"hex8"`, `"rgba"`, or `"hsla"`. |
| `aria_label`   | `string`   | `"Pick color"`                         | Overrides the accessible name on the swatch button. |

## Methods

```javascript
$("#picker").drawrpalette("set", "#FF00FF");    //6- or 8-char hex accepted
$("#picker").drawrpalette("destroy");           //restores the original input
```

## Events

All events are namespaced under `.drawrpalette`. The second argument is the current color string in the configured `format`.

- `open.drawrpalette`
- `close.drawrpalette`
- `preview.drawrpalette` fires continuously while the user drags
- `choose.drawrpalette` fires when OK is clicked (or on release in `auto_apply` mode)
- `cancel.drawrpalette` fires when Cancel is clicked or the user clicks outside

```javascript
$("#picker").drawrpalette().on("choose.drawrpalette", function(e, color) {
    console.log("picked", color);
});
```

## Keyboard

The picker is fully keyboard-operable:

- **Enter / Space** on the swatch opens the picker.
- **Arrow keys** adjust saturation and value.
- **Shift + Arrow** adjusts hue.
- **Alt + Arrow** adjusts alpha (when `enable_alpha` is on).
- **Enter** commits and closes; **Escape** cancels and closes.
- **Tab** cycles within the open dialog; focus returns to the swatch on close.

## Theming (optional, Bootstrap-compatible)

The plugin ships with Bootstrap-compatible class names on the elements that benefit most from theming:

- The dropdown container has `card` (alongside `drawrpallete-dropdown`).
- The OK button has `btn btn-sm btn-primary`.
- The Cancel button has `btn btn-sm btn-secondary`.

If Bootstrap 4 or 5 is loaded on the page, these classes pick up its styling with no extra work. If not, the plugin injects its own lightweight defaults for the dropdown chrome and the buttons fall back to native browser styling. You can also style `.drawrpallete-dropdown` directly to match your own design system, because the plugin's default stylesheet is prepended to `<head>`, any later stylesheet (including yours) wins the cascade. See `examples/bootstrap.html` for a full Bootstrap 5 example.

## Build

```
npm install
npm run build
```

The build concatenates `src/umd/start.js` + `src/jquery.drawrpalette.js` + `src/umd/end.js` into `dist/jquery.drawrpalette.js`, then minifies to `dist/jquery.drawrpalette-min.js`.

# To install

jquery-drawrpalette is also available on npm:

npm install jquery-drawrpalette

More [Info and demos at this link](https://cachecat.io/jquery-drawrpalette/ "Info and demos at this link")
