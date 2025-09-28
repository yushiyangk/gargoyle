## Changelog


### 0.5

#### Breaking changes

- Renamed the variable `--g-demi-font-size` to `--g-demi-relative-font-size`, and changed its default value's unit from `rem` to `em`
- Renamed the variable `--g-inverse-demi-font-size` to `--g-inverse-demi-relative-font-size`, and changed its default value's unit from `rem` to `em`
- Renamed the variable `--g-inline-border-radius-line-height-compat` to `--g-inline-border-radius-monospace-line-height-compat`

These changes are breaking if and only if the old variable names have been overwritten

#### Added

- Added customisable variables for relative font size changes in `<abbr>` and `<kbd>` inside headings:
	- `--g-h1-demi-relative-font-size`
	- `--g-h1-inverse-demi-relative-font-size`
	- `--g-h1-demi-font-weight`
	- `--g-heading-demi-relative-font-size`
	- `--g-heading-inverse-demi-relative-font-size`
	- `--g-heading-demi-font-weight`
	- The default values for these are set to `var(--g-demi-relative-font-size)`, `var(--g-inverse-demi-relative-font-size)` and `var(--g-demi-bold-font-weight)` respectively (same behaviour as before, notwithstanding the breaking change above)
- Added customisable variables for heading line heights (in addition to that for `<h1>` which was already present):
	- `g-h2-line-height`
	- `g-h3-line-height`
	- `g-h4-line-height`
	- `g-h5-line-height`
	- `g-h6-line-height`
	- The default values for these are all set to `var(--g-line-height)` (same behaviour as before)
- Added customisable variables for monospace font size and line height:
	- `--g-monospace-font-size`, set to `var(--g-font-size)` by default (same behaviour as before)
	- `--g-monospace-line-height`, set to `var(--g-line-height)` by default (same behaviour as before)
- Added styles for `<tt>`, to use the new monospace variables also


### 0.4.4

- Fixed variables for button colours not being applied to built-in icon types

### 0.4.3

- Changed scrolling behaviour of wide tables
	- Removed `overflow-x: auto` from `<table>` elements
	- It will now rely on horizontal scrolling of the page itself rather than rendering its own scrollbars

### 0.4.2

- Added current version number to `gargoyle.css`
- Fixed incorrect variable used for main text colour

### 0.4.1

- Changed all CSS variables to add the prefix `--g-`

### 0.4

#### Added

- Added CSS variables for easier customisation of the stylesheet for individual sites
	- Most derived values are automatically computed using `calc()`
	- **Note**: media queries cannot be automatically computed from variables, and must be manually updated to the appropriate value in `px`; the variables that each media query uses is indicated beside it.
	- **Note**: in order to support IE 11, each derived value is separately defined as a variable ending in `-compat`, which should be updated manually; the variables that each `-compat` variable depends on is indicated beside it.
- Compatibility check and a fallback implementation for thumbnail lists
	- Fallback avoids using Grid Layout as it is poorly supported by IE 11
	- Fallback will be used for IE 11 and Edge 18 (the latter due to it not supporting `display: content`)

#### Changed

- Use `gap` property for Grid Layout instead of the older `grid-gap` (the older property name is still used for iOS Safari 11.2)
- Use `overflow-wrap` property instead of the older `word-wrap` (the older property name is still used for IE 11)

#### Removed

- Dropped support for browsers with less than 0.1% global user share as of May 2025. The **earliest supported** browsers are now:
	- Google Chrome 109
	- Edge 18
	- Safari 15.6
	- Firefox 115
	- Opera 117
	- IE 11
	- Google Chrome Android 135
	- iOS Safari 11.2
	- Samsung Internet 27
	- Opera Mobile 80
	- Android Browser 135
	- Firefox Android 137
- Removed the following fallbacks for old browsers:
	- fallback for `vw` units
	- fallbacks for `transform: translate()` in figures and action buttons
	- fallback for `display: inline-flex` or `display: -ms-inline-flexbox` in inline lists
	- fallback for `counter-reset`, `counter-increment` properties and `counter()` function in inline lists
	- `-moz-hyphens: auto` and `-ms-hyphens: auto` properties
	- `-moz-tab-size` and `-o-tab-size` properties
	- `width: -moz-max-content`, `width: -webkit-max-content` and `width: intrinsic` (used by Safari before version 11)
	- `-moz-border-radius` and `-webkit-border-radius` properties
	- `display: -ms-inline-flexbox` and `display -webkit-inline-flex` in inline lists
	- `-webkit-flex` property
	- `white-space: -moz-pre-wrap`, `white-space: -pre-wrap` and `white-space: -o-pre-wrap`


