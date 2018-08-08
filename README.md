# MOLGENIS test App

This is the MOLGENIS test app. Used for demoing purposed and template for developing Apps in MOLGENIS.

## Contributing
There are 2 ways to test and develop in apps for MOLGENIS.

- locally without MOLGENIS
- locally with MOLGENIS

### Test locally without a running MOLGENIS instance

For local testing you can execute the following commands:

```bash
# To install the application
yarn install

# To run develop mode
yarn dev
```

It will render a local version of the core variable catalogue.

#### Run unit tests
You can run unit tests by executing this command:

```bash
# Run once
yarn unit

# Run in watch-mode
yarn debug
```

#### Run end-to-end tests
You can run end-to-end test locally by running the following command:

```bash
yarn e2e
```

### Test with a running MOLGENIS instance
For local testing with a running MOLGENIS instance you have to alter the config of the app:

Comment in the following block

```config/index.js```

```javascript
module.exports = {
  dev: {

    // Paths
    assetsSubDirectory: 'static',
    assetsPublicPath: '/',
    // Beginning of block
    proxyTable: {
      '/login': {
        target: 'http://localhost:8080'
      },
      '/api': {
        target: 'http://localhost:8080'
      }
    },
    // End of block
```

And comment out this block in the same file.


```javascript
/**
 * GET and POST interceptors
 * Removes the need for a running backend during development
 */
No mock data available
```

That is it. Run a molgenis instance on localhost:8080 and start the core variable catalogue with:

```javascript
yarn dev
```

## Build your MOLGENIS app

See: [App developement documentation](https://molgenis.gitbooks.io/molgenis/content/developer_documentation/app-development.html)

You can now create a working application that can be imported in MOLGENIS directly, by executing:

```bash
yarn build
```

You can find the zip-file in the ```dist/molgenis-app-test.zip```.
