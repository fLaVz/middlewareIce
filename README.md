# MiddlewareIce

This is the streaming application for middleware subject.  
---
<img src="images/screen.png" width="50%" height="50%">

## Description
I created an Android application which can display musics available on several servers.  
For the purpose of the tests, I only created 2 servers with 1 music (low upload rate) on each servers.

You can select any musics displayed and it will be played in streaming.

## Objectives
- [x] Implement streaming on the app
- [x] Create an Android client application (java)
- [x] Implement a message service (IceStorm)

## Libs & techno used
I used python vlc lib for the streaming service since I started to develop the server in python.  
IceBox and IceStorm to create a pub/sub service with a metaServer and subservers which contains musics.  
Java and Ice for the Android client so that it can communicate with the metaServer.  
All Ice version are 3.7  

Google exo player for android.

## Running the app
First, Clone or download these 2 projects:
- Server : https://github.com/fLaVz/IceStormPythonService  
- Client : https://github.com/fLaVz/AndroidIceClient

Go to IceStormPythonService/META  
Launch IceBox and the metaServer:  
> icebox --Ice.Config=config.icebox  
> python metaServer.py   

Go to IceStormPythonService/SubServers 
Launch the subservers:  
> python server1.py & python server2.py  

Launch or open with android studio the 'AndroidIce' project, build and run. 

Click on any music and listen!  

## Structure explanation

### Android client
Ice is implemented in the gradle build. This allows the application to generate Ice
definitions so that the application can communicate with the metaserver.  
Google exo player is also implemented to read the streaming link provided by the subservers.
I used the google player because I had buffering issues with the classic android media player.  

### Meta Server
The meta server is basically a "parser" which takes the name of the song and the action 
to do on subservers. IceStorm is implemented in order to communicate with several servers 
and playlists/songs.  
This server act as a publisher for the IceStorm service.

### SubServers
These servers contains physicals .mp3 files and can create streaming links that the android application 
read trough the player.   
These servers are subscriber of the IceStorm service.


## Troubleshooting
If the app is not working please verify the subservers status.
If they are not working as intended:  
> Delete all the files in Server/IceStormPythonServer/db folder and restart everything  

If the app displays a white screen:
> Server AND/OR IceBox is not running and the app cannot connect to the service

## Repos
Both server and client are available through git repos:
- Server : https://github.com/fLaVz/IceStormPythonService  
- Client : https://github.com/fLaVz/AndroidIceClient