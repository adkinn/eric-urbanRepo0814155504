---
title: "PollGenerateReport Service Operation"
ms.custom: ""
ms.date: "05/23/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f37b97e3-83b9-41a3-a61a-cac5d615f7d1
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# PollGenerateReport Service Operation
Gets the status of a report request.

> [!NOTE]
> You must use the same user credentials for the [SubmitGenerateReport](../reporting-api/submitgeneratereport-service-operation.md) and [PollGenerateReport](../reporting-api/pollgeneratereport-service-operation.md). For more information, see [Request and Download a Report](http://go.microsoft.com/fwlink/?LinkId=691110).

[!INCLUDE[reporting_service_namespace](../reporting-api/includes/reporting-service-namespace.md)]

## <a name="request"></a>PollGenerateReportRequest Message

### Request Body
The *PollGenerateReportRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ReportRequestId*|The identifier of the report request. The [SubmitGenerateReport](../reporting-api/submitgeneratereport-service-operation.md) operation returns the identifier.|*string*|

### Request Headers
[!INCLUDE[header_intro](../reporting-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[rep_header_oauth](../reporting-api/includes/rep-header-oauth.md)]
#### Password Authentication
[!INCLUDE[rep_header_password](../reporting-api/includes/rep-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Reporting/v11">
    <Action mustUnderstand="1">PollGenerateReport</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <PollGenerateReportRequest xmlns="https://bingads.microsoft.com/Reporting/v11">
      <ReportRequestId i:nil="false"></ReportRequestId>
    </PollGenerateReportRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>PollGenerateReportResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ReportRequestStatus*|Contains the status of the report request and the download URL.|[ReportRequestStatus](../reporting-api/reportrequeststatus-data-object.md)|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[reporting_response_header_table](../reporting-api/includes/reporting-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Reporting/v11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <PollGenerateReportResponse xmlns="https://bingads.microsoft.com/Reporting/v11">
      <ReportRequestStatus p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <ReportDownloadUrl p4:nil="false"></ReportDownloadUrl>
        <Status></Status>
      </ReportRequestStatus>
    </PollGenerateReportResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[reperror](../reporting-api/includes/reperror.md)]The following are example error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|ReportingServiceInvalidReportId|
|ReportingServiceReportNotFound|

## See Also
[SubmitGenerateReport](../reporting-api/submitgeneratereport-service-operation.md)

