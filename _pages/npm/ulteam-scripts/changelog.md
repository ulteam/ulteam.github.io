---
title: ulteam-scripts changelog
permalink: /npm/ulteam-scripts/changelog/
---

### changelog

#### v1.10.0
- feat: add DateFormat class

#### v1.9.6
- fix: empty 'data' property in the WebResponse.get method
- fix: add console.error logging when JSON.parse returned error in the WebResponse.get method

#### v1.9.5
- fix: error in WebResponse.get method where a 'fetch response' is an empty

#### v1.9.4
- docs: add page for the WebResponse class in the ulteam.github.io site
#### v1.9.3
- fix: registerGetValueCallback selector with '$' symbol in UOverride.setTextField method

#### v1.9.2
- fix: '$' symbol in control id for UForm.setItemValue method

#### v1.9.1
- fix: '$' symbol in control id for UForm.setItemValue method

#### v1.9.0
- feat: add ULogger class

#### v1.8.1
- fix: add fieldname attribute for tr tag in UForm class

#### v1.8.0
- feat: add UForm.hideTimeInDatePicker method

#### v1.7.1
- fix: delete required star with UForm.setRequiredStar method

#### v1.7.0
- feat: add UForm.setTextFieldAsMultiChoice method

#### v1.6.2
- fix: add *.scss files for sp folder

#### v1.6.1
- fix: set methods setDisplayUserMulti, setTextField in UOverride class as static methods

#### v1.6.0
- feat: add new classes for working with standard SharePoint list forms: UOverride, UForm

#### v1.5.1
- fix: error in WebResponse.get() method if response data json has 'd' prop with value as plain text 

#### v1.5.0
- feat: add Delay class

#### v1.4.0
- feat: add FetchHelper class

#### v1.3.1
- fix: error with blocking others track types if add url filters for trackPageView

#### v1.3.0
- feat: add url filters for trackPageView method in AzureLogger

#### v1.2.0
- fix: add compatible for Date object to UObjects.cloneDeep method