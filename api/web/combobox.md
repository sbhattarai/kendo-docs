---
title: kendo.ui.ComboBox
meta_title: Configuration, methods and events of Kendo UI ComboBox
meta_description: Learn to configure Kendo UI ComboBox widget, use the documentation guide to operate different types of methods and get familiar with all events, used in ComboBox UI widget.
slug: api-web-combobox
relatedDocs: gs-web-combobox-overview
tags: api,web
publish: true
---

# kendo.ui.ComboBox

Represents the Kendo UI ComboBox widget. Inherits from [Widget](/api/framework/widget).

## Configuration

### animation `Object`

Configures the opening and closing animations of the suggestion popup. Setting the `animation` option to `false` will disable the opening and closing animations. As a result the suggestion popup will open and close instantly.

#### Example - disable open and close animations

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      animation: false
    });
    </script>

#### Example - configure the animation

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      animation: {
       close: {
         effects: "fadeOut zoom:out",
         duration: 300
       },
       open: {
         effects: "fadeIn zoom:in",
         duration: 300
       }
      }
    });
    </script>

### animation.close `Object`

#### Example - configure the close animation

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      animation: {
       close: {
         effects: "zoom:out",
         duration: 300
       }
      }
    });
    </script>

### animation.close.effects `String`

The effect(s) to use when playing the close animation. Multiple effects should be separated with a space.

[Complete list of available animations](/api/framework/fx#effects)

### animation.close.duration `Number` *(default: 100)*

The duration of the close animation in milliseconds.

### animation.open `Object`

The animation played when the suggestion popup is opened.

#### Example - configure the open animation

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      animation: {
       open: {
         effects: "zoom:in",
         duration: 300
       }
      }
    });
    </script>

### animation.open.effects `String`

The effect(s) to use when playing the open animation. Multiple effects should be separated with a space.

[Complete list of available animations](/api/framework/fx#effects)

### animation.open.duration `Number` *(default: 200)*

The duration of the open animation in milliseconds.

### autoBind `Boolean`*(default: true)*

Controls whether to bind the widget to the data source on initialization.

#### Example

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
        autoBind: false
    });
    </script>

### cascadeFrom `String`

Use it to set the Id of the parent ComboBox widget.
[Help topic showing how cascading functionality works](/web/combobox/cascading)

#### Example

    <input id="parent" />
    <input id="child" />
    <script>
    $("#parent").kendoComboBox({
        dataTextField: "parentName",
        dataValueField: "parentId",
        dataSource: [
            { parentName: "Parent1", parentId: 1 },
            { parentName: "Parent2", parentId: 2 }
        ]
    });

    $("#child").kendoComboBox({
        cascadeFrom: "parent",
        dataTextField: "childName",
        dataValueField: "childId",
        dataSource: [
            { childName: "Child1", childId: 1, parentId: 1 },
            { childName: "Child2", childId: 2, parentId: 2 },
            { childName: "Child3", childId: 3, parentId: 1 },
            { childName: "Child4", childId: 4, parentId: 2 }
        ]
    });
    </script>

### dataSource `Object|Array|kendo.data.DataSource`

The data source of the widget which is used to display a list of values. Can be a JavaScript object which represents a valid data source configuration, a JavaScript array or an existing [kendo.data.DataSource](/api/framework/datasource)
instance.

If the `dataSource` option is set to a JavaScript object or array the widget will initialize a new [kendo.data.DataSource](/api/framework/datasource) instance using that value as data source configuration.

If the `dataSource` option is an existing [kendo.data.DataSource](/api/framework/datasource) instance the widget will use that instance and will **not** initialize a new one.

#### Example - set dataSource as a JavaScript object

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: {
        data: ["One", "Two"]
      }
    });
    </script>

#### Example - set dataSource as a JavaScript array

    <input id="combobox" />
    <script>
    var data = ["One", "Two"];
    $("#combobox").kendoComboBox({
      dataSource: data
    });
    </script>

