These request headers are required for legacy username and password authentication.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CustomerAccountId*|The identifier of the account that owns the entities in the request. This header element must have the same value as the *AccountId* body element when both are required.<br /><br />Required for most service operations, and as a best practice you should always specify this element.|*string*|
|*CustomerId*|The identifier of the customer that contains and owns the account. If you manage an account of another customer, you should use that customer ID instead of your own customer ID.<br /><br />Required for most service operations, and as a best practice you should always specify this element.|*string*|
|*DeveloperToken*|The developer token used to access the Bing Ads API.|*string*|
|*Password*|The Bing Ads user's sign-in password.|*string*|
|*UserName*|The Bing Ads user's sign-in user name. You must not set this element to a Microsoft account or email address. To authenticate a Microsoft account, use the *AuthenticationToken* header instead of *UserName* and *Password*.|*string*|
