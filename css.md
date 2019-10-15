# CSS

## Modern CSS for backend developers
Source: Laracasts

Date: 11/10/19

Covering the 'need-to-know' parts of CSS like Flexbox, tailwind, procedure for building

1. Structure
    - How to begin with the obvious
    - normalize.css
    - flexbox module - 'most powerful addition to css in last decade'
        - `display:flex`
        - by default `flex-direction: row`

2. Flex your Grids
    - display blocks in a row using utility class meaning every child element should display as a row
        - `<div class='row flex' style='justify-content:space between'></div>`
        - `<div class='col p-2' style='flex: 2'></div>` means takes up 200% of the space as other units 
            - (and add some padding for breathing space)
    - A flexed item can be its own flexed container
    - to align vertically, set child of `col` to `display:flex` and then `align-items:center`

3. Card Design
    - To start with, set up markup structure
    - center component on page: flexbox
        - `display:flex` on `<body>`, `align-items:center`
        - ..and `justify-content:center` and `height:100%` on both `<html>` and `<body>`
    - Apply padding to the card must be done on the child elements so as not to spoil the `background-color` of the main el
    - Lock the meta info to bottom: flexbox
        - `flex-direction:column /* vertical */` and child blocks have `flex:1`
    - distribute items equally with `justify-content:space-between` and `flex-direction:column`
    
4. Refactoring to Utility Classes
    - simply use tailwind cdn
    - Use help to look up definitions
        - https://tailwindcss.com/docs/text-color/https://tailwindcss.com/docs/text-color/
    - Enables you to rapidly bootstrap your markup file without constantly switching to external css file but can't always use utility classes when there are specific heights
    - Can set width with `class='w-64`
    - child takes up whole heigh of container - `.. class='h-full'`

5. Easy Flexbox Wins
    - Instant navigation, split-nav, align image with text, perfectly centred text
    - sticky footer - no matter how high the content is, stick the footer to bottom of page 

6.  FAQs
    - To and Fro with design and make tweaks to adjust and nudge spacing
7. Pricing selection design
    - Build in increments start with structure of markup
    - add a shadow with a utility class `class='shadow'`
    - make a component for a button so you only need to make changes in one place
    - Use tailwind's `@apply` directive to extract common utility patterns
        - https://tailwindcss.com/docs/extracting-components/#extracting-css-components-with-apply
        
8. Tailwind Customisation
    - can define the exact colours in `tailwind.js`

9. Call to Action Banner design
    - start with the most obvious thing - background
    - An image that includes the foreground illustrations is not v. responsive
    - **don't hardcode heights and try to use padding**
    - css supports multiple background images as comma separated list
10. Mobile First Design
    - `flex-wrap:wrap`  telling CSS to wrap on to a new line if you need to
    - Media Queries: "_If the browser window is at least 576px, on that condition, render relevant CSS, or I would like this class available_"
    - `lg:w-1/4` - tailwind uses sm,md,lg
    - tailwind is mobile-first so think of the minimum widths first

11. Mobile First Layouts
    - Get it to look good for a moblie device, and then grow from there
12. Peice by Peice Mobile Tweaks
    - more tweaking and considerations for mobile
13. Better sizing and spacing
    - relative ems
    - px to rem = {pixel_size} / {root_pixel_size}
    - tweak the root fontsize because all other fontsizes in tailwind are rems
    - wrap every section in `<section>`
14. Reverse the order
    - when optimising for mobile, so prefix `lg:` to `flex` to _turn off for mobile_
    - `flex-direction: column-reverse` which reverses the direct children
    
15. Make it Sticky
    - `position:sticky` is like a hybrid between `position:relative` and `position:fixed`
    - ie. normally it will display as relative but when it hits a certain offset, it switches to `fixed` until the end of its container
    - _'pin'_ it to the top by giving it a coordinate like `top:0`
    - not universally available currently in browsers - check with http://www.caniuse.com
16. Wield complete control over the order of elements
    - use flexbox ordering, when you need more control by tweaking the order of every direct child so for certin breakpoints, can reorder
    - a bit like z-index for ordering
    - default is `0` so value of `-1` places at the top but you do have to be explicit for every single item 
17. Modals with zero javascript
    - target elements based on what the #hash is
        - HTML: 
            - Open: `<a href="#join">Join</a>`
            - Close: `<a href="#">X</a>`
        - CSS: `.overlay:target{visibility:visible}`
