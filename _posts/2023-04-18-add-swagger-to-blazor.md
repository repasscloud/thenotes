---
title: Add Swagger to Blazor
author: danijeljw-rpc
date: 2023-03-22 00:00:00 +1000
categories: [C#, Blazor]
tags: [swagger, C#, blazor, wasm, swashbuckle]
math: true
mermaid: true 
image:
  path: /assets/image/2023/04/18/409qgloh9brwc9eg1ym5.webp
  alt: Blazor logo
---

# Add Swagger

## Add Nuget Package

Swagger is installed on the `/Server` directory. `cd` to that directory first, then run:

```pwsh
dotnet add package Swashbuckle.AspNetCore
```

## Update Program.cs

Open the file called `Program.cs` ad add the following code after line 9:

```csharp
builder.Services.AddSwaggerGen();
```

And the following code after line 32:

```csharp
app.UseSwagger();
app.UseSwaggerUI(c =>
{
    c.SwaggerEndpoint("/swagger/v1/swagger.json", "Blazor API v1");
});
```

# Review Program.cs

The code should look like this:

```csharp
var builder = WebApplication.CreateBuilder(args);

// Add services to the container.
builder.Services.AddSwaggerGen();

builder.Services.AddControllersWithViews();
builder.Services.AddRazorPages();

var app = builder.Build();

// Configure the HTTP request pipeline.
if (app.Environment.IsDevelopment())
{
    app.UseWebAssemblyDebugging();
}
else
{
    app.UseExceptionHandler("/Error");
}

app.UseBlazorFrameworkFiles();
app.UseStaticFiles();

app.UseRouting();
app.UseSwagger();
app.UseSwaggerUI(c =>
{
    c.SwaggerEndpoint("/swagger/v1/swagger.json", "Blazor API V1");
});

app.MapRazorPages();
app.MapControllers();
app.MapFallbackToFile("index.html");

app.Run();
```

## Accessing Swagger

Run the project and the default path `/swagger` will populate with the Swagger UI.