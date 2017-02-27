--------------- INTRODUCTION ---------------

Readme file for Contagion GUI mod for Baldur's Gate 2: Enhanced Edition v 2.3672 (or 2+ idk).

The main goal of the mod - return old-school "black on white" fonts. 
Contagion GUI is a comsetic GUI mod for BG2:EE based on the WEIDU (https://github.com/WeiDUorg/weidu)
installer.
Mostly it will replace some MOS (graphics) and *.LUA (configuration) files that will slightly change
the background for text areas and the text's font colors. 

Modified files: BGEE.LUA, UI.MENU, BOX5.PVRZ (only standard version), GUIREC2.MOS, INVENTOR.MOS, INVSTATS.MOS, GUIWLSP.MOS, GUIWRSP.MOS

Actually this mod will replace this files, but I hope I will fix it in the future.

--------------- INSTALLATION ---------------

1. Unpack the archive content in your game-root directory
( i.e. D:\Program Files\Baldur's Gate 2: Enhanced Edition)
in this directory must be chitin.key file, if there not, find chitin.key file and unpack an archive
in the same location.

2. Execute the ContagionGuiMod_setup.exe, this actually WeiDU program for BG modding

3. If all is fine you will see console and then 'Done .. Press Enter'

--------------- UNINSTALL ---------------

To uninstall mod just run ContagionGuiMod_setup.exe again, and follow instructions. 

Inventory fonts and background - INVENTOR.MOS

Character record, biography/kit_description, player statistics - and GUIREC2.MOS
 
Left and right sided panels backgrounds -  GUIWLSP.MOS and GUIWRSP.MOS

The dialogue box - BOX5.PVRZ

--------------- COMPABILITY, configuring ---------------

Tested on Baldur's Gate 2: Enhanced Edition v 2.673 or something like that. This mod can be installed during game in progress, this mod does not interact with save-game files, I hope so. So it can be easily installed and removed, whatever you want. 

This mod by default, overrides UI.MENU, and BGEE.LUA, which is means this mod will undo any other GUI mods, so if you want to install this mod along with other, in this case you can find helpful information about manual changes - 

To check for detailed inforamtion looat at *.DEBUG and WeiDU.log files in the directory with Chitin.key (usually root directory of the game). 

=== Baldur.lua (where saves) ===

Add this string - 

SetPrivateProfileString('Program Options','UI Edit Mode','1') 

- this will place UI.MENU file into "override" folder in the same folder where Chitin.key file, and allow you to use <F11> (be careful, when using it... it can make changes that may be hard to find in the UI.MENU) key to enter into UI-editing mode, and <F5> to reload UI.MENU without restarting the entire game program, if UI.MENU edited (very useful) .

Use Nearinfinity (link to download in "USED PROGRAMS" section) - find BGEE.LUA in the LUA section , export it to override folder in your root game directory (or in the directory where Chitin.key file exist, read manuals about installing WeiDU mods on BG).

=== BGEE.LUA ===

search for "styles = ", right above you will see "fontcolors = ()" , add this string in the fontcolors stack.  

fontcolors['Y'] = '21030401' -- Contagion Gui mod Black

in the end of "styles = " column, before closing parenthesis, add this 

CGuiMod = 
	{
		color = 'Y',
		font = 'NORMAL',
		point = 12,
		valign = 'top',
		halign = 'left',
	useFontZoom = 1,
	}

This will create a new program for font. detailed modification can be found in "BG2:EE - UI.MENU .." section 

--------------- BG:EE + DLC: Siege of Dragonspear ---------------

0. Download link. 

1. Installation : just extract the stuff from the archive-file to the directory where Chitin.key, usually the root directory of the game. And then run ...

2. Unistallation: run ... again, and follow instruction. 
It is WeiDU program. 

Manual configuring and compability with the other mods: 

Of course SoD UI is impressive, much more impressive than BG2:EE, but as for myself I liked old school black on white text-styles. So I decide to modify SoD UI too. 
This mod can be installed any time during game progress, because this mod is only cosmetic and not changes anything that is not connected ti the graphical user interface, game parameters, save-game files, etc obviously including. 
But this mod in the default installation just copying to "override" folder next files: BGEE.LUA, UI.MENU, INVENTOR.MOS + MOS57000.PVRZ, invstats.MOS, GUIREC2.MOS + MOS57001.PVRZ . So this mod will delete the all other UI mods ! To prevent this. if you want to use this mod with the other UI-mods, you need to install this mod, making a manual modification. I have listed the all modification that I have done in the files.

NOTE: *.MOS v2, is just a small "link" to the *.PVRZ data file, that is an image data-file that can carry an information about transparency. The game have limited numbers of *.PVRZ file-indexes. In the CGUI mod I have used the next indexes - MOS57000, and MOS57001, if the any other mod will use the same indexes for *.PVRZ data-files - will happens something horrible...  

Basically there is the same changes in Baldur.lua, and in BGEE.LUA, as in the case of Baldur's Gate 2: EE. 

=== Baldur.lua (where saves) ===

added string:

SetPrivateProfileString('Program Options','UI Edit Mode','1')

=== BGEE.LUA ===

section "fontcolors = ()" , added:

fontcolors['Y'] = '21030401' -- Contagion Gui mod Black

then in the section "styles = " (in the end of the section) added this stuff (dont forgot about comma "," after the "}" , before the "CGuiMod): 

	CGuiMod = 
	{
		color = 'Y',
		font = 'NORMAL',
		point = 12,
		valign = 'top',
		halign = 'left',
	useFontZoom = 1,
	},
	CGuiModl =
	{
		color = 'Y',
		font = 'MODESTOM',
		point = 14,
		useFontZoom = 0,
		valign = 'center',
		halign = 'center',
	},
	CGuiModlg =
	{
		color = 'Y',
		font = 'POSTANTI',
		point = 12,
		useFontZoom = 1,
		valign = 'top',
		halign = 'left',
	}
	
CGuiMod - mod of "normal" font, CGuiModl - mod of "label" font, CGuiModlg - mod of "gamelog" font (only for standard version, with modifications of dialogue box stuff)
For detailed modification, look in "SOD - UI.MENU.." section. 

=== BG2:EE - UI.MENU (which also will be in your override folder!) === 

NOTE: The changes only in two fields "text style" and "area" which is means the used font, default font usually was "normal" and we changed it to our "CGuiMod", and the are field means a position and size of the elements. 

NOTE: "area" field - first two numbers is a coordinates of top left corner of the respective element, first number (from the left) - is HORIZONTAL coordinate, second number is VERTICAL coordinate  the origin point of the coord. system is a top-left corner of the screen, so if you want move up your element, you must decrease second number for some value, if you want move right your element, you need to increase first number by some value. 

Number of line - 794, 
this is information table in Charrec menu. Changed font, and the size (and obviously this changed a position of the top left corner too) a little bit.

NOTE: Upper fields - changed, lower default!

NOTE: I can miss something, if that may haps - me sorry. 

Line 794 - Biography sections stuff, Charec menu. 

text
	{
		enabled		"showJustText"
		area		54 176 342 428
		text		lua "helpTextString"
		text style  'CGuiMod'
		text align	left top
		scrollbar	'GUISCRC'
	}

text
	{
		enabled		"showJustText"
		area		54 186 342 408
		text		lua "helpTextString"
		text style  'normal'
		text align	left top
		scrollbar	'GUISCRC'
	}

Number of line - 640, 
this is class table in Charrec menu.

	text
	{
		enabled		"showClassInfo"
		area		54 176 342 428
		text		lua "getClassString()"
		text style  'CGuiMod'
		scrollbar	'GUISCRC'
	}
	
	text
	{
		enabled		"showClassInfo"
		area		50 182 342 412
		text		lua "getClassString()"
		text style  'normal'
		scrollbar	'GUISCRC'
	}

Number of line - 651, 
this is abilities table in Charrec menu.


	-- ability bonus stuff
	
	list
	{		
		column 
		{ 
			width 100
			label
			{
				area		0 0 -1 -1
				text		lua "listItems[rowNumber][2]" 
				text style  'CGuiMod'
				text align	left center

			}
		}

		area 54 176 342 428
		
		enabled		"showAbilityBonuses"
		rowheight	45
		table		"listItems"
		var			currentItem
		scrollbar	'GUISCRC'		
		hidehighlight
		action
		"
			--helpTextString = Infinity_FetchString( listItems[currentItem][1].helpStrRef)
		"		
	}

	list
	{		
		column 
		{ 
			width 100
			label
			{
				area		0 0 -1 -1
				text		lua "listItems[rowNumber][2]" 
				text style  'normal'
				text align	left center

			}
		}

		area 50 182 342 418
		
		enabled		"showAbilityBonuses"
		rowheight	45
		table		"listItems"
		var			currentItem
		scrollbar	'GUISCRC'		
		hidehighlight
		action
		"
			--helpTextString = Infinity_FetchString( listItems[currentItem][1].helpStrRef)
		"		
	}
	
Number of line - 680, 
this is statistics table in Charrec menu.

	-- Stats screen stuff
	list
	{		
		column 
		{ 
			width 65
			label
			{
				area		0 0 -1 -1
				text		lua "Infinity_FetchString(otherlist[rowNumber][1])" 
				text style  'CGuiMod'
				text align	left center

			}
		}
		column 
		{ 
			width 35
			label
			{
				area		0 0 -1 -1
				text		lua " otherlist[rowNumber][2]"				
				text style  'CGuiMod'
				text align	center center
			}
		}

		area 50 182 346 186
		
		enabled		"showStats"
		rowheight	45
		table		"otherlist"
		var			currentItem
		scrollbar	'GUISCRC'		
		hidehighlight
		action
		"
			--helpTextString = Infinity_FetchString( listItems[currentItem][1].helpStrRef)
		"		
	}

	-- Stats screen stuff
	list
	{		
		column 
		{ 
			width 65
			label
			{
				area		0 0 -1 -1
				text		lua "Infinity_FetchString(otherlist[rowNumber][1])" 
				text style  'normal'
				text align	left center

			}
		}
		column 
		{ 
			width 35
			label
			{
				area		0 0 -1 -1
				text		lua " otherlist[rowNumber][2]"				
				text style  'normal'
				text align	center center
			}
		}

		area 50 182 346 186
		
		enabled		"showStats"
		rowheight	45
		table		"otherlist"
		var			currentItem
		scrollbar	'GUISCRC'		
		hidehighlight
		action
		"
			--helpTextString = Infinity_FetchString( listItems[currentItem][1].helpStrRef)
		"		
	}

Number of line - 721, 
this is "Game" label in STATS screen in Charrec menu.

label
	{
		enabled		"showStats"
		area		338 368 54 38
		text		"GAME_LABEL"
		text style  'CGuiMod'
		text align	center center
	}

	label
	{
		enabled		"showStats"
		area		338 368 54 38
		text		"GAME_LABEL"
		text style  'label'
		text align	center center
	}


Number of line - 729, 
this is "Chapter" label in the Stats screen in Charrec menu.


	label
	{
		enabled		"showStats"
		area		262 368 76 38
		text		"CHAPTER_LABEL"
		text style  'CGuiMod'
		text align	center center
	}

	label
	{
		enabled		"showStats"
		area		262 368 76 38
		text		"CHAPTER_LABEL"
		text style  'label'
		text align	center center
	}

Number of line - 738, 
this is bottom list in Stats screen in Charrec menu.


	list
	{		
		column 
		{ 
			width 65
			label
			{
				area		0 0 -1 -1
				text		lua "Infinity_FetchString(listItems[rowNumber][1])"  --lua " '^M' .. Infinity_FetchString(listItems[rowNumber][1]) .. '^-' .. '\n'  .. trunc(Infinity_FetchString( listItems[rowNumber][3]), 140)"
				text style  'CGuiMod'
				text align	left center

			}
		}
		column 
		{ 
			width 20
			label
			{
				area		0 0 -1 -1
				text		lua " listItems[rowNumber][2]"				
				text style  'CGuiMod'
				text align	center center
				
			}
		}
		column 
		{ 
			width 15
			label
			{
				area		0 0 -1 -1
				text		lua " listItems[rowNumber][3]"				
				text style  'nCGuiMod'
				text align	center center
				
			}
		}

		area 54 406 350 188
		
		enabled		"showStats"
		rowheight	45
		table		"listItems"
		var			currentItem
		scrollbar	'GUISCRC'		
		hidehighlight
		action
		"
			--helpTextString = Infinity_FetchString( listItems[currentItem][1].helpStrRef)
		"		
	}

	list
	{		
		column 
		{ 
			width 65
			label
			{
				area		0 0 -1 -1
				text		lua "Infinity_FetchString(listItems[rowNumber][1])"  --lua " '^M' .. Infinity_FetchString(listItems[rowNumber][1]) .. '^-' .. '\n'  .. trunc(Infinity_FetchString( listItems[rowNumber][3]), 140)"
				text style  'normal'
				text align	left center

			}
		}
		column 
		{ 
			width 20
			label
			{
				area		0 0 -1 -1
				text		lua " listItems[rowNumber][2]"				
				text style  'normal'
				text align	center center
				
			}
		}
		column 
		{ 
			width 15
			label
			{
				area		0 0 -1 -1
				text		lua " listItems[rowNumber][3]"				
				text style  'normal'
				text align	center center
				
			}
		}

		area 54 406 350 188
		
		enabled		"showStats"
		rowheight	45
		table		"listItems"
		var			currentItem
		scrollbar	'GUISCRC'		
		hidehighlight
		action
		"
			--helpTextString = Infinity_FetchString( listItems[currentItem][1].helpStrRef)
		"		
	}

Number of line - 543, 
this is list of parameters (INT, CHR etc) table in Charrec menu.


list
	{
		column 
		{ 
			width 65
			label
			{
				area		0 0 -1 36 
				text		lua "Infinity_FetchString( attributeItems[rowNumber][1].strRef)"
				text style  'CGuiMod'
				text align	left center
			}
		}
		column 
		{ 
			width 35
			label
			{
				area		0 0 -1 36 
				text		lua  "displayAttr(rowNumber)" --"listItems[rowNumber][1].current"
				text style  'CGuiMod'
				text align right center
				text shadow lua "isStatModified(rowNumber)"
				
			}
		}

		area 426 144 152 216
		
		rowheight	36
		table		"attributeItems"
		var			currentItem
		hidehighlight
		action
		"
			helpTextString = Infinity_FetchString( attributeItems[currentItem][2])
		"		
	}

	list
	{
		column 
		{ 
			width 65
			label
			{
				area		0 0 -1 36 
				text		lua "Infinity_FetchString( attributeItems[rowNumber][1].strRef)"
				text style  'normal'
				text align	left center
			}
		}
		column 
		{ 
			width 35
			label
			{
				area		0 0 -1 36 
				text		lua  "displayAttr(rowNumber)" --"listItems[rowNumber][1].current"
				text style  'label'
				text align right center
				text shadow lua "isStatModified(rowNumber)"
				
			}
		}

		area 426 144 152 216
		
		rowheight	36
		table		"attributeItems"
		var			currentItem
		hidehighlight
		action
		"
			helpTextString = Infinity_FetchString( attributeItems[currentItem][2])
		"		
	}

Number of line - 582, 
this is applied effects list in Charrec menu.


	list
	{
		column 
		{ 
			width 13
			label
			{
				area		0 0 22 -1
				bam			lua "statusEffects[rowNumber].bam"
				sequence	lua "statusEffects[rowNumber].current"
				text align	center center				
			}
		}
		column 
		{ 
			width 87
			label
			{
				area		0 0 -1 -1
				text		lua "Infinity_FetchString(statusEffects[rowNumber].strRef)"
				text style  'CGuiMod'
				text align	left center
			}
		}

		area 420 486 164 94
		rowheight	dynamic
		table		"statusEffects"
		var		notrealValue
		scrollbar	'GUISCRC'
		hidehighlight	
	}

	list
	{
		column 
		{ 
			width 13
			label
			{
				area		0 0 22 -1
				bam			lua "statusEffects[rowNumber].bam"
				sequence	lua "statusEffects[rowNumber].current"
				text align	center center				
			}
		}
		column 
		{ 
			width 87
			label
			{
				area		0 0 -1 -1
				text		lua "Infinity_FetchString(statusEffects[rowNumber].strRef)"
				text style  'normal'
				text align	left center
			}
		}

		area 420 486 164 94
		rowheight	dynamic
		table		"statusEffects"
		var		notrealValue
		scrollbar	'GUISCRC'
		hidehighlight	
	}

Number of line - 629, 
this is Char description label in Charrec menu.


	label
	{
		area 610 492 194 92
		text lua "characterDescString(characters[currentID])"
		text style 'CGuiMod'
		text align center center
		
	}
	
	label
	{
		area 610 492 194 92
		text lua "characterDescString(characters[currentID])"
		text style 'normal'
		text align center center
		
	}


Number of line 615 - 
Char photo from Char Record screen, changed position for little bit


	button
	{
		name		"BUTTON_2_2"
		area		619 144 180 279
		--text		lua "characters[currentID].portrait"
		text align	center center
		text point	10
		text color	B
		bitmap		lua "characters[currentID].portrait"
		action
		"
			Infinity_Log(dump(characters, 0))
		"
	}

	button
	{
		name		"BUTTON_2_2"
		area		618 147 180 279
		--text		lua "characters[currentID].portrait"
		text align	center center
		text point	10
		text color	B
		bitmap		lua "characters[currentID].portrait"
		action
		"
			Infinity_Log(dump(characters, 0))
		"
	}

Number of line 5467 - 
Armory stats text details main, Inventory screen, changed position and font for a little bit. 


	text
	{
		enabled		"tempStats[id] == nil"
		area 609 55 248 79
		text lua "characters[id].AC.details"
		text style "CGuiMod"
		scrollbar 'GUISCRC'
	}

	text
	{
		enabled		"tempStats[id] == nil"
		area 605 55 248 79
		text lua "characters[id].AC.details"
		text style "normal"
		scrollbar 'GUISCRC'
	}
	
Number of line 5483 - 
HP stats text main, Inventory screen


	text
	{
		enabled		"tempStats[id] == nil"
		area 609 150 248 76
		text lua "characters[id].HP.details"
		text style "CGuiMod"
		scrollbar 'GUISCRC'
	}

	text
	{
		enabled		"tempStats[id] == nil"
		area 605 150 248 76
		text lua "characters[id].HP.details"
		text style "normal"
		scrollbar 'GUISCRC'
	}

Number of line 5500 - 
THACO stats main, Inventory screen


	text
	{
		enabled		"tempStats[id] == nil"
		area 609 244 248 72
		text lua "getInventoryTHAC0Details()"
		text style "CGuiMod"
		scrollbar 'GUISCRC'
	}

	text
	{
		enabled		"tempStats[id] == nil"
		area 605 244 248 72
		text lua "getInventoryTHAC0Details()"
		text style "normal"
		scrollbar 'GUISCRC'
	}

Number of line 5517 - 
Damage stats main, Inventory screen


	text
	{
		enabled		"tempStats[id] == nil"
		area 609 332 248 74
		text lua "getInventoryDamageDetails()"
		text style "CGuiMod"
		scrollbar 'GUISCRC'
	}

	text
	{
		enabled		"tempStats[id] == nil"
		area 605 332 248 74
		text lua "getInventoryDamageDetails()"
		text style "normal"
		scrollbar 'GUISCRC'
	}

Number of line 5675 - 
Character color button,


	button
	{
		area 460 96 50 52
		bam INVBUT
		colordisplay 1
		action
		"
			Infinity_PushMenu('CHARACTER_COLOR', 0, 0)
		"
	}

	button
	{
		area 458 98 50 52
		bam INVBUT
		colordisplay 1
		action
		"
			Infinity_PushMenu('CHARACTER_COLOR', 0, 0)
		"
	}

Number of line 5453 - 
INVENTORY stats details main rectangle, 


	label
	{
		enabled		"tempStats[id] == nil"
		area 516 44 349 376
		mosaic "INVSTATS"
	}

	label
	{
		enabled		"tempStats[id] == nil"
		area 512 44 349 376
		mosaic "INVSTATS"
	}

Number of line 5459 - 
Armor text label (inside the Shield). 


	label
	{
		enabled		"tempStats[id] == nil"
		area		544 70 38 40
		text lua	"characters[id].AC.current"
		text style	"label"
		align center center
	}

	label
	{
		enabled		"tempStats[id] == nil"
		area		540 70 38 40
		text lua	"characters[id].AC.current"
		text style	"label"
		align center center
	}

Number of line 5475 - 
Hit Points (circle). 


	label
	{
		enabled		"tempStats[id] == nil"
		area		538 159 44 42
		text lua	"characters[id].HP.current .. '/' .. characters[id].HP.max"
		text style	"label"
		align center center
	}

	label
	{
		enabled		"tempStats[id] == nil"
		area		534 159 44 42
		text lua	"characters[id].HP.current .. '/' .. characters[id].HP.max"
		text style	"label"
		align center center
	}

Number of line 5492 - 
Thaco. 


	label
	{
		enabled		"tempStats[id] == nil"
		area		544 254 34 42
		text lua	"getInventoryTHAC0()"
		text style	"label"
		align center center
	}

	label
	{
		enabled		"tempStats[id] == nil"
		area		540 254 34 42
		text lua	"getInventoryTHAC0()"
		text style	"label"
		align center center
	}

Number of line 5509 - Damage. 


	label
	{
		enabled		"tempStats[id] == nil"
		area		540 348 42 39
		text lua	"getInventoryDamage()"
		text style	"label"
		align center center
	}

	label
	{
		enabled		"tempStats[id] == nil"
		area		536 348 42 39
		text lua	"getInventoryDamage()"
		text style	"label"
		align center center
	}

Number of line 5626 (not modified) - 
Shiled slot, inventory. 
NOTE: buged slot Identifier in the f11 menu, is less by unit than real one 


	slot {name "slot_inv_25"		area 338 361 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.boots"		}

	slot {name "slot_inv_25"		area 338 361 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.boots"		}

Number of line 5618 - 
Amulet slot,


	slot {name "slot_inv_14"		area 404 96 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.amulet"		}

	slot {name "slot_inv_14"		area 398 98 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.amulet"		}

Number of line 5617 - 
Helmet Slot, 


	slot {name "slot_inv_13"		area 350 96 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.helmet"		}

	slot {name "slot_inv_13"		area 346 98 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.helmet"		}

Number of line 5616 - 
Gauntlets slot. 


	slot {name "slot_inv_12"		area 296 96 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.gauntlets"	}

	slot {name "slot_inv_12"		area 294 98 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.gauntlets"	}

Number of line 5615 - 
Armor slot,


	slot {name "slot_inv_11"		area 242 96 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.armor"		}

	slot {name "slot_inv_11"		area 242 98 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.armor"		}

Number of line 5627 - 
Shield Slot,


	slot {name "slot_inv_26"		area 462 243 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.shield"		}

	slot {name "slot_inv_26"		area 461 244 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.shield"		}

Number of line 5623 - 
Left Ring Slot, 


	slot {name "slot_inv_22"		area 217 302 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.ringleft"	}

	slot {name "slot_inv_22"		area 218 302 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.ringleft"	}

Number of line 5613 - 
Personal Slot right, 


	slot {name "slot_inv_7"		area 132 347 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.personal2"	}

	slot {name "slot_inv_7"		area 130 347 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.personal2"	}

Number of line 5612 - 
Personal Slot middle, 


	slot {name "slot_inv_6"		area 79 347 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.personal1"	}

	slot {name "slot_inv_6"		area 78 347 52 52	bam "STONSLOT"	slotinfo "characters[id].equipment.personal1"	}

NOTE: Dialoguebox modification is on the testing stage, I do not know what they actually do, I mean - what kind of fonts its changing. Dialogbox modifications is only aviable for "standard version", in the "mini version" is not such modifications. 

Number of line 11751 - 
Dialoguebox stuff main.


	text
	{
		name "worldMessageBox"
		area 28 135 816 102
		text lua "worldMessageBoxText"
		text style "CGuiMod"
		scrollbar	'GUISCRC'
		scrollbar func "chatboxScroll"
	}

	text
	{
		name "worldMessageBox"
		area 28 135 816 102
		text lua "worldMessageBoxText"
		text style "normal"
		scrollbar	'GUISCRC'
		scrollbar func "chatboxScroll"
	}

Number of line 11965 - 
Dialoguebox stuff


	text
	{
		name "worldNPCDialog"
		area 84 22 749 38
		text lua "worldNPCDialogText"
		text style "CGuiMod"
		scrollbar	'GUISCRC'
	}

	text
	{
		name "worldNPCDialog"
		area 84 22 749 38
		text lua "worldNPCDialogText"
		text style "normal"
		scrollbar	'GUISCRC'
	}

Number of line 11973 - 
Dialoguebox stuff. 


	text
	{
		name "worldDialogMessageBox"
		enabled "showWorldMessages"
		area 20 -124 813 124
		text lua "worldMessageBoxText"
		text style "CGuiMod"
		scrollbar	'GUISCRC'
		scrollbar func "chatboxScroll"
	}

	text
	{
		name "worldDialogMessageBox"
		enabled "showWorldMessages"
		area 20 -124 813 124
		text lua "worldMessageBoxText"
		text style "normal"
		scrollbar	'GUISCRC'
		scrollbar func "chatboxScroll"
	}

Number of line 12023 - 
Dialoguebox. 


			text
			{
				area 0 0 -1 -1
				text lua "getDialogEntryText(rowNumber)"
				text style "CGuiMod"
			}

			text
			{
				area 0 0 -1 -1
				text lua "getDialogEntryText(rowNumber)"
				text style "normal"
			}
	
=== SoD - UI.MENU, inventory field ===

First is the modified stuff, second is the default stuff, from up to down. 

NOTE: About the coordinate system and connected stuff, that game using, you can read in the "COMPABILITY" section for BG2:EE. Basically orign of coords. is in the top-left corner of the game-screen. 

Line 5413 - AC details, text main stats. Text color, and moving little bit right. Little bit resizing in width. etc

	text
	{
		enabled		"tempStats[id] == nil"
		area 598 55 246 95
		text lua "characters[id].AC.details"
		text style "CGuiMod"
		scrollbar 'GUISCRC'
	}
 
	text
	{
		enabled		"tempStats[id] == nil"
		area 594 57 246 97
		text lua "characters[id].AC.details"
		text style "normal"
		scrollbar 'GUISCRC'
	}

Line 5429 - Hit Points text stuff, main stats. Color, moving down and resizing for little bit. 

	text
	{
		enabled		"tempStats[id] == nil"
		area 598 162 244 102
		text lua "characters[id].HP.details"
		text style "CGuiMod"
		scrollbar 'GUISCRC'
	}

	text
	{
		enabled		"tempStats[id] == nil"
		area 598 160 244 104
		text lua "characters[id].HP.details"
		text style "normal"
		scrollbar 'GUISCRC'
	}

Line 5446 - Thaco text stuff main stats.  Color, moving down, and resize.

	text
	{
		enabled		"tempStats[id] == nil"
		area 598 276 244 104
		text lua "getInventoryTHAC0Details()"
		text style "CGuiMod"
		scrollbar 'GUISCRC'
	}

	text
	{
		enabled		"tempStats[id] == nil"
		area 598 272 244 106
		text lua "getInventoryTHAC0Details()"
		text style "normal"
		scrollbar 'GUISCRC'
	}
	
Line 5463 - Damage text stuff, main stats. Just a color. 

	text
	{
		enabled		"tempStats[id] == nil"
		area 598 386 244 98
		text lua "getInventoryDamageDetails()"
		text style "CGuiMod"
		scrollbar 'GUISCRC'
	}

	text
	{
		enabled		"tempStats[id] == nil"
		area 598 386 244 98
		text lua "getInventoryDamageDetails()"
		text style "normal"
		scrollbar 'GUISCRC'
	}

Line 5272 - Item name label, item-bonus panel. Color. 

	label
	{
		area		524 50 330 56
		text lua	"getStatsTitle()"
		text style	"label"
		text color 'Y'
	}

	label
	{
		area		524 50 330 56
		text lua	"getStatsTitle()"
		text style	"label"
		text color 'D'
	}

Line 5280 - "Current" label, item bonus menu. Color.  

	label
	{
		enabled		"tempStats[id] ~= nil"
		area		674 110 84 28
		text		"CURRENT_LABEL"
		text style	"label"
		text color 'Y'
		text point 10
	}

	label
	{
		enabled		"tempStats[id] ~= nil"
		area		674 110 84 28
		text		"CURRENT_LABEL"
		text style	"label"
		text color 'D'
		text point 10
	}

Line 5289 -  "New" label, item bonus menu. Color

	label
	{
		enabled		"tempStats[id] ~= nil"
		area		758 110 84 28
		text		"NEW_LABEL"
		text style	"label"
		text color 'Y'
		text point 10
	}
	
		label
	{
		enabled		"tempStats[id] ~= nil"
		area		758 110 84 28
		text		"NEW_LABEL"
		text style	"label"
		text color 'D'
		text point 10
	}

Line 5298 -  "Armor Class" label, item bonus menu. Color. 

	text
	{
		area		534 148 134 58
		text		"ARMOR_CLASS_LABEL"
		text style	"CGuiModl"
		enabled		"tempStats[id] ~= nil"
		tooltip lua "characters[id].AC.details"
		text align left center
	}

	text
	{
		area		534 148 134 58
		text		"ARMOR_CLASS_LABEL"
		text style	"label"
		enabled		"tempStats[id] ~= nil"
		tooltip lua "characters[id].AC.details"
		text align left center
	}

Line 5307 - Value of AC, without item, item bonus menu. Color. 

	label
	{
		area		674 143 84 63
		text lua	"getStat(characters[id].AC.current,'AC',-1)"
		text style	"CGuiModl"
		align center center
	}

	label
	{
		area		674 143 84 63
		text lua	"getStat(characters[id].AC.current,'AC',-1)"
		text style	"label"
		align center center
	}

Line 5323 - Hit points label, item bonus menu. Color 

	text
	{
		area		534 216 134 76
		text		"HIT_POINTS_LABEL"
		text style	"CGuiModl"
		enabled		"tempStats[id] ~= nil"
		tooltip lua "characters[id].HP.details"
		text align left center
	}

	text
	{
		area		534 216 134 76
		text		"HIT_POINTS_LABEL"
		text style	"label"
		enabled		"tempStats[id] ~= nil"
		tooltip lua "characters[id].HP.details"
		text align left center
	}

Line 5332 - HP without item, item bonus menu. Color

	label
	{
		area		674 216 84 71
		text lua	"characters[id].HP.current .. '/' .. getStat(characters[id].HP.max, 'HP', 1) "
		text style	"CGuiModl"
		align center center
	}

	label
	{
		area		674 216 84 71
		text lua	"characters[id].HP.current .. '/' .. getStat(characters[id].HP.max, 'HP', 1) "
		text style	"label"
		align center center
	}

Line 5348 - Thaco lable, item bonus menu. Color. 

	text
	{
		area		534 290 134 74
		text		"THAC0_LABEL"
		text style	"CGuiModl"
		enabled		"tempStats[id] ~= nil"
		tooltip lua "characters[id].THAC0.details"
		text align left center
	}	

	text
	{
		area		534 290 134 74
		text		"THAC0_LABEL"
		text style	"label"
		enabled		"tempStats[id] ~= nil"
		tooltip lua "characters[id].THAC0.details"
		text align left center
	}	

Line 5357 - Thaco without item, item bonus menu. Color. 

	label
	{
		area		674 290 84 77
		text lua	"getStat(characters[id].THAC0.current,'THAC0', -1)"
		text style	"CGuiModl"
		align center center
	}

	label
	{
		area		674 290 84 77
		text lua	"getStat(characters[id].THAC0.current,'THAC0', -1)"
		text style	"label"
		align center center
	}

Line 5373 - Damage label, item bonus menu. Color

	text
	{
		area		534 367 134 70
		text		"DAMAGE_LABEL"
		text style	"CGuiModl"
		enabled		"tempStats[id] ~= nil"
		tooltip lua "characters[id].damage.details"
		text align left center
	}	

	text
	{
		area		534 367 134 70
		text		"DAMAGE_LABEL"
		text style	"label"
		enabled		"tempStats[id] ~= nil"
		tooltip lua "characters[id].damage.details"
		text align left center
	}	

Line 5382 - Damage without item, item bonus menu. Color

	label
	{
		area		674 367 84 70
		text lua	"getStat(characters[id].damage.min,'dmgMin',1) .. ' - ' .. getStat(characters[id].damage.max, 'dmgMax', 1)"
		text style	"CGuiModl"
		align center center
	}

	label
	{
		area		674 367 84 70
		text lua	"getStat(characters[id].damage.min,'dmgMin',1) .. ' - ' .. getStat(characters[id].damage.max, 'dmgMax', 1)"
		text style	"label"
		align center center
	}

=== SoD - UI.MENU, Charrec field ===

Line 794 - Information field. Moving up and increasing heigh, text color. 

	text
	{
		enabled		"showJustText"
		area		92 202 342 428
		text		lua "helpTextString"
		text style  'CGuiMod'
		text align	left top
		scrollbar	'GUISCRC'
	}

	text
	{
		enabled		"showJustText"
		area		92 208 342 412
		text		lua "helpTextString"
		text style  'normal'
		text align	left top
		scrollbar	'GUISCRC'
	}
	
Line 640 - Class field. Same modification as previous one.

	text
	{
		enabled		"showClassInfo"
		area		92 202 342 428
		text		lua "getClassString()"
		text style  'CGuiMod'
		scrollbar	'GUISCRC'
	}


	text
	{
		enabled		"showClassInfo"
		area		92 208 342 412
		text		lua "getClassString()"
		text style  'normal'
		scrollbar	'GUISCRC'
	}

Line 651 - Abilities stuff. Resizing as previous.

	list
	{		
		column 
		{ 
			width 100
			label
			{
				area		0 0 -1 -1
				text		lua "listItems[rowNumber][2]" 
				text style  'CGuiMod'
				text align	left center

			}
		}

		area 92 202 342 428
		
		enabled		"showAbilityBonuses"
		rowheight	45
		table		"listItems"
		var			currentItem
		scrollbar	'GUISCRC'		
		hidehighlight
		action
		"
			--helpTextString = Infinity_FetchString( listItems[currentItem][1].helpStrRef)
		"		
	}


	list
	{		
		column 
		{ 
			width 100
			label
			{
				area		0 0 -1 -1
				text		lua "listItems[rowNumber][2]" 
				text style  'normal'
				text align	left center

			}
		}

		area 92 208 342 418
		
		enabled		"showAbilityBonuses"
		rowheight	45
		table		"listItems"
		var			currentItem
		scrollbar	'GUISCRC'		
		hidehighlight
		action
		"
			--helpTextString = Infinity_FetchString( listItems[currentItem][1].helpStrRef)
		"		
	}

Line 681 - Stats screend stuff. Only colors. ("text style" field : "normal" => "CGuiMod", "label" => "CGuiModl")

	list
	{		
		column 
		{ 
			width 65
			label
			{
				area		0 0 -1 -1
				text		lua "Infinity_FetchString(otherlist[rowNumber][1])" 
				text style  'CGuiMod'
				text align	left center

			}
		}
		column 
		{ 
			width 35
			label
			{
				area		0 0 -1 -1
				text		lua " otherlist[rowNumber][2]"				
				text style  'CGuiMod'
				text align	center center
			}
		}

		area 92 204 346 186
		
		enabled		"showStats"
		rowheight	45
		table		"otherlist"
		var			currentItem
		scrollbar	'GUISCRC'		
		hidehighlight
		action
		"
			--helpTextString = Infinity_FetchString( listItems[currentItem][1].helpStrRef)
		"		
	}

	label
	{
		enabled		"showStats"
		area		370 402 64 28
		text		"GAME_LABEL"
		text style  'CGuiModl'
		text align	center center
	}
	label
	{
		enabled		"showStats"
		area		300 402 70 28
		text		"CHAPTER_LABEL"
		text style  'CGuiModl'
		text align	center center
	}

	list
	{		
		column 
		{ 
			width 65
			label
			{
				area		0 0 -1 -1
				text		lua "Infinity_FetchString(listItems[rowNumber][1])"  --lua " '^M' .. Infinity_FetchString(listItems[rowNumber][1]) .. '^-' .. '\n'  .. trunc(Infinity_FetchString( listItems[rowNumber][3]), 140)"
				text style  'CGuiMod'
				text align	left center

			}
		}
		column 
		{ 
			width 20
			label
			{
				area		0 0 -1 -1
				text		lua " listItems[rowNumber][2]"				
				text style  'CGuiMod'
				text align	center center
				
			}
		}
		column 
		{ 
			width 15
			label
			{
				area		0 0 -1 -1
				text		lua " listItems[rowNumber][3]"				
				text style  'CGuiMod'
				text align	center center
				
			}
		}

		area 92 430 350 196
		
		enabled		"showStats"
		rowheight	45
		table		"listItems"
		var			currentItem
		scrollbar	'GUISCRC'		
		hidehighlight
		action
		"
			--helpTextString = Infinity_FetchString( listItems[currentItem][1].helpStrRef)
		"		
	}

Line 543 - Attributes stuff, only colors. ("text style" field : "normal" => "CGuiMod", "label" => "CGuiModl")

	list
	{
		column 
		{ 
			width 65
			label
			{
				area		0 0 -1 36 
				text		lua "Infinity_FetchString( attributeItems[rowNumber][1].strRef)"
				text style  'CGuiMod'
				text align	left center
			}
		}
		column 
		{ 
			width 35
			label
			{
				area		0 0 -1 36 
				text		lua  "displayAttr(rowNumber)" --"listItems[rowNumber][1].current"
				text style  'CGuiModl'
				text align right center
				text shadow lua "isStatModified(rowNumber)"
				
			}
		}

		area 456 162 162 218
		
		rowheight	36
		table		"attributeItems"
		var			currentItem
		hidehighlight
		action
		"
			helpTextString = Infinity_FetchString( attributeItems[currentItem][2])
		"		
	}

Line 629 - Character description stuff. 

	label
	{
		area 644 512 194 92
		text lua "characterDescString(characters[currentID])"
		text style 'CGuiMod'
		text align center center
		
	}

	label
	{
		area 644 512 194 92
		text lua "characterDescString(characters[currentID])"
		text style 'normal'
		text align center center
		
	}

=== SoD - UI.MENU, Message box stuff (only in standard version) ===

NOTE: I do not know, how my modification taking effect in game. in this case. 

Line 11746 - Something connected to Message Box

	text
	{
		name "worldMessageBox"
		area 28 66 816 171
		text lua "worldMessageBoxText"
		text style "CGuiModlg"
		scrollbar	'GUISCRC'
		scrollbar func "chatboxScroll"
	}

	text
	{
		name "worldMessageBox"
		area 28 66 816 171
		text lua "worldMessageBoxText"
		text style "gamelog"
		scrollbar	'GUISCRC'
		scrollbar func "chatboxScroll"
	}

Line 11960 - Perhaps dialogues with npc text???

	text
	{
		name "worldNPCDialog"
		area 86 -25 758 111
		text lua "worldNPCDialogText"
		text style "CGuiModlg"
		scrollbar	'GUISCRC'
	}

	text
	{
		name "worldNPCDialog"
		area 86 -25 758 111
		text lua "worldNPCDialogText"
		text style "gamelog"
		scrollbar	'GUISCRC'
	}
 
Line 11969 - Do not know what is that

	text
	{
		name "worldDialogMessageBox"
		enabled "showWorldMessages"
		area 20 -175 824 124
		text lua "worldMessageBoxText"
		text style "CGuiModlg"
		scrollbar	'GUISCRC'
		scrollbar func "chatboxScroll"
	}

	text
	{
		name "worldDialogMessageBox"
		enabled "showWorldMessages"
		area 20 -175 824 124
		text lua "worldMessageBoxText"
		text style "gamelog"
		scrollbar	'GUISCRC'
		scrollbar func "chatboxScroll"
	}

Line 12007 - I do not know what is that. perhaps connected to dialogue stuff. "text style" : "gamelog" => "CGuiModlg"

	list
	{
		column
		{
			width 100
			label
			{
				area 0 0 -1 -1
				enabled "dialogEntryGreyed()"
				rectangle 1
				rectangle opacity 100
			}
			text
			{
				area 0 0 -1 -1
				text lua "getDialogEntryText(rowNumber)"
				text style "CGuiModlg"
			}
		}
		name "worldPlayerDialogChoicesList"
		area 86 86 758 151
		rowheight dynamic
		hideHighlight
		table "worldPlayerDialogChoices"
		var "worldPlayerDialogSelection"
		scrollbar	'GUISCRC'
		actionEnter
		"
			if(gameOptions.m_bConfirmDialog == true) then return end
			glowTest = mouseoverRow
			worldPlayerDialogSelection = mouseoverRow
		"
		actionExit
		"
			if(gameOptions.m_bConfirmDialog == true) then return end
			glowTest = nil
			worldPlayerDialogSelection = 0
		"
		action
		"
			--In confirm mode, just highlight the choice.
			if(gameOptions.m_bConfirmDialog == true) then return end
			worldScreen:OnDialogReplyClick(worldPlayerDialogChoices[worldPlayerDialogSelection].marker)
			worldPlayerDialogSelection = 0
		"
	}

--------------- USED PROGRAMS ---------------

NotePad++ - https://notepad-plus-plus.org

WeiDU - https://github.com/WeiDUorg/weidu

NearInfinity - https://github.com/Argent77/NearInfinity/releases

GIMP - https://www.gimp.org/

ImageMagick - www.imagemagick.org (i.e. %pugrify [optins] *.PNG)

Blender - https://www.blender.org

Free Hex Editor Neo - http://www.hhdsoftware.com/free-hex-editor

Lunix tools such as : mv, mkdir, rename, ls, ImageMagick, and others.  

--------------- THNAKS TO ---------------

G3 community - gibberlinds3.net/forums , and especially to Jarno Mikkola, argent77, lynx, agb1, Fiann of the Silver Hand,

Beamdog Forums - forums.beamdog.com , to user lefreut for exposing the dialogue-box background image data file. 

Deviant Art - deviantart.com , there I have found many muse-inspiring-pictures for the mod ^^ . 

--------------- VERSIONS HISTORY ---------------

v 0,3 - Fixed bug, UI.MENU -- line 602: text style "normal" ---> text style "CGuiMod", there was Charrec panel, resistence, effects, etc field.

v 0,2beta - tested on BG2:EE v 2.3672, updated README file, the single program divided into two version. 1) Standard , 2) mini (without modifications to dialogue-box), 4shared data-host service changed to GitHub. 
Added mod for Siege of Dragonspear, and tested on BG:EE + SoD DLC v 2.3673

v 0,2alpha - adaptation for BG2:EE v2+, deleted contrast BAM for spells, and Spell Description. 

v 0,1alpha - initial release without transparency of the dialogue boxes ;./ for BG2:EE v1.3.2

--------------- LICENSE ---------------

You can freely modify and redistribute the any parts of this mod, but try to do not forget scribe about the initial author in your credits or something like that :P . 




										frostysh , 2017 year AD. 
