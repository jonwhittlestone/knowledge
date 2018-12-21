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

### 03-42 - loop through range of integers   ###
- `<div v-for="(value, key, index) in person">{{ key }}: {{ value }} {{index}}"></div>`
- `<span v-for="n in 10">{{n}}</span>`

### 03-43 - keeping track of elements with v-for   ###
- to ensure vuejs knows about the position and the item (element itself) to be safe against reording, assign a unique ky with the `v-bind` syntax
- if you get strange bugs with a v-for where items appear in the wrong order, you probably aren't assigning a key
- `<li v-for="(ingredient, i) in ingredients" :key="ingredient">{{ingredient}}`


### 03-44 - Module wrap up   ###
- conditionals and lists
- loops

----


## Module 04 of 24 Project - The monster slayer ##


### 04-46 - Introduction challenge   ###
- https://github.com/skdigital/vue-monster-slayer 
- v-if for conditionall showing things, setting styles, v-for, two rounds getting execited for you and monster
- styles and html can be found

- My version of project: https://github.com/jonwhittlestone/vue-monster-slayer

### 04-47 - setting up course project   ###

### 04-48 - creating the vue instance and styling the health bars   ###

### 04-49 - start a new game, and actions  ###
- `v-else` only works with containers of the same type eg. `<section>`

### 04-50 - implementing a start game method  ###

### 04-51 - implementing an attack game method  ###
- create each function in `methods()` for each action button

### 04-52 - write better code  ###
- check if we win `checkWin()`

### 04-53 - Implementing special attack  ###
- code duplication
- monster attacks

### 04-54 - implementing a heal method  ###
- always heal by 10
- when you heal, monster always atacks
- don't want to heal in exceess of maximum health

### 04-55 - implementing the give up method  ###

### 04-56 - adding items to a log  ###
- `this.turns.unshift({ isPlayer: true, text: 'Player hits monster for' + damage })`

### 04-57 - skkhowing a log with v-for ###

### 04-58 - finishing the log ###

### 04-59 - add conditional styling to log ###
- `:class=~{'player-turn': turnisPlayer, 'player-turn' : 'monser-turn'}`

### 04-60 - wrap up ###

----

## Module 05 of 24 - Understanding the Vue instance

### 05-62 - Module Introduction  ###
- how it works
- which properties are created
- what is the lifecycle
- theoretical module

### 05-63 - some basics  ###
- http://jsfiddle.net/smax/9a2k6cja
- contains computed, watch
- the vue instance is the middleman between html code and business logic
- dependencies where we depend on the value of another property (computed properties)
- can have more than 1 vue instance
- can access vue instance from outside
 
### 05-64 - multiple instances  ###
- it's ok to control multiple peices with multipe vue instances
- can only control specific instance with this keyword, it's encapsulated, there is no connection between the two instances
- can see when only want to have a page show a widget (eg. calendar) and not a SPA


### 05-65 - accessing the vue instance from outside  ###
- `onChange: function() {$vm1.title = 'Changed!'}`
- probably better just to include same properties in same vue instance in the first place
- can set outside of vue instance
- `$vm1.title`  // vuejs does this automatic proxying for us

### 05-66 - how vuejs manages data and methods  ###
- vm0 is the core object of vue instance
- vuejs will take instance and take data properties and methods and use them as native and sets as a watcher so it knows when to update the DOM

- watcher layer where recognised where something has changed but we cannot create reactive properties from outside the vue instance. getters and setters are created by vuejs when created in the constructor

### 05-67 - a closer look at el and data  ###
- `$el` refers to our template and html code
- `$data`
- is possible to create the data before you create the vue instance and then pass it to the constructor `vm1.data = yourDataObject`
- vuejs does not create enclosed world and is able to interact with the JavaScript code around it
- you don't have to create a JS-only application

### 05-68 - placing $ref and using in templates  ###
- `<button v-on:click="show" ref="myButton``">Button Text</button>`
- `this.$refs.myButton.innerText = 'Test';`
- vuejs will override this behaviour rendering it based on its internal template
- this is not reactive and your changes with `ref` maybe overrided
- refs is based used for getting a value rather than setting

### 05-69 - where to learn more about the vuejs api  ###
- https://vuejs.org/v2/api/

