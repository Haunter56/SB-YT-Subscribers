# SB-YT-Subscribers
Instructions and code to be able to get notifications for YouTube subscribers through [Streamer.Bot](https://streamer.bot/) and be able to add them to a custom group for command permissions.

This is a workaround using YouTube's API with OAuth 2.0 credentials. You will be creating a Google Cloud account and each time it runs the action, you will be using some of your daily quota allowance.

For more information about YouTube API quota [click here](https://developers.google.com/youtube/v3/guides/quota_and_compliance_audits)

## 3 Important Things
- This will NOT work if you have Streamer.Bot in a folder on your desktop or on a drive without full permission access. If needed please move your Streamer.Bot folder to a location that has full permission access. If you have set up dll files from Streamer.Bot to auto-compile in your Settings > C# Compiler, then you will need to delete and re-add them after moving the folder
- If a viewer has their subscriptions set to "private" then there is no way of knowing that they subscribed through this method.
- Please pay attention when selecting which YouTube account to link. You will need to make sure you choose the channel/brand account you want to get subscribers for.

# Instructions
## Get OAuth 2.0 set up and download your token
- Log into the [Google Developers Console](https://console.developers.google.com/) with your email you use for YouTube.
- Choose your country and agree to terms of service
- Under `Enabled APIs & Services` select `Create Project`
- Choose a project name (I called mine “MyApp”) and click `Creeate`

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/0f39b56c-3972-4672-990e-c34f0553af9b)
- Click `+ Enable APIs and Services` and scroll down to YouTube

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/e491205d-5178-44be-930c-fffa8314e879)
- Click on `YouTube Data API v3` then click `ENABLE`

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/85eb0b42-cf90-4534-99b7-0a5a226fd6e2)
- Click on `Credentials` and the ` + Create Credentials`

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/ccc0a070-99b1-46c0-8091-3056fc214bae)
- Then choose `OAuth Client ID`

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/99b45247-680b-4632-add3-c6bb3dd6fb33)
- Select `Configure Consent Screen` then select `External` and then `Create`

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/d4f0f613-b599-4938-8169-6e6e922ac067)
- App name is "MyApp" and then add your email address, then add your email address for the Developer contact information, the click `Save and Continue`
- For scopes select `Save and Continue`, for Test Users select `Save and Continue`
- Then go back to dashboard and Publish your app
- Then go back to the credentials screen and create credentials
- Select Desktop app, then name it something, then select `CREATE`

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/534dcde2-55f9-413e-92cf-6a5731b6242c)
- Then in the next screen download the JSON Token

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/f11a8244-7552-4cf7-acc4-4da3136bc37c)
- Move it from your downloads to a folder called “subscribers” ALL LOWERCASE inside your Streamer.Bot folder

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/4f90a301-e854-4c03-955f-1c19196527ff)
- Make sure you go to `View > Show > Show File Name Extensions`, then edit the file so that it is just called `client_secret.json`

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/08cf02a3-4e27-496a-82da-b9f19c2530d0)
- In that same folder, create a text file called `channel_ids_record.txt` and leave the file blank

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/65a45515-368a-497e-9f64-a6e57b6e39e4)

## Streamer.Bot Initial Code Setup
- In Streamer.Bot go to `Settings` > `C# compiler` then right-click to add these references from your Streamer.Bot folder location

`Google.Apis.Auth.dll`

`Google.Apis.Core.dll`

`Google.Apis.dll`

`Google.Apis.YouTube.v3.dll`
  

- Add these references from the default .Net Location

`mscorlib.dll`

`System.dll`

`System.Core.dll`

`System.Runtime.dll`

![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/cc6111ad-ded1-413a-a3b8-0f4d587c2f64)


