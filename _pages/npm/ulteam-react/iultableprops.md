---
title: ulteam-react UlTable
permalink: /npm/ulteam-react/ultable/
---

## UlTable component
Generate your table with controls from [office-ui-fabric-react](https://www.npmjs.com/package/office-ui-fabric-react) package.
Configure table fields and component aggregates all rows values in one plain object.
Table has edit mode, shimmer mode. You can fix header or/and fix left columns.
### IUlTableProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | addTotalRow | `Optional` |  *boolean* |     Add total row on the bottom of the table. For handling add 'handleTotalRow' prop. WARN: it is working only for text and number field types       |  
 | checkRequired |  |  *boolean* |     Add error message if required value is empty       |  
 | customClass | `Optional` |  *string* |     Add custom class to main div       |  
 | defaultRowFieldName | `Optional` |  *string* |     Focus on the field by default       |  
 | defaultRowId | `Optional` |  *number* |     Focus on the row by default       |  
 | errorsAsTooltip | `Optional` |  *boolean* |     Error as Office UI Fabric Tooltip component       |  
 | fieldNavByArrows | `Optional` |  *boolean* |     Add cell navigation by keyboard arrows and enter buttons       |  
 | fields |  |  *Array‹[IFormField](interfaces/iformfield.md)‹any››* |     Row fields configuration       |  
 | fixHeight | `Optional` |  *number* |     Table row       |  
 | handleCellClick | `Optional` |  *function* |     Click event on any cell in table       |  
 | handleChangeValues |  |  *function* |  |  
 | handleTotalRow | `Optional` |  *function* |     If you want to add total row in table, you should set property addTotalRow = true Set values for total row. WARN: it is working only for text and number field types       |  
 | hideHeader | `Optional` |  *boolean* |     Hide table header or not       |  
 | isShimmer | `Optional` |  *boolean* |     Show Office UI Shimmer component instead of field       |  
 | onChangeSelection | `Optional` |  *function* |  |  
 | onComponentMount | `Optional` |  *function* |     Get table metadata with error fields after mount Use this if you need to know info about error fields directly after mount component       |  
 | readView | `Optional` |  *boolean* |     Table on read mode       |  
 | readViewNoFocus | `Optional` |  *boolean* |     No focused rows will always be on read mode       |  
 | rowCustomClass | `Optional` |  *string* |     Add custom class to row div       |  
 | rows |  |  *Array‹[IUlTableRow](interfaces/iultablerow.md)‹any››* |     Table row values and errors       |  
 | scrollOptions | `Optional` |  *IUlTableScrollOptions* |     Add scroll to the table and fix header on the top       |  
 | selectionMode | `Optional` |  *UlTableSelectionMode* |     Controls how/if the details list manages selection. Options include single, multiple       |  
 | shimmerRowCount | `Optional` |  *number* |  |
