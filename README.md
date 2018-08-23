# vue-over-body
Create modals, sidebars, notifications, pop ups! 
CSS framework agnostic!

## Demo
[Live Demo](http://marcodpt.github.io/vue-over-body)
in this demo was used bulma css framework

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
        open: 1,
        dialogClass: 'sampleNotification'
      }
    }
  }).$mount('#app')
```

```html
  <vue-over-body :open="open" dialogClass="notification">
    <div>
      <button @click="open = 0">&times;</button>
      <p>A little alert message!</p> 
      <p>For the users of your app!</p> 
    </div>
  </vue-over-body>
```

```css
  .notification {
    top: 50px;
    right: 50px;
    width: 300px;
    background-color:yellow;
  }
```

###Props
 - open
   - type: Number
   - default: 0
   - description: 0 means hide, other number means z-index of the component
 - dialogClass
   - type: String
   - default: ""
   - description: css class aplied to slot parent

## Contribute
We need help! Our goals are:
 - CSS Transitions
 - Add tests
 - More usage examples and better home page
 - Add support to most browsers

What is outside of the scope of this project:
 - Create any kind of layout like buttons, headers, pre build alerts!
