---
title: "ReportRequestStatus Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe7a63b6-5f28-4148-bc8d-61ade0753172
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ReportRequestStatus Data Object
Defines the status of a report request.

## Syntax

```xml
\<xs:complexType name="ReportRequestStatus">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="ReportDownloadUrl" nillable="true" type="xs:string" />
    \<xs:element minOccurs="0" name="Status" type="tns:ReportRequestStatusType" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ReportDownloadUrl*|The URL from where the report can be downloaded. Once returned, the URL is valid for five minutes.<br /><br />The report that you download is compressed by using zip compression. You must first unzip the report before you can use its contents.<br /><br />**Note:** Use the download URL only if the *Status* element is set to *Success*. Even when the *Status* is set to *Success*, this element can be nil if no data is available for the submitted report parameters.|*string*|
|*Status*|The status of a report request.|[ReportRequestStatusType](../reporting-api/reportrequeststatustype-value-set.md)|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[PollGenerateReport](../reporting-api/pollgeneratereport-service-operation.md)

