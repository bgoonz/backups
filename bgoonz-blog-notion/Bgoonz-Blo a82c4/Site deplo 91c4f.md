# Site deploys overview | Netlify Docs

[https://docs.netlify.com/site-deploys/overview/#deploy-contexts](https://docs.netlify.com/site-deploys/overview/#deploy-contexts)

- 
    
    ![Site%20deplo%2091c4f/site-deploys-deploy-log-selected-lines.png](Site%20deplo%2091c4f/site-deploys-deploy-log-selected-lines.png)
    

![Site%20deplo%2091c4f/site-deploys-allowed_branches.png](Site%20deplo%2091c4f/site-deploys-allowed_branches.png)

Netlify automatically ensures that only your currently published production deploy and most recent branch deploys can be indexed by search engines. Requests to Deploy Previews, unpublished production deploys, and old branch deploys will have an `X-Robots-Tag: noindex` header included in the response. Depending on how you use branch deploys, you may want to prevent even your most recent branch deploys from being indexed by search engines. You can do so by configuring [custom headers](https://docs.netlify.com/routing/headers/) in your branch.

## [#](https://docs.netlify.com/site-deploys/overview/#deploy-contexts) Deploy contexts

Deploy contexts give you the flexibility to [configure your site's builds](https://docs.netlify.com/configure-builds/file-based-configuration/) depending on the context they are going to be deployed to.

There are three predefined deploy contexts:

- `production`: this context corresponds to the main site's deployment, attached to the Git branch you set when the site is created.
- `deploy-preview`: this context corresponds to the previews we build for pull/merge requests.
- `branch-deploy`: this context corresponds to deploys from branches that are not the site's main production branch.

Besides these three predefined contexts, sites can use also branch names as custom deploy contexts. For example, a branch called `staging` will match a deploy context called `staging`.

Deploy contexts allow you to override options from your site's settings including the build command, the environment variables added to the build, [Build Plugin configuration](https://docs.netlify.com/configure-builds/build-plugins/#configure-by-deploy-context), and more.

Overrides are applied in a hierarchical order. The site's global settings apply to each deploy, if we're building the production site, and if you change options in your production context, they will be overridden. Only options that are set explicitly are overridden; if you leave one out, the build will use the value of the global settings or previous contexts. Environment variables are also overridden individually, for example, you can have access tokens as environment variables per context.

To configure deploy contexts, you must create a file called `netlify.toml` in the root of your Git repository. There, you can set as many contexts as you want to configure.

```
# Production context:
# All deploys from the main repository branch
# will inherit these settings.
[context.production]
  command = "make production"
  [context.production.environment]
    ACCESS_TOKEN = "super secret"
  # Deploys from main branch run this plugin in the build.
  # Plugins context requires double brackets.
  [[context.production.plugins]]
    package = "@netlify/plugin-sitemap"

# Deploy Preview context:
# All deploys generated from a pull/merge request
# will inherit these settings.
[context.deploy-preview.environment]
  ACCESS_TOKEN = "not so secret"

# Branch deploy context:
# All deploys that are not from a pull/merge request
# or from the production branch will inherit these settings.
[context.branch-deploy]
  command = "make staging"

# Specific branch context:
# Deploys from this branch will take these settings
# and override their current ones.
[context.feature]
  command = "make feature"

[context."features/branch"]
  command = "gulp"

```

File-based configuration settings will override those set in the UI. In the `netlify.toml` file, settings for more specific contexts will override more general ones. For example, settings for a specific branch will override those for branch-deploy.

Visit our docs on [file-based configuration](https://docs.netlify.com/configure-builds/file-based-configuration/) to learn more about what you can do with deploy contexts.

## [#](https://docs.netlify.com/site-deploys/overview/#more-site-deploys-resources) More site deploys resources

- [Create deploys](https://docs.netlify.com/site-deploys/create-deploys/)
- [Manage deploys](https://docs.netlify.com/site-deploys/manage-deploys/)
- [Deploy Previews](https://docs.netlify.com/site-deploys/deploy-previews/)
- [Split Testing](https://docs.netlify.com/site-deploys/split-testing/)
- [Deploy notifications](https://docs.netlify.com/site-deploys/notifications/)
- [Post processing](https://docs.netlify.com/site-deploys/post-processing/)
