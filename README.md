# chiasm-bundle

Work in progress, not working yet.

A tool for creating a production-ready bundle of Chiasm and its plugins.

The goal is that Chiasm plugins will each live in their own separate repositories, and this tool will be able to produce bundles that include a specific set of plugins.

## Requirements
This is a draft of the requirements for the Chiasm-bundle tool.

Users should be able to specify:

 * a list of Chiasm plugins to include in the bundle, and
 * a list of dependencies to exclude from the bundle and instead shim (e.g. D3, Lodash)

By running some command, the following should happen:

 * specified Chiasm plugins should be installed from a registry
 * a UMD bundle should be created that exposes a distribution of Chiasm with the speficied plugins available to configurations.

## Implementation

Several tools can fetch packages:

 * NPM
 * Bower
 * JSPM

Several tools can create bundles:

 * Browserify
 * WebPack
 * JSPM
 * Esperanto / Rollup

We assume that Chiasm plugins will depend on third party modules, therefore a combination of tools that makes it easy to resolve transitive dependencies is preferred. NPM seems like the most stable and straightforward solution for this.

Chiasm-bundle will need to take as input a set of plugins, and based on that, dynamically install those plugins and produce a top-level JS module that includes all of them. Since NPM already uses `package.json` to specify a list of dependencies, Chiasm-bundle can leverage that as the means to specify a collection of Chiasm plugins.

If `package.json` is used to specify a collection of Chiasm plugins to include in the bundle, the Chiasm-bundle tool can read that file and dynamically generate a top-level JS module for the bundle that includes all of them via `require()` statements and makes them available to the Chiasm runtime.

Once the top-level JS module for the bundle is generated, Browserify can be used to generate the complete bundle using that module as the entry point.

Since Browserify supports shims for browser globals via [browserify-shim](https://github.com/thlorenz/browserify-shim), Chiasm-bundle can leverage its shim configuration options, which are conveniently embedded within `package.json`.
