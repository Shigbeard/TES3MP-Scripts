## Werewolf Robe
### VERSION 1.0

![Werewolf Robe](https://i.imgur.com/7Ylemds.png)

This small script adds a chat command `/wwrobe` that allows players on the server to equip the elusive "Werewolf Robe". This item is essentially the body of a werewolf and is actually given to player when it turns into a werewolf, however, the item cannot be seen in inventory. Still, the item is saved in the player's datafile, so it can be kept track of. The scripts allows some customization, such as:

• Who is allowed to equip the robe (everyone/mods and admins/admins only)
• Whether the process cost anything (both the item and the amount of item)

## Installing instructions

1) Copy `WWRobe.lua` to `...\<tes3mpfolder>\mp-stuff\scripts`.

2) Open `serverCore.lua` with a text editor.

3) Add `WWRobe = require("WWRobe")` at the top, along with all other included scripts.

4) Find `if myMod.OnGUIAction(pid, idGui, data) then return end` near the end of the file and add `if WWRobe.OnGUIAction(pid, idGui, data) then return end` below that line.

5) Save `serverCore.lua`. Open `commandHandler.lua`.

6) Find `local message = "Not a valid command. Type /help for more info.\n"`. Above you will see `else` line of code. Above THAT line of code, add `elseif cmd[1] == "wwrobe" then WWRobe.Initialize(pid)`.

7) Save `commandHandler.lua`. Open `help.lua` in `...\scripts\menu\` folder. 

8) Find `color.White .. "Open up a small crafting menu used as a scripting example\n" ..` and below it add
```
        color.Yellow .. "/wwrobe\n" ..
            color.White .. "Equip werewolf robe\n" ..
```
to include the new command in the `/help` function.

9) Save `help.lua`. Start your server and type `/wwrobe` in chat to see some magic.

10) (OPTIONAL) Open `WWRobe.lua` and edit the variables at the top of the file.

## CHANGELOG:
### 1.0:
Instructions updated for 0.7.x.