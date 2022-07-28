# Getting started

## Installation

``` bash
npm install @fad-producto/ng-fad-regula-id
```

## Dependencies

Add the folder provided by the technical team within the project assets (images and js)

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
  [license]="licence"
  [side]="side"
  [shotOne]="shotOne"
  [idData]="idData"
  [idPhoto]="idPhoto"
  (ondata)="ondata($event)"
  (onerror)="onerror($event)">
</ng-fad-regula-id>
```

## Typescript 

Listen to the events:

``` ts

license = "route to license";
shotOne = "image base64";
side = 0;
idData = true;
idPhoto = false;

ondata(result: RegulaResult) {
  console.log(result)
}

onerror(error) {
   alert(JSON.stringify(error));
}
```



# Inputs


| Name           | Required   | Default             |  Type             | Description                                            |
| -----------    | ---------- | ------------------- | ----------------- | ------------------------------------------------------ |
| license        |   true     |   undefined         | string            | Route to license file                                  |
| side           |   true     |   0                 | 0 | 1             | Side of image to capture, 0 - Front, 1 - Back          |
| shotOne        |   false    |   undefined         | string            | base 64 of first captured image                        |
| idData         |   false    |   false             | boolean           | add OCR to the final response                          |
| idPhoto        |   false    |   false             | boolean           | Image of the face cutout                               |


# Outputs


| Name        | Return        | Description                                |
| ----------- | ------------- | ------------------------------------------ |
| ondata      | RegulaResult  | Fires when the module send ocr             |
| onerror     | object        | Is called when an error happens            |
