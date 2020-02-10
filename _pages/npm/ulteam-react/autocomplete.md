---
title: ulteam-react AutoComplete
permalink: /npm/ulteam-react/autocomplete/
---

## AutoComplete component

Text field with search and autocomplete. Based on Office UI Picker control.

<!-- Test -->

### IAutoCompleteProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | customClassName | `Optional` |  *string* |     Class name which added to Office Ui Picker control       |  
 | defaultSelectedItems | `Optional` |  *ITag[]* |     Default values       |  
 | disabled | `Optional` |  *boolean* |     Flag for disabling the picker       |  
 | errorMessage | `Optional` |  *string* |     Text displayed below the control       |  
 | fieldName |  |  *string* |     Field name. It returns in handleChangeValues callback function       |  
 | handleChangeValues | `Optional` |  *function* |  |  
 | itemLimit |  |  *number* |     Restrict the amount of selectable items       |  
 | items |  |  *ITag[]* |     Possible values       |  
 | label | `Optional` |  *string* |     Field label       |  
 | noResultsFoundText | `Optional` |  *string* |     The text that should appear if no results are found when searching       |  
 | openItemsOnEmptyFocus | `Optional` |  *boolean* |     Open all items when a user clicks the input       |  
 | placeholder | `Optional` |  *string* |     Standard HTML input placeholder       |  
 | required | `Optional` |  *boolean* |     If field is required       |  
 | resolveDelay | `Optional` |  *number* |     The delay time in ms before resolving suggestions, which is kicked off when input has been changed. e.g. If a second input change happens within the resolveDelay time, the timer will start over. Only until after the timer completes will onResolveSuggestions be called.       |  
 | suggestionsHeaderText | `Optional` |  *string* |     The text that appears at the top of the suggestions list       |
