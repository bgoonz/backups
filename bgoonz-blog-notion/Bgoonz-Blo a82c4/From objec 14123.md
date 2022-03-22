# From object to iframe — other embedding technologies - Learn web development | MDN

[https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies)

![mdn-social-share.0ca9dbda.png](From%20objec%2014123/mdn-social-share.0ca9dbda.png)

By now you should really be getting the hang of embedding things into your web pages, including images, video and audio. At this point we'd like to take somewhat of a sideways step, looking at some elements that allow you to embed a wide variety of content types into your webpages: the `[<iframe>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)`, `[<embed>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed)` and `[<object>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object)` elements. `<iframe>`s are for embedding other web pages, and the other two allow you to embed PDFs, SVG, and even Flash — a technology that is on the way out, but which you'll still see semi-regularly.

Basic computer literacy, , basic knowledge of , familiarity with HTML fundamentals (as covered in ) and the previous articles in this module.

---

To learn how to embed items into web pages using , , and , like PDF documents and other webpages.

---

A long time ago on the Web, it was popular to use **frames** to create websites — small parts of a website stored in individual HTML pages. These were embedded in a master document called a **frameset**, which allowed you to specify the area on the screen that each frame filled, rather like sizing the columns and rows of a table. These were considered the height of coolness in the mid to late 90s, and there was evidence that having a webpage split up into smaller chunks like this was better for download speeds — especially noticeable with network connections being so slow back then. They did however have many problems, which far outweighed any positives as network speeds got faster, so you don't see them being used anymore.

A little while later (late 90s, early 2000s), plugin technologies became very popular, such as [Java Applets](https://developer.mozilla.org/en-US/docs/Glossary/Java) and [Flash](https://developer.mozilla.org/en-US/docs/Glossary/Adobe_Flash) — these allowed web developers to embed rich content into webpages such as videos and animations, which just weren't available through HTML alone. Embedding these technologies was achieved through elements like `[<object>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object)`, and the lesser-used `[<embed>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed)`, and they were very useful at the time. They have since fallen out of fashion due to many problems, including accessibility, security, file size, and more. These days major browsers have stopped supporting plugins such as Flash.

Finally, the `[<iframe>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)` element appeared (along with other ways of embedding content, such as `[<canvas>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/canvas)`, `[<video>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)`, etc.) This provides a way to embed an entire web document inside another one, as if it were an `[<img>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img)` or other such element, and is used regularly today.

With the history lesson out of the way, let's move on and see how to use some of these.

In this article we are going to jump straight into an active learning section, to immediately give you a real idea of just what embedding technologies are useful for. The online world is very familiar with [YouTube](https://www.youtube.com/), but many people don't know about some of the sharing facilities it has available. Let's look at how YouTube allows us to embed a video in any page we like using an `[<iframe>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)`.

1. First, go to YouTube and find a video you like.
2. Below the video, you'll find a *Share* button — select this to display the sharing options.
3. Select the *Embed* button and you'll be given some `<iframe>` code — copy this.
4. Insert it into the *Input* box below, and see what the result is in the *Output*.

For bonus points, you could also try embedding a [Google Map](https://www.google.com/maps/) in the example:

1. Go to Google Maps and find a map you like.
2. Click on the "Hamburger Menu" (three horizontal lines) in the top left of the UI.
3. Select the *Share or embed map* option.
4. Select the Embed map option, which will give you some `<iframe>` code — copy this.
5. Insert it into the *Input* box below, and see what the result is in the *Output*.

If you make a mistake, you can always reset it using the *Reset* button. If you get really stuck, press the *Show solution* button to see an answer.

## Editable code

Press Esc to move focus away from the code area (Tab inserts a tab character).

So, that was easy and fun, right? `[<iframe>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)` elements are designed to allow you to embed other web documents into the current document. This is great for incorporating third-party content into your website that you might not have direct control over and don't want to have to implement your own version of — such as video from online video providers, commenting systems like [Disqus](https://disqus.com/), maps from online map providers, advertising banners, etc. The live editable examples you've been using through this course are implemented using `<iframe>`s.

There are some serious [Security concerns](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies#security_concerns) to consider with `<iframe>`s, as we'll discuss below, but this doesn't mean that you shouldn't use them in your websites — it just requires some knowledge and careful thinking. Let's explore the code in a bit more detail. Say you wanted to include the MDN glossary on one of your web pages — you could try something like this:

```
<head>
  <style> iframe { border: none } </style>
</head>
<body>
  <iframe src="https://developer.mozilla.org/en-US/docs/Glossary"
          width="100%" height="500" allowfullscreen sandbox>
    <p>
      <a href="/en-US/docs/Glossary">
         Fallback link for browsers that don't support iframes
      </a>
    </p>
  </iframe>
</body>

```

This example includes the basic essentials needed to use an `<iframe>`:

 If used, the `<iframe>` is displayed without a surrounding border. Otherwise, by default, browsers display the `<iframe>` with a surrounding border (which is generally undesirable).    If set, the `<iframe>` is able to be placed in fullscreen mode using the [Fullscreen API](https://developer.mozilla.org/en-US/docs/Web/API/Fullscreen_API) (somewhat beyond the scope of this article.)    This attribute, as with `[<video>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)`/`[<img>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img)`, contains a path pointing to the URL of the document to be embedded.    These attributes specify the width and height you want the iframe to be.  Fallback content  In the same way as other similar elements like `[<video>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)`, you can include fallback content between the opening and closing `<iframe></iframe>` tags that will appear if the browser doesn't support the `<iframe>`. In this case, we have included a link to the page instead. It is unlikely that you'll come across any browser that doesn't support `<iframe>`s these days.    This attribute, which works in slightly more modern browsers than the rest of the `<iframe>` features (e.g. IE 10 and above) requests heightened security settings; we'll say more about this in the next section. 

**Note:** In order to improve speed, it's a good idea to set the iframe's `src` attribute with JavaScript after the main content is done with loading. This makes your page usable sooner and decreases your official page load time (an important [SEO](https://developer.mozilla.org/en-US/docs/Glossary/SEO) metric.)

## [Summary](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies#summary)