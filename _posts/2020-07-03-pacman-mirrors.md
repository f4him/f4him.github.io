---
layout: post
title: Fix poor download speed in terminal when updating or installing new packages on manjaro
description: Fix poor download speed in terminal when updating or installing new packages on manjaro.
summary: Fix poor download speed in terminal when updating or installing new packages on manjaro.
tags: manjaro linux
minute: 3
---



I remember, like every other day I fired up my potato and may be an hour later when i finally logged in, I opened up terminal and wrote the divine mantra to make my device new.

    sudo pacman -Syu

Then I saw the download speed was around a few kbps even though my internet speed was a decent one. 

So, I surfed the internet and found out about **pacman-mirrors**.
Pacman-mirrors is a Manjaro specific utility for generating and maintaining the system mirror-list.

Manjaro uses pacman as package manager for maintainence, updates, installations and removal of packages.

For pacman to function, a list of servers, or more commonly known as mirrors, with Manjaro software packages is required. As Manjaro has many mirrors all over the world it is feasible to use the mirrors closest to our location and preferably also up-to-date.

Here is how you can use pacman-mirrors to select the closest server so you get the best possible download speed.
    
<br>
##### To list available countries in the default mirror pool execute this command on your terminal:

    pacman-mirrors --country-list

##### To list available countries in custom mirror pool execute this:

    pacman-mirrors --country-config

##### To check what branch you are on:

    pacman-mirrors --get-branch

<br>

>Here was the main problem I was facing. I didn’t know that Bangladesh has an official manjaro mirror. It is hosted in Xeonbd’s Bangladesh Data Center since 2018. So, I configured my pacman-mirrors for a custom mirror pool (In this case it was Bangladesh, obviously) and my problem was solved.

<br>
##### To Update mirror-list with the fastest mirrors you can invoke this command:

    sudo pacman-mirrors --fasttrack

Remember, after changing the mirror-list you have to synchronize pacman with the newly configured mirror-list.

##### You can synchronize pacman by this command:

    sudo pacman -Syyu

So it’s better to execute the command like this:

    sudo pacman-mirrors --fasttrack && sudo pacman -syyu
<br>

##### To use your current location as a mirror, you can invoke this command:

    sudo pacman-mirrors --geoip && sudo pacman -Syyu

>Note: Not all countries have mirrors, if geoip returns a country not in the pool all mirrors will be used.

<br>
##### Customize mirror pool by specific countries:

If you have checked the mirror-list and you are certain about using a custom mirror pool by some specific countries, you can use this command to do so:

    sudo pacman-mirrors --country Germany,France,Austria && sudo pacman -Syyu
Customize mirror pool by interactive selection:

If you are not so comfortable supplying all arguments in commands, you can do this by an interactive selection too. This command will do it:

    sudo pacman-mirrors --interactive --default && sudo pacman -Syyu

Here, using the `--default` flag will list all available mirrors and procotols in a gui windows allowing to sort the columns and interactively select according to your preferences. If you don’t use `--default` flag all the mirrors from current list (wheather default or not) will be listed.

When you save your selection, a custom mirror pool is created and will serve as your current mirror pool.

>Don’t limit the mirror list in a custom pool too much. pacman will always use the up-to-date mirrors and ignore the other mirrors. So, keep in mind what you are doing.

The customized pool is saved as `/var/lib/pacman-mirrors/custom-mirrors.json`

If you think you have gone too far and dont know where you are and what to do, you can always reset everything. To apply pacman-mirrors defaults:

    sudo pacman-mirrors --country all --api --protocol all -set-branch stable && sudo pacman -Syyu

The system will now throw messages about newer packages on the system. These messages can safely be ignored and they dissappear when the installed package(s) equals the system branch.

Hope this helped you solving your terminal download speed issue.

For more info on pacman-mirrors you can always head to our friend `man`:

    man pacman-mirrors

To get help on usage:

    $ pacman-mirrors --help

To check Version:

    $ pacman-mirrors --version

I am glad if this piece of writing did help you in any way. 
All the informations here was taken from [manjaro-wiki](http://https://wiki.manjaro.org/index.php/Pacman-mirrors "manjaro-wiki").


