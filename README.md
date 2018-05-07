# MiddlewareIce

This is the streaming application for middleware subject.  
---
<img src="images/screen.png" width="50%" height="50%">

## Description
I created an Android application which can display musics available on several servers.  
For the purpose of the tests, I only created 2 servers with 2 musics (low upload rate) on each servers.

You can select any musics displayed and it will be played in streaming.

## Objectives
- [x] Implement streaming on the app
- [x] Create an Android client application (java)
- [x] Implement a message service (IceStorm)

## Libs & techno used
I used python vlc lib for the streaming service since I started to develop it in python.  
IceBox and IceStorm to create a pub/sub service with a metaServer and subservers which contains musics.  
Java and Ice for the Android client so that it can communicate with the metaServer.

## Running the app
Go to Server/IceStormPythonService/META  
Launch IceBox with > icebox --Ice.Config=config.icebox  
Launch > metaServer.py   

Go to Server/IceStormPythonService/SubServers  
Launch > server1.py & server2.py  

Launch or open with android studio the 'AndroidIce' project.  

Click on any music and listen!