#### Example - set dataSource as an existing kendo.data.DataSource instance

    <input id="combobox" />
    <script>
    var dataSource = new kendo.data.DataSource({
      transport: {
        read: {
          url: "http://demos.kendoui.com/service/products",
          dataType: "jsonp"
        }
      }
    });
    $("#combobox").kendoComboBox({
      dataSource: dataSource,
      dataTextField: "ProductName",
      dataValueField: "ProductID"
    });
    </script>

### dataTextField `String`*(default: "")*

The field of the data item that provides the text content of the list items. The widget will filter the data source based on this field.

> **Important** When `dataTextField` is defined, the`dataValueField` option also should be set.

#### Example - set the dataTextField

    <input id="combobox" />
    <script>
    $("#comboBox").kendoComboBox({
        dataSource: [{
            { Name: "Parent1", Id: 1 },
            { Name: "Parent2", Id: 2 }
        }]
        dataTextField: "Name",
        dataValueField: "Id"
    });
    </script>

### dataValueField `String`*(default: "")*

The field of the data item that provides the value of the widget.

> **Important** When `dataValueField` is defined, the`dataTextField` option also should be set.

#### Example - set the dataValueField

    <input id="combobox" />
    <script>
    $("#comboBox").kendoComboBox({
        dataSource: [{
            { Name: "Parent1", Id: 1 },
            { Name: "Parent2", Id: 2 }
        }]
        dataTextField: "Name",
        dataValueField: "Id"
    });
    </script>

### delay `Number`*(default: 200)*

The delay in milliseconds between a keystroke and when the widget displays the popup.

#### Example - set the delay

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      delay: 500
    });
    </script>

### enable `Boolean`*(default: true)*

If set to `false` the widget will be disabled and will not allow user input. The widget is enabled by default and allows user input.

#### Example - disable the widget

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      enable: false
    });
    </script>

### filter `String`*(default: "none")*

The filtering method used to determine the suggestions for the current value. Filtration is turned of by default.
The supported filter values are `startswith`, `endswith` and `contains`.

#### Example - set the filter

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      filter: "contains"
    });
    </script>

### height `Number`*(default: 200)*

The height of the suggestion popup in pixels. The default value is 200 pixels.

#### Example - set the height

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      height: 500
    });
    </script>

### highlightFirst `Boolean`*(default: true)*

If set to `true` the first suggestion will be automatically highlighted.

#### Example - set highlightFirst

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      highlightFirst: false
    });
    </script>

### ignoreCase `String`*(default: true)*

If set to `false` case-sensitive search will be performed to find suggestions. The widget performs case-insensitive searching by default.

#### Example - disable case-insensitive suggestions

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      ignoreCase: false
    });
    </script>

### index `Number`*(default: -1)*

The index of the initially selected item. The index is `0` based.

#### Example - select second item

    <input id="combobox" />
    <script>
    var items = [{ text: "Item 1", value: "1" }, { text: "Item 2", value: "2" }];
    $("#combobox").kendoComboBox({
        dataTextField: "text",
        dataValueField: "value",
        dataSource: items,
        index: 1
    });
    </script>

### minLength `Number`*(default: 1)*

The minimum number of characters the user must type before a search is performed. Set to higher value than `1` if the search could match a lot of items.

#### Example - set minLength

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      minLength: 3
    });
    </script>

### placeholder `String`*(default: "")*

The hint displayed by the widget when it is empty. Not set by default.

#### Example - specify placeholder option

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      placeholder: "Select..."
    });
    </script>

#### Example - specify placeholder as HTML attribute

    <input id="combobox" placeholder="Select..." />

    <script>
    $("#combobox").kendoComboBox({
        dataSource: ["Item1", "Item2"]
    });
    </script>

### suggest `Boolean`*(default: false)*

If set to `true` the widget will automatically use the first suggestion as its value.

