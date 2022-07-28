# Getting started

## Installation

```
npm i @fad-producto/ng-fad-pdf-reader
```

## Dependencies

Add the folder provided by the technical team within the project assets (images and js)

# Usage

## HTML

Add service inside some component:


## Add

In assets of angular.json file add

```json
"assets": [
    {
      "glob": "**/*",
      "input": "node_modules/@fad-producto/ng-fad-pdf-reader/assets",
      "output": "/assets/"
    }
```


## Import

In the necessary file *example.component.ts* import the service.


## Typescript

``` ts
  import { NgFadPdfReaderService } from '@fad-producto/ng-fad-pdf-reader';
  .
  .
  .

  constructor(private pdfReader: NgFadPdfReaderService) { }

  ngOnInit() {
    // 1.- Observe if pdf is ready
    this.pdfReader.verifyStatePdf.subscribe(res => {
      if (res) {
        // do something
      }
    });

    // 2.- Observe if module has error
    this.pdfReader.verifyErrorPdf.subscribe(res => {
      // get errors
      alert(JSON.stringify(res))
    });

    // 3.- initialize pdf reader
    this.pdfReader.loadPdfjsLibrary();
  }

  async getPdf() {
     /**
     * Get PDF
     * @param {any} pdfSrc
     * @return {Promise<any>}
     */

    const pdf = await this.pdfReader.getPdf("your_pdf");
    if (pdf) // get page(s)
    else // get error in verifyErrorPdf
  }

  async getPage(pdf: any) {
    /**
     * Get page
     * @param {any} pdf
     * @param {number} numberPage
     * @return {Promise<{number, src: string}>}
     */

    const page = await this.pdfReader.getPage(pdf, 1);
    if (page) // do something
    else // get error in verifyErrorPdf
  }
```