- Import the [Streamer.Bot code](https://github.com/Haunter56/SB-YT-Subscribers/blob/main/YT_subscriber_list.sb) with one action
- Go into the Execute Code sub-action (double-click it) and click `Compile`

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/fb6cf54f-2136-4d8f-b1d2-e225949cd58d)
- Make sure it compiled successfully then click `Save and Close`.
- Go to Hot Keys and create a hot-key with the new imported action

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/60a19687-95dc-4e84-906f-1bc9de4c530e)
- Now activate the hot key to run the subscriber list action. It will have an authorization page in your default browser pop up.
- **Make sure to select your YouTube channel account/Brand account here** The account you select here is the account it will use to get your subscribers

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/0a4a73c6-0a85-4b77-b46d-b7ed6214f9df)
- It will say that Google hasn’t verified your app yet. It’s ok because it’s the one you made. Make sure it’s your email you put in.

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/bdde5d0e-e5f5-498e-b2d8-d98f29f37d48)
- Click `go to my app`, then click `Continue`

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/eb482375-a598-48c4-ab8e-4c34d540ac3b)
- You should get confirmation that the verification code was received and you will be good to go.

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/4a30b4bb-1719-4268-8cf1-45052607cabb)
- You should now be able to check the channel_ids_record.txt file and see all the channel IDs of people who have subscribed to you and have their subscriptions set to “public”.
- You should also be able to see a bunch of names have populated in the “Users” field under Settings > Groups >SubscribersYT
- If not, then you will need to check your log file to see why it didn't run or connect.

## Streamer.Bot Action Setup
- go into the C# code again and delete the `//` on line 60

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/6dc98b64-23d3-4996-9d2b-0c205d003418)
- Then create an action for the alert when someone new subscribes to your channel *Make sure to put it in a blocking queue*. You can have it be something very simple like just sending a message to chat or playing a sound to start.
- Next, copy the action ID from the action you just created

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/599e19c2-b1e8-429a-b490-15909daae3e6)
- In the “Get Subscriber List” action, double-click on the sub-action called “Set argument %subscriberActionId% to…” and paste the action ID you copied into the `Value` field

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/a457b2d4-ef2a-41d9-b5f8-a62138e57eff)
- In order for this to monitor your subscriber list, you will need to create a timed action in `Settings` > `Timed Actions` then Right-click and > `Add`

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/90a5f995-6648-4e88-8d87-66d05a1a48f1)
- Then it will check your subscribers every 15 seconds

## Streamer.Bot Timers Setup
Each time the action runs it uses part of your YouTube quota, as long as you aren’t streaming for too long or have the interval to low, or leave Streamer.Bot open and the action running all day while not streaming, you should be fine.

Something I like to do is set a timed action that is enabled when my broadcast starts. This way the alerts go off for anyone who subscribed while I was not live streaming.

- Create a new action that just enables the Subscriber List Timed action (I called mine “Enable Subscriber API Action”)
- Then Create a new timed action in `Settings` > `Timed Actions`
- Assign the "Enable Subscriber API Action" to that timer (see screenshot)

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/3e92b975-fd27-466f-8fb3-ad9cd91b549c)
- Go back to your action > `New sub-action` > `Core` > `Timers` > `Set Timer State`

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/fed5b100-8dad-48b3-ab4e-24365c83b531)
- Now add one to disable the delay timer

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/a1e42b65-54e5-42e6-b9ff-6a5194334898)
- Add one to enable the Subscriber List Timer

![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/da1338d6-bc96-4955-91c3-d6332153fe23)

- If you don’t have one already, create an action called `Broadcast Started Action`
- Create a sub-action to enable the `Subscriber List Delay` timer

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/450a4ef2-1cab-4bbb-a71c-51906ad6195a)
- Then assign the broadcast started action to your `Broadcast Started` Event - `Platforms` > `YouTube` > `Broadcast Events` > `Broadcast Started`

- If you don’t have one already, create an action called `Broadcast Ended Action`
- Create a sub-action to disable the `Subscriber List Timer` timer
![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/228e273b-299d-4677-babc-4101f964bbaa)


- Then go into your timed actions and disable the two subscriber list timers you just created. When you go live, it will enable the delay timer and then it won’t check for new subscribers until that delay is over. You can set it to whatever amount of time you want, but I set mine for 180 seconds (3 minutes) in the screenshot. You will want to add more time if you have a stream starting soon screen or something. When you end your stream, the `Broadcast Ended Action` will stop the timer so that it doesn't keep using your quota.

 ![image](https://github.com/Haunter56/SB-YT-Subscribers/assets/107263697/d74fd8fe-17bd-4d4e-b674-8e3af334f951)
- Now, every time someone new subscribes, it will run the Subscriber Alert action you just created, so you can put whatever you want in that alert action
- Use `%subscriberName%` as the variable for the name of the user who subscribed for any text sources or in chat messages or whatever you like
- Don't forget to disable any other subscriber actions or commands that you already have









































