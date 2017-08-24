# Bing Ads Content API
Bing Ads Content API is a RESTful API that allows advertisers to programmatically 
manage their [Bing Merchant Center](http://help.bingads.microsoft.com/#apex/3/en/51083/1) catalogs. The Content API is an alternative to managing your catalog using the Bing Merchant Center web page or by using FTP. The Content API has the following advantages:

-   Provides the ability to update product offers incrementally rather than uploading the entire data feed. Being able to update  a subset of your products is more efficient than having to upload the entire feed by using FTP.

-   Provides the ability to make changes to product pricing and availability to reflect close to real-time market conditions. For example, if your product goes out of stock, you can quickly update its Availability field using the Content API.

-   Provides the ability to batch together large numbers of items to process in a single request. A batch operation can include inserts, deletes, and updates. Using batch operations is a more efficient use of resources than using single operation calls (for example, a single insert operation).

-   Provides the ability to download catalog status reports.

- Provides the ability to manage your catalogs programmatically.


## Who Should Use the API?
You should consider using the Content API if:

-   You are currently using the Google Content API. 

-   Your feed includes a large number of products.

-   You are able to integrate the Content API with the rest of your inventory management systems.

If your catalog is small, or you have a limited ability to integrate with your inventory systems, you may be better off using one of the other methods for uploading your catalog (see [Submit your feed file](http://help.bingads.microsoft.com/#apex/3/en/51086/1)).



## In This Section

|Topic|Description|
|---------|---------------|
|[Release Notes](../content-api/release-notes.md)|Describes changes to the Bing Ads Content API for each release.|
|[Getting Started](../content-api/getting-started.md)|Provides the steps for getting started using the Bing Ads Content API.|
|[Testing your Code in Sandbox](../content-api/testing-your-code-in-sandbox.md)|Provides options for testing your app before releasing it into production.|
|[API Best Practices](../content-api/api-best-practices.md)|Provides best practices for using the Bing Ads Content API.|
|[Managing your Products](../content-api/managing-your-products.md)|Provides details for how to use the [Products](../content-api/products-resource.md) resource to add, get, update, and delete product offers.|
|[Managing your Catalogs](../content-api/managing-your-catalogs.md)|Provides details for how to use the [Catalogs](../content-api/catalogs-resource.md) resource to add, get, update, and delete API enabled catalogs.|
|[How Do I Get the Status of Product Offers?](../content-api/how-do-i-get-the-status-of-product-offers.md)|Provides details for how to use the [Status](../content-api/catalogs-resource.md) resource to get the status of product offers in a catalog.|
|[Code Examples](../content-api/code-examples.md)|Provides C# code examples that show how to use Bing Ads Content API resources.|
|[Content API Reference](../content-api/content-api-reference.md)|Provides details about the programming elements of the Bing Ads Content API.|
