Yet another flexible, percentage-based grid, with [BEM](http://bem.info/)-style class naming. *Only this one is made of pizza.*

Because of our project requirements, the media queries are arranged "desktop first," using `max-width`-based queries to activate the rulesets for additional smaller screen devices.

## Usage

### .grid

The block in our grid system, the `.grid` class is the main container for any number of child `.grid__cell` elements. You can think of it as a row, but be aware that `.grid__cell`s will wrap, so there can be many visual "rows" of content inside of a single `.grid`. `.grid` and `.grid__cell` elements are also infinitely nestable. `.grid__cell`s are the primary child element of the `.grid` block, this class will most often be used with `--[width]` or `--[device]` modifiers.Width classes will set the percentage width of `.grid__cell`s. Named with human-readable proportions, so that you can easily predict how much of the parent block's width the element will fill.