### 05-70 - mounting a template  ###
- ` vm1.$mount('#app');`
-  properties prefixed with `$` are the native properties/methods we can use
- actually now an underscore `console.log(vm1._data.title);`
- may have a use case where the object for mounting the vue instance does not exist yet
- `var vm3 = new Vue({template: '<h1>Hello</h1>'})`
- `document.getElementById('app3').appendChild(vm3.$el);`
- ^ not common

### 05-71 - using components  ###
- create a reusable component with selector `<hello`>
- 
    Vue.component('hello', {
        template: '<h1>Hello!</h1>'
    });
    
### 05-72 - limitations of using components  ###
- precompiled version
- $template have to specifiy everything as a string

### 05-73 - VueJS DOM updating  ###
- it's not reloading the page, its updating parts of it via JavaScript
- the Vue instance holds a template 
- each property we set up has its own watcher
- accessing the real DOM is the part which affects performance the most
- Virtual DOM is the intermediary and a copy of the DOM parsed in JavaScript and watches the changes and writes them to the Virtual DOM
- and checks for differences and then updates the real DOM

## 05-74 - VueJS Instance lifecycle  ###
- we can tap into this to update certain code with hooks
- see diagram


### 05-75 - VueJS lifecycle in practice  ###
- by adding them as functions to the vue instance
- not in `methods `property, but on the root
- `beforeCreate()`
- `created()`
- beforeMount()
- mounted()
- beforeUpdate()
- updated() // after DOM has been updated
- `beforeDestroy()`     //do some cleanup to free up resources
- `destroyed`()`

### 05-76 - module wrap up  ###
- how vuejs creates instances and the lifecycle hooks
- virtual DOM diffing
----

## Module 06 of 24 - Moving to a real development workflow with webpack and vue-cli ##

### 06-78 - Module Introduction ###

### 06-79 - Why we need a dev server ###
- so vuejs can work with real HTTP transactions 

### 06-80 - What is a development workflow ###
- use ES6, be able to transform before going to production server
- can compile single file templates (instead of using `el` property and inferring template from DOM
- can apply preprocessors and use next gen JS features
- compiler is removed from final vuejs package so 30% smaller in size
 
### 06-81 - using vue-cli ###
- if we went on our own, we could use webpack on our own
- use vue cli to fetch vuejs project templates with a build process already set up

### 06-82 - installing ###
- `vue init webpack-simple vue-cli`
- `cd vue-cli; npm install`
- `npm run dev`
- most packages just needed for development
 

### 06-83 - an overview of file structure ###
- `/home/jon/code/playground/vue/vue-cli`
 

### 06-84 - Understanding .vue files ###
- outsource template and vue.js code to separate files but will run natively in browser
- override el selector with ES6 `render()` function
- specifying template, not as a string but a compiled vuejs template
- `.vue` files always have a `<template>`, then `<script>` containing like a new vue instance, then possible styling
-  still works if remove all template and just leave in script: `export default {}`

### 06-85 - Understanding the object in the Vue file ###
- whatever we export is a Vue instance
- add `data` and `methods` if we want

### 06-86 - how to build app for production ###
- `npm run build` will minify and create `/dist` folder

### 06-87 - wrapup ###
----

## Module 07 of 24 - An introduction to Components ##

### 07-90 - Module Introduction ###
- reusable components to put UI and business logic in different places


### 07-91 - Intro to components ###
- a component extends the vue instance
- simple example, repeatable as often as you want
- like our own htnml element
- make sure it is unique/prefix
- `Vue.component('my-selector', {data:function(){return{status:'Critical'}}});`
- wrap data property in a function so it doesn't intefere

### 07-92 - storing data in components ###
- there is an issue with having a shared data object
- so return a function containing the variable and then we have two differenct objects / locations in memory
- `this` will only refer to the current component instance because it is used in the context of the component
- each vue component is its own component and we run into problems when sharing a data source

### 07-93 - registering components locally and globally ###
- use same selector, but different component
- assign the instance to a variable and tell which local component to use with the `components` variable to set up using a local instance
- to use globally - `Vue.component('my-cmp', {})`

### 07-94 - The root components in the App.vue file ###
- the `render` function is a better alternative to the `template` property
- already exporting an object as root Vue instance, remember to return the `data` property

### 07-95 - Creating a new component ###
- https://github.com/neutraltone/vue-js-2-the-complete-guide/blob/master/7-an-introduction-to-components/introduction-to-components/src/Home.vue
- can use ES6 since it's getitng compiled to ES6
- `main.js` is the entry point
- the template tag must only have one child / wrap all template code in one root element`i


