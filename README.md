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
