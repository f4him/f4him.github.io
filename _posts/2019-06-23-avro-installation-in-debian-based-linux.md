---
layout: post
title: Installing Avro and fixing up Bangla font problem on Debian based Linux
description: Installing Avro and fixing up Bangla font problem on Debian based Linux
summary: Installing Avro and fixing up Bangla font problem on Debian based Linux
tags: debian linux bangla avro ibus-avro
minute: 2
---

If you have installed a fresh debian based linux distro (Kali, Ubuntu, Deepin etc) and you need to work with Bangla font, you will need to install Avro and also some Bangla fonts.

Installing avro will let you type in Bangla where installing the fonts will fix the preview of joint letters (Jukta borno).

If you do not know what is avro, it’s a system which supports most modern English to Bangla phonetic typing method. For example, write anywhere “ami banglay gan gai” and it will be automatically typed as “আমি বাংলায় গান গাই”.

>If you cant see the above bangla text or it appears as broken boxes in your bowser, installing the fonts will fix this issue.

In linux, you can install avro through ibus-avro. This software works as an Engine (plugin) of IBus and let users type in English and on-the-fly transliterate them phonetically to Bangla.

<br>

Features of ibus-avro:

- 100% compatible with the current Avro Phonetic scheme.
- A preview window lets you see the originally typed text right under the cursor.
- Enabling dictionary can predict and suggest phonetically similar words with correct spelling on the fly.
- Commonly used English words are transliterated to Bangla (like, Facebook, download etc.) even with their original English spelling.
- All the preferences are customizable.

<br>

#### Installing ibus-avro:

**Step 1 – Installing dependencies:**

You need to install the following packages. Use the command as shown below for debian based distros:

	apt-get install git ibus libibus-1.0-dev automake autoconf gjs gir1.2-ibus-1.0 ibus-1.0


**Step 2 – Installing ibus-avro:**

Once the dependencies are installed, copy the git repository for ibus-avro through the following command:

	git clone git://github.com/sarim/ibus-avro.git

After the completion of cloning, go inside the git directory, compile, configure and install ibus-avro by giving the following commands step by step:

	cd ibus-avro
	aclocal && autoconf && automake --add-missing 


>If for some reasons, this command doesn’t work for you, just give the commands one by one, without using the && like shown below:
    aclocal
    autoconf
    automake --add-missing 
    
after the successful completion of these 3 commands add the `--prefix=/usr` flag to configuration.

	./configure --prefix=/usr 
	sudo make install

Done.

<br>

##### Setting up Bangla as an input method:

- Run IBus (Applications->System Tools->IBus)
- Open IBus Preferences right-clicking the panel icon
- Go to Input method
- Select an input method -> Bengali -> Avro
- Now Click Add button to add Avro to the list
- Now restart IBus from the top panel icon (Right Click -> Restart)
- Now Press Ctrl+Space to toggle between English and Avro (Bengali)
- Enjoy Avro Phonetic!

<br>

#### Installing Bangla fonts:

Now that avro is installed, you can type in Bangla without any problem. There might be one more issue though. You are most likely to see certain joint letters not showing up properly (like: স্থান, শাস্ত্র, পঞ্চাশ etc).

If this is the case then you have to install some bangla fonts.

<br> 

**To install Bangla fonts:**

- Download some Bangla fonts from [here](https://github.com/f4him/bangla-fonts "here").
- Go to your home directory.
- Turn show hidden files on, Create a directory named .fonts (if it’s not already there)
- In that directory create a folder bangla_fonts and paste all the downloaded fonts there.
- Open terminal, type this command `fc-cache -fv` and hit Return.
- All the fonts should be loaded now.

Restart applications you were using in the running session and you will see everything is showing up correctly and no letters are broken or anything.

