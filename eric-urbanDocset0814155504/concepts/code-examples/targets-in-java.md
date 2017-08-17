---
title: "Targets in Java"
ms.custom: na
ms.date: "08/16/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: 855d655d-48b1-41f6-a688-819a047e2652
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Targets in Java
This example shows how to associate targets with a campaign and ad group.

[!INCLUDE[java_header](../../concepts/code-examples/includes/java_header.md)]

```java
package com.microsoft.bingads.examples.v10;

import java.rmi.*;
import java.util.ArrayList;

import com.microsoft.bingads.*;
import com.microsoft.bingads.v10.campaignmanagement.*;

public class Targets {

     static AuthorizationData authorizationData;
     static ServiceClient<ICampaignManagementService> CampaignService; 

     protected static java.lang.String UserName = "<UserNameGoesHere>";
     protected static java.lang.String Password = "<PasswordGoesHere>";
     protected static java.lang.String DeveloperToken = "<DeveloperTokenGoesHere>";
     protected static long CustomerId = <CustomerIdGoesHere>;
     protected static long AccountId = <AccountIdGoesHere>;

 	 // Prints the string to System.out
     protected static void outputStatusMessage(java.lang.String message){
   		System.out.println(message);
   	}

     public static void main(java.lang.String[] args) {

         try
         {
             authorizationData = new AuthorizationData();
             authorizationData.setDeveloperToken(DeveloperToken);
             authorizationData.setAuthentication(new PasswordAuthentication(UserName, Password));
             authorizationData.setCustomerId(CustomerId);
             authorizationData.setAccountId(AccountId);

             CampaignService = new ServiceClient<ICampaignManagementService>(
	    				authorizationData, 
	    				ICampaignManagementService.class);

             // Specify a campaign. 

             ArrayOfCampaign campaigns = new ArrayOfCampaign();
             Campaign campaign = new Campaign();
             campaign.setName("Summer Shoes " + System.currentTimeMillis());
             campaign.setDescription("Summer shoes line.");
             campaign.setBudgetType(BudgetLimitType.MONTHLY_BUDGET_SPEND_UNTIL_DEPLETED);
             campaign.setMonthlyBudget(1000.00);
             campaign.setTimeZone("PacificTimeUSCanadaTijuana");
             campaign.setDaylightSaving(true);
             campaigns.getCampaigns().add(campaign);

             // Specify an ad group. 

             ArrayOfAdGroup adGroups = new ArrayOfAdGroup();
             AdGroup adGroup = new AdGroup();
             adGroup.setName("Women's Red Shoes");
             ArrayList<AdDistribution> adDistribution = new ArrayList<AdDistribution>();
             adDistribution.add(AdDistribution.SEARCH);
             adGroup.setAdDistribution(adDistribution);
             adGroup.setBiddingModel(BiddingModel.KEYWORD);
             adGroup.setPricingModel(PricingModel.CPC);
             adGroup.setStartDate(null);
             adGroup.setEndDate(new com.microsoft.bingads.v10.campaignmanagement.Date());
             adGroup.getEndDate().setDay(31);
             adGroup.getEndDate().setMonth(12);
             adGroup.getEndDate().setYear(2016);
             Bid searchBid = new Bid();
             searchBid.setAmount(0.09);
             adGroup.setSearchBid(searchBid);
             adGroup.setLanguage("English");
             adGroups.getAdGroups().add(adGroup);

             // Add the campaign and ad group

             AddCampaignsResponse addCampaignsResponse = addCampaigns(AccountId, campaigns);
             ArrayOfNullableOflong campaignIds = addCampaignsResponse.getCampaignIds();
             ArrayOfBatchError campaignErrors = addCampaignsResponse.getPartialErrors();
             outputCampaignsWithPartialErrors(campaigns, campaignIds, campaignErrors);

             AddAdGroupsResponse addAdGroupsResponse = addAdGroups(campaignIds.getLongs().get(0), adGroups);
             ArrayOfNullableOflong adGroupIds = addAdGroupsResponse.getAdGroupIds();
             ArrayOfBatchError adGroupErrors = addAdGroupsResponse.getPartialErrors();
             outputAdGroupsWithPartialErrors(adGroups, adGroupIds, adGroupErrors);

             // This example demonstrates how to associate targets with a campaign and ad group.

             Target campaignTarget = new Target();
             campaignTarget.setName("My Campaign Target");

             DayTimeTarget campaignDayTimeTarget = new DayTimeTarget();
             DayTimeTargetBid campaignDayTimeTargetBid = new DayTimeTargetBid();
             campaignDayTimeTargetBid.setBidAdjustment(10);
             campaignDayTimeTargetBid.setDay(Day.MONDAY);
             campaignDayTimeTargetBid.setFromHour(1);
             campaignDayTimeTargetBid.setToHour(12);
             campaignDayTimeTargetBid.setFromMinute(Minute.ZERO);
             campaignDayTimeTargetBid.setToMinute(Minute.FORTY_FIVE);
             ArrayOfDayTimeTargetBid campaignDayTimeTargetBids = new ArrayOfDayTimeTargetBid();
             campaignDayTimeTargetBids.getDayTimeTargetBids().add(campaignDayTimeTargetBid);
             campaignDayTimeTarget.setBids(campaignDayTimeTargetBids);
             campaignTarget.setDayTime(campaignDayTimeTarget);

             DeviceOSTarget campaignDeviceOSTarget = new DeviceOSTarget();
             DeviceOSTargetBid campaignDeviceOSTargetBid = new DeviceOSTargetBid();
             campaignDeviceOSTargetBid.setBidAdjustment(10);
             campaignDeviceOSTargetBid.setDeviceName("Tablets");
             ArrayOfDeviceOSTargetBid campaignDeviceOSTargetBids = new ArrayOfDeviceOSTargetBid();
             campaignDeviceOSTargetBids.getDeviceOSTargetBids().add(campaignDeviceOSTargetBid);
             campaignDeviceOSTarget.setBids(campaignDeviceOSTargetBids);
             campaignTarget.setDeviceOS(campaignDeviceOSTarget);

             LocationTarget campaignLocationTarget = new LocationTarget();
             campaignLocationTarget.setIntentOption(IntentOption.PEOPLE_IN_OR_SEARCHING_FOR_OR_VIEWING_PAGES);

             RadiusTarget campaignRadiusTarget = new RadiusTarget();
             RadiusTargetBid campaignRadiusTargetBid = new RadiusTargetBid();
             campaignRadiusTargetBid.setBidAdjustment(50);
             campaignRadiusTargetBid.setLatitudeDegrees(47.755367);
             campaignRadiusTargetBid.setLongitudeDegrees(-122.091827);
             campaignRadiusTargetBid.setRadius(5);
             campaignRadiusTargetBid.setRadiusUnit(DistanceUnit.KILOMETERS);
             ArrayOfRadiusTargetBid campaignRadiusTargetBids = new ArrayOfRadiusTargetBid();
             campaignRadiusTargetBids.getRadiusTargetBids().add(campaignRadiusTargetBid);
             campaignRadiusTarget.setBids(campaignRadiusTargetBids);
             campaignLocationTarget.setRadiusTarget(campaignRadiusTarget);
             campaignTarget.setLocation(campaignLocationTarget);

             Target adGroupTarget = new Target();
             adGroupTarget.setName("My Ad Group Target");

             DayTimeTarget adGroupDayTimeTarget = new DayTimeTarget();
             DayTimeTargetBid adGroupDayTimeTargetBid = new DayTimeTargetBid();
             adGroupDayTimeTargetBid.setBidAdjustment(10);
             adGroupDayTimeTargetBid.setDay(Day.FRIDAY);
             adGroupDayTimeTargetBid.setFromHour(1);
             adGroupDayTimeTargetBid.setToHour(12);
             adGroupDayTimeTargetBid.setFromMinute(Minute.ZERO);
             adGroupDayTimeTargetBid.setToMinute(Minute.FORTY_FIVE);
             ArrayOfDayTimeTargetBid adGroupDayTimeTargetBids = new ArrayOfDayTimeTargetBid();
             adGroupDayTimeTargetBids.getDayTimeTargetBids().add(adGroupDayTimeTargetBid);
             adGroupDayTimeTarget.setBids(adGroupDayTimeTargetBids);
             adGroupTarget.setDayTime(adGroupDayTimeTarget);

             // Each customer has a target library that can be used to set up targeting for any campaign
             // or ad group within the specified customer. 

             // Add a target to the library and associate it with the campaign.
             ArrayOfTarget targets = new ArrayOfTarget();
             targets.getTargets().add(campaignTarget);
             long campaignTargetId = addTargetsToLibrary(targets).getLongs().get(0);
             outputStatusMessage(String.format("Added Target Id: %d\n\n", campaignTargetId));
             setTargetToCampaign(campaignIds.getLongs().get(0), campaignTargetId);
             outputStatusMessage(String.format("Associated CampaignId %d with TargetId %d.\n\n", campaignIds.getLongs().get(0), campaignTargetId));

             // Get and print the Target with the GetTargetsByIds operation
             outputStatusMessage("Get Campaign Target: \n");
             ArrayOflong targetIds = new ArrayOflong();
             targetIds.getLongs().add(campaignTargetId);
             targets = getTargetsByIds(targetIds);
             outputTarget(targets.getTargets().get(0));

             // Add a target to the library and associate it with the ad group.
             targets = new ArrayOfTarget();
             targets.getTargets().add(adGroupTarget);
             long adGroupTargetId = addTargetsToLibrary(targets).getLongs().get(0);
             outputStatusMessage(String.format("Added Target Id: %d\n\n", adGroupTargetId));
             setTargetToAdGroup(adGroupIds.getLongs().get(0), adGroupTargetId);
             outputStatusMessage(String.format("Associated AdGroupId %d with TargetId %d.\n\n", adGroupIds.getLongs().get(0), adGroupTargetId));

             // Get and print the Target with the GetTargetsByIds operation
             outputStatusMessage("Get AdGroup Target: \n");
             targetIds = new ArrayOflong();
             targetIds.getLongs().add(adGroupTargetId);
             targets = getTargetsByIds(targetIds);
             outputTarget(targets.getTargets().get(0));

             // Update the ad group's Target object with additional target types.
             // Existing target types such as DayTime must be specified 
             // or they will not be included in the updated target.

             Target target = new Target();
             target.setId(adGroupTargetId);
             target.setName("My Target");

             AgeTarget ageTarget = new AgeTarget();
             AgeTargetBid ageTargetBid = new AgeTargetBid();
             ageTargetBid.setBidAdjustment(10);
             ageTargetBid.setAge(AgeRange.EIGHTEEN_TO_TWENTY_FIVE);
             ArrayOfAgeTargetBid ageTargetBids = new ArrayOfAgeTargetBid();
             ageTargetBids.getAgeTargetBids().add(ageTargetBid);
             ageTarget.setBids(ageTargetBids);
             target.setAge(ageTarget);

             DayTimeTarget dayTimeTarget = new DayTimeTarget();
             DayTimeTargetBid dayTimeTargetBid = new DayTimeTargetBid();
             dayTimeTargetBid.setBidAdjustment(10);
             dayTimeTargetBid.setDay(Day.FRIDAY);
             dayTimeTargetBid.setFromHour(1);
             dayTimeTargetBid.setToHour(12);
             dayTimeTargetBid.setFromMinute(Minute.ZERO);
             dayTimeTargetBid.setToMinute(Minute.FORTY_FIVE);
             ArrayOfDayTimeTargetBid dayTimeTargetBids = new ArrayOfDayTimeTargetBid();
             dayTimeTargetBids.getDayTimeTargetBids().add(dayTimeTargetBid);
             dayTimeTarget.setBids(dayTimeTargetBids);
             target.setDayTime(dayTimeTarget);

             DeviceOSTarget deviceOSTarget = new DeviceOSTarget();
             DeviceOSTargetBid deviceOSTargetBid = new DeviceOSTargetBid();
             deviceOSTargetBid.setBidAdjustment(20);
             deviceOSTargetBid.setDeviceName("Tablets");
             ArrayOfDeviceOSTargetBid deviceOSTargetBids = new ArrayOfDeviceOSTargetBid();
             deviceOSTargetBids.getDeviceOSTargetBids().add(deviceOSTargetBid);
             deviceOSTarget.setBids(deviceOSTargetBids);
             target.setDeviceOS(deviceOSTarget);

             GenderTarget genderTarget = new GenderTarget();
             GenderTargetBid genderTargetBid = new GenderTargetBid();
             genderTargetBid.setBidAdjustment(10);
             genderTargetBid.setGender(GenderType.FEMALE);
             ArrayOfGenderTargetBid genderTargetBids = new ArrayOfGenderTargetBid();
             genderTargetBids.getGenderTargetBids().add(genderTargetBid);
             genderTarget.setBids(genderTargetBids);
             target.setGender(genderTarget);

             LocationTarget locationTarget = new LocationTarget();
             locationTarget.setIntentOption(IntentOption.PEOPLE_SEARCHING_FOR_OR_VIEWING_PAGES);

             CountryTarget countryTarget = new CountryTarget();
             CountryTargetBid countryTargetBid = new CountryTargetBid();
             countryTargetBid.setBidAdjustment(10);
             countryTargetBid.setCountryAndRegion("US");
             countryTargetBid.setIsExcluded(false);
             ArrayOfCountryTargetBid countryTargetBids = new ArrayOfCountryTargetBid();
             countryTargetBids.getCountryTargetBids().add(countryTargetBid);
             countryTarget.setBids(countryTargetBids);
             locationTarget.setCountryTarget(countryTarget);

             PostalCodeTarget postalCodeTarget = new PostalCodeTarget();
             PostalCodeTargetBid postalCodeTargetBid = new PostalCodeTargetBid();
             postalCodeTargetBid.setBidAdjustment(10);
             postalCodeTargetBid.setPostalCode("98052, WA US");
             postalCodeTargetBid.setIsExcluded(false);
             ArrayOfPostalCodeTargetBid postalCodeTargetBids = new ArrayOfPostalCodeTargetBid();
             postalCodeTargetBids.getPostalCodeTargetBids().add(postalCodeTargetBid);
             postalCodeTarget.setBids(postalCodeTargetBids);
             locationTarget.setPostalCodeTarget(postalCodeTarget);

             RadiusTarget radiusTarget = new RadiusTarget();
             RadiusTargetBid radiusTargetBid = new RadiusTargetBid();
             radiusTargetBid.setBidAdjustment(50);
             radiusTargetBid.setLatitudeDegrees(47.755367);
             radiusTargetBid.setLongitudeDegrees(-122.091827);
             radiusTargetBid.setRadius(11);
             radiusTargetBid.setRadiusUnit(DistanceUnit.KILOMETERS);
             ArrayOfRadiusTargetBid radiusTargetBids = new ArrayOfRadiusTargetBid();
             radiusTargetBids.getRadiusTargetBids().add(radiusTargetBid);
             radiusTarget.setBids(radiusTargetBids);
             locationTarget.setRadiusTarget(radiusTarget);
             target.setLocation(locationTarget);

             // Update the Target object associated with the ad group. 
             targets = new ArrayOfTarget();
             targets.getTargets().add(target);
             updateTargetsInLibrary(targets);
             outputStatusMessage("Updated the ad group level target as a Target object.\n");

             ArrayOflong campaignTargetIds = new ArrayOflong();
             campaignTargetIds.getLongs().add(campaignTargetId);
             ArrayOflong adGroupTargetIds = new ArrayOflong();
             adGroupTargetIds.getLongs().add(adGroupTargetId);

             // Get and print the campaign Target with the GetTargetsByIds operation
             outputStatusMessage("Get Campaign Target: \n");
             targets = getTargetsByIds(campaignTargetIds);
             outputTarget(targets.getTargets().get(0));

             // Get and print the ad group Target with the GetTargetsByIds operation
             outputStatusMessage("Get AdGroup Target: \n");
             targets = getTargetsByIds(adGroupTargetIds);
             outputTarget(targets.getTargets().get(0));

             // Get all new and existing targets in the customer library, whether or not they are
             // associated with campaigns or ad groups.

             ArrayOfTargetInfo allTargetsInfo = getTargetsInfoFromLibrary();
             outputStatusMessage("All target identifiers and names from the customer library: \n");
             outputTargetInfos(allTargetsInfo);

             // Delete the campaign, ad group, and targets that were previously added. 
             // DeleteCampaigns would remove the campaign and ad group, as well as the association
             // between ad groups and campaigns. To explicitly delete the association between an entity 
             // and the target, use DeleteTargetFromCampaign and DeleteTargetFromAdGroup respectively.

             deleteTargetFromCampaign(campaignIds.getLongs().get(0));
             deleteTargetFromAdGroup(adGroupIds.getLongs().get(0));

             ArrayOflong deleteCampaignIds = new ArrayOflong();
             deleteCampaignIds.getLongs().add(campaignIds.getLongs().get(0));
             deleteCampaigns(AccountId, deleteCampaignIds);
             outputStatusMessage(String.format("Deleted CampaignId %d\n\n", campaignIds.getLongs().get(0)));

             // DeleteCampaigns deletes the association between the campaign and target, but does not 
             // delete the target from the customer library. 
             // Call the DeleteTargetsFromLibrary operation for each target that you want to delete. 
             // You must specify an array with exactly one item.

             ArrayOflong deleteCampaignTargetIds = new ArrayOflong();
             deleteCampaignTargetIds.getLongs().add(campaignTargetId);
             deleteTargetsFromLibrary(deleteCampaignTargetIds);
             outputStatusMessage(String.format("Deleted TargetId %d\n\n", campaignTargetId));

             ArrayOflong deleteAdGroupTargetIds = new ArrayOflong();
             deleteAdGroupTargetIds.getLongs().add(adGroupTargetId);
             deleteTargetsFromLibrary(deleteAdGroupTargetIds);
             outputStatusMessage(String.format("Deleted TargetId %d\n\n", adGroupTargetId));

         // Campaign Management service operations can throw AdApiFaultDetail.
         } catch (AdApiFaultDetail_Exception ex) {
             outputStatusMessage("The operation failed with the following faults:\n");

             for (AdApiError error : ex.getFaultInfo().getErrors().getAdApiErrors())
             {
                 outputStatusMessage("AdApiError\n");
                 outputStatusMessage(String.format("Code: %d\nError Code: %s\nMessage: %s\n\n", error.getCode(), error.getErrorCode(), error.getMessage()));
             }

         // Campaign Management service operations can throw ApiFaultDetail.
         } catch (ApiFaultDetail_Exception ex) {
             outputStatusMessage("The operation failed with the following faults:\n");

             for (BatchError error : ex.getFaultInfo().getBatchErrors().getBatchErrors())
             {
                 outputStatusMessage(String.format("BatchError at Index: %d\n", error.getIndex()));
                 outputStatusMessage(String.format("Code: %d\nMessage: %s\n\n", error.getCode(), error.getMessage()));
             }

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

  // Adds one or more campaigns to the specified account.

     static AddCampaignsResponse addCampaigns(long accountId, ArrayOfCampaign campaigns) throws RemoteException, Exception
     {
         AddCampaignsRequest request = new AddCampaignsRequest();

         // Set the request information.

         request.setAccountId(accountId);
         request.setCampaigns(campaigns);

         return CampaignService.getService().addCampaigns(request);
     }

     // Deletes one or more campaigns from the specified account.

     static void deleteCampaigns(long accountId, ArrayOflong campaignIds) throws RemoteException, Exception
     {
    	 DeleteCampaignsRequest request = new DeleteCampaignsRequest();

         // Set the request information.

         request.setAccountId(accountId);
         request.setCampaignIds(campaignIds);

         CampaignService.getService().deleteCampaigns(request);
     }

     // Adds one or more ad groups to the specified campaign.

     static AddAdGroupsResponse addAdGroups(long campaignId, ArrayOfAdGroup adGroups) throws RemoteException, Exception
     {
         AddAdGroupsRequest request = new AddAdGroupsRequest();

         // Set the request information.

         request.setCampaignId(campaignId);
         request.setAdGroups(adGroups);

         return CampaignService.getService().addAdGroups(request);
     }

     // Gets all target info from the customer library.

     static ArrayOfTargetInfo getTargetsInfoFromLibrary() throws RemoteException, Exception
     {
    	 GetTargetsInfoFromLibraryRequest request = new GetTargetsInfoFromLibraryRequest();

         return CampaignService.getService().getTargetsInfoFromLibrary(request).getTargetsInfo();
     }

     // Gets the list of Target objects given the specified target identifiers.

     static ArrayOfTarget getTargetsByIds(ArrayOflong targetIds) throws RemoteException, Exception
     {
    	 GetTargetsByIdsRequest request = new GetTargetsByIdsRequest();

         request.setTargetIds(targetIds);

         return CampaignService.getService().getTargetsByIds(request).getTargets();
     }

     // Adds the specified Target object to the customer library. 
     // The operation requires exactly one Target in a list.

     static ArrayOflong addTargetsToLibrary(ArrayOfTarget targets) throws RemoteException, Exception
     {
    	 AddTargetsToLibraryRequest request = new AddTargetsToLibraryRequest();

         request.setTargets(targets);

         return CampaignService.getService().addTargetsToLibrary(request).getTargetIds();
     }

     // Updates the specified Target object within the customer library. 
     // The operation requires exactly one Target in a list.

     static void updateTargetsInLibrary(ArrayOfTarget targets) throws RemoteException, Exception
     {
    	 UpdateTargetsInLibraryRequest request = new UpdateTargetsInLibraryRequest();

         request.setTargets(targets);

         CampaignService.getService().updateTargetsInLibrary(request);
     }

     // Deletes the specified target from the customer library. 
     // The operation requires exactly one identifier in a list.

     static void deleteTargetsFromLibrary(ArrayOflong targetIds) throws RemoteException, Exception
     {
    	 DeleteTargetsFromLibraryRequest request = new DeleteTargetsFromLibraryRequest();

         request.setTargetIds(targetIds);

         CampaignService.getService().deleteTargetsFromLibrary(request);
     }

     // Removes the target association from the specified campaign. 
     // Does not delete the target or the campaign.

     static void deleteTargetFromCampaign(long campaignId) throws RemoteException, Exception
     {
    	 DeleteTargetFromCampaignRequest request = new DeleteTargetFromCampaignRequest();

         request.setCampaignId(campaignId);

         CampaignService.getService().deleteTargetFromCampaign(request);
     }

     // Removes the target association from the specified ad group. 
     // Does not delete the target or the ad group.

     static void deleteTargetFromAdGroup(long adGroupId) throws RemoteException, Exception
     {
    	 DeleteTargetFromAdGroupRequest request = new DeleteTargetFromAdGroupRequest();

         request.setAdGroupId(adGroupId);

         CampaignService.getService().deleteTargetFromAdGroup(request);
     }

     // Associates the specified campaign and target.

     static void setTargetToCampaign(long campaignId, long targetId) throws RemoteException, Exception
     {
    	 SetTargetToCampaignRequest request = new SetTargetToCampaignRequest();

         request.setCampaignId(campaignId);
         request.setTargetId(targetId);

         CampaignService.getService().setTargetToCampaign(request);
     }

     // Associates the specified ad group and target.

     static void setTargetToAdGroup(long adGroupId, long targetId) throws RemoteException, Exception
     {
    	 SetTargetToAdGroupRequest request = new SetTargetToAdGroupRequest();

         request.setAdGroupId(adGroupId);
         request.setTargetId(targetId);

         CampaignService.getService().setTargetToAdGroup(request);
     }

     // Outputs the info for each target. 

     static void outputTargetInfos(ArrayOfTargetInfo targetInfos)
     {
         if (targetInfos == null)
         {
             return;
         }

         for (TargetInfo info : targetInfos.getTargetInfos())
         {
             outputStatusMessage(String.format("Target Id: %d\n", info.getId()));
             outputStatusMessage(String.format("Target Name: %s\n\n", info.getName()));
         }
     }

     // Outputs the specified Target object. 

     static void outputTarget(Target target)
     {
         if (target == null)
         {
             return;
         }

         outputStatusMessage(String.format("Target Id: %d\n", target.getId()));
         outputStatusMessage(String.format("Target Name: %s\n\n", target.getName()));

         if (target.getAge() != null)
         {
             outputStatusMessage("AgeTarget:");
             for (AgeTargetBid bid : target.getAge().getBids().getAgeTargetBids())
             {
                 outputStatusMessage(String.format("\tBidAdjustment: %d\n", bid.getBidAdjustment()));
                 outputStatusMessage(String.format("\tAge: %s\n\n", bid.getAge()));
             }
         }
         if (target.getDayTime() != null)
         {
             outputStatusMessage("DayTimeTarget:");
             for (DayTimeTargetBid bid : target.getDayTime().getBids().getDayTimeTargetBids())
             {
                 outputStatusMessage(String.format("\tBidAdjustment: %d\n", bid.getBidAdjustment()));
                 outputStatusMessage(String.format("\tDay: %s\n", bid.getDay()));
                 outputStatusMessage(String.format("\tFromHour: %s\n", bid.getFromHour()));
                 outputStatusMessage(String.format("\tToHour: %s\n", bid.getToHour()));
                 outputStatusMessage(String.format("\tFromMinute: %s\n", bid.getFromMinute()));
                 outputStatusMessage(String.format("\tToMinute: %s\n\n", bid.getToMinute()));
             }
         }
         if (target.getDeviceOS() != null)
         {
             outputStatusMessage("DeviceOSTarget:");
             for (DeviceOSTargetBid bid : target.getDeviceOS().getBids().getDeviceOSTargetBids())
             {
                 outputStatusMessage(String.format("\tBidAdjustment: %d\n", bid.getBidAdjustment()));
                 outputStatusMessage(String.format("\tDeviceName: %s\n", bid.getDeviceName()));
                 outputStatusMessage("");
             }
         }
         if (target.getGender() != null)
         {
             outputStatusMessage("GenderTarget:");
             for (GenderTargetBid bid : target.getGender().getBids().getGenderTargetBids())
             {
                 outputStatusMessage(String.format("\tBidAdjustment: %d\n", bid.getBidAdjustment()));
                 outputStatusMessage(String.format("\tGender: %s\n\n", bid.getGender()));
             }
         }
         if (target.getLocation() != null)
         {
             outputStatusMessage("LocationTarget:");
             outputStatusMessage(String.format("\tIntentOption: %s\n\n", target.getLocation().getIntentOption()));
             if (target.getLocation().getCityTarget() != null)
             {
                 outputStatusMessage("\tCityTarget:");
                 for (CityTargetBid bid : target.getLocation().getCityTarget().getBids().getCityTargetBids())
                 {
                     outputStatusMessage(String.format("\t\tBidAdjustment: %s\n", bid.getBidAdjustment()));
                     outputStatusMessage(String.format("\t\tCity: %s\n\n", bid.getCity()));
                 }
             }
             if (target.getLocation().getCountryTarget() != null)
             {
                 outputStatusMessage("\tCountryTarget:");
                 for (CountryTargetBid bid : target.getLocation().getCountryTarget().getBids().getCountryTargetBids())
                 {
                     outputStatusMessage(String.format("\t\tBidAdjustment: %d\n", bid.getBidAdjustment()));
                     outputStatusMessage(String.format("\t\tCountryAndRegion: %s\n", bid.getCountryAndRegion()));
                     outputStatusMessage(String.format("\t\tIsExcluded: %s\n\n", bid.isIsExcluded() ? "True" : "False"));
                 }
             }
             if (target.getLocation().getMetroAreaTarget() != null)
             {
                 outputStatusMessage("\tMetroAreaTarget:");
                 for (MetroAreaTargetBid bid : target.getLocation().getMetroAreaTarget().getBids().getMetroAreaTargetBids())
                 {
                     outputStatusMessage(String.format("\t\tBidAdjustment: %d\n", bid.getBidAdjustment()));
                     outputStatusMessage(String.format("\t\tMetroArea: %s\n", bid.getMetroArea()));
                     outputStatusMessage(String.format("\t\tIsExcluded: %s\n\n", bid.isIsExcluded() ? "True" : "False"));
                 }
             }
             if (target.getLocation().getPostalCodeTarget() != null)
             {
                 outputStatusMessage("\tPostalCodeTarget:");
                 for (PostalCodeTargetBid bid : target.getLocation().getPostalCodeTarget().getBids().getPostalCodeTargetBids())
                 {
                     outputStatusMessage(String.format("\t\tBidAdjustment: %d\n", bid.getBidAdjustment()));
                     outputStatusMessage(String.format("\t\tPostalCode: %s\n", bid.getPostalCode()));
                     outputStatusMessage(String.format("\t\tIsExcluded: %s\n\n", bid.isIsExcluded() ? "True" : "False"));
                 }
             }
             if (target.getLocation().getRadiusTarget() != null)
             {
                 outputStatusMessage("\tRadiusTarget:");
                 for (RadiusTargetBid bid : target.getLocation().getRadiusTarget().getBids().getRadiusTargetBids())
                 {
                     outputStatusMessage(String.format("\t\tBidAdjustment: %d\n", bid.getBidAdjustment()));
                     outputStatusMessage(String.format("\t\tLatitudeDegrees: %f\n", bid.getLatitudeDegrees()));
                     outputStatusMessage(String.format("\t\tLongitudeDegrees: %f\n", bid.getLongitudeDegrees()));
                     outputStatusMessage(String.format("\t\tRadius: %s %s\n\n", bid.getRadius(), bid.getRadiusUnit()));
                 }
             }
             if (target.getLocation().getStateTarget() != null)
             {
                 outputStatusMessage("\tStateTarget:");
                 for (StateTargetBid bid : target.getLocation().getStateTarget().getBids().getStateTargetBids())
                 {
                     outputStatusMessage(String.format("\t\tBidAdjustment: %d\n", bid.getBidAdjustment()));
                     outputStatusMessage(String.format("\t\tState: %s\n", bid.getState()));
                     outputStatusMessage(String.format("\t\tIsExcluded: %s\n\n", bid.isIsExcluded() ? "True" : "False"));
                 }
             }
         }

         outputStatusMessage("");
     }

  // Prints the campaign identifiers, as well as any partial errors

     static void outputCampaignsWithPartialErrors(ArrayOfCampaign campaigns, ArrayOfNullableOflong campaignIds, ArrayOfBatchError partialErrors)
     {
         if (campaignIds == null)
         {
             return;
         }

         // Print the identifier of each successfully added campaign.

         for (int index = 0; index < campaigns.getCampaigns().size(); index++ )
         {
             // The array of keyword identifiers equals the size of the attempted campaigns. If the element 
             // is not null, the campaign at that index was added successfully and has a campaign identifier. 

             if (campaignIds.getLongs().get(index) != null)
             {
                 outputStatusMessage(String.format("Campaign[%d] (Name:%s) successfully added and assigned CampaignId %d\n", 
                     index,  
                     campaigns.getCampaigns().get(index).getName(),
                     campaignIds.getLongs().get(index)));
             }
         }

         // Print the error details for any campaign not successfully added.
         // Note also that multiple error reasons may exist for the same attempted campaign.

         for (BatchError error : partialErrors.getBatchErrors())
         {
             // The index of the partial errors is equal to the index of the list
             // specified in the call to AddCampaigns.

             outputStatusMessage(String.format("\nCampaign[%d] (Name:%s) not added due to the following error:\n", 
            		 error.getIndex(), campaigns.getCampaigns().get(error.getIndex()).getName()));

             outputStatusMessage(String.format("\tIndex: %d\n", error.getIndex()));
             outputStatusMessage(String.format("\tCode: %d\n", error.getCode()));
             outputStatusMessage(String.format("\tErrorCode: %s\n", error.getErrorCode()));
             outputStatusMessage(String.format("\tMessage: %s\n", error.getMessage()));

             // In the case of an EditorialError, more details are available
             if (error.getType().equals("EditorialError") && error.getErrorCode().equals("CampaignServiceEditorialValidationError"))
             {
                 outputStatusMessage(String.format("\tDisapprovedText: %s\n", ((EditorialError)(error)).getDisapprovedText()));
                 outputStatusMessage(String.format("\tLocation: %s\n", ((EditorialError)(error)).getLocation()));
                 outputStatusMessage(String.format("\tPublisherCountry: %s\n", ((EditorialError)(error)).getPublisherCountry()));
                 outputStatusMessage(String.format("\tReasonCode: %d\n", ((EditorialError)(error)).getReasonCode()));
             }
         }

         outputStatusMessage("");
     }

     // Prints the ad group identifiers, as well as any partial errors

     static void outputAdGroupsWithPartialErrors(ArrayOfAdGroup adGroups, ArrayOfNullableOflong adGroupIds, ArrayOfBatchError partialErrors)
     {
         if (adGroupIds == null)
         {
             return;
         }

         // Print the identifier of each successfully added ad group.

         for (int index = 0; index < adGroups.getAdGroups().size(); index++ )
         {
             // The array of ad group identifiers equals the size of the attempted ad group. If the element 
             // is not null, the ad group at that index was added successfully and has an ad group identifier. 

             if (adGroupIds.getLongs().get(index) != null)
             {
                 outputStatusMessage(String.format("AdGroup[%d] (Name:%s) successfully added and assigned AdGroupId %d\n", 
                     index,  
                     adGroups.getAdGroups().get(index).getName(),
                     adGroupIds.getLongs().get(index)));
             }
         }

         // Print the error details for any ad group not successfully added.
         // Note also that multiple error reasons may exist for the same attempted ad group.

         for (BatchError error : partialErrors.getBatchErrors())
         {
             // The index of the partial errors is equal to the index of the list
             // specified in the call to AddAdGroups.

             outputStatusMessage(String.format("\nAdGroup[%d] (Name:%s) not added due to the following error:\n", 
            		 error.getIndex(), adGroups.getAdGroups().get(error.getIndex()).getName()));

             outputStatusMessage(String.format("\tIndex: %d\n", error.getIndex()));
             outputStatusMessage(String.format("\tCode: %d\n", error.getCode()));
             outputStatusMessage(String.format("\tErrorCode: %s\n", error.getErrorCode()));
             outputStatusMessage(String.format("\tMessage: %s\n", error.getMessage()));

             // In the case of an EditorialError, more details are available
             if (error.getType().equals("EditorialError") && error.getErrorCode().equals("CampaignServiceEditorialValidationError"))
             {
                 outputStatusMessage(String.format("\tDisapprovedText: %s\n", ((EditorialError)(error)).getDisapprovedText()));
                 outputStatusMessage(String.format("\tLocation: %s\n", ((EditorialError)(error)).getLocation()));
                 outputStatusMessage(String.format("\tPublisherCountry: %s\n", ((EditorialError)(error)).getPublisherCountry()));
                 outputStatusMessage(String.format("\tReasonCode: %d\n", ((EditorialError)(error)).getReasonCode()));
             }
         }

         outputStatusMessage("");
     }
 }
```

## See Also
[Getting Started Using Java with Bing Ads Services](../../concepts/get-started/getting-started-using-java-with-bing-ads-services.md)  