#### Example - enable automatic suggestion

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      suggest: true
    });
    </script>

### template `String|Function`

The [template](/api/framework/kendo#methods-template) used to render the items. By default the widget displays only the text of the data item (configured via `dataTextField`).

#### Example - specify template as a function

    <input id="combobox" />
    <script id="template" type="text/x-kendo-template">
      <span>
        <img src="/img/#: id #.png" alt="#: name #" />
        #: name #
      </span>
    </script>
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [
        { id: 1, name: "Apples" },
        { id: 2, name: "Oranges" }
      ],
      dataTextField: "name",
      dataValueField: "id",
      template: kendo.template($("#template").html())
    });
    </script>

#### Example - specify template as a string

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [
        { id: 1, name: "Apples" },
        { id: 2, name: "Oranges" }
      ],
      dataTextField: "name",
      dataValueField: "id",
      template: '<span><img src="/img/#: id #.png" alt="#: name #" />#: name #</span>'
    });
    </script>

### text `String`*(default: "")*

The text of the widget used when the `autoBind` is set to `false`.

#### Example - specify text of the widget

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
         autoBind: false,
         text: "Chai"
    });
    </script>

### value `String`*(default: "")*

The value of the widget.

#### Example - specify value of the widget

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
         dataSource: ["Item1", "Item2"],
         value: "Item1"
    });
    </script>

### valuePrimitive `Boolean`*(default: false)*

Specifies the [value binding](/getting-started/framework/mvvm/bindings/value) behavior for the widget when the initial model value is null. If set to true, the View-Model field will be updated with the selected item value field. If set to false, the View-Model field will be updated with the selected item.

#### Example - specify that the View-Model field should be updated with the selected item value

    <input id="combobox" data-bind="value: selectedProductId, source: products" />

    <script>
    $("#combobox").kendoComboBox({
      valuePrimitive: true,
      dataTextField: "name",
      dataValueField: "id"
    });
    var viewModel = kendo.observable({
      selectedProductId: null,
      products: [
        { id: 1, name: "Coffee" },
        { id: 2, name: "Tea" },
        { id: 3, name: "Juice" }
      ]
    });

    kendo.bind($("#combobox"), viewModel);
    </script>

## Fields

### dataSource `kendo.data.DataSource`

The [data source](/api/framework/datasource) of the widget. Configured via the [dataSource](#configuration-dataSource) option.

> Changes of the data source will be reflected in the widget.

> **Important:** Assigning a new data source would have no effect. Use the [setDataSource](#methods-setDataSource) method instead.

#### Example - add a data item to the data source
    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [
        { name: "Apples" },
        { name: "Oranges" }
      ],
      dataTextField: "name",
      dataValueField: "name"
    });
    var combobox = $("#combobox").data("kendoComboBox");
    combobox.dataSource.add({ name: "Appricot" });
    combobox.search("A");
    </script>

### input `jQuery`
A jQuery object of the visible input element, where the user types.

#### Example - get input element

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox();

    var combobox = $("#combobox").data("kendoComboBox");

    var input = combobox.input;
    <script>

### options `Object`
An object, which holds the options of the widget.

#### Example - get options of the widget

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox();

    var combobox = $("#combobox").data("kendoComboBox");

    var options = combobox.options;
    <script>

### list `jQuery`
A jQuery object of the drop-down list element.

#### Example - get list element

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox();

    var combobox = $("#combobox").data("kendoComboBox");

    var list = combobox.list;
    <script>

### ul `jQuery`
A jQuery object of the ul element, which holds the available options.

#### Example - get ul element

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox();

    var combobox = $("#combobox").data("kendoComboBox");

    var ul = combobox.ul;
    <script>

### popup `kendo.ui.Popup`

The Popup instance used by the widget.

#### Example - get widget popup

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox();

    var combobox = $("#combobox").data("kendoComboBox");

    var popup = combobox.popup;

    console.log(popup.visible());
    <script>

