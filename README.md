# NgDeployGhPoc

This repo is a proof of concept of hosting an [Angular][Angular] application on
[GitHub Pages][GitHub Pages].

The application itself was generated with the [Angular CLI][Angular
CLI] [^1].

```sh
# E.g.,
ng new ng-deploy-gh-poc
```

I chose to use [SCSS][SCSS] and no server-side rendering.

## Build / Deploy

```shell
ng build --output-path docs --base-href /ng-deploy-gh-poc/
```

The above command writes its output to a ./docs/browser.

## GitHub Configuration

In the project's GitHub Pages settings, we choose to use GitHub
Actions. The default workflow template only had to be updated
([here][static-template-change]) to use the path `docs/browser`.

[^1]: "ng --version" is 18.2.12.
[Angular]: https://angular.dev/
[GitHub Pages]: https://pages.github.com/
[Angular CLI]: https://angular.dev/tools/cli
[SCSS]: https://sass-lang.com/
[static-template-change]: https://github.com/memestreak/ng-deploy-gh-poc/blob/904027ac25bae6dcc96578d3f83532ff6f707f5e/.github/workflows/static.yml#L41
