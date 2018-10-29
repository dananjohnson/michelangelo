# ✨ Sparklesheets: KSS-based Living Style Guide

Generated from SCSS comments using [kss-node](https://github.com/kss-node/kss-node), a Node.js implementation of [Knyle Style Sheets (KSS)](http://warpspire.com/kss/).

## Building the Styleguide
```
yarn kss
```

## Usage
Documentation is added as comments directly in the SCSS files. See the [KSS docs](https://warpspire.com/kss/syntax/) for full usage guidelines.

Sample usage:
```
// Button (title)
//
// Use with a `<button>` or `<a>` block. Can be called using `@include button`
// or `.button`. (description)
//
// (mixin parameter)
// $bg-color - Background color of the button. Defaults to `inherit`.
//
// Markup:
// <button class="button {{modifier}}">Button Element</button>
// <a class="button {{modifier}}">Link Button</a>
//
// (modifiers)
// :hover - When user hovers over the button.
// .button-primary - A button with higher visual priority.
// .button-secondary - A button with lower visual priority.
//
// Weight: 1 (optional ordering, overrides alphabetical order)
//
// Styleguide STACSS.Appearance.Buttons (styleguide organization)

@mixin button($bg-color: inherit) {
  color: $neutralWhite;
  background-color: $bg-color;

  &:hover {
    background-color: rgba($bg-color, 0.7);
  }
}

.button {
  @include button;
}

.button-primary {
  font-weight: bold;
}

.button-secondary {
  font-size: 0.8em;
}
```

## Configuration
Set in `kss-config.json` in the project root. Note that the file paths for site CSS and JS files are pulled from the Webpack asset manifest file. See `webpack/kss/build.js`.
```
{
  "title"        : "Health Share Styleguide",
  "mask"         : "*.scss",
  "placeholder"  : "[modifier]",

  "builder"      : "node_modules/michelangelo/kss_styleguide/custom-template/",
  "source"       : "themes/healthshare/assets/style/stylesheets/",
  "destination"  : "www/styleguide/",

  "css"          : *see webpack/kss/build.js*
  "js"          : *see webpack/kss/build.js*

  "homepage"     : "../styleguide-intro.md"
}
```
