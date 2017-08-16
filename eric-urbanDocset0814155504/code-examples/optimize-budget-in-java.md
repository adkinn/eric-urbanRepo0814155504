---
title: "Optimize Budget in Java"
ms.custom: na
ms.date: "08/16/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: 83263084-8183-4e23-a090-657a1e7572e5
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Optimize Budget in Java
This example shows how to get the budget opportunities for the specified account.

[!INCLUDE[java_header](../code-examples/includes/java_header.md)]

```java
package com.microsoft.bingads.examples.v11;

import java.rmi.*;
import java.util.ArrayList;

import com.microsoft.bingads.*;
import com.microsoft.bingads.v11.campaignmanagement.*;
import com.microsoft.bingads.v11.adinsight.*;

public class BudgetOpportunities extends ExampleBase {

    static AuthorizationData authorizationData;
    static ServiceClient<IAdInsightService> AdInsightService;
    static ServiceClient<ICampaignManagementService> CampaignService;
    
    public static void main(java.lang.String[] args) {
   	 
    	try
        {
            authorizationData = new AuthorizationData();
            authorizationData.setDeveloperToken(DeveloperToken);
            authorizationData.setAuthentication(new PasswordAuthentication(UserName, Password));
            authorizationData.setCustomerId(CustomerId);
            authorizationData.setAccountId(AccountId);
	         
            AdInsightService = new ServiceClient<IAdInsightService>(
                    authorizationData, 
                    API_ENVIRONMENT,
                    IAdInsightService.class);
            
            CampaignService = new ServiceClient<ICampaignManagementService>(
                    authorizationData, 
                    API_ENVIRONMENT,
                    ICampaignManagementService.class);
	         
            // Get the budget opportunities for each campaign in the current authenticated account.

            ArrayList<CampaignType> campaignTypes = new ArrayList<CampaignType>();
            campaignTypes.add(CampaignType.SEARCH_AND_CONTENT);
            campaignTypes.add(CampaignType.SHOPPING);
            ArrayOfCampaign campaigns = getCampaignsByAccountId(AccountId, campaignTypes);
            
            ArrayOfBudgetOpportunity opportunities = null;
            
            for (Campaign campaign : campaigns.getCampaigns())
            {
                if (campaign.getId() != null)
                {
                	opportunities = getBudgetOpportunities((long)campaign.getId());
                	outputBudgetOpportunities(opportunities, (long)campaign.getId());
                }
            }
        
        // Ad Insight service operations can throw AdApiFaultDetail.
        } catch (com.microsoft.bingads.v11.adinsight.AdApiFaultDetail_Exception ex) {
	        outputStatusMessage("The operation failed with the following faults:\n");
	
	        for (com.microsoft.bingads.v11.adinsight.AdApiError error : ex.getFaultInfo().getErrors().getAdApiErrors())
	        {
	            outputStatusMessage("AdApiError\n");
	            outputStatusMessage(String.format("Code: %d\nError Code: %s\nMessage: %s\n\n", error.getCode(), error.getErrorCode(), error.getMessage()));
	        }

	    // Ad Insight service operations can throw ApiFaultDetail.
        } catch (com.microsoft.bingads.v11.adinsight.ApiFaultDetail_Exception ex) {
            outputStatusMessage("The operation failed with the following faults:\n");

            for (com.microsoft.bingads.v11.adinsight.BatchError error : ex.getFaultInfo().getBatchErrors().getBatchErrors())
            {
                outputStatusMessage(String.format("BatchError at Index: %d\n", error.getIndex()));
                outputStatusMessage(String.format("Code: %d\nMessage: %s\n\n", error.getCode(), error.getMessage()));
            }

            for (com.microsoft.bingads.v11.adinsight.OperationError error : ex.getFaultInfo().getOperationErrors().getOperationErrors())
            {
                outputStatusMessage("OperationError\n");
                outputStatusMessage(String.format("Code: %d\nMessage: %s\n\n", error.getCode(), error.getMessage()));
            }
        // Campaign Management service operations can throw AdApiFaultDetail.
        } catch (com.microsoft.bingads.v11.campaignmanagement.AdApiFaultDetail_Exception ex) {
	        outputStatusMessage("The operation failed with the following faults:\n");
	
	        for (com.microsoft.bingads.v11.campaignmanagement.AdApiError error : ex.getFaultInfo().getErrors().getAdApiErrors())
	        {
	            outputStatusMessage("AdApiError\n");
	            outputStatusMessage(String.format("Code: %d\nError Code: %s\nMessage: %s\n\n", error.getCode(), error.getErrorCode(), error.getMessage()));
	        }

	    // Campaign Management service operations can throw ApiFaultDetail.
        } catch (com.microsoft.bingads.v11.campaignmanagement.ApiFaultDetail_Exception ex) {
            outputStatusMessage("The operation failed with the following faults:\n");

            for (com.microsoft.bingads.v11.campaignmanagement.BatchError error : ex.getFaultInfo().getBatchErrors().getBatchErrors())
            {
                outputStatusMessage(String.format("BatchError at Index: %d\n", error.getIndex()));
                outputStatusMessage(String.format("Code: %d\nMessage: %s\n\n", error.getCode(), error.getMessage()));
            }

            for (com.microsoft.bingads.v11.campaignmanagement.OperationError error : ex.getFaultInfo().getOperationErrors().getOperationErrors())
            {
                outputStatusMessage("OperationError\n");
                outputStatusMessage(String.format("Code: %d\nMessage: %s\n\n", error.getCode(), error.getMessage()));
            }
        } catch (RemoteException ex) {
            outputStatusMessage("Service communication error encountered: ");
            outputStatusMessage(ex.getMessage());
            ex.printStackTrace();
        } catch (Exception ex) {
             outputStatusMessage("Error encountered: ");
             outputStatusMessage(ex.getMessage());
             ex.printStackTrace();
        }
    }

    // Gets campaigns of the specified type for the account.
    public static ArrayOfCampaign getCampaignsByAccountId(
    		long accountId,
    		ArrayList<CampaignType> campaignTypes) throws RemoteException, Exception
    {
    	GetCampaignsByAccountIdRequest request = new GetCampaignsByAccountIdRequest();
        
        request.setAccountId(accountId);
        request.setCampaignType(campaignTypes);

        return CampaignService.getService().getCampaignsByAccountId(request).getCampaigns();
    }
    
    // Gets the budget opportunities for the specified campaign.
    public static ArrayOfBudgetOpportunity getBudgetOpportunities(long campaignId) throws RemoteException, Exception
    {
        GetBudgetOpportunitiesRequest request = new GetBudgetOpportunitiesRequest();
        
        request.setCampaignId(campaignId);

        return AdInsightService.getService().getBudgetOpportunities(request).getOpportunities();
    }
    
    // Outputs the list of BudgetOpportunity objects.
    static void outputBudgetOpportunities(ArrayOfBudgetOpportunity budgetOpportunities, long campaignId){
    	if (budgetOpportunities != null && budgetOpportunities.getBudgetOpportunities().size() > 0)
        {
            for (BudgetOpportunity budgetOpportunity : budgetOpportunities.getBudgetOpportunities())
            {
                outputStatusMessage("BudgetPoints: ");
                for (BudgetPoint budgetPoint : budgetOpportunity.getBudgetPoints().getBudgetPoints())
                {
                    outputBudgetPoint(budgetPoint);
                }
                outputStatusMessage(String.format("BudgetType: %s", budgetOpportunity.getBudgetType()));
                outputStatusMessage(String.format("CampaignId: %s", budgetOpportunity.getCampaignId()));
                outputStatusMessage(String.format("CurrentBudget: %s", budgetOpportunity.getCurrentBudget()));
                outputStatusMessage(String.format("IncreaseInClicks: %s", budgetOpportunity.getIncreaseInClicks()));
                outputStatusMessage(String.format("IncreaseInImpressions: %s", budgetOpportunity.getIncreaseInImpressions()));
                outputStatusMessage(String.format("OpportunityKey: %s", budgetOpportunity.getOpportunityKey()));
                outputStatusMessage(String.format("PercentageIncreaseInClicks: %s", budgetOpportunity.getPercentageIncreaseInClicks()));
                outputStatusMessage(String.format("PercentageIncreaseInImpressions: %s", budgetOpportunity.getPercentageIncreaseInImpressions()));
                outputStatusMessage(String.format("RecommendedBudget: %s", budgetOpportunity.getRecommendedBudget()));
            }
        }
    	else {
    		outputStatusMessage(String.format("There are no budget opportunities for CampaignId: %s.", campaignId));
    	}
    }
    
    // Outputs the BudgetPoint object.
    static void outputBudgetPoint(BudgetPoint budgetPoint){
    	if (budgetPoint != null)
        {
            outputStatusMessage(String.format("BudgetAmount: %s", budgetPoint.getBudgetAmount()));
            outputStatusMessage(String.format("BudgetPointType: %s", budgetPoint.getBudgetPointType()));
            outputStatusMessage(String.format("EstimatedWeeklyClicks: %s", budgetPoint.getEstimatedWeeklyClicks()));
            outputStatusMessage(String.format("EstimatedWeeklyCost: %s", budgetPoint.getEstimatedWeeklyCost()));
            outputStatusMessage(String.format("EstimatedWeeklyImpressions: %s", budgetPoint.getEstimatedWeeklyImpressions()));
        }
    }
}
```

## See Also
[Getting Started Using Java with Bing Ads Services](../docset-overview/getting-started-using-java-with-bing-ads-services.md)  

