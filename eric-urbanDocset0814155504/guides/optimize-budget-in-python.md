---
title: "Optimize Budget in Python"
ms.custom: na
ms.date: "07/10/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: 345f11f6-218a-4001-85ac-7a99045f4a74
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Optimize Budget in Python
This example shows how to get the budget opportunities for the specified account using the following Ad Insight service operations.

[!INCLUDE[python_header](../guides/includes/python_header.md)]

```python
from auth_helper import *
from output_helper import *

# You must provide credentials in auth_helper.py.

def main(authorization_data): 

    try:
        # Get the budget opportunities for each campaign in the current authenticated account.

        campaign_types=['SearchAndContent', 'Shopping']
        campaigns=campaign_service.GetCampaignsByAccountId(authorization_data.account_id, campaign_types)

        for campaign in campaigns['Campaign']:
            if campaign.Id is not None:
                opportunities=adinsight_service.GetBudgetOpportunities(campaign.Id)
                output_budget_opportunities(opportunities, campaign.Id)

        output_status_message("Program execution completed")

    except WebFault as ex:
        output_webfault_errors(ex)
    except Exception as ex:
        output_status_message(ex)


# Main execution
if __name__ == '__main__':

    print("Python loads the web service proxies at runtime, so you will observe " \
          "a performance delay between program launch and main execution...\n")
    
    authorization_data=AuthorizationData(
        account_id=None,
        customer_id=None,
        developer_token=DEVELOPER_TOKEN,
        authentication=None,
    )

    adinsight_service=ServiceClient(
        service='AdInsightService', 
        authorization_data=authorization_data, 
        environment=ENVIRONMENT,
        version=11
    )
    
    campaign_service=ServiceClient(
        service='CampaignManagementService', 
        authorization_data=authorization_data, 
        environment=ENVIRONMENT,
        version=11,
    )

    # You should authenticate for Bing Ads production services with a Microsoft Account, 
    # instead of providing the Bing Ads username and password set. 
    # Authentication with a Microsoft Account is currently not supported in Sandbox.
        
    authenticate(authorization_data)
        
    main(authorization_data)
```

## See Also
[Getting Started Using Python with Bing Ads Services](../guides/getting-started-using-python-with-bing-ads-services.md)  
