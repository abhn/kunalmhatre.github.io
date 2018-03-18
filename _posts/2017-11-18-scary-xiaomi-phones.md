---
title: "Scary Xiaomi phone(s)"
layout: post
date: 2017-11-18 22:44
headerImage: false
tag:
- PRIVACY
- TRACKING
category: blog
author: kunalmhatre
description: Data collected by Mi phones in the background.
---

Xiaomi or Mi smartphones are booming a lot nowadays. It's good to see that their phones are cheap and affordable, but if you are more privacy concerned, you may need to give it a second thought before buying it. 

I used two cool packages called, [mitmproxy](https://mitmproxy.org/) and [arpspoof](https://su2.info/doc/arpspoof.php) to intercept traffic on a Mi phone (Redmi 4A) running **MIUI Global 8.5** and observed some activities happening in the background which could harm users' privacy.

***Note**: The values of the parameters shown in the data sent by an API is faked and I have not marked "mac" parameter as red because of the confusion that whether it stands for Message Authentication Code or Wi-Fi's MAC address. Most probably it's the Wi-Fi's MAC address, if it is, then assume that I marked it red as well.*

## Promoted apps

**API**: https://global.market.xiaomi.com

In Redmi 4A, MIUI provides us with a default folder named "More apps" where you can store more... apps. You can create many such folders in your app drawer, but they have implemented a new function into this called Promoted apps. If you make a new folder, it will have a little switch of Promoted apps. If you turn it on, the info (package name) regarding **all the apps** present in that folder is sent back to Xiaomi and based on that they recommend you new apps in that particular folder. The default folder "More apps" is configured to give promoted apps, so either turn it off or recreate the folder with Promoted apps turned off. 

![Promted apps data](/assets/images/2017_11_18/promoted.png)

## Contact cards

**API**: https://us.micardapi.micloud.xiaomi.net

I observed that whenever I open any "contact" in Contacts app to see more details; a request is made to that API. Unsurprisingly, an encoded phone number is attached to it. I am quite sure, it's the same phone number which we check details of. The Strange part is, they have implemented a contact syncing option for the Mi Cloud, which is good, but this API is called even after you turn off the (entire) sync configuration - which seems quite creepy to me because if that's the same phone number which is encoded, then they can get my contact numbers even if I don't want to sync it with their servers.   

![Contacts app data](/assets/images/2017_11_18/contacts.png)

## Advertising

**API**: http://api.ad.intl.xiaomi.com/getSplashScreenAds

I disabled too much of stuff on this phone to protect privacy including the creepy options like **User Experience Program**, **User Experience "Programme"** and **User advertising identifier**. I am not sure why they still call this advertising API whenever I open any Mi app. The worst part is, they are not even using SSL/TLS connection here.

![Advertising data](/assets/images/2017_11_18/ad_data.png)

Take my word, This (Mi) phone calls too much of various Ad related APIs in the background.

<iframe width="560" height="310" src="https://www.youtube.com/embed/WISORijUJrg" frameborder="0" allowfullscreen></iframe> 

## Tracking

**API**: https://tracking.intl.miui.com/track/v1

This API mostly triggered whenever I used to open Music player. It has one such parameter called "sender", which for the most of the time has the following package name: **com.miui.systemAdSolution**. Also when I open Security app provided by Mi, this API comes back into the picture and at that time the sender becomes **com.miui.securitycenter**. It also contains analytics related parameters, like the event timing and such similar things. There is a slight possibility that many such Mi apps may be calling this API in the background.

#### After opening Music Player

![Tracking data - Music Player](/assets/images/2017_11_18/music_player_tracking.png)

#### After opening Security Center

![Tracking data - Security Center](/assets/images/2017_11_18/security_center_tracking.png)

## Messaging

**API**: https://global.api.huangye.miui.com

Again, some encoded data was sent every time I opened someone's message from the Message app. Although the encoded data was not same if any particular message was opened more than once. Not sure, what all data or stats they grab whenever we check a message, but still a thing to be concerned about. 

![Messaging app data](/assets/images/2017_11_18/messaging.png)

## Wrap-up

Bottom line is, there is too much of information going out of your device even if you strengthen your privacy settings provided by MIUI. Now, this may be subjective because a decent fellow may put this into one single line, *"They need data so that they can provide you with good user experience or certain bells and whistle in their apps."*, I would say, give me a single switch in settings to turn it off and then no more data should be sent outside apart from what is required, which I guess, is not available.

## Solution

Luckily there is one good solution for all of this and we should thank Xiaomi for it. That is, you can **unlock your bootloader and flash a more (privacy) secured custom ROM**.

That's it. Have a great day.

## Further reading

- [Xiaomi Can Silently Install Any App On Your Android Phone Using A Backdoor](https://thehackernews.com/2016/09/xiaomi-android-backdoor.html)
- [Is Xiaomi really spying on the your privacy?](http://www.deccanchronicle.com/141023/technology-mobiles-and-tabs/article/xiaomi-really-spying-indian-user%E2%80%99s-privacy)
- [Security firm discovers several major security flaws in Xiaomi’s MIUI](https://www.androidauthority.com/xiaomi-miui-security-flaws-793107/)
