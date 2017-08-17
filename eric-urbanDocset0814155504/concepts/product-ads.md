---
title: "Product Ads"
ms.custom: ""
ms.date: "07/28/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5376e19c-97f1-430e-8a31-c6036cbb7cb5
caps.latest.revision: 15
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Product Ads
A [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaign enables you to advertise the products from your [!INCLUDE[storebrand](../concepts/includes/storebrand.md)] store product catalog. Product ads from a [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaign include details about the product, an image, and optional promotional text.

You can manage [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] settings with either the [Bulk Service](https://msdn.microsoft.com/library/jj134984.aspx) or [Campaign Management Service](https://msdn.microsoft.com/library/bb671719.aspx). You should use the [Bulk Service](https://msdn.microsoft.com/library/jj134984.aspx) if you need to upload or download a high volume of entity settings. For example you can update all ad groups for your entire account in a single upload. In comparison, with the [Campaign Management Service](https://msdn.microsoft.com/library/bb671719.aspx) you can only update 100 ad groups per call and those ad groups must be in the same campaign. For details see the following sections. 

-   [Setup Bing Merchant Center](#setup)

-   [Create a Bing Shopping Campaign with the Bulk Service](#bingshopping_bulkservice)

-   [Create a Bing Shopping Campaign with the Campaign Management Service](#bingshopping_campaignservice)

-   [Product Conditions](#conditions)

-   [Performance Statistics for Bing Shopping Campaigns](#reports)


## <a name="setup"></a>Setup Bing Merchant Center
To create a [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaign, follow these steps.

1.  Set up the customer’s [!INCLUDE[storebrand](../concepts/includes/storebrand.md)] store. In the [!INCLUDE[brand](../concepts/includes/brand.md)] web application, click **Tools** &gt; **Bing Merchant Center**. Click on **Create store** and provide the requested store details. For information about setting up your store catalog, see [Create a Bing Merchant Center store](https://help.bingads.microsoft.com/#apex/3/en/51085/1-500) and [How is the feed file organized](https://help.bingads.microsoft.com/#apex/3/en/51084/1).

2.  [Create a product catalog](https://help.bingads.microsoft.com/#apex/3/en/51105/1-500), and then submit the catalog feed via [FTP](https://help.bingads.microsoft.com/#apex/3/en/51086/1-500) or the [Bing Ads Content API](https://msdn.microsoft.com/library/bing-ads-content-api.aspx).

3.  Get your [!INCLUDE[storebrand](../concepts/includes/storebrand.md)] store unique system identifier. Call [GetBMCStoresByCustomerId](https://msdn.microsoft.com/library/dn411607.aspx) and get the *StoreId* from of one of the returned [BMCStore](https://msdn.microsoft.com/library/dn411606.aspx) objects, or in the [!INCLUDE[brand](../concepts/includes/brand.md)] web application, click **Tools** &gt; **Bing Merchant Center** to access your store details.

After you complete these steps, you can follow the steps to [Create a Bing Shopping Campaign with the Campaign Management Service](#bingshopping_campaignservice).

## <a name="bingshopping_bulkservice"></a>Create a Bing Shopping Campaign with the Bulk Service
The [Bulk Service](https://msdn.microsoft.com/library/jj134984.aspx) create, update, and delete operations can be completed using Bulk upload. You can use Bulk download to read back your data. For more information see [Bulk File Schema](https://msdn.microsoft.com/library/dn539651.aspx) and [Bulk Download and Upload](../concepts/bulk-download-and-upload.md).

These are the [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] entities that can be accessed using the [Bulk Service](https://msdn.microsoft.com/library/jj134984.aspx).

-   [Campaign](https://msdn.microsoft.com/library/dn764752.aspx)
-   [Campaign Product Scope](https://msdn.microsoft.com/library/cc540192.aspx)
-   [Ad Group](https://msdn.microsoft.com/library/dn764731.aspx)
-   [Ad Group Product Partition](https://msdn.microsoft.com/library/cc540184.aspx)
-   [Product Ad](https://msdn.microsoft.com/library/dn764755.aspx)

For code examples that show how to apply product conditions for [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaigns using the Bulk service, see [C&#35;](../concepts/bulk-shopping-campaigns-in-csharp.md) | [Java](../concepts/bulk-shopping-campaigns-in-java.md) | [Python](../concepts/bulk-shopping-campaigns-in-python.md).

To create a [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaign, follow these steps.

1.  Create one or more [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaigns.

    > [!TIP]
    > You must create designated campaigns for [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)]. You may not create text ads in your [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaigns.

    -   Set the *Campaign Type* field of the [Campaign](https://msdn.microsoft.com/library/dn764752.aspx) to *Shopping*.

    -   Set the *Priority* field of the [Campaign](https://msdn.microsoft.com/library/dn764752.aspx) to 0, 1, or 2.

    -   Set the *COUNTRY_CODE* field of the [Campaign](https://msdn.microsoft.com/library/dn764752.aspx).

    -   Set the *Store Id* field of the [Campaign](https://msdn.microsoft.com/library/dn764752.aspx).

2.  Optionally, you can upload a [Campaign Product Scope](https://msdn.microsoft.com/library/cc540192.aspx) criterion that will be associated with your [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaign. Use the product scope criterion to include a subset of your product catalog, for example a specific brand, category, or product type. A campaign can only be associated with one [Campaign Product Scope](http://msdn.microsoft.com/library/76c8e7db-3ef7-4f46-a514-eedd729455f7), which contains a list of up to 7 product conditions. You'll also be able to specify more specific product conditions for each ad group.

    > [!NOTE]
    > Product conditions may be returned by [!INCLUDE[brand](../concepts/includes/brand.md)] services in a different order from the order that you submitted.

3.  Upload an [Ad Group](https://msdn.microsoft.com/library/dn764731.aspx) and set its *Parent Id* field to the *Id* of the campaign added above.

4.  Upload one or more [Ad Group Product Partition](https://msdn.microsoft.com/library/cc540184.aspx) records which represent product partition nodes in a tree structure that will be used to further refine the product catalog offers. Duplicate or conflicting product conditions attempted within an ad group's product partition group will be rejected by the upload operation; however, the operation will not validate whether duplicate or conflicting conditions already exist within the campaign level [Campaign Product Scope](https://msdn.microsoft.com/library/cc540192.aspx). For example given one ad group and one campaign, the [Campaign Product Scope](https://msdn.microsoft.com/library/cc540192.aspx) and [Ad Group Product Partition](https://msdn.microsoft.com/library/cc540184.aspx) may each have *Product Condition 1* set to CategoryL1 and *Product Value 1* set to Animals &amp; Pet Supplies, and the service will not throw any error or warning for a duplicate condition.

    > [!NOTE]
    > There is a 1 to 1 relationship between ad groups and product groups. In other words, each ad group has one product group and vice versa. In the [!INCLUDE[brand](../concepts/includes/brand.md)] web application, for each ad group you would add one product group with multiple levels of division or multiple partitions. This is the equivalent of adding ad group level product partitions using the [!INCLUDE[brand](../concepts/includes/brand.md)] API. 

    Please also consider the following validation rules for uploading [Ad Group Product Partition](https://msdn.microsoft.com/library/cc540184.aspx) records.

    -   At minimum you must specify at least the root node for the product partition group tree structure. The product partition group's root node must have its *Product Condition 1* field set to "All" and *Product Value 1* null or empty. If you are bidding on all products in the catalog equally, set the *Sub Type* field to *Unit*. If you are partitioning the bids based on more specific product conditions, then set the *Sub Type* field to *Subdivision*, the *Parent Criterion Id* to null or empty, and the *Id* to a negative value. You will use the negative value as *Parent Criterion Id* for any child nodes.

    -   The root node is considered level 0, and a tree can have branches up to 7 levels deep.

    -   Per upload request, you can include a maximum of 20,000 product partition tree nodes per ad group. The entire product partition tree node count for an ad group cannot exceed 20,000.

    -   The product partition tree nodes for the same tree (same ad group) must be grouped together in the file.

    -   The order of the product partition nodes is not guaranteed during download, and parent nodes might be provided after child nodes; however, all nodes for the same ad group will be grouped together in the file.

    -   If you are creating or modifying the tree structure, parent product partition tree nodes must be ordered ahead of the child product partition tree nodes ; however, the order does not matter for non-structural changes such as updating the bid. For example if you want to update the bids without adding, deleting, or updating the tree structure, then you only need to upload the *Id*, *Parent Id*, and *Bid* fields.

    -   To update the *Product Condition 1*, *Product Value 1* or *Is Excluded* field, you must delete the existing product partition tree node and upload a new product partition tree node which will get a new identifier.

    -   If any action fails, all remaining actions that might have otherwise succeeded will be rejected.

    -   All product partition node addition and deletion actions must result in a complete tree structure.

    -   Every path from the root node to the end of a branch must terminate with a leaf node (*Sub Type*=Unit). Every Unit must have a bid, unless the *Is Excluded* field is TRUE which means that the node is a negative ad group criterion.

    -   Every subdivision must have at least one leaf node that bids on the remainder of the subdivision's conditions, i.e. use the same operand as its sibling unit(s) and set its *Product Value 1* null or empty.

    -   If you are adding partitions with multiple levels where neither the parent or child yet exist, use a negative int value as a reference to identify the parent. For example set the both the parent's *Id*, and the child's *Parent Criterion Id* field to the same negative value. The negative IDs are only valid for the duration of the call. Unique system identifiers for each successfully added ad group criterion are returned in the upload result file.

    -   The *Bid* and *Destination Url* fields are only applicable if the *Is Excluded* field is FALSE which means that the node is a biddable ad group criterion. However, these fields are ignored for *Subdivision* partition nodes. Those elements are only relevant for *Unit* (leaf) partition nodes.

    -   To pause any product partition you must pause the entire ad group by updating the *Status* field of the [Ad Group](https://msdn.microsoft.com/library/dn764731.aspx) to Paused. You can pause the entire campaign by updating the *Status* field of the [Campaign](https://msdn.microsoft.com/library/dn764752.aspx) to Paused.

    -   For a *Deleted* action you only need to specify the *Id* and *Parent Id*.

    -   If you delete a parent product partition, all of its children and descendants will also be deleted.

    -   You may not specify duplicate product conditions in a branch. For more information, see [Product Conditions](#conditions).

5.  Upload a product ad. You must add at least one [Product Ad](https://msdn.microsoft.com/library/dn764755.aspx) to the corresponding ad group. A [Product Ad](https://msdn.microsoft.com/library/dn764755.aspx) is not used directly for delivered ad copy. Instead, the delivery engine generates product ads from the product details that it finds in your [!INCLUDE[storebrand](../concepts/includes/storebrand.md)] store's product catalog. The primary purpose of the [Product Ad](https://msdn.microsoft.com/library/dn764755.aspx) object is to provide promotional text that the delivery engine adds to the product ads that it generates. For example, if the promotional text is set to “Free shipping on $99 purchases”, the delivery engine will set the product ad’s description to “Free shipping on $99 purchases.”

After you complete these steps, the delivery engine can begin serving product ads for the products that it finds in the customer’s [!INCLUDE[storebrand](../concepts/includes/storebrand.md)] store. If the user’s search query has product intent, the delivery engine searches the customer’s [!INCLUDE[storebrand](../concepts/includes/storebrand.md)] store for products that matches the query. If it finds a product, and the product meets the conditions of the product filters specified in the product scope and product partitions, the delivery engine generates a product ad using the product details from the store.

## <a name="bingshopping_campaignservice"></a>Create a Bing Shopping Campaign with the Campaign Management Service
These are the [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] entities that can be accessed using the [Campaign Management Service](https://msdn.microsoft.com/library/bb671719.aspx). You can create, read, update, and delete these entities.

> [!NOTE]
> Partial success is supported for a subset of these operations. For example if you submit 10 ad groups and 2 fail, the remaining 8 will succeed. For more information, see [Partial Success using the Campaign Management Service](../concepts/handling-service-errors-and-exceptions.md#partialsuccess).

|Entities|Service Operations|
|------------|----------------------|
|[Campaign](https://msdn.microsoft.com/library/bb672054.aspx)|[AddCampaigns](https://msdn.microsoft.com/library/dn277510.aspx)<br /><br />[DeleteCampaigns](https://msdn.microsoft.com/library/dn236314.aspx)<br /><br />[GetCampaignsByAccountId](https://msdn.microsoft.com/library/dn236299.aspx)<br /><br />[GetCampaignsByIds](https://msdn.microsoft.com/library/dn236303.aspx)<br /><br />[UpdateCampaigns](https://msdn.microsoft.com/library/dn277536.aspx)|
|[ProductScope](https://msdn.microsoft.com/library/dn913124.aspx)|[AddCampaignCriterions](https://msdn.microsoft.com/library/dn913127.aspx)<br /><br />[DeleteCampaignCriterions](https://msdn.microsoft.com/library/dn913125.aspx)<br /><br />[GetCampaignCriterionsByIds](https://msdn.microsoft.com/library/dn913135.aspx)<br /><br />[UpdateCampaignCriterions](https://msdn.microsoft.com/library/dn913121.aspx)|
|[AdGroup](https://msdn.microsoft.com/library/bb671956.aspx)|[AddAdGroups](https://msdn.microsoft.com/library/dn277502.aspx)<br /><br />[DeleteAdGroups](https://msdn.microsoft.com/library/dn236307.aspx)<br /><br />[GetAdGroupsByCampaignId](https://msdn.microsoft.com/library/dn277524.aspx)<br /><br />[GetAdGroupsByIds](https://msdn.microsoft.com/library/dn277529.aspx)<br /><br />[UpdateAdGroups](https://msdn.microsoft.com/library/dn277528.aspx)|
|[ProductAd](https://msdn.microsoft.com/library/jj738612.aspx)|[AddAds](https://msdn.microsoft.com/library/dn277506.aspx)<br /><br />[GetAdsByAdGroupId](https://msdn.microsoft.com/library/dn277534.aspx)<br /><br />[DeleteAds](https://msdn.microsoft.com/library/dn236310.aspx)<br /><br />[GetAdsByEditorialStatus](https://msdn.microsoft.com/library/dn277538.aspx)<br /><br />[GetAdsByIds](https://msdn.microsoft.com/library/dn236296.aspx)<br /><br />[UpdateAds](https://msdn.microsoft.com/library/dn277531.aspx)|
|[BiddableAdGroupCriterion](https://msdn.microsoft.com/library/jj689538.aspx)<br /><br />**Note:** Currently the only supported [BiddableAdGroupCriterion](https://msdn.microsoft.com/library/jj689538.aspx) is used for a [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaign [ProductPartition](https://msdn.microsoft.com/library/dn913123.aspx). You cannot update or delete a product partition, so [ApplyProductPartitionActions](https://msdn.microsoft.com/library/dn913134.aspx) is used for all write operations. [AddAdGroupCriterions](https://msdn.microsoft.com/library/dn277499.aspx), [DeleteAdGroupCriterions](https://msdn.microsoft.com/library/dn236302.aspx), and [UpdateAdGroupCriterions](https://msdn.microsoft.com/library/dn277527.aspx) operations are not supported for managing [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaigns.|[ApplyProductPartitionActions](https://msdn.microsoft.com/library/dn913134.aspx)<br /><br />[GetAdGroupCriterionsByIds](https://msdn.microsoft.com/library/dn277520.aspx)

For code examples that show how to apply product conditions for [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaigns using the Campaign Management service, see [C&#35;](../concepts/shopping-campaigns-in-csharp.md) | [Java](../concepts/shopping-campaigns-in-java.md) | [PHP](../concepts/shopping-campaigns-in-php.md) | [Python](../concepts/shopping-campaigns-in-python.md).

To create a [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaign, follow these steps.

1.  Create one or more [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaigns.

    > [!TIP]
    > You must create designated campaigns for [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)]. You may not create text ads in your [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaigns.

    -   Set the *CampaignType* element of the [Campaign](https://msdn.microsoft.com/library/bb672054.aspx) to *Shopping*.

    -   Create a [ShoppingSetting](https://msdn.microsoft.com/library/dn913132.aspx) instance and set its *Priority* (0, 1, or 2), *SalesCountryCode*, and *StoreId* elements. Add this shopping setting to the *Settings* list of the [Campaign](https://msdn.microsoft.com/library/bb672054.aspx).

2.  Optionally, you can create a [ProductScope](https://msdn.microsoft.com/library/dn913124.aspx) criterion that will be associated with your [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaign. Use the product scope criterion to include a subset of your product catalog, for example a specific brand, category, or product type. A campaign can only be associated with one *ProductScope*, which contains a list of up to 7 [ProductCondition](https://msdn.microsoft.com/library/jj721705.aspx). You'll also be able to specify more specific product conditions for each ad group.

    Call the [AddCampaignCriterions](https://msdn.microsoft.com/library/dn913127.aspx) operation to associate the [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaign with your product scope criterion.

    > [!NOTE]
    > Product conditions may be returned by [!INCLUDE[brand](../concepts/includes/brand.md)] services in a different order from the order that you submitted.

3.  Create an [AdGroup](https://msdn.microsoft.com/library/bb671956.aspx) and add it to the campaign by calling [AddAdGroups](https://msdn.microsoft.com/library/dn277502.aspx).

4.  Create a list of [AdGroupCriterionAction](https://msdn.microsoft.com/library/dn913128.aspx) objects in a tree structure that will be used to further refine the product catalog offers. Apply the list of actions by calling [ApplyProductPartitionActions](https://msdn.microsoft.com/library/dn913134.aspx). Duplicate or conflicting product conditions attempted within an ad group's product partition group will be rejected by the [ApplyProductPartitionActions](https://msdn.microsoft.com/library/dn913134.aspx) operation; however, the operation will not validate whether duplicate or conflicting conditions already exist within the campaign level [ProductScope](https://msdn.microsoft.com/library/dn913124.aspx).

    > [!NOTE]
    > To retrieve product partitions after they have been applied, call [GetAdGroupCriterionsByIds](https://msdn.microsoft.com/library/dn277520.aspx) and set the *AdGroupCriterionIds* element to *null* to get all product partitions for the ad group. The product partition with *ParentCriterionId* set to *null* is the root node.

    Please also consider the following validation rules for the [ApplyProductPartitionActions](https://msdn.microsoft.com/library/dn913134.aspx) operation.

    -   At minimum you must specify at least the root node for the product partition group tree structure. The product partition group's root [BiddableAdGroupCriterion](https://msdn.microsoft.com/library/jj689538.aspx) must have its condition *Operand* set to "All" and *Attribute* to *null*. If you are bidding on all products in the catalog equally, set the *PartitionType* to Unit. If you are partitioning the bids based on more specific product conditions, then set the *PartitionType* to Subdivision, the *ParentCriterionId* to *null*, and the *Id* to a negative value. You will use the negative value as *ParentCriterionId* for any child nodes.

    -   The root node is considered level 0, and a tree can have branches up to 7 levels deep.

    -   You may specify up to 5,000 [AdGroupCriterionAction](https://msdn.microsoft.com/library/dn913128.aspx) objects per call. The entire tree created through multiple calls can have up to 20,000 nodes.

    -   Each of the [AdGroupCriterionAction](https://msdn.microsoft.com/library/dn913128.aspx) objects must have the same *AdGroupId*, otherwise the call will fail.
    
    -   To update the *Condition* or *Attribute* properties, you must delete the existing product partition tree node and add a new product partition tree node which will get a new identifier. Likewise to update from a [BiddableAdGroupCriterion](https://msdn.microsoft.com/library/jj689538.aspx) to a [NegativeAdGroupCriterion](https://msdn.microsoft.com/library/dn913133.aspx) or vice versa, you must delete the existing product partition tree node and add a new product partition tree node which will get a new identifier. 

    -   If any action fails, all remaining actions that might have otherwise succeeded will be rejected.

    -   All actions in one call must result in a complete tree structure. If you need to apply more than 5,000 actions per ad group, you must make multiple calls. Get the parent ad group criterion identifiers from the first call, and then add more children as needed in subsequent calls.

    -   Every path from the root node to the end of a branch must terminate with a leaf node (*ProductPartitionType*=Unit). Every Unit must have a bid, unless the node is a [NegativeAdGroupCriterion](https://msdn.microsoft.com/library/dn913133.aspx).

    -   Every subdivision must have at least one leaf node that bids on the remainder of the subdivision's conditions, i.e. use the same operand as its sibling unit(s) and set its *Attribute* to *null*.

    -   You may only specify a child node after its parent.

    -   If you are adding partitions with multiple levels where neither the parent or child yet exist, use a negative int value as a reference to identify the parent. For example set the both the parent's *Id*, and the child's *ParentCriterionId* element to the same negative value. The negative IDs are only valid for the duration of the call. Unique system identifiers for each successfully added ad group criterion are returned in the response message.

    -   The *CriterionBid* and *DestinationUrl* elements of the [BiddableAdGroupCriterion](https://msdn.microsoft.com/library/jj689538.aspx) are ignored for *Subdivision* partition nodes. Those elements are only relevant for *Unit* (leaf) partition nodes.

    -   The *Status* element of the *AdGroupCriterion* is always ignored for product partition criterion. To add, update, or delete a product partition, set the *Action* element of the corresponding [AdGroupCriterionAction](https://msdn.microsoft.com/library/dn913128.aspx).

    -   To pause any product partition you must pause the entire ad group by calling [UpdateAdGroups](https://msdn.microsoft.com/library/dn277528.aspx). You can call [UpdateCampaigns](https://msdn.microsoft.com/library/dn277536.aspx) to pause the entire campaign.

    -   The *EditorialStatus* element of the *AdGroupCriterion* has no significant meaning for product partition criterion. Editorial validation for the product catalog is completed in the [!INCLUDE[storebrand](../concepts/includes/storebrand.md)] store.

    -   For a *Delete* action you only need to specify the *Id* and *AdGroupId* in the  *AdGroupCriterion*.

    -   If you delete a parent product partition, all of its children and descendants will also be deleted.

    -   You may not specify duplicate product conditions in a branch. For more information, see [Product Conditions](#conditions).

5.  Create a product ad. You must add at least one [ProductAd](https://msdn.microsoft.com/library/jj738612.aspx) to the corresponding ad group. A *ProductAd* is not used directly for delivered ad copy. Instead, the delivery engine generates product ads from the product details that it finds in your [!INCLUDE[storebrand](../concepts/includes/storebrand.md)] store's product catalog. The primary purpose of the *ProductAd* object is to provide promotional text that the delivery engine adds to the product ads that it generates. For example, if the promotional text is set to “Free shipping on $99 purchases”, the delivery engine will set the product ad’s description to “Free shipping on $99 purchases.”

    To create a product ad, instantiate a *ProductAd* object and set the *PromotionalText* element as needed. If you do not want to add promotional text to your ads, set *PromotionalText* to null or an empty string. Next, call the [AddAds](https://msdn.microsoft.com/library/dn277506.aspx) operation to add the product ad to an ad group.

After you complete these steps, the delivery engine can begin serving product ads for the products that it finds in the customer’s [!INCLUDE[storebrand](../concepts/includes/storebrand.md)] store. If the user’s search query has product intent, the delivery engine searches the customer’s [!INCLUDE[storebrand](../concepts/includes/storebrand.md)] store for products that matches the query. If it finds a product, and the product meets the conditions of the product filters specified in the product scope and product partitions, the delivery engine generates a product ad using the product details from the store.

## <a name="conditions"></a>Product Conditions
Multiple product conditions can be specified for each campaign and ad group. Each condition is met if the product’s attribute value equals the operand’s attribute value. For example, if *Operand* is set to Brand and *Attribute* is set to Contoso, the condition is met if the value of the product catalog's Brand attribute is equal to Contoso.

The following table maps the operand names to the corresponding attribute string restrictions for campaign product scope and ad group product partition.

|Operand Name|Attribute Description|ProductScope Rules|ProductPartition Rules|
|----------------|-------------------------|----------------------|--------------------------|
|All|Must be null.|Not applicable.|For an ad group's product partitions, the root node must have *Operand* set to *"All"* and *Attribute* set to *null*.|
|Brand|The product's manufacturer, brand, or publisher.<br /><br />A maximum of 1,000 characters.|The *Brand* operand may only be specified once per campaign product scope filter.|The *Brand* operand may be used in multiple branches, but may only be specified once per branch.|
|Condition|The condition of the product.<br /><br />If *Operand* is set to Condition, the supported attribute values that you can specify are *New*, *Used*, and *Refurbished*.|The *Condition* operand may only be specified once per campaign product scope filter.|The *Condition* operand may be used in multiple branches, but may only be specified once per branch.|
|Id|The product identifier defined by the merchant.<br /><br />A maximum of 1,000 characters.|The *Id* operand may only be specified once per campaign product scope filter.|The *Id* operand may be used in multiple branches, but may only be specified once per branch.|
|CategoryL1-5<br /><br />**Note:** Five category operand values are available i.e. CategoryL1, CategoryL2, CategoryL3, CategoryL4, and CategoryL5.|A product category defined by the [!INCLUDE[storebrand](../concepts/includes/storebrand.md)] store. Please see [Bing Category Taxonomy](http://go.microsoft.com/fwlink?LinkId=507666) for valid category values and taxonomy.<br /><br />CategoryL0 is the highest level category, and CategoryL4 is the lowest level or most granular category.<br /><br />A maximum of 100 characters.|Each of the *CategoryL* operands may be used once per campaign product scope filter.<br /><br />If you specify a product condition with *Operand* set to a product category from 1 through 5,<br /> they must be specified in ascending order. For example you can specify *Operand="CategoryL2"*, *Attribute="Pet Supplies"*, if a preceding product condition has the *Operand="CategoryL1"*, *Attribute="Animals & Pet Supplies"* condition.|Each of the *CategoryL* operands may be used in multiple branches, but may only be specified once per branch. For example one branch may contain *CategoryL1* and *CategoryL2*, but may not contain another node with the *CategoryL2* operand.<br /><br />If you specify a product condition with *Operand* set to a product category from 1 through 5, they must be specified in ascending order. For example you can specify *Operand="CategoryL2"*, *Attribute="Pet Supplies"*, if a higher level product partition has the *Operand="CategoryL1"*, *Attribute="Animals & Pet Supplies"* condition.<br /><br/>The prior level product category operand doesn't need to be specified in the immediate parent partition. For example a CategoryL2 condition could be specified for a product partition if the parent of its parent criterion specified a CategoryL1 condition.|
|ProductType1-5<br /><br />**Note:** Five product type operand values are available i.e. ProductType1, ProductType2, ProductType3, ProductType4, and ProductType5.|A product type or category defined by the merchant.<br /><br />ProductType1 is the highest level product type, and ProductType5 is the lowest level or most granular product type.<br /><br />A maximum of 100 characters.|Each of the product type operands may be used once per campaign product scope filter.<br /><br />If you specify a product condition with *Operand* set to a product type from 1 through 5,<br />they must be specified in ascending order. For example you can specify *Operand="ProductType2"*, *Attribute="Pet Supplies"*, if a preceding product condition has the *Operand="ProductType1"*, *Attribute="Animals & Pet Supplies"* condition.|Each of the *ProductType* operands may be used in multiple branches, but may only be specified once per branch. For example one branch may contain *ProductType1* and *ProductType2*, but may not contain another node with the *ProductType2* operand.<br /><br />If you specify a product condition with *Operand* set to a product type from 1 through 5, they must be specified in ascending order. For example you can specify *Operand="ProductType2"*, *Attribute="Pet Supplies"*, if a higher level product partition has the *Operand="ProductType1"*, *Attribute="Animals & Pet Supplies"* condition.<br /><br/>The prior level product type operand doesn't need to be specified in the immediate parent partition. For example a ProductType2 condition could be specified for a product partition if the parent of its parent criterion specified a ProductType1 condition.|
|CustomLabel0-4<br /><br />**Note:** Five custom label operand values are available i.e. CustomLabel0, CustomLabel1, CustomLabel2, CustomLabel3, and CustomLabel4.|A custom label defined by the merchant.<br /><br />Custom labels e.g. CustomLabel0 and CustomLabel4 are not validated based on any hierarchy.<br /><br />A maximum of 100 characters.|Each of the *CustomLabel* operands may be used once per campaign product scope filter.|Each of the *CustomLabel* operands may be used in multiple branches, but may only be specified once per branch. For example one branch may contain *CustomLabel0* and *CustomLabel1*, but may not contain another node with the *CustomLabel1* operand.|

## <a name="reports"></a>Performance Statistics for Bing Shopping Campaigns
The following reports can be submitted and downloaded with the [Reporting Service](https://msdn.microsoft.com/library/bb671732.aspx) to get performance data for [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaigns.

|Report Name|Description|Reporting Service Programming Elements|
|---------------|---------------|------------------------------------------|
|Product Dimension|Defines a product dimension performance report request that aggregates the performance data by product category, custom label, title, and type for a specified time period. You can include details in the report such as impressions, clicks, and spend that you can use to identify whether or not the [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] products are performing well.|[ProductDimensionPerformanceReportRequest](https://msdn.microsoft.com/library/dn913141.aspx)<br /><br />[ProductDimensionPerformanceReportFilter](https://msdn.microsoft.com/library/dn913139.aspx)<br /><br />[ProductDimensionPerformanceReportColumn](https://msdn.microsoft.com/library/dn913140.aspx)|
|Product Partition|Defines a product partition performance report request that aggregates the performance data by product group and product partition type for a specified time period. You can include details in the report such as impressions, clicks, and spend that you can use to identify whether or not the [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] products are performing well.|[ProductPartitionPerformanceReportRequest](https://msdn.microsoft.com/library/dn913138.aspx)<br /><br />[ProductPartitionPerformanceReportFilter](https://msdn.microsoft.com/library/dn913143.aspx)<br /><br />[ProductPartitionPerformanceReportColumn](https://msdn.microsoft.com/library/dn913142.aspx)|
|Product Partition Unit|Defines a product partition unit performance report request that aggregates the performance data by product partition unit for a specified time period. You can include details in the report such as impressions, clicks, and spend that you can use to identify whether or not the product partitions are performing well.|[ProductPartitionUnitPerformanceReportRequest](https://msdn.microsoft.com/library/mt592960.aspx)<br /><br />[ProductPartitionUnitPerformanceReportFilter](https://msdn.microsoft.com/library/mt592961.aspx)<br /><br />[ProductPartitionUnitPerformanceReportColumn](https://msdn.microsoft.com/library/mt592967.aspx)|
If you request a report using account level scope, then the performance reports will include aggregated data for all campaigns, whether or not the campaign type is [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)]. To only get data for [!INCLUDE[brand_bsc](../concepts/includes/brand-bsc.md)] campaigns, use campaign scope or ad group scope. The following is an example SOAP request that specifies campaign level scope.

```xml
<Scope>
    \<AccountIds i:nil="true" xmlns:a="http://schemas.microsoft.com/2003/10/Serialization/Arrays" />
    \<AdGroups i:nil="true" />
    <Campaigns>
    <CampaignReportScope>
        <AccountId>AccountIdGoesHere</AccountId>
        <CampaignId>CampaignIdGoesHere</CampaignId>
    </CampaignReportScope>
    </Campaigns>
</Scope>
```
For more information about using the [Reporting Service](https://msdn.microsoft.com/library/bb671732.aspx), see [Reports](../concepts/reports.md) and [Request and Download a Report](../concepts/request-and-download-a-report.md).

When you download entities with the [Bulk Service](https://msdn.microsoft.com/library/jj134984.aspx), if the [DataScope](https://msdn.microsoft.com/library/dn249976.aspx) element of the download request includes *EntityPerformanceData*, the download file will also include performance statistics for most of the record types listed in [Create a Bing Shopping Campaign with the Bulk Service](#bingshopping_bulkservice). The tree root [Ad Group Product Partition](https://msdn.microsoft.com/library/cc540184.aspx) record contains performance statistics for the entire tree, the [Ad Group Product Partition](https://msdn.microsoft.com/library/cc540184.aspx) record corresponding to each subdivision contains the performance statistics of all leaf nodes under it, and the [Ad Group Product Partition](https://msdn.microsoft.com/library/cc540184.aspx) record corresponding to each unit contains performance statistics only for that specific node.

> [!NOTE]
> Performance statistics returned by the Bulk and Reporting services lags behind the performance statistics that you see in the [!INCLUDE[brand](../concepts/includes/brand.md)] web application by up to an hour. Please note the following differences between the [Bulk Service](https://msdn.microsoft.com/library/jj134984.aspx) and [Reporting Service](https://msdn.microsoft.com/library/bb671732.aspx) with respect to the freshness of the tree structure and performance statistics.
> 
> -   If you have modified your product partition tree structure within the last hour, the tree structure of your product partitions will always be up to date in the [Bulk Service](https://msdn.microsoft.com/library/jj134984.aspx) download. Only the *Ad Group Product Partition* record that represents you tree root node will contain performance statistics fields such as impressions and clicks, which may lag behind the performance statistics that you see in the [!INCLUDE[brand](../concepts/includes/brand.md)] web application by up to an hour.
> -   If you have modified your product partition tree structure within the last hour, both the performance statistics and the tree structure of your product partitions returned in a report through the [Reporting Service](https://msdn.microsoft.com/library/bb671732.aspx) may lag behind the data that you see in the [!INCLUDE[brand](../concepts/includes/brand.md)] web application by up to an hour.

 