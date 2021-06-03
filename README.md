# RockRunner

A pure HTML5 game ([source](https://github.com/juwalbose/ThreeJSEndlessRunner3D)) that can be streamed from SAS 9 or Viya using [SASjs](https://sasjs.io).

The purpose is to demonstrate the ease with which HTML5 apps can be compiled, built and deployed using SASjs.

## Prerequisites

* NPM and Node (12+)
* SASJS-CLI (`npm install -g @sasjs/cli`)

## Build Instructions

First, clone the directory, then open `sasjs/sasjsconfig.json`.  Choose your target (sas9 or Viya).  Within this target, modify the following items:

* `appLoc` -> the metadata or viya folder root location in which to build the app

At this point you can already run `sasjs cb -t sas9` or `sasjs cb -t viya` from the root of the project to compile and build a program you can run in SAS to generate the app.

## Build & Deploy Instructions

To auto build / deploy there are some additional steps.

### Viya

First obtain a client and secret (perhaps by using the [Viya Token Generator](https://youtu.be/mHP96rmyRoo)).

Then run `sasjs add cred -t viya` to authenticate and update the target attributes.

You can now run `sasjs cbd -t viya` and the log will be found under `sasjsbuild`.

### SAS9

For SAS9 just run `sasjs cb -t sas9` and run the `sasjsbuild/sas9deploy.sas` program in EG or SAS Studio.  A link to open the app will be shown in the bottom of the log.

Any issues, do raise an issue!