### 07-96 - using components ###
- file naming convention `ServerStatus.vue` but unrelated to selector that you use
- track the component 5 times by using `v-for` directive
- https://github.com/neutraltone/vue-js-2-the-complete-guide/blob/master/7-an-introduction-to-components/introduction-to-components/src/Home.vue#L3
- using global and local component
- import them in other files with ES6 (required for this multiple file set up)

### 07-97 - moving to a better folder structure  ###
- structure your folders according to feature
- `src/components/Shared`

### 07-99 - how to name components and selectors  ###
- we can use case sensitive selectors if we want as its being compiled to javscript
- vue.js will automatically give us access to the hyphenated name (convention to use `<app-header>` in template)

### 07-100 - scoping component styles  ###
- any style set up will be applied globally so add `<style scope>`
- vuejs emulates the shadow dom, a dom within a dom (sub doms)

### 07-101 - wrap up   ###
- register components globally/locally
- choose selector names
- styling
- directory structure

----
## Module 08 of 24 - Communicating between components ##

- how to send data from a parent to a child
- not just contained peices of code, but there are communications accross components

### 08-103 - Module Introduction ###
- finished module app:
    - /home/jon/code/playground/vue/section8-component-communication/dl/130 Section-Code-Finished/Section Code (Finished)  
    

### 08-104 - Communication problems ###
- /home/jon/code/playground/vue/section8-component-communication/dl/104 Section-Code-Start/Section Code (Start)
- how to get the name from the parent component

### 08-105 - transferring from parent to child component using props ###
- `props`
- properties set from outside
- tell `UserDetail.vue` by adding `props` array and will give us access to name
- in order to actually pass it:
    - `<app-user-detail v-bind:name='name'></app-user-detail>`
- passing a dynamic property using a colon to make it dynamic

### 08-106 - naming props ###
- case sensitive

### 08-107 - using props in Child component ###
- as well as output in child template, we can use it in Vue instance
- as long as it's in props, it can be accessed like a normal property

### 08-108 - Validating props ###
- if you want to validate, `props` should be an object
- making sure only get the data we want to get
- `props {myName: String}` 
- Expected String, got Number
- `required: true` to ensure that the property is passed
- can set a `defaault` instead of `required`
 
### 08-109 - using custom events for child parent communication   ###
- pass an event to our parent component
- reset name
-  the properties are only a pointer to a place in memory
- difference between reference types and primitive types
- `this.$emit('nameWasReset', this.myName);`
- listen to in parent component - `<app-user-detail @nameWasReset="name=$event"></app-user-detail>`

### 08-110 - understanding unidirectional data flow ###
- generall communication is unidirectional meaning the data flowas from parent to child and child to parent by not from child to child

### [08 111](08-111) - communicating with callback function ###

### 08-112 - getting data from one child to another child ###
- communication between sibling components
- editAge()
- `UserEdit.vue`
- after setting up an `$emit()` event on the child component, then set up a listener on the parent - `$ageWasEdited="age=$event`
- pass as prop to parent and all children which use property
- another alternative is to use an event bus
 
### 08-113 - event bus, using an object to listen to events and pass on  ###
- in Angular 2, this is known as a service
- state management for small to medium size applications
- store in a constant `eventBus` which is a new vue object and then export it
- import named export into a component
- add a new lifecycle hook `created() {}` and register a [listener](listener)
- create event bus in `main.js` before other compoennts are loaded
-  managing state of a property across multiple components can get very complicated quickly so most people use vuex

 
### 08-114 - centralising code in an event bus vue instance  ###
- in child component can use `eventBus.changeAge(this.userAge);`
- makes a lot of sense if you don't want to duplicate code, accessible from anywhere in application as long as you import it

### 08-115 - wrap up  ###
- cross component communication
- primitive and referece types
- how to pass data

----

