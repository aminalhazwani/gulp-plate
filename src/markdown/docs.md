## Layout

To create the structure of your page Gulp Plate provides you with some predefined helper classes. To better recognize them all layout classes are prefixed with `.l-`.

### Sections

You can divide pages in different sections. To create a section use the following markup:

```html
<section class="l-section">
	...
</section>
```

### Containers

To center the content inside a section use a `.l-container` class.

```html
<section class="l-section">
	<div class="l-container">
		...
	</div>
</section>
```

### Grid

Gulp Plate offers you a default grid system of 24 columns with 30px gutters. All grid classes are prefixed with a `.g-` class.

You can change the default values inside `src/sass/base/_vars.scss`.  You can define the number of columns for your grid system as well as the gutter size on different media queries. The dedicated mixin will take care of all classes generation. 

```scss
// _vars.scss

$grid-columns: 24;

$grid-config-xs: (
  "name": "",
  "cols": $grid-columns,
  "gutter": 16px,
  "bp": false,
  "off": false,
  "pull": false,
  "push": false
);

$grid-config-sm: (
  "name": "sm",
  "cols": $grid-columns,
  "gutter": 20px,
  "bp": $bp-sm,
  "off": true,
  "pull": true,
  "push": true
);

$grid-config-md: (
  "name": "md",
  "cols": $grid-columns,
  "gutter": 22px,
  "bp": $bp-md,
  "off": true,
  "pull": true,
  "push": true
);

$grid-config-lg: (
  "name": "lg",
  "cols": $grid-columns,
  "gutter": 30px,
  "bp": $bp-lg,
  "off": true,
  "pull": true,
  "push": true
);
```

But lets see how we can use these generated classes. To create a grid you have to wrap all grid units in a `.g-row` class:

```html
<div class="g-row">
	Grid columns go here.
</div>
```

Grid columns need the base grid class `.g` and a width definiton e.g. `.g-12`:

```html
<div class="g-row">
  <div class="g g-12">Span 12 columns</div>
  <div class="g g-12">Span 12 columns</div>
</div>
```

If the columns need to change depeneding on the screen size you can use a **width key** in the class name.

The default keys are:

- `-sm-` Small screens start at a browser width of 768px
- `-md-` Medium screens start at a browser width of 966px
- `-lg-` Large screens start at a browser width of 1290px

You can change them always inside `_vars.scss`.

If no **width key** is given the rule will apply from 0px onward. See the example below to get a better impression:

```html
<div class="g-row">
  <div class="g g-12 g-sm-8 g-md-4 g-lg-2">
    span 12 columns on mobile
    span 8 columns on small screens
    span 4 columns on medium screens
    span 2 columns on large screens
  </div>
  <div class="g g-12 g-sm-16 g-md-20 g-lg-22">
    span 12 columns on mobile
    span 16 columns on small screens
    span 20 columns on medium screens
    span 22 columns on large screens
  </div>
</div>
```

By default grid units span 24 columns (100% width), if you want the columns to span 12 starting on medium sized screens only add classes for that size:

```html
<div class="g-row">
  <div class="g g-md-12">
    span 24 columns on mobile
    span 24 columns on small screens
    span 12 columns on medium screens
    span 12 columns on large screens
  </div>
</div>
```

#### Offset

The grid system includes offset classes to create spacing:

```html
<div class="g-row">
  <div class="g g-12 g-off-4">
    span 12, start after the 4 col
  </div>
</div>
```


#### Clearing floats
...

## Utility classes

These classes provide a fast way to create new layouts without much effort. All utility classes, with the exception of headings, are prefixed with `.u-`. Most utility classes are responsive which means that you can combine them with a **width key** (`-sm-`, `-md-`, `-lg-`) to target different screen sizes.

### Dimensions

Dimension utilities help you handle whitespace between elements. Classnames are composed by:

- utility prefix `.u-`
- width key `sm-`, `md-` or `lg-`
- property name `push-`, `pull-` or `padd-`
- property position `top-`, `rgt-`, `btm-`, `lft-`, `horz-` or `vert-`
- property value `none`, `quarter`, `half`, `double`

The base dimesion `$space` is defined as always in the `_vars.scss`. The default value is 24px.

It may sounds complicated but it isn't at all. Let's try to see this class naming in action:

```html
<div class="u-md-push-btm u-lg-push-btm-double">
  margin bottom of 24px on medium screens
  margin bottom of 48px on large screens
</div>
```

When not defined the **property position** is applied to all position: top, right, bottom and left. 

When not defined the **property value** is equal to the base dimension `$space`, in our case 24px. If you would like to remove it simply add the property valur `-none`:

```html
<div class="u-md-push-none">
  margin bottom of 0px
</div>
```

