# The `_aux` module

`D.R.Y.` One of the most basic and most important rules in programming. It stands for Don't Repeat Yourself, and it should always be followed! It's a method of organizing your code so it doesn't turn into what is called "spaghetti code," which is a term used to describe programming that is very disorganized, poor, ugly, slow, and overall a nightmare. That at least is my connotative definition of it.

Anyway, enough side tracking; the `_aux` module, short for "auxiliary", is used to help keep organized and follow `D.R.Y`. This is accomplished by using a function to check the "player status," so whether or not a player variable was entered as "all" or "other," or if it was just a player instead. As well as it utilizes other functions like `isMe()` to check if a specific argument is equal to "me", so the command will run for the sender and they don't have to write their full username.

The rest is explained in the "Read Me Important" module inside of AdminService.

---

### Permissions, Game Passes, and Group Ranks

Unlike what you're probably familiar with in HD Admin and how the permission gets higher with the bigger number, the lower number means higher permission in AdminService.
Permissions also only restrict certain very high level commands, like using `/ban` or `/unban`. Every command can be run by someone with the lowest permission, unless restricted using the `_aux.hasPermission()` function to check.

The way permissions are setup is also a little weird compared to HD Admin using nested tables, however, that was the best way it would work with how it was all programmed before permissions were added in.

Adding players into permissions is very simple. `1` is the highest permission, and `3` has the lowest. Every permission has a table inside called `Players`. You add the `UserId` of every player you want to give that permission.

# Refer to the "Read Me Important" module inside of AdminService for more information.