# RockRunner

A pure HTML5 game ([source](https://github.com/juwalbose/ThreeJSEndlessRunner3D)) that can be streamed from SAS 9 or Viya using [SASjs](https://sasjs.io).

The purpose is to demonstrate the ease with which HTML5 apps can be compiled, built and deployed using the Viya REST APIs and/or the [SAS9API](https://sas9api.io).

## Prerequisites

* NPM and Node (12+)
* SASJS-CLI (`npm install -g sasjs-cli`)

## Build Instructions

First, clone the directory, then open `sasjs/sasjsconfig.json`.  Choose your target (sas9 or Viya).  Within this target, modify the following items:

* `appLoc` -> the metadata or viya folder root location in which to build the app

At this point you can already run `sasjs cb sas9` or `sasjs cb viya` from the root of the project to create a build script you can run in SAS.

## Build & Deploy Instructions

To auto build / deploy there are some additional steps.

### Viya

First obtain a client, secret and access token (perhaps by using the [Viya Token Generator](https://youtu.be/mHP96rmyRoo)).  

Paste these in `tgtBuildVars` as follows (these are used by SAS to create the services)

```
    "tgtBuildVars": {
      "client": "client3FD3E2E4C127C5CA",
      "secret": "secret3FC9A521DC334A44",
      "access_token": "eyJhbGciOiJSUzI1NiIstruncated",
      "refresh_token": "eyJhbGciOiJSUztruncated"
    },
```

In addition, the `access_token` and the `contextName` (name of the compute server) should be entered below:

```
    "tgtDeployVars": {
      "contextName": "sharedcompute",
      "access_token": "eyJhbGciOiJSUzI1NiIstruncated"
    },
```

Finally, enter the `serverUrl`:
```
    "serverUrl": "http://sas.analytium.co.uk",
```

You can now run `sasjs cbd viya` and the log will be found under `sasjsbuild`.

### SAS9

For SAS9 we link into the [sas9api](https://sas9api.io) by Analytium.  Contact them for a free demo copy.  Config as follows:



```
    "tgtDeployVars": {
      "serverName": "SASApp",
      "repositoryName": "Foundation"
    },
    "serverUrl": "YOURSERVER:PORT",
```

Any issues, do raise an issue!