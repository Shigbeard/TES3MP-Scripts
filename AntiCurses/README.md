## AntiCurses
### VERSION 1.0

This script automatically removes any Dremora Lords, Ancestral Ghosts or Dwemer Ghosts created by the cursed items when a player picks one up. Server owners can choose to not remove entities spawned by certain items.

## INSTALLING INSTRUCTIONS

1) Copy `antiCurses.lua` to `.../tes3mp/mp-stuff/scripts`.

2) Open `serverCore.lua` with a text editor.

3) Add `antiCurses = require("antiCurses")` at the top, along with all other included scripts.

4) Find `base.lua` file located in `../tes3mp/mp-stuff/scripts/cell/` and open it with a text editor.

5) Find first instance of `self:RemoveLinkToRecord(recordStore.storeType, refId, uniqueIndex)`. After the two `end`s below, add
```
if wasPlacedHere then
    antiCurses.CheckItem(pid, refId)
end
```

The entire block would look something like this:
```
elseif logicHandler.IsGeneratedRecord(refId) then
    local recordStore = logicHandler.GetRecordStoreByRecordId(refId)

    if recordStore ~= nil then
        self:RemoveLinkToRecord(recordStore.storeType, refId, uniqueIndex)
    end
end
if wasPlacedHere then
    antiCurses.CheckItem(pid, refId)
end
```

6) Save `base.lua` file and you should be good to go - test out different cursed items ([list found here](http://en.uesp.net/wiki/Morrowind:Cursed_Items)) to make sure nothing spawns when you pick it up from the ground.

## SETTINGS

The script contains a minor list of settings:
```
local disableDremoras = true
local disableDremorasSpecial = true
local disableGhosts = true
local disableDwemerGhosts = true
```

Each variable defines whether or not to remove a specific type of enemy from a cursed item list. Since cursed gold does not naturally appear in the game, one may wish to use it as a special currency on their server. Thus, it will be possible to "disarm" those coins, while keeping other cursed items working as intended, if you wish.

## CHANGELOG:
### 1.0:
Script updated for 0.7.x.