## Module 09 of 24 - Advanced Component Usage ##

### 09-117 - Module Introduction ###

### 10-118 - setting up module project ###
- simple quote component with single template file
- dynamically set the content of compoenent from the parent

### 10-119 - passing content - suboptimal solution  ###
- sending ' to `<app-quote>`a wonderful quote'
- vuejs offers us slots to be able to reserve for content being passed from outside 

### 10-120 passing content with slots  ###
- in child component where we want to receive the data, add `<slot>` component and renders the content we are passing from outside

### 10-121 how slot gets compiled and styled  ###
- child component styling is applied to the data coming from outside
- if parent has the styling (and set to scoped), the styling won't apply
- compiling the template ('rendering any vuejs operation')  the component where you actually have the code for the template will be the one doing the changes
- styling on the child, everything else (where you can use vue syntax) is on the parent

### 10-122 using multiple named slots  ###
- one slot for the title, one for the content
- `<h2 slot="content">distribute the content into a named slot</h2>`

### 10-123 default slots and slot default  ###
- vuejs will treat the slot without a name as the default slot
- can also set up default content to be displayed:
    - `<slot name='subtitle'>this will get overwritten if there is data</slot>`

### 10-124 slot summary   ###
- help to dristribute content in other components
- make sure content is distributed in html as you intend

### 10-125 switching multiple components with dynamic components   ###
- eg. `appAuthor`, `appNew`
- one place where will display one of three components depending which button is pressed
- use `<component :is="selectedComponent``">` to dynamically add components and is bound to variable
- dynamically replace content of components 

### 10-126 dynamic component behaviour   ###
- incrememnt a counter in a component to see if the component stays alive or is destroyed and created new
- the counter starts agan at zero meaning the component is destroyed and recreated (could have also tapped into the `destroyed()` lifecycle hook)

### 10-127 how to override to destroy behaviour of dynamic components   ###
- keeping dynamic components alive
- `<keep alive><component :is='selectedComponent'><p>Default Content</p></component></keep-alive>`
- but then lose `destroyed()` lifecycle hook
 
### 10-128 dynamic component lifecycle hook   ###
- `deactivated()`
- `activated()`

### 10-129 wrap up    ###
- slots to distribute content
- dynamic components depending on the state of a property
 
----

## Module 10 of 24 - Second Course Project - Wonderful Quotes ##

### 10-131 - Module Introduction ###
-  `/home/jon/Dropbox/playground/vue-section10-quotes/jw`

### 10-132 - setup ###

### 10-133 - initialising the app ###

### 10-134 - creating the application components ###
- use a `v-for` to replicate quote as often as needed inside of row
 

### 10-136 - Allowing users to create qotes with a newquote component ###
- `<button @click.prevent="createNew">Add Quote</button>`
- add prevent modifier to prevent default behaviour
- in `createNew()` method we `emit()` the new quote to the parent component

### 10-137 - Adding quotes with custom events ###
- `this.$emit('quoteAdded', this.quote);`
- in the parent component, listen to quote added with:
    - `<app-new-quote @quoteAdded='newQuote'></app-new-quote>`

### 10-138 - adding an info box ###

### 10-139 - Allowing for quote deletion ###
- native modifier, react to a click on this component if it happens on the native element 
- `<app-quote v-for="quote in quotes" @click.native='deleteQuote'>{{quote}}</app-quote>`
- add listener in parent component, and implement method to remove the quote from the `quotes[]` array


### 10-140 - controlling quotes with a progress bar ###

### 10-141 - finishing touches and state management ###
- pass `quoteCount` from parent down to child `<app-header :quoteCount='quoteCount'></app-header>`

----

## Module 11 of 24 - Handling User Input with Forms ##

### 11-143 - Module Introduction ###

### 11-144 - basic input form binding ###
- use `<input v-model='email'>`
- vuejs will check what the source of the editing automagically

### 11-145 - grouping data with pre-populating inputs  ###
- can bind to a property in an object to nest properties

### 11-146 - modifying user input with input modifiers  ###
- reacts to the input event by default
- listen to the change event with the lazy modifier
- `<input v-model.lazy='userData.password'>`
- `<input v-model.number='userData.age>`

