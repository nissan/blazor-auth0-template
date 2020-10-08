# Blazor Auth0 Template
This holds "Getting started" code for building a Blazor Server Side or Blazor WebAssembly application that already includes Auth0 integration components configurable from a settings file.

[Reference article for Blazor Server Side application](https://auth0.com/blog/what-is-blazor-tutorial-on-building-webapp-with-authentication/)

The following snippet must be added to the appsettings.json file once downloaded with your specific Auth0 parameters
```json
"Auth0": {
    "Domain": "YOUR_AUTH0_DOMAIN",
    "ClientId": "YOUR_CLIENT_ID",
    "ClientSecret": "YOUR_CLIENT_SECRET"
  }
```
