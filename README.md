# flag-icons

> A curated collection of all country flags in SVG — plus the CSS for easier integration. See the [demo](https://flagicons.lipis.dev).

## Install

You can either [download](https://github.com/lipis/flag-icons/archive/main.zip) the whole project as is or install it via npm or Yarn:

```bash
npm install flag-icons
# or
yarn add flag-icons
```

## Usage

First, you need to import css:

```js
import "/node_modules/flag-icons/css/flag-icons.min.css";
```

or use CDN:

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/gh/lipis/flag-icons@7.3.2/css/flag-icons.min.css"
/>
```

or use SASS:

```scss
@use "node_modules/flag-icons/sass/flag-icons";

// or with custom configuration
@use "node_modules/flag-icons/sass/flag-icons" with (
  // Override path to flags directory
  $flag-icons-path: "node_modules/flag-icons/flags",

  // Include only specific country flags
  $flag-icons-included-countries: ("gr", "de", "gb")
);
```

You can find all available variables in [`sass/_variables.scss`](sass/_variables.scss).

### JavaScript modules

From npm installations you can import metadata for each flag directly in modern bundlers:

```js
import "flag-icons/css/flag-icons.css";
import { flagCn, flagUs } from "flag-icons";

console.log(flagUs.name);
// → "United States"
console.log(flagCn.square);
// → URL pointing to the 1x1 asset that can be used in img/src or CSS
```

The ESM entry exposes one export per flag so bundlers can tree-shake unused icons automatically. TypeScript
definitions are included, providing literal unions for the available country codes and strongly typed metadata.

For using the flags inline with text add the classes `.fi` and `.fi-xx` (where `xx` is the [ISO 3166-1-alpha-2 code](https://www.iso.org/obp/ui/#search/code/) of a country) to an empty `<span>`. If you want to have a squared version flag then add the class `fis` as well. Example:

```html
<span class="fi fi-gr"></span> <span class="fi fi-gr fis"></span>
```

You could also apply this to any element, but in that case you'll have to use the `fib` instead of `fi` and you're set. This will add the correct background with the following CSS properties:

```css
background-size: contain;
background-position: 50%;
background-repeat: no-repeat;
```

Which means that the flag is just going to appear in the middle of an element, so you will have to set manually the correct size of 4 by 3 ratio or if it's squared add also the `flag-icon-squared` class.

## Development

Run the `yarn` to install the dependencies after cloning the project and you'll be able to:

To build `*.scss` files

```bash
$ yarn build
```

To serve it on `localhost:8000`

```bash
$ yarn start
```

To have only specific countries in the css file, remove the ones that you don't need from the [`_flag-icons-list.scss`](sass/_flag-icons-list.scss) file and build it again.

## Credits

- This project wouldn't exist without the awesome and now deleted collection of SVG flags by [koppi](https://github.com/koppi).
- Thank you [Andrejs Abrickis](https://twitter.com/andrejsabrickis) for providing the `flag-icons` name on [npm](https://www.npmjs.com/package/flag-icons).
