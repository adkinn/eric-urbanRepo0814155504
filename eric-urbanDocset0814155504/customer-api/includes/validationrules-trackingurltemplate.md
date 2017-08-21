The following validation rules apply to tracking templates.

-   Tracking templates defined for lower level entities e.g. keyword override those set for higher level entities e.g. campaign. For more information, see [Entity Hierarchy and Limits](http://go.microsoft.com/fwlink/?LinkID=627130).

-   The length of the tracking template is limited to 2,048 characters.

    **Note:** The HTTP or HTTPS protocol string does count towards the 2,048 character limit.

-   The tracking template must be a well-formed URL beginning with one of the following: *http://*, *https://*, *{lpurl}*, or *{unescapedlpurl}*.

-   You must include at least one of the following landing page URL parameters: *{lpurl}*, *{lpurl+2}*, *{lpurl+3}*, *{unescapedlpurl}*, *{escapedlpurl}*. Additionally, you can use any dynamic parameter supported by Bing Ads. For a list of supported parameters, see the *Available parameters* sections within the Bing Ads help article [Set up a tracking template](https://help.bingads.microsoft.com/#apex/3/en/56772/-1).

-   Bing Ads does not validate whether custom parameters exist. If you use custom parameters in your tracking template and they do not exist, then the final URL will include the key and value placeholders of your custom parameters without substitution. For example if your tracking template is  for example *http://tracker.example.com/?season={_season}&promocode={_promocode}&u={lpurl}*, and neither {_season} or {_promocode}  are defined at the campaign, ad group, keyword, or ad level, then the final URL will be the same.
