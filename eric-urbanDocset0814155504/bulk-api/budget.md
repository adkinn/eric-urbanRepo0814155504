---
title: "Budget"
ms.custom: ""
ms.date: "07/25/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3be01c5c-e8f1-42be-bc9d-00c1624c2003
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Budget
Defines a budget that can be uploaded and downloaded in a bulk file.

You can set a single daily budget that can be used by any campaign within the same account. This will enable you to efficiently distribute a single daily budget across all campaigns or across a defined group of campaigns within your Bing Ads account.

Say you have a budget of $20 to be used uniformly between two campaigns every day. On a given day Campaign A spends only $8 (of its $10 budget) because it got a smaller amount of impressions and clicks than usual. Using a Shared Budget, if Campaign B is performing well then Bing Ads will automatically take the remaining $2 and allocate it to Campaign B. This will increase the chances that the remaining budget will be used to send you more traffic.

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For an *Budget* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Budget](#budget)
- [Budget Name](#budgetname)
- [Budget Type](#budgettype)
- [Client Id](#clientid)
- [Id](#id)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Status](#status)

You can download all fields of the *Budget* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *Budgets* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](~/concepts/bulk-download-and-upload.md).

The following Bulk CSV example would add a new budget. 

```csv
Type,Status,Id,Parent Id,Client Id,Modified Time,Budget Id,Budget Name,Budget,Budget Type,Name
Format Version,,,,,,,,,,5
Budget,Active,-20,0,ClientIdGoesHere,,,My Shared Budget,50,DailyBudgetAccelerated,
```

If you are using the [Bing Ads SDKs](~/concepts/bing-ads-client-libraries.md) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkBudget* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkBudget
var bulkBudget = new BulkBudget
{
    // 'Parent Id' column header in the Bulk file
    AccountId = 0,
                
    // Map properties in the Bulk file to the 
    // Budget object of the Campaign Management service.
    Budget = new Budget
    {
        // 'Budget' column header in the Bulk file
        Amount = 50,
        // 'Budget Type' column header in the Bulk file
        BudgetType = BudgetLimitType.DailyBudgetAccelerated,
        // 'Budget Name' column header in the Bulk file
        Name = "My Shared Budget",
        // 'Id' column header in the Bulk file
        Id = budgetIdKey,
    },

    // 'Client Id' column header in the Bulk file
    ClientId = "ClientIdGoesHere",
    // 'Status' column header in the Bulk file
    Status = Status.Active
};

uploadEntities.Add(bulkBudget);

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

### <a name="budget"></a>Budget
The amount to spend daily across all campaigns that share the budget.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="budgetname"></a>Budget Name
The name of the budget. The name must be unique among all budgets within the account. The name can contain a maximum of 255 characters.

The service performs a case-insensitive comparison when it compares the name to existing budget names.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="budgettype"></a>Budget Type
The budget type determines the pace at which the budget is spent throughout the day.

You can set a shared budget to either *DailyBudgetAccelerated* or *DailyBudgetStandard*. The *MonthlyBudgetSpendUntilDepleted* value is not supported for shared budgets.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="clientid"></a>Client Id
[!INCLUDE[bulkcolumn_clientid](../bulk-api/includes/bulkcolumn-clientid.md)]

**Add:** Optional  
**Update:** Optional    
**Delete:** Read-only  

### <a name="id"></a>Id
The system generated identifier of the budget.

**Add:** Optional. You must either leave this field empty, or specify a negative identifier. A negative identifier set for the budget can then be referenced in the *Budget Id* field of dependent record types such as [Campaign](../bulk-api/campaign.md). This is recommended if you are adding new budget and new dependent records in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The system generated identifier of the account that contains the budget.

This bulk field maps to the *Id* field of the [Account](../bulk-api/account.md) record.

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="status"></a>Status
The status of the budget.

Possible values are *Active* or *Deleted*. 

**Add:** Optional. The default value is *Active*.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Required. The Status must be set to *Deleted*.


