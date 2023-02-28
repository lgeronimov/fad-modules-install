# Getting started

## Installation

```
npm install @fad-producto/ng-fad-identy-fingerprints
```

## License
Add the file provided by the technical team


## Configuration project
In angular.json file add identy assets and styles

```
.
.
"assets": [
    "src/favicon.ico",
    "src/assets",
    {
      "glob": "**/*",
      "input": "node_modules/@identy/identy-finger/dist/assets",
      "output": "./assets/"
    },
    {
      "glob": "**/*",
      "input": "node_modules/@identy/identy-common/dist/assets",
      "output": "./assets/"
    },
    {
      "glob": "**/*",
      "input": "node_modules/@fad-producto/ng-fad-identy-fingerprints/assets",
      "output": "./assets/"
    }
],
"styles": [
    "node_modules/@identy/identy-finger/dist/identy-finger-style.css",
    "node_modules/@fad-producto/ng-fad-identy-fingerprints/assets/style/fad-fingerprints.scss"
],
.
.
```

In tsconfig.json or tsconfig.app.json add

{
  ...
  compilerOptions: {
    ...
  "skipLibCheck": true,
    ...
  }
  ...
}

## Import

In the file necessary *example.module.ts* import the module.

In this case  *app.module.ts*

``` ts
import { NgFadIdentyFingerprintsModule } from '@fad-producto/ng-fad-identy-fingerprints';
.
.
.
... imports: [
       ...,
       NgFadIdentyFingerprintsModule
    ]...
```

# Usage

## HTML

Add the selector inside some component

``` html
<ng-fad-identy-fingerprints 
    [modelURL]="modelURL"
    [detectionModes]="detectionModes"
    [captureTimeout]="captureTimeout"
    (onerror)="onerror($event)" 
    (oncomplete)="oncomplete($event)"
    (onclose)="onclose()">
</ng-fad-identy-fingerprints>
```

## Typescript

```ts
import { NgFadFingerprintsComponent, CONFIGURATION_DEFAULT, FINGERS, IFingerprintsConfiguration, ResponseError, ResponseSuccess, WEB_ASSEMBLY_BACKEND } from '@fad-producto/ng-fad-identy-fingerprints';
.
.
.

modelURL: string = 'yor_model_url';
captureTimeout = 30000;
detectionModes: FINGERS[] = [FINGERS.L4F];

onerror(error: ResponseError) {
  // manage error
}

oncomplete(event: ResponseSuccess) {
   // capture result
}

onclose() {
  // manage close capture
}
```

# Inputs

| Name                  | Type                       |  Required  | Default               | Description                                                |
| --------------------- | -------------------------- | ---------- |---------------------- | ---------------------------------------------------------- |
| configuration         | IFingerprintsConfiguration |  false     | CONFIGURATION_DEFAULT | Configuration module                                       |
| modelURL              | string                     |  true      | undefined             | Server url                                                 |
| detectionModes        | FINGERS[]                  |  true      | undefined             | Hand (right or left) and fingers (4F or thumb) to capture  |
| captureTimeout        | number                     |  false     | 60000                 | Set capture timeout                                        |

## IFingerprintsConfiguration

The following properties are for a more specific configuration of the module

| Name          | Type                       |  Required  | Default                   | Description                                                |
| ------------- | -------------------------- | ---------- |-------------------------- | ---------------------------------------------------------- |
| allowClose    | boolean                    |  false     | undefined                 | Button that allows close the process before finish         |
| livenesCheck  | boolean                    |  false     | undefined                 | Run liveness check on the captured images                  |
| backend       | WEB_ASSEMBLY_BACKEND       |  false     | WEB_ASSEMBLY_BACKEND.WASM | WebAssembly backend for TensorFlow.js                      |


# Outputs

| Name           | Return          | Description                                    |
| -------------- | --------------- | ---------------------------------------------- |
| oncomplete     | ResponseSuccess | Is called when capture completes successfully  |
| onerror        | ResponseError   | Is called when an error happens                |
| onclose        | void            | Is called when user close component            |
