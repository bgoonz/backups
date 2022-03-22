# Thinking in Atomic Design | Stackbit Documentation - V2 Beta

[https://docs.stackbit.com/conceptual-guides/components/atomic-design/](https://docs.stackbit.com/conceptual-guides/components/atomic-design/)

Each of our theme may differ a bit in the components it provides, to fit the use case and the look & feel of that specific theme. However, the guiding principle for organizing components in each of our themes is [Atomic Design](https://bradfrost.com/blog/post/atomic-web-design/).

Atomic design is a systematic approach to composing page layouts using multiple levels: from the full page layout all the way down to the smallest basic elements of functionality (e.g. a button, a link, a single image). Getting to know this approach is beneficial even if you plan on building your own component library.

Here is how we break down a typical homepage into four types of components.

[Homepage composition](https://docs.stackbit.com/static/231979121c3edab38a0127b6649df75e/33c15/atomic-homepage.png)

![Thinking%20i%207ae31/atomic-homepage.png](Thinking%20i%207ae31/atomic-homepage.png)

Layout components are responsible for building out the high-level structure of the full page. They determine which types of components can appear on the page, and where. In atomic design this type of element is known as a *template*.

A layout component accepts the content object for a single full page, and only renders the top-level elements of the page by itself. Wherever a component's data is found in the content, it delegates the rendering to the appropriate component.

Many webpages, if you examine them closely, are mostly made of horizontal building blocks - which we call **sections**.

These sections are vertically stacked over each other, and usually take up the full width of the page. Each section has a distinct look and internal structure, and may have a complex hierarchy of data and actions within it. Each section component has its own set of properties, which are defined by its accompanying [model](https://docs.stackbit.com/conceptual-guides/modeling-storing-content/).

Here are some typical, easily recognizable section types: a Hero Banner, a row of recommended products, a row of customer logos or featured blog posts, or a "subscribe" element.

In Atomic Design parlance, these components are called *organisms*. Like layout components, much of their actual rendering work is typically delegated to other, lower-level components.

Blocks are components suitable for embedding and reuse in multiple types of sections, and they can often be interchangeable within a parent component.

For example, the *Hero Section* component you'll find in our themes can typically accept a single block as its featured item: either an image block (which supports capabilities such as a semi-transparent text overlay), a video player, or a mini-form.

Additional block types can be developed and used as a featured item without having to modify the Hero Section's code - as long as they play well within the space allocated to them within the section.

These same blocks are also used by other section types where relevant - and you could develop new section components which use these existing blocks within them.

These are the equivalent of *atoms* in Atomic Design: they provide a basic piece of functionality, such as a single button or link, and do not accept any other component within them.

**Next up:** [Designing nested components effectively](https://docs.stackbit.com/conceptual-guides/components/nesting/).