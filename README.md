# webpack-archive-plugin

Webpack plugin to create archives of emitted files.

## Installation

```bash
# for webpack 4.x
npm install --save-dev @laomao800/webpack-archive-plugin
```

```bash
# for webpack < 4
npm install --save-dev @laomao800/webpack-archive-plugin@1.x
```

## Usage

webpack.config.js:

```javascript
const ArchivePlugin = require('@laomao800/webpack-archive-plugin');

module.exports = {
  // ...
  output: {
    path: path.join(__dirname, 'dist'),
    filename: 'bundle.js'
  },
  plugins: [
    new ArchivePlugin({
      // the output location, can be relative (to Webpack output path) or absolute
      output: '',

      // output archive filename, defaults to the Webpack output filename (above),
      // if not present, use the basename of the path
      filename: '',

      // defaults to the array ['zip', 'tar']
      // valid format is 'zip' and 'tar', can be a string or an array,
      format: '',

      // OPTIONAL: defaults to the empty string
      // the file extension to use instead of 'zip' or 'tar.gz'
      // if 'format' is Array, extension needs to be like { zip: 'zipext', tar: 'tarext' }
      extension: '',

      // OPTIONAL: defaults to the empty string
      // the prefix for the files included in the zip/tar.gz file
      pathPrefix: 'relative/path'
    })
  ],
}
```

Will create two archives in the same directory as output.path (`__dirname/dist` in the example),
`${output.filename}.tar.gz` and `${output.filename}.zip` containing all compiled assets.
