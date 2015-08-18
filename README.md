<!---------------------------------------------------------------------------->
<!-- STOP, LOOK & LISTEN!                                                   -->
<!-- ====================                                                   -->
<!-- Do NOT edit this file directly since it's generated from a template    -->
<!-- file, using https://github.com/IonicaBizau/node-blah                   -->
<!--                                                                        -->
<!-- If you found a typo in documentation, fix it in the source files       -->
<!-- (`lib/*.js`) and make a pull request.                                  -->
<!--                                                                        -->
<!-- If you have any other ideas, open an issue.                            -->
<!--                                                                        -->
<!-- Please consider reading the contribution steps (CONTRIBUTING.md).      -->
<!-- * * * Thanks! * * *                                                    -->
<!---------------------------------------------------------------------------->

# svg.connectable.js
A JavaScript library for connecting SVG things.

[![svg.connectable.js](http://i.imgur.com/VPZjM3v.png)](http://jillix.github.io/svg.pan-zoom.js/)

## CDN
The library is available on [CDNJS](https://cdnjs.com/libraries/svg.connectable.js) as well. To use it, just do:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/svg.connectable.js/2.0.0/svg.connectable.min.js"></script>
```

## Usage

This library depends on:

 - [SVG.js](https://github.com/wout/svg.js)
 - [svg.draggy.js](https://github.com/jillix/svg.draggy.js)

```html
<script src="path/to/svg.js"></script>
<script src="path/to/svg.draggy.js"></script>
<script src="path/to/svg.connectable.js"></script>
<!-- Or from CDN
<script src="https://cdnjs.cloudflare.com/ajax/libs/svg.connectable.js/2.0.0/svg.connectable.min.js"></script>
-->
<div class="graph"></div>
<script>
    var svg = new SVG(document.querySelector(".graph")).size("100%", 500);
    var links = svg.group();
    var markers = svg.group();
    var nodes = svg.group();

    var g1 = nodes.group().translate(300, 200).draggy();
    g1.circle(80).fill("#C2185B");

    var g2 = nodes.group().translate(100, 200).draggy();
    g2.circle(50).fill("#E91E63");

    var g3 = nodes.group().translate(200, 400).draggy();
    g3.circle(100).fill("#FF5252");

    g1.connectable({
        container: links,
        markers: markers
    }, g2).setLineColor("#5D4037");

    g2.connectable({
        padEllipse: true
    }, g3).setLineColor("#5D4037")
</script>
```

## Documentation

### `connectable(options, elmTarget)`
Connects two elements. If called multiple times, the lines will be curved.

#### Params
- **Object** `options`: An object containing the following fields:
 - `container` (SVGElement): The line elements container.
 - `markers` (SVGElement): The marker elements container.
- **SVGElement** `elmTarget`: The target SVG element.

#### Return
- **Object** The connectable object containing:
 - `source` (SVGElement): The source element.
 - `target` (SVGElement): The target element.
 - `line` (SVGElement): The line element.
 - `marker` (SVGElement): The marker element.
 - `padEllipe` (Boolean): If `true`, the line coordinates will be placed with a padding.
 - [`computeLineCoordinates` (Function)](#computelinecoordinatescon)
 - [`update` (Function)](#update)
 - [`setLineColor` (Function)](#setlinecolorcolor-c)

### `computeLineCoordinates(con)`
The function that computes the new coordinates.
It can be overriden with a custom function.

#### Params
- **Connectable** `con`: The connectable instance.

#### Return
- **Object** An object containing the `x1`, `x2`, `y1` and `y2` coordinates.

### `update()`
Updates the line coordinates.

### `setLineColor(color, c)`
Sets the line color.

#### Params
- **String** `color`: The new color.
- **Connectable** `c`: The connectable instance.

## How to contribute
Have an idea? Found a bug? See [how to contribute][contributing].

## License
See the [LICENSE](/LICENSE) file.

[contributing]: /CONTRIBUTING.md
[docs]: /DOCUMENTATION.md