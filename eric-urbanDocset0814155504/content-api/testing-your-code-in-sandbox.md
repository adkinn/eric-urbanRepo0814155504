---
title: "Testing your Code in Sandbox"
ms.custom: ""
ms.date: "05/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e214e92c-885b-4673-b15b-0c6157ad25ba
caps.latest.revision: 12
author: "eric-urban"
ms.author: "rongrant"
manager: "ehansen"
---
# Testing your Code in Sandbox
Bing Ads does not provide a sandbox for the Content API where you can test your application before you deploy it to the production environment. 

However, you can use the following options to test your application in production without affecting live data. These options apply only to the [Products](../content-api/products-resource.md) resource and not to the [Catalogs](../content-api/catalogs-resource.md) resource.

### Using dry-run query parameter

To test your code in  production without modifying your live feed and impacting served ads, include the [dry-run](../content-api/products-resource.md#dryrun) query parameter in the endpoint URL as shown below. 

`https://content.api.bingads.microsoft.com/shopping/v9.1/bmc/{bmcMerchantId}/products/{itemUniqueId}?dry-run` 

Using `dry-run` will not change your live feed, but it will return validation errors.

Because data is not stored in the database when using the dry-run parameter, consider the following limitations when using this option:
* Insert operations will not return an ID
* The service will not generate and return secondary error messages such as data quality, editorial issues, and database related validations

Note that the Catalogs resource does not support the `dry-run` query parameter.

### Disabling publishing

Another option is to disable a catalog's ability to publish content. Catalogs that are disabled will not serve ads. This allows you to perform operations against the catalog and capture any errors that occur.  

To disable a catalog in the Bing Ads web application, select the catalog from the **Catalog management** tab. Then, on the **Catalog settings** tab, deselect **Enable publishing**. 

You may also use the [Catalogs](../content-api/catalogs-resource.md) resource to disable publishing. For details see, [Managing your Catalogs](../content-api/managing-your-catalogs.md).

As with using the `dry-run` query parameter, secondary error messages such as data quality, editorial issues, and database related validations are not generated and will not be returned. However, Insert operations will return IDs.

> [!CAUTION]
> Products are unique within a store, not a catalog. If you have a product with the same [id](../content-api/products-resource.md#productid) in more than one catalog, then any changes that you make to the product in the disabled catalog will also occur in the enabled catalogs. This means that even with publishing disabled in one catalog, another catalog may serve ads for that product. 
