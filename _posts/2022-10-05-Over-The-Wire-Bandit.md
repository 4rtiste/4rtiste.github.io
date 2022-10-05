---
title: Over the Wire - Bandit
tags: Wargame Linux
cover: /assets/images/overthewire/bandit/bandit.png
---

# Level 0
*`"The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1."`*

First, we find out all options off **`ssh`**{:.warning} with the command:
```zsh
┌──(kali㉿kali)-[~]
└─$ ssh   
usage: ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-B bind_interface]
           [-b bind_address] [-c cipher_spec] [-D [bind_address:]port]
           [-E log_file] [-e escape_char] [-F configfile] [-I pkcs11]
           [-i identity_file] [-J [user@]host[:port]] [-L address]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-Q query_option] [-R address] [-S ctl_path] [-W host:port]
           [-w local_tun[:remote_tun]] destination [command [argument ...]]
```
Option **`-p`{:.warning}** is the port. So, if we want to connect the host **`bandit.labs.overthewire.org`** with port **`2220`** and the username is **`bandit0`**, we could use: **`ssh bandit0@bandit.labs.overthewire.org -p 2220`{:.warning}**.
```zsh
┌──(kali㉿kali)-[~]
└─$ ssh bandit0@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

bandit0@bandit.labs.overthewire.org's password: 

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org
```
# Level 0 → Level 1
*`"The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game."`*

After login with username **`bandit0`**, found **`readme`** file with command **`ls`{:.warning}** and the target is just access file.
```zsh
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme 
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
```
**Password: NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL**
{:.success}
# Level 1 → Level 2
*`"The password for the next level is stored in a file called - located in the home directory"`*

Login bandit1 with the password abose. At this time, when using **`ls`{:.warning}**, but this time there is no **`readme`** file but just one Dash (symbol **`-`**) exist. 
```zsh
bandit1@bandit:~$ ls
-
```
In [**Dashed Filename – Learn How to Create, Remove, List, Read & Copy!**](https://www.webservertalk.com/dashed-filename), there are ways to access filename starting with Dash: Using **`cat < -`{:.warning}** or **`cat ./-`{:.warning}**.
```zsh
bandit1@bandit:~$ cat ./-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
bandit1@bandit:~$ cat < -
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```
**Password: rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi**
{:.success}
# Level 1 → Level 2