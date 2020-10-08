# Blazor Auth0 Template
This holds "Getting started" code for building a Blazor Server Side or Blazor WebAssembly application that already includes Auth0 integration components configurable from a settings file.

## Reference documentation
- [Reference article for Blazor Server Side application][1]
- [Reference Documentation on user secrets][2]
- 
## Notes
The following snippet in the [reference article by Auth0][1] looks to the appsettings.json file once in production  for your specific Auth0 parameters
```json
"Auth0": {
    "Domain": "YOUR_AUTH0_DOMAIN",
    "ClientId": "YOUR_CLIENT_ID",
    "ClientSecret": "YOUR_CLIENT_SECRET"
  }
```

This code uses [user secrets][2] instead to set these values. 
For a given release pipeline these values can be injected dependent on the deployment environment targeted.
Secrets are set in development with the following commands
```bash
dotnet user-secrets init
dotnet user-secrets set "Auth0:Domain" "YOUR_AUTH0_DOMAIN"
dotnet user-secrets set "Auth0:ClientId" "YOUR_CLIENT_ID"
dotnet user-secrets set "Auth0:ClientSecret" "YOUR_CLIENT_SECRET"
```
After deploying, any new Razor Page created needs to have the following added to secure it
```csharp
@attribute [Authorize]
```

[1]: https://auth0.com/blog/what-is-blazor-tutorial-on-building-webapp-with-authentication/ 
[2]: https://docs.microsoft.com/en-us/aspnet/core/security/app-secrets?view=aspnetcore-3.1&tabs=windows
