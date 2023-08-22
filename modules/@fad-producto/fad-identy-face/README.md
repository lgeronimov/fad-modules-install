# Getting started

## Installation

```
npm install @fad-producto/ng-fad-identy-face
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
      "input": "node_modules/@identy/identy-face/dist/assets",
      "output": "./assets/"
    },
    {
      "glob": "**/*",
      "input": "node_modules/@identy/identy-common/dist/assets",
      "output": "./assets/"
    }
  ],
  "styles": [
    "node_modules/@identy/identy-face/dist/identy-face-style.css",
    "node_modules/@fad-producto/ng-fad-identy-face/assets/style/fad-identy-face.scss"
  ],
  .
  .
```

In tsconfig.json or tsconfig.base.json add

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
import { NgFadIdentyFaceModule } from '@fad-producto/ng-fad-identy-face';
.
.
.
... imports: [
       ...,
       BrowserAnimationsModule 
       NgFadIdentyFaceModule
    ]...
```

Note: BrowserAnimationsModule is required.

# Usage

## HTML

Add the selector inside some component

``` html
<ng-fad-identy-face
  [modelURL]="modelURL"
  (oncomplete)="oncomplete($event)"
  (onerror)="onerror($event)">
</ng-fad-identy-face>
```

## Typescript

```ts
import { CONFIGURATION_DEFAULT, IdentyDevice, IdentyFace, IIdentyFaceConfiguration, NgFadIdentyFaceComponent, ResponseError, ResponseSuccess } from '@fad-producto/ng-fad-identy-face';
.
.
.
@ViewChild(NgFadIdentyFaceComponent) component!: NgFadIdentyFaceComponent;
modelURL: string = 'yor_model_url';

onerror(error: ResponseError) {
  // manage error
}

oncomplete(event: ResponseSuccess) {
   // capture result
}

oncamera(event: IdentyDevice[]) {
   // select camera and execute next method
   deviceId = event[0].deviceId;
   this.component.selectCamera(deviceId)
}
```

# Inputs

| Name                  | Type                       |  Required  | Default               | Description                               |
| --------------------- | -------------------------- | ---------- |---------------------- | ----------------------------------------- |
| configuration         | IFingerprintsConfiguration |  false     | CONFIGURATION_DEFAULT | Configuration module                      |
| modelURL              | string                     |  true      | undefined             | Server url                                |
| delay                 | number                     |  false     | 1000                  | Set init delay                            |

The following properties are for a more specific configuration of the module

| Name              | Type                       |  Required  | Default                   | Description                                                |
| ----------------- | -------------------------- | ---------- |-------------------------- | ---------------------------------------------------------- |
| livenesCheck      | boolean                    |  false     | undefined                 | Run liveness check on the captured images                  |
| backend           | WEB_ASSEMBLY_BACKEND       |  false     | WEB_ASSEMBLY_BACKEND.WASM | WebAssembly backend for TensorFlow.js                      |
| allowCameraSelect | boolean                    |  false     | undefined                 | Set selection of camera (only in desktop)                  |


  allowCameraSelect?: boolean;



# Outputs

| Name           | Return                | Description                                         |
| -------------- | --------------------- | --------------------------------------------------- |
| oncomplete     | ResponseSuccess       | Is called when capture completes successfully       |
| onerror        | ResponseError         | Is called when an error happens                     |
| oncamera       | IdentyDevice[]        | returns the list of cameras available for selection |
