---
title: "ReportRequestStatusType Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b3e7cff-d9bb-4701-9170-82ccf3e26ae6
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ReportRequestStatusType Value Set
Defines the status of a report.

## Syntax

```xml
\<xs:simpleType name="ReportRequestStatusType">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Error"/>
    \<xs:enumeration value="Success"/>
    \<xs:enumeration value="Pending"/>
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Error|An error occurred while generating the report. You will need to submit your report request again. If the request continues to fail, consider getting the tracking identifier from the response message and contacting support.|
|Pending|The report is not yet complete.|
|Success|The report was successfully completed.<br /><br />The report can be downloaded from the URL contained in the *ReportDownloadUrl* element of the [ReportRequestStatus](../reporting-api/reportrequeststatus-data-object.md) object.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[ReportRequestStatus](../reporting-api/reportrequeststatus-data-object.md)  
[PollGenerateReport](../reporting-api/pollgeneratereport-service-operation.md)  

