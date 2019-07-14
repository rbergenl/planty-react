## 100 Lighthouse score
- Before running the webserver and navigating to `http://localhost`
- Run `$ npm run build` to be able to host the production optimized files.
- `$ npm install local-web-server`.
- Add to package.json the script `"serve": "ws --directory ./build --port 443 --compress --http2"`.

### SEO to 100
- The minimum setup is already provided by create-react-app.
- Add to `public/index.html` the line `<meta name="description" content="Description" />`.

### Accessibility to 100
- Make sure in `public/index.html` the root div has a role like `<div id="root" role="main"></div>`

### Performance to 100

#### Trust the Certificate
- https://github.com/lwsjs/local-web-server/wiki/How-to-get-the-%22green-padlock%22-using-the-built-in-certificate
- Open KeychainOS > Certificates > 'File' > 'Import Items...'.
- Import the certificate located at `./node_modules/lws/ssl/lws-cert.pem`
- In the list of certificates is now a new one with the name `lws`.
- Open it and at the section 'Trust' set it to 'Always Trust'.
- Open the website specifying the protocol `https://localhost/`.

#### Redirect HTTP to HTTPS
- https://github.com/lwsjs/local-web-server/wiki/How-to-redirect-HTTP-traffic-to-HTTPS
- `$ npm install lws-redirect`.
- Add to package.json the script `"serve-http": "ws --port 80 --stack redirect --redirect 'http -> https'"`.

### PWA to 100

#### Enable the Service Worker
- https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app
- In `serc/index.js` change `serviceWorker.unregister();` into `serviceWorker.register();`

#### Add Logos to the Manifest
- https://developers.google.com/web/fundamentals/web-app-manifest/
- Convert the `src/logo.svg` into a PNG using an online converter.
- Then make copies and resize the PNG into `512x512` and `192x192`.
- Place both PNGs in the folder `public`.
- Add to the `public/manifest.json` to the `icons` section:
```
{
    "src": "/icon-192.png",
    "type": "image/png",
    "sizes": "192x192"
},
{
    "src": "/icon-512.png",
    "type": "image/png",
    "sizes": "512x512"
}
```