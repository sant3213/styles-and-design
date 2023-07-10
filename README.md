<strong>Flexbox and Grid</strong>

Flexbox controls how items flow in one dimension, whereas Grid controls how items flow in two dimensions.
Flexbox is great at handling alignment, distribution, and order of content and space.
CSS Grid, on the other hand, is suited to lay items out in both dimensions.

The core difference between Flexbox and Grid is that Flexbox lets content size itself based on the space available or the dimensions of the content itself, and Grid specifies nothing about how the individual items themselves should be sized and instead relies on various grid lines being defined on the grid container for its sizing info. 

CSS Grid is more about creating a bunch of virtual areas and then placing all items within them.

Grid Layout basic concepts

CSS Grid like Flexbox, is all about the relationship between a parent container and its child items.
A Grid container (known as the grid) contains what are known as grid items. This grid container establishes a grid context for its children.

A grid is made up of two sets of lines, known as grid lines; one set of lines defines the columns for the grid, these lines run along what is known as the column axis.
Then there is another set of lines that defines the rows for the grid, and these lines run perpendicular to the column axis along what is known as the row axis.

set of lines: columns - rows

columns relate to column axis
rows relate to row axis

These grid lines together make up what are known as grid tracks which is simply a generic term for grid rows or grid columns. They are created by the space between two consecutive row or column lines and are given a size, which controls how tall a row can be or how wide a column can be. 

Where grid rows and grid columns intersect is where we find what are known as grid cells, and these are similar to table cells and are the smallest units of the grid that we can place items into.

Grid Areas are essentially any portiong of the grid that is contained by four grid lines.


.grid-container {
  display: flex;
} 

When using inline-grid, the grid container now takes up only as much space as its items require.
 
.grid-container {
  display: inline-flex;
} 

With grid we need to define columns and rows for our items to be placed within.
grid-template-columns: define our grid columns
grid-template-rows: define our grid rows

The way we that we use these two properties is to define a width for our column or a height for our row, then follow it with another width for another column or a height for another row. and so on, unitil we have the amount of columns and rows that we need.

grid-template-columns: width width;

grid-template-rows: height height;

Placing Grid Items
To control the size of the items, to place our items into these areas that we’ve defined. This is done by specifying at which grid lines they should begin and end. We do this by calling each item individually, giving them:
   grid-column-start
   grid-column-end
   grid-row-start
   grid-row-start


.grid-container {
	display: grid;
	grid-template-columns: 6em 6em 6em 6em;
}

.grid-item {
	grid-column-start: 2;
	grid-column-end: 3;
}
￼

If we want this item to expand two columns, for example, we would just set its grid-column-end to 3.
.grid-item {
	grid-column-start: 2;
	grid-column-end: 3;
}
￼


Grid rows work exactly the same as columns do, except they run horizontally.
We just divide the space just as we did with columns, defining row heights.

.grid-container {
	display: grid;
	grid-template-columns: 6em 6em 6em 6em;
	grid-template-rows: 6em 6em;
}

￼
And now we can give our grid-item grid-row-start and grid-row-end properties

.grid-item {
	grid-column-start: 2;
	grid-column-end: 3;
 	grid-row-start: 1;
	grid-row-end: 3;
}
￼

So there is a grid with cells that are 6em tall and 6em wide. But what if we want some space between the cells?
We can use the gap property.

.grid-container {
	display: grid;
	grid-template-columns: 6em 6em 6em 6em;
	grid-template-rows: 6em 6em;
	gap: 1em;
}

Now if we want a little bit more space between our columns than we do our rows? for this we can switch to the column-gap and row-gap properties.

.grid-container {
	display: grid;
	grid-template-columns: 6em 6em 6em 6em;
	grid-template-rows: 6em 6em;
	row-gap: 1em;
	column-gap: 1.5em;
}

Auto Grid Featues

We may just want to have grid items that are automatically placed into cells on our grid.
If we do not declare item position on the grid, then it will use what is known as the grid auto placement algorithm and automatically size and place items.
You may notice about this autoplacement that the items flow horizontally from left to right along the row axis, and then top bottom. This is because there is a grid-auto-flow property, which defaults to a value of row. 
grid-auto-flow: row; 
￼
If we need to siwtch this, however, we could do so by switching this grid-auto-flow property to a value of column.

.grid-container {
	display: grid;
	grid-template-columns: 6em 6em 6em 6em;
	grid-template-rows: 6em 6em;
	grid-auto-flow: column;
}

￼

If we were to take our second item and set some plcament on it, we can see that it twill move to the location that we defined and it will force all auto placed items to wrap around it accordingly.


.grid-container {
	display: grid;
	grid-template-columns: 6em 6em 6em 6em;
	grid-template-rows: 6em 6em;
	grid-auto-flow: column;
}

.grid-item-02 {
	grid-column-start: 2;
	grid-column-end: 4;
	grid-row-start: 2
	grid-row-end: 2;
}
￼

If we didn’t have the need to resize grid items but just wanted to change the order of them, we can do so using the order property. All items have a default order of 0