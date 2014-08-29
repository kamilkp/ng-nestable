angular-nestable 0.0.1
=================


###DESCRIPTION:
`angular-nestable` is a module for [AngularJS](https://angularjs.org) that uses the [jQuery nestable plugin](https://github.com/dbushell/Nestable) to create multi-sortable lists with the ability to nest items within each other.

###USAGE:

```html
<div ng-nestable ng-model="items">
	<div>
		<!-- this element is the template for each menu item -->
		<!-- the $item is availabla on scope and is the reference to the menu item object -->
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

Also the options object can be passed to the directive as the `ng-nestable` attribute. Those options will be passed to the jQuery `nestable` function when creating a nestable.
