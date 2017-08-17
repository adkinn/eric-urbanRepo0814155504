---
title: "CampaignNegativeSites Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3539186b-d935-4548-ba41-d52a7256c283
caps.latest.revision: 12
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CampaignNegativeSites Data Object
Defines an object that contains the negative site URLs of a campaign.

## Syntax

```xml
\<xs:complexType name="CampaignNegativeSites">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="CampaignId" type="xs:long" />
    \<xs:element xmlns:q53="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="NegativeSites" nillable="true" type="q53:ArrayOfstring" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CampaignId*|The identifier of the campaign to which the negative site URLs belong.|*long*|
|*NegativeSites*|A list of URLs of the websites on which you do not want your ads displayed. You can specify a maximum of 2,500 URLs. Each URL must specify the domain name e.g., *contoso.com* which can include up to three subdomains and two subdirectories. The subdomain count includes the *www* prefix. For example *one.two.three.contoso.com/1/2*, *www.two.three.contoso.com/1/2*, and *one.two.contoso.co.uk/1/2* are valid URLs, whereas *one.two.three.contoso.co.uk/1/2* (too many subdomains) and *one.two.three.contoso.com/1/2/3* (too many subdirectories) are not. Duplicate URLs in the list are not added.<br /><br />You can only exclude websites for syndicated search websites. The ad group's network must be set to either *OwnedAndOperatedAndSyndicatedSearch* or *SyndicatedSearchOnly*. For more information about network distribution, see [Network](../campaign-api/network-value-set.md).<br /><br />Negative site URLs specified at the ad group level are used instead of any negative site URLs specified at the campaign level.<br /><br />To remove all negative site URLs of the campaign, set this element to null.|*string* array|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[GetNegativeSitesByCampaignIds](../campaign-api/getnegativesitesbycampaignids-service-operation.md)  
[SetNegativeSitesToCampaigns](../campaign-api/setnegativesitestocampaigns-service-operation.md)  
[Network](../campaign-api/network-value-set.md)  

