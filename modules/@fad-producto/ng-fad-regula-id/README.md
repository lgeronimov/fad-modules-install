# Getting started

## Installation

``` bash
npm install @fad-producto/ng-fad-regula-id
```

## Update
``` bash
npm install @fad-producto/ng-fad-regula-id@latest
```

## Angular >= 13

``` bash
npm install npm i --save-dev @types/pako
```

Change noImplicitOverride and noImplicitReturns to false on tsonfig.json file

``` ts
"compilerOptions" : {
  .
  .
  .
  "noImplicitOverride": false,
  "noImplicitReturns": false,
  .
  .
  .
}
```

## Import

In the file necessary *example.module.ts* import the module.

In this case  *app.module.ts*

``` ts
import { NgFadRegulaIdModule } from '@fad-producto/ng-fad-regula-id';
.
.
.
... imports: [
       ...,
       BrowserAnimationsModule 
       NgFadRegulaIdModule
    ]...
```

# Usage

## HTML


Add the selector inside some component and configure the output events:


``` html
<ng-fad-regula-id
  [configuration]="configuration"
  [credentials]="credentials"
  [side]="side"
  [shotOne]="shotOne"
  [idData]="idData"
  [idPhoto]="idPhoto"
  (oncomplete)="oncomplete($event)"
  (onerror)="onerror($event)">
</ng-fad-regula-id>
```

## Typescript 

Listen to the events:

``` ts
import { Credentials, IRegulaIdConfiguration, ResponseError, ResponseSuccess } from '@fad-producto/ng-fad-regula-id';
.
.
.
public configuration: IRegulaIdConfiguration;

public credentials: Credentials = {
    license: 'assets/third-party/regula/regula.license',
    apiBasePath: environment.BASE_URL_REGULA
};

public shotOne = "image base64 of first capture";
public side = 0;
public idData = true;
public idPhoto = false;

oncomplete(result: ResponseSuccess) {
  console.log(result)
}

onerror(error: ResponseError) {
   alert(JSON.stringify(error));
}

onclose() {
  // remove module component from your component
}

```

# Inputs


| Name           | Required   | Default                                 |  Type                  | Description                                            |
| -----------    | ---------- | --------------------------------------- | ---------------------- | ------------------------------------------------------ |
| configuration  |   false    |  CONFIGURATION_DEFAULT                  | IRegulaIdConfiguration | Configuration module                                   |
| credentials    |   true     |  undefined                              | Credentials            | Route to license file and request api                  |
| side           |   true     |  0                                      | 0 or 1                 | Side of image to capture, 0 - Front, 1 - Back          |
| shotOne        |   false    |  undefined                              | string                 | Base 64 of first captured image                        |
| idData         |   false    |  false                                  | boolean                | Add OCR to the final response                          |
| idPhoto        |   false    |  false                                  | boolean                | Image of the face cutout, only works if idData is true |


## IRegulaIdConfiguration


The following properties are for a more specific configuration of the module

| Name                | Type                       |  Required  | Default                   | Description                                                |
| ------------------- | -------------------------- | ---------- |-------------------------- | ---------------------------------------------------------- |
| allowClose          | boolean                    |  false     | false                     | allows closing of the capture component                    |


# Outputs

| Name        | Return          | Description                                |
| ----------- | --------------- | ------------------------------------------ |
| oncomplete  | ResponseSuccess | Fires when the liveness ends successfully  |
| onerror     | ResponseError   | Is called when an error happens            |
| onclose     | void            | Fires when user closes the camera          |
