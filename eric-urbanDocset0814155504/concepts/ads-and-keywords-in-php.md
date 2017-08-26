---
title: "Ads and Keywords in PHP"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c68b0a8-6eab-4183-841b-e4fe5c54e988
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ads and Keywords in PHP
The following example shows how to add ads and keywords to a new ad group, and handle partial errors when some ads or keywords are not successfully created.

[!INCLUDE[php_header](../concepts/includes/php-header.md)]

```php
<?php

namespace Microsoft\BingAds\Samples\v11;

// For more information about installing and using the Bing Ads PHP SDK, 
// see https://go.microsoft.com/fwlink/?linkid=838593.

require_once "/../vendor/autoload.php";

include "/../AuthHelper.php";

use SoapVar;
use SoapFault;
use Exception;

//Specify the Microsoft\BingAds\v11\CampaignManagement classes that will be used.
use Microsoft\BingAds\v11\CampaignManagement\AddBudgetsRequest;
use Microsoft\BingAds\v11\CampaignManagement\GetBudgetsByIdsRequest;
use Microsoft\BingAds\v11\CampaignManagement\GetCampaignIdsByBudgetIdsRequest;
use Microsoft\BingAds\v11\CampaignManagement\UpdateBudgetsRequest;
use Microsoft\BingAds\v11\CampaignManagement\DeleteBudgetsRequest;
use Microsoft\BingAds\v11\CampaignManagement\AddCampaignsRequest;
use Microsoft\BingAds\v11\CampaignManagement\DeleteCampaignsRequest;
use Microsoft\BingAds\v11\CampaignManagement\GetCampaignsByAccountIdRequest;
use Microsoft\BingAds\v11\CampaignManagement\GetCampaignsByIdsRequest;
use Microsoft\BingAds\v11\CampaignManagement\UpdateCampaignsRequest;
use Microsoft\BingAds\v11\CampaignManagement\AddAdGroupsRequest;
use Microsoft\BingAds\v11\CampaignManagement\AddKeywordsRequest;
use Microsoft\BingAds\v11\CampaignManagement\DeleteKeywordsRequest;
use Microsoft\BingAds\v11\CampaignManagement\GetKeywordsByAdGroupIdRequest;
use Microsoft\BingAds\v11\CampaignManagement\UpdateKeywordsRequest;
use Microsoft\BingAds\v11\CampaignManagement\AddAdsRequest;
use Microsoft\BingAds\v11\CampaignManagement\GetAdsByAdGroupIdRequest;
use Microsoft\BingAds\v11\CampaignManagement\UpdateAdsRequest;
use Microsoft\BingAds\v11\CampaignManagement\Budget;
use Microsoft\BingAds\v11\CampaignManagement\Campaign;
use Microsoft\BingAds\v11\CampaignManagement\CampaignType;
use Microsoft\BingAds\v11\CampaignManagement\CampaignAdditionalField;
use Microsoft\BingAds\v11\CampaignManagement\KeywordAdditionalField;
use Microsoft\BingAds\v11\CampaignManagement\IdCollection;
use Microsoft\BingAds\v11\CampaignManagement\AdGroup;
use Microsoft\BingAds\v11\CampaignManagement\Keyword;
use Microsoft\BingAds\v11\CampaignManagement\Ad;
use Microsoft\BingAds\v11\CampaignManagement\AdType;
use Microsoft\BingAds\v11\CampaignManagement\ExpandedTextAd;
use Microsoft\BingAds\v11\CampaignManagement\Bid;
use Microsoft\BingAds\v11\CampaignManagement\BiddingScheme;
use Microsoft\BingAds\v11\CampaignManagement\MatchType;
use Microsoft\BingAds\v11\CampaignManagement\BudgetLimitType;
use Microsoft\BingAds\v11\CampaignManagement\AdDistribution;
use Microsoft\BingAds\v11\CampaignManagement\Date;
use Microsoft\BingAds\v11\CampaignManagement\CustomParameters;
use Microsoft\BingAds\v11\CampaignManagement\CustomParameter;
use Microsoft\BingAds\v11\CampaignManagement\EnhancedCpcBiddingScheme;
use Microsoft\BingAds\v11\CampaignManagement\InheritFromParentBiddingScheme;
use Microsoft\BingAds\v11\CampaignManagement\ManualCpcBiddingScheme;

// Specify the Microsoft\BingAds\v11\CustomerManagement classes that will be used.
use Microsoft\BingAds\v11\CustomerManagement\GetUserRequest;
use Microsoft\BingAds\v11\CustomerManagement\SearchAccountsRequest;
use Microsoft\BingAds\v11\CustomerManagement\Paging;
use Microsoft\BingAds\v11\CustomerManagement\Predicate;
use Microsoft\BingAds\v11\CustomerManagement\PredicateOperator;
use Microsoft\BingAds\v11\CustomerManagement\Account;
use Microsoft\BingAds\v11\CustomerManagement\User;

// Specify the Microsoft\BingAds\Auth classes that will be used.
use Microsoft\BingAds\Auth\ServiceClient;
use Microsoft\BingAds\Auth\ServiceClientType;

// Specify the Microsoft\BingAds\Samples classes that will be used.
use Microsoft\BingAds\Samples\AuthHelper;

$GLOBALS['AuthorizationData'] = null;
$GLOBALS['Proxy'] = null;
$GLOBALS['CustomerProxy'] = null; 
$GLOBALS['CampaignProxy'] = null; 

// Disable WSDL caching.

ini_set("soap.wsdl_cache_enabled", "0");
ini_set("soap.wsdl_cache_ttl", "0");

try
{
    // You should authenticate for Bing Ads production services with a Microsoft Account, 
    // instead of providing the Bing Ads username and password set. 
    
    //AuthHelper::AuthenticateWithOAuth();

    // However, authentication with a Microsoft Account is currently not supported in Sandbox,
    // so it is recommended that you set the UserName and Password in sandbox for testing.

    AuthHelper::AuthenticateWithUserName();

    $GLOBALS['CustomerProxy'] = new ServiceClient(ServiceClientType::CustomerManagementVersion11, $GLOBALS['AuthorizationData'], AuthHelper::GetApiEnvironment());

    // Set the GetUser request parameter to an empty user identifier to get the current 
    // authenticated Bing Ads user, and then search for all accounts the user may access.

    $user = GetUser(null);

    // For this example we'll use the first account.

    $accounts = SearchAccountsByUserId($user->Id);
    $GLOBALS['AuthorizationData']->AccountId = $accounts->Account[0]->Id;
    $GLOBALS['AuthorizationData']->CustomerId = $accounts->Account[0]->ParentCustomerId;

    $GLOBALS['CampaignProxy'] = new ServiceClient(ServiceClientType::CampaignManagementVersion11, $GLOBALS['AuthorizationData'], AuthHelper::GetApiEnvironment());

    // Let's create a new budget and share it with a new campaign.

    $budgetIds = array();
    $budgets = array();
    $budget = new Budget();
    $budget->Amount = 50;
    $budget->BudgetType = BudgetLimitType::DailyBudgetStandard;
    $budget->Name = "My Shared Budget " . $_SERVER['REQUEST_TIME'];
    
    $budgets[] = $budget;
    $budgetIds = AddBudgets($budgets)->BudgetIds;
                
    // Specify one or more campaigns.
    
    $campaigns = array();
   
    $campaign = new Campaign();
    $campaign->Name = "Winter Clothing " . $_SERVER['REQUEST_TIME'];
    $campaign->Description = "Winter clothing line.";
    // You must choose to set either the shared  budget ID or daily amount.
    // You can set one or the other, but you may not set both.
    $campaign->BudgetId = count($budgetIds) > 0 ? $budgetIds->long[0] : null;
    $campaign->DailyBudget = count($budgetIds) > 0 ? 0 : 50;
    $campaign->BudgetType = BudgetLimitType::DailyBudgetStandard;
    $campaign->TimeZone = "PacificTimeUSCanadaTijuana";
    $campaign->DaylightSaving = true;
    
    // You can set your campaign bid strategy to Enhanced CPC (EnhancedCpcBiddingScheme) 
    // and then, at any time, set an individual ad group or keyword bid strategy to 
    // Manual CPC (ManualCpcBiddingScheme).
    // For campaigns you can use either of the EnhancedCpcBiddingScheme or ManualCpcBiddingScheme objects. 
    // If you do not set this element, then ManualCpcBiddingScheme is used by default.
    $biddingScheme = new EnhancedCpcBiddingScheme();
    $campaign->BiddingScheme = new SoapVar(
        $biddingScheme, 
        SOAP_ENC_OBJECT, 
        'EnhancedCpcBiddingScheme', 
        $GLOBALS['CampaignProxy']->GetNamespace()
        );
        
    // Used with FinalUrls shown in the ads that we will add below.
    $campaign->TrackingUrlTemplate = 
       "http://tracker.example.com/?season={_season}&promocode={_promocode}&u={lpurl}";

    $campaigns[] = $campaign;
    
    // Specify one or more ad groups.

    $adGroups = array();

    date_default_timezone_set('UTC');
    $endDate = new Date();
    $endDate->Day = 31;
    $endDate->Month = 12;
    $endDate->Year = date("Y");

    $adGroup = new AdGroup();
    $adGroup->Name = "Women's Heated Ski Glove Sale";
    $adGroup->AdDistribution = AdDistribution::Search;
    $adGroup->StartDate = null;
    $adGroup->EndDate = $endDate;
    $adGroup->SearchBid = new Bid();
    $adGroup->SearchBid->Amount = 0.07;
    $adGroup->Language = "English";
    
    // For ad groups you can use either of the InheritFromParentBiddingScheme or ManualCpcBiddingScheme objects. 
    // If you do not set this element, then InheritFromParentBiddingScheme is used by default.
    $biddingScheme = new ManualCpcBiddingScheme();
    $adGroup->BiddingScheme = new SoapVar(
        $biddingScheme, 
        SOAP_ENC_OBJECT, 
        'ManualCpcBiddingScheme', 
        $GLOBALS['CampaignProxy']->GetNamespace()
        );
    
    // You could use a tracking template which would override the campaign level
    // tracking template. Tracking templates defined for lower level entities 
    // override those set for higher level entities.
    // In this example we are using the campaign level tracking template.
    $adGroup->TrackingUrlTemplate = null;
    
    $adGroups[] = $adGroup;

    // In this example only the second keyword should succeed. The Text of the first keyword exceeds the limit,
    // and the third keyword is a duplicate of the second keyword. 

    $keywords = array();

    $keyword = new Keyword();
    $keyword->Bid = new Bid();
    $keyword->Bid->Amount = 0.47;
    $keyword->Param2 = "10% Off";
    $keyword->MatchType = MatchType::Broad;
    $keyword->Text = "Brand-A Gloves Brand-A Gloves Brand-A Gloves Brand-A Gloves Brand-A Gloves " .
                     "Brand-A Gloves Brand-A Gloves Brand-A Gloves Brand-A Gloves Brand-A Gloves " .
                     "Brand-A Gloves Brand-A Gloves Brand-A Gloves Brand-A Gloves Brand-A Gloves";
    // For keywords you can use either of the InheritFromParentBiddingScheme or ManualCpcBiddingScheme objects. 
    // If you do not set this element, then InheritFromParentBiddingScheme is used by default.
    $biddingScheme = new InheritFromParentBiddingScheme();
    $keyword->BiddingScheme = new SoapVar(
        $biddingScheme, 
        SOAP_ENC_OBJECT, 
        'InheritFromParentBiddingScheme', 
        $GLOBALS['CampaignProxy']->GetNamespace()
        );
    $keywords[] = $keyword;

    $keyword = new Keyword();
    $keyword->Bid = new Bid();
    $keyword->Bid->Amount = 0.47;
    $keyword->Param2 = "10% Off";
    $keyword->MatchType = MatchType::Phrase;
    $keyword->Text = "Brand-A Gloves";
    // For keywords you can use either of the InheritFromParentBiddingScheme or ManualCpcBiddingScheme objects. 
    // If you do not set this element, then InheritFromParentBiddingScheme is used by default.
    $biddingScheme = new InheritFromParentBiddingScheme();
    $keyword->BiddingScheme = new SoapVar(
        $biddingScheme, 
        SOAP_ENC_OBJECT, 
        'InheritFromParentBiddingScheme', 
        $GLOBALS['CampaignProxy']->GetNamespace()
        );
    $keywords[] = $keyword;

    $keyword = new Keyword();
    $keyword->Bid = new Bid();
    $keyword->Bid->Amount = 0.47;
    $keyword->Param2 = "10% Off";
    $keyword->MatchType = MatchType::Phrase;
    $keyword->Text = "Brand-A Gloves";
    // For keywords you can use either of the InheritFromParentBiddingScheme or ManualCpcBiddingScheme objects. 
    // If you do not set this element, then InheritFromParentBiddingScheme is used by default.
    $biddingScheme = new InheritFromParentBiddingScheme();
    $keyword->BiddingScheme = new SoapVar(
        $biddingScheme, 
        SOAP_ENC_OBJECT, 
        'InheritFromParentBiddingScheme', 
        $GLOBALS['CampaignProxy']->GetNamespace()
        );
    $keywords[] = $keyword;

    // In this example only the first 3 ads should succeed. 
    // The TitlePart2 of the fourth ad is empty and not valid,
    // and the fifth ad is a duplicate of the second ad. 

    $ads = array();

    for ($index = 0; $index < 5; $index++)
    {
        $expandedTextAd = new ExpandedTextAd();
        $expandedTextAd->TitlePart1 = "Contoso";
        $expandedTextAd->TitlePart2 = "Fast & Easy Setup";
        $expandedTextAd->Text = "Find New Customers & Increase Sales! Start Advertising on Contoso Today.";
        $expandedTextAd->Path1 = "seattle";
        $expandedTextAd->Path2 = "shoe sale";

        // With FinalUrls you can separate the tracking template, custom parameters, and 
        // landing page URLs. 

        $expandedTextAd->FinalUrls = array();
        $expandedTextAd->FinalUrls[] = "http://www.contoso.com/womenshoesale";

        // Final Mobile URLs can also be used if you want to direct the user to a different page 
        // for mobile devices.
        $expandedTextAd->FinalMobileUrls = array();
        $expandedTextAd->FinalMobileUrls[] = "http://mobile.contoso.com/womenshoesale";
 
        // You could use a tracking template which would override the campaign level
        // tracking template. Tracking templates defined for lower level entities 
        // override those set for higher level entities.
        // In this example we are using the campaign level tracking template.
        $expandedTextAd->TrackingUrlTemplate = null;

        // Set custom parameters that are specific to this ad, 
        // and can be used by the ad, ad group, campaign, or account level tracking template. 
        // In this example we are using the campaign level tracking template.
        $expandedTextAd->UrlCustomParameters = new CustomParameters();
        $expandedTextAd->UrlCustomParameters->Parameters = array();
        $customParameter1 = new CustomParameter();
        $customParameter1->Key = "promoCode";
        $customParameter1->Value = "PROMO" . ($index+1);
        $expandedTextAd->UrlCustomParameters->Parameters[] = $customParameter1;
        $customParameter2 = new CustomParameter();
        $customParameter2->Key = "season";
        $customParameter2->Value = "summer";
        $expandedTextAd->UrlCustomParameters->Parameters[] = $customParameter2;   

        $ads[] = new SoapVar($expandedTextAd, SOAP_ENC_OBJECT, 'ExpandedTextAd', $GLOBALS['CampaignProxy']->GetNamespace());
    }

    $ads[1]->enc_value->TitlePart2 = "Quick & Easy Setup";
    $ads[2]->enc_value->TitlePart2 = "Fast & Simple Setup";
    $ads[3]->enc_value->TitlePart2 = "";
    $ads[4]->enc_value->TitlePart2 = "Quick & Easy Setup";

    // Add the campaign, ad group, keywords, and ads
    
    $addCampaignsResponse = AddCampaigns($GLOBALS['AuthorizationData']->AccountId, $campaigns);
    $campaignIds = $addCampaignsResponse->CampaignIds->long;
    $campaignErrors = $addCampaignsResponse->PartialErrors;
    if(isset($addCampaignsResponse->PartialErrors->BatchError)){
        $campaignErrors = $addCampaignsResponse->PartialErrors->BatchError;
    }
    OutputCampaignsWithPartialErrors($campaigns, $campaignIds, $campaignErrors);
    
    $addAdGroupsResponse = AddAdGroups($campaignIds[0], $adGroups);
    $adGroupIds = $addAdGroupsResponse->AdGroupIds->long;
    $adGroupErrors = $addAdGroupsResponse->PartialErrors;
    if(isset($addAdGroupsResponse->PartialErrors->BatchError)){
        $adGroupErrors = $addAdGroupsResponse->PartialErrors->BatchError;
    }
    OutputAdGroupsWithPartialErrors($adGroups, $adGroupIds, $adGroupErrors);    

    $addKeywordsResponse = AddKeywords($adGroupIds[0], $keywords);
    $keywordIds = $addKeywordsResponse->KeywordIds->long;
    $keywordErrors = $addKeywordsResponse->PartialErrors;
    if(isset($addKeywordsResponse->PartialErrors->BatchError)){
        $keywordErrors = $addKeywordsResponse->PartialErrors->BatchError;
    }
    OutputKeywordsWithPartialErrors($keywords, $keywordIds, $keywordErrors);

    $addAdsResponse = AddAds($adGroupIds[0], $ads);
    $adIds = $addAdsResponse->AdIds->long;
    $adErrors = $addAdsResponse->PartialErrors;
    if(isset($addAdsResponse->PartialErrors->BatchError)){
        $adErrors = $addAdsResponse->PartialErrors->BatchError;
    }
    OutputAdsWithPartialErrors($ads, $adIds, $adErrors);
            
    
    // Here is a simple example that updates the campaign budget.
    // If the campaign has a shared budget you cannot update the Campaign budget amount,
    // and you must instead update the amount in the Budget object. If you try to update 
    // the budget amount of a campaign that has a shared budget, the service will return 
    // the CampaignServiceCannotUpdateSharedBudget error code.

    $campaignType = array(CampaignType::DynamicSearchAds, CampaignType::SearchAndContent, CampaignType::Shopping);
    
    $getCampaigns = GetCampaignsByAccountId(
            $GLOBALS['AuthorizationData']->AccountId, 
            $campaignType)->Campaigns;

    $updateCampaigns = array();
    $updateBudgets = array();
    $getCampaignIds = array();
    $getBudgetIds = array();

    // Increase existing budgets by 20%
    foreach ($getCampaigns->Campaign as $campaign)
    {
        // If the campaign has a shared budget, let's add the budget ID to the list we will update later.
        if (!empty($campaign) && isset($campaign->BudgetId) && $campaign->BudgetId > 0)
        {
            $getBudgetIds[] = $campaign->BudgetId;
        }
    }

    // Update shared budgets in Budget objects.
    if (!empty($getBudgetIds))
    {
        // The UpdateBudgets operation only accepts 100 Budget objects per call. 
        // To simply the example we will update the first 100.
        $getUniqueBudgetIds = array_unique($getBudgetIds, SORT_REGULAR);
        $top100BudgetIds = array_slice($getUniqueBudgetIds, 0, 100);
        $getBudgets = GetBudgetsByIds($top100BudgetIds)->Budgets;

        print("List of shared budgets BEFORE update:\n\n");
        foreach ($getBudgets->Budget as $budget)
        {
            print("Budget:\n");
            OutputBudget($budget);
        }

        print("List of campaigns that share each budget:\n\n");
        $getCampaignIdCollection = GetCampaignIdsByBudgetIds($top100BudgetIds)->CampaignIdCollection;
        for($index = 0; $index < count($getCampaignIdCollection); $index++)
        {
            printf("BudgetId: %s\n", $top100BudgetIds[$index]);
            print("Campaign Ids:\n");
            if(!empty($getCampaignIdCollection->IdCollection[$index]))
            {
                foreach ($getCampaignIdCollection->IdCollection[$index]->Ids->long as $id)
                {
                    printf("\t%s\n", $id);
                }
            }
            print("\n");
        }

        foreach ($getBudgets->Budget as $budget)
        {
            if (!empty($budget))
            {
                // Increase budget by 20 %
                $budget->Amount *= 1.2;
                $updateBudgets[] = $budget;
            }
        }
        UpdateBudgets($updateBudgets);

        $getBudgets = GetBudgetsByIds($top100BudgetIds)->Budgets;

        print("List of shared budgets AFTER update:\n\n");
        foreach ($getBudgets->Budget as $budget)
        {
            print("Budget:\n");
            OutputBudget($budget);
        }
    }

    // Update unshared budgets in Campaign objects.
    if(!empty($getCampaigns))
    {
        print("List of 100 campaigns BEFORE update:\n");
        // The UpdateCampaigns operation only accepts 100 Campaign objects per call. 
        // To simply the example we will update the first 100.
        $index=0;
        while($index < 100 && $index < count($getCampaigns))
        {
            $campaign = $getCampaigns->Campaign[$index];
            print("Campaign:\n");
            OutputCampaign($campaign);

            $updateCampaign = new Campaign();
            $updateCampaign->Id = $campaign->Id;
                        
            // If the campaign has a shared budget, we can update other properties of the campaign, 
            // but cannot update the budget via Campaign object.
            if (isset($campaign->BudgetId) && $campaign->BudgetId > 0)
            {
                $updateCampaign->Name = $campaign->Name . $_SERVER['REQUEST_TIME'];
            }        
            else
            {
                // Increase budget by 20 %
                $updateCampaign->BudgetType = $campaign->BudgetType;
                $updateCampaign->DailyBudget = $campaign->DailyBudget * 1.2;
            }
            
            $getCampaignIds[] = $updateCampaign->Id;
            $updateCampaigns[] = $updateCampaign;
            $index++;
        }
        
        UpdateCampaigns($GLOBALS['AuthorizationData']->AccountId, $updateCampaigns);