## Methods

### close

Closes the widget popup.

#### Example - close the suggestion popup

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [ "Apples", "Oranges" ]
    });
    var combobox = $("#combobox").data("kendoComboBox");
    // Search for items starting with "A" - will open the suggestion popup and show "Apples"
    combobox.search("A");
    // Close the suggestion popup
    combobox.close();
    </script>

### dataItem

Returns the data item at the specified index. If the index is not specified, the selected index will be used.

#### Parameters

##### index `Number` *(optional)*

The zero-based index of the data record.

#### Returns

`Object` The raw data record. Returns <i>undefined</i> if no data.

#### Example

    <input id="combobox" />
    <script>

    $("#combobox").kendoComboBox({
      dataSource: [
        { id: 1, name: "Apples" },
        { id: 2, name: "Oranges" }
      ],
      dataTextField: "name",
      dataValueField: "id",
      index: 1
    });

    var combobox = $("#combobox").data("kendoComboBox");

    // get the dataItem corresponding to the selectedIndex.
    var dataItem = combobox.dataItem();

    // get the dataItem corresponding to the passed index.
    var dataItem = combobox.dataItem(0);
    </script>

### destroy

Prepares the **ComboBox** for safe removal from DOM. Detaches all event handlers and removes jQuery.data attributes to avoid memory leaks. Calls destroy method of any child Kendo widgets.

> **Important:** This method does not remove the ComboBox element from DOM.

#### Example

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox();
    var combobox = $("#combobox").data("kendoComboBox");
    combobox.destroy();
    </script>

### enable

Enables or disables the widget.

#### Parameters

##### enable `Boolean`

If set to `true` the widget will be enabled. If set to `false` the widget will be disabled.

#### Example - enable the widget

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      enable: false
    });
    var combobox = $("#combobox").data("kendoComboBox");
    combobox.enable(true);
    </script>

### readonly

Toggles the readonly state of the widget. When the widget is readonly it doesn't allow user input.

> There is a difference between disabled and readonly mode. The value of a disabled widget is **not** posted as part of a `form` whereas the value of a readonly widget is posted.

#### Parameters

##### readonly `Boolean`

If set to `true` the widget will not allow user input. If set to `false` the widget will allow user input.

#### Example - make the widget readonly

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox();
    var combobox = $("#combobox").data("kendoComboBox");
    combobox.readonly(true);
    </script>

### focus

Focuses the widget.

#### Example - focus the widget

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox();
    var combobox = $("#combobox").data("kendoComboBox");
    combobox.focus();
    </script>

### open

Opens the popup.

#### Example

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [
        { id: 1, name: "Apples" },
        { id: 2, name: "Oranges" }
      ],
      dataTextField: "name",
      dataValueField: "id",
      index: 1
    });

    var combobox = $("#combobox").data("kendoComboBox");
    combobox.focus();
    </script>

### refresh

Refresh the popup by rendering all items again.

#### Example - refresh the popup items

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [
        { id: 1, name: "Apples" },
        { id: 2, name: "Oranges" }
      ],
      dataTextField: "name",
      dataValueField: "id",
      index: 1
    });

    var combobox = $("#combobox").data("kendoComboBox");

    combobox.refresh();
    </script>

### search

Searches the data source for the provided value and displays any matches as suggestions.

#### Parameters

##### word `String`

The filter value.

#### Example - search the widget

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [
        { id: 1, name: "Apples" },
        { id: 2, name: "Oranges" }
      ],
      dataTextField: "name",
      dataValueField: "id",
      index: 1
    });

    var combobox = $("#combobox").data("kendoComboBox");

    combobox.search("App");
    </script>

### select

Selects the item provided as an argument and updates the value and text of the widget.

#### Parameters

##### li `jQuery | Number | Function`

