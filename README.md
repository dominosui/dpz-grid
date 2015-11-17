Yet another flexible, percentage-based grid, with [BEM](http://bem.info/)-style class naming. *Only this one is made of pizza.*

## Usage

### .grid

The block in our grid system, the `.grid` class is the main container for any number of child `.grid__cell` elements. You can think of it as a row, but be aware that `.grid__cell`s will wrap, so there can be many visual "rows" of content inside of a single `.grid`. `.grid` and `.grid__cell` elements are also infinitely nestable. `.grid__cell`s are the primary child element of the `.grid` block, this class will most often be used with `--[width]` modifiers and `@[device]` scoping suffixes. Width classes will set the percentage width of `.grid__cell`s. Named with human-readable proportions, so that you can easily predict how much of the parent block's width the element will fill.

```html
<div class="grid">
	<div class="grid__cell--1">One</div>

	<div class="grid__cell--1/2">One half</div>
	<div class="grid__cell--1/2">One half</div>

	<div class="grid__cell--1/3">One third</div>
	<div class="grid__cell--1/3">One third</div>
	<div class="grid__cell--1/3">One third</div>

	<div class="grid__cell--1/4">One quarter</div>
	<div class="grid__cell--1/4">One quarter</div>
	<div class="grid__cell--1/4">One quarter</div>
	<div class="grid__cell--1/4">One quarter</div>

	<div class="grid__cell--1/5">One fifth</div>
	<div class="grid__cell--1/5">One fifth</div>
	<div class="grid__cell--1/5">One fifth</div>
	<div class="grid__cell--1/5">One fifth</div>
	<div class="grid__cell--1/5">One fifth</div>

	<div class="grid__cell--1/6">One sixth</div>
	<div class="grid__cell--1/6">One sixth</div>
	<div class="grid__cell--1/6">One sixth</div>
	<div class="grid__cell--1/6">One sixth</div>
	<div class="grid__cell--1/6">One sixth</div>
	<div class="grid__cell--1/6">One sixth</div>

	<div class="grid__cell--1/8">One eighth</div>
	<div class="grid__cell--1/8">One eighth</div>
	<div class="grid__cell--1/8">One eighth</div>
	<div class="grid__cell--1/8">One eighth</div>
	<div class="grid__cell--1/8">One eighth</div>
	<div class="grid__cell--1/8">One eighth</div>
	<div class="grid__cell--1/8">One eighth</div>
	<div class="grid__cell--1/8">One eighth</div>
</div>
```

####Nested `grid`s

You can nest additonal `grid` blocks inside of `grid__cell`s. Be aware that `grid__cell` widths are percentage-based and are calculated based on their parent element's width, so a nested `grid__cell--1/2` will not be the same rendered width as one that is not nested within a `grid__cell`.

```html
<div class="grid">
	<div class="grid__cell--1/2">
		<div class="grid">
			<div class="grid__cell--1/2">One half</div>
			<div class="grid__cell--1/2">One half</div>
		</div>
	</div>
	<div class="grid__cell--1/2">One half</div>
</div>
```

###Modifiers

There are a handful of built-in modifier classes for both the `grid` and `grid__cell` elements. Feel free to extend the base elements with additional modifier classes.

####`.grid--center`

By default, all `grid__cell`s are left-aligned, and, predictably, this will center them (but will not center the text within them).

```html
<div class="grid grid--center">
    ...
</div>
```

####`.grid--no-gutter`

Removes the 2.5% margin between all `grid__cell`s so that they fit tight up against each other.

```html
<div class="grid grid--no-gutter">
    ...
</div>
```

####`.grid__cell--offset-[width]`

Using the same human-readable proportions that define the cell width, it offsets an individual cell the specified distance from either the left border of the `grid` or its nearest preceeding `grid__cell`.

```html
<div class="grid">
	<div class="grid__cell--1/3 grid__cell--offset-1/6">One third, offset by one sixth</div>
</div>
```

####Device type suffixes

DPZ Grid includes built in suffixes for handheld, tablet, and widescreen device types (following the format `.grid__cell--[width]@[device-type]`), but you can create your own device types as well. The simplest implementation is to `@import` the new files based on media queries like the following contrived example:

```css
@import url("l.grid-tablet.css") screen and (max-width: 54em);
@import url("l.grid-handheld.css") screen and (max-width: 40em);
```

Depending on how your media queries are organized (mobile first vs "desktop" first), make sure that the files are included in the correct order. Once a media query is matched, the corresponding device type suffixed classes will be activated and will override the base `grid__cell` class. In the following example, when no media queries are matched, the `grid__cell`s will take up one half of the parent container's width, and when the media query that includes the "handheld" suffixed classes is matched, the cells will fill the entire width and stack on top of each other.

```html
<div class="grid">
	<div class="grid__cell--1/2 grid__cell--1@handheld">...</div>
	<div class="grid__cell--1/2 grid__cell--1@handheld">...</div>
</div>
```

####Utility

A more semantically named state class, `is-hidden` replaces the deprecated `grid__cell--none` classes. This class can be used with device type suffixes as well.

```html
<div class="grid">
	<div class="grid__cell--1/2 is-hidden@handheld">...</div>
</div>
```