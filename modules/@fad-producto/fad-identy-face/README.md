# Getting started

## Installation

```
npm install @fad-producto/ng-fad-identy-face
```

### NOTE: For installations after Angular 9

```
npm install @fad-producto/ng-fad-identy-face --legacy-peer-deps
```

## SERVER
Request to the technical team:
1.- Server URL
2.- Add to the server the domains in which the application will be used (including development url's)

### Development URL'S
For local tests it is necessary to open a tunnel, it can be from PORTS in Visual Studio Code or it can be with the ngrok tool.
The url obtained from the tunnel must be passed to the technical team so that it can be added to the server.
Local tests must be done on the url obtained from the tunnel.

## Configuration project

In angular.json file add assets and styles

```
.
.
"assets": [
    "src/favicon.ico",
    "src/assets",
    {
      "glob": "**/*",
      "input": "node_modules/@fad-producto/ng-fad-identy-face/assets",
      "output": "./assets/"
    }
  ],
  "styles": [
    "node_modules/@fad-producto/ng-fad-identy-face/assets/third-party/identy-face/style/identy-face-style.css"
  ],
  .
  .
```

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
  [configuration]="configuration"
  [credentials]="credentials"
  (oncomplete)="oncomplete($event)"
  (onerror)="onerror($event)"
  (oncamera)="oncamera($event)">
</ng-fad-identy-face>
```

## Typescript

```ts
import { CONFIGURATION_DEFAULT, Credentials, IdentyDevice, IIdentyFaceConfiguration, NgFadIdentyFaceComponent, ResponseError, ResponseSuccess } from '@fad-producto/ng-fad-identy-face';.
.
.
@ViewChild(NgFadIdentyFaceComponent) component: NgFadIdentyFaceComponent;
configuration: IIdentyFaceConfiguration;
credentials: Credentials = {
  modelUrl: 'your_model_url'
}

onerror(error: ResponseError) {
  // manage error
}

oncomplete(event: ResponseSuccess) {
   // capture result
}

oncamera(data: IdentyDevice[]) {
  // select camera and execute next method
   deviceId = event[0].deviceId;
   this.component.selectCamera(deviceId)
}
```

# Inputs

| Name                  | Type                       |  Required  | Default               | Description                               |
| --------------------- | -------------------------- | ---------- |---------------------- | ----------------------------------------- |
| configuration         | IIdentyFaceConfiguration   |  false     | CONFIGURATION_DEFAULT | Configuration module                      |
| credentials           | Credentials                |  true      | undefined             | Credentials from server url               |

The following properties are for a more specific configuration of the module

| Name              | Type                       |  Required  | Default                   | Description                                                                   |
| ----------------- | -------------------------- | ---------- |-------------------------- | ----------------------------------------------------------------------------- |
| livenesCheck      | boolean                    |  false     | true                      | Run liveness check on the captured images                                     |
| allowCameraSelect | boolean                    |  false     | false                     | Set selection of camera (only in desktop)                                     |
| asThreshold       | AS_THRESHOLD               |  false     | AS_THRESHOLD.HIGH         | Property to set strictness of AS logic                                        |
| assisted          | boolean                    |  false     | false                     | Set selection of rear or front camera (only in mobile)                        |
| timeout           | number                     |  false     | 50000                     | Set the capture time in milliseconds. The amount cannot be greater than 50000 |
| appUI             | APP_UI                     |  false     | APP_UI.STANDARD           | Set the Capture Screen                                                        |


# Outputs

| Name           | Return                | Description                                         |
| -------------- | --------------------- | --------------------------------------------------- |
| oncomplete     | ResponseSuccess       | Is called when capture completes successfully       |
| onerror        | ResponseError         | Is called when an error happens                     |
| oncamera       | IdentyDevice[]        | returns the list of cameras available for selection |
