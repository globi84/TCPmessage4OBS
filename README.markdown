TCPmessage4OBS
==============

A background serve that recieve TCP messages to transmit to the OBS websocket server.



### Prerequisits

* [OBS](https://obsproject.com/de/download)
* [OBS Websocket](https://github.com/obsproject/obs-websocket/releases/latest)
* [OBSCommand](https://github.com/REALDRAGNET/OBSCommand/releases/latest)

How to use:

* Install `OBS` and `OBS Websocket` and start it.
* Create some scenes in obs
* Download `OBSCommand` and unzip the archive. For Example `c:\scratch\OBSCommand`
* Clone the git repo https://github.com/globi84/TCPmessage4OBS
* Check the path to the `OBSCommand.exe` at `TCPMessage4OBS_server.ps1` and run it from the command line.
* Run now `TCPMessages4OBS_testclient.ps1` from the command line.
* Now you should be ready to remote controll your OBS.

```powershell
#Start VirtualCam
Send-TCPMessage -Port 29800 ` -Endpoint 127.0.0.1 -message "=StartVirtualCam"
#Stop VirtualCam
Send-TCPMessage -Port 29800 ` -Endpoint 127.0.0.1 -message "=StopVirtualCam"

#Switch to Scene "Speaker"
Send-TCPMessage -Port 29800 ` -Endpoint 127.0.0.1 -message "=SetCurrentScene,scene-name=Speaker"
```
It should work with every command, that are defined at https://github.com/obsproject/obs-websocket/blob/4.x-current/docs/generated/protocol.md

### Help

If you get an error, when you start the powershell script, then you need enable to run it.

```powershell
c:\temp\TCPMessage4OBS_server.ps1 : File C:\temp\TCPMessage4OBS_server.ps1 cannot be loaded because running scripts
is disabled on this system. For more information, see about_Execution_Policies at
http://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ c:\temp\TCPMessage4OBS_server.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : SecurityError: (:) [], PSSecurityException
+ FullyQualifiedErrorId : UnauthorizedAccess
```

then you sould run the following command on a elavated console.

```powershell
Set-ExecutionPolicy RemoteSigned
```

after this. should everything work.
