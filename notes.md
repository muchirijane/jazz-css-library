#install Gulp

```bash
npm install sass gulp-sass --save-dev

```

```js
const { src, dest, watch, series } = require("gulp");
const sass = require("gulp-sass")(require("sass"));

function buildStyles() {
  return (
    src("src/styles/**/*.scss")
      //the folder of the sass files in the styles folder and any sub folder ( /** )
      .pipe(sass()) // sass compiler
      .pipe(dest("css/styles"))
  ); //folder for the css results
}

// a function to watch our changes in scss files and compiles them by running build styles
function watchStyles() {
  watch("src/styles/*.scss", buildStyles);
}
exports.default = series(buildStyles, watchStyles);
// series function to export the changes in order
```

- files with (\_variables) are ignored by the compiler

## use of maps

- maps are like using object in javascript
- Useful for generating utility classes, you can loop through a map and get a value of each class.

- Create a theme folder and add a color scss file

```scss
$colors: (
  "primary": (
    "base": $primary-base,
    "light": $primary-light,
    "dark": $primary-dark,
  ),
  "secondary": (
    "base": $secondary-base,
    "light": $secondary-light,
    "dark": $secondary-dark,
  ),
  "blue": #1919e6,
  "red": #e61919,
  "yellow": #e6e619,
```

@debug map-get(
$colors,
"primary",
"base"
); // shows the base colour of the primary colour

@debug map-has-key(
$colors,
"primary",
"base"
); // returns true if the key exists

@debug map-remove(
$colors,
"primary",
"base"
); // removes the key "base" from the map

@debug map-keys($colors); //shows the keys of the map

@debug map-merge( $colors, ("pink": #ffa8e5) ); //merges the map with the new key"))
