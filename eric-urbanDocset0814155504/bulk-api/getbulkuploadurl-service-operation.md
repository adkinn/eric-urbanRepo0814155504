---
title: "GetBulkUploadUrl Service Operation"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5bc41148-c430-4430-a0c0-ea59848e3737
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetBulkUploadUrl Service Operation
Submits a request for a URL where a bulk upload file may be posted.

[!INCLUDE[bulk-service-namespace](../bulk-api/includes/bulk-service-namespace.md)]

## <a name="request"></a>GetBulkUploadUrlRequest Message
The *GetBulkUploadUrlRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

### Request Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountId*|The account identifier corresponding to the data that will be uploaded.|*long*|
|*ResponseMode*|Specify whether to return errors and their corresponding data, or only the errors in the results file. The default is *ErrorsOnly*.|[ResponseMode](../bulk-api/responsemode-value-set.md)|

### Request Headers
[!INCLUDE[header_intro](../bulk-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[bulk_header_oauth](../bulk-api/includes/bulk-header-oauth.md)]
#### Password Authentication
[!INCLUDE[bulk_header_password](../bulk-api/includes/bulk-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <Action mustUnderstand="1">GetBulkUploadUrl</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetBulkUploadUrlRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <ResponseMode></ResponseMode>
      <AccountId></AccountId>
    </GetBulkUploadUrlRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetBulkUploadUrlResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*RequestId*|The identifier of the upload request.<br /><br />The identifier is valid for a maximum of two days. If you have not successfully uploaded the file within this period, you will need to get a new request identifier and upload URL. .|*string*|
|*UploadUrl*|The URL where you may submit your bulk upload file with  HTTP POST.<br /><br />The upload URL is valid for a maximum of two days. If you have not successfully uploaded the file within this period, you will need to get a new request identifier and upload URL.|*string*|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[bulk_response_header_table](../bulk-api/includes/bulk-response-header-table.md)]
### Response SOAP
The following example shows the complete SOAP response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <GetBulkUploadUrlResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <RequestId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></RequestId>
      <UploadUrl p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></UploadUrl>
    </GetBulkUploadUrlResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[bulkerror](../bulk-api/includes/bulkerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[GetBulkUploadStatus](../bulk-api/getbulkuploadstatus-service-operation.md)  

