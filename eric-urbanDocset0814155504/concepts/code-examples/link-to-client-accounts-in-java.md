---
title: "Link to Client Accounts in Java"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 08154864-25f8-450a-b0a2-365ab8543bb9
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Link to Client Accounts in Java
The following example shows how to use agency credentials to invite a client, and use client credentials to accept the invitation. Run this sample multiple times alternating between agency and client credentials to update and observe the status change, for example from LinkPending to LinkAccepted to Active.

[!INCLUDE[java_header](../../concepts/code-examples/includes/java-header.md)]

```java
package com.microsoft.bingads.examples.v11;

import java.rmi.*;

import com.microsoft.bingads.*;
import com.microsoft.bingads.v11.customermanagement.*;

/// 
/// This example demonstrates how to use agency credentials to invite a client, 
/// and use client credentials to accept the invitation. 
/// Run this sample multiple times alternating between agency and client credentials 
/// to update and observe the status change, for example from LinkPending to LinkAccepted to Active. 
/// 
public class ManageClient extends ExampleBase {

    static AuthorizationData authorizationData;
    static ServiceClient<ICustomerManagementService> CustomerService; 
        
    // Agency Customer Id
    private static long CustomerId = <CustomerIdGoesHere>;
    
    // Client Account Id
    private static long ClientAccountId = <ClientAccountIdGoesHere>;
        

    public static void main(java.lang.String[] args) {
   	 
    	try
        {
            authorizationData = new AuthorizationData();
            authorizationData.setDeveloperToken(DeveloperToken);
            authorizationData.setCustomerId(CustomerId);
            authorizationData.setAuthentication(new PasswordAuthentication(UserName, Password));
	        
            CustomerService = new ServiceClient<ICustomerManagementService>(
                    authorizationData, 
                    API_ENVIRONMENT,
                    ICustomerManagementService.class);
	        
            outputStatusMessage("You must edit this example to provide the ClientAccountId for " +
                    "the client link.");
            outputStatusMessage("When adding a client link, the client link's ManagingCustomerId is set to the CustomerId of the current " +
                    	"authenticated user, who must be a Super Admin of the agency.");
            outputStatusMessage("Login as an agency Super Admin user to send a client link invitation, " +
                    	"or unlink an existing client link.");
            outputStatusMessage("Login as a client Super Admin user to accept a client link invitation.\n");
 
            UpdateClientLinksResponse updateClientLinksResponse = null;

            // Specify the client link search criteria

            Paging pageInfo = new Paging();
            pageInfo.setIndex(0);    // The first page
            pageInfo.setSize(100);   // The first 100 client links for this page of results
            
            ArrayOfOrderBy ordering = new ArrayOfOrderBy();
            OrderBy orderBy = new OrderBy();
            orderBy.setField(OrderByField.NUMBER);
            orderBy.setOrder(SortOrder.ASCENDING);
            ordering.getOrderBies().add(orderBy);

            ArrayOfPredicate predicates = new ArrayOfPredicate();
            Predicate predicate = new Predicate();
            predicate.setField("ClientAccountId");
            predicate.setOperator(PredicateOperator.IN);
            predicate.setValue("" + ClientAccountId);
            predicates.getPredicates().add(predicate);
            
            // Search for client links that match the specified criteria.

            ArrayOfClientLink clientLinks = searchClientLinks(
                ordering,
                pageInfo,
                predicates);

            // Determine whether the agency is already managing the specified client account. 
            // If a link exists with status either Active, LinkInProgress, LinkPending, 
            // UnlinkInProgress, or UnlinkPending, the agency may not initiate a duplicate client link.

            ClientLink clientLink;
            boolean newLinkRequired = true;

            if (clientLinks.getClientLinks().size() > 0)
            {
                clientLink = clientLinks.getClientLinks().get(0);
                outputStatusMessage(String.format("Current ClientLink Status: %s.\n\n", clientLink.getStatus()));
                printClientLinks(clientLinks);
                
                ArrayOfClientLink updateClientLinks = new ArrayOfClientLink();
                updateClientLinks.getClientLinks().add(clientLink);
                
                switch (clientLink.getStatus())
                {
                    // The agency may choose to initiate the unlink process, 
                    // which would terminate the existing relationship with the client. 
                    case ACTIVE:
                        clientLink.setStatus(ClientLinkStatus.UNLINK_REQUESTED);
                        updateClientLinksResponse = updateClientLinks(updateClientLinks);
                        outputStatusMessage("UpdateClientLinks : UnlinkRequested.\n");
                        newLinkRequired = false;
                        break;
                    // Waiting on a system status transition or waiting for the StartDate.
                    case LINK_ACCEPTED:
                        outputStatusMessage("The status is transitioning towards LinkInProgress.\n");
                        newLinkRequired = false;
                        break;
                    // Waiting on a system status transition.
                    case LINK_IN_PROGRESS:
                        outputStatusMessage("The status is transitioning towards Active.\n");
                        newLinkRequired = false;
                        break;
                    // When the status is LinkPending, either the agency or client may update the status.
                    // The agency may choose to cancel the client link invitation; however, in this sample 
                    // the client will accept the invitation. 
                    // If the client does not accept or decline the invitation within 30 days, and if the agency
                    // does not update the status to LinkCanceled, the system updates the status to LinkExpired.
                    case LINK_PENDING:
                        /*
                        clientLink.setStatus(ClientLinkStatus.LinkCanceled);
                        updateClientLinksResponse = UpdateClientLinks(updateClientLinks);
                        outputStatusMessage("UpdateClientLinks: LinkCanceled.\n");
                         */
                        clientLink.setStatus(ClientLinkStatus.LINK_ACCEPTED);
                        updateClientLinksResponse = updateClientLinks(updateClientLinks);
                        outputStatusMessage("UpdateClientLinks: LinkAccepted.\n");
                        newLinkRequired = false;
                        break;
                    // Waiting on a system status transition.
                    case UNLINK_IN_PROGRESS:
                        outputStatusMessage("The status is transitioning towards Inactive.\n");
                        newLinkRequired = false;
                        break;
                    // Waiting on a system status transition.
                    case UNLINK_PENDING:
                        outputStatusMessage("The status is transitioning towards Inactive.\n");
                        newLinkRequired = false;
                        break;
                    // The link lifecycle has ended.  
                    default:
                        outputStatusMessage("A new client link invitation is required.\n");
                        break;
                }

                // Print errors if any occurred when updating the client link.
                if (updateClientLinksResponse != null)
                {
                    printPartialErrors(updateClientLinksResponse.getOperationErrors(),
                                       updateClientLinksResponse.getPartialErrors());
                }
            }

            // If no links exist between the agency and specified client account, or a link exists with status  
            // either Inactive, LinkCanceled, LinkDeclined, LinkExpired, or LinkFailed, then the agency must
            // initiate a new client link.

            if(newLinkRequired)
            {
                clientLink = new ClientLink();
                clientLink.setClientAccountId(ClientAccountId);
                clientLink.setManagingCustomerId(authorizationData.getCustomerId());
                clientLink.setIsBillToClient(true);
                clientLink.setName("My Client Link");
                clientLink.setStartDate(null);
                clientLink.setSuppressNotification(true);

                ArrayOfClientLink addClientLinks = new ArrayOfClientLink();
                addClientLinks.getClientLinks().add(clientLink);
                
                AddClientLinksResponse addClientLinksResponse = addClientLinks(addClientLinks);

                // Print errors if any occurred when adding the client link.
                printPartialErrors(addClientLinksResponse.getOperationErrors(), addClientLinksResponse.getPartialErrors());
                outputStatusMessage("The user attempted to add a new ClientLink.\n");
            }

            // Get and print the current client link

            clientLinks = searchClientLinks(
                    ordering,
                    pageInfo,
                    predicates);

            printClientLinks(clientLinks);
            
            outputStatusMessage("Program execution completed\n"); 
        
        // Customer Management service operations can throw AdApiFaultDetail.
        } catch (AdApiFaultDetail_Exception ex) {
            outputStatusMessage("The operation failed with the following faults:\n");

            for (AdApiError error : ex.getFaultInfo().getErrors().getAdApiErrors())
            {
	            outputStatusMessage("AdApiError\n");
	            outputStatusMessage(String.format("Code: %d\nError Code: %s\nMessage: %s\n\n", error.getCode(), error.getErrorCode(), error.getMessage()));
            }
        
        // Customer Management service operations can throw ApiFault.
        } catch (ApiFault_Exception ex) {
            outputStatusMessage("The operation failed with the following faults:\n");

            for (OperationError error : ex.getFaultInfo().getOperationErrors().getOperationErrors())
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

    // Searches client links for the customer of the current authenticated user,
    // filtered by the search criteria.

    static ArrayOfClientLink searchClientLinks(
        ArrayOfOrderBy ordering,
        Paging pageInfo,
        ArrayOfPredicate predicates) throws RemoteException, Exception
    {
        SearchClientLinksRequest request = new SearchClientLinksRequest();
        request.setOrdering(ordering);
        request.setPageInfo(pageInfo);
        request.setPredicates(predicates);
           
        return CustomerService.getService().searchClientLinks(request).getClientLinks();
    }

    // Initiates the client link process to manage the account of another customer. 
    // Sends an invitation from an agency to a potential client.

    static AddClientLinksResponse addClientLinks(ArrayOfClientLink clientLinks) throws RemoteException, Exception
    {
        AddClientLinksRequest request = new AddClientLinksRequest();

        request.setClientLinks(clientLinks);

        return CustomerService.getService().addClientLinks(request);
    }

    // Using agency credentials, updates the status of the specified client links.

    static UpdateClientLinksResponse updateClientLinks(ArrayOfClientLink clientLinks) throws RemoteException, Exception
    {
        UpdateClientLinksRequest request = new UpdateClientLinksRequest();

        request.setClientLinks(clientLinks);

        return CustomerService.getService().updateClientLinks(request);
    }

    // Prints a list of client links.

    private static void printClientLinks(ArrayOfClientLink clientLinks)
    {
        if (clientLinks == null)
        {
            return;
        }

        for (ClientLink clientLink : clientLinks.getClientLinks())
        {
            outputStatusMessage(String.format("Status: %s\n", clientLink.getStatus()));
            outputStatusMessage(String.format("ClientAccountId: %s\n", clientLink.getClientAccountId()));
            outputStatusMessage(String.format("ClientAccountNumber: %s\n", clientLink.getClientAccountNumber()));
            outputStatusMessage(String.format("ManagingAgencyCustomerId: %s\n", clientLink.getManagingCustomerId()));
            outputStatusMessage(String.format("ManagingCustomerNumber: %s\n", clientLink.getManagingCustomerNumber()));
            outputStatusMessage(clientLink.getIsBillToClient() ? "IsBillToClient: True\n" : "IsBillToClient: False\n");
            outputStatusMessage(String.format("InviterEmail: %s\n", clientLink.getInviterEmail()));
            outputStatusMessage(String.format("InviterName: %s\n", clientLink.getInviterName()));
            outputStatusMessage(String.format("InviterPhone: %s\n", clientLink.getInviterPhone()));
            outputStatusMessage(String.format("LastModifiedByUserId: %s\n", clientLink.getLastModifiedByUserId()));
            outputStatusMessage(String.format("Name: %s\n", clientLink.getName()));
            outputStatusMessage(String.format("Note: %s\n", clientLink.getNote()));
            outputStatusMessage("\n");
        }
    }

    // Print errors if any occurred when adding or updating the client link.

    static void printPartialErrors(ArrayOfOperationError operationErrors, ArrayOfArrayOfOperationError partialErrors)
    {
        if (operationErrors == null)
        {
            return;
        }

        for (OperationError error : operationErrors.getOperationErrors())
        {
            outputStatusMessage("OperationError");
            outputStatusMessage(String.format("Code: %d\nMessage: %s\n", error.getCode(), error.getMessage()));
        }

        if (partialErrors == null)
        {
            return;
        }

        for (ArrayOfOperationError errors : partialErrors.getArrayOfOperationErrors())
        {
            if (errors != null)
            {
                for (OperationError error : errors.getOperationErrors())
                {
                    if (error != null)
                    {
                    	outputStatusMessage("OperationError");
                        outputStatusMessage(String.format("Code: %d\nMessage: %s\n", error.getCode(), error.getMessage()));
                    }
                }
            }
        }
    }
}
```

## See Also
[Getting Started Using Java with Bing Ads Services](../../concepts/get-started/getting-started-using-java-with-bing-ads-services.md)  
