# spotify-tui-package  
Debian bookworm packages for spotify-tui : spotify client for the terminal written in Rust.  
( https://github.com/Rigellute/spotify-tui )  
  
I builded these packages because they are not in debian 12 repository.  
x64,i386 & armhf packages provided.  
  
I slighty modified the source script in order to launch spotifyd (if it is installed) when the application start, and terminate it when the application exit.
It's convenient if, like me you don't want spotifyd to run when not needed. (this way it is more like spotify-qt behavior who can launch spotifyd at start and terminate it when exiting.)
(you can check the modified main.rs file in /src folder)
  
# installation:  
  
download appropriate package for your architecture, and do (for example for 32bits package):  
  
```
sudo apt install ./spotify-tui-0.25.0_i386.deb
```
(or install with graphical .deb installer if you have one, for example QSI installer for q4os: left click the .deb, then 'open with' and choose QSI installer)  
  
The package takes care of creating the corresponding '.desktop' entry (so you will have access to spotify-tui from your menu).  
There's a postinstall script that configure this .desktop file to set the size of the konsole windows that will be used to display spotify-tui almost as large as your screen resolution. The reason behind that, besides the fact it is more convenient, is that I discovered the playlists windows is 'truncated' if the windows is too small at start, it doesn't display all the playlists (I have a lot) and no way to have more than the few displayed. (need to open an issue for that in the spotify-tui owner's github).  
Of course, you can edit this desktop file ( /usr/share/applications/spotify-tui.desktop ) to modify or remove the geometry argument.  
  
* There are great chances that you want to listen to music locally, so you will have to install too the 'spotifyd' package, you can found it here along with instructions to configure it:
 https://github.com/seb3773/spotify-qt-spotifyd-packages  
  
  
# Connecting to Spotify’s API
(the above text is taken from https://github.com/Rigellute/spotify-tui README ):  
  
spotify-tui needs to connect to Spotify’s API in order to find music by name, play tracks etc.  
Instructions on how to set this up will be shown when you first run the app.  
  
But here they are again:  
  
Go to the Spotify dashboard  
Click Create an app  
You now can see your Client ID and Client Secret  
Now click Edit Settings  
Add http://localhost:8888/callback to the Redirect URIs  
Scroll down and click Save  
You are now ready to authenticate with Spotify!  
Go back to the terminal  
Run spt  
Enter your Client ID  
Enter your Client Secret  
Press enter to confirm the default port (8888) or enter a custom port  
You will be redirected to an official Spotify webpage to ask you for permissions.  
After accepting the permissions, you'll be redirected to localhost. If all goes well, the redirect URL will be parsed automatically and now you're done. If the local webserver fails for some reason you'll be redirected to a blank webpage that might say something like "Connection Refused" since no server is running. Regardless, copy the URL and paste into the prompt in the terminal.  
And now you are ready to use the spotify-tui 🎉  
  
  
----------------
