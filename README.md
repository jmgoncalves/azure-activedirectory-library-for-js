Active Directory Authentication Library (ADAL) for JavaScript
====================================

Fork of [this](https://github.com/AzureAD/azure-activedirectory-library-for-js) that publishes vanilla ADAL as a Node module.

Active Directory Authentication Library for JavaScript (ADAL JS) helps you to use Azure AD for handling authentication in your single page applications.

## Versions
Current version - 1.0.16  
Minimum recommended version - 1.0.11  
You can find the changes for each version in the [change log](https://github.com/AzureAD/azure-activedirectory-library-for-js/blob/master/changelog.txt).

## Samples and Documentation

[We provide a full suite of sample applications and documentation on GitHub](https://github.com/azure-samples?query=active-directory) to help you get started with learning the Azure Identity system. This includes tutorials for native clients such as Windows, Windows Phone, iOS, OSX, Android, and Linux; and a detailed guide to registering your app with Azure Active Directory. We also provide full walkthroughs for authentication flows such as OAuth2, OpenID Connect, Graph API, and other awesome features.
 

## Community Help and Support

We leverage [Stack Overflow](http://stackoverflow.com/) to work with the community on supporting Azure Active Directory and its SDKs, including this one! We highly recommend you ask your questions on Stack Overflow (we're all on there!) Also browser existing issues to see if someone has had your question before. 

We recommend you use the "adal" tag so we can see it! Here is the latest Q&A on Stack Overflow for ADAL: [http://stackoverflow.com/questions/tagged/adal](http://stackoverflow.com/questions/tagged/adal)

## Security Reporting

If you find a security issue with our libraries or services please report it to [secure@microsoft.com](mailto:secure@microsoft.com) with as much detail as possible. Your submission may be eligible for a bounty through the [Microsoft Bounty](http://aka.ms/bugbounty) program. Please do not post security issues to GitHub Issues or any other public site. We will contact you shortly upon receiving the information. We encourage you to get notifications of when security incidents occur by visiting [this page](https://technet.microsoft.com/en-us/security/dd252948) and subscribing to Security Advisory Alerts.

## The Library

This is a GA released version. The current version is **1.0.16**.

You have multiple ways of getting ADAL JS:

Via NPM:

    npm install adal-vanilla

Via CDN:

    <!-- Latest compiled and minified JavaScript -->
    <script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.16/js/adal.min.js"></script>


CDN will be updated to latest version 1.0.16.


The adal.js source is [here](https://github.com/AzureAD/azure-activedirectory-library-for-js/tree/master/lib/adal.js).
## Samples, tests and documentation

For a sample demonstrating basic usage of ADAL JS please refer to [this repo](https://github.com/AzureADSamples/SinglePageApp-DotNet).

**To run tests**

    npm install
    bower install
    npm test

**Logging**

Log levels are mapped as:

    0: Error
    1: Warning
    2: Info
    3: Verbose

You can add the code below to app.js to turn on logging. Implement the `log` method depending on how you want to redirect logs.

    Logging = {
        level: 3,
        log: function (message) {
            console.log(message);
        }
    };
    
**documentation generation**
Install grunt; call

    grunt doc

### Multi-Tenant

By default, you have multi-tenant support. ADAL will set tenant to 'common', if it is not specified in the config. This allows any Microsoft account to authenticate to your application. If you are not interested in multi-tenant behavior, you will need to set the ```tenant``` property as shown above.

If you allow multi-tenant authentication, and you do not wish to allow all Microsoft account users to use your application, you must provide your own method of filtering the token issuers to only those tenants who are allowed to login.

### Cache Location
Default storage location is sessionStorage. You can specify localStorage in the config as well.

```js
adalAuthenticationServiceProvider.init(
        {
            // Config to specify endpoints and similar for your app
            clientId: 'cb68f72f...',
            cacheLocation: 'localStorage' // optional cache location default is sessionStorage
        },
        $httpProvider   // pass http provider to inject request interceptor to attach tokens
        );
```

### Security
Tokens are accessible from javascript since ADAL.JS is using HTML5 storage. Default storage option is sessionStorage, which keeps the tokens per session. You should ask user to login again for important operations on your app.
You should protect your site for XSS. Please check the article here: [https://www.owasp.org/index.php/XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet](https://www.owasp.org/index.php/XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet)

### Trusted Site settings in IE
If you put your site in the trusted site list, cookies are not accessible for iFrame requests. You need to remove protected mode for Internet zone or add the authority url for the login to the trusted sites as well.

### Known issues on Edge
Certain issues have been reported when using ADAL.js with the Microsoft Edge version 40.15063.0.0. Please take a look at [this page](https://github.com/AzureAD/azure-activedirectory-library-for-js/wiki/Known-issues-on-Edge) for details and work arounds before filing a new issue.

## We Value and Adhere to the Microsoft Open Source Code of Conduct

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
