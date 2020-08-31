---
title: ulteam-scripts UOverride
permalink: /npm/ulteam-scripts/uoverride/
---

## UOverride class

Override SharePoint form CSR template

### Sample

```tsx
import { Delay } from "../../common/Delay";
import { IUChoiceField, UForm, UOverride } from "../../sp";

export class TestJSLink {
  public static async run() {
    const override: UOverride = new UOverride({
      addLoading: true,
      hideInDispForm: ['Title'],
      hideInEditForm: ['Title'],
      hideInNewForm: ['Title'],
      Templates: { Fields: {
        'Title': {
          'NewForm': UOverride.setTextField,
          'EditForm': UOverride.setTextField
        },
      }}
    });

    override.init();

    // wait 2 seconds (just for test loading circle)
    await Delay.go(2000);
    // --- your async 'onload' code (for example, REST API calls)
    
    // unblock form controls
    UForm.setFormDisabled(false);
    
    const choices: IUChoiceField[] = [
      {
        value: 'Choice #1'
      },
      {
        value: 'Choice #2'
      },
      {
        value: 'Choice #3'
      }
    ];
    // set text field as multi choice
    UForm.setTextFieldAsMultiChoice('TextField', false, ',', choices, 'Choice #1', (key: string, newValue: string, container: HTMLDivElement) => {
      console.log(key, newValue, container);
    });
    
    // disable one choice
    await Delay.go(2000);
    choices[0].disabled = true;
    UForm.setTextFieldAsMultiChoice('TextField', false, ',', choices, 'Choice #2', (key: string, newValue: string, container: HTMLDivElement) => {
      console.log(key, newValue, container);
    });

    // check in browser console what generated in UForm.formData object
    // this object generated in UOverride.init method
    console.log(UForm.formData);
  }
}
```

#### Constructors

| Name | Description |
|-|-|
| new UOverride(options: IUOverrideOptions) | Init template  <br> **options**: *Override options <br>*  |

#### Properties

| Name | Static | Description |
|-|-|-|
| override: TemplateOverridesOptions |  | Override SharePoint client template |

#### Methods

| Name | Returns | Static | Description |
|-|-|-|-|
| init() | void |  | Register template in TemplateManager. <br>(Run method SPClientTemplates.TemplateManager.RegisterTemplateOverrides(this.override))  |
| setDisplayUserMulti(ctx: RenderContext_FieldInForm) | string |  `Static`  | Set multi user field to display mode  <br> **ctx**: *Field render context <br>*  |
| setTextField(ctx: RenderContext_FieldInForm) | string |  `Static`  | Set single line text field to display mode  <br> **ctx**: *Field render context <br>*  |
