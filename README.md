# Angular Deployment to GitHub Pages

This repo is a proof of concept for hosting an
[Angular](https://angular.dev/) application on [GitHub
Pages](https://pages.github.com/).

The deployed application can be found at
[eminor.net/ng-deploy-gh-poc](https://eminor.net/ng-deploy-gh-poc).

Note that I point my Github Page at a custom domain. By default, a
GitHub Pages deployment like this would be hosted at something like
`github.io/username/reponame`.

## Details

The application itself was generated with the [Angular
CLI](https://angular.dev/tools/cli) [^1].

```sh
# E.g.,
ng new ng-deploy-gh-poc
```

We use [SCSS](https://sass-lang.com/) and no server-side rendering.

### Build / Deploy

The way things are are currently set up, changes to the
application require:
1.   A manual build of the application.

```shell
# Writes ouptut to docs/browser.
ng build --output-path docs --base-href /ng-deploy-gh-poc/
```

2.   Commit the changes under the `docs/` output directory.
3.   Push the changes for handling by GitHub. Our GitHub workflow will
     deploy the static files the same way it would any other GitHub
     Pages change.

We could conceivably have our GitHub workflow perform the `ng build`
step as well. I'll probably do that.

### GitHub Configuration Details

In the project's GitHub Pages settings, we choose to use GitHub
Actions. The default workflow template only had to be updated
([here](https://github.com/memestreak/ng-deploy-gh-poc/blob/904027ac25bae6dcc96578d3f83532ff6f707f5e/.github/workflows/static.yml#L41))
to use the path `docs/browser`.

[^1]: `ng --version` is 18.2.12.
