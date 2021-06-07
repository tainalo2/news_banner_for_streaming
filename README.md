# NEWS BANNER FOR STREAMING
A news banner in HTML CSS and JS to integrate in OBS (or other streaming tool supporting browser source)

![Demo](https://raw.githubusercontent.com/tainalo2/news_banner_for_streaming/main/Animation.gif)


# Summary
  - Prerequesites
  - Technical explanation
  - Installation
    - Nodered file host
    - Nodered import
    - Nodered configuration
  - Using
  - Credit

# Prerequesites
  - A nodered server (free low code GUI for NodeJS server) https://nodered.org/
  - Nodered libraries : node-red-dashboard

# Technical explanation
The objective is to dynamicaly generate a banner in streaming live from a web video control panel, to create show on twitch.
  - The video controller set a text for the banner that is put in a variable
  - When the video controller click on ON button : a websocket message is send.
  - A webpage with animation is set as browser source in you streaming  tool (like OBS) and receive websocket message to update text and show the banner
  - When the video controller click on OFF button : a websocket message is send to the webpage to hide the banner

# Installation
 - Nodered file host
   - create a directory called /home/user/node-red-static/
   - download andcopy all your library files (xxx.js) content into that directory
   - you need library : anime.min.js (https://github.com/juliangarnier/anime/blob/master/lib/anime.min.js)
   - set httpStatic in your settings file to /home/user/node-red-static (line be like :  httpStatic: '/home/user/node-red-static/',)
   - restart Node-RED
   - check you can load http://YOUR_NODERED_IP:1880/xxx.js in your browser.
   - Credit for this chapter : Knolleary https://discourse.nodered.org/t/import-javascript-library-into-node-red/7665
 - Nodered import
   - Copy the content of the git file : "nodered_flow.json"
   - In nodered dashboard go to options and "Import"
   - Paste the file content and click "Import"
 - Nodered configuration
   - Go to "Banner Web Page" node
   - On line 30 replace "YOUR_NODERED_IP" by your nodered server IP
   - Click "Done"
   - You may have to modify the "Dashboard" layout to place button and text-input correctly. See the officiel documentation : https://flows.nodered.org/node/node-red-dashboard

 - Using
   - Go to http://YOUR_NODERED_IP:1880/ui (you can also integrate it in an OBS dock)
   - In OBS create a browser source with URL : http://YOUR_NODERED_IP:1880/banner ; width : 1920 (minimum, to reduce it put more and resize the object); height : 100
   - Set text in input text, click button "BANNER ON" to display it, clikc "BANNER OFF" to hide it
   - Text is update only on display, so you can change it in text input when banner is alread display to prevent next message

 - Credit
 Create by tainalo2 : french streamer on twitch every week day from 07H to 09H (Paris hours)
 All my links here : https://linktr.ee/tainalo2
