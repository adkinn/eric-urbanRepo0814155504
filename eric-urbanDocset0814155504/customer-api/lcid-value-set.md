---
title: "LCID Value Set"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f7f53c3-58f6-486f-a321-dc90ca95c98d
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# LCID Value Set
Defines a selection of locale values.

> [!NOTE]
> The value set defines a broad selection of locales; however, not all languages are supported in each market. For a list of supported languages by market country, see [Ad Languages](https://msdn.microsoft.com/library/bing-ads-ad-languages.aspx).

## Syntax

```xml
\<xs:simpleType name="LCID">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="ArabicSaudiArabia">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1025</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ArabicAlgeria">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">5121</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ArabicBahrain">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">15361</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ArabicEgypt">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">3073</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ArabicIraq">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">2049</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ArabicJordan">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">11265</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ArabicKuwait">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">13313</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ArabicLebanon">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">12289</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ArabicLibya">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">4097</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ArabicMorocco">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">6145</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ArabicOman">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">8193</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ArabicQatar">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16385</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ArabicTunisia">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">7169</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ArabicUnitedArabEmirates">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">14337</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ArabicYemen">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">9217</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ChineseTaiwan">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1028</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="DanishDenmark">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1030</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="GermanGermany">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1031</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="EnglishUS">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1033</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="SpanishSpain">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1034</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="FinnishFinland">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1035</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="FrenchFrance">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1036</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="HebrewIsrael">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1037</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ItalianItaly">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1040</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="KoreanKorea">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1042</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="DutchNetherlands">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1043</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="NorwegianNorway">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1044</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="PortugueseBrazil">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1046</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="RussianRussia">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1049</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="SwedishSweden">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1053</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="EnglishThailand">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1054</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="EnglishIndonesia">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1057</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="EnglishVietnam">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1066</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="GermanSwitzerland">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">2055</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="EnglishUK">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">2057</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="SpanishMexico">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">2058</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ChineseHongKong">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">3076</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="GermanAustria">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">3079</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="EnglishAustralia">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">3081</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="FrenchCanada">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">3084</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="EnglishCanada">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">4105</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="EnglishNewZealand">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">5129</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="EnglishIreland">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">6153</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="SpanishVenezuela">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">8202</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="SpanishColombia">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">9226</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="SpanishPeru">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">10250</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="SpanishArgentina">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">11274</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="EnglishPhilippines">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">13321</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="SpanishChile">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">13322</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="EnglishIndia">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16393</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="EnglishMalaysia">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">17417</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="EnglishSingapore">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">18441</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
  \</xs:restriction>
  \</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|ArabicSaudiArabia|Arabic (Saudi Arabia)|
|ChineseHongKong|Chinese (Hong Kong)|
|ChineseTaiwan|Chinese (Taiwan)|
|DanishDenmark|Danish (Denmark)|
|DutchNetherlands|Dutch (Netherlands)|
|EnglishAustralia|English (Australia)|
|EnglishCanada|English (Canada)|
|EnglishIndia|English (India)|
|EnglishIndonesia|English (Indonesia)|
|EnglishMalaysia|English (Malaysia)|
|EnglishNewZealand|English (New Zealand)|
|EnglishPhilippines|English (Philippines)|
|EnglishSingapore|English (Singapore)|
|EnglishThailand|English (Thailand)|
|EnglishUK|English (United Kingdom)|
|EnglishUS|English (United States)|
|EnglishVietnam|English (Vietnam)|
|FinnishFinland|Finnish (Finland)|
|FrenchCanada|French (Canada)|
|FrenchFrance|French (France)|
|GermanAustria|German (Austria)|
|GermanGermany|German (Germany)|
|GermanSwitzerland|German (Switzerland)|
|HebrewIsrael|Hebrew (Israel)|
|ItalianItaly|Italian (Italy)|
|KoreanKorea|Korean (Korea)|
|NorwegianNorway|Norwegian (Norway)|
|PortuguesePortugal|Portuguese (Portugal)|
|RussianRussia|Russian (Russia)|
|SpanishArgentina|Spanish (Argentina)|
|SpanishChile|Spanish (Chile)|
|SpanishColombia|Spanish (Colombia)|
|SpanishMexico|Spanish (Mexico)|
|SpanishPeru|Spanish (Peru)|
|SpanishSpain|Spanish (Spain)|
|SpanishVenezuela|Spanish (Venezuela)|
|SwedishSweden|Swedish (Sweden)|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]