---
title: "Price Ad Extension"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4080e572-333f-4924-9b1b-0b98b95174c7
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Price Ad Extension
Defines an ad extension that includes between 3 and 8 price table rows.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../bulk-api/includes/pilot-comingsoon.md)]

You can associate a price ad extension with one or more accounts, campaigns, and ad groups. Each account, campaign, or ad group can be associated with between 1 and 20 price ad extensions. 

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For a *Price Ad Extension* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Ad Schedule](#adschedule)
- [Client Id](#clientid)
- [Currency Code (1-8)](#currencycode)
- [Custom Parameter](#customparameter)
- [Editorial Location](#editoriallocation)
- [Editorial Reason Code](#editorialreasoncode)
- [Editorial Status](#editorialstatus)
- [Editorial Term](#editorialterm)
- [End Date](#enddate)
- [Final Mobile Url (1-8)](#finalmobileurl)
- [Final Url (1-8)](#finalurl)
- [Header (1-8)](#header)
- [Id](#id)
- [Language](#language)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Price (1-8)](#price)
- [Price Description (1-8)](#pricedescription)
- [Price Extension Type](#priceextensiontype)
- [Price Unit (1-8)](#priceunit)
- [Price Qualifier (1-8)](#pricequalifier)
- [Publisher Countries](#publishercountries)
- [Start Date](#startdate)
- [Status](#status)
- [Tracking Template](#trackingtemplate)
- [Use Searcher Time Zone](#usesearchertimezone)
- [Version](#version)

You can download all fields of the *Price Ad Extension* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *PriceAdExtensions* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](~/concepts/bulk-download-and-upload.md).

The following Bulk CSV example would add a new Price Ad Extension to the account's shared library. 

```csv
Type,Status,Id,Parent Id,Campaign,Ad Group,Client Id,Modified Time,Start Date,End Date,Device Preference,Name,Ad Schedule,Use Searcher Time Zone,Tracking Template,Custom Parameter,Price Extension Type,Currency Code 1,Currency Code 2,Currency Code 3,Currency Code 4,Currency Code 5,Currency Code 6,Currency Code 7,Currency Code 8,Price Description 1,Price Description 2,Price Description 3,Price Description 4,Price Description 5,Price Description 6,Price Description 7,Price Description 8,Header 1,Header 2,Header 3,Header 4,Header 5,Header 6,Header 7,Header 8,Final Mobile Url 1,Final Mobile Url 2,Final Mobile Url 3,Final Mobile Url 4,Final Mobile Url 5,Final Mobile Url 6,Final Mobile Url 7,Final Mobile Url 8,Final Url 1,Final Url 2,Final Url 3,Final Url 4,Final Url 5,Final Url 6,Final Url 7,Final Url 8,Price 1,Price 2,Price 3,Price 4,Price 5,Price 6,Price 7,Price 8,Price Qualifier 1,Price Qualifier 2,Price Qualifier 3,Price Qualifier 4,Price Qualifier 5,Price Qualifier 6,Price Qualifier 7,Price Qualifier 8,Price Unit 1,Price Unit 2,Price Unit 3,Price Unit 4,Price Unit 5,Price Unit 6,Price Unit 7,Price Unit 8
Format Version,,,,,,,,,,,5,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,
Price Ad Extension,,-24,,,,ClientIdGoesHere,,,,,,(Monday[09:00-21:00]),FALSE,,{_promoCode}=PROMO1; {_season}=summer,Events,USD,USD,USD,,,,,,Come to the event,Come to the next event,Come to the final event,,,,,,New Event,Next Event,Final Event,,,,,,,,,,,,,,https://contoso.com,https://contoso.com,https://contoso.com,,,,,,9.99,9.99,9.99,,,,,,From,From,From,,,,,,PerDay,PerDay,PerDay,,,,,

```

If you are using the [Bing Ads SDKs](~/concepts/bing-ads-client-libraries.md) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkPriceAdExtension* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkPriceAdExtension
var bulkPriceAdExtension = new BulkPriceAdExtension
{
    // 'Parent Id' column header in the Bulk file
    AccountId = 0,
    // 'Client Id' column header in the Bulk file
    ClientId = "ClientIdGoesHere",

    // Map properties in the Bulk file to the 
    // PriceAdExtension object of the Campaign Management service.
    PriceAdExtension = new PriceAdExtension
    {
        // 'Language' column header in the Bulk file
        Language = "English",
        // 'Id' column header in the Bulk file
        Id = priceAdExtensionIdKey,
        // 'Price Extension Type' column header in the Bulk file
        PriceExtensionType = PriceExtensionType.Events,

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
            EndDate = new Microsoft.BingAds.V11.CampaignManagement.Date
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

        // TableRows must include between 3 and 8 PriceTableRow
        TableRows = new PriceTableRow[]
        {
            // Each PriceTableRow is mapped to columns with suffix 1..8. 
            // This example shows 3 price table rows i.e., with column suffix from 1..3
            new PriceTableRow
            {
                // 'Currency Code 1' column header in the Bulk file
                CurrencyCode = "USD",
                // 'Price Description 1' column header in the Bulk file
                Description = "Come to the new event",
                // 'Final Url 1' column header in the Bulk file
                FinalUrls = new[] {
                    // Each Url is delimited by a semicolon (;) in the Bulk file
                    "http://www.contoso.com/womenshoesale"
                },
                // 'Final Mobile Url 1' column header in the Bulk file
                FinalMobileUrls = new[] {
                    // Each Url is delimited by a semicolon (;) in the Bulk file
                    "http://mobile.contoso.com/womenshoesale"
                },
                // 'Header 1' column header in the Bulk file
                Header = "New Event",
                // 'Price 1' column header in the Bulk file
                Price = 9.99,
                // 'Price Qualifier 1' column header in the Bulk file
                PriceQualifier = PriceQualifier.From,
                // 'Price Unit 1' column header in the Bulk file
                PriceUnit = PriceUnit.PerDay,
            },
            new PriceTableRow
            {
                // 'Currency Code 2' column header in the Bulk file
                CurrencyCode = "USD",
                // 'Price Description 2' column header in the Bulk file
                Description = "Come to the next event",
                // 'Final Url 2' column header in the Bulk file
                FinalUrls = new[] {
                    // Each Url is delimited by a semicolon (;) in the Bulk file
                    "http://www.contoso.com/womenshoesale"
                },
                // 'Final Mobile Url 2' column header in the Bulk file
                FinalMobileUrls = new[] {
                    // Each Url is delimited by a semicolon (;) in the Bulk file
                    "http://mobile.contoso.com/womenshoesale"
                },
                // 'Header 2' column header in the Bulk file
                Header = "Next Event",
                // 'Price 2' column header in the Bulk file
                Price = 9.99,
                // 'Price Qualifier 2' column header in the Bulk file
                PriceQualifier = PriceQualifier.From,
                // 'Price Unit 2' column header in the Bulk file
                PriceUnit = PriceUnit.PerDay,
            },
            new PriceTableRow
            {
                // 'Currency Code 3' column header in the Bulk file
                CurrencyCode = "USD",
                // 'Price Description 3' column header in the Bulk file
                Description = "Come to the final event",
                // 'Final Url 3' column header in the Bulk file
                FinalUrls = new[] {
                    // Each Url is delimited by a semicolon (;) in the Bulk file
                    "http://www.contoso.com/womenshoesale"
                },
                // 'Final Mobile Url 3' column header in the Bulk file
                FinalMobileUrls = new[] {
                    // Each Url is delimited by a semicolon (;) in the Bulk file
                    "http://mobile.contoso.com/womenshoesale"
                },
                // 'Header 3' column header in the Bulk file
                Header = "Final Event",
                // 'Price 3' column header in the Bulk file
                Price = 9.99,
                // 'Price Qualifier 3' column header in the Bulk file
                PriceQualifier = PriceQualifier.From,
                // 'Price Unit 3' column header in the Bulk file
                PriceUnit = PriceUnit.PerDay,
            },
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
    },
};

uploadEntities.Add(bulkPriceAdExtension);

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

### <a name="currencycode"></a>Currency Code (1-8)
The bulk file includes up to 8 currency code columns, i.e., one for each price table item in the ad extension. The bulk file column headers are *Currency Code 1*, *Currency Code 2*, *Currency Code 3*, *Currency Code 4*, *Currency Code 5*, *Currency Code 6*, *Currency Code 7*, and *Currency Code 8*. For more information, see [Currencies](~/concepts/currencies.md).

You must have between 3 and 8 price table items per price ad extension. All price table items for a price ad extension must be in the same bulk file record. Each price table item is mapped to the same index of [Currency Code](#currencycode), [Final Mobile Url](#finalmobileurl), [Final Url](#finalurl), [Header](#header), [Price](#price), [Price Description](#pricedescription), [Price Unit](#priceunit), and [Price Qualifier](#pricequalifier) columns. For example the first price table item is mapped to the *Currency Code 1*, *Final Mobile Url 1*, *Final Url 1*, *Header 1*, *Price 1*, *Price Description 1*, *Price Unit 1*, and *Price Qualifier 1* columns.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="customparameter"></a>Custom Parameter
Your custom collection of key and value parameters for URL tracking.

[!INCLUDE[validationrules_customparameters_bulk](../bulk-api/includes/validationrules-customparameters-bulk.md)]

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] To remove all custom parameters, set this field to *delete_value*. The *delete_value* keyword removes the previous setting. To remove a subset of custom parameters, specify the custom parameters that you want to keep and omit any that you do not want to keep. The new set of custom parameters will replace any previous custom parameter set.    
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

### <a name="finalmobileurl"></a>Final Mobile Url (1-8)
The bulk file includes up to 8 final mobile url columns, i.e., one for each price table item in the ad extension. The bulk file column headers are *Final Mobile Url 1*, *Final Mobile Url 2*, *Final Mobile Url 3*, *Final Mobile Url 4*, *Final Mobile Url 5*, *Final Mobile Url 6*, *Final Mobile Url 7*, and *Final Mobile Url 8*. 

[!INCLUDE[validationrules_finalurls_bulk](../bulk-api/includes/validationrules-finalurls-bulk.md)]

You must have between 3 and 8 price table items per price ad extension. All price table items for a price ad extension must be in the same bulk file record. Each price table item is mapped to the same index of [Currency Code](#currencycode), [Final Mobile Url](#finalmobileurl), [Final Url](#finalurl), [Header](#header), [Price](#price), [Price Description](#pricedescription), [Price Unit](#priceunit), and [Price Qualifier](#pricequalifier) columns. For example the first price table item is mapped to the *Currency Code 1*, *Final Mobile Url 1*, *Final Url 1*, *Header 1*, *Price 1*, *Price Description 1*, *Price Unit 1*, and *Price Qualifier 1* columns.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="finalurl"></a>Final Url (1-8)
The bulk file includes up to 8 final url columns, i.e., one for each price table item in the ad extension. The bulk file column headers are *Final Url 1*, *Final Url 2*, *Final Url 3*, *Final Url 4*, *Final Url 5*, *Final Url 6*, *Final Url 7*, and *Final Url 8*. 

The landing page URL to use with optional tracking template and custom parameters.

[!INCLUDE[validationrules_finalurls_bulk](../bulk-api/includes/validationrules-finalurls-bulk.md)]

Also note that  if the *Tracking Template* or *Custom Parameter* fields are set, then the final URL is required for each price table item.

You must have between 3 and 8 price table items per price ad extension. All price table items for a price ad extension must be in the same bulk file record. Each price table item is mapped to the same index of [Currency Code](#currencycode), [Final Mobile Url](#finalmobileurl), [Final Url](#finalurl), [Header](#header), [Price](#price), [Price Description](#pricedescription), [Price Unit](#priceunit), and [Price Qualifier](#pricequalifier) columns. For example the first price table item is mapped to the *Currency Code 1*, *Final Mobile Url 1*, *Final Url 1*, *Header 1*, *Price 1*, *Price Description 1*, *Price Unit 1*, and *Price Qualifier 1* columns.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="header"></a>Header (1-8)
The header that precedes the pricing data in your price ad extension. Each header can contain a maximum of 25 characters. Each header must tie directly to the *Price Extension Type* field for the price ad extension.

The bulk file includes up to 8 header columns, i.e., one for each price table item in the ad extension. The bulk file column headers are *Header 1*, *Header 2*, *Header 3*, *Header 4*, *Header 5*, *Header 6*, *Header 7*, and *Header 8*. 

You must have between 3 and 8 price table items per price ad extension. All price table items for a price ad extension must be in the same bulk file record. Each price table item is mapped to the same index of [Currency Code](#currencycode), [Final Mobile Url](#finalmobileurl), [Final Url](#finalurl), [Header](#header), [Price](#price), [Price Description](#pricedescription), [Price Unit](#priceunit), and [Price Qualifier](#pricequalifier) columns. For example the first price table item is mapped to the *Currency Code 1*, *Final Mobile Url 1*, *Final Url 1*, *Header 1*, *Price 1*, *Price Description 1*, *Price Unit 1*, and *Price Qualifier 1* columns.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="id"></a>Id
The system generated identifier of the ad extension.

**Add:** Optional. You must either leave this field empty, or specify a negative identifier. A negative identifier set for the ad extension can then be referenced in the *Id* field of dependent record types such as [Ad Group Price Ad Extension](../bulk-api/ad-group-price-ad-extension.md) and [Campaign Price Ad Extension](../bulk-api/campaign-price-ad-extension.md). This is recommended if you are adding new ad extensions and new dependent records in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="language"></a>Language
The language for the ad copy of your price ad extension.

For possible values, see [Ad Languages](~/concepts/ad-languages.md).

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

### <a name="price"></a>Price (1-8)
The price that you are advertising. 

The bulk file includes up to 8 price columns, i.e., one for each price table item in the ad extension. The bulk file column headers are *Price 1*, *Price 2*, *Price 3*, *Price 4*, *Price 5*, *Price 6*, *Price 7*, and *Price 8*. 

You must have between 3 and 8 price table items per price ad extension. All price table items for a price ad extension must be in the same bulk file record. Each price table item is mapped to the same index of [Currency Code](#currencycode), [Final Mobile Url](#finalmobileurl), [Final Url](#finalurl), [Header](#header), [Price](#price), [Price Description](#pricedescription), [Price Unit](#priceunit), and [Price Qualifier](#pricequalifier) columns. For example the first price table item is mapped to the *Currency Code 1*, *Final Mobile Url 1*, *Final Url 1*, *Header 1*, *Price 1*, *Price Description 1*, *Price Unit 1*, and *Price Qualifier 1* columns.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  
  
### <a name="pricedescription"></a>Price Description (1-8)
The description must provide further information about the header that is also defined in this object. Each description can contain a maximum of 25 characters.

The bulk file includes up to 8 price description columns, i.e., one for each price table item in the ad extension. The bulk file column headers are *Price Description 1*, *Price Description 2*, *Price Description 3*, *Price Description 4*, *Price Description 5*, *Price Description 6*, *Price Description 7*, and *Price Description 8*. 

You must have between 3 and 8 price table items per price ad extension. All price table items for a price ad extension must be in the same bulk file record. Each price table item is mapped to the same index of [Currency Code](#currencycode), [Final Mobile Url](#finalmobileurl), [Final Url](#finalurl), [Header](#header), [Price](#price), [Price Description](#pricedescription), [Price Unit](#priceunit), and [Price Qualifier](#pricequalifier) columns. For example the first price table item is mapped to the *Currency Code 1*, *Final Mobile Url 1*, *Final Url 1*, *Header 1*, *Price 1*, *Price Description 1*, *Price Unit 1*, and *Price Qualifier 1* columns.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="priceextensiontype"></a>Price Extension Type
The type of the price ad extension.

Possible values include: *Brands*, *Events*, *Locations*, *Neighborhoods*, *ProductCategories*, *ProductTiers*, *ServiceCategories*, *Services*, *ServiceTiers*, and *Unknown*. (Unknown is reserved for future use and cannot be set.)

**Add:** Required  
**Update:** Read-only   
**Delete:** Read-only  

### <a name="priceunit"></a>Price Unit (1-8)
The price unit.

Possible values include: *Average*, *From*, *UpTo*, *None*, and *Unknown*. (Unknown is reserved for future use and cannot be set.)

The bulk file includes up to 8 price unit columns, i.e., one for each price table item in the ad extension. The bulk file column headers are *Price Unit 1*, *Price Unit 2*, *Price Unit 3*, *Price Unit 4*, *Price Unit 5*, *Price Unit 6*, *Price Unit 7*, and *Price Unit 8*. 

You must have between 3 and 8 price table items per price ad extension. All price table items for a price ad extension must be in the same bulk file record. Each price table item is mapped to the same index of [Currency Code](#currencycode), [Final Mobile Url](#finalmobileurl), [Final Url](#finalurl), [Header](#header), [Price](#price), [Price Description](#pricedescription), [Price Unit](#priceunit), and [Price Qualifier](#pricequalifier) columns. For example the first price table item is mapped to the *Currency Code 1*, *Final Mobile Url 1*, *Final Url 1*, *Header 1*, *Price 1*, *Price Description 1*, *Price Unit 1*, and *Price Qualifier 1* columns.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="pricequalifier"></a>Price Qualifier (1-8)
The price qualifier.

Possible values include: *PerDay*, *PerHour*, *PerMonth*, *PerNight*, *PerWeek*, *PerYear*, *None*, and *Unknown*. (Unknown is reserved for future use and cannot be set.)

The bulk file includes up to 8 price unit columns, i.e., one for each price table item in the ad extension. The bulk file column headers are *Price Qualifier 1*, *Price Qualifier 2*, *Price Qualifier 3*, *Price Qualifier 4*, *Price Qualifier 5*, *Price Qualifier 6*, *Price Qualifier 7*, and *Price Qualifier 8*. 

You must have between 3 and 8 price table items per price ad extension. All price table items for a price ad extension must be in the same bulk file record. Each price table item is mapped to the same index of [Currency Code](#currencycode), [Final Mobile Url](#finalmobileurl), [Final Url](#finalurl), [Header](#header), [Price](#price), [Price Description](#pricedescription), [Price Unit](#priceunit), and [Price Qualifier](#pricequalifier) columns. For example the first price table item is mapped to the *Currency Code 1*, *Final Mobile Url 1*, *Final Url 1*, *Header 1*, *Price 1*, *Price Description 1*, *Price Unit 1*, and *Price Qualifier 1* columns.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="publishercountries"></a>Publisher Countries
The list of publisher countries whose editorial guidelines do not allow the specified [term](#editorialterm).

In a bulk file, the list of publisher countries are delimited with a semicolon (;).

**Add:** Read-only  
**Update:** Read-only  
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
The tracking template to use for your price table item URLs.

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
The number of times the contents of the ad extension has been updated. The version is set to 1 when you add the extension and is incremented each time it’s revised.

**Add:** Read-only  
**Update:** Read-only    
**Delete:** Read-only  

