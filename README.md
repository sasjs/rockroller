# RockRunner

A pure HTML5 game ([source](https://github.com/juwalbose/ThreeJSEndlessRunner3D)) that can be streamed from SAS 9 or Viya using [SASjs](https://sasjs.io).

The purpose is to demonstrate the ease with which HTML5 apps can be compiled, built and deployed using SASjs.

## Prerequisites

* NPM (v7)
* SASJS-CLI (`npm install -g @sasjs/cli`)

## Build Instructions

First, clone the directory, then open `sasjs/sasjsconfig.json`.  Choose your target (sas9 or Viya).  Within this target, modify the following items:

* `appLoc` -> the metadata or viya folder root location in which to build the app
* `serverUrl` -> the URL of the Viya server.  Only needed for the Autodeploy option (below)

# Manual Deploy (Streaming App)

Simply run `sasjs cb -t sas9` or `sasjs cb -t viya` from the root of the project to compile and build a SAS program (`sasjsbuild/sas9deploy.sas` or `sasjsbuild/viyadeploy.sas`) that you can run to generate the app.  The link to the app will be at the bottom of the log.

## Auto Deploy (Streaming App)

To auto build / deploy there are some additional steps.

### Viya

First obtain a client and secret (perhaps by using the [Viya Token Generator](https://youtu.be/mHP96rmyRoo)).

Then run `sasjs add cred -t viya` to authenticate and update the target attributes.

You can now run `sasjs cbd -t viya` and a link to the app will be shown in the console.

### SAS9

For SAS9 you need to add `SAS_USERNAME` and `SAS_PASSWORD` in the `.env` file in the root of your project.  You can now run `sasjs cbd -t sas9` and the log will be found under `sasjsbuild`.
