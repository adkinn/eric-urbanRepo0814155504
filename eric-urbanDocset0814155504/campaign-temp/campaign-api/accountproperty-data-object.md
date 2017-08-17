---
title: "AccountProperty Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f916aef-7377-4c84-8972-584c4d653e74
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
---
# AccountProperty Data Object
Maps an account level property name to a string value.

## Syntax

```xml
\<xs:complexType name="AccountProperty">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Name" type="tns:AccountPropertyName"/>
    \<xs:element minOccurs="0" name="Value" nillable="true" type="xs:string"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Name*|The name of the account property.|[AccountPropertyName](../campaign-api/accountpropertyname-value-set.md)|
|*Value*|The value of the named account property.<br/><br/>The value will vary by account property name. For more information, see [Account Property Values](#accountpropertyvalues) in the section below.|*string*|


## <a name="accountpropertyvalues"></a>Account Property Values

### <a name="msclkidautotaggingenabled"></a>MSCLKIDAutoTaggingEnabled
If the *Name* element is set to *MSCLKIDAutoTaggingEnabled*, then the value can be set to either *True* or *False*. If the value is *True*, then the MSCLKID auto tagging feature is enabled. You might want to enable auto-tagging of MSCLKID for tracking leads via offline conversion goals. If auto-tagging of MSCLKID is enabled, the MSCLKID is automatically appended to the landing page URL when a customer clicks on your ad. For example, *www.contoso.com/?msclkid={msclkid}*. The click ID is unique for each ad click and multiple clicks on the same ad from the same user will result in multiple click IDs.

> [!IMPORTANT]
> [!INCLUDE[MSCLKID_auto_enabled](../campaign-api/includes/msclkid-auto-enabled.md)]


### <a name="trackingurltemplate"></a>TrackingUrlTemplate
If the *Name* element is set to *TrackingUrlTemplate*, then the value represents your account's tracking template to use as a default for all URLs in your account. The value of the *TrackingUrlTemplate* key can be set to any valid string as described below.

-   Tracking templates defined for lower level entities e.g. keyword override those set for higher level entities e.g. campaign. For more information, see [Entity Hierarchy and Limits](http://go.microsoft.com/fwlink/?LinkID=627130).

-   The length of the tracking template is limited to 2,048 characters.

    **Note:** The HTTP or HTTPS protocol string does count towards the 2,048 character limit.

-   The tracking template must be a well-formed URL beginning with one of the following: *http://*, *https://*, *{lpurl}*, or *{unescapedlpurl}*.

-   You must include at least one of the following landing page URL parameters: *{lpurl}*, *{lpurl+2}*, *{lpurl+3}*, *{unescapedlpurl}*, *{escapedlpurl}*. Additionally, you can use any dynamic parameter supported by Bing Ads. For a list of supported parameters, see the *Available parameters* sections within the Bing Ads help article [Set up a tracking template](https://help.bingads.microsoft.com/#apex/3/en/56772/-1).

-   Bing Ads does not validate whether custom parameters exist. If you use custom parameters in your tracking template and they do not exist, then the final URL will include the key and value placeholders of your custom parameters without substitution. For example if your tracking template is  for example *http://tracker.example.com/?season={_season}&promocode={_promocode}&u={lpurl}*, and neither {_season} or {_promocode}  are defined at the campaign, ad group, keyword, or ad level, then the final URL will be the same.

> [!NOTE]
> To delete the account's tracking template set the *Name* to *TrackingUrlTemplate* and the *Value* to *""* (empty string).

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md)  

