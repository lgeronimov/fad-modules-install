# Migration Details 
@fad-producto/ng-fad-acuant

---
## v5.x.x

The error response now provides more information about the AcuantResponse through the data value. The new error response returns an object of AcuantResultImage instead of an base 64 image.
``` ts
ResponseError {
  error: string;
  code: ErrorCode;
  data: {
    image: {
      data: string;
      width: number;
      height: number;
    };
    glare: string;
    dpi: string;
    cardtype: string;
    sharpness: number;
    moire: string;
    moireraw: string;
  }
};
``` 

> For more details check the `ResponseError` class

---
## v4.1.x

Manual capture images now is customizable through the pathDependencies object.

``` ts

pathDependencies: {
  acuantDirectory?: string;

  images?: {
    instructionFrontManualCaptureMobile?: string,
    instructionBackManualCaptureMobile?: string,
    instructionFrontManualCaptureDesktop?: string,
    instructionBackManualCaptureDesktop?: string,
  };
}
```

> For more details check the `IAcuantPathDependencies` interface

## v4.x.x

Customizable legends structure has been modified for manual capture.

Previus releases had a general legends for the manual capture. The newer structure divides the legends for the desktop view and the mobile view.
``` ts
manualCapture: {
  tooltip?: string;
  mobile?: {
    instruction?: string;
    buttonNext?: string;
  }
  desktop?: {
    instruction?: string;
    title?: string;
  }
}
```

> For more details check the `IModuleCustomizationLegendsManualCapture` interface
