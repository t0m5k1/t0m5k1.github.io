---
layout: post
title: Browser Privacy Part 1
date:   2017-02-21 11:07
description: Some advice on how to retain privacy when browsing online with chromium
comments: true
tags:
 - PC
 - Linux
 - Windows
 - Security
 - Privacy
---


For a while now I have been mentioning on social networks and to friends how and why I use something called a “Browser Profile” the main reason why is due to tracker cookies but also it helps me in maintaining and controlling my online presence.
We all know that many people like to block adverts on websites but many do not worry about cookies, I for one do not like the fact that websites can plant a single cookie on you computer which can then record the websites you visit, Facebook is one prolific website which loves to follow you all over the web and then use this gathered browsing info to create directed advertising when you use Facebook but it does not stop there.
Facebook can and do crawl/mine your actual browsing history, by creating an account with them then agreeing to their terms & conditions you are allowing them to do this!

So I use a separate browser profile specificity for Twitter and Facebook this way I ensure that the data about me that is can crawl/mine will only ever be from Facebook.com as will the browser history. Now when you first look into Browser Profiles & begin to use them you will need to change your browsing habits, for example if friend A shares a link to a website when I view it in my Facebook feed I don’t just click to view it I now right click & copy it to the clip board & then go to my “Normal” web browser instance & paste the URL in my address bar & visit the page. This way Facebook now has no idea I have visited the site & cannot in anyway use that website to create a targeted advert.

I know many will say “Why not just block cookies & use ghostery?” well I do use ghostery but Twitter & Facebook demand you have cookies enabled & as well as that if you use ghostery & have cookies deleted when your browser is closed you will still see targeted advertising in Facebook meaning their forced cookie is managing to store some data of where you have been & then using their apis & access methods when you see an amazon advert it will show what you last browsed within amazon. Yes I could just block the advert but what I am trying to achieve is a setup that blocks everything from these companies & also stops them looking at data I do not want them to see which is why Facebook decided to start to log the history from the browser itself so even when you block all the above Facebook can see your tracks still. So this method locks everything but impacts the experience & convenience we have grown accustomed to have.

One thing many say all the time is “Why would I want to do that! I love being able to easily access site shared by my friends…” I used to hear that all the time & mainly ended up with people stating it was pointless, waste of time, cumbersome etc but I am getting more & more people ask me how to stop/block tracking & keep privacy. So here goes one of a series of articles I’ll be posting here to help you block, separate even replace the web based services to enable you to keep using them but also retain some privacy.

Browser Profile / User Data Directory
The user data directory contains data specific to a given user. Some examples of this type of data are: history, bookmarks, and cookies.
(Note that in Windows, the profile name is included in the directory hierarchy.)

Default Locations

Windows XP:
Google Chrome:
C:\Documents and Settings\%USERNAME%\Local Settings\Application Data\Google\Chrome\User Data\Default
Chromium:

C:\Documents and Settings\%USERNAME%\Local Settings\Application Data\Chromium\User Data\Default
Windows 10 / 8 / 7 / Vista:
Google Chrome:
C:\Users\%USERNAME%\AppData\Local\Google\Chrome\User Data\Default
Chromium:

C:\Users\%USERNAME%\AppData\Local\Chromium\User Data\Default
Mac OS X:
Google Chrome:
~/Library/Application Support/Google/Chrome/Default
Chromium:

~/Library/Application Support/Chromium/Default
Linux:
Google Chrome:
~/.config/google-chrome/Default
Chromium:

 ~/.config/chromium/Default
Chrome OS:
/home/chronos/
Running from a Custom Location
OK so this is the reason for this post run Google-Chrome or Chromium with a custom user data directory in order to run multiple instances at the same time.

Windows:
to do this, add the –user-data-dir flag to chrome.exe, like this:

chrome.exe --user-data-dir=c:\foo
Here are the full steps on how to make a new profile & get a shortcut for it:

Step 1: Open Windows Explorer and switch to Chromes User Data folder available at:

For Windows 7 and Windows Vista 
C:\Users\<username>\AppData\Local\Google\Chrome\User Data 

For Windows XP 
C:\Documents and Settings\<username>\Local Settings\Application Data\Google\Chrome\User Data
chromeprofile

Step 2: While inside Windows Explorer, select the subfolder called default and make a copy of that folder inside the same User Data folder of Chrome. Rename that new folder copy to, say, Your_Name as shown in the screenshot.

