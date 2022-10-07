---
title: Over the Wire - Bandit
tags: Wargame Linux
cover: /assets/images/overthewire/bandit/bandit.png
---

# Level 0
*"The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1."*
<p align="center">
---
</p>

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
*"The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game."*
<p align="center">
---
</p>

After login with username **`bandit0`**, found **`readme`** file with command **`ls`{:.warning}** and the target is just access file. To access `readme`, we could use command **`cat`{:.warning}**.
```zsh
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme 
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
```
**Password: NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL**
{:.success}
# Level 1 → Level 2
*"The password for the next level is stored in a file called - located in the home directory"*
<p align="center">
---
</p>

Login bandit1 with the password abose. At this time, when using **`ls`{:.warning}**, but this time there is no **`readme`** file but just one Dash (symbol **`-`**) exist. 
```zsh
bandit1@bandit:~$ ls
-
```
When you cat that file, it will get stuck because The Dash interprets it as a synonym for STDIN. In [**Dashed Filename – Learn How to Create, Remove, List, Read & Copy!**](https://www.webservertalk.com/dashed-filename), there are ways to access filename starting with Dash: Using **`cat < -`{:.warning}** or **`cat ./-`{:.warning}**.
```zsh
bandit1@bandit:~$ cat ./-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
bandit1@bandit:~$ cat < -
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```
**Password: rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi**
{:.success}
# Level 2 → Level 3
*"The password for the next level is stored in a file called spaces in this filename located in the home directory"*
<p align="center">
---
</p>

This time, we have a file which has space in name. 
```zsh
bandit2@bandit:~$ ls
spaces in this filename
```
To cat the file, we can write filename as string by double quote or use the **`\`{:.warning}** symbol.
```zsh
bandit2@bandit:~$ cat "spaces in this filename"
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
bandit2@bandit:~$ cat spaces\ in\ this\ filename 
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```
**Password: aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG**
{:.success}
# Level 3 → Level 4
*"The password for the next level is stored in a hidden file in the inhere directory."*
<p align="center">
---
</p>

This time we have a folder `inhere`, but in normal view, there's nothing in folder.
```zsh
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ 
```
Trying using command **`ls`{:.warning}** again. But this time, we put 2 option: **`-a`{:.warning}** and **`-1`{:.warning}**.

- **`-a`{:.warning}**: listing all file, do not ignore entries starting with **`.`{:.warning}**
- **`-1`{:.warning}**: list one file per line.

So the full command is: **`ls -a1`{:.warning}**
```zsh
bandit3@bandit:~/inhere$ ls -a1
.
..
.hidden
```
Now we just access the file and get password.
```zsh
bandit3@bandit:~/inhere$ cat .hidden 
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
```
**Password: 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe**
{:.success}
# Level 4 → Level 5
*"The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command."*
<p align="center">
---
</p>

Here, there's a folder `inhere` again, and this time, we have 10 files in it.
```zsh
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$ ls -a1
.
..
-file00
-file01
-file02
-file03
-file04
-file05
-file06
-file07
-file08
-file09
```
The simplest way is just access each file with **`cat`{:.warning}** until finding readable file. 
```zsh
bandit4@bandit:~/inhere$ cat ./-file00
��Q�6
     ▒�V����gH��b���v��Qȇ� 
bandit4@bandit:~/inhere$ cat ./-file01
▒q$`8��&[S�S����IE����2; 
bandit4@bandit:~/inhere$ cat ./-file02
�G)=I��O� 
          $܌۶&������/v���%� 
bandit4@bandit:~/inhere$ cat ./-file03
���&���l���r�▒QEd8�tQ׼��e����O 
bandit4@bandit:~/inhere$ cat ./-file04


���ٷxw�Diz�;�B���m�z�������
bandit4@bandit:~/inhere$ cat ./-file05
��!��>E�+�����"�K�bg
                    ����
��I=4
bandit4@bandit:~/inhere$ cat ./-file06
^�f����s�_��c�$!C��j�?迟�Mt 
bandit4@bandit:~/inhere$ cat ./-file07
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
```
Or we could use **`cat ./-file0*`{:.warning}**, it will show all content of files which have **`-file0`** in their name.
```zsh
bandit4@bandit:~/inhere$ cat ./-file0*
��Q�6
     ▒�V����gH��b���v��Qȇ�▒q$`8��&[S�S����IE����2;�G)=I��O� 
                                                            $܌۶&������/v���%����&���l���r�▒QEd8�tQ׼��e����O

                                                                                                           ���ٷxw�Diz�;�B���m�z���������!��>E�+�����"�K�bg
                                                                                                                                                          ����
��I=4^�f����s�_��c�$!C��j�?迟�MtlrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
�O��\�p�1سNF���z�#Z�Z`�#ї
\�(�J,l6��e���PT4"��:�����~`�q
``` 
But these ways have one problem, they show all contents of file, which have lots of unreadable bytes. So we need another solution to fixing this.

Let use **`find`{:.warning}**, here we use option **`-type f`{:.warning}** for searching regular file and put together with xargs to execute command lines (here is **`file`{:.warning}**) to files we found. The result will give us type of files in folder. After that just cat the file.
```zsh
bandit4@bandit:~$ find . -type f | xargs file
./.profile:       ASCII text
./.bashrc:        ASCII text
./.bash_logout:   ASCII text
./inhere/-file03: data
./inhere/-file04: data
./inhere/-file09: data
./inhere/-file07: ASCII text
./inhere/-file08: data
./inhere/-file06: data
./inhere/-file05: data
./inhere/-file01: data
./inhere/-file02: data
./inhere/-file00: OpenPGP Public Key
bandit4@bandit:~$ cat ./inhere/-file07
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
bandit4@bandit:~$ 
```
**Password: lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR**
{:.success}
# Level 5 → Level 6
*The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:*

- *human-readable*
- *1033 bytes in size*
- *not executable*
<p align="center">
---
</p>

