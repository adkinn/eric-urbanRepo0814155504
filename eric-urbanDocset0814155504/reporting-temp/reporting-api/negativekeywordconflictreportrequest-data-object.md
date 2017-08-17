---
title: "NegativeKeywordConflictReportRequest Data Object"
ms.custom: ""
ms.date: "05/23/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4441a0b-63e4-4563-98d6-060a08e441df
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# NegativeKeywordConflictReportRequest Data Object
Defines a negative keyword conflict report request. Use this report to discover which keywords and negative keywords are in conflict, and whether the conflict is at the campaign or ad group level. Use this list to figure out which negative keywords to delete.

You can request negative keywords that conflict with some of your keywords, and block your ad from showing.

[!INCLUDE[reportrequest_header](../reporting-api/includes/reportrequest-header.md)]
## Syntax

```xml
\<xs:complexType name="NegativeKeywordConflictReportRequest">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:ReportRequest">
      \<xs:sequence>
        \<xs:element name="Columns" type="tns:ArrayOfNegativeKeywordConflictReportColumn" nillable="true"/>
        \<xs:element name="Filter" type="tns:NegativeKeywordConflictReportFilter" nillable="true" minOccurs="0"/>
        \<xs:element name="Scope" type="tns:AccountThroughAdGroupReportScope" nillable="true"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
This object inherits elements from the [ReportRequest](../reporting-api/reportrequest-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*Columns*|The list of attributes and performance statistics to include in the report. The report will include the columns in the order that you specify them.|[NegativeKeywordConflictReportColumn](../reporting-api/negativekeywordconflictreportcolumn-value-set.md) array|Required|
|*Filter*|The filter information to use to filter the report data.|[NegativeKeywordConflictReportFilter](../reporting-api/negativekeywordconflictreportfilter-data-object.md) array|Optional|
|*Scope*|The scope of the report. Use this element to limit the report to include data for a combination of accounts, ad groups, and campaigns.|[AccountThroughAdGroupReportScope](../reporting-api/accountthroughadgroupreportscope-data-object.md)|Required|

## <a name="InheritedElements"></a>Inherited Elements
This object inherits the following elements from the [ReportRequest](../reporting-api/reportrequest-data-object.md) object.

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*Format*|[!INCLUDE[reportrequest_format](../reporting-api/includes/reportrequest-format.md)]|[ReportFormat](../reporting-api/reportformat-value-set.md)|Optional|
|*Language*|[!INCLUDE[reportrequest_language](../reporting-api/includes/reportrequest-language.md)]|[ReportLanguage](../reporting-api/reportlanguage-value-set.md)|Optional|
|*ReportName*|[!INCLUDE[reportrequest_reportname](../reporting-api/includes/reportrequest-reportname.md)]|*string*|Optional|
|*ReturnOnlyCompleteData*|[!INCLUDE[reportrequest_returnonlycompletedata](../reporting-api/includes/reportrequest-returnonlycompletedata.md)]|*boolean*|Optional|

## Remarks
The report does not show the ad group or campaign that contains the negative keyword that conflicts with the keyword.

The report will identify a maximum of five conflicts per keyword. To ensure that you have resolved all the conflicts, you should run the report, resolve the conflicts, and then repeat until the report is empty.

The report uses a phrase-match comparison to determine the conflict. If you specify an exact-match negative keyword, the report may contain a false positive.

> [!WARNING]
> In this report, the keyword and negative keyword may not match exactly due to normalization. For example, if the keyword is “fork-lift” and negative keyword is “fork lift”, both of these get normalized to “fork lift”, and therefore will be considered a conflict. However, in the report the original keyword and negative keyword are displayed.

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[ReportRequest](../reporting-api/reportrequest-data-object.md)  
[SubmitGenerateReport](../reporting-api/submitgeneratereport-service-operation.md)  

