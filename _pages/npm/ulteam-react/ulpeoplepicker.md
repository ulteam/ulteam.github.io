---
title: ulteam-react UlPeoplePicker
permalink: /npm/ulteam-react/ulpeoplepicker/
---

## UlPeoplePicker component

People picker based on NormalPeoplePicker component from [office-ui-fabric-react](https://www.npmjs.com/package/office-ui-fabric-react) package.
It's just more convenient NormalPeoplePicker component.




### IUlPeoplePickerProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | customClassName | `Optional` |  *string* |     Class name which added to Office Ui Picker control       |  
 | defaultSelectedItems | `Optional` |  *IPersonaProps[]* |     Default values       |  
 | disabled | `Optional` |  *boolean* |     Flag for disabling the picker       |  
 | errorMessage | `Optional` |  *string* |     Text displayed below the control       |  
 | fieldName |  |  *string* |     Field name. It returns in handleChangeValues callback function       |  
 | handleChangeValues | `Optional` |  *function* |  |  
 | itemLimit |  |  *number* |     Restrict the amount of selectable items       |  
 | label | `Optional` |  *string* |     Field label       |  
 | noResultsFoundText | `Optional` |  *string* |     The text that should appear if no results are found when searching       |  
 | onResolveSuggestions |  |  *function* |     A callback for what should happen when a person types text into the input. Returns the already selected items so the resolver can filter them out. If used in conjunction with resolveDelay this will ony kick off after the delay throttle.       |  
 | required | `Optional` |  *boolean* |     If field is required       |  
 | resolveDelay | `Optional` |  *number* |     The delay time in ms before resolving suggestions, which is kicked off when input has been changed. e.g. If a second input change happens within the resolveDelay time, the timer will start over. Only until after the timer completes will onResolveSuggestions be called.       |  
 | suggestionProps | `Optional` |  *IBasePickerSuggestionsProps* |     Consts for suggestion list       |
