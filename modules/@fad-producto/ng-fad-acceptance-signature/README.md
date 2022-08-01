# Getting started

## Installation

``` bash
npm install @fad-producto/ng-fad-acceptance-signature
```

## Assets
Add into the assets array (*angular.json*) the next lines:
``` json
{
  "glob": "**/*",
  "input": "node_modules/@fad-producto/ng-fad-pdf-reader/assets",
  "output": "./assets/"
},
{
  "glob": "**/*",
  "input": "node_modules/@fad-producto/ng-fad-acceptance-signature/assets",
  "output": "./assets/"
}
```

## Dependencies

Add the folder provided by the technical team within the project assets (images and js)


## Import

In the file necessary *example.module.ts* import the module.

In this case  *app.module.ts*

``` ts
import { NgFadAcceptanceSignatureModule } from '@fad-producto/ng-fad-acceptance-signature';
.
.
.
... imports: [
       ...,
       BrowserAnimationsModule 
       NgFadAcceptanceSignatureModule
    ]...
```

# Usage

## HTML


Add the selector inside some component and configure the output events:


``` html
<ng-fad-acceptance-signature
    [configuration]="configuration"
    [pdfSrc]="pdf"
    [positionSignatures]="signatures"
    [pdfResources]="pdfResources"
    (onerror)="onerror($event)"
    (onmoreinformation)="onmoreinformation()"
    (onsigndocument)="onsigndocument()">
  </ng-fad-acceptance-signature>
```

## Typescript 

Listen to the events:

``` ts

configuration = null;
pdf = 'src of your pdf';
positionSignatures: PdfPagesSignature[];
pdfResources = null;

onerror(event) {
  alert(JSON.stringify(event));
}

onmoreinformation() {
  // do somethig after click in some information
}

onsigndocument() {
  // do somethig after accept all signatures
}
.
.
.

export class PdfPagesSignature {
  page: number;
  positionX1: number;
  positionX2: number;
  positionY1: number;
  positionY2: number;
  isSelected?: boolean;
  id?: string;
}

export class PdfResource {
  scriptSrc: string;
  workerSrc: string;
  hasError: boolean;
  id: string;
}
```



# Inputs


| Name                  | Required   | Default             |  Type                | Description                                            |
| ------------------    | ---------- | ------------------- | -------------------- | ------------------------------------------------------ |
| configuration         |   false    |   object            | object               | configuration of legends                               |
| pdf                   |   true     |   undefined         | string               | source of your pdf                                     |
| pdfResources          |   false    |   undefined         | PdfResource[]        | modify the paths and files for the pdfjs library files |
| positionSignatures    |   true     |   undefined         | PdfPagesSignature[]  | signature coordinates displayed in pdf                 |


# Outputs


| Name              | Return  | Description                                   |
| ----------------- | ------- | --------------------------------------------- |
| onmoreinformation | void    | Is called when user click to more information |
| onerror           | Object  | Is called when an error happens               |
| onsigndocument    | void    | Is called when user finish the process        |