#### Fixed

- Incorrect stylesheet breakpoints due to using `rem` units in media queries (`rem` uses the browser default font size instead of that defined in the stylesheet)
- Missing hover effect in uncoloured action buttons
- Misaligned icons on hover or focus in custom action buttons that were aligned with `g-right`
- Overly vertically cramped `<kbd>` elements
- Incorrect size of initial capital letter when the `g-capital` class was added to an `<abbr>` element or an element with the `g-abbr` class

### 0.3.9

- Changed the `g-continue` class for `<ol>` elements so that list numbering is continued
- Fixed vertical margins in lists with `g-continue` not being symmetrical
- Fixed unwanted hover effects in images in the labels of custom action buttons

### 0.3.8

- Undo the change in version 0.3.7
- Added explicit styles for `<abbr>` to show a dotted underline when the `title` attribute is defined
- Added the `g-abbr` class, which c an be added to any element to also show a dotted underline when the `title` attribute is defined

### 0.3.7

- Fixed the simulated smallcaps in `<abbr>` not being of the appropriate size when nested inside elements with small text

### 0.3.6

- Changed the `g-continue` class so that it merely reduces vertical margins of the list, rather than completely eliminating them

### 0.3.5

- Set the `position` property of `<ul>`, `<ol>` and `<dl>` elements back to `position: inline-flex`, as they were before version 0.3
	- While they may not be nested inside `<p>`, they can still be nested inside other inline contexts, e.g. `<td>`

### 0.3.4

- Fixed `<kbd>` not being bolded when nested inside an otherwise bolded element
- Tweaked horizontal spacing of action buttons to use `rem` units instead of `em`

### 0.3.3

- Added the `g-quiet` class, which can be added to any element to de-emphasise its text

### 0.3.2

- Increased vertical margins of thumbnail lists
- Removed vertical margins for `<p>` and `<h1>` through `<h6>` elements when nested inside a thumbnail list

### 0.3.1

- Changed text hyperlinks to double underline on hover instead of hiding the underline as before
- Added hover effects for images, i.e. `<image>`, `<picture>` and `<svg>` elements
	For images with `g-frame`, hide the frame on hover
- Fixed images in `<a>` in `<figure>` not being centred and ignoring `g-bound`

#### Thumbnail lists

- Revamped thumbnail lists, which can now be achieved by adding the `g-thumbnail` class to `<dl>` only
	- Each `<dt>` defines a thumbnail
	- Each `<dd>` defines the content of the list item
	- Either or both may be nested in `<a>`
- Added hover effects for thumbnail list items
- Removed support for `<ul>` thumbnail lists

### 0.3

#### Highlights

- Custom and predefined action buttons, fully animated
- Floating action buttons on images
- Automatically numbered sections
- Code and output blocks with display titles
- Margin annotations using `<aside>`
- Simplified the installation to a single `.css` file

#### Sections

- Added the `g-counter1` through `g-counter6` classes for `<section>` elements, which causes nested heading elements (`<h1>` through `<h6>`) to be prepended with a section number
	- The number in the class, e.g. 2 in `g-counter2`, corresponds to the lowest heading level that should be included in the section number; any heading levels lower than that would not be counted and would not be part of the section number
- Added the `g-nocount` class for heading elements, `<h1>` through `<h6>`, which disables section numbering for that heading and does not increment the section number

#### Asides

- Added support for text annotations outside the main content column, using the `<aside>` element when nested inside `<main>`
	- If the viewport is not wide enough, the contents of the `<aside>` will be placed in the main column as usual

#### Lists

- Added support for `<menu>` elements, which are treated identically to `<ul>` elements
- Fixed the margins of nested lists so that top and bottom vertical margins of nested lists are now symmetrical
- Made `<dt>` elements bold by default
- For inline lists, i.e. `<ul>`, `<ol>` and `<dl>` elements (and the new `<menu>` elements) with class `g-inline` or `g-subinline`,
	- Set them to `display: flex` instead of `display: inline-flex` by default because list elements cannot be inside `<p>` even when inline
	- Made the separator dots slightly larger to be more visible
	- Fixed the missing separator dots for inline `<dl>` elements
	- Defined new counters, `inline-list` and `subinline-list` for inline `<ol>` elements, to better support behavioural tweaks that are separate from regular lists
- Added support for thumbnail lists, achieved by adding the `g-thumbnail` class to `<ul>`, `<menu>` or `<dl>`
	- These behave similarly to `<dl>`, where a `<img>`, `<picture>` or `<svg>` should be defined before every `<li>` or `<dt>`
	- The `g-thumbnail` class should also be added to every `<img>`, `<picture>` or `<svg>`
	- Any of these may be nested inside `<a>`

