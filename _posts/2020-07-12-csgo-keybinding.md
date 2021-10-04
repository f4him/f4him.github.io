---
layout: post
title: CS:GO key binding and scripting on linux
description: CS:GO key binding and scripting on linux
summary: CS:GO key binding and scripting on linux
tags: CS:GO gaming
minute: 3
---

Buying weapons takes time in CS:GO and every second counts.

Before a round start we usually get a few seconds to buy things. Here, ‘things’ includes arms, different types of explosives and kits. Imagine you hit a keyboard key and items are bought instantly. No need to open the buy menu to buy items and waste time before every round starts.

I know that you already know about key binding in CS:GO.

For those who didn’t know, binding means to set a keyboard key to do some events like purchasing weapons, sending in-game messages  or may be decrease your mouse sensitivity. Normally, you have to manually do these events in the particular interfaces. But if you bind keys to these events, they can be done only by a single key stroke.

I play CS:GO on my manjaro linux. So, when I searched the internet over tutorials and howtos on key binding, I found a lot. But all of them were for windows platform. I was at a loss what to do or which file to edit for linux. So, after doing a lot of file searching, some guessing I found the way to permanently bind CS:GO commands to keyboard keys.

Here is how you can do it too.
##### Finding the config.cfg file:

Basically to bind the commands you have to go to the following location on your file system:

	/home/your_user_name/.local/share/Steam/userdata/1025583974/730/local/cfg/config.cfg
	

>If you have multiple accounts registered in your steam cleint, you will find multiple directories inside the `userdata` directory. Inside the user directory you will look for a directory named `730` as it is the game code of CS:GO.


Before you start playing with the config file, I will highly recommend you to keep a backup of the file. To back up fire up the terminal in the directory containg the config file and give the following command

    cp config.cfg config_backup.cfg 


##### Binding a single command:

Now to bind commands to a key, you have to follow the following format:

	bind “key_code” “command [arg]”

‘bind‘ is a keyword here, ‘key_code‘, ‘command‘ and ‘arg‘ (if there is) must be exchanged with actual key codes, command and the command’s argument respectively.

For example:

	bind “p” “buy defuser”

Here, ‘p’ is the key code, ‘buy‘ is the command and ‘defuser‘ is the argument.
Binding multiple commands:

You can also bind multiple commands to a single key, you have to follow the following format:

	bind “key_code” “command1 [arg1]; command2 [arg2]”

For example:
bind "l" "use weapon_c4;drop;say_team dropping bomb"
Now, pressing ‘L’ will immediatly drop the c4 no matter which slot you are equipped with and a team message “dropping bomb” will be sent.

You have to append these commands in the config file each on a newline.

There is also another method to bind keys on the developer console. After binding, there you have to export the binds to a file. Then the contents of the files have to be pasted in the config file. That method is effective for newbies who has to check the functionality of the scripts by playing at the same time. But if you know what you are doing then I suggest you to directly append the bindings to the config file.

>As I have experienced, on linux, this `config.cfg` file is executed automatically everytime your game launches. So, unlike windows, you won’t have to put any launch options to auto execute your config file everytime the game launches.

Here’s an example of some standard bindings.
    
    // buy binds
    bind “kp_home” “buy ak47; buy m4a1;”
    bind “kp_uparrow” “buy awp;”
    bind “kp_pgup” “buy negev;”
    bind “kp_leftarrow” “buy flashbang;”
    bind “kp_5” “buy smokegrenade;”
    bind “kp_rightarrow” “buy molotov; buy incgrenade;”
    bind “kp_end” “buy vesthelm;”bind “kp_downarrow” “buy defuser;”
    bind “kp_pgdn” “buy p250;”
    bind “kp_del” “buy vest;”
    bind “kp_slash” “buy ump45;”
    bind “kp_multiply” “buy p90;”
    
Once you’ve set your binds, your next step is to practice them and become adjusted to their functionality. This will inevitably take time to get used to, but the more you practice, the better you become. Eventually, the buy menu will be a breeze, giving you time to focus on strategy and get your head in the game.

You should also check the functionality of the ‘alias‘ command in CS:GO scripts to make your scripts simpler and more manageable.

Here is a [tool](http://csgobindsgenerator.com/ "tool") to help you with generating buy binds.
