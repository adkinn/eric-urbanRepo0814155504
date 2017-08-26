---
title: "DownloadCampaignsByCampaignIds Service Operation"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24e0dc96-4438-415b-8cbb-072466d031a0
caps.latest.revision: 12
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DownloadCampaignsByCampaignIds Service Operation
Downloads settings and performance data for the specified campaigns. You can request all campaign data or only the data that has changed since the last time you downloaded the campaign.

> [!NOTE]
> You must use the same user credentials for the download request operation (either [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md)) and  the [GetBulkDownloadStatus](../bulk-api/getbulkdownloadstatus-service-operation.md) polling operation.

[!INCLUDE[bulk_service_namespace](../bulk-api/includes/bulk-service-namespace.md)]

## <a name="request"></a>DownloadCampaignsByCampaignIdsRequest Message

### Request Body
The *DownloadCampaignsByCampaignIdsRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*Campaigns*|The campaigns to download. You can specify a maximum of 1,000 campaigns. The campaigns that you specify must belong to the same account.|[CampaignScope](../bulk-api/campaignscope-data-object.md) array|Yes|
|*CompressionType*|The compression type of the download file. For possible values, see [CompressionType](../bulk-api/compressiontype-value-set.md). The default is Zip.|[CompressionType](../bulk-api/compressiontype-value-set.md)|No|
|*DataScope*|You may include performance data such as spend, in addition to entity data such as campaign settings. The default is *EntityData* which will exclude performance data from the download.<br /><br />You may include multiple values as flags. How you specify multiple flags depends on the programming language that you use. For example, C# treats these values as flag values and Java treats them as an array of strings. The SOAP should include a string that contains a space-delimited list of values for example, `<DataScope>EntityData EntityPerformanceData</DataScope>`.<br /><br />**Note:** If *BidSuggestionsData*, *EntityPerformanceData*, or *QualityScoreData* are included, you must request a full sync to get performance data. To perform  a full sync, set *LastSyncTimeInUTC* to NULL.<br /><br />**Note:** If *EntityPerformanceData* is included, you must specify the *CustomerId* in the service request header.|[DataScope](../bulk-api/datascope-value-set.md)|No|
|*DownloadEntities*|The entities to include in the download. For a list of entities that you can download, see the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value set.<br /><br />**Note:** You must specify at least one download entity, and otherwise the operation will error.|*DownloadEntity* array|Yes|
|*DownloadFileType*|The format of the download file. For possible values, see [DownloadFileType](../bulk-api/downloadfiletype-value-set.md). The default is CSV.|[DownloadFileType](../bulk-api/downloadfiletype-value-set.md)|No|
|*FormatVersion*|The format for records of the download file.<br /><br />As a best practice you should always specify the latest format version. Currently the only supported format version for Bing Ads API Version 10 is 4.0.<br /><br />You should manage records according to the [Bulk File Schema](../bulk-api/bulk-file-schema.md) for the corresponding format version. |*string*|Yes|
|*LastSyncTimeInUTC*|The last time that you requested a download. The date and time is expressed in Coordinated Universal Time (UTC).<br /><br />If you specify the last sync time, only those entities that have changed (added, updated, or deleted) since the specified date and time will be downloaded. You cannot specify a date and time older than 90 days, as otherwise an error will be returned.<br/><br/> Target criterion are treated slightly different from other entities, and deleted records are not returned. If any changes were made to a campaign or ad group's target, then all currently active sub target criterion records are returned.<br /><br />Typically, you request a full download the first time you call the operation by setting this element to null. On all subsequent calls you set the last sync time to the time stamp of the previous download.<br /><br />The download file contains the time stamp of the download in the *SyncTime* column of the *Account* record. Use the time stamp to set *LastSyncTimeInUTC* the next time that you request a download.<br /><br />After requesting a full download, the only time that you should again request a full download would be if your account was included in a data migration (for example, the sitelink version 2 migration). If you specify a last sync time that predates the end of the migration process, the download will fail with CampaignServiceFullSyncRequired (error code 3603).|*dateTime*|No|
|*PerformanceStatsDateRange*|Defines the start and end date when downloading performance data.<br /><br />If the *DataScope* element includes *EntityPerformanceData*, then the start and end date must be set with this element.<br/><br/>The date range cannot exceed one year. For example April 1, 2015 through March 31, 2016 or April 1, 2016 through March 31, 2017 are both valid date ranges; however January 1, 2016 through April 30, 2017 is invalid.|[PerformanceStatsDateRange](../bulk-api/performancestatsdaterange-data-object.md)|No|

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
    <Action mustUnderstand="1">DownloadCampaignsByCampaignIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <DownloadCampaignsByCampaignIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Campaigns i:nil="false">
        <CampaignScope>
          <CampaignId></CampaignId>
          <ParentAccountId></ParentAccountId>
        </CampaignScope>
      </Campaigns>
      <CompressionType i:nil="false"></CompressionType>
      <DataScope></DataScope>
      <DownloadEntities i:nil="false">
        <DownloadEntity></DownloadEntity>
      </DownloadEntities>
      <DownloadFileType i:nil="false"></DownloadFileType>
      <FormatVersion i:nil="false"></FormatVersion>
      <LastSyncTimeInUTC i:nil="false"></LastSyncTimeInUTC>
      <PerformanceStatsDateRange i:nil="false">
        <CustomDateRangeEnd i:nil="false">
          <Day></Day>
          <Month></Month>
          <Year></Year>
        </CustomDateRangeEnd>
        <CustomDateRangeStart i:nil="false">
          <Day></Day>
          <Month></Month>
          <Year></Year>
        </CustomDateRangeStart>
        <PredefinedTime i:nil="false"></PredefinedTime>
      </PerformanceStatsDateRange>
    </DownloadCampaignsByCampaignIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>DownloadCampaignsByCampaignIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DownloadRequestId*|The identifier of the download request. You use the identifier to call the [GetBulkDownloadStatus](../bulk-api/getbulkdownloadstatus-service-operation.md) operation to check the status of the download. The identifier is valid for a maximum of two days. If you have not successfully downloaded the file within this period, it is removed from the download site and you will need to get a new download request identifier.<br /><br />The string has a length up to 40 and can contain any character.|*string*|

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
    <DownloadCampaignsByCampaignIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <DownloadRequestId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></DownloadRequestId>
    </DownloadCampaignsByCampaignIdsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[bulkerror](../bulk-api/includes/bulkerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
|CampaignServiceCampaignsArrayShouldNotBeNullOrEmpty|
|CampaignServiceCampaignsArrayExceedsLimit|
|CampaignServiceCampaignsContainsMultipleAccounts|
|CampaignServiceCampaignsContainsNullScope|
|CampaignServiceLastSyncTimeCannotBeInTheFuture|
|CampaignServiceFullSyncRequired|

## See Also
[DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md)  
[GetBulkDownloadStatus](../bulk-api/getbulkdownloadstatus-service-operation.md)

