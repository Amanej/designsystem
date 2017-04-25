# ffe-dropdown-react

React implementation of the dropdown found in FFE.

## Install

```
$ npm install --save ffe-dropdown-react
```

`ffe-dropdown-react` depends on `ffe-core`, `ffe-form` and `ffe-spinner` being present and imported in your project.
More specifically, the CSS classes related to dropdowns in those packages should be in your CSS Object Model when using this component.

## Usage

```javascript
import Dropdown from 'ffe-dropdown-react';
```

```javascript
<Dropdown label={ labelTextString } onChange={ function }>
    { cards.map(c => <option value={ c.id }>{ c.name }</option>) }
</Dropdown>
```

The passed function will be called with the `SynthethicEvent` dispatched by `React`,
allowing access to the `value` property of the selected option through `e.target.value`, where `e` is the argument passed.

```javascript
<Dropdown label={ labelTextString } onChange={ function } onBlur={ anotherFunction }>
    { cards.map(c => <option value={ c.id }>{ c.name }</option>) }
</Dropdown>
```

The passed 'anotherFunction' will be called on blur event, ie when user tabs out of the select element. Same usage as the onChange property.


If you need to render a label tag outside of the component and pass an id for the select as a parameter you can pass an id attribute.
The label-attribute should then be omitted.

```javascript
<label for={ uniqueIdString }>{ labelTextString }</label>
<Dropdown id={ uniqueIdString } onChange={ function }>
    { cards.map(c => <option value={ c.id }>{ c.name }</option>) }
</Dropdown>
```

Alternatively, you can also use the `labelledBy` property in case you need to explicitly link the component to another label.
Similarly, you can also use the `describedBy` property to mark another element as a description of the dropdown.

If you want to initialize the dropdown with a non-empty value, you can supply a `defaultValue` prop.

To get an error message showing pass `errorMessage` to the `Dropdown`.
Passing `invalid` to the `Dropdown` will give a red color on the element.

```javascript
<Dropdown defaultValue="foo" invalid="true" errorMessage="test">
    <option value="make_foo" disabled="true">Not Bar</option>
    <option value="bar">Bar</option>
</Dropdown>
```

If you need to add styling to the outer div-container of the component and pass the attribute containerClassName.
The containerClassName will be appended to the default class 'ffe-input-group'.

```javascript
<label for={ uniqueIdString }>{ labelTextString }</label>
<Dropdown containerClassName={ myContainterClass }>
    <option value="val1">Option text</option>
</Dropdown>
```

### Loading state

Loading state can be indicated using `isLoading`. When this is set a loading spinner will be rendered next to the dropdown.

```javascript
<Dropdown isLoading={ true }>...</Dropdown>
```

##### Focus
In some situations where you remove a part of the DOM that contains the focused element (e.g after clicking a button), you might want to automatically set focus to a specific element.

The `autoFocus`-prop may be used for this purpose. It will automatically focus the element after mounting. Please note that this only works on one element!

