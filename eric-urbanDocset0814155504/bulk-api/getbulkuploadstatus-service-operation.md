---
title: "GetBulkUploadStatus Service Operation"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3db8105-9373-440c-952a-609f655454c4
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetBulkUploadStatus Service Operation
Gets the status and completion progress of a bulk upload request.

[!INCLUDE[bulk_service_namespace](../bulk-api/includes/bulk-service-namespace.md)]

## <a name="request"></a>GetBulkUploadStatusRequest Message
The *GetBulkUploadStatusRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

### Request Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*RequestId*|The identifier of the upload request.|*string*|

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
    <Action mustUnderstand="1">GetBulkUploadStatus</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetBulkUploadStatusRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <RequestId i:nil="false"></RequestId>
    </GetBulkUploadStatusRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetBulkUploadStatusResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Errors*|An array of *OperationError* objects corresponding to errors encountered during the system processing of the bulk file after your HTTP POST upload completed.<br /><br />For example, an *OperationError* would include the *BulkServiceFormatVersionNotSupported* error code if the uploaded file contains one or more bulk records that are not supported with the corresponding file format version.|[OperationError](../bulk-api/operationerror-data-object.md) array|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for the *GetBulkUploadStatusResponse* message object.|*KeyValuePairOfstringstring* array|
|*PercentComplete*|The progress completion percentage for system processing of the uploaded bulk file. The value range is between 0 and 100.<br /><br />**Note:** You should also compare the upload status. If the upload fails, the percent complete will reset to zero (0).|*int*|
|*RequestStatus*|The status of the upload. The following are the possible returned status values.<br /><br />Completed - The upload file was accepted and processed successfully without errors.<br /><br />CompletedWithErrors - The upload completed with one or more errors. While the overall upload was successful, one or more add or update errors could have occurred. As a best practice you should request error information via the *ResponseMode* element when calling [GetBulkUploadUrl](../bulk-api/getbulkuploadurl-service-operation.md) and check the *ResultFileUrl* for any errors.<br /><br />Failed - The entire upload failed due to an unexpected error. You may submit a new upload with fewer entities or try again to submit the same upload later.<br /><br />FileUploaded - The upload request has been received and is in the queue for processing.<br /><br />InProgress - The upload file has been accepted and the upload is in progress.<br /><br />PendingFileUpload - The upload file has not been received for the corresponding *RequestId*.<br/><br/>UploadFileRowCountExceeded - The limit of bulk records in the upload file has been exceeded. For more information about limits and upload best practices, see [Bulk Upload](https://msdn.microsoft.com/library/bing-ads-bulk-download-and-upload-guide.aspx#bulkupload).<br/><br/>UploadFileFormatNotSupported - The [Format Version](../bulk-api/format-version.md) *Name* field specified in the upload is not supported for this version of the Bulk API.|*string*|
|*ResultFileUrl*|The URL of the file that contains the requested results, for example upload error information.<br /><br />**Note:** The URL must be used within five minutes of the time that the *GetBulkUploadStatus* operation returns the *Completed* status response string. If you do not start the download within this period of time, you will need to call *GetBulkUploadStatus* again to get a new URL.|*string*|

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
    <GetBulkUploadStatusResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Errors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <OperationError>
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <Message p4:nil="false"></Message>
        </OperationError>
      </Errors>
      <ForwardCompatibilityMap xmlns:e2="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e2:KeyValuePairOfstringstring>
          <e2:key p5:nil="false"></e2:key>
          <e2:value p5:nil="false"></e2:value>
        </e2:KeyValuePairOfstringstring>
      </ForwardCompatibilityMap>
      <PercentComplete></PercentComplete>
      <RequestStatus p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></RequestStatus>
      <ResultFileUrl p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></ResultFileUrl>
    </GetBulkUploadStatusResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[bulkerror](../bulk-api/includes/bulkerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
|BulkServiceInvalidRequestId|

## See Also
[GetBulkUploadUrl](../bulk-api/getbulkuploadurl-service-operation.md)  