A string, DOM element or jQuery object which represents the item to be selected. A string is treated as a jQuery selector.
A number representing the index of the item or function predicate which returns the correct data item.

#### Returns

`Number` The index of the selected item, if called with no parameters. If a custom value is entered, the returned selected index is `-1`.

`undefined` If called with a parameter as a setter.

#### Example - select item based on jQuery object

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [
        { id: 1, name: "Apples" },
        { id: 2, name: "Oranges" }
      ],
      dataTextField: "name",
      dataValueField: "id"
    });

    var combobox = $("#combobox").data("kendoComboBox");

    combobox.select(combobox.ul.children().eq(0));
    </script>

#### Example - select item based on index

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [
        { id: 1, name: "Apples" },
        { id: 2, name: "Oranges" }
      ],
      dataTextField: "name",
      dataValueField: "id"
    });

    var combobox = $("#combobox").data("kendoComboBox");

    combobox.select(1);
    </script>

#### Example - select item based on function predicate

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [
        { id: 1, name: "Apples" },
        { id: 2, name: "Oranges" }
      ],
      dataTextField: "name",
      dataValueField: "id"
    });

    var combobox = $("#combobox").data("kendoComboBox");

    combobox.select(function(dataItem) {
        return dataItem.text === "Apples";
    });
    </script>

#### Example - get selected index of the widget

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [
        { id: 1, name: "Apples" },
        { id: 2, name: "Oranges" }
      ],
      dataTextField: "name",
      dataValueField: "id",
      index: 1
    });

    var combobox = $("#combobox").data("kendoComboBox");

    var selectedIndex = combobox.select();
    </script>

### setDataSource

Sets the dataSource of an existing ComboBox and rebinds it.

#### Parameters

##### dataSource `kendo.data.DataSource`

#### Example

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [ "Apples", "Oranges" ]
    });
    var dataSource = new kendo.data.DataSource({
      data: [ "Bananas", "Cherries" ]
    });
    var combobox = $("#combobox").data("kendoComboBox");
    combobox.setDataSource(dataSource);
    </script>

### suggest

Sets the value of the widget to the specified argument and visually selects the text.

#### Parameters

##### value `String`

Characters to force a suggestion.

#### Example

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [ "Apples", "Oranges" ]
    });
    var combobox = $("#combobox").data("kendoComboBox");
    combobox.suggest("Apples");
    </script>

### text

Gets or sets the text of the ComboBox. Widget will select the item with same text. If
there are no matches then the text will be considered as a custom value of the widget.

#### Parameters

##### text `String`

The text to set.

#### Returns

`String` The text of the combobox.

#### Example - set text of the widget

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [ "Apples", "Oranges" ]
    });

    var combobox = $("#combobox").data("kendoComboBox");

    combobox.text("Apples");
    </script>

### toggle

Opens or closes the widget popup.

#### Parameters

##### toggle `Boolean`

Defines the whether to open/close the drop-down list.

#### Example - set text of the widget

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [ "Apples", "Oranges" ]
    });

    var combobox = $("#combobox").data("kendoComboBox");

    combobox.toggle();
    </script>

### value

Gets or sets the value of the combobox.

> **Important:** If the widget is not bound, value method will pre-fetch the data before continue with the value setting.

#### Parameters

##### value `String`

The value to set.

#### Returns

`String` The value of the combobox.

#### Example - set value of the widget

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataSource: [ "Apples", "Oranges" ]
    });

    var combobox = $("#combobox").data("kendoComboBox");

    combobox.value("Oranges");
    </script>

## Events

### change

Fired when the value of the widget is changed by the user.

The event handler function context (available via the `this` keyword) will be set to the widget instance.

> **Important:** The event is not fired when the value of the widget is changed from code.

#### Event Data

##### e.sender `kendo.ui.ComboBox`

The widget instance which fired the event.

