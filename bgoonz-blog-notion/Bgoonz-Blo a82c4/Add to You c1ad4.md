# Add to Your Site | Netlify CMS | Open-Source Content Management System

[https://www.netlifycms.org/docs/add-to-your-site/#add-the-netlify-identity-widget](https://www.netlifycms.org/docs/add-to-your-site/#add-the-netlify-identity-widget)

1. Scroll down to , and click . This authenticates with your Git host and generates an API access token. In this case, we're leaving the field blank, which means any logged in user may access the CMS. For information on changing this, check the [Netlify Identity documentation](https://www.netlify.com/docs/identity/).

With the backend set to handle authentication, now you need a frontend interface to connect to it. The open source Netlify Identity Widget is a drop-in widget made for just this purpose. To include the widget in your site, add the following script tag in two places:

```
<script src="https://identity.netlify.com/v1/netlify-identity-widget.js"></script>
```

Add this to the `<head>` of your CMS index page at `/admin/index.html`, as well as the `<head>` of your site's main index page. Depending on how your site generator is set up, this may mean you need to add it to the default template, or to a "partial" or "include" template. If you can find where the site stylesheet is linked, that's probably the right place. Alternatively, you can include the script in your site using Netlify's [Script Injection](https://www.netlify.com/docs/inject-analytics-snippets/) feature.

When a user logs in with the Netlify Identity widget, an access token directs to the site homepage. In order to complete the login and get back to the CMS, redirect the user back to the `/admin/` path. To do this, add the following script before the closing `body` tag of your site's main index page:

```
<script>
  if (window.netlifyIdentity) {
    window.netlifyIdentity.on("init", user => {
      if (!user) {
        window.netlifyIdentity.on("login", () => {
          document.location.href = "/admin/";
        });
      }
    });
  }
</script>
```

Note: This example script requires modern JavaScript and does not work on IE11. For legacy browser support, use function expressions (`function () {}`) in place of the arrow functions (`() => {}`), or use a transpiler such as [Babel](https://babeljs.io/).

Your site CMS is now fully configured and ready for login!

If you set your registration preference to "Invite only," invite yourself (and anyone else you choose) as a site user. To do this, select the **Identity** tab from your site dashboard, and then select the **Invite users** button. Invited users receive an email invitation with a confirmation link. Clicking the link will take you to your site with a login prompt.

If you left your site registration open, or for return visits after confirming an email invitation, access your site's CMS at `yoursite.com/admin/`.

**Note:** No matter where you access Netlify CMS — whether running locally, in a staging environment, or in your published site — it always fetches and commits files in your hosted repository (for example, on GitHub), on the branch you configured in your Netlify CMS config.yml file. This means that content fetched in the admin UI matches the content in the repository, which may be different from your locally running site. It also means that content saved using the admin UI saves directly to the hosted repository, even if you're running the UI locally or in staging.

Happy posting!