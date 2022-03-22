# Generate RSS feeds for your static Next.js blog | Phiilu | Florian Kapfenberger

[https://phiilu.com/generate-rss-feeds-for-your-static-next-js-blog](https://phiilu.com/generate-rss-feeds-for-your-static-next-js-blog)

![989c9e1db48d1ac7b8c2b4d970ecc337.png](Generate%20R%209d20e/989c9e1db48d1ac7b8c2b4d970ecc337.png)

On the internet, there are many ways to allow visitors to get updated for new content on your blog. A pretty common option is to offer a **Really Simple Syndication** or more commonly known as **RSS** feed.

An [RSS](https://en.wikipedia.org/wiki/RSS) feed is a standardized XML file that contains information about the website and about all articles. Many people like to use RSS readers like [Feedly](https://feedly.com/) or [Feeder](https://feeder.co/) to read blog posts, so it's a good idea to offer it!

Next to RSS there also exists the [Atom](https://en.wikipedia.org/wiki/Atom_(Web_standard)) and [JSON feed](https://jsonfeed.org/). Atom should be the successor of RSS and has some improvements over RSS. JSON feed is basically RSS, but instead of using XML, it uses JSON.

In this tutorial, I will show you how to generate all 3 feeds in Javascript with the help of the `[feed](https://github.com/jpmonette/feed)` package and add them to your static Next.js site. You can see the final results of the different feeds by clicking the link:

## Generating RSS feeds

Inside the Next.js project create a new file where you want to put all the logic for generating RSS feeds. I created my file inside a `lib` folder and named it `rss.js`.

Next, add the `feed` package from npm to your project.

```
yarn add feed
```

Before writing any code, let's think about what we want to do. There are 3 steps we need to do:

- create a new Feed instance and initialize it with common data about the blog
- loop over all articles and add them to the feed
- generate the web feeds that you want and store them in files

Sounds not too complicated so let's get started.

### Creating a new Feed instance

Inside the `rss.js` file create a new function and name it something like `generateRssFeed`.

Next, we want to initialize the Feed instance.

```
const baseUrl = "https://phiilu.com";const date = new Date();const feed = new Feed({  title: `Phiilu's Blog`,  description: "Welcome to my blog!",  id: baseUrl,  link: baseUrl,  language: "en",  image: `${baseUrl}/images/logo.svg`,  favicon: `${baseUrl}/favicon.ico`,  copyright: `All rights reserved ${date.getFullYear()}, Florian Kapfenberger`,  updated: date,  generator: "Next.js using Feed for Node.js",  feedLinks: {    rss2: `${baseUrl}/rss/feed.xml`,    json: `${baseUrl}/rss/feed.json`,    atom: `${baseUrl}/rss/atom.xml`,},});
```

This is meta-information about your blog. You can define the `title`, `description`, `image`, `favicon`, and other data that will be used inside RSS readers.

### Add articles to the feed

Now you need to gather all articles from your blog and add them to the feed.

I am using [Contentful](https://www.contentful.com/) as my headless CMS, so I am fetching the data using the Contentful API.

> 
> 
> 
> If you are using MDX you probably need to read the files from your disk and extract the frontmatter data.
> 

```
const author = {  name: "Florian Kapfenberger",  email: "hey@phiilu.com",  link: "https://twitter.com/phiilu",const posts = await contentful.getEntries("post", {  order: "-fields.publishedDate",});posts.forEach((post) => {const url = `${baseUrl}/${post.slug}`;  feed.addItem({    title: post.title,    id: url,    link: url,    description: post.description,    content: markdown.toHTML(post.content),    author: [author],    contributor: [author],    date: new Date(post.rawDate),});});
```

Here I am fetching my articles using the Contentful API and adding them to the `Feed` instance. My articles are written in Markdown, but RSS feeds expect them to be in HTML. This is why I am using the `markdown` package to transform my Markdown into HTML for the `content` property.

### Generate the different feed files

Next.js will serve files from the `public` folder, so this is the location where we want to store the different feeds.

```
fs.mkdirSync("./public/rss", { recursive: true });fs.writeFileSync("./public/rss/feed.xml", feed.rss2());fs.writeFileSync("./public/rss/atom.xml", feed.atom1());fs.writeFileSync("./public/rss/feed.json", feed.json1());
```

Thanks to `feed` we can generate all three formats by just calling the correct function!

### Steps summary

After these 3 steps, your `rss.js` file should look similar to this one.

```
const Feed = require('feed').Feed;const contentful = require('./contentful').default;const markdown = require('markdown').markdown;const fs = require('fs');async function generateRssFeed() {if (process.env.NODE_ENV === 'development') {return;const baseUrl = process.env.BASE_URL;const date = new Date();const author = {    name: 'Florian Kapfenberger',    email: 'hey@phiilu.com',    link: 'https://twitter.com/phiilu'};const feed = new Feed({    title: `Phiilu's Blog`,    description: 'Welcome to my blog!',    id: baseUrl,    link: baseUrl,    language: 'en',    image: `${baseUrl}/images/logo.svg`,    favicon: `${baseUrl}/favicon.ico`,    copyright: `All rights reserved ${date.getFullYear()}, Florian Kapfenberger`,    updated: date,    generator: 'Next.js using Feed for Node.js',    feedLinks: {      rss2: `${baseUrl}/rss/feed.xml`,      json: `${baseUrl}/rss/feed.json`,      atom: `${baseUrl}/rss/atom.xml`},});const posts = await contentful.getEntries('post', { order: '-fields.publishedDate' });  posts.forEach((post) => {const url = `${baseUrl}/${post.slug}`;    feed.addItem({      title: post.title,      id: url,      link: url,      description: post.description,      content: markdown.toHTML(post.content),      author: [author],      contributor: [author],      date: new Date(post.rawDate)});});  fs.mkdirSync('./public/rss', { recursive: true });  fs.writeFileSync('./public/rss/feed.xml', feed.rss2());  fs.writeFileSync('./public/rss/atom.xml', feed.atom1());  fs.writeFileSync('./public/rss/feed.json', feed.json1());export default generateRssFeed;
```

## Generate RSS feeds during the build

Now that we have our little utility function to generate the RSS feeds, we need to define when the RSS feeds should get generated.

To keep it simple I am importing this function in the `pages/index.js` file and adding it to the `getStaticProps`. Doing it this way will make sure Next.js will call this function during the build of the `pages/index.js` page and generate the feeds.

```
export async function getStaticProps() {await generateRssFeed();return {    props: { posts, ogImage, baseUrl },};
```

The cleaner way probably is to call this function somewhere in the webpack config by using a plugin or something like this.

## Conclusion

There is a whole market out there for RSS readers and offering RSS for your readers can be very valuable to grow your audience.

Thanks to the `feed` package it is very easy to generate RSS feeds with Javascript too.

What do you think about RSS? Do you offer RSS on your blog? Are you using RSS readers and if so which one do you use? I am very interested in what you think, lets chat in the comments below!

## Want blog post updates? Sign up for my newsletter.

**Did you find this post useful or learned something?**
I would be really grateful if you let me [@phiilu](https://twitter.com/phiilu) know by sharing it on Twitter!