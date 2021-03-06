PL Modal
========
Modal created with Javascript and CSS Transitions. Customizable by user and easy to implement.

### Usage
```javascript
let settings = {
	avoidClose: false,
	closeWithOverlay: true,
	effectName: 'pl-effect-4'
};

let modal = new pl.Modal(settings);
let element = document.getElementById('element');

modal.open(element);
```

Use `settings` to personalize the modal instance.

<table>
    <tr>
        <th>Value</th>
        <th>Type</th>
        <th>Default Value</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>avoidClose</td>
        <td><code>boolean</code></td>
        <td><code>false</code></td>
        <td>If avoidClose is true the modal can't be closed.</td>
    </tr>
    <tr>
        <td>closeWithOverlay</td>
        <td><code>boolean</code></td>
        <td><code>false</code></td>
        <td>Allows close the modal by clicking the overlay.</td>
    </tr>
    <tr>
        <td>effectName</td>
        <td><code>string</code></td>
        <td>(empty)</td>
        <td>Allows the user select a predeterminated effect to open the modal.</td>
    </tr>
</table>

A modal instance has four events to notify when it was opening, closing, opened and closed and can be called as follows:

```javascript
// Notify when modal is opening.
modal.opening.add(() => { /* ... */ });

// Notify when modal is closing.
modal.closing.add(() => { /* ... */ });

// Notify when modal is opened.
modal.opened.add(() => { /* ... */ });

// Notify when modal is closed.
modal.closed.add(() => { /* ... */ });
```

### Create your own effect
To create your own effect you need to create two CSS styles that will be applied to the `.pl-modal-content` element. The first style represents the initial state of the modal with the properties that will be affected and the second represents the open state of the modal, the transition property of CSS3 will take care of the magic.
Here is how to assign the initial state to the element `.pl-modal-content`:

```css
/* Initial state of "custom-effect" */
.custom-effect .pl-modal-content {
    opacity: 0;
    
    -webkit-transition: opacity 375ms; 
    transition: opacity 375ms;
}
```


To declare the open state to the modal, the `.pl-modal-open` class will be added to the declaration of our custom style and it must be a parent node of the `.pl-modal-content` element as shown below:
```css
/* Open state of "custom-effect" */
.custom-effect.pl-modal-open .pl-modal-content {
    opacity: 1;
}
```

**Let's call our new custom effect.**

To call our new custom effect we need create an instance of `pl.Modal` and set the name of our effect in the variable `effectName` in the `settings` object that we passed to the constructor as shown below:

```javascript
/* Call our new custom effect */
let modal = new pl.Modal({ effectName: 'custom-effect' });
```

### Static Methods
<table>
    <tr>
        <th>Name</th>
        <th>Return value</th>
        <th>Description</th>
    </tr>
    <tr>
        <td><code>transitionSelect()</code></td>
        <td><code>string</code></td>
        <td>Get the name of <code>transitioned</code> supported by used browser.</td>
    </tr>
    <tr>
        <td><code>extendsDefaults(source: object, settings: object)</code></td>
        <td><code>object</code></td>
        <td>Mix two objects.</td>
    </tr>
</table>

### Events
<table>
    <tr>
        <th>Name</th>
        <th>Return value</th>
        <th>Description</th>
    </tr>
    <tr>
        <td><code>closed</code></td>
        <td><code>pl.Event</code></td>
        <td>Get closed event.</td>
    </tr>
    <tr>
        <td><code>opened</code></td>
        <td><code>pl.Event</code></td>
        <td>Get opened event.</td>
    </tr>
</table>

### Methods
<table>
    <tr>
        <th>Name</th>
        <th>Return value</th>
        <th>Description</th>
    </tr>
    <tr>
        <td><code>close()</code></td>
        <td><code>void</code></td>
        <td>Close modal.</td>
    </tr>
    <tr>
        <td><code>changeEffect(effectName: string)</code></td>
        <td><code>void</code></td>
        <td>Change current modal effect.</td>
    </tr>
    <tr>
        <td><code>open(element: HTMLElement|string)</code></td>
        <td><code>void</code></td>
        <td>Open modal with passed element.</td>
    </tr>
    <tr>
        <td><code>setContent(element: HTMLElement|string)</code></td>
        <td><code>void</code></td>
        <td>Change modal content with passed element.</td>
    </tr>
</table>

### Getters
You can access to elements of `pl.Modal` as read only with the follow getters:

<table>
    <tr>
        <th>Name</th>
        <th>Return value</th>
        <th>Description</th>
    </tr>
    <tr>
        <td><code>overlay</code></td>
        <td><code>HTMLElement</code></td>
        <td>Gets the overlay element.</td>
    </tr>
    <tr>
        <td><code>modal</code></td>
        <td><code>HTMLElement</code></td>
        <td>Gets the modal element.</td>
    </tr>
    <tr>
        <td><code>content</code></td>
        <td><code>HTMLElement</code></td>
        <td>Gets the content element.</td>
    </tr>
    <tr>
        <td><code>closeButton</code></td>
        <td><code>HTMLElement</code></td>
        <td>Gets the close button element.</td>
    </tr>
</table>

### Browser Support