#### Action buttons

- Added the ability to set an action button to a specific colour, using the classes `g-green`, `g-cyan`, `g-blue`, `g-magenta`, `g-red`, `g-orange` or `g-yellow` (for `<a>` used in tandem with `g-button`)
- Added predefined action buttons complete with corresponding animated icons in the same manner as `g-go` from before, using the classes `g-send`, `g-upload`, `g-download`, `g-okay`, `g-cancel`, `g-back`, `g-star` or `g-delete` (for `<a>` used in tandem with `g-button`)
	- The SVG icons are fully embedded in CSS, obviating the need for additional files which includes `icons/go.svg` from before
- The colours of the predefined actions can be overridden using the one of the colour classes on top of the appropriate action class and `g-button`
- Multiple buttons can be placed in a row using the `<nav>` element when nested inside `<main>`
- Added the ability to define custom action buttons with animated icons, using the `g-icon` class together with the `g-left` or `g-right` classes
	- `g-left` or `g-right` should be added to an `<a>` that is an action button (i.e. already has the `g-button` class), which specifies which side the icon should be placed on
	- `g-icon` should be added to any element nested within the `<a>`, and that element will be used as the icon and automatically animated
	- The colour of the action button can be customised as above
	- The `<a>` element *cannot* have one of the predefined action classes

#### Figures, images and tables

- Added support for `<svg>` elements, which are treated identically to `<picture>` elements (or `<img>` elements that are not nested in a `<picture>`)
- Added support for `<a>` elements inside `<figure>`, and for nesting `<img>`, `<picture>`, `<svg>` or `<table>` inside `<a>` inside `<figure>`
- Added support for inline images, which are achieved by adding the `g-inline` class to `<img>`, `<picture>` or `<svg>`
- Added the `g-frame` class for `<img>`, `<picture>` and `<svg>` elements, which adds a noticeable border (useful for e.g. transparent images)
- For `<img>`, `<picture>`, `<svg>` and `<table>` elements inside `<figure>`
	- Set the maximum width of the contents of `<figure>` to be the viewport width minus a small fixed margin
	- Set the maximum width of the corresponding `<figcaption>` to slightly narrower than the main column width
	- Added support for the `g-left` and `g-right` classes for `<figure>`, which causes its contents, including `<figcaption>`, to be aligned accordingly (can also be used in tandem with `g-bound` to align with the main column rather than the viewport)
- For bare `<img>` elements,
	- Changed them to be flush left instead of centred
	- Added vertical margins like other block-level elements
	- Set their maximum width to be the containing content width
- For `<th>` and `<td>` elements, added the `g-center` class as an alias of `g-centre`

#### Floating action buttons on images

- Added support for floating action buttons on images, achieved by adding the `g-button` class to an `<a>` element nested inside `<picture>`
- Predefined floating action buttons are available, using the `g-external` and `g-expand` classs on `<a>` in tandem with `g-button`
- Floating action buttons are placed on the bottom right corner by default
- The placement of the buttons can be set by adding the `g-left` or `g-right` classes to `<picture>` (as distinct from adding it to `<figure>`, described in the next section)
- Multiple buttons can be added by nesting the `<a>` inside `<nav>` then inside `<picture>`
	- Buttons are placed in a row at the bottom, starting from the right by default
	- Buttons may form additional rows, from the bottom upwards, if the width of the image cannot contain them all
	- The `g-vertical` class can be added to `<picture>`, which causes the buttons to be placed in a column on the right by default, starting from the top; they may form additional columns, leftwards by default
	- In any of the above, left or right placement can be set by adding the classes `g-left` or `g-right` to `<picture>`

#### Code and output blocks

- Added support for block-level `<code>` and `<samp>` elements, which are achieved by nesting each in `<pre>`
	- A title for each block can be displayed by setting the `title` attribute of `<code>` or `<samp>` (useful for e.g. displaying a file name or a console command)
	- Long lines will cause the block to extend to beyond outside the main column on one side
- Block-level `<code>` and `<samp>` elements can be further nested inside `<figure>`, i.e. `<code>` or `<samp>` inside `<pre>` inside `<figure>`
	- For blocks containing long lines, this causes the block to be centred, extending outside the main column on both sides instead of just one side
	- The `g-bound` class can be added to `<figure>`, which forces line wrapping in blocks instead of allowing them to extend outside the main column

#### Mathematics

