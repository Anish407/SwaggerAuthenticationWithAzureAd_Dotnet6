# SwaggerAuthenticationWithAzureAd_Dotnet6
Enable authentication in swagger UI for azure AD
<h2>Create 2 App Registrations in Azure AD</h2>
<p>The First App registration will be for the webAPI (swaggerwebapi) <img src="https://github.com/Anish407/SwaggerAuthenticationWithAzureAd_Dotnet6/blob/master/SwaggerAzureADAuthentication/Images/1.png" />
   <ul> 
      <li> Expose a scope in the WebAPI 
         <img src="https://github.com/Anish407/SwaggerAuthenticationWithAzureAd_Dotnet6/blob/master/SwaggerAzureADAuthentication/Images/1.png" />
         We have exposed a scope called <b> read </b>in this case We will grant the swagger app registration access to this scope in the subsequent steps </li>  
       <li>Change the token version to 2 so that any application that requests a token for this webapi will be returned a v2 token.
         <img src="https://github.com/Anish407/SwaggerAuthenticationWithAzureAd_Dotnet6/blob/master/SwaggerAzureADAuthentication/Images/7.png" />
      </li>   
   </ul>
 </p>
<p>The Create 2nd App registration for the swagger App (SwaggerAuthApp) 
   <img src="https://github.com/Anish407/SwaggerAuthenticationWithAzureAd_Dotnet6/blob/master/SwaggerAzureADAuthentication/Images/3.png" />
   <ul> 
      <li>Add a redirect URL for the APP. The token will be recevied on this URL 
      <img src="https://github.com/Anish407/SwaggerAuthenticationWithAzureAd_Dotnet6/blob/master/SwaggerAzureADAuthentication/Images/4.png" />
      </li>   
      <li>Grant the app access to the scope that the web api exposes. 
        <img src="https://github.com/Anish407/SwaggerAuthenticationWithAzureAd_Dotnet6/blob/master/SwaggerAzureADAuthentication/Images/5.png" />
        <img src="https://github.com/Anish407/SwaggerAuthenticationWithAzureAd_Dotnet6/blob/master/SwaggerAzureADAuthentication/Images/6.png" />
      </li>   
   </ul>
</p>
<h2>Code changes</h2>
<p>
Go to <a href="https://github.com/Anish407/SwaggerAuthenticationWithAzureAd_Dotnet6/blob/master/SwaggerAzureADAuthentication/appsettings.json"> Appsettings.json</a>. We have defined 2 sections. One for the Web Api and one for the swagger App. The swagger app will ask the user to sign in and will aquire a token on behalf of the user and will add the token to the authorization header as a bearer token. This will be sent to the web api which will have azure ad authentication configured. So only a user with a valid token will be able to access the WeatherForecast controller. 
</p>
<p>
Install Microsoft.Identity.Web from nuget package. This package will have all the needed methods to configure azure AD authentication.
 Inside <a href="https://github.com/Anish407/SwaggerAuthenticationWithAzureAd_Dotnet6/blob/master/SwaggerAzureADAuthentication/Program.cs">Program.cs</a> at LN: 13 we have configured azure AD authentication based on the AzureAd section inside <a href="https://github.com/Anish407/SwaggerAuthenticationWithAzureAd_Dotnet6/blob/master/SwaggerAzureADAuthentication/appsettings.json">appsettings.json</a>
</p>

<h1>OUTPUT</h1>
<img src="https://github.com/Anish407/SwaggerAuthenticationWithAzureAd_Dotnet6/blob/master/SwaggerAzureADAuthentication/Images/final.gif"/>
