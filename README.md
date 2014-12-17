# Android SDK 0.8.1 BETA

This is an early beta release. If you would like an invite to the private beta please contact us at android-sdk@intercom.io.

## Supported versions
Supports Android 2.3 (API 9) for data only calls and 4.0.3 (API 15) and above for the messaging functionality



## Basic set up

### aar
- Add the intercomsdk-0.8.1.aar to the libs directory of your project
- In the apps build.gradle add the following:

```Java
repositories {
    flatDir {
        dirs 'libs'
    }
}
dependencies {
    compile(name:'intercomsdk-0.8.1', ext:'aar')
}
```

### remote dependancy

- For 0.8.1 we have a remote dependancy on volley. Please add the following as a dependancy in your build.gradle also.

```
compile 'com.mcxiaoke.volley:library:1.0.+'
```

## Initialize Intercom and Begin Session
- Get the Intercom App Id and the SDK API key from `https://app.intercom.io/apps/<your_app_id>/sdk_apps`
- Initialize Intercom by calling `setApiKey(<your_api_key> ,<your_app_id> , <current_context>);` 
- Start a session by calling `beginSessionWithEmail(<your_email_here>, <current_context>, null);`, `beginSessionWithUserId(<your_userid_here>, <current_context>, null);` or `beginSessionForAnonymousUser(<current_context>, null);`
- Optionally you may also begin a session with an eventlister to inform you if and when a session is ready. The eventlistener may be used to kick off any user updates or event tracking that you require to do immediately after a session has started.
```Java
        intercom.beginSessionWithEmail(<your_email_here>, <current_context>, new Intercom.IntercomEventListener() {
            @Override
            public void onComplete(String error) {
                // lets check if we get an error string
                if(error != null) {
                    // handle error here
                } else {
                    // do success logic here
                    // You can also do an user updates / event tracking from here as you are sure that the session has started at this point
                }
            }
        });
```

After calling beginSession you will see an initial 401 response as it will not have valid tokens at that point. This is expected behaviour. 

- End a session when your user successfully logs out of your application by adding
    `intercom.endSession()`

## Developer's Advanced Guide

If you want to learn about the following topics:

- Session control
- Updating a user
- Working with attributes
- Company Data
- Custom Attributes
- Events
- Messaging
- Using Push notifications
- How to configure Secure Mode in the SDK

You may find our guide here

http://docs.intercom.io/Install-on-your-mobile-product/installing-the-android-sdk-developers-guide-part-1
 
 http://docs.intercom.io/Install-on-your-mobile-product/configuring-the-android-sdk-developers-guide-part-2
 
 http://docs.intercom.io/Install-on-your-mobile-product/secure-mode-developers-guide-part-3

http://docs.intercom.io/Install-on-your-mobile-product/using-google-cloud-messaging-gcm-developers-guide-part-4

## License
Copyright 2014 Intercom, Inc.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License.
You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
