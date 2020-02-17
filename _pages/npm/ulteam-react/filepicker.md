---
title: ulteam-react FilePicker
permalink: /npm/ulteam-react/filepicker/
---

## FilePicker component

File picker based on HTML input with type="file".
Main features:
- You can pick one or several files.
- You can replace files or accumulate

### Demo
Try component on the [demo](/npm/ulteam-react/demo/?r=filepicker)

### Sample

```js
import * as React from 'react';
import { FilePicker, IFilePickerResult } from '../../../../common/components/FilePicker/FilePicker';

/**
 * Debug common components
 */
export class TestFilePicker extends React.Component<{}, {}> {
  constructor(props: {}) {
    super(props);
  }
  
  public render() {
    return (
      <div>
        <FilePicker 
          accumulateFiles={true}
          errorMessage="You should pick the file!!!"
          label="File picker label" 
          text="Browse..." 
          multiple={true}
          onChangeFile={this.onChangeFilePicker}
          onChangeFileBase64={this.onChangeFilePickerAsBase64}
          placeholder="Please pick the file..."
          required={true}
        />
      </div>
    );
  }

  public onChangeFilePicker = (files: File[]) => {
    for (const index in files) {
      console.log('file selected', files[index]);
    }
  }

  public onChangeFilePickerAsBase64 = (files: IFilePickerResult[]) => {
    for (const index in files) {
      if (index) {
        console.log(`base64: ${files[index].base64}`);
      }
    }
  }
}
```


### IFilePickerProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | accumulateFiles | `Optional` |  *boolean* |     Whether accumulate files or not.       |  
 | className | `Optional` |  *string* |     Custom class added to root div of component       |  
 | disabled | `Optional` |  *boolean* |     Whether the button is disabled       |  
 | errorMessage | `Optional` |  *string* |     Error message if required = true and file is not picked       |  
 | label | `Optional` |  *string* |     Label displayed above the control       |  
 | multiple | `Optional` |  *boolean* |     it specifies that the user is allowed to select more than one file       |  
 | onChangeFile | `Optional` |  *function* |     Fires after files are selected       |  
 | onChangeFileBase64 | `Optional` |  *function* |     Fires after files are selected. Returns file list with base64 prop.       |  
 | placeholder | `Optional` |  *string* |     Text placeholder. Displayed until file is not picked       |  
 | required | `Optional` |  *boolean* |     Whether file must be picked or not       |  
 | text | `Optional` |  *string* |     Button text       |
