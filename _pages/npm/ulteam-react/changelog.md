---
title: ulteam-react changelog
permalink: /npm/ulteam-react/changelog/
---

### changelog

#### v2.35.1
- docs: add pages for PaginationDots & Slider components

#### v2.35.0
- feat: add PaginationDots & Slider components

#### v2.34.1
- fix: add background-color to ImageTile if image not found. 
- fix: set ImageTile photoPlacholder prop as optional

#### v2.34.0
- feat: add ImageTile props: maxHeight, maxWidth, id, onClick, tileTitle

#### v2.33.0
- feat: add ImageTile component

#### v2.32.4
- fix: raise IBlogTileBoardProps.style priority in BlogTileBoard component

#### v2.32.3
- fix: not show likes in BlogTile component if numberOfLikes = 0

#### v2.32.2
- fix: error style in BlogTile component

#### v2.32.1
- fix: correct style if BlogTile.noFixedHeight = true

#### v2.32.0
- feat: add BlogTile & BlogTileBoard components

#### v2.31.0
- feat: add errorMessage, required & placeholder props to FilePicker component

#### v2.30.0
- feat: add accumulateFiles, onChangeFileBase64 props to FilePicker component

#### v2.29.0
- feat: add resolveDelay to IPickerFieldProps and AutoComplete component

#### v2.28.0
- feat: add placeholder prop to IPickerFieldProps and AutoComplete component

#### v2.27.0
- feat: add autoValidation prop in INumberFieldProps

#### v2.26.0
- feat: add labelsOnTheLeftClassName for FormApp with prop 'labelsOnTheLeft' = 'true'

#### v2.25.6
- fix: add hidden priority. If hidden changed in field commonProperties then hiddenMap will be regenerated

#### v2.25.5
- fix: hidden prop was not included in condition to hide UlField & UlReadField

#### v2.25.4
- fix: delete tabIndex prop from UlReadField if fieldNavByArrows prop is not true

#### v2.25.3
- fix: delete tabIndex prop from UlReadField if field is not a table row field

#### v2.25.2
- fix: select All checkbox is selected if table has no rows.

#### v2.25.1
- fix: add onChangeSelection prop in UlTable component

#### v2.25.0
- feat: add row selection in UlTable. 
You need to add selectionMode prop for UlTable component

#### v2.24.0
- feat: add innerHtmlForReadMode prop to IFormFieldCommonProps

#### v2.23.1
- fix: add class 'ul-table-totalrow' to total row in UlTable component

#### v2.23.0
- feat: add total row in UlTable

#### v2.22.1
- feat: change groupKey type from string to any

#### v2.22.0
- feat: add groupKey & onClick props to GroupContent component for add custom behavior

#### v2.21.1
- fix: update current cell focus in UlTable if defaultRowFieldName or defaultRowId is changed

#### v2.21.0
- feat: add defaultRowId & defaultRowFieldName props in UlTable

#### v2.20.0
- feat: add custom class to GroupContent component

#### v2.19.1
- feat: add class for current row div in UlTable component
- fix: arrows navigation for readView (if all IUlTableRow's has isReadView = true)

#### v2.19.0
- feat: add officeUIProps to IDatePickerFieldProps

#### v2.18.0
- feat: add round prop to INumberFieldProps and ITextFieldProps

#### v2.17.2
- fix: incorrect behavior in UlTable navigation by arrows if one of the fields has name with underscore ('_')

#### v2.17.1
- fix: disable default keyboard scrolling in UlTable component if IUlTableProps.fieldNavByArrows is true

#### v2.17.0
- feat: add fieldNavByArrows prop for UlTable component (cell navigation by keyboard arrows and enter buttons)

#### v2.16.0
- feat: add disabled to FilePicker component

#### v2.15.0
- feat: add label to FilePicker component

#### v2.14.0
- feat: add FilePicker component based on HTML input with type="file"

#### v2.13.2
- fix: error with default value for ChoiceField in FormApp

#### v2.13.1
- fix: error in DatePicker field if no selected date and value is empty

#### v2.13.0
- feat: add errorOnChange callback function to IFormFieldCommonProps

#### v2.12.1
- fix: not showing error for required PeoplePicker form field

#### v2.12.0
- feat: update office-ui-fabric-react packet to v6.182.0

#### v2.11.0
- feat: add customActions prop to IHeaderFieldProps

#### v2.10.2
- fix: return undefined if default number value is 0

#### v2.10.1
- fix: unfocused field in UlTable sometimes

#### v2.10.0
- feat: add default value to IPeoplePickerFieldProps

#### v2.9.1
- fix: error with Title type in UlTable

#### v2.9.0
- feat: add errorsAsTooltip prop for UlTable
- feat: add errorType prop for FormApp
- fix: show error message in UlTable, FormApp if fieldValue is null

#### v2.8.2
- fix: error if fieldValues is undefined in UlTable, FormApp components

#### v2.8.1
- refactor: optimize UlTable, FormApp components

#### v2.8.0
- feat: add onComponentMount prop to FormApp, UlTable for info about error fields

#### v2.7.0
- feat: add PeoplePicker to FormApp, UlTable

#### v2.6.0
- feat: add isReadView to IUlTableRow

#### v2.5.0
- feat: add shimmer view mode for UlTable
- fix: add maxWidth from FormConsts in UlTable rows if field.properties.maxWidth is undefined

#### v2.4.1
- fix: width bug if type long value and focused out.
Add maxWidth property to IFormFieldCommonProps.
If you use fix header in UlTable you need add maxWidth parameter.

#### v2.4.0
- feat: add strings, allowTextInput, parseDateFromString props to IDatePickerFieldProps

#### v2.3.1
- fix: fix style in error message on DatePicker field

#### v2.3.0
- feat: add placeholder to TextField and NumberField
- feat: add Office UI Fabric DatePicker in all form components

#### v2.0.0
- Move helpers (Common and DateOperations classes) to ulteam-scripts package

#### v1.2.1
- Add handleCellClick event handler for UlTable

#### v1.1.1
- Small style fixes

#### v1.1.0
- Add DateOperations class

#### v1.0.0

- Add fix column feature to UlTable
- Add shadow to fix columns and fix header

#### v0.7.0
- Add auto focus in UlTable with readNoFocus prop
- Add fix header feature for UlTable

#### v0.6.6
- Add comments

#### v0.6.2
- Fix small errors

#### v0.6.1
- Fix sort bug

#### v0.6.0
- Add UlTable component
- Add Common 'helper' class

#### v0.5.0
- Fixed error with updating field values outside controls
- Code optimized

#### v0.4.4
- Fixed required controls with error.

#### v0.4.3
- Small fixes in styles.

#### v0.4.2
- Added errorFields attribute to handleFieldValues property for FormApp component.

#### v0.4.1
- Small fixes in styles.

#### v0.4.0
- Added openItemsOnEmptyFocus property to Picker field.

#### v0.3.3
- Fixed error with default values in form.

#### v0.3.2
- Fixed error with settings.scss.

#### v0.3.1
- Changed form sass files for more reusable.

#### v0.3.0
- Added custom accent color to Office UI Fabric controls.

#### v0.2.0
- Added Multiline props to TextField control.

#### v0.1.0
- Init project