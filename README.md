Yet another flexible, percentage-based grid, with [BEM](http://bem.info/)-style class naming. *Only this one is made of pizza.*

## Usage

### .grid

The block in our grid system, the `.grid` class is the main container for any number of child `.grid__cell` elements. You can think of it as a row, but be aware that `.grid__cell`s will wrap, so there can be many visual "rows" of content inside of a single `.grid`. `.grid` and `.grid__cell` elements are also infinitely nestable. `.grid__cell`s are the primary child element of the `.grid` block, this class will most often be used with `--[width]` or `--[device]` modifiers. Width classes will set the percentage width of `.grid__cell`s. Named with human-readable proportions, so that you can easily predict how much of the parent block's width the element will fill.

```html
<div class="grid">
	<div class="grid__cell--one">One</div>

	<div class="grid__cell--one-half">One half</div>
	<div class="grid__cell--one-half">One half</div>

	<div class="grid__cell--one-third">One third</div>
	<div class="grid__cell--one-third">One third</div>
	<div class="grid__cell--one-third">One third</div>

	<div class="grid__cell--one-quarter">One quarter</div>
	<div class="grid__cell--one-quarter">One quarter</div>
	<div class="grid__cell--one-quarter">One quarter</div>
	<div class="grid__cell--one-quarter">One quarter</div>

	<div class="grid__cell--one-fifth">One fifth</div>
	<div class="grid__cell--one-fifth">One fifth</div>
	<div class="grid__cell--one-fifth">One fifth</div>
	<div class="grid__cell--one-fifth">One fifth</div>
	<div class="grid__cell--one-fifth">One fifth</div>

	<div class="grid__cell--one-sixth">One sixth</div>
	<div class="grid__cell--one-sixth">One sixth</div>
	<div class="grid__cell--one-sixth">One sixth</div>
	<div class="grid__cell--one-sixth">One sixth</div>
	<div class="grid__cell--one-sixth">One sixth</div>
	<div class="grid__cell--one-sixth">One sixth</div>

	<div class="grid__cell--one-eighth">One eighth</div>
	<div class="grid__cell--one-eighth">One eighth</div>
	<div class="grid__cell--one-eighth">One eighth</div>
	<div class="grid__cell--one-eighth">One eighth</div>
	<div class="grid__cell--one-eighth">One eighth</div>
	<div class="grid__cell--one-eighth">One eighth</div>
	<div class="grid__cell--one-eighth">One eighth</div>
	<div class="grid__cell--one-eighth">One eighth</div>
</div>
```

####Nested `grid`s

You can nest additonal `grid` blocks inside of `grid__cell`s. Be aware that `grid__cell` widths are percentage-based and are calculated based on their parent element's width.

```html
<div class="grid">
	<div class="grid__cell--one-half">
		<div class="grid">
			<div class="grid__cell--one-half">One half</div>
			<div class="grid__cell--one-half">One half</div>
		</div>
	</div>
	<div class="grid__cell--one-half">One half</div>
</div>
```

###Modifiers

There are a handful of built-in modifier classes for both the `grid` and `grid__cell` elements. Feel free to extend the base elements with additional modifier classes.

####`.grid--center`

By default, all `grid__cell`s are left-aligned, and, predictably, this will center them (but will not center the text within them).

####`.grid--no-gutter`

Removes the 2.5% margin between all `grid__cell`s so that they fit tight up against each other.

####`.grid__cell--offset-[width]`

Offsets an individual cell the specified distance from either the left border of the `grid` or its nearest preceeding `grid__cell`.

```html
<div class="grid">
	<div class="grid__cell--one-third grid__cell--offset-one-sixth">One third, offset by one sixth</div>
</div>
```