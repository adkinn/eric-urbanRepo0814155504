These request headers are required for [Authentication with OAuth](~/concepts/authentication-with-oauth.md).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AuthenticationToken*|The OAuth access token that represents a Microsoft Account user who has permissions to Bing Ads accounts.|*string*|
|*CustomerAccountId*|The identifier of the account that owns the entities in the request. This header element must have the same value as the AccountId body element when both are required.<br /><br />**Note:** Required for most service operations, and as a best practice you should always specify this element.|*string*|
|*CustomerId*|The identifier of the customer that contains and owns the account. If you manage an account of another customer, you should use that customer ID instead of your own customer ID.<br /><br />**Note:** Required for most service operations, and as a best practice you should always specify this element.|*string*|
|*DeveloperToken*|The developer token used to access the Bing Ads API.|*string*|
