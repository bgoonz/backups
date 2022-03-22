# Avoid an excessive DOM size

[https://web.dev/dom-size/](https://web.dev/dom-size/)

A large DOM tree can slow down your page performance in multiple ways:

- **Network efficiency and load performance**
    
    A large DOM tree often includes many nodes that aren't visible when the user first loads the page, which unnecessarily increases data costs for your users and slows down load time.
    
- **Runtime performance**
    
    As users and scripts interact with your page, the browser must constantly [recompute the position and styling of nodes](https://developers.google.com/web/fundamentals/performance/rendering/reduce-the-scope-and-complexity-of-style-calculations?utm_source=lighthouse&utm_medium=cli). A large DOM tree in combination with complicated style rules can severely slow down rendering.
    
- **Memory performance**
    
    If your JavaScript uses general query selectors such as `document.querySelectorAll('li')`, you may be unknowingly storing references to a very large number of nodes, which can overwhelm the memory capabilities of your users' devices.
    

## How the Lighthouse DOM size audit fails [#](https://web.dev/dom-size/#how-the-lighthouse-dom-size-audit-fails)

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) reports the total DOM elements for a page, the page's maximum DOM depth, and its maximum child elements:

![Avoid%20an%20e%203e182/SUCUejhAE77m6k2WyI6D.png](Avoid%20an%20e%203e182/SUCUejhAE77m6k2WyI6D.png)

Lighthouse flags pages with DOM trees that:

- Warns when the body element has more than ~800 nodes.
- Errors when the body element has more than ~1,400 nodes.

See the [Lighthouse performance scoring](https://web.dev/performance-scoring) post to learn how your page's overall performance score is calculated.

## How to optimize the DOM size [#](https://web.dev/dom-size/#how-to-optimize-the-dom-size)

In general, look for ways to create DOM nodes only when needed, and destroy nodes when they're no longer needed.

If you're currently shipping a large DOM tree, try loading your page and manually noting which nodes are displayed. Perhaps you can remove the undisplayed nodes from the initially loaded document and only create them after a relevant user interaction, such as a scroll or a button click.

If you create DOM nodes at runtime, [Subtree Modification DOM Change Breakpoints](https://developers.google.com/web/tools/chrome-devtools/javascript/breakpoints#dom) can help you pinpoint when nodes get created.

If you can't avoid a large DOM tree, another approach for improving rendering performance is simplifying your CSS selectors. See Google's [Reduce the Scope and Complexity of Style Calculations](https://developers.google.com/web/fundamentals/performance/rendering/reduce-the-scope-and-complexity-of-style-calculations) for more information.

## Stack-specific guidance [#](https://web.dev/dom-size/#stack-specific-guidance)

If you're rendering large lists, use [virtual scrolling](https://web.dev/virtualize-lists-with-angular-cdk/) with the Component Dev Kit (CDK).

- Use a "windowing" library like `[react-window](https://web.dev/virtualize-long-lists-react-window/)` to minimize the number of DOM nodes created if you are rendering many repeated elements on the page.
- Minimize unnecessary re-renders using `[shouldComponentUpdate](https://reactjs.org/docs/optimizing-performance.html#shouldcomponentupdate-in-action)`, `[PureComponent](https://reactjs.org/docs/react-api.html#reactpurecomponent)`, or `[React.memo](https://reactjs.org/docs/react-api.html#reactmemo)`.
- [Skip effects](https://reactjs.org/docs/hooks-effect.html#tip-optimizing-performance-by-skipping-effects) only until certain dependencies have changed if you are using the `Effect` hook to improve runtime performance.

## Resources [#](https://web.dev/dom-size/#resources)

- [Source code for **Avoid an excessive DOM size** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/dobetterweb/dom-size.js)
- [Reduce the Scope and Complexity of Style Calculations](https://developers.google.com/web/fundamentals/performance/rendering/reduce-the-scope-and-complexity-of-style-calculations)