---
title: ulteam-react FilePicker
permalink: /npm/ulteam-react/filepicker/
---

## FilePicker component
File picker based on HTML input with type="file".
Main features:
- You can pick one or several files.
- You can replace files or accumulate
### IFilePickerProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | accumulateFiles | `Optional` |  *boolean* |     Whether accumulate files or not.       |  
 | className | `Optional` |  *string* |     Custom class added to root div of component       |  
 | disabled | `Optional` |  *boolean* |     Whether the button is disabled       |  
 | label | `Optional` |  *string* |     Label displayed above the control       |  
 | multiple | `Optional` |  *boolean* |     it specifies that the user is allowed to select more than one file       |  
 | onChangeFile | `Optional` |  *function* |     Fires after files are selected       |  
 | onChangeFileBase64 | `Optional` |  *function* |     Fires after files are selected. Returns file list with base64 prop.       |  
 | text | `Optional` |  *string* |     Button text       |
