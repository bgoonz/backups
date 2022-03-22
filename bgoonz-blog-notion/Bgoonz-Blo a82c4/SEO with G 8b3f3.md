# SEO with Gatsby | Gatsby

[https://www.gatsbyjs.com/docs/how-to/adding-common-features/seo/](https://www.gatsbyjs.com/docs/how-to/adding-common-features/seo/)

![gatsby.jpg](SEO%20with%20G%208b3f3/gatsby.jpg)

Gatsby can help your site rank and perform better in search engines. Using Gatsby makes your site fast and efficient for search engine crawlers, like Googlebot, to crawl your site and index your pages. Some advantages, like speed, come out of the box and others require configuration.

Because Gatsby pages are server-side rendered, all the page content is available to Googlebot and other search engine crawlers. You can see this by viewing the source for this page in your browser, Right-Click => View source. You'll see the fully rendered HTML document.

When you've installed `[gatsby-plugin-offline](https://www.gatsbyjs.com/plugins/gatsby-plugin-offline/)`, you'll see a partial HTML document that does not contain the HTML you were hoping for. By using `gatsby-plugin-offline`, we can optimize bandwidth consumption and not let your users download too much data. Serving a partial HTML document is okay. Google and other search engines will still see the full HTML because `gatsby-plugin-offline` only starts working on the second-page load. A search engine always runs a page in Sandbox mode, which essentially is the first visit.

As a website owner, how do I test my site is serving its HTML correctly when `gatsby-plugin-offline` is being used? It would be best if you used your terminal of choice to visit your website. You can crawl your site by running the following command:

**on Windows (using PowerShell):**

```
Invoke-WebRequest https://www.gatsbyjs.com/docs/how-to/adding-common-features/seo | Select -ExpandProperty Content
```

**on macOS/Linux:**

```
curl https://www.gatsbyjs.com/docs/how-to/adding-common-features/seo
```

Gatsby's many built-in performance optimizations, such as rendering to static files, progressive image loading, and so on, helping your site be lightning-fast by default.

In June 2021, [Google implemented a new ranking factor for site speed](https://developers.google.com/search/blog/2020/11/timing-for-page-experience), calling the algorithm update the "Core Web Vitals Update".

The Gatsby team included information about this in the [Core Web Vitals webinar](https://www.gatsbyjs.com/resources/webinars/understanding-core-web-vitals).

Adding metadata to pages, such as page title, meta description, alt text and structured data using JSON-LD, helps search engines understand your content and when to show your pages in search results.

A common way to add metadata to pages is to add [react-helmet](https://github.com/nfl/react-helmet) components (together with the [Gatsby React Helmet plugin](https://www.gatsbyjs.com/plugins/gatsby-plugin-react-helmet) for SSR support) to your page components. Here's a [guide on how to add an SEO component](https://www.gatsbyjs.com/docs/add-seo-component/) to your Gatsby app.

Some examples using react-helmet:

## Generate rich snippets in search engines using structured data

Google uses structured data that it finds on the web to understand the content of the page, as well as to gather information about the web and the world in general.

For example, here is a structured data snippet (added with `react-helmet`) in the [JSON-LD format](https://developers.google.com/search/docs/guides/intro-structured-data) (JavaScript Object Notation for Linked Data), that might appear on the contact page of a company called Spooky Technologies, describing their contact information:

```
<script type="application/ld+json"></script>
```

When using structured data, you'll need to test during development and the [Rich Results Test](https://search.google.com/test/rich-results) from Google is one recommended method.

After deployment, their [Rich result status reports](https://support.google.com/webmasters/answer/7552505?hl=en) may help to monitor the health of your pages and mitigate any templating or serving issues.

## Additional resources
