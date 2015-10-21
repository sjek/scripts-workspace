# scripts-workspace
morrowind scripts categorized and writes

partially copy pasting from from MSFD and wikis 

activate

    -can force player activation on ID by activate, player (vanilla usage without unload cell reference)(2099)
    -not restricted inside, if onactivate == 1 as in vanilla

animation

    playgroup 
        -is the same behavior for 1st and 3rd person view (npc and player alike) referred
        -don't loop animations with no loop keys (revision 8bc7eb55)(2223)(2304)
  
AI

    setflee, -attack, -etc 
        (distance dependancy?)

check functions

    onpcequip
        -check after item is equipped to prevent stack contamination (2969)
        -working with addfunctions inside menumode + realtime updating screens (2967)
        -don't set onpcequip for items that failed to equip (revision 992b7703)
            revent's walse alarm in worn item check (2776)
        -use on equip function (revision c04a8afc)
        
        revision 7983b07b (bk_treasurereport script)
            check also on using enchanted (any) items
            pcskipeguip variable handling ( 1 = skip equipping, 0 = allow )
            execute item script once immediately after setting onpceguip
            bypass after skipped with pcskipequip and pcskipequip set to 0 + equip (same script?)

movement

    setangle 
        
        workings ingame and via scripts
        
    rotate 
    rotateworld 
        difference in local and global rotation in openmw?
  
position

    -interior and exterior behaviour when using underground, outside or in allowed space
    -if something fails, player is teleported to coe 0,0 , daedric ruin with scamp running around
    

    coe, centeronexterior and coc, centeroncell
        -don't copy the height info when teleporting causing possible death on ground level
    position 
        effect of water and groundlevel on behavior
    placeatpc
        non vanilla safeguards on bad placement?
    fixme unimplemented (1421)
        hard to detect collision at random relocation 

messsagebox

    behavior at different tages
        on screen
        script
        dialogue
        multiples (almost impossible to detect on runtime)
        
    getbuttonpressed
        
    dialogue
    

if

elseif

while

    will execute after whole script is run due to structure
......

unittest ?


requests:

unequip like function / disable / setdelete on worn items (2960)

    base scripts need removeitem and additem for all similar content in 
    inventory losing script variable data, nonunique reference being unrefencelable
