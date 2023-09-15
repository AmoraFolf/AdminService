# AdminService

![adminservice_icon](/images/logos/temporary_icon.png)

**The official documentation on the open source module 'AdminService,' the versatile, easy-to-work-with admin module for any and all Roblox developers to use!**

~~This website is very ugly right now. It will get better the more I learn how to use GitHub pages (and when I can learn how to use themes. Why did they have to take away the "Change Theme" button. It was so simple, now I have no idea what to do, the documentation is extremely unhelpful, and I can't find any videos online about it. Someone please help 😭😭😭😭😭😭)~~

---

### What is AdminService?

AdminService is an open source module meant to make admin commands easy!

With the module being open source, and its user-friendly work envrionment, you can easily add commands, even with very low level knowledge of Luau. Though, they may be basic and restrained by that.. but you will be able to do more the more you learn.

### Click [here](https://www.youtube.com) to view the DevForum post about AdminService. This documentation is where the most information is.

---

### Setup

>IMPORTANT!
>
>Small amounts of setup is needed. Without it. AdminService will not work.


Most, if not every admin command module or system requires no setup. With the way AdminService is designed, it unfortunately does, but it's done in only three lines of code!

Despite needing setup via another script as already mentioned, it only takes three lines of code; however, you need to insert the module before you can do anything else.

If you don't have the module, [get it here](https://create.roblox.com/marketplace/asset/14663644773/AdminService).

---

In Studio, you need the toolbox open if you don't already. Go to the `Home` tab at the very top, or the `View` tab, and click the `Toolbox` button in either tab.
Next, you have to insert the module by going to "My Models"

![screenshot](/images/screenshots/toolbox1.png)

Then you click on the model to insert it:

![screenshot2](/images/screenshots/toolbox2.png)

It may prompt you with a notification saying the model includes scripts. Just click "Ok" to insert it:

![screenshot3](images/screenshots/modelcontainsscripts.png)

Next, it should appear in the `Workspace`. Drag it from there into `ServerScriptService`, or into a folder in `ServerScriptService`. You could also put it in `ServerStorage` or a folder in there instead.

![screenshot4](images/screenshots/inworkspace.png)
![screenshot5](images/screenshots/insss.png)

Then insert a new script into `ServerScriptService`:

![screenshot6](images/screenshots/newscript.png)

Then inside of the script, add the following three lines of code:
```lua
local Players = game:GetService("Players") --// Accesses the Players service. This is "Players" in the Explorer.
local AdminService = require(script.Parent:WaitForChild("AdminService")) --// Gets the AdminService module to be used, and sets everything else needed up automatically after running.

Players.PlayerAdded:Connect(AdminService.init) --// Runs the initializer for the player and sets everything up for them.
```

And boom, you've setup AdminService!

---

### The `_aux` module

`D.R.Y.` One of the most basic and most important rules in programming. It stands for Don't Repeat Yourself, and it should always be followed! It's a method of organizing your code so it doesn't turn into what is called "spaghetti code," which is a term used to describe programming that is very disorganized, poor, ugly, slow, and overall a nightmare. That at least is my connotative definition of it.

Anyway, enough side tracking; the `_aux` module, short for "auxiliary", is used to help keep organized and follow `D.R.Y`. This is accomplished by using a function to check the "player status," so whether or not a player variable was entered as "all" or "other," or if it was just a player instead. As well as it utilizes other functions like `isMe()` to check if a specific argument is equal to "me", so the command will run for the sender and they don't have to write their full username.

The rest is explained in the "Read Me Important" module inside of AdminService.

---

### Permissions, Game Passes, and Group Ranks

Unlike what you're probably familiar with in HD Admin and how the permission gets higher with the bigger number, the lower number means higher permission in AdminService.
Permissions also only restrict certain very high level commands, like using `/ban` or `/unban`. Every command can be run by someone with the lowest permission, unless restricted using the `_aux.hasPermission()` function to check.

The way permissions are setup is also a little weird compared to HD Admin using nested tables, however, that was the best way it would work with how it was all programmed before permissions were added in.

Adding players into permissions is very simple. `1` is the highest permission, and `3` has the lowest. Every permission has a table inside called `Players`. You add the `UserId` of every player you want to give that permission.

---

### Troubleshooting and support

...

If you've had errors and nothing here has helped your problem, if you have an important question that wasn't solved here or anywhere else, or if you need extra support, PM me on the DevForum!
[This is my profile](https://devforum.roblox.com/u/amorafolf/summary)


---

### Thank you for choosing or looking into AdminService!

I hope you have a great rest of your day or night!

![amorafolfgames](images/logos/AmoraFolf_Games_256x128.png)
