# electron-fcm-demo

**Demonstration of [electron-push-receiver](https://github.com/MatthieuLemoine/electron-push-receiver).**
This demo app shows how to make use of Matthieu Lemoine's excellent electron module for receiveing push notifications from Google's Firebase Cloud Messaging (FCM) service.

```bash
# Clone this repository
git clone https://github.com/CydeSwype/electron-fcm-demo
# Go into the repository
cd electron-fcm-demo
# Install dependencies
npm install
```

You'll need a free Firebase project and you'll want to have Postman installed to simulate the server push.

1. Go to the [Firebase starting page](https://console.firebase.google.com)
2. Select (or create a new) project
3. Go into your Firebase project settings and then into Cloud Messaging
4. Copy your Sender ID and paste it into renderer.js (in place of 123456789)
5. Also copy your Server Key and replace the placeholder value of "SERVER_KEY" in the postman_collection.json

```bash
# Run the app
npm start
```

With the app running, select View -> Toggle Developer Tools.  You should see the client's FCM push token in the Chromium debug console.  Copy this token and paste it into the postman_collection.json (replacing "FCM_CLIENT_PUSH_TOKEN" with it).  You should now be able to send yourself (or any other client registered with your Sender ID) a push message using Postman.

This example shows how you can make use of a "silent push message" by not providing the optional body of the message.  This is an arbitrary design and you could just as easily use a flag in the data portion of the push payload to determine whether the user should see a notification vs. it being silent.  Silent pushes can be useful for informing clients of new information only when changes occur on your server without having all clients query your servers at regular intervals (creating unnecessary load even when there may be no new information for them).

Note: There is a feature in FCM's web console that allows you to send single or batch push notifications ad-hoc.  This feature seems to only be functional for iOS and Android clients.  At the time of this writing, it doesn't appear that the web console allows for sending to desktop/JS clients.


## License

[CC0 1.0 (Public Domain)](LICENSE.md)
