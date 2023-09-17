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

For example, if you want to make a speed command, you'd have one argument be the player, and the other a number (the speed the player wants to set).
The speed command already exists, this is just for an example.

You'd need to get the player, and as you saw on the previous page, you can use the `_aux` module to check if the player argument from the sender is "all" or "other," as well as 
```lua
--// This one shows you how to do it for just one player

Cmds.speed = function(sender: Player, arguments: {any})
    local player = _aux.getPlayer(arguments[1]) --// Since "arguments" is a table, and the first argument for this command is the player, you index the table with "1" to get the name of the player.

    if _aux.isMe(arguments[1]) then --// As described on the previous page, this function will check if the selected argument is "me", and set the corresponding player to the sender.
        player = sender
    end

    if player then
        --// This is where code gets ran.
    else
        GUI:Notify(sender, "Error", "First and/or second player is not in the experience") --// Using the GUI module in AdminService, this will give the sender a notification if the player variable is nil.
    end
end
```

```lua
--// This one shows you how to do it for other, all, or one player.

Cmds.speed = function(sender: Player, arguments: {any})
    local status = _aux.plrStatus(arguments) --// As described on the previous page, this function will check if any of the arguments for a player are "other" or "all," then it will run functions later correspondingly.

    if status == "other" then
        _aux.forOther(sender, function(player) --// As described on the previous page, this will run the anonymous function passed for all players in experience except the sender.
            --// This is where code gets ran. (It is the exact same for all three spots)
        end)
    elseif status == "all" then
        _aux.forAll(sender, function(player) --// As described on the previous page, this will run the anonymous function passed for all players in experience.
            --// This is where code gets ran. (It is the exact same for all three spots)
        end)
    else
        local player = _aux.getPlayer(arguments[1]) --// Since "arguments" is a table, and the first argument for this command is the player, you index the table with "1" to get the name of the player.

        if _aux.isMe(arguments[1]) then --// As described on the previous page, this function will check if the selected argument is "me", and set the corresponding player to the sender.
            player = sender
        end

        if player then
            --// This is where code gets ran. (It is the exact same for all three spots)
        else
            GUI:Notify(sender, "Error", "First and/or second player is not in the experience") --// Using the GUI module in AdminService, this will give the sender a notification if the player variable is nil.
        end
    end
end
```

---

!!! notice
    As shown, it is not required to use `_aux.plrStatus`. It is completely optional

Once you have figured out the arguments needed, if you wanted it to work with "other" and "all" player types, and getting it in proper format (shown above), you need to write the actual code.

Since this example command is changing the player's speed, you need to get their character, then their humanoid, so that you can change the humanoid's WalkSpeed property.

The comments from the code blocks above will not be included here, only new ones. If you haven't read them (and especially if you want to), go read them from above.

```lua
Cmds.speed = function(sender: Player, arguments: {any})
    local status = _aux.plrStatus(arguments)

    if status == "other" then
        _aux.forOther(sender, function(player)
            local character = player.Character or player.CharacterAdded:Wait() --// Gets the player's character, and if it doesn't exist yet, it will return the character that is given from the CharacterAdded event.
            local humanoid = character:WaitForChild("Humanoid")

            if character and humanoid then
                if arguments[2] then --// Checks if the second argument (the number to set as the WalkSpeed) exists.
                    local speed = tonumber(arguments[2]) --// Converts the argument (a string) into a number
                    humanoid.WalkSpeed = speed
                end
            end
        end)
    elseif status == "all" then
        _aux.forAll(sender, function(player)
            local character = player.Character or player.CharacterAdded:Wait() --// Gets the player's character, and if it doesn't exist yet, it will return the character that is given from the CharacterAdded event.
            local humanoid = character:WaitForChild("Humanoid")

            if character and humanoid then
                if arguments[2] then --// Checks if the second argument (the number to set as the WalkSpeed) exists.
                    local speed = tonumber(arguments[2]) --// Converts the argument (a string) into a number
                    humanoid.WalkSpeed = speed
                end
            end
        end)
    else
        local player = _aux.getPlayer(arguments[1])

        if _aux.isMe(arguments[1]) then
            player = sender
        end

        if player then
            local character = player.Character or player.CharacterAdded:Wait() --// Gets the player's character, and if it doesn't exist yet, it will return the character that is given from the CharacterAdded event.
            local humanoid = character:WaitForChild("Humanoid")

            if character and humanoid then
                if arguments[2] then --// Checks if the second argument (the number to set as the WalkSpeed) exists.
                    local speed = tonumber(arguments[2]) --// Converts the argument (a string) into a number
                    humanoid.WalkSpeed = speed
                end
            end
        else
            GUI:Notify(sender, "Error", "First and/or second player is not in the experience")
        end
    end
end
```

Although it is repetitive using the same code three times (kind of breaking the D.R.Y rule), it is preferable to having to repeat the same code every single time to check what the status of arguments for players, create a for loop specifically for other players, and a for loop for all players. It is a lot more compressed than it would be.
And a lot more preferable than having a module just for command functions to run inside of the function for a command inside of the `Cmds` module. It sounds gross just typing that sentence.

---

!!! notice
    This next step is also very important, because it will not show up in the "cmds" menu when using the `cmds` command!

Anyway, after you have created your full command, there is one more thing you have to do.

You have to open the `Descriptions` module inside of the `Cmds` module, then add a table like this inside of the module's table:
```lua
cmdname = {
    Description = "The description must be a string, just like this! Make a description of what the command does."
    Arguments = {"Player", "Number"} --// These are just examples. Make as many arguments that are used for the command (it is not recommended to make something that needs more than five), and make sure they are in the order the command uses them, otherwise a player will type something incorrectly and it will not work how you want.
}, --// This comma at the end is very important. Without it, the script will error because it will not know how to separate it from the next index of the table. 
```

---

And that is the process of making custom commands! Bravo, have a medal! :medal:

[Previous Page](https://amorafolf.github.io/AdminService/basics/_aux_module/){ .md-button .md-button--primary } [Next Page](https://amorafolf.github.io/AdminService/basics/updating/){ .md-button .md-button--primary }