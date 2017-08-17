---
title: "AgeRange Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6acc8cfd-a80f-4097-86ac-8868d6f421a0
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AgeRange Value Set
Defines the possible age range values that you can use to target ads to People.

## Syntax

```xml
\<xs:simpleType name="AgeRange">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="ZeroToSeventeen" />
    \<xs:enumeration value="ThirteenToSeventeen" />
    \<xs:enumeration value="EighteenToTwentyFour" />
    \<xs:enumeration value="TwentyFiveToThirtyFour" />
    \<xs:enumeration value="ThirtyFiveToFortyNine" />
    \<xs:enumeration value="FiftyToSixtyFour" />
    \<xs:enumeration value="SixtyFiveAndAbove" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|ZeroToSeventeen|People 17 years of age and younger.<br/><br/>**Note:** Reserved for internal use. This value will be removed in a future version of the API.|
|ThirteenToSeventeen|People from the ages of 13 through 17 years.<br/><br/>In many countries, online advertisers are not supposed to target any users less than 18 years old. Bing Ads does not deliver interest-based advertising to children whose birthdate in their Microsoft account identifies them as under 13 years of age. For more information see the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).<br/><br/>Currently people ages 13 to 17 can see your ads, although you cannot adjust the bid for that age range. Soon in Bing Ads you will be enabled to specifically exclude ages 13 to 17. The age range value of *ThirteenToSeventeen* will be supported with negative bid adjustments between -100 and 0. We will announce more specific dates within the next few months.|
|EighteenToTwentyFour|People from the ages of 18 through 24 years.|
|TwentyFiveToThirtyFour|People from the ages of 25 through 34 years.|
|ThirtyFiveToFortyNine|People from the ages of 35 through 49 years.|
|FiftyToSixtyFour|People from the ages of 50 through 64 years.|
|SixtyFiveAndAbove|People 65 years of age and older.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AgeCriterion](../campaign-api/agecriterion-data-object.md)

