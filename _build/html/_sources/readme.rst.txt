Readme
===========================================

morrowind scripts categorized and writes

partially copy pasting from from MSFD and wikis

activate

    can force player activation on ID by activate, player (vanilla usage without unload cell reference)(2099)

    not restricted inside if (onactivate == 1) as in vanilla (needs checking)

animation

    playgroup, gruop
        plays the animation group in kf file applying it to function target

        is the same behavior for 1st and 3rd person view (npc and player alike) referred

        don't loop animations with no loop keys (revision 8bc7eb55)(2223)(2304)

    LoopGroup



AI

    setflee, -attack, -etc
        (distance dependancy?)

    getAIpackagedone
        return 1 if the package is done
        vanilla/openmw repair: returns value when next package is called to bypass skipped frame.

    startcombat, target
        starts the comnat with given target

            vanilla: in scripts only works to existing references and first found target.
                also placeatme and placeatpc are untargetable
            works in console
            workaround to place reference to somewhere and use positiocell when needed

            openmw: striggering when the id is found ingame (ie. not giving error of unfound id before)
            should be possible as position needs unique id, but could overlap if the position from other cell is
            anyway used. leading to fix for referencing any id in any cell interfere.

            placeatpc and placeatme could also be used in mod as way to safeguard from one from dublicate id
            otherwise after 1.0 it could be fixed with keywork to handle multiple targets and so on out of the bucket

            TEST : current status

    equip, objectID
        equips the given item in the owner inventory

        vanilla: works randomly differing in script and console ie. potions and armors, repair hammers and such

        openmw: should work without problems.

        TEST : creatures?

check variables

    onpcequip
        -check after item is equipped to prevent stack contamination (2969)
        -working with addfunctions inside menumode + realtime updating screens (2967)
        -don't set onpcequip for items that failed to equip (revision 992b7703)
            revent's walse alarm in worn item check (2776)
        -use on equip function (revision c04a8afc)
        -run the script after setting OnPcEquip, but before actually equipping the item to allow setting onPCskipequip             (Bug #3016) not exactly right bug (mentions)

        revision 7983b07b (bk_treasurereport script)
            check also on using enchanted (any) items
            pcskipeguip variable handling ( 1 = skip equipping, 0 = allow )
            execute item script once, immediately after getting onpceguip
            bypass after skipped with pcskipequip and pcskipequip set to 0 allowing afterhand equip (same script?)

movement

    setangle, axis, angle
        workings ingame and via scripts?

    getangle, axis
        returns the angle in relation to given world axis

    rotate, axis, speed
        reference's axis

    rotateworld, axis, speed
        global axis

    difference in local and global rotation in openmw?

    face, target
        makes the npc face the desired target


position

    -interior and exterior behaviour when using underground, outside or in allowed space
    -if something fails, player is teleported to coe 0,0 , daedric ruin with scamp running around


    coe, centeronexterior and coc, centeroncell
        -don't copy the height info when teleporting causing possible death on ground level

    position
        effect of water and groundlevel on behavior

    positioncell
        places the reference inside the cell into given coordinates

            vanilla: buggy. accepting float variables is picky and moving object from far away cell
            is not guaranteed to load + arbitary move can cause crash on activation

            openmw: should work right out of the bucket with variables and loading + script execution

    placeatpc, ID, distance, direction
        places given object

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

inventory related

    addsoulgem, creature, soulgem

        vanilla: referencded soulgem need to be in target inventory for function to work
        openmw: adds soulgem if not alredy in inventory


if

    no nested if / elseif limit like in vanilla or script lenght for that matter

elseif

while

    will execute after whole script is run once due to structure
    preventing getting getbuttonpressed from inside while loop for if condition


unittest


requests: (wishlist)

unequip like function / disable / setdelete on worn items (2960)

    base scripts need removeitem and additem for all similar content in
    inventory losing script variable data, nonunique reference being unrefencelable
