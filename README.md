# Boiled Page slider component and script

Slider SCSS singleton and script for Boiled Page frontend framework. They are intended to create responsive content sliders which work with grid component.

## Install

Place `_slider.scss` file to `/assets/css/components` directory, and add its path to component block in `assets/css/app.scss` file. 

You will also need to place `slider.js` to `/assets/js` directory and add its path to `scripts` variable in `gulpfile.js` to be combined with other scripts.

## Usage

### Slider component

#### Classes

Class name | Description | Example
---------- | ----------- | -------
`slider` | Applies a slider. | `<div class="slider"></div>`
`slider-viewport` | Applies a viewport inside slider. | `<div class="slider-viewport"></div>`
`slider-list` | Applies a slider list inside viewport. Grid component is used to set width of slider list items. | `<ul class="slider-list grid"></ul>`
`slider-action-list` | Applies a list of actions inside slider. Grid component can be used optionally for alignment. | `<ul class="slider-action-list"></ul>`

#### Examples

##### Example 1

The following example shows a slider

```html
<div id="sample-slider" class="slider" aria-describedby="sample-slider-description" tabindex="0">
  <p id="sample-slider-description" class="is-visually-hidden">Sample slider description</p>
  <div class="slider-viewport" data-slider-viewport>
    <ul class="slider-list grid grid--gutter" data-slider-list>
      <li class="grid-col grid-col--1of3 grid-col--small--1of2 grid-col--xsmall--full" data-slider-list-item>
        <div class="box">
          <h3 class="h5">
            <a href="#">Sample slider list item 1</a>
          </h3>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus blandit leo at tempor iaculis. Curabitur fringilla non enim in malesuada. Proin ipsum nisl, scelerisque pharetra lectus at, ultrices mollis sem.</p>
        </div>
      </li>
      <li class="grid-col grid-col--1of3 grid-col--small--1of2 grid-col--xsmall--full" data-slider-list-item>
        <div class="box">
          <h3 class="h5">
            <a href="#">Sample slider list item 2</a>
          </h3>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus blandit leo at tempor iaculis. Curabitur fringilla non enim in malesuada. Proin ipsum nisl, scelerisque pharetra lectus at, ultrices mollis sem.</p>
        </div>
      </li>
      <li class="grid-col grid-col--1of3 grid-col--small--1of2 grid-col--xsmall--full" data-slider-list-item>
        <div class="box">
          <h3 class="h5">
            <a href="#">Sample slider list item 3</a>
          </h3>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus blandit leo at tempor iaculis. Curabitur fringilla non enim in malesuada. Proin ipsum nisl, scelerisque pharetra lectus at, ultrices mollis sem.</p>
        </div>
      </li>
      <li class="grid-col grid-col--1of3 grid-col--small--1of2 grid-col--xsmall--full" data-slider-list-item>
        <div class="box">
          <h3 class="h5">
            <a href="#">Sample slider list item 4</a>
          </h3>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus blandit leo at tempor iaculis. Curabitur fringilla non enim in malesuada. Proin ipsum nisl, scelerisque pharetra lectus at, ultrices mollis sem.</p>
        </div>
      </li>
      <li class="grid-col grid-col--1of3 grid-col--small--1of2 grid-col--xsmall--full" data-slider-list-item>
        <div class="box">
          <h3 class="h5">
            <a href="#">Sample slider list item 5</a>
          </h3>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus blandit leo at tempor iaculis. Curabitur fringilla non enim in malesuada. Proin ipsum nisl, scelerisque pharetra lectus at, ultrices mollis sem.</p>
        </div>
      </li>
      <li class="grid-col grid-col--1of3 grid-col--small--1of2 grid-col--xsmall--full" data-slider-list-item>
        <div class="box">
          <h3 class="h5">
            <a href="#">Sample slider list item 6</a>
          </h3>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus blandit leo at tempor iaculis. Curabitur fringilla non enim in malesuada. Proin ipsum nisl, scelerisque pharetra lectus at, ultrices mollis sem.</p>
        </div>
      </li>
    </ul>
  </div>
  <ul class="slider-action-list grid grid--gutter grid--gutter--half grid--uniform grid--center">
    <li class="grid-col">
      <button type="button" class="slider-action-prev button" aria-controls="sample-slider" data-slider-prev>Prev</button>
    </li>
    <li class="grid-col">
      <button type="button" class="slider-action-next button" aria-controls="sample-slider" data-slider-next>Next</button>
    </li>
  </ul>
</div>
```

Add `sampleSlider` property to `app` object in `assets/js/app.js`.

```js
sampleSlider: null
```

Place the following code inside `assets/js/app.js` to initialize element with `sample-slider` id as a slider.

```js
// Initialize sample slider
var sampleSliderElem = document.getElementById('sample-slider');
app.sampleSlider = new Slider({
  element: sampleSliderElem,
  viewport: sampleSliderElem.querySelector('[data-slider-viewport]'),
  list: sampleSliderElem.querySelector('[data-slider-list]'),
  items: sampleSliderElem.querySelectorAll('[data-slider-list-item]'),
  prevTrigger: sampleSliderElem.querySelector('[data-slider-prev]'),
  nextTrigger: sampleSliderElem.querySelector('[data-slider-next]')
});
app.sampleSlider.init();
```

Place the following code inside the `onBreakpointChange` function in `assets/js/app.js` to update active and visible slider items on breakpoint changes.

