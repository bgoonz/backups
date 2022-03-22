# How to use CSS ::before and ::after to create custom animations and transitions - LogRocket Blog

[https://blog.logrocket.com/how-to-use-css-before-after-create-custom-animations-transitions/](https://blog.logrocket.com/how-to-use-css-before-after-create-custom-animations-transitions/)

![How%20to%20use%203fc9e/how-to-use-css-before-after-create-custom-animations-nocdn.png](How%20to%20use%203fc9e/how-to-use-css-before-after-create-custom-animations-nocdn.png)

Have you ever come across a beautifully animated component on a website and thought to yourself, "Wow! That's sleek — I wish I could do that," but quickly gave up on the thought because you assumed it was either beyond your skill or only achievable using an animation library of some sort?

You'd be surprised to learn that most of these complex designs you see every day were created with plain vanilla CSS, using the power of pseudo-elements. In this article, we'll be looking at how to utilize these pseudo-elements to create staggering effects.

We'll learn about pseudo-elements — specifically the `::before` and `::after` pseudo-elements — and how we can get creative with them to create staggering animated transitions. We'll start by creating a simple but creative animated button to get a feel for it, then take it a notch higher by creating an animated profile card that showcases these pseudo-elements' true power.

### Why use animations?

Animations create micro-interactions between your users and your website. It can be quite difficult to grab a user's attention, but a well-designed and well-placed animation can pull users in by getting them interested in the content of your website.

Cool animations also give life to simple-looking interface designs and also help to improve the user experience when they're designed around user actions by providing visual feedback.

## Prerequisites

Before we can get to the fun part, we have to cover some basics to familiarize ourselves with all that's required to make our animations work. You should have:

- A basic understanding of HTML
- A basic understanding of CSS
- Code editor and browser

## What are pseudo-elements?

[Pseudo-elements are CSS selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements) used to insert artificial or decorative content (i.e., content that is not found in the actual HTML markup) and to style certain parts of an element. There are several pseudo-elements like the `::before`, `::after`, `::placeholder`, `::first-letter`, etc. But in this article we'll be focusing on just two, `::before` and `::after`.

### The `::before` pseudo-element

An element's `::before` pseudo-element inserts some content before the element.

```
h1::before {
  content: "";
}
```

The output of the above would be:

![How%20to%20use%203fc9e/hello-world-before.png](How%20to%20use%203fc9e/hello-world-before.png)

### The `::after` pseudo-element

The `::after` pseudo-element is used to insert some content after the content of an element.

```
h1::after{
  content: "";
}
```

Similarly, the output of the above would be:

![How%20to%20use%203fc9e/hello-world-after.png](How%20to%20use%203fc9e/hello-world-after.png)

## What is the difference between pseudo-elements and pseudo-classes?

Pseudo-elements are sometimes confused for pseudo-classes because they look and sound similar, but they are actually not.

In contrast with pseudo-elements, which are used to insert content, pseudo-classes are just selectors that target an element's state, as well as a few other things. A typical example is the `:hover` state pseudo-class selector of an element, which indicates that you want to apply certain CSS rules when the user hovers over it.

It is also worth noting that a pseudo-element is declared with two colons, i.e., `::` while a pseudo-class is declared with a single colon, i.e., `:`.

## Animating with pseudo-elements

Before we can get right down to the project section of the article, we have to get on the same page first. Let's make sure we have a basic understanding of some of the CSS properties that make animating with CSS a possibility:

- `transition`

It is my assumption that you are probably familiar with most of these, if not all of them, but just in case, we'll take a cursory look at them. If you're already familiar with them, feel free to [skip ahead to the tutorial](https://blog.logrocket.com/how-to-use-css-before-after-create-custom-animations-transitions/#creating-animated-button-using-pseudo-element).

### A look at CSS Transform and Transition

We'll be using the CSS `transform` and `transition` properties in our project, so it is important that you have a basic understanding of what they are and how they work.

The [CSS transform property](https://blog.logrocket.com/css-transitions-animating-hamburger-menu-button/) basically allows you to translate (move), rotate, scale, and skew an element.

```
.box-1 {
 transform: translate(100px, 100px);}.box-2 {
 transform: rotate(60deg);}.box-3 {
 transform: scale(2);}.box-4 {
  transform: skew(-30deg);}
```

![How%20to%20use%203fc9e/translate-rotate-scale-skew-demo.png](How%20to%20use%203fc9e/translate-rotate-scale-skew-demo.png)

The transition property allows you to set a time duration for these changes, from one state to another to occur, smoothing the entire animation process.

## Positioning with `relative` and `absolute` properties

There are several CSS properties that help you easily control the flow and position of an element in an HTML document, but for the sake of this article, we'll only be looking at the `relative` and `absolute` position properties.

### Relative position

Setting an element's position to `relative` lets you control the position of the element in relation to its normal document flow. For example, you can move it around and use the location where it would have been by default as a point of reference.

Here's an example:

```
.box-2 {
  position: relative;
  right: 150px;
  top: 0;}
```

![How%20to%20use%203fc9e/relative-position-flow.png](How%20to%20use%203fc9e/relative-position-flow.png)

As you can see, the second box gets moved to the right by 150px from its original position, which also doesn't affect the natural flow of the document as the previous space it occupied is respected by the surrounding elements.

### Absolute position

When setting an element's position to `absolute`, on the other hand, CSS pulls the element from its natural flow (making it overlap other elements) and uses the provided coordinate to try to place this element in a parent container, whose position has been set to `relative`.

When it fails to find any parent, it uses the body of the document as a relative point of reference.

Example:

```
.parent-container {
  position: relative;}.box-1 {
  position: absolute;
  left: 20px;
  top: 20px;}.box-2 {
  position: absolute;
  right: 50px;
  bottom: 40px;}
```

![How%20to%20use%203fc9e/absolute-position-relative-container.png](How%20to%20use%203fc9e/absolute-position-relative-container.png)

As you'd expect, the parent container becomes a relative point of reference for positioning its absolute children using the provided coordinates.

## Controlling the stacking order of elements using `z-index`

The `z-index` property lets us stack elements on top of each other within the stacking context of the page. If an element has a higher stack order, it will always appear before an element with a lower stack order.

Example:

```
.box-1 {
  z-index: 1;}.box-2 {
  z-index: 2;}.box-3 {
  z-index: 3;}.box-4 {
  z-index: 4;}
```

![How%20to%20use%203fc9e/stacking-context-z-index.png](How%20to%20use%203fc9e/stacking-context-z-index.png)

It is also worth noting that the z-index only works on elements that have been positioned using the `position` property. If two elements have the same z-index, the one that appears last in the HTML markup stays on top.

Now that we've covered our basics, let's move on to our starter project.

## Creating an animated button using pseudo-element

For our first project, we'll start by creating a simple animated button to get a feel for using pseudo-elements to animate. Then, we'll move on to the more complicated project.

We'll start by creating an anchor tag in our HTML mockup that we'll later style to a button.

Here's our output:

![How%20to%20use%203fc9e/html-button-output.png](How%20to%20use%203fc9e/html-button-output.png)

Let's jump to our CSS file and style this link to look like a typical button.

```
.btn {
  text-decoration: none;
  border: 2px solid #764abc;
  color: #764abc;
  padding: 10px 20px;
  border-radius: 25px;
    transition: all 1s;
  position: relative;}
```

The code should be self-explanatory — we've removed the default underline decoration, added a solid border of 2px, and made the color of the button the same as the text. We also added padding to put some space between the text and the border and added a border radius to curve the edges of the button.

Lastly, we added a transition duration of `1` second — i.e., any change that occurs to this button should occur smoothly and animate within a second — and set the position to `relative` because we intend to put a pseudo-element inside this button.

Recall that to position a child element with absolute position, the parent container has to be set to `relative`? This button will be the parent container. Below is our output:

![How%20to%20use%203fc9e/button-parent-container.png](How%20to%20use%203fc9e/button-parent-container.png)

Now, we are going to create a pseudo-element of this button.

```
.btn::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #764abc;
  transition: all 1s;}
```

We've created a pseudo-element with an empty `content` property, which ensures nothing is placed inside of it. We set its position to `absolute`, which removes it from its normal flow (making it overlap the button), and then set the coordinates for `top` and `left` to `0`, which pins the empty pseudo-element to the button at those exact locations.

Afterwards, we set the width and height to be exactly 100 percent of the parent, making it the same size as the button itself.

Lastly, we made the pseudo-element's background the same color as the button and added a transition of `1` second once more. Below is the output:

![How%20to%20use%203fc9e/pseudo-element-overlaps-button.png](How%20to%20use%203fc9e/pseudo-element-overlaps-button.png)

As you can see, the pseudo-element is overlapping the button because we've used an absolute position.

To resolve this, we have to use the `z-index` property to change their stacking context by pulling the pseudo-element behind the button using a negative value. Then, we will use the `translate` property to move this pseudo-element to the left by `-100%`.

```
.btn::before {
  /*...previous code */
  z-index: -1;
  transform: translateX(-100%);}
```

Et voilà:

![How%20to%20use%203fc9e/change-stacking-context-pseudo-element-button.png](How%20to%20use%203fc9e/change-stacking-context-pseudo-element-button.png)

Now we will animate this pseudo-element so that it returns to its original position when we hover over the button, using the `:hover` pseudo-class.

```
.btn:hover::before {
  transform: translateX(0);}
```

In the above, we are basically saying that when someone hovers over this button, this pseudo-element should move back to its initial absolute position. Here's our output:

![How%20to%20use%203fc9e/animate-pseudo-element-hover.gif](How%20to%20use%203fc9e/animate-pseudo-element-hover.gif)

However, the text is still hidden because the text and the pseudo-element are both the same color. Let's change the color of the text to display in white when the button is hovered over.

```
.btn:hover {
  color: #fff;}
```

![How%20to%20use%203fc9e/white-text-display-hover.gif](How%20to%20use%203fc9e/white-text-display-hover.gif)

Because we added a `translate` property to the button itself, this change will occur smoothly.

For the last step, we will apply an `overflow: hidden` property to the button to hide any element that overflows from the container. When applied to the button, it will hide the translated pseudo-element and only show it when it moves back to position.

```
.btn {
  /*...previous code. */
  overflow: hidden;}
```

Final output:

![How%20to%20use%203fc9e/final-animated-button.gif](How%20to%20use%203fc9e/final-animated-button.gif)

There you have it! We've successfully created a beautifully animated button using pseudo-elements. You can find the complete source code at the end of this article.

## Creating an advanced animated profile card using multiple pseudo-elements

Now for the main event, we'll create a more complex animated profile card using multiple pseudo-elements — four, to be exact — to create a truly stunning hover effect.

Without further ado, let's get right into the HTML markup.

```
<divclass="profile-card">
      <divclass="info">
        <h2>John Doe</h2>
        <p>Ceo / Founder</p>
      </div></div>
```

We've created a simple card `div` that holds the user's bio (consisting of name and position):

![How%20to%20use%203fc9e/john-doe-div-card.png](How%20to%20use%203fc9e/john-doe-div-card.png)

Let's jump to the CSS file and style this card.

```
.profile-card {
  width: 300px;
  height: 400px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  display: grid;
  place-items: center;
  position: relative;
  background: url("/image.jpg") no-repeat center center/cover;}
```

We've created a fixed width/height card, placed the content inside at the center using CSS Grid, and added a box shadow to give the edges a bit of shadow so it looks more realistic. Lastly, we set the card as `relative` to make it a parent container for the pseudo-elements and added a centered background image. Let's see our output:

![How%20to%20use%203fc9e/css-grid-card-box-shadow.png](How%20to%20use%203fc9e/css-grid-card-box-shadow.png)

With that out of the way, let's get on with creating the pseudo-elements.

This is the tricky part. We intend to use four pseudo-elements, but an element can only have one `::before` and one `::after` pseudo-element, respectively. To get around this, we'll be using the card itself to create two pseudo-elements, and then use the `info div` inside the card to create another two.

Let's begin with the `info div`.

```
.info::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: #764abc;
  transform: skew(30deg) translateX(100%);
  opacity: 0.3;
  z-index: -1;
  transition: all 0.6s ease;}
```

Now, because the `info div` itself has no fixed width or height, the pseudo-element takes the full width and height of the parent card, making it the same size as the card.

We then skew it by `30deg`, which slants and then translates it by 100 percent. This moves it to the right. The negative index ensures it stays behind the text, while the opacity makes it semi-transparent.

![How%20to%20use%203fc9e/card-with-two-pseudo-elements.png](How%20to%20use%203fc9e/card-with-two-pseudo-elements.png)

Moving on to the second pseudo-element:

```
.info::after {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: #764abc;
  transform: skew(-30deg) translate(90%);
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.7);
  opacity: 0.3;
  z-index: -1;
  transition: all 0.6s ease;}
```

We've done basically the same thing as the `::before` pseudo-element, but then switched the `skew` direction to the opposite direction, and added a box shadow so shadows are added to the sides, making it more 3D-like.

![How%20to%20use%203fc9e/duplicate-inverse-box-shadow.png](How%20to%20use%203fc9e/duplicate-inverse-box-shadow.png)

Now, we'll make it so that whenever this card is hovered over, the pseudo-elements move further into the card. You can rest assured this will happen smoothly because we added a `transition` to the pseudo-elements.

```
.profile-card:hover .info::before {
  transform: skew(30deg) translateX(50%);}.profile-card:hover .info::after {
  transform: skew(-30deg) translateX(40%);
  opacity: 0.7;}
```

Output:

![How%20to%20use%203fc9e/pseudo-element-animation.gif](How%20to%20use%203fc9e/pseudo-element-animation.gif)

Now let's create two more pseudo-elements using the card itself.

```
.profile-card::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: #764abc;
  opacity: 0.3;
  transform: skew(30deg) translate(100%);
  transition: all 0.6s ease;
  z-index: -1;}
```

This code should be self-explanatory by this point; we've simply done the same thing as above, but this time we've only translated the card's own `::before` pseudo-element to the right by 85 percent. Take a look:

![How%20to%20use%203fc9e/add-before-pseudo-element-85-percent.png](How%20to%20use%203fc9e/add-before-pseudo-element-85-percent.png)

Next, we'll create the last pseudo-element and skew it in the opposite direction from the `::before`.

```
.profile-card::after {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: #764abc;
  opacity: 0.3;
  transform: skew(-30deg) translate(85%);
  transition: all 0.6s ease;
  z-index: -1;}
```

![How%20to%20use%203fc9e/four-pseudo-elements-added.png](How%20to%20use%203fc9e/four-pseudo-elements-added.png)

As you would have guessed, we'll also make it so when this profile card is hovered, these newly created pseudo-elements move in, like the previous two. But this time around, we'll move them even further than the previous two.

```
.profile-card:hover:before {
  transform: skew(30deg) translateX(30%);}.profile-card:hover:after {
  transform: skew(-30deg) translateX(20%);}
```

Output:

![How%20to%20use%203fc9e/animate-all-four-pseudo-elements.gif](How%20to%20use%203fc9e/animate-all-four-pseudo-elements.gif)

As you can see, our profile card is coming together. Now for the last piece of the puzzle, we will set the `overflow` property of this card to `hidden` so as to hide the overflowing parts.

```
.profile-card {
 /*...previous code. */
  overflow: hidden;}
```

Output:

![How%20to%20use%203fc9e/add-overflow-property.gif](How%20to%20use%203fc9e/add-overflow-property.gif)

Lastly, we will change the text color to white and make it so the opacity is fully transparent — but, when the card is hovered over, we'll change the opacity back to normal, making them visible.

```
.info h2, .info p {
  color: #fff;
  opacity: 0;
  transition: all 0.6s;}.profile-card:hover .info h2,.profile-card:hover .info p {
  opacity: 1;}
```

Final result:

![How%20to%20use%203fc9e/change-text-white.gif](How%20to%20use%203fc9e/change-text-white.gif)

### **Source code (CodePen)**

## Conclusion

Congrats on making it to the end. As you have seen, the `::before` and `::after` pseudo-elements can be used in several different ways to produce interesting animated effects that give life to our designs.

You can explore these further to create even more complex designs and animations, as there's so much more that can be done using the `::before` and `::after` CSS pseudo-elements, and we have only just scratched the surface.

## Is your frontend hogging your users' CPU?

As web frontends get increasingly complex, resource-greedy features demand more and more from the browser. If you're interested in monitoring and tracking client-side CPU usage, memory usage, and more for all of your users in production, [try LogRocket](https://logrocket.com/signup/).

[https://logrocket.com/signup/](https://logrocket.com/signup/)

![How%20to%20use%203fc9e/cpu-memory-usage.png](How%20to%20use%203fc9e/cpu-memory-usage.png)

[LogRocket](https://logrocket.com/signup/) is like a DVR for web and mobile apps, recording everything that happens in your web app or site. Instead of guessing why problems happen, you can aggregate and report on key frontend performance metrics, replay user sessions along with application state, log network requests, and automatically surface all errors.

Modernize how you debug web apps — [Start monitoring for free](https://logrocket.com/signup/).
