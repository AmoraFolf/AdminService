# The "Read Me Important" module

There is nothing to read on this page!

All this page contains is the contents of the "Read Me Important" module inside of AdminService in case you deleted it, want it check it out here, or whatever other reason you don't in studio.

---

---

---

AmoraFolf's AdminService:

Current version: UNDER_DEVELOPMENT:1.0.0-PRIVATE
The most recent version will always be listed on the Roblox model page, Roblox DevForum post, and documentation.

When updating, be sure to copy every custom command you've made, and the description for them into the new version before deleting the old version, otherwise they will
be deleted!

---

Credit:

I only want credit I built into this module. You can add more credit if you want, but please do not change or remove the credits placed into the built-in GUI!

---

Thank you so much for using AdminService!

This is very easy to setup. All you need to do is require the AdminService module in a server sided script in ServerScriptService,
and in a PlayerAdded event, run AdminService.init(player)


The script could look like this:

local Players = game:GetService("Players")
local AdminService = require(script:WaitForChild("AdminService"))

Players.PlayerAdded:Connect(AdminService.init)

---

The module is completely open source, and you can change just about everything in it, as well as add your own commands!

To add your own commands, you add them into the "Cmds" module inside of AdminService by creating a new function doing "Cmds.cmdName = function(sender, arguments)"
The _aux module has functions to very easily do code that you would need to repeat a lot. It helps you follow the D.R.Y rule in programming!

You just have to remember to follow the format of the built-in commands, using the _aux module script to detect specific things for you.
And do not forget to add the new description values in the Descriptions module. Copy and paste the last table in the module, make sure there's a comma after it
then paste it and change it according to the function's info (i.e. name (must be the exact same), description of it, and arguments it takes)

Also don't forget to make the name of the command inside of the commands module all lowercase, otherwise it won't find the command to run in the main module
using "local status = _aux.plrStatus(arguments)" is required to be used in any command you create that has a player for an argument

---

Important Information and Terms:

Important Information:

Under absolutely zero conditions, AdminService should NEVER be ran by a LocalScript. In most cases, it will cause errors, and will lead to extreme vulnerabilities
 in the service from exploiters. All code that should be handled by the client is automatically done by AdminService.
AdminService should be placed somewhere in ServerScriptService. It does not matter if it is a direct child of ServerScriptService, or if it's in a folder, or in a
 tree of different folders, the ancestor or direct parent must be ServerScriptService, otherwise AdminService is at risk of vulnerabilities from exploiters. Especially
 with certain commands, exploiters can (and likely will) cause serious damage to your experience.


Terms:
	1. Everything built into AdminService are following Roblox's Terms of Service and Community Guidelines. Anything you add, such as UI, imrpoper text filtering, commands,
		and anything else you can add, that is in violation of Roblox ToS and Community Guidelines is on you, and the creator, AmoraFolf, and any other developers and
		contributers of the module have no responsibility.
	2. Do NOT redistribute AdminService or any of its other modules, take and reuse code for your own public Roblox models or other public work (including the entire
		internet) without sufficient credit to the creator and original model, or violate any other conditions under the GNU General Public License v3.0 on Roblox or any
		other site and platform. Any work found in violation of the license will have action taken against it to be removed from Roblox or other site on the internet.

---

Explaining _aux:

The _aux module script is used to organize code in the Cmds module so it isn't thousands of lines long with repeating if statements

_aux.plrStatus(data) is used to check all of the players in the arguments, or if it is entered as "other" or "all"

_aux.getPlayer(name) is used to get a player from their username in the arguments

_aux.isMe(argument) is used to check if the specific argument in a command provided is equal to "me", so it will run the command with the sender so they don't have to
type their full username

_aux.forAll(sender, function(player) will run code provided running _aux.forAll for ALL players. It is very important you add "player" into the parameters when writing
the anonymous function

_aux.forOther(sender, function(player) will run code provided by the script running _aux.forOther for all players except the person running the command. It is very
important you add "player" into the parameters when writing the anonymous function

_aux.hasPermission(player) is used to check if a player has a certain permission level or higher to be able to run specific commands. If a player's permission level is
zero and they are an admin (which they have to be to have the permission level NumberValue), they will have access to all commands not restricted by permission checks

_aux.getCharacters() will return a table of the characters for every player in the experience