---
title: "Account Image Ad Extension"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 525bd751-cf7a-4f6c-84b1-48ab348005db
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Account Image Ad Extension
Defines an association record between an [Account](../bulk-api/account.md) and an [Image Ad Extension](../bulk-api/image-ad-extension.md) that can be uploaded and downloaded in a bulk file. To upload or download the account or image ad extension, use the [Account](../bulk-api/account.md) or [Image Ad Extension](../bulk-api/image-ad-extension.md) record.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../bulk-api/includes/pilot-comingsoon.md)]
	
## <a name="entitydata"></a>Attribute Fields in the Bulk File
For a *Account Image Ad Extension* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Client Id](#clientid)
- [Editorial Location](#editoriallocation)
- [Editorial Reason Code](#editorialreasoncode)
- [Editorial Status](#editorialstatus)
- [Editorial Term](#editorialterm)
- [Id](#id)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Publisher Countries](#publishercountries)
- [Status](#status)

You can download all fields of the *Account Image Ad Extension* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *AccountImageAdExtensions* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](https://msdn.microsoft.com/library/bing-ads-bulk-download-and-upload-guide.aspx).

The following Bulk CSV example would associate an image ad extension to an account if the valid *Id* is provided. 

```csv
Type,Status,Id,Parent Id,Client Id,Modified Time,Name
Format Version,,,,,,5
Account Image Ad Extension,Active,-11,,ClientIdGoesHere,,
```

If you are using the [Bing Ads SDKs](https://msdn.microsoft.com/library/bing-ads-client-libraries.aspx) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkAccountImageAdExtension* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 

```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkAccountImageAdExtension
var bulkAccountImageAdExtension = new BulkAccountImageAdExtension
{
    // Map properties in the Bulk file to the 
    // AdExtensionIdToEntityIdAssociation object of the Campaign Management service.
    AdExtensionIdToEntityIdAssociation = new AdExtensionIdToEntityIdAssociation
    {
        // 'Id' column header in the Bulk file
        AdExtensionId = imageAdExtensionIdKey,
        // 'Parent Id' column header in the Bulk file
        EntityId = accountIdKey,
    },
                
    // 'Client Id' column header in the Bulk file
    ClientId = "ClientIdGoesHere",
    // 'Status' column header in the Bulk file
    Status = Status.Active,
};

uploadEntities.Add(bulkAccountImageAdExtension);

var entityUploadParameters = new EntityUploadParameters
{
    Entities = uploadEntities,
    ResponseMode = ResponseMode.ErrorsAndResults,
    ResultFileDirectory = FileDirectory,
    ResultFileName = DownloadFileName,
    OverwriteResultFile = true,
};

var uploadResultEntities = (await BulkService.UploadEntitiesAsync(entityUploadParameters)).ToList();
```

### <a name="clientid"></a>Client Id
[!INCLUDE[bulkcolumn_clientid](../bulk-api/includes/bulkcolumn-clientid.md)]

**Add:** Optional  
**Delete:** Read-only  

### <a name="editoriallocation"></a>Editorial Location
The component or property of the ad extension that failed editorial review. 

**Add:** Read-only  
**Delete:** Read-only  

### <a name="editorialreasoncode"></a>Editorial Reason Code
A code that identifies the reason for the failure. For a list of possible reason codes, see [Editorial Failure Reason Codes](https://msdn.microsoft.com/library/bing-ads-editorialfailurereasoncodes.aspx). 

**Add:** Read-only  
**Delete:** Read-only  

### <a name="editorialstatus"></a>Editorial Status
The editorial status of the ad extension.

Possible values include *Active*, *ActiveLimited*, *Disapproved*, and *Inactive*. For more details, see [AdExtensionEditorialStatus Value Set](https://msdn.microsoft.com/library/bing-ads-campaign-management-adextensioneditorialstatus.aspx).

**Add:** Read-only  
**Delete:** Read-only  

### <a name="editorialterm"></a>Editorial Term
The term that failed editorial review.

This field will not be set if a combination of terms caused the failure or if the failure was based on a policy violation.

**Add:** Read-only  
**Delete:** Read-only  

### <a name="id"></a>Id
The identifier of the ad extension that is associated or removed from the account.

This bulk field maps to the *Id* field of the [Image Ad Extension](../bulk-api/image-ad-extension.md) record. 

**Add:** Read-only and Required. You must either specify an existing ad extension identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Image Ad Extension](../bulk-api/image-ad-extension.md) record. This is recommended if you are adding new ad extensions and associations in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](https://msdn.microsoft.com/library/bing-ads-bulk-file-schema.aspx#referencekeys).  
**Delete:** Read-only and Required  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The identifier of the account where this ad extension is associated or removed.
	
This bulk field maps to the *Id* field of the [Account](../bulk-api/account.md) record. 

**Add:** Read-only  
**Delete:** Read-only  

### <a name="publishercountries"></a>Publisher Countries
The list of publisher countries whose editorial guidelines do not allow the specified [term](#editorialterm).

In a bulk file, the list of publisher countries are delimited with a semicolon (;).

**Add:** Read-only  
**Delete:** Read-only  

### <a name="status"></a>Status
Represents the association status between the account and the ad extension. 

Possible values are *Active* and *Deleted*. If the ad extension is associated with the account, this field's value is *Active*.

**Add:** Read-only  
**Delete:** Required. The Status must be set to *Deleted*. 
	
## <a name="entityperformancedata"></a>Performance Data Fields in the Bulk File
If the [DataScope Value Set](../bulk-api/datascope-value-set.md) element of the download request includes *EntityPerformanceData*, the download file will also include the following fields in this record.

|Column Header|Description|
|-----------------|---------------|
|*Spend*|[!INCLUDE[reportcolumn_spend](../bulk-api/includes/reportcolumn-spend.md)]|
|*Impressions*|[!INCLUDE[reportcolumn_impressions](../bulk-api/includes/reportcolumn-impressions.md)]|
|*Clicks*|[!INCLUDE[reportcolumn_clicks](../bulk-api/includes/reportcolumn-clicks.md)]|
|*CTR*|[!INCLUDE[reportcolumn_ctr](../bulk-api/includes/reportcolumn-ctr.md)]|
|*Avg CPC*|[!INCLUDE[reportcolumn_averagecpc](../bulk-api/includes/reportcolumn-averagecpc.md)]|
|*Avg CPM*|[!INCLUDE[reportcolumn_averagecpm](../bulk-api/includes/reportcolumn-averagecpm.md)]|
|*Avg position*|[!INCLUDE[reportcolumn_averageposition](../bulk-api/includes/reportcolumn-averageposition.md)]|
|*Conversions*|[!INCLUDE[reportcolumn_conversions](../bulk-api/includes/reportcolumn-conversions.md)]|
|*CPA*|[!INCLUDE[reportcolumn_costperconversion](../bulk-api/includes/reportcolumn-costperconversion.md)]|
