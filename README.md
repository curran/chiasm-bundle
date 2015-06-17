# chiasm-bundle

Work in progress, not working yet.

A tool for creating a production-ready bundle of Chiasm and its plugins.

The goal is that Chiasm plugins will each live in their own separate repositories, and this tool will be able to produce bundles that include a specific set of plugins.

## Requirements
This is a draft of the requirements for the Chiasm-bundle tool.

Users should be able to specify:

 * a list of Chiasm plugins to include in the bundle, and
 * a list of dependencies to exclude from the bundle (e.g. D3, Lodash)

By running some command, the following should happen:

 * specified Chiasm plugins should be installed from a registry
 * a UMD bundle should be created that exposes a distribution of Chiasm with the speficied plugins available to configurations.
