---
title: Blazored Toast Notifications
author: danijeljw-rpc
date: 2023-04-23 00:00:00 +1000
categories: [C#, Blazor]
tags: [swagger, C#, blazor, wasm, toast]
math: true
mermaid: true 
image:
  path: /assets/image/2023/04/24/Toast-Bread.png
  alt: Toast
---

A beautiful library by Chris Sainty called [Blazored Toast](https://github.com/Blazored/Toast) for adding toast notifications to Blazor projects.

![Screenshot of component in action](https://github.com/Blazored/Toast/raw/main/screenshot.png)

```powershell
Install-Package Blazored.Toast
```

Or via the dotnet CLI.

```bash
dotnet add package Blazored.Toast
```

### 1. Register Services
You will need to register the Blazored Toast service in your application

#### Blazor Server
Add the following line to your applications `Startup.ConfigureServices` method.

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddBlazoredToast();
}
```

#### Blazor WebAssembly
Add the following line to your applications `Program.Main` method before `await builder.Build().RunAsync();`:

```csharp
builder.Services.AddBlazoredToast();
```

### 2. Add Imports
Add the following to your *_Imports.razor*

```razor
@using Blazored.Toast
@using Blazored.Toast.Services
```

### 3. Add reference to CSS
If your app is using CSS isolation, add the following to your `index.html`:

```razor
<link href="{YOUR APP ASSEMBLY NAME}.styles.css" rel="stylesheet">
```

### 4. Register and Configure Toasts Component
Add the `<BlazoredToasts />` tag into your applications *MainLayout.razor*:

```razor
<BlazoredToasts Position="ToastPosition.BottomRight"
                ShowProgressBar="true"
                IconType="IconType.FontAwesome"
                SuccessClass="success-toast-override"
                ErrorIcon="fa fa-bug"
                SuccessIcon="fa fa-thumbs-up" />
```