### 11-147 - binding text area and saving line breaks  ###
- don't use string interpolation to set default for value for `<textarea>`
- to keep line break use normall css `<p style='whitespace: pre'> something</p>`

### 11-148 - checkboxes and saving data in arrays   ###
- the property you want to bind to should be an array and vuejs will detect that it should be an array and merge the value of the checkboxes

### 11-149 - using radio buttons  ###
- map the same variable to both radio button elements and vuejs recognises that only one is selectable and are party of a group

### 11-150 - handling dropdows with select and option  ###
- `<option v-for='priority in priorities' :selected="priority == 'Medium'" v-model="selectedPriority">{{ priority }}</option>`

### 11-151 - what v-model does and how to create a custom control ###
- switch component
- make our own UI component
 
### 11-152 - creating custom input control ###
1. add component in App.vue
2. add in html form
3. set `dataSwtich` in `data()` as `false`
4. add `<app-switch v-model="dataSwitch"></app-switch>`
5. Set up value prop in `Swtich.vue` and emit input event
6. put `@click=switched(true)` handler in component template and set class depending on reactive :`value` property
7. add `methods.switched()` property
8. go back to main component with sanity output

### 11-153 - submitting a form ###
- handled the data in the main component's `submitted()` method

### 11-154 - wrap up ###
----

## Module 12 of 24 - Using and creating directives ##


### 12-156 - Module Introduction ###
- built-in directives prefixed with `-` like `<component v-bind:`

### 13-157 - Understanding directives ###
- Built-in directive `v-for`, `v-bind`
- the name follows after `v-`
- eg. `<p v-html='<strong>hi</strong>'></p>`
- Register it in app.js with `Vue.directive('highlight');`

 
### 13-158 - 5 hook functions ###
- https://vuejs.org/v2/guide/custom-directive.html#Hook-Functions 
- are like lifecycle hooks
- `bind(el, binding, vnode)` - once directive is attached
- `inserted(el, binding, vnode)` - once inserted in the parent node
- `updated(el,binding,vnode, oldVnode)`
- componentupdated
- unbind

### 13-159 - creating a simple directive ###
- create a global directive
 
### 13-160 - passing values to custom directives ###
- whatever we enter between quotes, is the value of the binding

### 13-161 - passing arguments to custom directives ###
- `if (binding.arg == 'background') el.style.backgroundColor = binding.value`
- eg. `<p v-highlight:background='red'></p>`
 
### 13-162 - modifiers ###

### 13-163 - a summary ###

### 13-164 - a local directive ###
- add directive property to the component

### 13-165 - using multiple modifiers - blink ###
- `let` is the es6 block scope to define new variable
- `setInterval(()=> {// logic for blinking here},1000);` 
 
### 13-166 - passing more complex values to directives ###
-  https://vuejs.org/v2/guide/custom-directive.html#Object-Literals
- can pass in an object as a value

### 13-167 - wrap up ###

----


## Module 13 of 24 - Improving your App with Filters and Mixins ##
- https://vuejs.org/v2/guide/filters.html
- 

### 13-169 - module intro  ###

- 
----

## Module 14 of 24 - Animations and Transitions ##

- Half way through lessons count!!
 
### 14-180 - Module Introduction ###

----

## Module 15 of 24 - Connecting to Servers ##

### 15-208 - Module Introduction ###

----

## Module 16 of 24 - Routing a Vuejs App ##

### 16-222 - Module Introduction ###

----

## Module 17 of 24 - Better State Management ##

### 17-250 - Module Introduction ###

----

## Module 18 of 24 - Final Project - The stock trader ##

### 17-273 - Module Introduction ###

----
## Module 19 of 24 - Deploying ##

### 17-299 - Module Introduction ###

----
## Module 20 of 24 - Course Roundup ##

### 20-302 - Course Roundup ###

----
## Module 21 of 24 - All course exercies ##

### 21-302 - Exercises ###

----
## Module 22 of 24 - Axios ##


### 22-330 - About this section ###

----
## Module 23 of 24 - Authentication ##

### 23-342 - About this section ###

----
## Module 24 of 24 - Form Input Validation ##

### 24-360 - About this section ###

### 23-342 - About this section ###


### 22-330 - About this section ###
### 21-302 - Exercises ###

