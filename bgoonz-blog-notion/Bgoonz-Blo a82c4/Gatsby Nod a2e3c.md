# Gatsby Node APIs | Gatsby

[https://www.gatsbyjs.com/docs/reference/config-files/gatsby-node/](https://www.gatsbyjs.com/docs/reference/config-files/gatsby-node/)

![gatsby.jpg](Gatsby%20Nod%20a2e3c/gatsby.jpg)

Gatsby gives plugins and site builders many APIs for building your site. Code in the file `gatsby-node.js` is run once in the process of building your site. You can use its APIs to create pages dynamically, add data into GraphQL, or respond to events during the build lifecycle. To use the [Gatsby Node APIs](https://www.gatsbyjs.com/docs/reference/config-files/gatsby-node/), create a file named `gatsby-node.js` in the root of your site. Export any of the APIs you wish to use in this file.

Every Gatsby Node API gets passed a [set of helper functions](https://www.gatsbyjs.com/docs/reference/config-files/node-api-helpers/). These let you access several methods like reporting, or perform actions like creating new pages.

An example gatsby-node.js file that implements two APIs, `onPostBuild`, and `createPages`.

```
const path = require(`path`)exports.onPostBuild = ({ reporter }) => {  reporter.info(`Your Gatsby site has been built!`)exports.createPages = async ({ graphql, actions }) => {const { createPage } = actionsconst blogPostTemplate = path.resolve(`src/templates/blog-post.js`)const result = await graphql(`  result.data.allSamplePages.edges.forEach(edge => {createPage({      path: `${edge.node.slug}`,      component: blogPostTemplate,      context: {        title: edge.node.title,
```

## Async vs. sync work

If your plugin performs async operations (disk I/O, database access, calling remote APIs, etc.) you must either return a promise (explicitly using `Promise` API or implicitly using `async`/`await` syntax) or use the callback passed to the 3rd argument. Gatsby needs to know when plugins are finished as some APIs, to work correctly, require previous APIs to be complete first. See [Debugging Async Lifecycles](https://www.gatsbyjs.com/docs/debugging-async-lifecycles/) for more info.

```
exports.createPages = async () => {const result = await fetchExternalData()exports.createPages = () => {return new Promise((resolve, reject) => {exports.createPages = (_, pluginOptions, cb) => {cb()
```

If your plugin does not do async work, you can return directly.

## APIs

Create pages dynamically. This extension point is called only after the initial sourcing and transformation of nodes plus creation of the GraphQL schema are complete so you can query your data in order to create pages.

You can also fetch data from remote or local sources to create pages.

### Parameters

```
const path = require(`path`)

exports.createPages = ({ graphql, actions }) => {
  const { createPage } = actions
  const blogPostTemplate = path.resolve(`src/templates/blog-post.js`)
  // Query for markdown nodes to use in creating pages.
  // You can query for whatever data you want to create pages for e.g.
  // products, portfolio items, landing pages, etc.
  // Variables can be added as the second function parameter
  return graphql(`
    query loadPagesQuery ($limit: Int!) {
      allMarkdownRemark(limit: $limit) {
        edges {
          node {
            frontmatter {
              slug
            }
          }
        }
      }
    }
  `, { limit: 1000 }).then(result => {
    if (result.errors) {
      throw result.errors
    }

    // Create blog post pages.
    result.data.allMarkdownRemark.edges.forEach(edge => {
      createPage({
        // Path for this page — required
        path: `${edge.node.frontmatter.slug}`,
        component: blogPostTemplate,
        context: {
          // Add optional context data to be inserted
          // as props into the page component.
          //
          // The context data can also be used as
          // arguments to the page GraphQL query.
          //
          // The page "path" is always available as a GraphQL
          // argument.
        },
      })
    })
  })
}
```