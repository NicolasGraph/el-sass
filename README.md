# Oui_grid

## In process!

A sass powered css responsive grid using [flexbox](http://caniuse.com/#feat=flexbox) and [calc()](http://caniuse.com/#search=calc).
Click these features for support informations via [caniuse.com](http://caniuse.com/).

## Features

* Unlimited columns width;
* unlimited breakpoints;
* responsive gutters;
* gutters as margin and/or padding;
* etc.

## Variables settings

See `src/settings/variables.scss`.

### $layout

```scss
$layout: (
    s: (
        content-max-width : 480px,
        vertical-spacing  : 12px,
        horizontal-spacing: 8px
    ),
    m: (                           // Each $layout key is used as a breakpoint.
        device-min-width  : 640px, // Media-query min-width; also generates the max-width of the previous breakpoint.
        content-max-width : 800px, // Max-width to optionally apply to containers
        vertical-spacing  : 16px,  // Top and bottom gutters
        horizontal-spacing: 12px   // Right and left gutters
    ),
    …
);
```

## Mixins

### item

```scss
@include item($media, $width, $margin, $padding, $position, $flow);
```

#### item arguments

- `$media` (`null`): media-query min-width and/or max-width as `$layout` map keys.
```scss
@include item(s) { … };
@include item(s l) { … };
@include item(false l) { … };
```
- `$width` (`null`): fraction of factor of the container width.
You can also use `true` to apply a width of 100% and a max-width of the `$max-content-width` responsive value.
```scss
@include item(s l, 1/2) { … };
@include item(s l, .5) { … };
```
- `$margin` (`null`): value or list of two or four values.
  - `true` or `false` will enable or disable the responsive gutter;
  - `nested` will be read as a factor of `-1` of the responsive gutter (see the next list item);
  - a unitless value will be read as a factor of the responsive gutter;
  - a usual margin value followed by its unit will be used as it.
```scss
@include item(s l, 1/2, true) { … };
@include item(s l, 1/2, 2 -1) { … };
@include item(s l, 1/2, 1px 2px 3px 4px) { … };
```
- `$padding` (`null`): see `margin`.
```scss
@include item(s l, 1/2, true, true) { … };
@include item(s l, 1/2, true, 1 -1) { … };
@include item(s l, 1/2, true, 1px 2px 3px 4px) { … };
```
- `$position` (`null`): `pull-` or `push-` followed by a fraction of the container width.
```scss
@include item(s l, 1/2, true, true, push-1/2) { … };
```
- `flow` (`null`): …
```scss
@include item(s l, 1/2, true, true, push-1/2, grid) { … };
```

### children

```scss
@include children($media, $width, $margin, $padding, $position, $padding);
```

#### children specific changes

- `$width` (`null`): factor (.5) or fraction (1/2) of the parent width.
```scss
@include children(s l, 1/2) { … };
@include children(s l, 1/2 1/4) { … };
```
- `$repeat` (`null`): extra value for `$width` to define the repeat scheme to use.
```scss
@include children(s l, 1/2 1/4 repeat-last) { … };
```

## Author

[Nicolas Morand](https://twitter.com/NicolasGraph)

## Licence

This project is distributed under the [MIT licence](https://opensource.org/licenses/MIT).

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
