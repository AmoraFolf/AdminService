# Adding Commands

Adding your own commands to AdminService is very easy.

All you need is your idea, the level of knowledge needed to code that idea, and the resources to create it.

All commands have a certain format. They all must be created in a specific way, and must have two specific parameters.

!!! warning
    There should not be more or less parameters than the two, and they should not be changed, otherwise the entirety of AdminService has the potential to break and stop working.

Here is how new commands should be created:

Open up the `Cmds` module inside of AdminService. It does not matter where the command is inserted into the module, as long as it is not inside of another command. It must remain outside of other commands.

The format is creating an anonymous function inside of the module's table, `Cmds`, with an index, then setting the index equal to a function. It should look like this:
```lua
Cmds.cmdname = function() --// cmdname is what you want to name the command

end
```

!!! warning
    The name of the command, so what you type after `Cmds.`, must be all lowercase, otherwise it will not work. There cannot be a single capital letter. `Cmds.cMdname` must be changed to `Cmds.cmdname`

After creating the command, you need to add the parameters, otherwise you can't even do anything with it!
The two parameters you need to add are called `sender` and `arguments`

`sender` is the player who triggered the command, and `arguments` is a table of the arguments passed by the player when using the command. An example would be `{PlayerName, 50 --[[This number could be setting the speed or something]]}`
These parameters get put into the brackets after `function`.
```lua
Cmds.cmdname = function(sender, arguments)

end
```

You may notice that every other command has a colon ':', as well as "Player" and "{any}" after the `sender`, and `arguments` parameters. This is to set the type of the parameter to unlock properties you normally wouldn't have, because Roblox wouldn't have any idea what the parameters are supposed to be without it. It is very easy to add this yourself
```lua
Cmds.cmdname = function(sender: Player, arguments: {any})

end
```

!!! notice
    Adding the types to the parameters is not necessary for it to work, but it is very helpful when coding the command!

---

Next, you need to figure out what arguments are needed for this to work, and what to do with them.

