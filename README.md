tablesorter is a jQuery plugin for turning a standard HTML table with THEAD and TBODY tags into a sortable table without page refreshes.
tablesorter can successfully parse and sort many types of data including linked data in a cell.

### [Documentation](http://mottie.github.io/tablesorter/docs/)

* See the [full documentation](http://mottie.github.io/tablesorter/docs/).
* All of the [original document pages](http://tablesorter.com/docs/) have been included.
* Information from my blog post on [undocumented options](http://wowmotty.blogspot.com/2011/06/jquery-tablesorter-missing-docs.html) and lots of new demos have also been included.
* Change log moved from included text file into the [wiki documentation](https://github.com/Mottie/tablesorter/wiki/Change).

### Demos

* [Basic alpha-numeric sort Demo](http://mottie.github.com/tablesorter/).
* Links to demo pages can be found within the main [documentation](http://mottie.github.io/tablesorter/docs/).
* More demos & playgrounds - updated in the [wiki pages](https://github.com/Mottie/tablesorter/wiki).

### Features

* Multi-column alphanumeric sorting.
* Multi-tbody sorting - see the [options](http://mottie.github.io/tablesorter/docs/index.html#options) table on the main document page.
* Parsers for sorting text, alphanumeric text, URIs, integers, currency, floats, IP addresses, dates (ISO, long and short formats) &amp; time. [Add your own easily](http://mottie.github.io/tablesorter/docs/example-parsers.html).
* Support for ROWSPAN and COLSPAN on TH elements.
* Support secondary "hidden" sorting (e.g., maintain alphabetical sort when sorting on other criteria).
* Extensibility via [widget system](http://mottie.github.io/tablesorter/docs/example-widgets.html).
* Cross-browser: IE 6.0+, FF 2+, Safari 2.0+, Opera 9.0+.
* Small code size.
* Works with jQuery 1.2.6+ (jQuery 1.4.1+ needed with some widgets).
* Works with jQuery 1.9+ ($.browser.msie was removed; needed in the original version).

### Licensing

* Copyright (c) 2007 Christian Bach.
* Original examples and docs at: [http://tablesorter.com](http://tablesorter.com).
* Dual licensed under the [MIT](http://www.opensource.org/licenses/mit-license.php) and [GPL](http://www.gnu.org/licenses/gpl.html) licenses.

### Special Thanks

* Big shout-out to [Nick Craver](https://github.com/NickCraver) for getting rid of the `eval()` function that was previously needed for multi-column sorting.
* Also big thanks to [thezoggy](https://github.com/thezoggy) for helping with code, themes and providing valuable feedback.
* And, thanks to everyone else that has contributed, and continues to contribute to this forked project!

### Change Log

View the [complete listing here](https://github.com/Mottie/tablesorter/wiki/Change).

#### <a name="v2.11">Version 2.11</a> (10/10/2013)

**Core**
* Initialized widgets (widgets with options) are now tracked to ensure widget options are extended when using "applyWidgets". Fixes [issue #330](https://github.com/Mottie/tablesorter/issues/330).
* An javascript error no longer pops up when setting the `delayInit` option to `true` and using the `saveSort` widget (or triggering a `sorton` method). Fixes [issue #346](https://github.com/Mottie/tablesorter/issues/346).
* Only visible columns will be considered when fixing column widths. Fixes [issue #371](https://github.com/Mottie/tablesorter/issues/371).
* Merged in fix for jQuery version check ([pull #338](https://github.com/Mottie/tablesorter/pull/338)). This also fixes [issue #379](https://github.com/Mottie/tablesorter/issues/379). Thanks @lemoinem!
* Removed natural sort's ability to sort dates. This shouldn't be a problem since tablesorter uses parsers detect &amp; parse date columns automatically. Fixes [issue #373](https://github.com/Mottie/tablesorter/issues/373).
* Fixed [issue #381](https://github.com/Mottie/tablesorter/issues/381).
  * Any class name that is set by an option and is later used to search for that element now has an empty default class name.
  * The reasoning is that if a developer adds two class names to the option, the jQuery find breaks.
  * All default single class name options are now contained within `$.tablesorter.css`
  * Options affected include: tableClass, cssAsc, cssDesc, cssHeader, cssIcon, cssHeaderRow, cssProcessing in the core.
  * Note that the `cssIcon` option retains it's default class name &amp; functionality to not add an `<i>` inside the table cell if this *extra class name* is undefined.
  * Widget options affected include: filter_cssFilter and stickyHeaders.
* Removed `return false` from header mouse/keyboard interaction. Fixes [issue #305](https://github.com/Mottie/tablesorter/pull/305) &amp; [issue #366](https://github.com/Mottie/tablesorter/issues/366).

**Parsers**
* Fixed sugar date parser demo to point to the correct parser file and sugarjs resource.
* General cleaned up date, fraction and metric parsers &amp; fixing of minor bugs.

**Build Table Widget (new)**
* Build a table starting with an assortment of data types ( array, text (CSV, HTML) or object (json) ).
* This widget isn't really a widget because it is run and does it's processing before tablesorter has initialized; but the options for it are contained within the tablesorter `widgetOptions`.

**Column Widget**
* General cleanup

**Filter Widget**
* Exact matches can still be made if the user enters an exact match indicator twice (i.e. `John==` will still find `John` in the column; before it would think the user was looking for `John=` after the second `=` was typed)
* Dynamically added filter reset buttons will now work automatically. Added by [pull #327](https://github.com/Mottie/tablesorter/pull/327). Thanks @riker09!
* Chrome appears to have fixed the hidden input bug, so reverted changes to the basic filter demo. Fixes [issue #341](https://github.com/Mottie/tablesorter/issues/341).
* The filter widget will work properly with sub-tables. Fixes [issue #354](https://github.com/Mottie/tablesorter/issues/354). Thanks @johngrogg!
* Fixed issues with `filter_columnFilters` set to `false`. Fixes [issue #355](https://github.com/Mottie/tablesorter/issues/355).
* Searches now have accents replaced if the `sortLocaleCompare` option is `true`. Fixes [issue #357](https://github.com/Mottie/tablesorter/issues/357).
* Merged in enhancement for the filter widget & updated docs - add row to `filter_functions` parameters ([issue #367](https://github.com/Mottie/tablesorter/issues/367), [pull #368](https://github.com/Mottie/tablesorter/pull/368)). Thanks @gknights!
* FilterFormatter jQuery UI Datepicker now includes the user selected time for comparisons. Thanks @TheSin-!
* Another fix to the filteFormatter jQuery UI Datepicker to make it work properly with the sticky header widget. Thanks @TheSin-!
* Removed filter_cssFilter default class name. The "tablesorter-filter" class name is automatically added, and this option now contains any additional class names to add. Fixes [issue #381](https://github.com/Mottie/tablesorter/issues/381).

**Grouping Widget**
* The grouping widget now works across multiple tbodies.
* Added `group-false` header option which disables the grouping widget for a specific column. Fixes [issue #344](https://github.com/Mottie/tablesorter/issues/344).
* Added the `group_collapsed` option which when true and the `group_collapsible` option is also true, all groups will start collapsed. Fulfills [issue #352](https://github.com/Mottie/tablesorter/issues/352).
* You can now toggle *all* group rows by holding down the shift key while clicking on a group header.
* This widget now works properly with the pager addon (pager addon updated). Fixes [issue #281](https://github.com/Mottie/tablesorter/issues/281).

**StickyHeaders Widget**
* Caption outerheight now used to get the correct full height of the caption. Thanks @TheSin-!
* `stickyHeaders_zIndex` option added to allow users to customize their sticky header z-index. Fixes [issue #332](https://github.com/Mottie/tablesorter/pull/332). Thanks @TheSin-!

**UITheme widget**
* Updated Bootstrap theme to work with Bootstrap v3
  * Only additions were made to the sorting icons class names within in the `$.tablesorter.themes.bootstrap` defaults (contained in the `jquery.tablesorter.widgets.js` file).
  * So the theme will support all current versions of Bootstrap, just make sure you are using the appropriate icon class name (`icon-{name}` = v2; `glyphicon glyphicon-{name}` = v3).
  * Removed the gradient background from the header &amp; footer cells.
  * Added a reduced icon font side for header sort icons.
  * Renamed the pager class from `pager` to `ts-pager` as Bootstrap adds a lot of padding to that class. See [Bootstrap theme demo](http://mottie.github.io/tablesorter/docs/example-widget-bootstrap-theme.html).
  * Thanks @YeaYeah for sharing how to fix the top border in [issue #365](https://github.com/Mottie/tablesorter/issues/365).

**Pager**
* Fixed the `removeRows` option error when set to `true`.
* The pager now stores any object returned by the `ajaxProcessing` function in `table.config.pager.ajaxData`
  * The object should contain attributes for `total` (numeric), `headers` (array) and `rows` (array of arrays).
  * A replacement `output` option can also be loaded via this method and must be included in the `output` attribute (i.e. `ajaxData.output`).
  * Additional attributes are also available to the output display by using the attribute key wrapped in curly brackets (e.g. `{extra}` from `ajaxData.extra`).
  * Additional attributes can also be objects or arrays and can be accessed via the output string as `{extra:0}` (for arrays) or `{extra:key}` for objects.
  * The page number is processed first, so it would be possible to use this string `{extra:{page}}` (`{page}` is a one-based index), or if you need a different value use `{page+1}` (zero-based index plus any number), or `{page-1}` (zero-based index minus any number).
  * For more details, please see [issue #326](https://github.com/Mottie/tablesorter/issues/326).
  * Thanks @camallen for the suggestions &amp; feedback!
* The "updateComplete" event should now properly trigger after an ansynchronous ajax call has completed. Fixes [issue #343](https://github.com/Mottie/tablesorter/issues/343).
* Added a new `savePages` option
  * Requires requires the `$.tablesorter.storage` script within the `jquery.tablesorter.widget.js` file to work properly.
  * When `true`, it saves pager page & size if the storage script is loaded (requires $.tablesorter.storage in jquery.tablesorter.widgets.js).
  * The pager will continue to function properly without the storage script, it just won't save the current page or pager size.
  * Fulfills enhancement request from [issue #345](https://github.com/Mottie/tablesorter/issues/345).
* Removed table update when using ajax with a server that is already doing all of the work. Fixes [issue #372](https://github.com/Mottie/tablesorter/issues/372) &amp; [issue #361](https://github.com/Mottie/tablesorter/issues/361). Thanks @sbine!
* Merged in change to count table th length after ajaxProcessing ([pull #383](https://github.com/Mottie/tablesorter/pull/383)). Thanks @harryxu!
* Reverted changes made in [pull #349](https://github.com/Mottie/tablesorter/pull/349) as the error row was not showing because the urls did not exactly equal each other.
* Child rows within the pager will now properly display/hide. Fixes [issue #348](https://github.com/Mottie/tablesorter/issues/348).
* Merged in fix for pager redundant ajax requests ([pull #336](https://github.com/Mottie/tablesorter/pull/336)). Thanks @camallen!
* Merged in fix for pager totalRows check ([pull #324](https://github.com/Mottie/tablesorter/pull/324)). Thanks @camallen!

**Internal fixes**
* Modified the pager plugin internal variables to use `p` for pager options and `c` for table config options - for consistency.
* Cleaned up the formatting of a few parsers (mostly cosmetic!)
* Some parser functions were added to the `$.tablesorter` object instead of keeping them as private functions, just because my OCD compelled me to do it.
* Some of the changes made the parsers are no longer backward compatible to the original version of tablesorter. Break away man, just do it!

**Thanks**
* Thanks to @thezoggy and @TheSin- for help maintaining and supporting the tablesorter github project while I was away!
* Also thanks to everyone else that contributed and even more thanks to those that helped troubleshoot and solve problems!

#### <a name="v2.10.8">Version 2.10.8</a> (6/3/2013)

* Updated the percent parser to only detect if the content is shorter than 15 characters. This prevents columns with a lot of content and one percent sign (%) from being set to be parsed as a percent numeric column. Fixes [issue #320](https://github.com/Mottie/tablesorter/issues/320).
* Updated filter widget &amp; filter_formatter:
  * Added a new `filter_defaultAttrib` which points to the default `'data-value'` attribute in the table header which will contain the filter's default (starting) value and *will override* any set values within the filter_formatter functions. Updated the [custom filter widget function demo age column](http://mottie.github.io/tablesorter/docs/example-widget-filter-custom.html) to show this in action.
  * The `$.tablesorter.setFilter()` method now properly updates the filter formatter elements when set.
  * The `uiDateCompare` and `uiDatepicker` functions now adds a time of 11:59:59 to the "to" date or when a "less than" comparison is made so as to include all times within that selected day.
  * The `defaultDate` option (not `date` option, sorry) of the `uiDateCompare` now properly sets the value upon initialization.
  * The `from` and `to` options of the `uiDatepicker` now properly sets those values properly upon initialization.
  * Fixes [issue #321](https://github.com/Mottie/tablesorter/issues/321).
* Fixed stickyHeaders widget:
  * When removing a sticky headers widget, it no longer unbinds scrolling when other sticky headers are still active.
  * Added `stickyHeaders_includeCaption` option (set as `true` by default). When this option is `false` and a caption exists, it will not be included in teh sticky header. Fixes [issue #322](https://github.com/Mottie/tablesorter/issues/322).

#### <a name="v2.10.7">Version 2.10.7</a> (5/31/2013)

* Now using correct `closest()` function equivalent. Thanks to [isuTony](https://github.com/isuTony); Fixes [issue #319](https://github.com/Mottie/tablesorter/issues/319).
* Anticipating my sabbitical, I've added a few "beta-testing" scripts into a new folder for feedback, code fixes and help:
    * [Custom pager control script](http://mottie.github.io/tablesorter/beta-testing/example-pager-custom-controls.html) - should be working properly.
    * [External filters using Select2 plugin](http://mottie.github.io/tablesorter/beta-testing/example-external-filters-using-select2.html) - should be working properly.
    * [Column reorder widget](http://mottie.github.io/tablesorter/beta-testing/example-widget-column-reorder.html) - not working 100% with sticky headers.
    * [Column sum widget](http://mottie.github.io/tablesorter/beta-testing/example-widget-sum-columns.html) - still needs LOTS of work!

#### <a name="v2.10.6">Version 2.10.6</a> (5/30/2013)

* Added `skipTest` options to the HTML5 filter formatter functions. Fixes [issue #307](https://github.com/Mottie/tablesorter/issues/307).

#### <a name="v2.10.5">Version 2.10.5</a> (5/30/2013)

* Filter formatter functions now works properly within sticky headers. Fixes issues [#290](https://github.com/Mottie/tablesorter/issues/290) &amp; [#317](https://github.com/Mottie/tablesorter/issues/317).
