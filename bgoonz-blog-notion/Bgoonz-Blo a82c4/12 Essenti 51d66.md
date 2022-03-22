# 12 Essential Responsive Design Tools - SitePoint

[https://www.sitepoint.com/12-essential-responsive-design-tools/](https://www.sitepoint.com/12-essential-responsive-design-tools/)

Translating client requirements to a full fledged, live website is no easy task. At the best of times, it requires multiple rounds of discussions between clients, designers, and developers, resulting in multiple iterations of the design, and the website itself. Throw in the whole responsive concept – having your design adapt to all kinds of mobile devices – and it can get a bit much to handle.

Fortunately, designers and developers are an innovative, caring, and sharing lot. We like to ease each other's pain. Along with the growing need for responsive websites, there's been a parallel growth of tools to help make responsive web design and development just a little bit easier. I've sorted through some of the tools available and put together this list to help through the phases of the responsive design and development process. Note that this is by no means an exhaustive list, so if you have another tool to share, be sure to post a comment.

## Mock-ups, Prototyping and Wireframing Tools

Let's start with the basics. The design usually starts with a sketch, a wireframe, or a mock-up. The key element here is to get the layouts properly aligned for a variety of mobile devices. Here are some tools to help with that.

### 1. InterfaceSketch

![12%20Essenti%2051d66/1414610233InterfaceSketch.png](12%20Essenti%2051d66/1414610233InterfaceSketch.png)

I'm old fashioned and still prefer paper and ink for basic sketches. And I love that InterfaceSketch gives designers a bunch of simple (and free) PDF templates designed to match the screen of various mobile devices. You can print out these PDFs and use them to sketch out initial designs with the best design tool ever – a good old pencil. Though it's basic, it's a great way to visualize how you'd want things to be.

![12%20Essenti%2051d66/1414610247StyleTiles.jpg](12%20Essenti%2051d66/1414610247StyleTiles.jpg)

No one likes getting caught up in creating multiple mock-ups and wireframes for clients. [StyleTiles](http://styletil.es/) eases part of that pain by enabling web designers to borrow design concepts from interior design. StyleTiles are akin to the swatches of fabric and paint tiles interior designers use. Instead of creating full mock-ups, you can instead use StyleTile swatches to help define the visual language for clients and take them through iterations easily. This is perfect for responsive designs, since there's no fixed dimensions or layouts defined, but instead it's all about the visual appeal. Once that's frozen with the clients, it becomes that much easier for the designer to proceed to the wireframe or real mock-up.

![12%20Essenti%2051d66/1414610245ResponsiveWireframes.jpg](12%20Essenti%2051d66/1414610245ResponsiveWireframes.jpg)

Now that we've got the first sketches and the visual language, time to move on to the wireframes. Traditionally wireframes have been a static representation how the website will eventually look. But what about responsive sites? You don't want to create separate wireframes for multiple screen sizes. [James Miller has a work-workaround](http://www.thismanslife.co.uk/projects/lab/responsivewireframes/#desktop). He's adapted the most typical layouts and created responsive wireframes for them. This saves you the headache of creating them from scratch and lets you easily see which areas of your layout will draw the user's focus on different devices.

![12%20Essenti%2051d66/1414610248Wirefy.png](12%20Essenti%2051d66/1414610248Wirefy.png)

For those looking to create their own wireframe, [Wirefy](http://getwirefy.com/) is a great option. It has a very simple workflow with an extensive collection of atomic components that can be moved around easily. It enables designers to build functional wireframes with fluid designs that help keep the focus on the actual content.

## Generating Responsive HTML and CSS

After the mock-ups and the wireframes, it will be time to get down to the code. Writing out the CSS with multiple breakpoints and media queries isn't exactly the most enjoyable part of coding. The following tools take the drudgery out of it and help generate responsive code. While purists may not like them, in my humble opinion, they're a good way to get started and avoid re-inventing the wheel.

### 5. [Pure CSS](http://purecss.io/)

[PureCSS](http://purecss.io/) is a small set of CSS modules especially designed for mobile devices. It boasts a really tiny footprint (total 4.4KB, minified and gzipped), which drops off further if you use only a subset of the modules. You can create a responsive layout using the Grid and Menu modules. There are also separate modules for other typical CSS elements such as buttons, tables, and forms.

![12%20Essenti%2051d66/1414610243ResponsiveCSS.png](12%20Essenti%2051d66/1414610243ResponsiveCSS.png)

[Responsive Web CSS](https://www.entomic.com/responsivecss) takes a slightly different approach. It lets you create a layout by adding `div` elements for each section of the page and then setting the size of each `div` depending on how you want it to appear across different devices. Once you have all the elements and sizes in place, you can download a skeleton HTML+CSS for your site.

### 7. [Macaw](http://macaw.co/)

![12%20Essenti%2051d66/1414610237Macaw.jpg](12%20Essenti%2051d66/1414610237Macaw.jpg)

[Macaw](http://macaw.co/) truly empowers designers to create websites without any help. Positioned as a web design tool rather than a web development tool, the tagline says it all "Stop writing code, start drawing it." Macaw is a native application that you need to download and install, rather than an in-browser tool. Macaw gives users the flexibility of an image editor, the ability to drag and drop elements, create layouts, set typography, define global styles, and more – all with their real-time, fluid layout engine called Stream. The design-to-code engine, called Alchemy, converts these designs into semantically correct HTML and succinct CSS. Tall order for anyone! Make use of the free trial and give it a spin.

## Fonts, Images, and Videos

Once we have the basic code in place, we'll need to get to the finer details – the fonts, images, videos, etc. jQuery plugins can help do most of the heavy lifting here. Let's take a look.

![12%20Essenti%2051d66/1414610231FlowType.png](12%20Essenti%2051d66/1414610231FlowType.png)

Though text is often the most ignored part of responsive design, [you need to pay attention to it](https://www.sitepoint.com/thought-responsive-text-just-fad/). [FlowType](http://simplefocus.com/flowtype/) is a neat jQuery plugin that changes the font size based on a specific element's width to achieve the optimal character count, which is between 45-75 characters per line. No more guessing what *em* size you need to set the font to for a 4-inch screen versus a 6-inch screen. There are also other options to set the font and element size thresholds and ratios.

On smaller, lower bandwidth devices, loading desktop-centric images on your site will increase your page load times and consume the user's bandwidth. [Adaptive Images](http://adaptive-images.com/) incorporates the principles of fluid images so you don't have to hard code changes in your markup. It checks the visitor's screen size and accordingly creates and delivers a scaled version of the images embedded in your web page.

### 10. [FitVids.js](http://fitvidsjs.com/)

After images, it's time to make videos responsive. Unless you really know your way around responsive coding, you may want to just skip over to [FitVids.js](http://fitvidsjs.com/). It's a lightweight jQuery plugin that adjusts the size of embedded videos to match the screen size, while maintaining the right aspect ratio.

## Responsive Design Testing Tools

The tools listed above were to help you design and develop your responsive website. But of course, you can't launch your site without testing it. And if you're like the rest of us, you really don't have 10 different device layouts on hand to test in. Instead of fretting about how to test on multiple devices, you can use these neat simulators.

Of course, these kinds of testing tools are never the same as actual device testing, but they can serve as a replacement if actual device testing is not an option for you.

### 11. [DesignModo's Responsive Test](http://designmodo.com/responsive-test/)

DesignModo has perhaps [one of the best responsive testers available](http://designmodo.com/responsive-test/). Just feed in the site URL and the dimension you want to test it on, or alternatively, select the specific device you want to test it on. The tool supports a wide range of smartphones, tablets, and desktops, including Macs. If you need help deciding breakpoints, you can just drag the window separator around to see how the layout changes at different widths.

[Brad Frost's tool](http://bradfrost.com/demo/ish/) is another nice one you might want to consider. It lets you set the window width in px or em or you can drag the window resizer bar. There are also a number of size presets including something called "Hay" mode, which automatically starts the tool at a small size and slowly increases, allowing you to see exactly where your "break" points occur.

There are other responsive design testing tools, like the [Responsive Test](http://www.studiopress.com/responsive/) by Matt Kersley and [the Responsinator](http://www.responsinator.com/). The main differences being the range of preset device or size options they provide. Just play around with them a bit and see which one works best for you.

## Any Other Recommendations?

I hope this list of tools helps make your responsive design process a tad bit easier. Like I said earlier, there are other tools available (and a whole bunch of responsive grids and frameworks) that you could use as well. You'll need to experiment a bit to figure out which one best suits your requirements. Have you tried any of the tools above? Do share your experiences with us in the comments below. Or is your favourite tool not on this list? We'd love to know about it – just leave a comment below.
