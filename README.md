# Blazor Auth0 Template
This holds "Getting started" code for building a Blazor Server Side or Blazor WebAssembly application that already includes Auth0 integration components configurable from a settings file.

## Reference documentation
- [Reference article for Securing Blazor Server Side application with Auth0][1]
- [Reference article for Securing Blazor WebAssembly Apps with Auth0][3]
- [Reference Documentation on user secrets][2]
- 
## Notes

### Blazor Server Side Application
This application is self contained inside the `Demo.Blazor.Auth0.SS.WebApp` folder. A Github action has been
configured to use the `Dockerfile` in the root of the repository to build a docker container based on this Project.

The following snippet in the [reference article by Auth0 for securing Blazor Server Side applications][1] looks 
to the `appsettings.json` file once in production  for your specific Auth0 parameters
```json
"Auth0": {
    "Domain": "YOUR_AUTH0_DOMAIN",
    "ClientId": "YOUR_CLIENT_ID",
    "ClientSecret": "YOUR_CLIENT_SECRET"
  }
```

This code uses [user secrets][2] instead to set these values for development. 
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

### Blazor Web Assembly Application

The following snippet in the [reference article by Auth0 for securing Blazor WebAssembly applications][3] looks 
to the `appsettings.json` file inside the `Client\wwwroot` folder once in production for your specific Auth0 parameters:
```json
{
  "Auth0": {
    "Authority": "https://<YOUR_AUTH0_DOMAIN>",
    "ClientId": "<YOUR_CLIENT_ID>"
  }
}
```
The approach taken for a **Blazor Server Side Application** to use [user secrets][2] to obfuscate sensitive values
will not work as everything runs on the client side, 
so instead for this code the `appsettings.json` file is created in development but excluded when checking in the
source code by amending the repository's `.gitignore` with this file explicitly.
Any release will need to include a deployment step to create the appsettings.json file and 
insert the correct values for the target environment at this point.

## TODO 
- Secure the API side of the Blazor WebAssembly application


[1]: https://auth0.com/blog/what-is-blazor-tutorial-on-building-webapp-with-authentication/ 
[2]: https://docs.microsoft.com/en-us/aspnet/core/security/app-secrets?view=aspnetcore-3.1&tabs=windows
[3]: https://auth0.com/blog/securing-blazor-webassembly-apps/
