## Convert React App into a Progressive Web App (PWA)

![PWA](https://res.cloudinary.com/phonerefer/image/upload/c_scale,h_50,w_150/v1573154075/irshadali.site/wd0dusiqooqdg81ygqxj.png "PWA")      ![ReactJs](https://res.cloudinary.com/prvnbist/image/upload/c_scale,h_80/v1564054850/React.js_logo-512_bvpygm.png "ReactJs")

# What is a PWA?
Progressive Web Apps are user experiences that have the reach of the web, and are:

*<b>Reliable</b> - Load instantly and never show the downasaur, even in uncertain network conditions.*

*<b>Fast</b> - Respond quickly to user interactions with silky smooth animations and no janky scrolling.*

*<b>Engaging</b> - Feel like a natural app on the device, with an immersive user experience.*

This new level of quality allows Progressive Web Apps to earn a place on the user's home screen.

# 1. Register a Service Worker
<b>What is a service worker?</b>
Service workers (client-side proxies that pre-cache key resources) enable PWAs to load instantly and provide an instant,
reliable experience for users, regardless of the network state.

Create a new <b>worker.js</b>  file in the public folder <b>(public/worker.js)</b> and add the following code:
```
Let CACHE_NAME = 'your-app-name';
Let urlsToCache = [
  '/',
  '/completed'
];

// Install a service worker
self.addEventListener('install', event => {
  // Perform install steps
  event.waitUntil(
    caches.open(CACHE_NAME)
      .then(function(cache) {
        console.log('Opened cache');
        return cache.addAll(urlsToCache);
      })
  );
});

// Cache and return requests
self.addEventListener('fetch', event => {
  event.respondWith(
    caches.match(event.request)
      .then(function(response) {
        // Cache hit - return response
        if (response) {
          return response;
        }
        return fetch(event.request);
      }
    )
  );
});

// Update a service worker
self.addEventListener('activate', event => {
  Let cacheWhitelist = ['your-app-name'];
  event.waitUntil(
    caches.keys().then(cacheNames => {
      return Promise.all(
        cacheNames.map(cacheName => {
          if (cacheWhitelist.indexOf(cacheName) === -1) {
            return caches.delete(cacheName);
          }
        })
      );
    })
  );
});
```
## Note! from above code replace (your-app-name) with your app name
# 2. Now Update HTML
Update your <b>index.html</b> file in the public folder <b>(public/index.html)</b> 
to check if the client’s browser supports service workers. Just Add below code inside the body tag of your app's <b>(public/index.html)</b>
```
<script>
      if ('serviceWorker' in navigator) {
        window.addEventListener('load', function() {
          navigator.serviceWorker.register('worker.js').then(function(registration) {
            console.log('Worker registration successful', registration.scope);
          }, function(err) {
            console.log('Worker registration failed', err);
          }).catch(function(err) {
            console.log(err);
          });
        });
      } else {
        console.log('Service Worker is not supported by browser.');
      }
    </script>
```
# 3. Activating ServiceWorker
## Now go to your app's (index.js) in the src folder (src/index.js)
Now Update <b>serviceWorker.unregister() to serviceWorker.register()<b/>  Like Below Code At Last Line.
  
```
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import * as serviceWorker from './serviceWorker';

ReactDOM.render(<App />, document.getElementById('root'));

// If you want your app to work offline and load faster, you can change
// unregister() to register() below. Note this comes with some pitfalls.
// Learn more about service workers: http://bit.ly/CRA-PWA
serviceWorker.register();
```

Restart (npm start) and reload your React app — you should see the message “Worker registration successful” in the console.

# 4. Create a manifest.json file

Manifest is a simple JSON file that tells the browser about your web application and how it should behave when 'installed' on the user's mobile device or desktop. Having a manifest is required by Chrome to show the Add to Home Screen prompt.

A typical manifest file includes information about the app name, icons it should use, the start_url it should start at when launched, and more.

```
{
    "name": "your-app-name",
    "short_name": "your-app-name",
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

# That's it 🎉 Congratulations, you just created a working progressive web app!

## This Is "irshad ali" 
Check me out: https://www.irshadali.site