#### Example - subscribe to the "change" event during initialization

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      change: function(e) {
        var value = this.value();
        // Use the value of the widget
      }
    });
    </script>

#### Example - subscribe to the "change" event after initialization

    <input id="combobox" />
    <script>
    function combobox_change(e) {
      var value = this.value();
      // Use the value of the widget
    }
    $("#combobox").kendoComboBox();
    var combobox = $("#combobox").data("kendoComboBox");
    combobox.bind("change", combobox_change);
    </script>

### close

Fired when the popup of the widget is closed.

The event handler function context (available via the `this` keyword) will be set to the widget instance.

#### Event Data

##### e.sender `kendo.ui.ComboBox`

The widget instance which fired the event.

#### Example - subscribe to the "close" event during initialization

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      close: function(e) {
        // handle the event
      }
    });
    </script>

#### Example - subscribe to the "close" event after initialization

    <input id="combobox" />
    <script>
    function combobox_close(e) {
      // handle the event
    }
    $("#combobox").kendoComboBox();
    var combobox = $("#combobox").data("kendoComboBox");
    combobox.bind("close", combobox_close);
    </script>

### dataBound

Fired when the widget is bound to data from its data source.

The event handler function context (available via the `this` keyword) will be set to the widget instance.

#### Event Data

##### e.sender `kendo.ui.ComboBox`

The widget instance which fired the event.

#### Example - subscribe to the "dataBound" event during initialization

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      dataBound: function(e) {
          // handle the event
      }
    });
    </script>

#### Example - subscribe to the "dataBound" event after initialization

    <input id="combobox" />
    <script>
    function combobox_dataBound(e) {
      // handle the event
    }
    $("#combobox").kendoComboBox();
    var combobox = $("#combobox").data("kendoComboBox");
    combobox.bind("dataBound", combobox_dataBound);
    </script>

### open

Fired when the popup of the widget is opened by the user.

The event handler function context (available via the `this` keyword) will be set to the widget instance.

#### Event Data

##### e.sender `kendo.ui.ComboBox`

The widget instance which fired the event.

#### Example - subscribe to the "open" event during initialization

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      open: function(e) {
        // handle the event
      }
    });
    </script>

#### Example - subscribe to the "open" event after initialization

    <input id="combobox" />
    <script>
    function combobox_open(e) {
      // handle the event
    }
    $("#combobox").kendoComboBox();
    var combobox = $("#combobox").data("kendoComboBox");
    combobox.bind("open", combobox_open);
    </script>

### select

Fired when an item from the popup is selected by the user.

#### Event Data

##### e.item `jQuery`

The jQuery object which represents the selected item.

##### e.sender `kendo.ui.ComboBox`

The widget instance which fired the event.

#### Example - subscribe to the "select" event during initialization

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      select: function(e) {
        var item = e.item;
        var text = item.text();
        // Use the selected item or its text
      }
    });
    </script>

#### Example - subscribe to the "select" event after initialization

    <input id="combobox" />
    <script>
    function combobox_select(e) {
      var item = e.item;
      var text = item.text();
      // Use the selected item or its text
    }
    $("#combobox").kendoComboBox();
    var combobox = $("#combobox").data("kendoComboBox");
    combobox.bind("select", combobox_select);
    </script>

### cascade

Fired when the value of the widget is changed via API or user interaction.

#### Event Data

##### e.sender `kendo.ui.ComboBox`

The widget instance which fired the event.

#### Example - subscribe to the "cascade" event during initialization

    <input id="combobox" />
    <script>
    $("#combobox").kendoComboBox({
      cascade: function() {
        // Handle the event
      }
    });
    </script>

#### Example - subscribe to the "cascade" event after initialization

    <input id="combobox" />
    <script>
    function combobox_cascade(e) {
        // Handle the event
    }
    $("#combobox").kendoComboBox();
    var combobox = $("#combobox").data("kendoComboBox");
    combobox.bind("select", combobox_cascade);
    </script>
