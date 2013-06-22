# jQuery ListMenu Plugin

This jQuery plugin, developed in the iHwy Labs, allows you to easily convert a
long, hard to navigate list into a compact, easily skimmable 'first-letter'
based menuing system, allowing quick and 'out-of the-way' access to hundreds
of items. Users hover their mouse over a letter and a columnized list of all
of the list items that start with that letter appear in a submenu. Mousing off
of the letter or menu closes the submenu. Mousing between letters is very fast
and the columns in the submenu are nicely balanced.

This is great for product lists, address books, contact lists, lists of
hotels, parks and recreation areas, etc.

[View the Demos](http://cdn.ihwy.net/ihwy-com/labs/demos/jquery-listmenu.html)

## Highlights

  * Easy to unobtrusively add to existing lists of HTML elements.
  * Works nicely with UL and OL lists as well as any 'list' of HTML elements (child elements under a parent element).
  * Uses the first found letter of "actual text" in each list item (even if the text is nested inside multiple HTML tags) to determine what navigation letter to put the item under.
  * Creates balanced-height columns in the dropdown menu, taking into account the actual height of each element, rather than just going by count.
  * If your list is an OL, numbering in each submenu starts at 1 and is carried across columns, top to bottom, left to right, maintaining a logical sequence.
  * Optional hovering "record count" over each letter shows user how many items are under the letter.
  * Optional '[0-9]' menu item for access to list items that start with a number.
  * Optional '[...]' menu item for access to list items that start with punctuation or chars like &Auml; and &Uuml;.
  * Optionally set the text that appears if a letter with no list items is clicked.
  * Designed with CSS styling in mind. Style all aspects of the list navigation and dropdown menu via CSS.
  * Make letters with no list items appear "disabled" using an optional CSS class.

## More Information

For complete info about how to use this plugin, see the [jQuery ListMenu](http://www.ihwy.com/labs/jquery-listmenu-plugin.aspx) page at the [iHwy, Inc.](http://www.ihwy.com) site.

