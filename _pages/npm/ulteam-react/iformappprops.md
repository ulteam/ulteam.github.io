---
title: ulteam-react FormApp
permalink: /npm/ulteam-react/formapp/
---

## FormApp component
Generate your form with controls from [office-ui-fabric-react](https://www.npmjs.com/package/office-ui-fabric-react) package.
Configure form fields and component aggregates all field values in one plain object.
### IFormAppProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | asTableRow | `Optional` |  *boolean* |     Table row form view       |  
 | checkRequired |  |  *boolean* |     Add error message if required value is empty       |  
 | config |  |  *IFormConfig* |     Form field configuration       |  
 | currentFieldId | `Optional` |  *string* |     Current editing field. Used for UlTable optimization       |  
 | customClass | `Optional` |  *string* |     Add custom class to main div       |  
 | errorType | `Optional` |  *FormFieldErrorType* |     Field error type       |  
 | fieldNavByArrows | `Optional` |  *boolean* |     Add field navigation by keyboard arrows and enter buttons. Using in UlTable component       |  
 | fieldValues | `Optional` |  *any* |     Form fields as key value pairs. If value is undefined then form render with values from form field configuration (IFormAppProps.config)       |  
 | formId | `Optional` |  *number* |     Form id. Its value will be return in handleFieldValues function       |  
 | handleFieldNav | `Optional` |  *function* |     Fires if in control press arrow or enter buttons       |  
 | handleFieldOnClick | `Optional` |  *function* |     Fires if user clicked on any field control       |  
 | handleFieldValues |  |  *function* |     Fires if any field value has changed       |  
 | handleOnSelection | `Optional` |  *function* |     WARNING: It's prop using in UlTable. Handle on selection row in UlTable       |  
 | isFixed | `Optional` |  *boolean* |     Indicate than form is fixed column in UlTable       |  
 | isSelected | `Optional` |  *boolean* |     WARNING: it's prop using only in UlTable component. Whether form row is selected or not.       |  
 | isSelectionMode | `Optional` |  *boolean* |     WARNING: it's prop using only in UlTable component. Set selection mode: single or multiple       |  
 | isShimmer | `Optional` |  *boolean* |     Show Office UI Shimmer component instead of field       |  
 | labelsOnTheLeft | `Optional` |  *boolean* |     If true then control label will be moved from the top of the control to the left.       |  
 | onComponentMount | `Optional` |  *function* |     Get form metadata with error fields after mount Use this if you need to know info about error fields directly after mount component       |  
 | readView | `Optional` |  *boolean* |     Form on read mode       |
