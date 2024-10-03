# gitle
Gitle is my spin on git, supposed to be less of a pain to deal with.<br>
Unlike git, it is not suited for big or comercial products, only small personal projects by a single person.<br><br>
So what is it?<br>
All this is is a small program/library that helps you to sync up code across devices, where you can instantly propagate changes to a server.<br>
It is compatible with .gitignore (and that is about it)<br><br>
I mostly made it for my own needs. The code is not maintained to be too readable or customizable as a final product. Use on your own risk.
<br><br>
The auth system is much more simplified from Git. Forget the pain of SSH keys, accounts, github tokens and what not. It is a simple client to server relation via a persistent json web token (JWT).<br>
When you make any local changes, its just a single command to automatically propagate them on your server (can also work as a simple save to push, but be sure not to accidentaly push something you dont want).<br><br>
The command set is also extremely simplified. Forget having to make commits, merge.. pull.. uh.. whatever, just change a file and press the big red "LAUNCH" button.
<hr>

## Usage
1) Install gitle - its a simple node.js script with just a few dependencies, so try to figure this out. Unless this gets some actual interest, I'm not gonna bother with some fancy installation scripts.<br>For Linux, gitle.js should be in your /bin directory (as a symlink) and that should be it. If you are on Windows, too bad, you'll have to mess with the PATH variable or resort to a text config.<br>
<br>

2) Configure gitle

- Server
```sh
# If this is the first time, you should get the JWT for the client to use:
gitle get-token
```

- Client
```sh
# If this is the first time, you should setup the server first:
gitle connect [IP:PORT]
# This will then ask you for your JWT token
```

3) Use gitle

- Server
```sh
gitle init "name" .
```

- Client
```sh
gitle link "name" .
```
This acts basically the same as "git clone".<br>
After you make changes, either use the GUI or push changes like this:
```sh
# You can review changes
gitle diff

# Publish changes
gitle push
```
This will automatically sync them up on the server. <br>
You can setup automatic push on changes or frequency:
```sh
# On every change, push changes if the changes were at least 0.5s apart and more than one thing changed
gitle event on-change="push" if "elapsed > 500 && changes > 1"
```
To use for backups and such, you can setup local clones which will always sync up, even for small changes:
```sh
gitle init -l "name" .

# ...

gitle link -l "name" .
```
