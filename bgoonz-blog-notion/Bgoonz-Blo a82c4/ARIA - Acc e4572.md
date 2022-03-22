# ARIA - Accessibility | MDN

[https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA)

![mdn-social-share.0ca9dbda.png](ARIA%20-%20Acc%20e4572/mdn-social-share.0ca9dbda.png)

Accessible Rich Internet Applications **(ARIA)** is a set of attributes that define ways to make web content and web applications (especially those developed with JavaScript) more accessible to people with disabilities.

It supplements HTML so that interactions and widgets commonly used in applications can be passed to assistive technologies when there is not otherwise a mechanism. For example, ARIA enables accessible navigation landmarks in HTML4, JavaScript widgets, form hints and error messages, live content updates, and more.

[Keyboard-navigable JavaScript widgets - Accessibility | MDN](https://developer.mozilla.org/en-US/docs/Web/Accessibility/Keyboard-navigable_JavaScript_widgets)

**Warning:** Many of these widgets were later incorporated into HTML5, and **developers should prefer using the correct semantic HTML element over using ARIA**, if such an element exists. For instance, native elements have built-in [keyboard accessibility](https://developer.mozilla.org/en-US/docs/Web/Accessibility/Keyboard-navigable_JavaScript_widgets), roles and states. However, if you choose to use ARIA, you are responsible for mimicking (the equivalent) browser behavior in script.

Here's the markup for a progress bar widget:

```
<div id="percent-loaded" role="progressbar" aria-valuenow="75"
     aria-valuemin="0" aria-valuemax="100">
</div>

```

This progress bar is built using a `[<div>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/div)`, which has no meaning. Unfortunately, there isn't a more semantic tag available to developers in HTML 4, so we need to include ARIA roles and properties. These are specified by adding attributes to the element. In this example, the `role="progressbar"` attribute informs the browser that this element is actually a JavaScript-powered progress bar widget. The `aria-valuemin` and `aria-valuemax` attributes specify the minimum and maximum values for the progress bar, and the `aria-valuenow` describes the current state of it and therefore must be kept updated with JavaScript.

Along with placing them directly in the markup, ARIA attributes can be added to the element and updated dynamically using JavaScript code like this:

```
// Find the progress bar <div> in the DOM.
var progressBar = document.getElementById("percent-loaded");

// Set its ARIA roles and states,
// so that assistive technologies know what kind of widget it is.
progressBar.setAttribute("role", "progressbar");
progressBar.setAttribute("aria-valuemin", 0);
progressBar.setAttribute("aria-valuemax", 100);

// Create a function that can be called at any time to update
// the value of the progress bar.
function updateProgress(percentComplete) {
  progressBar.setAttribute("aria-valuenow", percentComplete);
}

```

**Note:** ARIA was invented after HTML4, so does not validate in HTML4 or its XHTML variants. However, the accessibility gains it provides far outweigh any technical invalidity. In HTML5, all ARIA attributes validate. The new landmark elements (`[<main>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/main)`, `[<header>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/header)`, `[<nav>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/nav)` etc.) have built-in ARIA roles, so there is no need to duplicate them.

Like any other web technology, there are varying degrees of support for ARIA. Support is based on the operating system and browser being used, as well as the kind of assistive technology interfacing with it. In addition, the version of the operating system, browser, and assistive technology are contributing factors. Older software versions may not support certain ARIA roles, have only partial support, or misreport its functionality.

It is also important to acknowledge that some people who rely on assistive technology are reluctant to upgrade their software, for fear of losing the ability to interact with their computer and browser. Because of this, it is important to [use semantic HTML elements](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/HTML) whenever possible, as semantic HTML has far better support for assistive technology.

It is also important to test your authored ARIA with actual assistive technology. Much as how browser emulators and simulators are not an effective solution for testing full support, proxy assistive technology solutions aren't sufficient to fully guarantee functionality.

 A quick introduction to making dynamic content accessible with ARIA. See also the classic [ARIA intro by Gez Lemon](https://dev.opera.com/articles/view/introduction-to-wai-aria/), from 2008.    See both real and simplified examples from around the web, including "before" and "after" ARIA videos.    A practical guide for developers. It suggests what ARIA attributes to use on HTML elements. Suggestions are based on implementation realities.