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

[View the Demos](http://www.ihwy.com/Labs/demos/current/jquery-listmenu-plugin.aspx)

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

Multiple [demos](http://www.ihwy.com/Labs/demos/current/jquery-listmenu-plugin.aspx) are available to
help you implement the plugin.

## Requirements

This plugin was developed and tested using jQuery 1.3.2 and tested using that
and jQuery 1.2.6. We recommend using [jQuery 1.3.2](http://www.jquery.com/) or
higher for the best performance.

## Supported Browsers

We tested this plugin on Firefox 3.x (Windows/Mac), IE6, IE7, IE8/rc
(Windows), Safari (Mac 3.2.1, Windows 4.0 beta), Google Chrome (Windows) and
Opera 9.6.3 (Windows).

## Usage

1. Include jquery and the listmenu plugin in your page:
    
    
      <script type="text/javascript" src="js/lib/jquery-1.3.2.min.js"></script>
      <script type="text/javascript" src="js/lib/jquery.listmenu-1.1.js"></script>
    

> (adjust the src path for the files based on where your files are located)

2. Add some HTML for your list. Your list wrapper **must** have an id attribute. For example:
    
    
      <ul id="myList">
        <li><a href="#">A item</a></li>
        <li><a href="#">B item</a></li>
        <li><a href="#">C item</a></li>
        etc...
      </ul>
    

> See the demos for more examples of the HTML you can use (other than UL >
LI). Note: the # href's above are just placeholders. You would use your actual
href's in those. Any HTML can be used inside of your list items.

3a. Create your listmenu using the defaults (here wrapped in the jQuery
document ready function):

    
    
      <script type="text/javascript">
        $(function(){
          $('#myList').listmenu();
        });
      </script>
    

3b. Or override some of the defaults. Here we're overriding all of them:

    
    
      <script type="text/javascript">
        $(function(){
          $('#myList').listmenu({
            includeNums: false,
            includeOther: true,
            flagDisabled: false,
            noMatchText: 'No items under this letter',
            showCounts: false,
            menuWidth: 825,
            cols:{
              count: 5,
              gutter: 15
            },
            onClick:function($target){
             if($target.is('a')){
              alert($target.text() + ' was clicked');
             }
            }
          });
        });
      </script>
    

Note: you can use any jQuery selector with .listmenu(). For example, if you
have two lists on a page and you want to activate them both using the same
listmenu options and both have the 'list' class on them, you could do:

    
    
      <script type="text/javascript">
        $(function(){
          $('.list').listmenu(); // set any options you want for all lists with the 'list' class
        });
      </script>
    

## Options

The iHwy listmenu plugin uses defaults that will work well for many
situations, but you can modify the defaults to suit your needs. See the
[demos](http://www.ihwy.com/Labs/Demos/Current/jquery-listmenu-plugin.aspx) for examples of overriding
the defaults.

<table class="options">
	<tbody>
		<tr>
			<th>Option</th>
			<th>Default</th>
			<th>Description</th>
		</tr>	
		<tr>
			<td>includeNums</td>
			<td>true</td>
			<td>true = show the [0-9] navigation item in the menu bar.<br/><br/>false = do not show the [0-9] navigation item. You may want to use this if your list does not contain items that start with a number.</td>
		</tr>
		<tr>
			<td>includeOther</td>
			<td>false</td>
			<td>true = show the [...] navigation item in the menu bar.<br/><br/>false = do not show the [...] navigation item. You may want to use this if your list contains items that start with punctuation or characters other than A-Z and 0-9 (like \u221a\u00d1 and \u221a\u00fa).</td>
		</tr>
		<tr>
			<td>flagDisabled</td>
			<td>true</td>
			<td>true = apply the disable class ('lm-disabled' - see the CSS in the demos) to letters in the navbar that have no entries in the list. Use this to make those letters look 'disabled' (typically grayed out).<br/><br/>false = do not to apply the style: letters with no items will look the same as letters with items.</td>
		</tr>
		<tr>
			<td>noMatchText</td>
			<td class="nowrap">'No matching entries'</td>
			<td>This is the text that appears in place of the list if the user clicks a letter that has no matching entries. Set this to your own text to override the default.</td>
		</tr>
		<tr>
			<td>showCounts</td>
			<td>true</td>
			<td>true = show the numerical count above each letter when they are moused-over.<br/><br/>false = do not show the counts.</td>
		</tr>
		<tr>
			<td>menuWidth</td>
			<td>null</td>
			<td>The plugin calculates a width for the dropdown submenu using the inner width of the HTML container that the listmenu control is in. Include this option with a numeric value if you want to force the width of the dropdown menu to a specific width.</td>
		</tr>
		<tr>
			<td>cols</td>
			<td>{count:4, gutter:40}</td>
			<td>By default the list items under each navigation letter are converted into 4 columns (the 'count') with a 40px space (the 'gutter') between them. Override the defaults by setting your own cols object values. For example:<br/><br/>cols:{count:6, gutter:15} or cols:{count:2, gutter:50}.</td>
		</tr>
		<tr>
			<td>onClick</td>
			<td>null</td>
			<td>Supply your own function to handle clicks on the dropdown menu. One argument is passed to the function: the clicked target as a jquery object. Event delegation is used internally to make this efficient. See the example in 3b under the Usage section above or check out Demo 6 in the <a href="demos/current/jquery-listmenu-plugin.aspx">demos</a>.</td>
		</tr>
	</tbody>
</table>

## CSS styling

The iHwy listmenu plugin has been designed with CSS-based styling in mind. The
easiest way for you to get started with styling your listmenu control is to
use the [listmenu.css](downloads/jquery-listmenu/1.0/listmenu.css) file as a
reference point or include it in your page and then adjust or override it as
needed.

**Here's a copy of the most relevant CSS classes:**
    
    
    .lm-wrapper { margin:0; padding:0; }
    .lm-wrapper .lm-letters { overflow:hidden; }
    * html .lm-wrapper .lm-letters { zoom:1; } /* for IE6 so that menu appears under letters */
    .lm-wrapper .lm-letters a { font-size:0.9em; display:block; float:left; padding:2px 11px; border:1px solid silver; border-right:none; text-decoration:none; }
    .lm-wrapper .lm-letters a:hover,
    .lm-wrapper .lm-letters a.lm-selected { background-color:#eaeaea; }
    .lm-wrapper .lm-letters a.lm-disabled { color:#ccc; }
    .lm-wrapper .lm-letters a.lm-last { border-right:1px solid silver; }
    .lm-wrapper .lm-letter-count { text-align:center; font-size:0.8em; line-height:1; margin-bottom:3px; color:#336699; }
    
    .lm-wrapper .lm-menu { border:1px solid silver; border-top:1px solid silver; padding:15px; z-index:10; position:absolute; margin-top:-1px; background:#ffc; display:none; }
    .lm-wrapper .lm-menu ul li { list-style-type:none; margin-bottom:5px; font-size:0.9em }
    .lm-wrapper .lm-menu ol li { margin-left:15px; }
    .lm-wrapper .lm-menu .lm-no-match { color:green; }
    .lm-wrapper .lm-menu a { text-decoration:none; }
    .lm-wrapper .lm-menu a:hover { text-decoration:underline; }
    .lm-wrapper .lm-menu .lm-submenu { overflow:hidden; }
    		

## Some tips for using the CSS classes:

**1.** Plan on styling the HTML that is created by the listmenu plugin, not your original list (except for people with javascript turned off). The original list is pulled out of the DOM so that the listmenu plugin can break it up by starting letter, create balanced columns and set it up to quickly hide and show submenu items.

**2.** The list that you apply listmenu to **must** have an id on it. For example: `<ul id="myList">`. The listmenu that gets created will have a `<div>` outer wrapper generated with an id that is the same as your original list, plus '-menu'. It will also be given class="lm-wrapper". Using the 'myList' example, this is what the outer wrapper of the listmenu will end up being:
    
    
      <div id="myList-menu" class="lm-wrapper">
        <!-- all of the generated listmenu HTML will be in here -->
      </div>
    

You can style the resulting listmenu using the generated id or style all
listmenu controls in your site using the 'lm-wrapper' class.

**3.** The letter navigation inside the listmenu has its own wrapper div with class="lm-letters", to make it easy to style. See the CSS above for how the 'lm-letters' class is used. Some notes:

***3.1.*** Each letter inside the letter navigation is an <a> tag styled with
float:left and display:block, so that they line up next to each other
horizontally. The last letter (Z) also gets the 'lm-last' class (typically
used to draw a right border on the letter).

***3.2.*** When a user mouses over a letter, the 'lm-selected' class gets added.
When they mouse off of the letter, that class gets removed.

***3.3.*** If the 'flagDisabled' option is set to true (the default), the 'lm-
disabled' class gets added to each letter that has no matching entries in the
original list. Use this class to "gray out" letters that will result in no
matches.

***3.4.*** If the 'showCounts' option is set to true (the default), you can use 'lm-
letter-count' class to style the 'count' that appears above each letter when
it's moused-over.

**4.** The dropdown menu that the listmenu plugin creates can be styled using the 'lm-menu' class. Note: the width of the menu is calculated by the listmenu control at runtime: if you want to adjust the width of the menu use the menuWidth option.

**5.** All items inside the dropdown menu can be styled using the 'lm-menu' class as the parent class. The CSS above shows some default styling we've included for LI items inside of UL and OL lists and styling for <a> tags to hide the underline that HTML adds by default, then show it when a link gets hovered over.

Note: the [demos](http://www.ihwy.com/Labs/demos/current/jquery-listmenu-plugin.aspx) inherit fonts and
basic styling from the core CSS of the ihwy.com site. We also use the [YUI CSS
reset](http://developer.yahoo.com/yui/reset/) file to help with cross-browser
styling. The CSS for the listmenu control is designed to play well with any
CSS that a site might already have and the 'lm-wrapper' has it's own 'reset'
built in via { margin:0; padding:0 }.

## Support

Please use the github [issue tracker](/iHwy/jQuery-ListMenu/issues) to
let us know about bugs and/or request new features.  Pull requests are
welcome!

## License

Dual licensed under the MIT and GPL licenses:

http://www.opensource.org/licenses/mit-license.php

http://www.gnu.org/licenses/gpl.html

## Revisions

**Version 1.1 -- 2009-08-09**  
- added includeOther option  
- added onClick option 

**Version 1.0 -- 2009-03-02**  
- initial Release 

