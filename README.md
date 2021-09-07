# Flight Form
Responsive form for a flight booking website. Inspired by the form on the landing page for [Cheapflights](https://www.cheapflights.com/):

**Source**

![Original form inspiration](assets/source.gif)

**End Product**

![My version of the form](assets/finished-product.gif)

## My Approach
I started with a mobile-first approach here and used media queries to change component layout as viewport size grew.

I needed images inside my input fields and took two approaches to this:
- Absolutely positioning the icons in relation to a relatively positioned input.
- Using SVGs instead of icons as `background-image`s.

I opted for the second approach, to familiarize myself more with the `background-image` property, and as this also resulted in flatter HTML.

## Challenges
There is a lot to learn about forms and I feel I am only scratching the surface. A few things I learned:
- Due to differences in browser support and system styling, form widgets are hard to style consistently.
- Some widgets, such as datepickers and select dropdowns cannot have much styling applied at all. My replica isn't completely faithful to the orignal because this would require creating custom form controls with JavaScript. I will tackle this when the time comes.
- Some form controls don't inherit some text features, so to make forms consistent with the rest of the content, the following rule was added to the styling:
```
button, input, select, textarea {
  font-family: inherit;
  font-size: 100%;
}
```
- In order to achieve form control customization on the elements that allow it, the `-webkit-appearance: none;` declaration has to be used to remove default system styles. This allowed me more control over the look of my radio buttons, which meant I had to style the element from scratch, including its `:checked` state. Pseudo-elements and generated content make this straightforward.
- I also stripped my select dropdown of default system styles. I couldn't use generated content here to add styling because `<select>` elements don't support `::before` or `::after`. So adding any content here required a wrapper div.
- Learned about default padding for inline elements when I couldn't manage to get rid of a ~5px space between two input fields. There's [several tricks](https://stackoverflow.com/questions/9832754/i-cant-remove-the-margin-between-two-input-fields/44430919) to dealing with this and I wanted to make a note of it should I forget 😅
