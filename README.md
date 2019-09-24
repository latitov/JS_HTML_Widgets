# JS_HTML_Widgets
Easily create widget objects of arbitrary complexity

By Leonid Titov, 2019-09-23

Please download, and open the Widget_v3.md.html in a browser, and read.

What you'll get:

- very interesting article about this;
- snippets of code and examples;
- ready to use... framework in vanilla JS, to create widgets of your own;

Here's an example of what it look like.

#### A widget code

```
// inside a js file of a widget class
(function () {
	var Module_Path = ["WidgetsLib", "a1", "Button"];
	var curr = this;
	Module_Path.forEach(function(i){if (curr[i] == null) {addChildToTree(curr, i, {})} curr = curr[i]});

	specialize_with(curr, {
		CSS_Literal: `
			.{{WIDGET_CLASS_ID}}_Something {
				color: hsl(0, 0%, 20%);
			}
		`,
		HTML_Literal: `
			<div onclick="{{WIDGET_INSTANCE}}.onclick(event)"
				class="{{WIDGET_CLASS_ID}}_Something"
			>
			SOME SUPER COOL WIDGET
			</div>
		`,
		new: typical_widget_new,
		WidgetSpecializer: {
			remove: typical_widget_remove,
		}
	});
})();
```

#### An HTML:

```
<div id="w1" style="background-color: hsl(200, 50%, 50%);"></div>

<script src="WidgetsLib/a1/Button/js"></script>
```

#### A user JavaScript code:

```
var b1 = WidgetsLib.a1.Button.new("w1", {
	onclick: function(ev) {
		ev.target.style.color = "#ffff00";
		console.log("====== HERE");
	}
});
```

#### Download and enjoy reading and using it. Then try demo_test.html, and see inside it.
