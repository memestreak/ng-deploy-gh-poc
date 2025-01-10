# Angular Deployment to GitHub Pages

This repo is a proof of concept for hosting an
[Angular](https://angular.dev/) application on [GitHub
Pages](https://pages.github.com/).

The deployed application can be found at
[eminor.net/ng-deploy-gh-poc](https://eminor.net/ng-deploy-gh-poc) or
[memestreak.github.io/ng-deploy-gh-poc](https://memestreak.github.io/ng-deploy-gh-poc)
if my DNS mapping is borked.

## Details

### Generation

The application itself was generated with the standard [Angular
CLI](https://angular.dev/tools/cli) [^1].

```sh
# E.g.,
ng new ng-deploy-gh-poc
```

### Build / Deploy

The deployment model we use requires a local build of the app. The
generated artifacts are served by GitHub as GitHub Pages.

```shell
ng build --output-path docs --base-href /ng-deploy-gh-poc/
```

Next:
*   Commit the changes under the `docs/` output directory.
*   Push the changes for handling by GitHub. Our GitHub workflow will
    deploy the static files the same way it would any other GitHub
    Pages change.

We could conceivably have our GitHub workflow perform the `ng build`
step as well. I'll probably do that.

### GitHub Configuration Details

In the project's GitHub Pages settings, we choose to use GitHub
Actions.

The default workflow template only had to be updated
([`static.yml`](https://github.com/memestreak/ng-deploy-gh-poc/blob/904027ac25bae6dcc96578d3f83532ff6f707f5e/.github/workflows/static.yml#L41))
to use the path `docs/browser`.

[^1]: My current Angular version, `ng --version`, is 18.2.12.

### References

*   [Easy Steps to Host an Angular App in GitHub
    Pages](https://www.syncfusion.com/blogs/post/host-angular-app-in-github-pages)
