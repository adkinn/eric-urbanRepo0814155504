---
title: "Bulk Download and Upload"
ms.custom: na
ms.date: "08/16/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: 37e84914-b0a0-4e53-907f-100faf9f4a1c
caps.latest.revision: 13
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Bulk Download and Upload
With the [bulk service](https://msdn.microsoft.com/library/bing-ads-bulk-service-reference.aspx) you can download and upload campaign settings asynchronously in the background. The Bulk service is recommended, especially if you need to add or update ads and keywords across multiple ad groups or campaigns in an account. For some entities you may also download bid suggestions and performance data. Each record can be uploaded successfully whether or not other records in the same file contain errors. For information about the schema used for the download and upload file, including details about which entities, bid estimates, and performance data are available, see [Bulk File Schema](https://msdn.microsoft.com/library/bing-ads-bulk-file-schema.aspx).

> [!IMPORTANT]
    > New record types (rows) and fields (columns) may be added anytime, and you should not depend on record or field order in the bulk download or bulk upload results file.

If you are using a .NET language, Java, or Python, you should use the [Bing Ads Client Libraries](../docset-overview/bing-ads-client-libraries.md). The .NET, Java, and Python SDKs abstract the low level details described below. For example instead of calling [DownloadCampaignsByAccountIds](https://msdn.microsoft.com/library/bing-ads-bulk-downloadcampaignsbyaccountids.aspx) and [GetBulkDownloadStatus](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkdownloadstatus.aspx) to download a file, you can use one method with the *BulkServiceManager* class. For more information about using Bulk download and upload with the SDKs, see [C#](../docset-overview/getting-started-using-csharp-with-bing-ads-services.md#bulkservicemanager) | [Java](../docset-overview/getting-started-using-java-with-bing-ads-services.md#bulkservicemanager) | [Python](../docset-overview/getting-started-using-python-with-bing-ads-services.md#bulkservicemanager).

For a code example that shows how to download and upload campaigns using the Bulk service with the workflow described below, see [Download and Upload Campaigns in PHP](../docset-overview/download-and-upload-campaigns-in-php.md).

## <a name="bulkdownload"></a>Bulk Download
To download an account’s campaign data, call the [DownloadCampaignsByAccountIds](https://msdn.microsoft.com/library/bing-ads-bulk-downloadcampaignsbyaccountids.aspx) operation. To download the data of specific campaigns, call the [DownloadCampaignsByCampaignIds](https://msdn.microsoft.com/library/bing-ads-bulk-downloadcampaignsbycampaignids.aspx) operation.

### Downloading a Bulk File
You may request all of the campaign’s data or only the data that has changed since the last time you downloaded the campaign’s data. For either download operation, the following is an overview of the request settings and download workflow.
  > [!IMPORTANT]
  > You must use the same user credentials for the download request operation (either [DownloadCampaignsByAccountIds](https://msdn.microsoft.com/library/bing-ads-bulk-downloadcampaignsbyaccountids.aspx) or [DownloadCampaignsByCampaignIds](https://msdn.microsoft.com/library/bing-ads-bulk-downloadcampaignsbycampaignids.aspx)) and the [GetBulkDownloadStatus](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkdownloadstatus.aspx) polling operation.
   
1.  Set the *DataScope* element of the request and specify whether to include performance data in addition to entity data. For a list of possible values, see the [DataScope](https://msdn.microsoft.com/library/bing-ads-bulk-datascope.aspx) value set.

    > [!NOTE]
    > If you are requesting performance data, then you must also set the start and end date within the *PerformanceStatsDateRange* element of the request.

2.  Set the *DownloadFileType* element of the request to select either **Csv** or **Tsv** for the format of the download file.

    > [!NOTE]
    > The downloaded **Csv** or **Tsv** file will be either ZIP or GZIP compressed depending on the *CompressionType* that you specified. ZIP is the default if you did not specify *CompressionType*.

3.  Set the *Entities* element of the request to include your campaign, ad group, ad, and keyword entities. You may optionally include additional entities such as negative keywords and targets in the download. For a list of entities that you may request, see the [BulkDownloadEntity](https://msdn.microsoft.com/library/bing-ads-bulk-bulkdownloadentity.aspx) value set.

4.  Set the *LastSyncTimeInUTC* element of the request to the time stamp of the previous download to request only those entities that have been updated or deleted since the last download.

    > [!NOTE]
    > If this is the first time that you are requesting a download for the specified entities, set the *LastSyncTimeInUTC* element of the request to NULL to download all available entities.

5.  Submit the download request with either the [DownloadCampaignsByAccountIds](https://msdn.microsoft.com/library/bing-ads-bulk-downloadcampaignsbyaccountids.aspx) or [DownloadCampaignsByCampaignIds](https://msdn.microsoft.com/library/bing-ads-bulk-downloadcampaignsbycampaignids.aspx) operation.

6.  The download request returns an identifier that you pass to the [GetBulkDownloadStatus](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkdownloadstatus.aspx) operation. You call the [GetBulkDownloadStatus](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkdownloadstatus.aspx) operation in a loop until the download completes or fails. The length of time that it takes the download to complete depends on a number of variables, such as the number of campaigns that you requested and the number of requests that are already in the queue. Because of these variables, the polling interval that you use may vary. You have two days to download the file from the time you submit the download request. If you have not successfully downloaded the file within this period, it is removed from the download site and you will need to call one of the download operations again.

7.  When the [GetBulkDownloadStatus](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkdownloadstatus.aspx) operation completes successfully, it returns the URL of the download file. Use the URL to copy the download file locally. The URL must be used within five minutes of the time that the [GetBulkDownloadStatus](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkdownloadstatus.aspx) operation returns a *Success* status code. If you do not start the download within this period of time, you will need to call [GetBulkDownloadStatus](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkdownloadstatus.aspx) again to get a new URL.

8.  The download file is compressed in zip format, so you must unzip the file to access the data. For information about the schema used for the download file, see [Bulk File Schema](https://msdn.microsoft.com/library/bing-ads-bulk-file-schema.aspx).

### Download Best Practices

-   Request only those bulk download entities that you require.

    > [!IMPORTANT]
    > New record types (rows) and fields (columns) may be added anytime, and you should not depend on record or field order in the bulk download or bulk upload results file.

-   Perform a full download one time only. Thereafter, perform delta downloads. Set the *LastSyncTimeInUTC* to the time stamp of the last download. The download file contains the time stamp of the download in the *SyncTime* column of the *Account* record. There is no advantage to performing a full download every time and it decreases everyone’s performance including yours.

-   Poll for downloads at reasonable intervals. You know your data better than anyone. If you download an account that is well less than one million keywords, consider polling at 15 to 20 second intervals. If the account contains about one million keywords, consider polling at one minute intervals after waiting five minutes. For accounts with about four million keywords, consider polling at one minute intervals after waiting 10 minutes.

-   Call the [DownloadCampaignsByCampaignIds](https://msdn.microsoft.com/library/bing-ads-bulk-downloadcampaignsbycampaignids.aspx) operation if the account contains more than four million keywords. Calling the [DownloadCampaignsByAccountIds](https://msdn.microsoft.com/library/bing-ads-bulk-downloadcampaignsbyaccountids.aspx) operation with an account that contains more than four million keywords will fail.

-   You may want to include fewer campaigns in your [DownloadCampaignsByCampaignIds](https://msdn.microsoft.com/library/bing-ads-bulk-downloadcampaignsbycampaignids.aspx) request. Calling the [DownloadCampaignsByCampaignIds](https://msdn.microsoft.com/library/bing-ads-bulk-downloadcampaignsbycampaignids.aspx) operation with an account that contains more than eight million keywords will fail. Requests that specify fewer campaigns per call typically complete sooner than calls that specify the maximum number allowed.

## <a name="bulkupload"></a>Bulk Upload
You can submit your bulk upload file with HTTP POST to a Url provided by the bulk service.

> [!NOTE]
> The file size limit for upload in production is 100MB and up to 4 million rows. For [Sandbox](../docset-overview/sandbox.md) the limit is 20K rows.

For information about the schema you should use for the upload file, see [Bulk File Schema](https://msdn.microsoft.com/library/bing-ads-bulk-file-schema.aspx).

### <a name="uploading"></a>Uploading a Bulk File
The following is an overview of the request settings and upload workflow.
  > [!IMPORTANT]
  > You must use the same user credentials throughout the [GetBulkUploadUrl](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadurl.aspx), HTTP POST, and [GetBulkUploadStatus](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadstatus.aspx) workflow.  

1.  Set the *AccountId* element of the [GetBulkUploadUrl](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadurl.aspx) request to the account identifier corresponding to the data that will be uploaded.

2.  Set the *ResponseMode* element of the [GetBulkUploadUrl](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadurl.aspx) request to specify whether the service should return errors and their corresponding data, or only the errors in the results file. For more information, see [ResponseMode](https://msdn.microsoft.com/library/bing-ads-bulk-responsemode.aspx).

3.  Use the *UploadUrl* returned with the [GetBulkUploadUrl](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadurl.aspx) response to submit your bulk upload file with HTTP POST. The content type must be *multipart/form-data*. UTF-8 files must include the byte order mark (BOM). The ZIP-compressed upload should contain one file formatted as either **Csv** or **Tsv**. The ZIP file must be properly structured, including an end of central directory record.

    > [!NOTE]
    > The HTTP standard Authorization header is not used. To authenticate you must add and set the [!INCLUDE[brand](../docset-overview/includes/brand.md)] custom header elements of your HTTP client, including the *DeveloperToken*, *CustomerId*, and *CustomerAccountId* headers. You must also set the user credentials header or headers. For [Authentication with OAuth](../docset-overview/authentication-with-oauth.md) you must set the *AuthenticationToken* header, otherwise to use the deprecated Bing Ads managed credentials you must set the *UserName* and *Password* headers. For more information, see [Where to Use the API Credentials](../docset-overview/getting-started-with-the-bing-ads-api.md#where_to_use).
    >
    > You must use the same user credentials throughout the [GetBulkUploadUrl](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadurl.aspx), HTTP POST, and [GetBulkUploadStatus](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadstatus.aspx) workflow.  

    Here is an example.

    ```
    POST <UploadUrl> HTTP/1.1
    AuthenticationToken: <AuthenticationToken>
    DeveloperToken: <DeveloperToken>
    CustomerId: <CustomerId>
    AccountId: <AccountId>
    Content-Type: multipart/form-data;
    ```

4.  Check the HTTP response status code. If the HTTP response status code is 200, then the file was received successfully by Bing Ads. If the HTTP response status code is 401, then authentication failed e.g. *UserName*, *Password*, *AuthenticationToken*, or *DeveloperToken* was invalid.  If the HTTP response status code is 400, then you should also check the response stream for [Bing Ads Operation Error Codes](../docset-overview/bing-ads-operation-error-codes.md) for example, in the range of 3220 - 3227. 

    Here is an example error response message that the URL had already been used to upload a bulk file.
    ```
    HTTP/1.1 400 Bad Request
    Cache-Control: private
    Content-Type: application/json; charset=utf-8
    Server: Microsoft-IIS/8.0
    X-AspNetMvc-Version: 3.0
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Tue, 12 Jan 2016 17:07:23 GMT
    Content-Length: 224

    {"TrackingId":"16bd93cc-22fb-4d3c-94be-25adefd06fae","RequestId":"26c3fbf6-3e24-4569-ada3-d4e8b3d0aecc","Code":3224,"ErrorCode":"BulkServiceUrlAlreadyUsedForUpload","Message":"The URL has already been used for file upload."}
    ```

5.  The [GetBulkUploadUrl](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadurl.aspx) response also includes a *RequestId* that you pass to the [GetBulkUploadStatus](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadstatus.aspx) operation. While the upload is pending, you may call the [GetBulkUploadStatus](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadstatus.aspx) operation in a loop until the upload completes or fails. You have two days to download the upload results file from the time you submit the upload request. If you have not successfully downloaded the file within this period, it is removed from the download site and it may not be retrieved. You could still call one of the download operations to get your updated entity data.

6.  When the [GetBulkUploadStatus](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadstatus.aspx) operation completes successfully, it returns the URL of the upload results file. Use the URL to copy the results file locally. The URL must be used within five minutes of the time that the [GetBulkUploadStatus](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadstatus.aspx) operation returns the *Completed* status response string. If you do not start the download within this period of time, you will need to call [GetBulkUploadStatus](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadstatus.aspx) again to get a new URL.

    > [!NOTE]
    > The format of the upload result file will be either **Csv** or **Tsv**, and will match the format of the file that you submitted for upload.

### <a name="uploadbestpractices"></a>Upload Best Practices
Please consider these tips to maximize Bulk upload performance.

-   Upload only the entities and fields that you are adding or updating. If supplied, read-only fields such as performance data will be ignored.

-   Upload one entity type e.g. Keyword per file. You can upload more than one entity per file; however this is a recommended best practice to maximize performance. 

-   Consider whether you need to request errors and results (*ResponseMode = ErrorsAndResults*) in the upload results file, or whether errors only (*ResponseMode = ErrorsOnly*) will suffice. Consider whether or not you should synchronize the results with your local data. For example if you are updating entities you might only need to know whether any errors occurred, and in that case you can specify *ResponseMode = ErrorsOnly* in the [GetBulkUploadUrl](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadurl.aspx) request. If you are adding new entities then you can specify *ResponseMode = ErrorsAndResults* in the [GetBulkUploadUrl](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadurl.aspx) request to receive the resulting entity identifiers.

-   For partial retry attempts, do not upload the entire file if only a subset of the records resulted in errors. Only upload the records that you want to retry. 

-   Do not retry until the upload status is either *Completed*, *CompletedwithErrors*, or *Failed*. If by chance performance does not meet expectations, please wait for the result anyways. 

-   Poll for upload results at reasonable intervals. Initially you should wait one minute for every 10K rows uploaded. After the initial wait time, consider polling in one minute intervals.

-   It is optional and recommended that the file be compressed for upload. If compressed it must be formatted as ZIP with the corresponding extension.

-   Consider using up to 5 or 6 threads to upload files in parallel. Wait on each thread until the previous file was processed, and then you can reuse the thread to upload another file. For example, one thread can upload a file and after the upload status is either *Completed*, *CompletedwithErrors*, or *Failed* that thread can upload another file. 

## See Also
[Bulk Service Reference](https://msdn.microsoft.com/library/bing-ads-bulk-service-reference.aspx)  
[Bing Ads Web Service Addresses](../docset-overview/bing-ads-web-service-addresses.md)