- Added support for basic mathematical notation
	- Added the `g-math` class, which sets the font to serif instead of the default sans-serif
	- Added the `g-mathrm` and `g-mathbf` classes, which sets the font to upright (non-italic) and bold respectively
	- These classes are meant to be used with the `<var>` element, which in most browsers sets the font to italic by default
- However, MathML should be used instead if possible, and `demo.html` is updated to state this as well

#### Other changes

- Added basic styles for the inline elements `<dfn>`, `<kbd>`, `<samp>`, `<sup>`, `<sub>`
	- Show a pretty but unobstrusive keycap outline for `<kbd>`
- Added basic styles for `<blockquote>` elements
- Changed `<abbr>` to no longer use the smallcap feature in fonts by default, and instead to approximate smallcaps in the manner described when smallcaps were introduced in version 0.1.3
	- As mentioned then, many fonts do not support smallcaps in the appropraite way, and this change to default behaviour is made in recognition of that
- Significantly expanded `demo.html` to illustrate the new features

### 0.2.5

- Fixed `<table>` elements inside `<figure>`, which previously were rendered with extremely wide top and bottom borders
- Enabled horizontal scrolling for extremely wide `<table>` elements
- Set the maximum width of `<img>`, `<picture>` and `<table>` when inside a `<figure>` to be close to the viewport width
- Added the `g-left`, `g-right` and `g-centre` classes for `<th>` and `<td>` elements, which sets the text alignment in the table cell
- Fixed the `g-bounded` class so that it applies to `<picture>` elements as well, instead of just `<img>` and `<table>` elements

### 0.2.4

- Reduced the maximum vertical size of `<img>` and `<picture>` elements when bounded by the viewport
- Updated `demo.html` to better demonstrate figure sizing using the `g-bounded` class, and added the previously missing demo image `gray-tree.jpg`

### 0.2.3

- Added basic styles for `<aside>` elements
- Added basic styles for plain `<ul>`, `<ol>` and `<dl>` elements, as well as their contained `<li>`, `<dt>` and `<dd>` elements

### 0.2.2

- Tweaked vertical spacing of action buttons to better fit the baseline grid

### 0.2.1

- Changed bare `<img>` elements to have no vertical margins by default (bare `<picture>` elements or either inside a `<figure>` are unchanged)

### 0.2

#### Added

- Inline lists, using the `g-inline` and `g-subinline` classes on `<ul>`, `<ol>` or `<dl>` elements
- Basic font styles for `<small>` elements

#### Changed

- Bare `<img>`, `<picture>` and `<table>` elements are now centred by default
- Adjusted vertical spacing of tables to better fit the baseline grid
- Increased vertical margin between `<figcaption>` elements and any of `<img>`, `<picture>` or `<table>` inside a `<figure>`

### 0.1.7

- Default font tweaks
	- Changed `<h1>` from serif to sans-serif, in line with all other elements
	- Increased the font sizes of `<h2>` through `<h6>`

### 0.1.6

- Reorganised the installation to move the SVG for the Go button to an `icons` subdirectory

### 0.1.5

- Added explicit rules for the default display properties of various content elements, for the sake of old browsers that do not recognise newer HTML5 elements
- Added basic margins for `<picture>` elements, identical to bare `<img>` elements
- Improved browser support for the green Go button specified by the `g-go` class
- Added a simple Readme

### 0.1.4

- Added two classes for `<a>` elements:
	- `g-button`, to turn it into an action button
	- `g-go`, used in tandem with `g-button` to turn it into a green Go button with an animated right arrow
- The installation now consists of two files, namely the stylesheet and an SVG for the Go button, instead of just the stylesheet

### 0.1.3

- `<abbr>` elements now automatically convert uppercase to smallcaps
	- This assumes that the font used comes with smallcaps that are appropriately-sized for inline abbreviations, which should be slightly larger than x-height while being smaller than regular cap height. Unfortunately, many fonts only provide petit caps which are much closer to x-height, which are more appropriate for replacing lowercase letters in headings. In such cases, the appropriate smallcaps glyphs should be approximated using full capitals at a slightly smaller font size and a slightly heavier weight, if possible, or else the smallcaps should be disabled entirely.
- Added the `g-capital` class for `<abbr>` elements, which sets the first letter to be a full-sized capital, intended for `<abbr>` elements at the start of a sentence or in title-cased contexts

### 0.1.2

- Body text is now sans-serif by default
- `<h1>` text is now explicitly serif by default
- Reduced line-height of `<code>` elements to account for the extra height from its border radius

### 0.1.1

- `<img>` elements are now bounded by viewport height
- Changed bare `<table>` elements to be flush left instead of being centred
- `<table>` elements inside `<figure>` are now centred

### 0.1

- Initial version
