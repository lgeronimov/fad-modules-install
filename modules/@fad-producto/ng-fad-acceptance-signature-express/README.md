# Getting started

## Installation

```
npm install @fad-producto/ng-fad-acceptance-signature-express
```

## Dependencies

Add the folder provided by the technical team within the project assets (images and js)

## Assets
Add into the assets array (*angular.json*) the next lines:
``` json
{
  "glob": "**/*",
  "input": "node_modules/@fad-producto/ng-fad-pdf-reader/assets",
  "output": "./assets/"
}
``` 

## Import

In the file necessary *example.module.ts* import the module.

In this case  *app.module.ts*

``` ts
import { NgFadAcceptanceSignatureExpressModule } from '@fad-producto/ng-fad-acceptance-signature-express';
.
.
.
... imports: [
       ...,
       BrowserAnimationsModule 
       NgFadAcceptanceSignatureExpressModule
    ]...
```

Note: BrowserAnimationsModule is required.

# Usage

## HTML


Add the selector inside some component and configure the input parameters:


``` html
  <ng-fad-acceptance-signature-express
    [configuration]="configuration"
    [pdfSrc]="pdfSrc"
    [positionSignatures]="positionSignatures"
    [pdfResources]="pdfResources"
    (onerror)="onerror($event)"
    (onsigndocument)="onsigndocument()">
  </ng-fad-acceptance-signature-express>
```

## Typescript 

Listen to the events and execute methods:

``` ts
  public configuration = {};
  public onsigndocument = [];
  public pdfSrc = 'pdf resource';
  public pdfResources = null;

  onerror(error) {
    alert(JSON.stringify(error));
  }

  onsigndocument() {
    alert('next step');
  }

```


# Inputs

| Name                | Type    |  Required  | Default      | Description                         |
| ------------------- | ------- | -----------| ------------ | ----------------------------------- |
| configuration       | object  |  false     |  {}          |  module data to be configured       |
| pdfSrc              | string  |  true      |  undefined   |  pdf resource                       |
| positionSignatures  | object  |  true      |  undefined   |  signature coordinates              |


# Outputs

| Name              | Return  | Description                                                    |
| ----------------- | ------- | -------------------------------------------------------------- |
| onerror           | object  | Is called when an error happens                                |
| oncontinue        | void    | Is called when the user finishes the process                   |

