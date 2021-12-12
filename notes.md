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
