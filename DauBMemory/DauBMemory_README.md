<!-- ![Alt Text](https://media.giphy.com/media/vFKqnCdLPNOKc/giphy.gif)

<img src="https://media.giphy.com/media/vFKqnCdLPNOKc/giphy.gif" width="40" height="40" />

<img src="/giphy.gif"/> -->
># [Dau B Memory] App in IOS
>>##### AppStore link: https://apps.apple.com/hk/app/dau-b-memory/id6476182093
>>>Developed by [Max DU](https://github.com/maxdu96)
>>>>*The app can make the couple record there are daily life together. All can access create or edit one diary. Or maybe say, people often forget what they do on a day. So when they wanna remember that day, they can open the app to check, can let them happy or xxx one more time. And the couple for two both have responsibility to do this things*


#### Background: 
Two years ago (in 2022), I couldn’t find a diary record app on mobile that could be added or edited together. Even though Google or Microsoft documents can be shared, they are not real diaries. Secondly, I used the method of sharing a folder in iCloud and typing in notes. However, I found that if there were too many characters on the page, it would lag. So, I got an idea, why can’t I develop one for myself?

<img src = "/DauBMemory/Image/git_first.jpg" />
<img src = "/DauBMemory/Image/git_version1.0.jpg" />
And here is my app(Project Created on Sep 2023). I released the app in Dec 2023 as version 1.0 (TestFlight only). 

#### Languages and technology:
+ Swift
+ Node.JS
+ Google Firsbase 
    - Authentication 
    - Firestore Database
    - Functions
    - Messaging
+ Google 
    - Admob
+ GitHub Source Control
+ Figma UI Design

#### App Store Status
<u>23/5/2025 - Support dark mode, add quick action when tap on app icon [v3.2.0] 🔥🔥</u> 

...
<!-- 
<u>19/3/2025 - Add emoji selection panel [v2.4.0]</u> 

...

<u>25/2/2025 - Add in app purchase can let you buy your own data and can handle in offline. [v2.2.1]</u> 

...

<u>28/1/2025 - Fix the not correct version number and add anniversary reminder notification. [v2.0.0] </u> 

... -->

<u>19/9/2024 - Successful launch on AppStore. [v1.0] </u> 

___

#### UI Version (Sample)
The following display may does not represent the current app effect, as different versions have different display effects.

###### 🎈1.0
<img src="/DauBMemory/Image/UI_v1.png" />

###### 🎈2.0
<img src="/DauBMemory/Image/UI_v2.png" />

___


#### Features
- [x] Version handling.
    - [x] Check iTunes API to known if there have a new version.
    - [x] Catch the version number determine if an update is necessary based on a version number. 
- [x] Onboarding View.
- [x] Authentication checks when opening the app.
- [x] Support multiple languages. (English, Cantonese, Chinese).
- [x] Privacy view, privacy protection when a device or app is inactive.
- [x] Sharing diaries and other stuffs will share with your partner.
- [x] Diaries filter by month.
- [x] Range selection for the date pick.
- [x] Custom emoji reaction, look like WhatsApp app.
- [x] Remote notication for new diary / comment.
    - [x]  NotificationServiceExtension can use custom icon.
    - [x]  Deeplink to that page when in active / backgurand / inactive.
- [x] Local notication for reminder alarms.
    - [x]  Deeplink to that page when in active / backgurand / inactive.
- [x] Anniversary celebrations poup, mean when 7 days / 1 month / n years.
- [x] Widget, show the reminder data in widget.
- [x] In-App Purchases (IAP), can buy your data handle offline.
- [x] Skeleton loading view.
- [x] Photo gallery, look like native-style.
- [x] Reminder list usage like native-style.
    - [ ] Support Siri add data.
- [X] Support long press functionality on app icon.
- [x] Support dark mode.
- [ ] Real full text search.



___


#### Video Demo Show:
The following display may does not represent the current app effect, as different versions have different display effects.

<i>Click below video:<i>

[![Dau B Memory](/DauBMemory/Image/play_video.png)](https://youtu.be/uHn1DlWv_UI "GO YOUTUBE")


<!-- | Function  | Description |
| ------ | :-----------: |
| `Welcome page & App basic` | <img src="/DauBMemory/Image/GIF/welcome.gif" width="30%" height="30%" /> <img src="/DauBMemory/Image/GIF/main_3tab.gif" width="30%" height="30%" />|
| `Diary create flow` | <img src="/DauBMemory/Image/GIF/diary_typing.gif" width="30%" height="30%" />  <img src="/DauBMemory/Image/GIF/day_range_selector.gif" width="30%" height="30%" /> <img src="/DauBMemory/Image/GIF/diary_create.gif" width="30%" height="30%" />|
| `Diary list show` | <img src="/DauBMemory/Image/GIF/diary_read.gif" width="30%" height="30%" /> <img src="/DauBMemory/Image/GIF/year_selector.gif" width="30%" height="30%" /> <img src="/DauBMemory/Image/GIF/diary_canEdit.gif" width="30%" height="30%" />|
| `Comment functions` | <img src="/DauBMemory/Image/GIF/coment_typing.gif" width="30%" height="30%" /> <img src="/DauBMemory/Image/GIF/coment_reaction.gif" width="30%" height="30%" />  <img src="/DauBMemory/Image/GIF/comment_count.gif" width="30%" height="30%" /> |
| `Diary status have remote notification` | <img src="/DauBMemory/Image/GIF/notif_create.gif" width="30%" height="30%" /> <img src="/DauBMemory/Image/GIF/notif_edit.gif" width="30%" height="30%"/> <img src="/DauBMemory/Image/GIF/notif_reaction.gif" width="30%" height="30%" />|
| `Profile all can be editable` | <img src="/DauBMemory/Image/GIF/profile_canEdit.gif" width="30%" height="30%" /> |
| `Reminder widget and deepLink` <br> If you ask me why I don't use the native "Reminder" feature of Apple, it's because the native "Reminder" updates a "completed task" on the left side, and it's very easy to accidentally click on it in the widget. ^ ^  | <img src="/DauBMemory/Image/GIF/reminder_typing.gif" width="30%" height="30%" /> <img src="/DauBMemory/Image/GIF/reminder_widget.gif" width="30%" height="30%" /> <img src="/DauBMemory/Image/GIF/reminder_widgetColor.gif" width="30%" height="30%" /> <img src="/DauBMemory/Image/GIF/reminder_widgetUpdate.gif" width="30%" height="30%" /> <img src="/DauBMemory/Image/GIF/reminder_widgetDeeplink.gif" width="30%" height="30%" />|
| `photo mark function` | <img src="/DauBMemory/Image/GIF/photo_mark.gif" width="30%" height="30%" /> |
| `privacy view protect when app not in foreground` | <img src="/DauBMemory/Image/privacy_view.png" width="30%" height="30%" /> |
| `skeleton loader` | <img src="/DauBMemory/Image/GIF/list_reload.gif" width="30%" height="30%" /> |
| `effect for backgroud photo` | <img src="/DauBMemory/Image/GIF/profile_effect.gif" width="30%" height="30%" /> |
<!-- | `Photo mark Widget` | Coming soon | -->
<!-- | `Photo mark Widget` | Coming soon | -->
<!-- | `Photo mark Widget` | Coming soon | -->

___


##### REST API and FCM example (Node.Js):

``` js
app.post('/', async (req, res) => {
    const date = req.body.date;
    const content = req.body.content;
    const authorID = req.body.authorID;

    if (date == null || content == null || authorID == null) {
        return res.status(400).send({"message":"Error, have nil value！"});
    }

    var diary = {"date":date, "content":content, "authorID": authorID};
    await admin.firestore().collection('Diaries_Test').add(diary);
    res.status(201).send({"message":"Diary insert successful！"});
});
```

``` js
  const message = {
        token: otherToken,
        notification: {
            title: userName,
            body: text_body,
        },
        data: {
            docId: docId,
            route_diaryContent: diaryContent,
            route_date: route_date,
            route_authorID: authorID,
            route_authorName: authorName
        },
        android: {
            notification: {
                imageUrl: userIcon
            }
        },
        apns: {
            payload: {
                aps: {
                    'mutable-content': 1
                }
            },
            fcm_options: {
                image: userIcon
            }
        },
        webpush: {
            headers: {
                image: userIcon
            }
        },
        //topic: 'all'
    };
    await admin.messaging().send(message)
        .then((response) => {
            console.log('Successfully sent message:', response);
        })
        .catch((error) => {
            console.log('Error sending message:', error);
        });
```

