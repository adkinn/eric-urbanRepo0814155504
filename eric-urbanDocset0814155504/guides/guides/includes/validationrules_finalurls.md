The following validation rules apply to Final URLs and Final Mobile URLs.

- The length of the URL is limited to 2,048 characters.

    **Note:** The HTTP or HTTPS protocol string does count towards the 2,048 character limit.

- You may specify up to 10 items for both *FinalUrls* and *FinalMobileUrls*; however, only the first item in each list is used for delivery. The service allows up to 10 for potential forward compatibility.

- Usage of '{' and '}' is only allowed to delineate tags, for example "{lpurl}".

- Final URLs must each be a well-formed URL starting with either http:// or https://.

- If you specify *FinalMobileUrls*, you must also specify *FinalUrls*.

- You may not specify *FinalMobileUrls* if the device preference is set to mobile.
