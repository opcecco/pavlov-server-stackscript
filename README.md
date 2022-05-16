# Quick & easy Pavlov VR dedicated server with Linode StackScripts

This guide will show you how to use Linode StackScripts to quickly set up a Pavlov VR dedicated server for PC or Shack (Quest).

Linode is a cloud hosting provider that focuses on providing Linux powered virtual machines to support a wide range of applications. StackScripts allow you to automatically configure new Linode instances using your own custom scripts, or scripts published by the community.

## Setting up a new server

1. Sign up on [Linode.com](https://www.linode.com/) and set up your account.

2. Once you reach the cloud dashboard, navigate to the "StackScripts" menu.

    (resources/screenshot.png)
    
3. Click on "Community StackScripts" and search for "pavlov". You should see a script called "zutano / Pavlov VR Dedicated Server" in the search results. Click on "Deploy New Linode" to create a new server instance.

    (resources/screenshot.png)
    
4. You should see several options for configuring your new server. The following options are required:

    - *Server Version* - Select between PC and Shack, stable or beta branch
    - *API Key* - An API key is now required for anyone who wants to host a server
        - You can obtain a key using Vankrupt's API key request tool: https://pavlov-ms.vankrupt.com/servers/v1/key
        - Be sure to save a backup of this key somewhere!
    - *Server Name* - The name of your server as it should appear in the in-game server browser
    - *RCON Password* - Password to access RCON admin commands (make this hard to guess)

    (resources/screenshot.png)
    
5. The next set of options are pre-filled with some default values, but can be changed to your liking.

    - *Server Password* - Password required to play on your server. This **must** be either a 4-digit PIN for private servers, or left blank for public servers.
    - *Map Rotation* - List of maps to be played on your server. This one can be a little complicated, so read carefully:
        - Each map needs a definition in the form `(MapId='map',GameMode='mode')`, replacing `'map'` with the ID of a default map or the UGC number of a workshop map, and replacing `'mode'` with the ID of a game mode
        - For workshop maps, the ID is `UGC` followed by the UGC number in the Steam workshop. If you navigate to a workshop map page in your web browser, you can find the ID within the URL of the page.
        - Take your map definitions and string them together separated by semicolons
        - Example rotation of default maps: `(MapId='datacenter',GameMode='SND');(MapId='bridge',GameMode='TDM');(MapId='sand',GameMode='GUN')`
        - Example rotation of workshop maps: `(MapId='UGC2432298572',GameMode='TDM');(MapId='UGC2575712044',GameMode='TDM')`
        - For a comprehensive list of default maps and modes, see the [Pavlov VR wiki](http://wiki.pavlov-vr.com/index.php?title=Dedicated_server)
        - **NOTE: This script does not support custom maps on Shack! If you want to add custom maps to a Shack server, you will need to SSH into your server and do some advanced configuration! See the [Pavlov VR wiki](http://wiki.pavlov-vr.com/index.php?title=Dedicated_server) for more details!**
    - *Max Players* - The maximum number of players that can connect to your server at once. Shack is limited to 10, but PC can go up to 24, although this will cause more strain on your server resources.
    - *Limited Ammo Type* - 0=Unlimited, 1=Limited Generic, 2=Limited Specific, 3=Custom (for modders), 4=Limited Special, 5=Boxless Mode. Refer to the [Pavlov VR wiki](http://wiki.pavlov-vr.com/index.php?title=Dedicated_server) for details.
    - *Competitive Mode* - Turn competitive mode on or off. This only works for SND mode.

    (resources/screenshot.png)
    
6. Below the Pavlov-specific server options you will see additional options for your server.

    - Only one Linux image is supported: Ubuntu 22.04 LTS
    - For "Region" select a datacenter close to you for the best ping
    - For "Linode Plan" you can select whichever plan suits your needs. The cheapest is the $5/month "Nanode" shared CPU plan. The Nanode plan should work for small servers with friends, but I suggest using a plan with more RAM for public servers. If you plan to support more than 10 players, I suggest one of the high-performance "Dedicated CPU" plans.
    - Optionally change your "Linode Label" to however your want your server to appear in the dashboard
    - Enter a "Root Password" for future SSH access to your server (make this hard to guess)

    (resources/screenshot.png)

7. The remaining settings shouldn't need to be changed. At the bottom of the page click "Create Linode".

8. **Congratulations!** Your Pavlov VR server is now up and running. The StackScript will need some time to download and configure the server files, so wait about 10 minutes before attempting to log in (longer if you added a lot of workshop maps). Once the server is ready to use, you should see it appear in the in-game server browser, or use a site like [pablub.xyz](https://pablub.xyz/) to verify that your server is visible.

## Advanced configuration

If you're interested in further configuration, or changing any of the options you set when you created the server, I highly suggest learning how to use SSH and reading up on how to edit your server's config files remotely. All of this info can be found on the [Pavlov VR wiki](http://wiki.pavlov-vr.com/index.php?title=Dedicated_server).

