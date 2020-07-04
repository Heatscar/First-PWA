# First-PWA
First Progressive Web App with .Net Core

Installation
------------
**1.- Install "WebEssentials.AspNetCore.PWA" in NuGet.**

**2.- Add the next code in Startup.cs configureServices class**
-   `services.AddProgressiveWebApp();`
-   `services.AddSingleton(typeof(IHttpContextAccessor), typeof(HttpContextAccessor));`

And add using

`using Microsoft.AspNetCore.Http;`

**3.- In appsettings.json file add next code:**

`"pwa": {
    "cacheId": "Worker 1.1",
    "strategy": "cacheFirstSafe",
    "routesToPreCache": "/Home/Contact, /Home/About",
    "offlineRoute": "fallBack.html",
    "registerServiceWorker": true,
    "registerWebmanifest": true
  }`

**4.- Create manifest.json in wwwroot, for example:**

`{
  "name": "Progressive Web App",
  "short_name": "PWA",
  "description": "Creating PWA in ASP.NET Core.",
  "icons": [
    {
      "src": "/icons/pwa-192x192.png",
      "sizes": "192x192"
    },
    {
      "src": "/icons/pwa-512x512.png",
      "sizes": "512x512"
    }
  ],
  "display": "standalone",
  "start_url": "/"
}`

**5.- Create "service-worker" js file (example in wwwroot folder).**

**6.- Add next code on Layout.cshtml file:**

`<link rel="manifest" href="~/manifest.json">`

And

>
    if ('serviceWorker' in navigator) {

        console.log("Will the service worker register?");

        navigator.serviceWorker.register('service-worker.js')
            .then(function (reg) {

                console.log("Yes, it did.");


            }).catch(function (err) {

                console.log("No it didn't. This happened:", err)

            });
    }

Finally add the icon resources.

**Congrats! Your ASP.NET Core application is now PWA.**
