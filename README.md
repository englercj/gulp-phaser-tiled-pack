# gulp-tiled-pack

This is a gulp plugin that will create phaser asset packs for tilemaps. This is useful to not
have to hard-code the assets required by a tilemap into your code. You can change the layers,
tilesets, images, etc. and just use this tool to regenerate the asset pack.

## Usage

```js
var gulp = require('gulp'),
    tiledmapPack = require('gulp-phaser-tiled-pack');

/*****
 * Assets Phaser packs task, creates phaser asset loader packs for tilemaps
 *****/
gulp.task('pack', function () {
    return gulp.src('./src/assets/**/*.json')
        .pipe(tiledmapPack({ baseUrl: 'assets' }))
        .pipe(gulp.dest('./public/assets'));
});
```
## Options

The only parameter to the exported function is an options object which has the following properties:

- `baseUrl`
 * Default: `''`
 * The base URL to use when building the asset urls
- `useExtInKey`
 * Default: `false`
 * If true will use the map file extension in the key

## Output

The file output from this plugin looks something like this:

```json
{
    "meta": {
        "generated": "1415053280402",
        "version": "1.0",
        "app": "gulp-phaser-tiled-pack",
        "url": "https://github.com/englercj/gulp-phaser-tiled-pack"
    },
    "level1": [
        {
            "type": "image",
            "subtype": "tileset",
            "key": "tilemap_level1_tileset_tiles-1",
            "name": "tiles-1",
            "url": "assets/levels/level1/tiles-1.png",
            "overwrite": false
        },
        {
            "type": "tilemap",
            "key": "tilemap_level1",
            "url": "assets/levels/level1/level1.json",
            "format": "TILED_JSON"
        }
    ]
}
```
