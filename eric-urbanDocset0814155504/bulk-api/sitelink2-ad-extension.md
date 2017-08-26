---
title: "Sitelink2 Ad Extension"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e0b02fc-7db9-40ad-97ba-f55364837c3f
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Sitelink2 Ad Extension
Defines a sitelink2 ad extension that can be downloaded and uploaded in a bulk file.

The *Sitelink2 Ad Extension* record adheres to the single sitelink data model, where each Sitelink2 Ad Extension has *one* sitelink. The entire Sitelink2 Ad Extension is represented as a single *Sitelink2 Ad Extension* record in the bulk file.

> [!IMPORTANT]
> [!INCLUDE[sitelinks_migration_eta](../bulk-api/includes/sitelinks-migration-eta.md)]    

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For a *Sitelink2 Ad Extension* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Ad Schedule](#adschedule)
- [Client Id](#clientid)
- [Custom Parameter](#customparameter)
- [Device Preference](#devicepreference)
- [Editorial Location](#editoriallocation)
- [Editorial Reason Code](#editorialreasoncode)
- [Editorial Status](#editorialstatus)
- [Editorial Term](#editorialterm)
- [End Date](#enddate)
- [Final Url](#finalurl)
- [Id](#id)
- [Mobile Final Url](#mobilefinalurl)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Publisher Countries](#publishercountries)
- [Sitelink Extension Description1](#sitelinkextensiondescription1)
- [Sitelink Extension Description2](#sitelinkextensiondescription2)
- [Sitelink Extension Destination Url](#sitelinkextensiondestinationurl)
- [Sitelink Extension Link Text](#sitelinkextensionlinktext)
- [Start Date](#startdate)
- [Status](#status)
- [Tracking Template](#trackingtemplate)
- [Use Searcher Time Zone](#usesearchertimezone)
- [Version](#version)

You can download all fields of the *Sitelink2 Ad Extension* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *Sitelink2AdExtensions* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](~/concepts/bulk-download-and-upload.md).

The following Bulk CSV example would add a new Sitelink2 Ad Extension to the account's shared library. 

```csv
Type,Status,Id,Parent Id,Campaign,Ad Group,Client Id,Modified Time,Start Date,End Date,Device Preference,Name,Ad Schedule,Use Searcher Time Zone,Sitelink Extension Order,Sitelink Extension Link Text,Sitelink Extension Destination Url,Sitelink Extension Description1,Sitelink Extension Description2,Final Url,Mobile Final Url,Tracking Template,Custom Parameter
Format Version,,,,,,,,,,,5,,,,,,,,,,,
Sitelink2 Ad Extension,Active,-17,0,,,ClientIdGoesHere,,,12/31/2018,,,(Monday[09:00-21:00]),FALSE,,Women's Shoe Sale 1,,Simple & Transparent.,No Upfront Cost.,http://www.contoso.com/womenshoesale,http://mobile.contoso.com/womenshoesale,,{_promoCode}=PROMO1; {_season}=summer
```

If you are using the [Bing Ads SDKs](~/concepts/bing-ads-client-libraries.md) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkSitelink2AdExtension* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkSitelink2AdExtension
var bulkSitelink2AdExtension = new BulkSitelink2AdExtension
{
    // 'Parent Id' column header in the Bulk file
    AccountId = 0,
    // 'Client Id' column header in the Bulk file
    ClientId = "ClientIdGoesHere",
                
    // Map properties in the Bulk file to the 
    // Sitelink2AdExtension object of the Campaign Management service.
    Sitelink2AdExtension = new Sitelink2AdExtension
    {
        // 'Id' column header in the Bulk file
        Id = sitelink2AdExtensionIdKey,
        // 'Sitelink Extension Description1' column header in the Bulk file
        Description1 = "Simple & Transparent.",
        // 'Sitelink Extension Description2' column header in the Bulk file
        Description2 = "No Upfront Cost.",
        // 'Text' column header in the Bulk file
        DisplayText = "Women's Shoe Sale",
        // 'Destination Url' column header in the Bulk file
        DestinationUrl = "",
        // 'Final Url' column header in the Bulk file
        FinalUrls = new[] {
            // Each Url is delimited by a semicolon (;) in the Bulk file
            "http://www.contoso.com/womenshoesale"
        },
        // 'Mobile Final Url' column header in the Bulk file
        FinalMobileUrls = new[] {
            // Each Url is delimited by a semicolon (;) in the Bulk file
            "http://mobile.contoso.com/womenshoesale"
        },
        // 'Tracking Template' column header in the Bulk file
        TrackingUrlTemplate = null,
        // 'Custom Parameter' column header in the Bulk file
        UrlCustomParameters = new CustomParameters
        {
            // Each custom parameter is delimited by a semicolon (;) in the Bulk file
            Parameters = new[] {
                new CustomParameter(){
                    Key = "promoCode",
                    Value = "PROMO1"
                },
                new CustomParameter(){
                    Key = "season",
                    Value = "summer"
                },
            }
        },

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

uploadEntities.Add(bulkSitelink2AdExtension);

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

### <a name="customparameter"></a>Custom Parameter
Your custom collection of key and value parameters for URL tracking.

[!INCLUDE[validationrules_customparameters_bulk](../bulk-api/includes/validationrules-customparameters-bulk.md)]

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] To remove all custom parameters, set this field to *delete_value*. The *delete_value* keyword removes the previous setting. To remove a subset of custom parameters, specify the custom parameters that you want to keep and omit any that you do not want to keep. The new set of custom parameters will replace any previous custom parameter set.    
**Delete:** Read-only  

### <a name="devicepreference"></a>Device Preference
This field determines whether the preference is for the ad extension to be displayed on mobile devices or all devices.

Possible values are *All* and *Mobile*, which differ from values used in the campaign management service. 

The default value is *All*.

In the bulk download and upload results file, this field will never be empty. If you did not specify a device preference, the default value of *All* will be returned.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] If you set this field to *delete_value*, then you are effectively resetting to the default value of *All*.    
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

### <a name="finalurl"></a>Final Url
The landing page URL to use with optional tracking template and custom parameters.

[!INCLUDE[validationrules_finalurls_bulk](../bulk-api/includes/validationrules-finalurls-bulk.md)]

Also note that  if the *Tracking Template* or *Custom Parameter* fields are set, then the *Final Url* is required.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_delete_all](../bulk-api/includes/update-optional-delete-all.md)]    
**Delete:** Read-only  

### <a name="id"></a>Id
The system generated identifier of the ad extension.

**Add:** Optional. You must either leave this field empty, or specify a negative identifier. A negative identifier set for the ad extension can then be referenced in the *Id* field of dependent record types such as [Ad Group Sitelink2 Ad Extension](../bulk-api/ad-group-sitelink2-ad-extension.md) and [Campaign Sitelink2 Ad Extension](../bulk-api/campaign-sitelink2-ad-extension.md). This is recommended if you are adding new ad extensions and new dependent records in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="mobilefinalurl"></a>Mobile Final Url
[!INCLUDE[validationrules_finalurls_bulk](../bulk-api/includes/validationrules-finalurls-bulk.md)]

Also note that you may not specify *Mobile Final Url* if the *Device Preference* is set to *Mobile*.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_delete_all](../bulk-api/includes/update-optional-delete-all.md)]    
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

### <a name="sitelinkextensiondescription1"></a>Sitelink Extension Description1
The site link description line 1.

The maximum input length is 35 characters. If any Traditional Chinese characters are included, the limit is 15 characters.

> [!NOTE]
> Starting the week of September 18th, the limit will be relaxed such that only the Traditional Chinese characters will be counted double against the character limit. Each Traditional Chinese character will count as two and each English character will count only as one character.

> [!NOTE]
> If you specify *Sitelink Extension Description1* then *Sitelink Extension Description2* is required.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="sitelinkextensiondescription2"></a>Sitelink Extension Description2
The site link description line 2.

The maximum input length is 35 characters. If any Traditional Chinese characters are included, the limit is 15 characters.

> [!NOTE]
> Starting the week of September 18th, the limit will be relaxed such that only the Traditional Chinese characters will be counted double against the character limit. Each Traditional Chinese character will count as two and each English character will count only as one character.

> [!NOTE]
> If you specify *Sitelink Extension Description2* then *Sitelink Extension Description1* is required.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="sitelinkextensiondestinationurl"></a>Sitelink Extension Destination Url
The URL of the webpage that users are taken to when they click the site link.

The URL can contain dynamic parameters such as {MatchType}. For a list of supported parameters, see the Available parameters section within the Bing Ads help article [How do I set up destination URL tracking?](https://help.bingads.microsoft.com/#apex/3/en/51091/2).

The URL can contain a maximum of 1,024 characters. If the URL does not specify a protocol, the system uses the HTTP protocol when a user clicks the ad. If the URL specifies the HTTP protocol when you add an ad, the service will remove the http:// protocol string (the HTTP protocol string does not count against the 1,024 character limit); however, the service will not remove an HTTPS protocol string (https://) from the URL.

> [!IMPORTANT]
> If you are currently using Destination URLs, you must eventually replace them with Final URLs. For more information, see [URL Tracking with Upgraded URLs](~/concepts/url-tracking-with-upgraded-urls.md).

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_delete_all](../bulk-api/includes/update-optional-delete-all.md)]    
**Delete:** Read-only  

### <a name="sitelinkextensionlinktext"></a>Sitelink Extension Link Text
The site-link text displayed in the ad.

If you specify *Sitelink Extension Description1* or *Sitelink Extension Description2* then the display text can contain a maximum of 25 characters; otherwise, the display text can contain a maximum of 35 characters. If any Traditional Chinese characters are included, the limits are 11 characters given *Sitelink Extension Description1* or *Sitelink Extension Description2*, and 15 characters otherwise.

> [!NOTE]
> Starting the week of September 18th, the limit will be relaxed such that only the Traditional Chinese characters will be counted double against the character limit. Each Traditional Chinese character will count as two and each English character will count only as one character.

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

### <a name="trackingtemplate"></a>Tracking Template
The tracking template to use for your sitelink URLs.

[!INCLUDE[validationrules_trackingurltemplate](../bulk-api/includes/validationrules-trackingurltemplate.md)]

**Add:** Optional  
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
