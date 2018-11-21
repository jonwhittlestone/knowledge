# Ultimate Vue.js Udemy Course #
* Plex: http://localhost:32400/web/index.html#!/server/f145ece5cbe45ac49c5ab58bd08851b4f312c16b?key=%2Flibrary%2Fsections%2F3
* Plex Playlist: http://localhost:32400/web/index.html#!/server/bc0049189e861dd58c943d9c7307957a899ce527/playlist?key=%2Fplaylists%2F74323
* nautilus "/home/jon/Videos/Learn/Udemy - vuejs-2-the-complete-guide" 
* Udemy course: https://www.udemy.com/vuejs-2-the-complete-guide/
* This file on github: https://github.com/jonwhittlestone/knowledge/blob/master/Vue.js.md

* Code samples: https://github.com/neutraltone/vue-js-2-the-complete-guide
----

## Module 02 of 24 Using VueJS to Interact with the DOM ##

### 02-12 Binding to Attributes ###

- cannot use curly braces in attributes but use directive `v-bind:href="vuejsVariableName"`


### 02-13 Understanding and Using Directives ###
- arguement allows you to pass dynamic data to HTML attributes

### 02-14 Disable re-rendering with v-once ###
- directive to mean that content is only rendered once `<h1 v-once>{{title}}</h1>`

### 02-15 How to output raw HTML ###
- vuejs escapes html so we do have problems with XSS attacks unless we use the directive `v-html` (good for blog posts)

### 02-16 Listening to Events ###
- `v-on:click="functionName"` the opposite of `v-bind` (instead of allowing us to pass data to it, we listen to receive something from template)

### 02-17 Getting Event Data from the Event Object ###
- default event object we can listen to
- `this.x = event.clientX;`


### 02-18 Passing your own Arguments with Events ###
- `<button v-on:click="increase(2, $event)">Click me</button>` 
- protected automatically created event object


### 02-19 Event modifier  ###
- to execute nothing, `event.stopPropogation();`
- or use a modifier; `<span v-on:movemove.stop="">DEAD SPOT</a>`
- for prevent default - `<span v-on:movemove.prevent="">prevent the elements default behaviour</a>`

### 02-20 Listening to keyboard events   ###
- with specific keys modifier `<input type='text' v-on:keyup.enter.space="alertMe"`

### 02-21 writing javascript code in templates   ###
- can include js in templates: `<button v-on:click="counter++">click me</button`

### 02-22 two-way binding  ###
- not just outputting data
- update the data property, including every where that it is output: `<input type="text" v-model="name">`

### 02-23 reacting to changes with computed properties  ###
- hard to maintain if `counter` needs to be updated from more than one location
- `data` object is not reactive
- could include in `methods()` with a `result()` method to DRY up code
    - disadvantage is that `result()` will get reexecuted regardless
- new method on vue instance: `computed: {}`
    - https://vuejs.org/v2/api/#computed
- output methods stored in `computed()` like you would a property stored in the data object
- the result is being cached

### 02-24 An alternative to computed properties  ###
- `watch()` object
- allows you to react to changes but it's more performant to use `computed()` properties
- `computed()` properties may not work when you need asynchronous tasks to be run
- to reset counter after 2 seconds, `setTimeout()` but in the closure, the vue instance must be stored in a separate variable `var vm = this;`
- 
### 02-25 - Shorthands  ###
- replace `v-on:click` with `@click='changeLink'`
- replace `v-bind:href="link"` with `<a :href="link">`

### 02-26 - Dynamic styling with CSS classes  ###
- `<div class="demo" @click="attachRed = !attachRed" :class="{red:attachRed}"></div>`

### 02-27 - Dynamic Styling with CSS - objects  ###
- if you don't want to store object in HTML template code so create computed property

### 02-28 - Dynamic Styling with CSS - Using Names  ###
- can attach multiple classes 
- can use an object where the key is the css class and the value is the condition

### 02-29 - setting styles without CSS classes  ###
- binding to style
- `<div class="demo" :style="{backgrounColor: red}"></div>`


### 02-30 - styling elements with array syntax  ###

### 02-31 - module wrap up   ###
- template syntax
- create reactive web app
- react to user apps
- dom interaction

---


## Module 03 of 24 Using conditionals and redering lists ##


### 03-33 - Module Intro ###

- only show parts of page under certain circumstances

### 03-34 - Conditional rendering with v-if ###

- eg. show an error message in case of a wrong input
- `<p v-if="">` we can bind to anything that evaluates to true/false
- v-if attaches and detaches from the DOM (and else nested elements)
- can extend with `v-else` that relates to the nearest `v-if`


### 03-36 - Using an alternative v-if syntax ###

- can also set up a `<template>` an HTML5 tag that does not get rendered in dom
- so can group multiple elements and we do not want a div/side effect that div introduces

### 03-37 - Don't detach it with v-show ###

- if you really want to hide it, rather than completely detach: `v-show`

### 03-38 - rendering lists with v-for  ###
- `<li v-for="ingredient in ingredients">{{ ingredient }}</li>`

### 03-39 - getting the current index   ###
- we can make the index available
- `<li v-for="{ingredient, i} in ingredients">{{ ingredient  }} ({{i}})</li>`


### 03-40 - an alternative v-for syntax   ###
- put everything within a `<template>` tag

### 03-41 - looping through objects   ###
- nested 
----


## Module 04 of 24 Project - The monster slayer ##



