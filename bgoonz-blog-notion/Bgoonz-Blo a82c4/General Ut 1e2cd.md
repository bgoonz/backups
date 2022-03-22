# General Utilities | webdevhub

[https://bgoonz-blog.netlify.app/docs/tools/dev-utilities/](https://bgoonz-blog.netlify.app/docs/tools/dev-utilities/)

## SEMVER CHECKER... WHY?

> In the world of software management there exists a dread place called "dependency hell."
> 
> 
> The bigger your system grows and the more packages you integrate into your software, the more likely you are to find yourself, one day, in this pit of despair.
> 

More and more projects try to follow Semantic Versioning to reduce package versioning nightmare and every dependency manager implements its own semantic versioner. [Composer](https://getcomposer.org/) and [NPM](https://www.npmjs.org/) for example don't handle version constraints the same way. It's hard sometimes to be sure how some library version will behave against some constraint.

This tiny webapp checks if a given version satisfies another given constraint.

## SEMVER CONSTRAINT IMPLEMENTATIONS

Semantic Versioning stands as a standard versioning scheme but it does not ([yet](https://github.com/mojombo/semver/issues/113)) cover dependency management and how to express constraint.

Without any formal specification about constraint, dependency managers sometimes handle or express them differently. For example, the tilde-range constraint (`~x.y`) does not work the same way in [NPM](https://www.npmjs.org/) and [Composer](https://getcomposer.org/).

- See how [NPM](https://www.npmjs.org/) handles constraints: [npm/node-semver](https://github.com/npm/node-semver)
- See how [Composer](https://getcomposer.org/) handles constraints: [Package Versions](https://getcomposer.org/doc/01-basic-usage.md#package-version-constraints)

## WHY USING STRICT CONSTRAINT IS BAD?

Strict constraint (or fully qualified constraint) are those constraints matching only one version. In most case it is a bad idea to use them.

Why? Because with them you are locking your dependency to a specific patch release which means you won't ever get bug fixes when updating your dependencies.

Moreover, using strict constraint will make the work of some dependency managers harder: if you are depending on a package and have a dependency in common, if both of you require this common dependency strictly, your manager won't be able to choose an appropriate version, satisfying every constraint.

Unless you know exactly what you are doing and why, you should change to a more flexible one like:

- `~x.y.z` if your dependency manager supports tilde-range constraints
- `>=x.y.z <x.(y+1).0` if your dependency manager supports range constraints

Using such constraints, you will allow your dependency manager to pull patch releases letting you get bug fixes. If the library you are depending on strictly implements Semantic Versioning you should be able to make your constraint even more flexible by allowing your dependency manager to also pull new features:

- `^x.y.z` if your dependency manager supports caret-range constraints
- `>=x.y.z <(x+1).0.0` if your dependency manager support range constraints

## WHY USING LOOSE CONSTRAINT IS BAD?

Loose constraint are those constraints matching any version greater than a given one. It is a very bad idea to use them.

Why? Because with them you are only giving a lower bound to your dependency's version, which means every version greater than the one you chose, be it a patch, minor or major release. If we read Semantic Versioning carefully:

> Major version X (x.y.z | x > 0) MUST be incremented if any backwards incompatible changes are introduced to the public API. It MAY include minor and patch level changes. Patch and minor version MUST be reset to 0 when major version is incremented.
> 

What does this mean? It means that major releases **may** break backward compatibility. With a loose constraint you will get those releases and the BC break they introduce. This is likely not what you want!

[@bgooonz](https://twitter.com/bgooonz)

[General%20Ut%201e2cd/66654881](General%20Ut%201e2cd/66654881)

Enter URL of the HTML file to preview:

try

```

  https://github.com/bgoonz/GIT-HTML-PREVIEW-TOOL/blob/master/readme.html

```

as an example

## Archives

![https://bgoonz-blog.netlify.app/docs/tools/dev-utilities/landing-page/dist/images/iphone-hero-bg.png](https://bgoonz-blog.netlify.app/docs/tools/dev-utilities/landing-page/dist/images/iphone-hero-bg.png)

![https://bgoonz-blog.netlify.app/docs/tools/dev-utilities/landing-page/dist/images/iphone-feature-bg-01.png](https://bgoonz-blog.netlify.app/docs/tools/dev-utilities/landing-page/dist/images/iphone-feature-bg-01.png)

![https://bgoonz-blog.netlify.app/docs/tools/dev-utilities/landing-page/dist/images/iphone-feature-bg-02.png](https://bgoonz-blog.netlify.app/docs/tools/dev-utilities/landing-page/dist/images/iphone-feature-bg-02.png)

![https://shots.codepen.io/bgoonz/pen/zYwLVmb-800.jpg?version=1641466](https://shots.codepen.io/bgoonz/pen/zYwLVmb-800.jpg?version=1641466)