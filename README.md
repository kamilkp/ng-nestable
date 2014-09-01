angular-nestable 0.0.1 [![Bower version](https://badge.fury.io/bo/ng-nestable.svg)](http://badge.fury.io/bo/ng-nestable)
=================

###DEMO:
check out the demo [here](http://kamilkp.github.io/ng-nestable)

###DESCRIPTION:
`angular-nestable` is a module for [AngularJS](https://angularjs.org) that uses the [jQuery nestable plugin](https://github.com/dbushell/Nestable) to create multi-sortable lists with the ability to nest items within each other.

###INSTALLATION

Either run `bower install ng-nestable` or download `angular-nestable.js` form the repository directly.

Include the module in your app dependency:

```javascript
angular.module('yourAppModule', ['ng-nestable']);
```

Note that this module requires jQuery and jQuery nestable plugin.

###USAGE:

```html
<div ng-nestable ng-model="items">
	<div>
		<!-- this element is the template for each menu item -->
		<!-- the $item is available on scope and is the reference to the menu item object -->
		{{$item}}
	</div>
</div>
```

Example `items` object structure:

```javascript
[
	{
		item: {}, // this object will be referenced as the $item on scope
		children: []
	},
	{
		item: {},
		children: [
			{
				item: {},
				children: []
			}
		]
	},
	{
		item: {},
		children: []
	}
]
```

Each nestable element in the DOM gets it's own non-isolated scope just like with `ng-repeat`.

Also the options object can be passed to the directive as the `ng-nestable` attribute. Those options will be passed to the jQuery `nestable` function when creating a nestable.

===

The module also exposes a `$nestableProvider` that can be injected into a `config` block. It provides two methods:

 * `$nestableProvider.modelName(str)` - can be used to set the model name variable inside each nestable element. The default value of model name is `$item`.
 * `$nestableProvider.defaultOptions(obj)` - can be used to set some default options for the nestable jquery plugin. Those options include the following: (extract from the [jQuery nestable](https://github.com/dbushell/Nestable) readme)

		maxDepth        : number of levels an item can be nested (default 5)
		group           : group ID to allow dragging between lists (default 0)

		listNodeName    : The HTML element to create for lists (default 'ol')
		itemNodeName    : The HTML element to create for list items (default 'li')
		rootClass       : The class of the root element .nestable() was used on (default 'dd')
		listClass       : The class of all list elements (default 'dd-list')
		itemClass       : The class of all list item elements (default 'dd-item')
		dragClass       : The class applied to the list element that is being dragged (default 'dd-dragel')
		handleClass     : The class of the content element inside each list item (default 'dd-handle')
		collapsedClass  : The class applied to lists that have been collapsed (default 'dd-collapsed')
		placeClass      : The class of the placeholder element (default 'dd-placeholder')
		emptyClass      : The class used for empty list placeholder elements (default 'dd-empty')
		expandBtnHTML   : The HTML text used to generate a list item expand button (default '<button data-action="expand">Expand></button>')
		collapseBtnHTML : The HTML text used to generate a list item collapse button (default '<button data-action="collapse">Collapse</button>')
		
===

Also note that the `ng-sortable` directive uses [ngModelController](https://docs.angularjs.org/api/ng/type/ngModel.NgModelController) to read and write to the provided model object and is fully compliant with `$formatters` and `$parsers`.
