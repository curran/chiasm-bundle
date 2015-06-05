# chiasm-bundle
A production-ready bundle of Chiasm and its plugins.

Just getting started, trying to work out the mechanics of JSPM.

The goal is that Chiasm plugins will each live in their own separate repositories, and can be authored in any JS module format (AMD, CJS, or ES6 modules). This repository will pull in the others using JSPM and create a bundle that contains them all.
