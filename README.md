# Angular Deployment to GitHub Pages

This repo is a proof of concept for hosting an [Angular](https://angular.dev/) application on
[GitHub Pages](https://pages.github.com/).

The application itself was generated with the [Angular
CLI](https://angular.dev/tools/cli) [^1].

```sh
# E.g.,
ng new ng-deploy-gh-poc
```

We chose to use [SCSS](https://sass-lang.com/) and no server-side rendering.

## Build / Deploy

```shell
ng build --output-path docs --base-href /ng-deploy-gh-poc/
```

The above command writes its output to `./docs/browser`.

## GitHub Configuration

In the project's GitHub Pages settings, we choose to use GitHub
Actions. The default workflow template only had to be updated
([here](https://github.com/memestreak/ng-deploy-gh-poc/blob/904027ac25bae6dcc96578d3f83532ff6f707f5e/.github/workflows/static.yml#L41))
to use the path `docs/browser`.

[^1]: `ng --version` is 18.2.12.
