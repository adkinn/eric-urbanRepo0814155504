---
title: "Geographical Locations in Python"
ms.custom: na
ms.date: "07/10/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: d1a1133c-2fa5-4d07-83eb-a09c93143de8
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Geographical Locations in Python
The following example shows how to download the comma separated value (CSV) file that contains geographical location information 
 that can be used with [!INCLUDE[brand](../guides/includes/brand.md)] location targeting. For more information, see [Geographical Location Codes](../guides/geographical-location-codes.md).

> [!NOTE]
> The example assumes that you have access to the "c:\geolocations" directory. You should modify the source as needed, or create the "c:\geolocations" directory.

```python
import urllib.request as urllib2

from auth_helper import *
from output_helper import *

# You must provide credentials in auth_helper.py.

# The full path to the local machine's copy of the geographical locations file.
LOCAL_FILE="c:\geolocations\geolocations.csv"

# The language and locale of the geographical locations file available for download.
# This example uses 'en' (English). Supported locales are 'zh-Hant' (Traditional Chinese), 'en' (English), 'fr' (French), 
# 'de' (German), 'it' (Italian), 'pt-BR' (Portuguese - Brazil), and 'es' (Spanish). 

LANGUAGE_LOCALE = "en"

# The only supported file format version is 1.0. 

VERSION = "1.0"
       
def main(authorization_data):    
    try:
        get_geo_locations_file_url_response = campaign_service.GetGeoLocationsFileUrl(VERSION, LANGUAGE_LOCALE)

        request=urllib2.Request(get_geo_locations_file_url_response.FileUrl)
        response=urllib2.urlopen(request)
                
        if response.getcode() == 200:
            download_locations_file(response)
            print("Downloaded the geographical locations to {0}.\n".format(LOCAL_FILE))
        
        output_status_message("Program execution completed")

    except urllib2.URLError as ex:
        if hasattr(ex, 'code'):
            print("Error code: {0}".format(ex.code))
        elif hasattr(ex, 'reason'):
            print("Reason: {0}".format(ex.reason))
        
    except WebFault as ex:
        output_webfault_errors(ex)
    except Exception as ex:
        output_status_message(ex)

def download_locations_file(response):
    CHUNK=16 * 1024
    with open(LOCAL_FILE, 'wb') as f:
        while True:
            chunk=response.read(CHUNK)
            if not chunk: break
            f.write(chunk)
            f.flush()

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

