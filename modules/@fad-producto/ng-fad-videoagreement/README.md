# Getting started

## Installation
``` bash
npm install @fad-producto/ng-fad-videoagreement
```

## Update
``` bash
npm install @fad-producto/ng-fad-videoagreement@latest
```

## Assets
Add into the assets array (*angular.json*) the next lines:
``` json
{
  "glob": "**/*",
  "input": "node_modules/@fad-producto/ng-fad-videoagreement/assets",
  "output": "./assets/"
}
``` 
### Example:
```json
"architect": {
  "build": {
    "options": {
      "assets": [
        "src/favicon.ico",
        "src/assets",
        {
          "glob": "**/*",
          "input": "node_modules/@fad-producto/ng-fad-videoagreement/assets",
          "output": "./assets/"
        }
      ],
    }
  }
}
```

## Import

In the file necessary *example.module.ts* import the module.

In this case  *app.module.ts*

``` ts
import { Configuration, ResponseError, ResponseSuccess, ErrorCode, CONFIGURATION_DEFAULT } from '@fad-producto/ng-fad-videoagreement';
.
.
.
... imports: [
       ...,
       BrowserAnimationsModule 
       NgFadVideoagreementModule
    ]...
```

Note: BrowserAnimationsModule is required.

# Usage

## HTML


Add the selector inside some component and configure the input parameters:


``` html
<ng-fad-videoagreement
  [legend]="legend"
  [configuration]="configuration"
  (onerror)="onerror($event)"
  (acceptCamera)="acceptCamera()"
  (oncomplete)="oncomplete($event)">
</ng-fad-videoagreement>
```

## Typescript 

Listen to the events:

``` ts
  public legend = 'Lorem Ipsum es simplemente el texto de relleno de las imprentas y archivos de texto. Lorem Ipsum ha sido el texto  de relleno estándar de las industrias desde el año 1500';

  const configuration: Configuration = {
    faceDetection: {
      faceRequired: true
    },
    selfie: {
      captureSelfie: false,
      imageType: 'image/png',
      imageQuality: 1
    },
    timer: {
      recording: { min: 5 , max: 10 },
      faceUndected: 3
    },
  };

  oncomplete(response: ResponseSuccess) {
    console.log(response);
  }

  onerror(error: ResponseError) {
    console.log(error);
    // if (error.code === ErrorCode.BROWSER_NOT_SUPPORTED) // do something
  }
  
  acceptCamera() {
    console.log('camera accepted');
  }

```



# Inputs

| Name           | Type           |  Required  | Default               | Description                          |
| -------------- | -------------- | ---------- | --------------------- | ------------------------------------ |
| legend         | string         |  true      |  null                 |  Legend to repeat in the recording   |
| configuration  | Configuration  |  false     | CONFIGURATION_DEFAULT |  Module data to be configured        |


# Outputs

| Name         | Return          | Description                                        |
| ------------ | --------------- | -------------------------------------------------- |
| oncomplete   | ResponseSuccess | Fires when the process completes successfully      |
| acceptCamera | void            | Fires when the user accepts the camera permissions |
| onerror      | ResponseError   | Is called when an error happens                    |

