# vue-over-body
Create modals, sidebars, notifications, pop ups with css transitions! 

## Demo
[Live Demo](http://marcodpt.github.io/vue-over-body)
with bulma css framework, but we do not impose any css framework

## Install
```
npm install --save vue-over-body
```

## Usage
```javascript
  import Vue from 'vue'
  import overBody from 'vue-over-body'

  new Vue({
    components: {
      'vue-over-body': overBody
    },
    data: function () {
      return {
        open: 1
      }
    }
  }).$mount('#app')
```

```html
  <vue-over-body :dim="false" :open="open" before="before" after="after" :transition="0.3">
    <div>
      <button @click="open = 0">&times;</button>
      <p>A little alert message!</p> 
      <p>For the users of your app!</p> 
    </div>
  </vue-over-body>
```

```css
  .before {
    top: 50px;
    right: -300px;
    width: 300px;
    background-color:yellow;
    position:absolute;
  }

  .after {
    right: 50px;
  }
```

### Props
 - open
   - type: Number
   - default: 0
   - description: 0 means hide, other number means z-index of the component
 - before
   - type: String
   - default: ""
   - description: css class aplied to slot parent, always active
 - after
   - type: String
   - default: ""
   - description: css class aplied to slot parent, active after the transition
 - transition
   - type: Number
   - default: 0.3
   - description: time of transition in seconds
 - dim
   - type: Boolean
   - default: true
   - description: make the background darker?
 - dialogStyle
   - type: Object
   - default: {}
   - description: style to be applied on dialog container

## Contribute
We need help! Our goals are:
 - CSS Transitions
 - Add tests
 - More usage examples and better home page
 - Add support to most browsers

What is outside of the scope of this project:
 - Create any kind of layout like buttons, headers, pre build alerts!