Step 3: We will now reset this new Your_Name profile in Chrome to the factory defaults. Open Command Prompt, use the cd command to switch to the Chrome Application folder (where Chrome is installed) and run the following command:

chrome.exe --user-data-dir="..\User Data\Your_Name" -first-run
Step 4: Your new user profile in Chrome is ready for use. To run Google Chrome using this profile instead of the default profile, lets create a shortcut. Right click anywhere on the desktop, choose New -> Shortcut and type the following in the location box:

For Windows 7 and Vista: 
C:\Users\<user>\AppData\Local\Google\Chrome\Application\chrome.exe --user-data-dir="..\User Data\Your_Name"

For Windows XP: 
C:\Documents and Settings\<user>\Local Settings\Application Data\Google\Chrome\Application\chrome.exe --user-data-dir="..\User Data\Your_Name"
chromeicons

Give this shortcut a name, change the shortcut icon to anything you want or just keep it as Chrome and youre done.

Mac OS X:
To achieve the same thing in Mac OS X take a little bit more work but still here are the steps:
Step 1:  Open AppleScript Script Editor (either in Applications/Utilities or Applications/AppleScript)
Enter this:
Chromium:

1
do shell script /Applications/Chromium.app/Contents/MacOS/Chromium user-data-dir=/Users/$USER/Library/Application\\ Support/Chromium/Facebook > /dev/null >> & &
Google Chrome:

1
do shell script /Applications/Google\\ Chrome.app/Contents/MacOS/Google\\ Chrome user-data-dir=/Users/$USER/Library/Application\\ Support/Google/Chrome/Facebook > /dev/null >> & &"
(If you did not install Chromium in the default location, modify the script as appropriate.)
Step 2: Save the script in your Applications directory with the file format Application and a memorable name like Facebook-webapp.
Now close the Script Editor and find your newly created application and run it. Running this application will open another Chromium instance pointing to your new profile.
If you want this application to have the same icon as Chromium, then select the Chromium application and type command+i to open the info dialog. Select the icon at the top left of the info dialog and you will see a blue highlight around the icon. Copy the icon using command+c. Now open the info dialog for the new script application using command+i. Select the icon at the top left and paste the copied icon using command+v.

Linux:
To do this, add the –user-data-dir flag to chrome, like this:

 chrome --user-data-dir=/path/to/foo
As explained here, the default directory is located at:

1
2
Google Chrome: ~/.config/google-chrome/Default
Chromium: ~/.config/chromium/Default
Step 1: Open a terminal and create a new directory for your second profile. For instance:

1
mkdir ~/.config/google-chrome/work
Step 2: Open Google Chrome with the switch:

1
google-chrome --user-data='~/.config/google-chrome/work'
If this is a profile youll be using often, you can also create a menu entry under Applications – Internet (Chrome|Work, maybe?) if you can’t edit the menu directly you can find all the .desktop files here:

1
2
/usr/share/applications
~/.local/share/applications
all you would do then is find the google-chrome.desktop file & copy it then edit it then save as a different filename & if you did it correctly just refresh your menu & there will be your new application short cut

iPad:
Unfortunately if most of your web usage occurs on an iPad then you will face issues in setting up multiple profiles mainly because there is no facility to copy/edit application shortcuts. This is due to the fact that iPads just run iOS.

Android:
Much the same as iOS unfortunately again you will not be able to run google chrome with multiple profiles because again you have no way to edit/copy shortcuts, I have tried with a rooted android phone & a terminal emulator but the issue is compounded slightly because every android app runs in a google version of a kernel container which means when you use a terminal to edit any part of the app that part is then ignored as you changed the permissions for it!

Web Application

For a while now I have been running popular websites within their own window with no menu, bookmark or navigation bars. This way the website fills the entire window but is not full screen
To Start you need to open your favourite site in a tab
Then in another tab open the apps window chrome://apps/
Now go back to the previous tab & in the navigation bar (or Omni-box as google call it!) you see the little icon next to the URL, if you click, hold & drag that icon to the apps tab then drop it between any 2 icon already present on the app window.
You should now see either a capital letter or the icon for the website, right click on that nice big icon you just made & select “Open as window”, there is another option called “Create shortcuts” this will put an icon for this “App” on your desktop & start menu in windows.

Here is a short vid clip that shows you what to do if you find watching  easier than reading about it.
