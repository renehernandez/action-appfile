# GitHub Actions for Appfile

This action enables you to manage Apps in the [DigitalOcean App Platform](https://www.digitalocean.com/products/app-platform/) services by installing [the `appfile` command-line client](https://github.com/renehernandez/appfile).

## Usage

To install the latest version of `appfile` and use it in GitHub Actions workflows, add the following step:

```yaml
    - name: Install appfile
      uses: renehernandez/action-appfile@v0.0.1
```

`appfile` will now be available in the virtual environment and can be used directly in the following steps. You will need a [DigitalOcean personal access token](https://www.digitalocean.com/docs/api/create-personal-access-token/) to execute appfile commands. As an example, one common use case is syncing an App platform specification to create a review environment for your branch:

```yaml
    - name: Deploy App in review environment
      env:
        DIGITALOCEAN_ACCESS_TOKEN: {{ secrets.DIGITALOCEAN_ACCESS_TOKEN }}
      run: appfile -f ./do/appfile.yaml -e review sync
```

### Arguments

- `version` – (Optional) The version of `appfile` to install. If excluded, the latest release will be used.

## Contributing

To install the needed dependencies, run `npm install`. The resulting `node_modules/` directory _is not_ checked in to Git.

Before submitting a pull request, run `npm run package` to package the code [using `ncc`](https://github.com/zeit/ncc#ncc). Packaging assembles the code including dependencies into one file in the `dist/` directory that is checked in to Git.

Pull requests should be made against the `main` branch. (it will switch to `v1` branch once it is stable)

## License

This GitHub Action and associated scripts and documentation in this project are released under the [MIT License](LICENSE).
