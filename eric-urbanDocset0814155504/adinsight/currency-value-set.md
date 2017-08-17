---
title: "Currency Value Set"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 858d864d-dacd-4a3f-a267-3523e69a35af
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Currency Value Set
Defines a selection of currency values.

> [!NOTE]
> The value set defines a broad selection of currency types; however, not all currencies are supported. For a list of supported currencies, see [Currencies](https://msdn.microsoft.com/library/bing-ads-currencies.aspx).

## Syntax

```xml
\<xs:simpleType name="Currency">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="AlgerianDinar" />
    \<xs:enumeration value="ArgentinePeso" />
    \<xs:enumeration value="ArmenianDram" />
    \<xs:enumeration value="AustralianDollar" />
    \<xs:enumeration value="AzerbaijanianManat" />
    \<xs:enumeration value="BahrainiDinar" />
    \<xs:enumeration value="Baht" />
    \<xs:enumeration value="Balboa" />
    \<xs:enumeration value="BelarussianRuble" />
    \<xs:enumeration value="BelizeDollar" />
    \<xs:enumeration value="Bolivar" />
    \<xs:enumeration value="Boliviano" />
    \<xs:enumeration value="BrazilianReal" />
    \<xs:enumeration value="BruneiDollar" />
    \<xs:enumeration value="CanadianDollar" />
    \<xs:enumeration value="ChileanPeso" />
    \<xs:enumeration value="ColombianPeso" />
    \<xs:enumeration value="CordobaOro" />
    \<xs:enumeration value="CostaRicanColon" />
    \<xs:enumeration value="Croatiankuna" />
    \<xs:enumeration value="CzechKoruna" />
    \<xs:enumeration value="DanishKrone" />
    \<xs:enumeration value="Denar" />
    \<xs:enumeration value="DominicanPeso" />
    \<xs:enumeration value="Dong" />
    \<xs:enumeration value="EgyptianPound" />
    \<xs:enumeration value="Euro" />
    \<xs:enumeration value="Forint" />
    \<xs:enumeration value="Guarani" />
    \<xs:enumeration value="HongKongDollar" />
    \<xs:enumeration value="Hryvnia" />
    \<xs:enumeration value="IcelandKrona" />
    \<xs:enumeration value="IndianRupee" />
    \<xs:enumeration value="IranianRial" />
    \<xs:enumeration value="IraqiDinar" />
    \<xs:enumeration value="JamaicanDollar" />
    \<xs:enumeration value="JapaneseYen" />
    \<xs:enumeration value="JordanianDinar" />
    \<xs:enumeration value="KenyanShilling" />
    \<xs:enumeration value="Kroon" />
    \<xs:enumeration value="KuwaitiDinar" />
    \<xs:enumeration value="Lari" />
    \<xs:enumeration value="LatvianLats" />
    \<xs:enumeration value="LebanesePound" />
    \<xs:enumeration value="Lek" />
    \<xs:enumeration value="Lempira" />
    \<xs:enumeration value="Leu" />
    \<xs:enumeration value="Lev" />
    \<xs:enumeration value="LibyanDinar" />
    \<xs:enumeration value="LithuanianLitus" />
    \<xs:enumeration value="MalaysianRinggit" />
    \<xs:enumeration value="MexicanPeso" />
    \<xs:enumeration value="MoroccanDirham" />
    \<xs:enumeration value="NewIsraeliSheqel" />
    \<xs:enumeration value="NewTaiwanDollar" />
    \<xs:enumeration value="NewZealandDollar" />
    \<xs:enumeration value="NorwegianKrone" />
    \<xs:enumeration value="NuevoSol" />
    \<xs:enumeration value="PakistanRupee" />
    \<xs:enumeration value="Pataca" />
    \<xs:enumeration value="PesoUruguayo" />
    \<xs:enumeration value="PhilippinePeso" />
    \<xs:enumeration value="QatariRial" />
    \<xs:enumeration value="Quetzal" />
    \<xs:enumeration value="RialOmani" />
    \<xs:enumeration value="Rufiyaa" />
    \<xs:enumeration value="Rupiah" />
    \<xs:enumeration value="RussianRuble" />
    \<xs:enumeration value="SaudiRiyal" />
    \<xs:enumeration value="SingaporeDollar" />
    \<xs:enumeration value="SlovakKoruna" />
    \<xs:enumeration value="Som" />
    \<xs:enumeration value="SouthAfricanRand" />
    \<xs:enumeration value="SwedishKrona" />
    \<xs:enumeration value="SwissFranc" />
    \<xs:enumeration value="SyrianPound" />
    \<xs:enumeration value="Tenge" />
    \<xs:enumeration value="Tolar" />
    \<xs:enumeration value="TrinidadandTobagoDollar" />
    \<xs:enumeration value="Tugrik" />
    \<xs:enumeration value="TunisianDinar" />
    \<xs:enumeration value="TurkishLira" />
    \<xs:enumeration value="UAEDirham" />
    \<xs:enumeration value="UKPound" />
    \<xs:enumeration value="USDollar" />
    \<xs:enumeration value="UzbekistanSum" />
    \<xs:enumeration value="Won" />
    \<xs:enumeration value="YemeniRial" />
    \<xs:enumeration value="YuanRenminbi" />
    \<xs:enumeration value="YugoslavianNewDinar" />
    \<xs:enumeration value="ZimbabweDollar" />
    \<xs:enumeration value="Zloty" />
  \</xs:restriction>
\</xs:simpleType>
```

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[EstimatedBidAndTraffic](../Ad Insight Version 11/estimatedbidandtraffic-data-object.md)  
[EstimatedPositionAndTraffic](../Ad Insight Version 11/estimatedpositionandtraffic-data-object.md)  
[GetEstimatedBidByKeywords](../Ad Insight Version 11/getestimatedbidbykeywords-service-operation.md)  
[GetEstimatedPositionByKeywords](../Ad Insight Version 11/getestimatedpositionbykeywords-service-operation.md)  

