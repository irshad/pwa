## PWA
# How To Create a PWA

# 1.View the Site on your Mobile

In case you have Android device plugged in with your desktop, type in this in your URL – chrome://inspect. This will let you set a port forward with the help of port that you wrote before to the same port on the device/

Press Enter for this to save.

Now you will be able to access the basic version of your website at – http://localhost:8887/ on the connected Android phone.

# 2.Create a manifest.json file

Manifest is a simple JSON file that tells the browser about your web application and how it should behave when 'installed' on the user's mobile device or desktop. Having a manifest is required by Chrome to show the Add to Home Screen prompt.

A typical manifest file includes information about the app name, icons it should use, the start_url it should start at when launched, and more.

```
{
    "name": "K IRSHAD ALI",
    "short_name": "ALI",
    "icons": [
        {
            "src": "img/logo.png",
            "sizes": "92x92",
            "type": "image/png"
        },
        {
            "src": "/img/logo.png",
            "sizes": "144x144",
            "type": "image/png"
        },
        {
            "src": "img/logo.png",
            "sizes": "152x152",
            "type": "image/png"
        }        
    ],
    "start_url": "/",
    "display": "standalone",
    "orientation": "portrait",
    "background_color": "#f0f2f5",
    "theme_color": "#96f2d7"
}
```
And also connect it in your `index.html` in order to work.

`<link rel="manifest" href="manifest.json">`

# 3.Add a Service Worker

Service Worker is the background script which the browser can run while the user is not on the page. It is the element that gives the offline support and gets active when the notification is pushed.

  <b>Create a Service Worker (create a file with name SW.js),</b>

Copy this code in a new file and then save it as `SW.js`.

`/** An empty service worker! */
self.addEventListener('fetch', function(event) {
});`
And that’s it.

# 4.Register the Service Worker

You will have to register the code in your website’s code, for that, open up your `App.js` file and paste this Now, 

`navigator.serviceWorker && 
navigator.serviceWorker.register('SW.js').then(function (registration)
 {
 });`
 
the code will get executed on every single page load. Check if its working properly by reloading the page and then checking – chrome://serviceworker-internals/

Now your website will be able to prompt users to install it on their home screens and secondly, you will be able to make your site able to support push notifications and even work offline.

# 5.Make the Site Work Offline

First step would be to open sw.js script and get hold of caches object. Once you have that, update the code and app the entire website to cache.

Try out how it’s working now. Uninstall the present app and load it on Chrome. Next, refresh the page and select ‘Add to Home Screen’ in the right corner menu.

For abiding by the rule that when Service Worker changes, the page should reload and reinstall it, all you will have to do is add a component which has the ‘version’ of the service worker. When that changes, the install movement happens again, caching the resources that would have changed.

Congratulations, you now know how to turn the website into Progressive Web App and if you followed the steps side-by-side, you have now even migrated your website into a Progressive Web App!

*Disclaimer*: While these steps will give you, the developer, an exact idea of how you will have to fill in the blanks and move from Point A in the process to Point C, if you are reading this as an enthusiastic entrepreneur who wishes to take charge of the migration, I would say, don’t do it without a person who excels in knowing how to turn website into progressive Web App.

While these steps are explanatory, there are a number of elements that come up as part of the process when you sit with the actual development process. So, instead of trying your hands with the steps and finding a different result because you weren’t sure of the between the line elements, give the job to the Progressive Web Apps experts who specialize in the domain.


# Hope you like this post

## irshad ali
