# Getting started

## Installation

``` bash
npm install @fad-producto/ng-fad-document-preview
```

## Assets
Add into the assets array (*angular.json*) the next lines:
``` json
{
  "glob": "**/*",
  "input": "node_modules/@fad-producto/ng-fad-pdf-reader/assets",
  "output": "./assets/"
}
``` 

## Dependencies

Add the folder provided by the technical team within the project assets (images and js)


## Import

In the file necessary *example.module.ts* import the module.

In this case  *app.module.ts*

``` ts
import { NgFadDocumentPreviewModule } from '@fad-producto/ng-fad-document-preview';
.
.
.
... imports: [
       ...,
       BrowserAnimationsModule 
       NgFadDocumentPreviewModule
    ]...
```

# Usage

## HTML


Add the selector inside some component and configure the output events:


``` html
<ng-fad-document-preview
  [configuration]="configuration"
  [pdfSrc]="pdf"
  [status]="status"
  [showDocumentRejection]="showDocumentRejection"
  [pdfResources]="pdfResources"
  (onerror)="onerror($event)"
  (onnext)="onnext()"
  (onrejectdocument)="onrejectdocument()">
</ng-fad-document-preview>
```

## Typescript 

Listen to the events:

``` ts

configuration = null;
pdf = 'src of your pdf';
status = 'PENDING';
showDocumentRejection = true;
pdfResources = null;

onerror(event) {
  alert(JSON.stringify(event));
}

onnext() {
  // do something after accept document
}

onrejectdocument() {
  this.status = STATUS_COMPONENT.REJECTED;
  // do something after reject document
}
  
.
.
.

export const STATUS_COMPONENT = {
  REJECTED: 'REJECTED',
  PENDING: 'PENDING',
  TO_SIGN: 'TO_SIGN',
}

export class PdfResource {
  scriptSrc: string;
  workerSrc: string;
  hasError: boolean;
  id: string;
}
```



# Inputs


| Name                  | Required   | Default             |  Type             | Description                                            |
| ------------------    | ---------- | ------------------- | ----------------- | ------------------------------------------------------ |
| configuration         |   false    |   object            | object            | configuration of legends                               |
| pdf                   |   true     |   undefined         | string            | source of your pdf                                     |
| status                |   true     |   undefined         | string            | status ofyour document                                 |
| showDocumentRejection |   false    |   undefined         | boolean           | shows the button to reject a document                  |
| pdfResources          |   false    |   undefined         | PdfResource[]     | modify the paths and files for the pdfjs library files |


# Outputs


| Name             | Return  | Description                             |
| ---------------- | ------- | --------------------------------------- |
| onnext           | string  | Is called when user ends the process    |
| onerror          | void    | Is called when an error happens         |
| onrejectdocument | void    | Is called when user reject the document |
