---
title: "GetBulkDownloadStatus Service Operation"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b13f42f7-e8ad-4dfe-8ea7-7eb1e08074c1
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetBulkDownloadStatus Service Operation
Gets the status of a bulk download request.

> [!NOTE]
> You must use the same user credentials for the download request operation (either [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md)) and  the [GetBulkDownloadStatus](../bulk-api/getbulkdownloadstatus-service-operation.md) polling operation.

[!INCLUDE[bulk-service-namespace](../bulk-api/includes/bulk-service-namespace.md)]

## <a name="request"></a>GetBulkDownloadStatusRequest Message

### Request Element
The *GetBulkDownloadStatusRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*RequestId*|The identifier of the download request.<br /><br />The [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) and [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operations return this element as the *DownloadRequestId*.|*string*|

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
    <Action mustUnderstand="1">GetBulkDownloadStatus</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetBulkDownloadStatusRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <RequestId i:nil="false"></RequestId>
    </GetBulkDownloadStatusRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetBulkDownloadStatusResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Errors*|An array of *OperationError* objects corresponding to errors encountered during the system processing of the bulk file after your download request was submitted.|[OperationError](../bulk-api/operationerror-data-object.md) array|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for the *GetBulkDownloadStatusResponse* message object.|*KeyValuePairOfstringstring* array|
|*PercentComplete*|The progress completion percentage for system processing of the bulk download file.|*int*|
|*RequestStatus*|The status of the download. The possible values are as follows.<br /><br />Completed - The download completed successfully.<br /><br />InProgress - The download is in progress.<br /><br />Failed - The download failed. You may submit a new download with fewer entities, without performance data, or try again to submit the same download later.<br /><br />FailedFullSyncRequired - The request's *LastSyncTimeInUTC* element must be set to null, for example if the specified account was included in a data migration. After requesting a full download, you may begin requesting delta downloads again.|*string*|
|*ResultFileUrl*|The URL that contains the download data. This element contains the URL when the *Status* element is *Success*.<br /><br />**Note:** You have five minutes from the time that *GetBulkDownloadStatus* returns success to start downloading the file. If you do not start the download within this time period, you will need to call *GetBulkDownloadStatus* again to get a new URL.<br /><br />The download file is compressed (in zip format), so you must unzip the file to access the data.<br /><br />For information about the bulk file format, see [Bulk File Schema](../bulk-api/bulk-file-schema.md).|*string*|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[bulk_response_header_table](../bulk-api/includes/bulk-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <GetBulkDownloadStatusResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Errors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <OperationError>
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <Message p4:nil="false"></Message>
        </OperationError>
      </Errors>
      <ForwardCompatibilityMap xmlns:e1="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e1:KeyValuePairOfstringstring>
          <e1:key p5:nil="false"></e1:key>
          <e1:value p5:nil="false"></e1:value>
        </e1:KeyValuePairOfstringstring>
      </ForwardCompatibilityMap>
      <PercentComplete></PercentComplete>
      <RequestStatus p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></RequestStatus>
      <ResultFileUrl p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></ResultFileUrl>
    </GetBulkDownloadStatusResponse>
  </s:Body>
</s:Envelope>
```

## Remarks
Poll for downloads at reasonable intervals. You know your data better than anyone. If you download an account that is well less than one million keywords, consider polling at 15 to 20 second intervals. If the account contains about one million keywords, consider polling at one minute intervals after waiting five minutes. For accounts with about four million keywords, consider polling at one minute intervals after waiting 10 minutes.

## <a name="errors"></a>Error Codes
[!INCLUDE[bulkerror](../bulk-api/includes/bulkerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Symbolic|
|------------|
|InvalidCredentials|
|CampaignServiceInvalidDownloadRequestId|

## See Also
[DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md)  
[DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md)  

