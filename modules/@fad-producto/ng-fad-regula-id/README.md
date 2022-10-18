# Getting started

## Installation

``` bash
npm install @fad-producto/ng-fad-regula-id
```

## Update
``` bash
npm install @fad-producto/ng-fad-regula-id@latest
```

## Import

In the file necessary *example.module.ts* import the module.

In this case  *app.module.ts*

``` ts
import { Configuration, CONFIGURATION_DEFAULT, Credentials, ErrorCode, ResponseError, ResponseSuccess, NgFadRegulaIdModule } from '@fad-producto/ng-fad-regula-id';
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

onerror(error) {
   alert(JSON.stringify(error));
}

```



# Inputs


| Name           | Required   | Default                                  |  Type                  | Description                                            |
| -----------    | ---------- | ---------------------------------------- | ---------------------- | ------------------------------------------------------ |
| configuration  |   false    |   CONFIGURATION_DEFAULT                  | IRegulaIdConfiguration | Configuration module                                   |
| credentials    |   true     |   undefined                              | Credentials            | Route to license file and request api                  |
| side           |   true     |   0                                      | 0 | 1                  | Side of image to capture, 0 - Front, 1 - Back          |
| shotOne        |   false    |   undefined                              | string                 | Base 64 of first captured image                        |
| idData         |   false    |   false                                  | boolean                | Add OCR to the final response                          |
| idPhoto        |   false    |   false                                  | boolean                | Image of the face cutout, only works if idData is true |
| delay          |   false    |   3 (always greater than or equal to 3 ) | number                 | Waiting time regarding the visibility of the camera    |


# Outputs


| Name        | Return          | Description                                |
| ----------- | --------------- | ------------------------------------------ |
| oncomplete  | ResponseSuccess | Fires when the liveness ends successfully  |
| onerror     | ResponseError   | Is called when an error happens            |
| onclose     | void            | Fires when user closes the camera          |

