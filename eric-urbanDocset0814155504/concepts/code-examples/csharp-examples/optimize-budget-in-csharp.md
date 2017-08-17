---
title: "Optimize Budget in C#"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4890a0f3-ead4-487f-bcb1-6aadedec3a9c
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Optimize Budget in C# #
This example shows how to get the budget opportunities for each campaign in the current authenticated account.

[!INCLUDE[csharp_header](../../../concepts/code-examples/csharp-examples/includes/csharp-header.md)]

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.ServiceModel;
using System.Threading.Tasks;
using Microsoft.BingAds.V11.AdInsight;
using Microsoft.BingAds.V11.CampaignManagement;
using Microsoft.BingAds;


namespace BingAdsExamplesLibrary.V11
{
    /// <summary>
    /// This example demonstrates how to get the budget opportunities for each campaign in the current authenticated account.
    /// </summary>
    public class BudgetOpportunities : ExampleBase
    {
        public override string Description
        {
            get { return "Budget Opportunities | AdInsight V11"; }
        }

        public async override Task RunAsync(AuthorizationData authorizationData)
        {
            try
            {
                AdInsightService = new ServiceClient<IAdInsightService>(authorizationData);
                CampaignService = new ServiceClient<ICampaignManagementService>(authorizationData);

                var campaigns = (await GetCampaignsByAccountIdAsync(
                    authorizationData.AccountId,
                    AllCampaignTypes)).Campaigns;

                IList<BudgetOpportunity> opportunities = null;

                // Get the budget opportunities for each campaign in the current authenticated account.

                foreach (var campaign in campaigns)
                {
                    if (campaign.Id != null)
                    {
                        opportunities = (await GetBudgetOpportunitiesAsync((long)campaign.Id)).Opportunities;
                        OutputBudgetOpportunities(opportunities, (long) campaign.Id);
                    }
                }
            }
            // Catch authentication exceptions
            catch (OAuthTokenRequestException ex)
            {
                OutputStatusMessage(string.Format("Couldn't get OAuth tokens. Error: {0}. Description: {1}", ex.Details.Error, ex.Details.Description));
            }
            // Catch AdInsight service exceptions
            catch (FaultException\<Microsoft.BingAds.V11.AdInsight.AdApiFaultDetail> ex)
            {
                OutputStatusMessage(string.Join("; ", ex.Detail.Errors.Select(error => string.Format("{0}: {1}", error.Code, error.Message))));
            }
            catch (FaultException\<Microsoft.BingAds.V11.AdInsight.ApiFaultDetail> ex)
            {
                OutputStatusMessage(string.Join("; ", ex.Detail.OperationErrors.Select(error => string.Format("{0}: {1}", error.Code, error.Message))));
                OutputStatusMessage(string.Join("; ", ex.Detail.BatchErrors.Select(error => string.Format("{0}: {1}", error.Code, error.Message))));
            }
            // Catch Campaign Management service exceptions
            catch (FaultException\<Microsoft.BingAds.V11.CampaignManagement.AdApiFaultDetail> ex)
            {
                OutputStatusMessage(string.Join("; ", ex.Detail.Errors.Select(error => string.Format("{0}: {1}", error.Code, error.Message))));
            }
            catch (FaultException\<Microsoft.BingAds.V11.CampaignManagement.ApiFaultDetail> ex)
            {
                OutputStatusMessage(string.Join("; ", ex.Detail.OperationErrors.Select(error => string.Format("{0}: {1}", error.Code, error.Message))));
                OutputStatusMessage(string.Join("; ", ex.Detail.BatchErrors.Select(error => string.Format("{0}: {1}", error.Code, error.Message))));
            }
            catch (Exception ex)
            {
                OutputStatusMessage(ex.Message);
            }
        }        
    }
}
```

## See Also
[Getting Started Using C&#35; with Bing Ads Services](../../../concepts/get-started/getting-started-using-csharp-with-bing-ads-services.md)  
