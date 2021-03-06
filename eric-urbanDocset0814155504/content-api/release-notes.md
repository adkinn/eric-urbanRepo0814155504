---
title: "Release Notes"
ms.custom: ""
ms.date: "07/27/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5e8de63-912c-47f7-835b-8fbad1ab0564
caps.latest.revision: 16
author: "eric-urban"
ms.author: "rongrant"
manager: "ehansen"
---
# Release Notes
This topic describes recent changes made to Version 9.1 of the Content API.

## July 2017

This release includes the following changes:

- Removed all references to version 9.0 from the document. Version 9.0 is no longer supported. 

## <a name="may2017"></a>May 2017
This release includes the following changes:

- The following [Product](http://msdn.microsoft.com/en-us/e431640b-fa1a-4161-8272-8b962b72ee7a) fields are now required if the manufacturer assigns them.  
  
  - [brand](http://msdn.microsoft.com/en-us/e431640b-fa1a-4161-8272-8b962b72ee7a) 
  - [gtin](http://msdn.microsoft.com/en-us/e431640b-fa1a-4161-8272-8b962b72ee7a) 
  - [mpn](http://msdn.microsoft.com/en-us/e431640b-fa1a-4161-8272-8b962b72ee7a)  
  
  If the manufacturer assigns values for these fields, you must specify them in your offer. If you do not, BMC will accept the offer for now but will return a warning message in the response (see [warnings](http://msdn.microsoft.com/en-us/e431640b-fa1a-4161-8272-8b962b72ee7a)). You should update your code at your earliest convenience to begin providing this information.  
  
- If you do not specify the `brand`, `gtin`, or `mpn` fields, you must set the [identifierExists](http://msdn.microsoft.com/en-us/e431640b-fa1a-4161-8272-8b962b72ee7a) field to **false**. It's default is **true**.  
  
- Added the `warnings` field to the [BatchItemError](http://msdn.microsoft.com/en-us/e431640b-fa1a-4161-8272-8b962b72ee7a) object.

 
## <a name="march2017"></a>March 2017
This release includes the following changes:

- Updated the documentation to reflect that your BMC store and catalogs are automatically enabled to use the Content API. You no longer have to use the Bing Ads web application to enable your store and catalogs to use the API.  

## <a name="february2017"></a>February 2017
This release includes the following changes:

- Updated the `Product` object's [availability](../content-api/products-resource.md#availability) field to accept *out of stock* and *preorder* values. Only users in the pilot program may specify these values.


## <a name="september2016"></a>September 2016
This release includes the following changes:

- Added the [promotionId](../content-api/products-resource.md#promotionid) field to the `Product` object. You use the promotion ID to associate a product offer with a promotion in your Promotions feed.
- Updated the [price](../content-api/products-resource.md#price) and [saleprice](../content-api/products-resource.md#saleprice) fields of the `Product` object to allow a minimum price of 0.0 (zero) under certain conditions. Previously, the minimum price allowed was 0.01 (1 cent).
 
## <a name="December2015"></a>December 2015
For information about the changes to the Content API  services included in this release, see the following section.

-   [Catalogs Management Resource](#catalogsmanagement)

### <a name="catalogsmanagement"></a>Catalogs Management Resource
This release introduces the `catalogs` resource.

For an overview and reference information about the `catalogs` resource see the topic [Catalogs Management Resource](../content-api/catalogs-resource.md). Code examples will be available in a forthcoming release.

## <a name="October2015"></a>October 2015
For information about the changes to the Content API  services included in this release, see the following sections.

-   [Status Resource](#staturesource_october2015)

-   [Documentation Reorganization](#docreorg_october2015)

### <a name="staturesource_october2015"></a>Status Resource
This release introduces the `status` resource.

For an overview and reference information about the `status` resource see the topic [Catalog Status Resource](../content-api/status-resource.md).

For an example of using the `status` resource in code see the topic [Catalog Status Resource Code Examples](../content-api/code-examples.md#catalog).

### <a name="docreorg_october2015"></a>Documentation Reorganization
The Content API was previously documented as "Version 1" and "Version 2". To make the Bing Ads API documentation consistent, the version number used in documentation has been changed to use the version in the URI.

## <a name="April2015"></a>April 2015
For information about the changes to the Content API  services included in this release, see the following sections.

-   [Products Resource](#productresource_april2015)

### <a name="productresource_april2015"></a>Products Resource
The April 2015 release updated the `products` resource to version 9.1.

Version 9 (previously version 1) of the products resource will be deprecated. Use version 9.1.

For general information about the `products` resource see the topic [Products Resource Overview](../Topic/Products%20Resource%20Overview.md).

Version 9.1 of the Content API's `products` resource was previously documented as version 2. [Products Resource](../content-api/products-resource.md)

Version 9 of the Content API's `products` resource was previously documented as version 1. [Products API Version 9](../Topic/Products%20API%20Version%209.md).

