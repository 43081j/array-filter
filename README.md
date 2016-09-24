# \<array-filter\>

Provides the ability to filter/sort an array and maintain bindings

## Install

Simply `bower install 43081j/array-filter`, then import `array-filter/array-filter.html`.

## Usage

When filtering/sorting arrays, it is difficult to maintain bindings. The `array-filter`
element ensures that bindings and change paths are linked correctly, allowing for a filtered
and/or sorted copy of an array to remain fully in sync.

This behaves in a similar way to the core `array-selector` element but with
an emphasis on full array operations rather than simple selection.

```html
	<array-filter
		items="{{items}}"
		filtered="{{filtered}}"
		filter="_filter"></array-filter>

	<iron-list items="{{filtered}}">
		<div>{{item.name}}</div>
	</iron-list>
```

As in the example, you can see that `filtered` becomes a fully bound copy
of the initial array with our filter applied.

This works very nicely with elements such as `iron-list` which do not
have their own filtering or sorting logic.

### Observing child sub-properties

Your sort and/or filter function may depend on a particular property
which each child has. If this is the case, you will likely want to
trigger a sort/filter when these properties change.

For this reason, you can use the `observe` propert.

```html
	<array-filter
		items="{{items}}"
		filtered="{{filtered}}"
		observe="name"
		filter="_filter"></array-filter>
```

In the example, any time the `name` property of a child changes, the sort
and filter state will be recomputed.
