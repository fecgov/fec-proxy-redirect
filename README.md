# fec-proxy-redirect

Proxy app to redirect applications to their CDN routes.

## Configuration

Add a `route` value to the manifest file to add a route to redirect to the `CDN_ROUTE` path.

## Deployment

The proxy follows [other projects](https://github.com/fecgov/openFEC#creating-a-release) for the release and hotfix processes. The changes will automatically deploy when PR's are merged, or the release is cut and deployed.

## Manual deployment

Manual deployment is an option if there are issues with CircleCI or you want more granular control of the process.

Before you start, make sure you have version 8 of the [Cloud Foundry CLI](https://docs.cloudfoundry.org/devguide/cf-cli/install-go-cli.html) installed.

When you're ready to deploy any changes, make sure you are on the `master` branch and have done a `git pull` so that all changes are pulled down.  Now run the following commands, where `<space>` is the desired space you'd like to deploy to (`dev`, `stage`, or `prod`):

```sh
    cf target -s <space>
    cf push --strategy rolling proxy-redirect -f manifest_<space>.yml
```

When the deployment is done, be sure to test the site to make sure everything is still functioning.

### Testing changes before deploying to Production

If you'd like to test any changes before they are fully merged and made a part of the code, you should feel free to do so but only in the `dev` and `staging` spaces.  To do this, just make sure you are on the branch you are currently working in and follow the deployment instructions above.

Just be sure to deploy the `master` branch again once the code is merged in (or the changes are rejected/abandoned).
