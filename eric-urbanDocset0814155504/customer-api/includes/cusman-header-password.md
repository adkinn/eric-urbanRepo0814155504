These request headers are required for legacy username and password authentication.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DeveloperToken*|The developer token used to access the Bing Ads API.|*string*|
|*Password*|The Bing Ads user's sign-in password.|*string*|
|*UserName*|The Bing Ads user's sign-in user name. You must not set this element to a Microsoft account or email address. To authenticate a Microsoft account, use the *AuthenticationToken* header instead of *UserName* and *Password*.|*string*|
