# SwaggerAuthenticationWithAzureAd_Dotnet6
Enable authentication in swagger UI for azure AD
<h2>Create 2 App Registrations in Azure AD</h2>
<p>The First App registration will be for the webAPI (swaggerwebapi) (Image: 1)
   <ul> 
      <li> Expose a scope in the WebAPI (Image: 2). We have exposed a scope called <b> read </b>in this case We will grant the swagger app registration access to this scope in the subsequent steps </li>  
       <li>Change the token version to 2 so that any application that requests a token for this webapi will be returned a v2 token.  (Image 7) </li>   
   </ul>
 </p>
<p>The Create 2nd App registration for the swagger App (SwaggerAuthApp) (Image: 3)
   <ul> 
      <li>Add a redirect URL for the APP. The token will be recevied on this URL (Image 4).  </li>   
      <li>Grant the app access to the scope that the web api exposes.  (Image 5). (image 6)  </li>   
   </ul>
</p>