```js
// Update active and visible slider items
sampleSlider.recalc();
```

#### Extension ideas

##### Slider dots

```scss
/* Slider component extensions */
div.slider {

  // Slider dots
  > ul.slider-dot-list {
    display: flex;
    justify-content: center;
    list-style: none;
    margin-left: ($box-padding * -0.5);
    padding-left: 0;

    > li {
      padding-left: ($box-padding * 0.5);

      > button {
        background-color: $border-color;
        border-radius: 50%;
        border: none;
        cursor: pointer;
        display: inline-block;
        height: 1rem;
        padding: 0;
        transition: background-color $slider-dot-transition;
        width: 1rem;

        body.no-touch &:hover {
          background-color: darken($border-color, 5);
        }

        &.keyboard-focus:focus {
          box-shadow: inset 0 0 0 3px $focus-color;
          outline: 0;
        }

        &.is-active {
          background-color: $link-color;

          body.no-touch &:hover {
            background-color: $link-color;
          }
        }
      }
    }
  }
}
```

### Slider script

#### Usage

To create a new slider instance, call `Slider` constructor the following way:

```js
// Create new slider instance
var slider = new Slider(options);

// Initialize slider instance
slider.init();
```

#### Options

The following options are available for slider constructor:

Option| Type | Default | Required | Description
------|------|---------|----------|------------
`element` | Object | null | Yes | Element is a wrapper of slider.
`viewport` | Object | null | Yes | Viewport is used to listen for dragging events.
`list` | Object | null | Yes | List is translated for visible items.
`items` | Object | null | Yes | A `NodeList` type object of slider list items.
`prevTrigger` | Object | null | No | Previous trigger slides slider to previous item on click.
`nextTrigger` | Object | null | No | Next trigger slides slider to next item on click.
`slideToTriggers` | Array | null | No | Array of items which slides slider to a given item. `trigger` and `index` properties must be defined for each item.
`initialIndex` | Number | 0 | No | Initial active index.
`rewind` | Boolean | true | No | Enable rewinding.
`touchDrag` | Boolean | true | No | Enable touch dragging.
`mouseDrag` | Boolean | true | No | Enable mouse dragging.
`initCallback` | Function | null | No | Callback function after slider is initialized.
`nextCallback` | Function | null | No | Callback function after slider is slided to next item.
`prevCallback` | Function | null | No | Callback function after slider is slided to previous item.
`slideToCallback` | Function | null | No | Callback function after slider is slided by an item of `slideToTriggers`, or `slideTo()` method is called.
`recalcCallback` | Function | null | No | Callback function after slider is recalculated.
`dragStartCallback` | Function | null | No | Callback function after dragging is started.
`dragMoveCallback` | Function | null | No | Callback function after dragging.
`dragEndCallback` | Function | null | No | Callback function after dragging is ended.
`destroyCallback` | Function | null | No | Callback function after slider is destroyed.
`hasNoNextItemClass` | String | 'has-no-next-item'' | No | Class added to slider when `rewind` is false and no next visible item is available.
`hasNoPrevItemClass` | String | 'has-no-prev-item' | No | Class added to slider when `rewind` is false and no previous visible item is available.
`hasMouseDragClass` | String | 'has-mouse-drag' | No | Class added to slider when `mouseDrag` is true.
`hasPointerDragClass` | String | 'has-pointer-drag' | No | Class added to slider when `touchDrag` is enabled and pointer events are supported.
`hasTouchDragClass` | String | 'has-touch-drag' | No | Class added to slider when `touchDrag` is enabled and touch events are supported.
`isDraggingClass` | String | 'is-dragging' | No | Class added to slider when it is dragging.
`isMouseDraggingClass` | String | 'is-mouse-dragging' | No | Class added to slider when the type of dragging is mouse.
`isPointerDraggingClass` | String | 'is-pointer-dragging' | No | Class added to slider when the type of dragging is pointer.
`isTouchDraggingClass` | String | 'is-touch-dragging' | No | Class added to slider when the type of dragging is touch.
`isRewindingClass` | String | 'is-rewinding' | No | Class added to slider when it is rewinding.
`isSlidingClass` | String | 'is-sliding' | No | Class added to slider when it is sliding.
`isSlidingFinishedClass` | String | 'is-sliding-finished' | No | Class added to slider after sliding is finished.
`isActiveClass` | String | 'is-active' | No | Class added to slider item when it is active.
`isVisibleClass` | String | 'is-visible' | No | Class added to each visible slider item.

Available options for a slide to trigger object:

Option| Type | Default | Required | Description
------|------|---------|----------|------------
`trigger` | Object | null | Yes | Trigger slides slider to item with given index on click.
`index` | Number | null | Yes | Item's index where to slide on trigger click.

#### Methods

##### Initialize slider

`init()` - Initialize slider. It creates events, adds classes relevant to slider.

##### Slide to next item

`next()` - Increment active index by one, update slider.

##### Slide to previous item

`prev()` - Decrement active index by one, update slider.

##### Slide to item by given index

`slideTo(index)` - Set active index to given number, and update slider.

Parameter | Type | Required | Description
----------|------|----------|------------
index | Number | Yes | Index of item where to slide.
##### Update slider

`update()` - Update active and visible items based on active index.

##### Recalculate visible items

`recalc()` - Reset active index when visible items are wider than slider list's width, update slider.

##### Destroy slider

`destroy()` - Destroy slider. It removes events and classes relevant to slider.