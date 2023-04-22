---
title: Topmenu in Blazor Client
author: danijeljw-rpc
date: 2023-04-23 00:00:00 +1000
categories: [C#, Blazor]
tags: [swagger, C#, blazor, wasm, layout]
math: true
mermaid: true 
image:
  path: /assets/image/2023/04/23/324830.png
  alt: Blazor logo
---

Dedicated `TopMenu` component can be added to the Blazor Client project by creating 2 files in the `Shared` folder:

1. TopMenu.razor
2. TopMenu.razor.css

The image file being used is in the `wwwroot` folder structure, as indicated by the `img src` path with a pixel size of 34.

### TopMenu.razor
```csharp
<div class="top-menu">
    <img src="img/icons/324830-34px.png" />
    @Bananas
</div>

@code {
    public int Bananas { get; set; } = 100;
}
```

### TopMenu.razor.css
```css
.top-menu {
    display: flex;
    justify-content: center;
    width: 100%
}
```

### Enable Mobile Visibility
Open the `MainLayout.razor` and reference the `TopMenu` component:
```csharp
<div class="top-row px-4">
    <TopMenu />
</div>
```

Edit the `MainLayout.razor.css` and comment out the visibility false:
```css
@media (max-width: 640.98px) {
    .top-row:not(.auth) {
/*        display: none;*/
    }
```