---
title: "Review Ad Extension"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7f90e86-6cfb-4975-83dc-ba08b06c0aaa
caps.latest.revision: 12
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Review Ad Extension
Defines a review ad extension that can be downloaded and uploaded in a bulk file.

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For a *Review Ad Extension* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Ad Schedule](#adschedule)
- [Client Id](#clientid)
- [Editorial Location](#editoriallocation)
- [Editorial Reason Code](#editorialreasoncode)
- [Editorial Status](#editorialstatus)
- [Editorial Term](#editorialterm)
- [End Date](#enddate)
- [Id](#id)
- [Is Exact](#isexact)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Publisher Countries](#publishercountries)
- [Source](#source)
- [Start Date](#startdate)
- [Status](#status)
- [Text](#text)
- [Url](#url)
- [Use Searcher Time Zone](#usesearchertimezone)
- [Version](#version)

You can download all fields of the *Review Ad Extension* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *ReviewAdExtensions* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](~/concepts/bulk-download-and-upload.md).

The following Bulk CSV example would add a new Review Ad Extension to the account's shared library. 

```csv
Type,Status,Id,Parent Id,Campaign,Ad Group,Client Id,Modified Time,Start Date,End Date,Text,Device Preference,Name,Ad Schedule,Use Searcher Time Zone,Is Exact,Source,Url
Format Version,,,,,,,,,,,,5,,,,,
Review Ad Extension,Active,-16,0,,,ClientIdGoesHere,,,12/31/2018,Review Text,,,(Monday[09:00-21:00]),FALSE,TRUE,Review Source Name,http://review.contoso.com
```

If you are using the [Bing Ads SDKs](~/concepts/bing-ads-client-libraries.md) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkReviewAdExtension* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkReviewAdExtension
var bulkReviewAdExtension = new BulkReviewAdExtension
{
    // 'Parent Id' column header in the Bulk file
    AccountId = 0,
    // 'Client Id' column header in the Bulk file
    ClientId = "ClientIdGoesHere",
                
    // Map properties in the Bulk file to the 
    // ReviewAdExtension object of the Campaign Management service.
    ReviewAdExtension = new ReviewAdExtension
    {
        // 'Id' column header in the Bulk file
        Id = reviewAdExtensionIdKey,
        // 'Is Exact' column header in the Bulk file
        IsExact = true,
        // 'Source' column header in the Bulk file
        Source = "Review Source Name",
        // 'Text' column header in the Bulk file
        Text = "Review Text",
        // 'Url' column header in the Bulk file
        Url = "http://review.contoso.com", 
                    
        // 'Ad Schedule' column header in the Bulk file
        Scheduling = new Schedule
        {
            // Each day and time range is delimited by a semicolon (;) in the Bulk file
            DayTimeRanges = new[]
            {
                // Within each day and time range the format is Day[StartHour:StartMinue-EndHour:EndMinute].
                new DayTime
                {
                    Day = Day.Monday,
                    StartHour = 9,
                    StartMinute = Minute.Zero,
                    EndHour = 21,
                    EndMinute = Minute.Zero,
                },
            },
            // 'End Date' column header in the Bulk file
            EndDate = new Microsoft.BingAds.V10.CampaignManagement.Date
            {
                Month = 12,
                Day = 31,
                Year = DateTime.UtcNow.Year + 1
            },
            // 'Start Date' column header in the Bulk file
            StartDate = null,
            // 'Use Searcher Time Zone' column header in the Bulk file
            UseSearcherTimeZone = false,
        },

        // 'Status' column header in the Bulk file
        Status = AdExtensionStatus.Active,
    },
};

uploadEntities.Add(bulkReviewAdExtension);

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

### <a name="adschedule"></a>Ad Schedule
The list of day and time ranges that you want the ad extension to be displayed with your ads. Each day and time range includes the scheduled day of week, start/end hour, and start/end minute. Each day and time range is enclosed by left and right parentheses, and separated from other day and time ranges with a semicolon (;) delimiter. Within each day and time range the format is *Day[StartHour:StartMinue-EndHour:EndMinute]*.

The possible values of *StartHour* range from 00 to 23, where *00* is equivalent to 12:00AM and *12* is 12:00PM.

The possible values of *EndHour* range from 00 to 24, where *00* is equivalent to 12:00AM and *12* is 12:00PM.

The possible values of *StartMinute* and *EndMinute* range from 00 to 60.

The following example demonstrates day and time ranges during weekdays from 9:00AM through 9:00PM: *(Monday[09:00-21:00]);(Tuesday[09:00-21:00]);(Wednesday[09:00-21:00]);(Thursday[09:00-21:00]);(Friday[09:00-21:00])*

**Add:** Optional. If you do not set this field, then ad extensions will be eligible for scheduling anytime during the calendar start and end dates.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] The individual day and time ranges cannot be updated. You can effectively update the day and time ranges by sending a new set that should replace the prior set. If you do not set this field, then the existing settings will be retained. If you set this field to *delete_value*, then you are effectively removing all existing day and time ranges.    
**Delete:** Read-only  

### <a name="clientid"></a>Client Id
[!INCLUDE[bulkcolumn_clientid](../bulk-api/includes/bulkcolumn-clientid.md)]

**Add:** Optional  
**Update:** Optional    
**Delete:** Read-only  

### <a name="editoriallocation"></a>Editorial Location
The component or property of the ad extension that failed editorial review. 

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="editorialreasoncode"></a>Editorial Reason Code
A code that identifies the reason for the failure. For a list of possible reason codes, see [Editorial Failure Reason Codes](~/concepts/bing-ads-editorial-failure-reason-codes.md). 

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="editorialstatus"></a>Editorial Status
The editorial status of the ad extension.

Possible values include *Active*, *ActiveLimited*, *Disapproved*, and *Inactive*. For more details, see [AdExtensionEditorialStatus Value Set](~/campaign-api/adextensioneditorialstatus-value-set.md).

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="editorialterm"></a>Editorial Term
The term that failed editorial review.

This field will not be set if a combination of terms caused the failure or if the failure was based on a policy violation.

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="enddate"></a>End Date
The ad extension scheduled end date string formatted as *MM/DD/YYYY*.

The end date is inclusive. For example, if you set this field to 3/10/2017, the ad extensions will stop being shown at 11:59 PM on 3/10/2017.

**Add:** Optional. If you do not specify an end date, the ad extensions will continue to be delivered unless you pause the associated campaigns, ad groups, or ads.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] The end date can be shortened or extended, as long as the start date is either null or occurs before the new end date. If you do not set this field, then the existing settings will be retained. If you set this field to *delete_value*, then you are effectively removing the end date and the ad extensions will continue to be delivered unless you pause the associated campaigns, ad groups, or ads.    
**Delete:** Read-only  

### <a name="id"></a>Id
The system generated identifier of the ad extension.

**Add:** Optional. You must either leave this field empty, or specify a negative identifier. A negative identifier set for the ad extension can then be referenced in the *Id* field of dependent record types such as [Ad Group Review Ad Extension](../bulk-api/ad-group-review-ad-extension.md) and [Campaign Review Ad Extension](../bulk-api/campaign-review-ad-extension.md). This is recommended if you are adding new ad extensions and new dependent records in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="isexact"></a>Is Exact
Determines whether the review text is an exact quote or paraphrased. If not specified, the default value of *FALSE* indicates that the review text is paraphrased from the source. If set to *TRUE*, the review text will be surrounded automatically with quotation marks when displayed with the ad.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The system generated identifier of the account that contains the ad extension.

This bulk field maps to the *Id* field of the [Account](../bulk-api/account.md) record.

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  
  
### <a name="publishercountries"></a>Publisher Countries
The list of publisher countries whose editorial guidelines do not allow the specified [term](#editorialterm).

In a bulk file, the list of publisher countries are delimited with a semicolon (;).

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="source"></a>Source
The review source name.

The combined length of the *Source* and *Text* strings must not exceed 67 characters.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="startdate"></a>Start Date
The ad extension scheduled start date string formatted as *MM/DD/YYYY*.

The start date is inclusive. For example, if you set *StartDate* to 3/5/2017, the ad extensions will start being shown at 12:00 AM on 3/5/2017.

**Add:** Optional. If you do not specify a start date, the ad extensions are immediately eligible to be scheduled during the day and time ranges.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] The start date can be shortened or extended, as long as the end date is either null or occurs after the new start date. If you do not set this field, then the existing settings will be retained. If you set this field to *delete_value*, then you are effectively removing the start date and the ad extensions are immediately eligible to be scheduled during the day and time ranges.    
**Delete:** Read-only  

### <a name="status"></a>Status
The status of the ad extension.

Possible values are *Active* or *Deleted*. 

**Add:** Optional. The default value is *Active*.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Required. The Status must be set to *Deleted*.

### <a name="text"></a>Text
The text that is either a paraphrase or an exact quote from the review source.

The combined length of the *Source* and *Text* strings must not exceed 67 characters.

> [!NOTE]
> Do not surround the text with quotation marks. If the *Is Exact* field is set to *TRUE*, the review text will be surrounded automatically with quotation marks when displayed with the ad.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="url"></a>Url
The review source Url.

The Url must begin with either the *http://* or *https://* prefix.

The length of this string is limited to 2,048 characters.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="usesearchertimezone"></a>Use Searcher Time Zone
Determines whether to use the account time zone or the time zone of the search user where the ads could be delivered.

Set this property to *TRUE* if you want the ad extensions to be shown in the search user's time zone, and otherwise set it to *FALSE*.

**Add:** Optional. If you do not specify this field or leave it empty, the default value of *FALSE* will be set and the account time zone will be used.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] If you set this field to *delete_value*, then you are effectively resetting to the default value of *FALSE*.   
**Delete:** Read-only  

### <a name="version"></a>Version
The number of times the contents of the ad extension has been updated. The version is set to 1 when you add the extension and is incremented each time it's revised.

**Add:** Read-only  
**Update:** Read-only    
**Delete:** Read-only  


  

