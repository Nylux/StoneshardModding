# NeoConsole

:octicons-tag-24: **0.8.1.9**

!!! Info "Important - Modders Please Read"
    Please **^^do not share^^** NeoConsole with end users.

    Do not **make it into a mod** and do not **distribute** it.  
    Be careful not to **leave it in a mod you're working on** either.

    For now please use it as a **convenient tool** to help you **create and test mods** and nothing more.

    When it's **stable enough** and has achieved **feature parity** with the **original console**, we can **release it** for end users to do whatever they want with it.

    ---

    Part of this code was taken from [Gamerev Games :material-youtube:](https://www.youtube.com/@GamerevGames)  videos.  
    **This project wouldn't be a thing without him**, so go check him out !

## Description

NeoConsole is an **ongoing project** that is attempting to create a new **developer console** from scratch.

The project is still at an **early stage**, and the current goal is to get a **working console up and running** without having to alter the game's behaviour in any way.

The current state of **NeoConsole** is a **working console** with a **multitude of scripts** as well as **various issues**.  
We are still **missing features** the **original developer console** had, but we're **getting there**.

---

##  Setup

**Setting up NeoConsole** takes anywhere from **5 to 20 minutes** for someone **familiar** with **UMT**.

While this isn't a particularly long time, be aware that a **single small mistake** can force you to **restart**, losing **several minutes**.  
In the long run, I'd like to introduce a **UMT script** to do all this delicate work for you, but for now, **read thoroughly**.

---

### **Scripts (Commands)**

???+ Warning
    Due to **limitations with UMT**, currently, **^^creating the scripts before anything that may call them is critically important^^**.  
    As such, it's **strongly recommended** to **^^import every single script FIRST^^**, and **only then** implementing the **scripts** or **gameobjects** that **call them**.

    If you don't, and for example you create the `o_neoconsole` Step Event **BEFORE** creating the `scr_neoconsole_log` script, **UMT will be confused** and wi**ll not find it**, which will **^^prevent the game from starting^^**.

??? abstract "Importing the scripts"
    Importing the scripts is pretty straightforward :

    - Download the **.zip file** below.
    - **Extract** it anywhere.
    - Use the `Scripts > Resources Repackers > ImportGML.csx` script in UMT for **^^each of the folders^^**.
    - Make sure to import them **in order** (Core, Required, Base, Post) or else you will **run into issues**.

    ---

    [NeoConsoleScripts.zip :octicons-download-16:](../downloads/NeoConsoleScripts.zip){ .md-button .md-button--primary}&emsp;:octicons-tag-24: **Version 9.3 - [11/6/2023]**


??? Info "Reminder - commandsMap"
    If you added any **non-standard script**, make sure to also add them to the **commandsMap** in `scr_neoconsole_init` !  
    Otherwise, they won't be **accessible** through the console.

    It may also be a good idea to add an entry to the **help command** there to indicate **how to use it** !

---

### **Core Console**

??? abstract "1. Adding `o_neoconsole`"
    - Create a new **gameobject** and change its name to `o_neoconsole`.
    - When **prompted**, make sure to click on the `Change all occurences of this value` **button**.
    - Finally, make sure to click on the `Persistent` **checkbox** to **enable** it.

??? abstract "2. Registering in `sessionDataInit`"
    Find `gml_GlobalScript_scr_sessionDataInit` in UMT and add the following **highlighted code** to it :
    ??? note "Code"
        ```py linenums="1" hl_lines="42 43" title="gml_GlobalScript_scr_sessionDataInit"
        function scr_sessionDataInit() //gml_Script_scr_sessionDataInit
        {
            global.loadGameLocationProcess = 0
            global.open_spells = 0
            global.open_weapon_skills = 0
            global.localX = 0
            global.localY = 0
            global.HP = -1
            global.MP = -1
            global.floor_counter = 0
            global.failDungeonSeed = 0
            global.enemyChasePattern = "horizontal"
            global.turns = -1
            global.contrattack = 0
            global.music_position_map = 0
            ds_list_clear(global.agred_enemy_list)
            ds_map_clear(global.duplicatedRoomMap)
            global.glmapPanelsVisible = 1
            global.glmapLegendVisible = 1
            global.glmapScale = 1
            global.glmapGridX = -4
            global.glmapGridY = -4
            global.glmapUserMarkX = -4
            global.glmapUserMarkY = -4
            global.backfire_cd = 0
            global.achRightBackatYou = 0
            global.achFetchThis = 0
            scr_locationPositionInit()
            scr_characterMenuInit()
            if (!global.is_load_game)
                scr_init_quests()
            audio_sound_gain(snd_skill_staticfield_hit, 0, 2000)
            if (!instance_exists(o_console_controller))
                instance_create_depth(0, 0, 0, o_console_controller)
            if (!instance_exists(o_actionsLog))
                instance_create_depth(0, 0, 0, o_actionsLog)
            if (!instance_exists(o_music_controller))
            {
                with (instance_create_depth(0, 0, 0, o_music_controller))
                    stop_music = 1
            }
            if (!instance_exists(o_neoconsole))  
                   instance_create_depth(0, 0, 0, o_neoconsole)
        }
        ```

    ??? Info "Explanations"
        - The code we're adding in `sessionDataInit` creates the `o_neoconsole` **gameobject** if it doesn't exist already.
        - It's run when a **save is loaded** or when a **new game is started** by the player.
        - This is the **only way** the **console** is **spawned** into the world.

??? abstract "3. Register in `persistentRoomController`"
    Find `gml_Object_persistentRoomController_Other_11` in UMT and add the following **highlighted code** to it :
    ??? note "Code"
        ```py linenums="1" hl_lines="20" title="gml_Object_persistentRoomController_Other_11"
        var _drawLoading = gameState == 2
        var _loadingImageIndex = 0
        with (o_black_overlay)
            _loadingImageIndex = loading.image_index
        ds_list_clear(persistentDuplicatedRoomList)
        audio_stop_all()
        with (o_player)
        {
            create_corpse = 0
            instance_destroy()
        }
        with (o_unit)
            persistent = 0
        scr_guiChildrenDestroy(global.guiBaseVisibleContainer)
        scr_guiChildrenDestroy(global.guiBaseHiddenContainer)
        scr_escapeButtonListClear()
        instance_destroy(o_fullscreen_effects)
        instance_destroy(o_shader_start)
        instance_destroy(o_console_controller)
        instance_destroy(o_neoconsole)
        instance_destroy(o_actionsLog)
        instance_destroy(o_music_controller)
        instance_destroy(o_NPC, false)
        if (!((0 || global.playerGridX == -4)))
            scr_glmap_destroyGrid()
        scr_waterSpritesCacheClear()
        __dsDebuggerMapDestroy(global.saveDataMap)
        with (scr_smoothRoomChange(-4, gameState, 10, _drawLoading))
        {
            with (blackOverlay)
            {
                image_alpha = 1
                loading.image_index = _loadingImageIndex
                loading.image_alpha = image_alpha
            }
            event_perform(ev_alarm, 0)
        }
        ```
    ??? Info "Explanations"
        - This code **destroys** the **console** when run.
        - It's mainly **called** when **going back** to the **main menu**.


??? abstract "4. Registering in `dataLoader`"
    Find `gml_Object_o_dataLoader_Other_10` in UMT and add the following **highlighted code** to it :
    ??? note "Code"
        ```py linenums="1" hl_lines="8" title="gml_Object_o_dataLoader_Other_10"
        global.bodypart = "random"
        global.campPresset = -4
        global.dungeon_controller = -4
        global.Upspeed = 0
        global.TurnDelay = 13
        global.globalMapInit = 0
        global.consoleEnabled = 0
        global.neoconsole_enabled = 0
        scr_slotsInit()
        scr_ds_init()
        scr_colorTextColorsMap(1)
        scr_skill_tier_init()
        scr_dayNightInit()
        scr_waterSpritesCacheInit()
        global.settingsMenuTab = 4394
        global.settingsMenuRecreate = 0
        global.saveErrorText = "N/A"
        global.skipTimeHours = -4
        global.skipTimeHungerChange = 0
        global.terrainGrid = -4
        global.fog = 1
        global.skill_can_cast = 1
        global.prologueTransition = 0
        global.permadeathMode = 0
        global.mainMenuRoom = 6
        global.credits_music = -4
        global.classesMap = __dsDebuggerMapCreate()
        scr_classCreate(o_verren, s_verren, "Verren", "Male", "HumanAldor", "RelicSeeker", 10, 10, 10, 10, 10, [global.pyromancy_tier1, global.pyromancy_tier2, global.geomancy_tier1, global.geomancy_tier2, global.electromancy_tier1, global.electromancy_tier2, global.swords_tier1, global.swords_tier2, global.maces_tier1, global.maces_tier2, global.daggers_tier1, global.daggers_tier2, global.swords2h_tier1, global.swords2h_tier2, global.shields_tier1, global.shields_tier2, global.staves_tier1, global.staves_tier2, global.bows_tier1, global.bows_tier2, global.axes_tier1, global.axes_tier2, global.combat_tier1, global.combat_tier2, global.athletics_tier1, global.athletics_tier2, global.polearms_tier1, global.polearms_tier2, global.dualwield_tier1, global.dualwield_tier2, global.greataxes_tier1, global.greataxes_tier2, global.greatmaces_tier1, global.greatmaces_tier2, global.armor_tier1, global.armor_tier2], [4335])
        scr_classCreate(o_revenger, s_Velmir, "Velmir", "Male", "HumanSkadia", "Revenger", 11, 11, 11, 10, 10, [global.polearms_tier1, global.greataxes_tier1, global.greatmaces_tier1, global.bows_tier1, global.athletics_tier1, global.combat_tier1], [4337])
        scr_classCreate(o_reaver, s_Jorgrim, "Jorgrim", "Male", "Dwarf", "Reaver", 11, 10, 11, 11, 10, [global.swords_tier1, global.axes_tier1, global.maces_tier1, global.greataxes_tier1, global.dualwield_tier1, global.combat_tier1], [4330])
        scr_classCreate(o_knight_maiden, s_ArnaDerVyrne, "Arna", "Female", "HumanAldor", "KnightMaiden", 11, 11, 10, 11, 10, [global.swords_tier1, global.swords2h_tier1, global.greatmaces_tier1, global.shields_tier1, global.armor_tier1, global.combat_tier1], [4331])
        scr_classCreate(o_woodward, s_Dirwin, "Dirwin", "Male", "HumanAldor", "Woodward", 10, 11, 11, 11, 10, [global.daggers_tier1, global.axes_tier1, global.greataxes_tier1, global.staves_tier1, global.bows_tier1, global.athletics_tier1], [4332])
        scr_classCreate(o_runaway_wizzard, s_Jonna, "Jonna", "Female", "HumanAldor", "RunawaySorceress", 10, 10, 11, 11, 11, [global.staves_tier1, global.pyromancy_tier1, global.geomancy_tier1, global.electromancy_tier1, global.magic_mastery_tier1, global.athletics_tier1], [4333])
        global.player_class = -4
        global.Osbrook = [4, 4]
        global.OsbrookTavernSleepIsOpen = 0
        global.is_load_game = 0
        global.is_devinfo = 0
        global.spriteOriginEditor = 0
        global.npc_animation_mode = 0
        global.skill_test = 0
        global.sightPlacelistEditor = 0
        global.devCamera = 0
        global.devCameraSpeed = 2
        global.is_teleporting = 0
        global.is_nocd = 0
        global.gridInfo = 0
        global.gridPosInfo = 0
        global.weatherInfo = 0
        global.fadeInfo = 0
        global.HP = -1
        global.MP = -1
        global.audiodebug = 0
        global.enemyinfo = 0
        global.RecivedDamage = 0
        global.AllDamage = 0
        global.position_tag = "NA"
        global.presset_map = __dsDebuggerMapCreate()
        global.timeScale = 1
        global.attack_mode_on = 0
        global.skill_select = 0
        global.skill_activate = 0
        global.transition_done = 0
        global.transition_scale = 1
        global.globalmaptest = 0
        global.playerGodMode = 0
        global.playerNoDeathMode = 0
        global.playerNoPain = 0
        global.in_steam = 1
        global.steam_api = 1
        global.steem_screenshot_counter = 0
        global.read_diary[2] = 0
        global.read_diary[3] = 0
        global.read_diary[4] = 0
        global.read_diary[5] = 0
        global.read_diary[6] = 0
        global.bad_luck[0] = 0
        global.bad_luck[1] = 0
        global.bad_luck[2] = 0
        global.bad_luck[3] = 0
        global.bad_luck[4] = 0
        global.bad_luck[5] = 0
        global.bad_luck[6] = 0
        global.bad_luck[7] = 0
        global.magalomania_value = 0
        global.target = -4
        global.checkpoint = room
        global.cryptchance = 0
        global.localX = 0
        global.localY = 0
        global.UI_is_on = 1
        global.checkpoint = 5
        global.inv_select = 0
        global.scrollbar_drag = 0
        global.gen_wall = __dsDebuggerListCreate()
        global.roompoint = 0
        audio_falloff_set_model(4)
        global.hunger_count = 0
        global.thirsty_count = 0
        global.GFX = 0
        if shaders_are_supported()
        {
            if shader_is_compiled(sh_whiteblend)
                global.GFX = 1
        }
        global.miniboss_type = scr_tableLoad(gml_Script_table_Miniboss_type)
        init_damage_material_constatns()
        global.inst_snd = -4
        global.choir_snd = -4
        global.crypts = __dsDebuggerListCreate()
        global.agred_enemy_list = __dsDebuggerListCreate()
        global.main_part = part_system_create()
        global.dustpart = part_type_create()
        global.whitepart = part_type_create()
        part_type_sprite(global.whitepart, 1607, 0, 1, 1)
        part_type_size(global.whitepart, 0.5, 1, 0.05, 0)
        part_type_scale(global.whitepart, 1, 1)
        part_type_orientation(global.whitepart, 0, 77, 0, 0, 0)
        part_type_color3(global.whitepart, 6911105, 4212565, 4010044)
        part_type_alpha3(global.whitepart, 0.62, 0.36, 0)
        part_type_blend(global.whitepart, 0)
        part_type_life(global.whitepart, 10, 25)
        part_type_speed(global.whitepart, 1, 1, 0, 1)
        part_type_direction(global.whitepart, -46, 143, 0, 0)
        part_type_gravity(global.whitepart, 0, 0)
        part_type_sprite(global.dustpart, 1616, 0, 1, 1)
        part_type_size(global.dustpart, 1, 1, 0, 0)
        part_type_alpha3(global.dustpart, 0, 0.5, 0)
        part_type_speed(global.dustpart, 0.1, 0.5, 0, 0)
        part_type_gravity(global.dustpart, 0, 0)
        part_type_direction(global.dustpart, 0, 359, 0, 0)
        part_type_orientation(global.dustpart, 0, 0, 0, 0, 0)
        part_type_colour1(global.dustpart, make_colour_rgb(255, 235, 172))
        part_type_life(global.dustpart, 40, 100)
        part_system_depth(global.main_part, -3000)
        global.pt_steam = part_type_create()
        part_type_shape(global.pt_steam, 0)
        part_type_sprite(global.pt_steam, 1632, 1, 0, 0)
        part_type_size(global.pt_steam, 1, 1, 0.15, 0)
        part_type_scale(global.pt_steam, 0.08, 0.08)
        part_type_orientation(global.pt_steam, 0, 0, 0, 0, 0)
        part_type_color3(global.pt_steam, 14868188, 16777215, 16777215)
        part_type_alpha3(global.pt_steam, 0.41, 0, 0)
        part_type_blend(global.pt_steam, 0)
        part_type_life(global.pt_steam, 25, 40)
        part_type_speed(global.pt_steam, 0.2, 1, 0, 0)
        part_type_direction(global.pt_steam, 149, 184, 0, 0)
        part_type_gravity(global.pt_steam, 0, 0)
        global.campsmoke = part_system_create()
        part_system_depth(global.campsmoke, -3000)
        global.pt_CampfireSmoke = part_type_create()
        part_type_shape(global.pt_CampfireSmoke, 10)
        part_type_sprite(global.pt_CampfireSmoke, 1633, 0, 0, 0)
        part_type_size(global.pt_CampfireSmoke, 0.01, 0.3, 0.01, 0)
        part_type_scale(global.pt_CampfireSmoke, 1, 1)
        part_type_orientation(global.pt_CampfireSmoke, 90, 107, 0, 0, 0)
        part_type_color3(global.pt_CampfireSmoke, 5863078, 6716795, 5592405)
        part_type_alpha3(global.pt_CampfireSmoke, 0.78, 0.21, 0)
        part_type_blend(global.pt_CampfireSmoke, 0)
        part_type_life(global.pt_CampfireSmoke, 80, 80)
        part_type_speed(global.pt_CampfireSmoke, 0.03, 1, 0, 0)
        part_type_direction(global.pt_CampfireSmoke, 100, 100, 0, 0)
        part_type_gravity(global.pt_CampfireSmoke, 0.04, 125)
        global.smokeParticleSystem = part_system_create()
        part_system_depth(global.smokeParticleSystem, -3000)
        global.smokeParticle = part_type_create()
        part_type_sprite(global.smokeParticle, 1642, 0, 0, 1)
        part_type_orientation(global.smokeParticle, 0, 0, 0.15, 0, 0)
        part_type_alpha3(global.smokeParticle, 0, 0.3, 0)
        part_type_blend(global.smokeParticle, 0)
        part_type_life(global.smokeParticle, room_speed, (room_speed * 4))
        part_type_speed(global.smokeParticle, 0, 0, 0, 0)
        part_type_direction(global.smokeParticle, 0, 360, 0, 0)
        part_type_gravity(global.smokeParticle, 0, 0)
        instance_destroy()
        ```
    ??? Info "Explanations"
        - This code **initializes** the **console's global variables** when run.
        - It's called when you load **load the game**.

??? abstract "5. Adding Create Event in `o_neoconsole`"
    Add a `Create` **event** for `o_neoconsole` and add the following **code** to it :
    ??? note "Code"
        ```py linenums="1" title="o_neoconsole - Create Event"
        global.neoconsole_enabled = 0 #(1)!
        global.neoconsole_toggle_key = vk_f2 #(2)!
        text_ = ""
        text_def = ">. " #(3)!
        text_[0] = ""
        text_currentline = text_def #(4)!
        erase = -1
        lastcommand = ""
        cursor = "|" #(5)!
        cursor_blink_delay = 15 #(6)!
        alarm[0] = cursor_blink_delay
        font = f_dmg_eu #(7)!
        hsize = window_get_width() #(8)!
        vsize = window_get_height() #(9)!
        text_background_color = c_black #(10)!
        text_background_alpha = 0.6 #(11)!
        text_primary_color = c_white #(12)!
        text_primary_alpha = 0.9 #(13)!
        text_line_color = c_white #(14)!
        text_line_alpha = 0.6 #(15)!
        text_line_background = c_black #(16)!
        commandsMap = ds_map_create()
        helpSyntaxMap = ds_map_create()
        helpUsageMap = ds_map_create()
        scr_neoconsole_init() #(17)!
        scr_neoconsole_log("NeoConsole : " + string(ds_map_size(commandsMap)) + " scripts loaded.")
        scr_neoconsole_log("NeoConsole : " + string(ds_map_size(helpUsageMap)) + " helps loaded.")
        scr_neoconsole_log("NeoConsole : Made with a lot of pain by Nylux")
        ```

        1. This global variable defines whether the console is currently opened or not.
        2. Defines the key that needs to be pressed to toggle the console on or off.</br>See [this page](https://manual.yoyogames.com/GameMaker_Language/GML_Reference/Game_Input/Keyboard_Input/Keyboard_Input.htm) for other valid keys.
        3. Defines the prompt for your console, the characters that are shown before you type in it.
        4. **text_currentline** holds the characters you're typing in the console.
        5. Cursor starting position.
        6. Delay in frames before your cursor blinks.
        7. Name of the **font asset** to use in your console.</br>This one is included in Stoneshard by default.
        8. Width of your console window.
        9. Height of your console window.
        10. Background color of your console window.
        11. Opacity (alpha) of your console window's background.
        12. Text color in your console. See [this page](https://manual.yoyogames.com/GameMaker_Language/GML_Reference/Drawing/Colour_And_Alpha/Colour_And_Alpha.htm) for more.
        13. Text opacity in your console.
        14. Text color in your input line.
        15. Opacity of your input line's background.
        16. Background color of your input line.
        17. Function that contains the shortname for all the commands as well as their documentation for the help command.

    ??? Info "Explanations"
        This documentation uses **annotations** to provide **line per line descriptions**.  
        Make sure you **read them** to know what each variable does !

        ---

        Feel free to **modify** some of these **values** !  
        They're mostly used for **styling** so you should be fine.
        
??? abstract "6. Adding Destroy Event in `o_neoconsole`"
    Add a `Destroy` **event** for `o_neoconsole` and add the following **code** to it :
    ```py linenums="1" title="o_neoconsole - Destroy Event"
    ds_map_destroy(commandsMap) #(1)!
    commandsMap = -1
    ds_map_destroy(helpSyntaxMap) #(3)!
    helpSyntax = -1
    ds_map_destroy(helpUsageMap) #(4)!
    helpUsageMap = -1
    global.neoconsole_enabled = 0 #(2)!
    ```

    1. Destroys the ds_map holding the shortnames for scripts since we don't need it if the console is destroyed.
    2. Disabling the global variable as the console can't be opened if it's destroyed.
    3. Destroys the ds_map holding the syntax help for scripts since we don't need it if the console is destroyed.
    4. Destroys the ds_map holding the usage help for scripts since we don't need it if the console is destroyed.

??? abstract "7. Adding Alarm 0 Event in `o_neoconsole`"
    Add a `Alarm 0` **event** for `o_neoconsole` and add the following **code** to it :

    ```py linenums="1" title="o_neoconsole - Alarm 0 Event"
    if (cursor == "|")
	    cursor = ""

    else
    	cursor = "|"

    alarm[0] = cursor_blink_delay #(1)!
    ```

    1. Calls this code again after the amount of frames defined in `cursor_blink_delay`.

    ??? Info "Explanations"
        This is the code responsible for **blinking** the console's cursor.  
        If you want to **change** what your cursor **looks like**, this is the place to do it.

---

### **Logic & Rendering**

??? abstract "1. Adding Step Event in `o_neoconsole`"
    Add a `Step` **event** for `o_neoconsole` and add the following **code** to it :
    
    ??? note "Code"
        ```py linenums="1" title="o_neoconsole - Step Event"
        if (keyboard_check_pressed(global.neoconsole_toggle_key)) #(1)!
	        scr_neoconsole_enable()
    
        if global.neoconsole_enabled = false #(2)!
        	exit

        if (keyboard_check(vk_backspace) && (string_length(text_currentline) > string_length(text_def))) #(3)!
        {
        	if (erase >= 2) #(4)!
        	{
        		text_currentline = string_copy(text_currentline, 1, string_length(text_currentline)-1)
        		erase = 0
        	}
        	else
        		erase++
        }
        if keyboard_check(vk_up) #(12)!
            text_currentline = lastcommand

        var command = ""
        var arg
        arg[0] = ""
        var argCount = 0

        if (keyboard_check_released(vk_enter) && string_length(text_currentline) > string_length(text_def)) #(5)!
        {
            lastcommand = text_currentline
        	text_currentline = text_currentline + " " #(6)!
        	var word = ""

        	for(var i = string_length(text_def); i < string_length(text_currentline); i++)
        	{
        		var next_char = string_char_at(text_currentline, i+1)
        		if (next_char != " ")
        			word += next_char
        		else
        		{
        			if (command == "")  
        	        {  
        	            if ds_map_exists(commandsMap, word)  #(7)!
        	            {  
        	                command = string(ds_map_find_value(commandsMap, word))  
        	                word = ""   
        	            }  
        	            else  #(8)!
        	            {  
        	                scr_neoconsole_log(text_currentline)  
        	                scr_neoconsole_log("Unknown command.")  
        	                command = ""  
        	                word = ""  
        	                break  
        	            }  
        	        }
        			else
        			{
        				arg[argCount] = word
        				argCount++
        				word = ""
        			}
        		}
        	}

        	if (script_exists(asset_get_index(command))) #(9)!
        	{
        		scr_neoconsole_log(text_currentline)
        		script_execute_ext(asset_get_index(command), arg)
        	}
        }

        if (keyboard_lastkey != -1)
        {
        	switch(keyboard_lastkey) #(10)!
        	{
        		case vk_shift:
        		case vk_lshift:
        		case vk_rshift:
        		case vk_control:
        		case vk_lcontrol:
        		case vk_rcontrol:
        		case vk_alt:  
                case vk_lalt:  
                case vk_ralt:
        		case vk_up:
        		case vk_down:
        		case vk_left:
        		case vk_right:
        		case vk_enter:
        		case global.neoconsole_toggle_key:
        		case vk_backspace:
        			keyboard_lastkey = -1
        			keyboard_lastchar = -1
        			exit
        		break
        	}
        	text_currentline += keyboard_lastchar #(11)!
        	keyboard_lastkey = -1
        }
        ```

        1. This block is responsible for toggling the console on or off when the key defined in the Create Event is pressed.
        2. If the console is not opened, we stop here.
        3. This block is responsible for erasing characters when ++backspace++ is pressed.
        4. Here `2` is the cooldown in frames between each character being erased. Should probably be its own variable in Create Event.
        5. This block is responsible for parsing user input when the ++return++ key is pressed.
        6. Necessary black magic for the string to behave properly.</br>I don't know either, don't ask.
        7. Looking up the ds_map we created in the Create Event to check if the command exists.</br>If it does, we assign the full script name to the command variable.
        8. If the command doesn't exist, we log the line and a message to let the user know.
        9. If the command was found, we run it here.
        10. The list of all the keys we don't want to be interpreted as text input in the console.
        11. If the character the user inputted isn't part of the exception list, we add it to current_line.
        12. If the arrow up key is pressed, we replace the current line with whatever command was typed last.

??? abstract "2. Adding DrawGUI Event in `o_neoconsole`"
    Add a `DrawGUI` **event** for `o_neoconsole` and add the following **code** to it :
    
    ??? note "Code"
        ```py linenums="1" title="o_neoconsole - DrawGUI Event"
        if(global.neoconsole_enabled = true)
        {
        	draw_set_color(text_background_color) #(1)!
        	draw_set_alpha(text_background_alpha)
        	draw_rectangle(0, 0, hsize, vsize, false)

        	draw_set_color(text_line_background) #(2)!
        	draw_set_alpha(text_line_alpha)
        	draw_rectangle(0, vsize-20, hsize, vsize, false)

        	draw_set_font(font) #(3)!
        	draw_set_color(text_primary_color)
        	draw_set_alpha(text_primary_alpha)
        	draw_set_valign(fa_bottom)
        	var text_lines = array_length(text_)

        	for(var i = 0; i < text_lines; i++)
        	{
        		var line_size
        		line_size = string_height(string_hash_to_newline(text_[i]))
        		draw_text_ext(4, vsize-(i*line_size)-32, string_hash_to_newline(text_[i]), -1, hsize)
        	}

        	draw_set_color(text_line_color)
        	draw_set_alpha(text_line_alpha)
        	draw_set_valign(fa_top)
        	draw_text(4, vsize-20, string_hash_to_newline(text_currentline + cursor))
        }
        ```

        1. Draws the GUI for the console.
        2. Draws the GUI for the user input line.
        3. Draws the text and handles text-wrapping.
---

### **Input Isolation**

Now that we have a **working console**, if you hop in-game right now, you will notice **something annoying** happening when you **type** into the console :

Your keys are still being **read** by the game and you're **accidentally opening** your **inventory**, **character menu** or even the **map** !  
You're also **resting** or **skipping turns** while typing !

This is because the game checks only if the **original console** is **opened or not** before doing these things, but doesn't check if **ours** is.

??? Warning "The Choice"
    And this is the part where I have to **warn** you.
    There is an **easy fix** for this, but **I don't like it**. Let me explain :

    By **hijacking** the **global variable** that the **original console** uses, we can **prevent** this issue.  
    !!! Question "But why is that bad, it works right ?"
    **Yes, it does** but that's **missing the point** :

    The goal of **NeoConsole** is to be **^^completely standalone^^**, and to not rely on code from the **original console**, as the developers could remove it at **any time**.  
    They have **already started doing this** by removing all the **scripts** (*godmode*, *enemyinfo*, *teleport*...), and it's only a **matter of time** before they remove the rest of the **original console** including, you guessed it, the **global variable** we want to **hijack**.

    The day this happens, **NeoConsole** will also **stop working** if we don't do anything about it.

??? abstract "Method 1 - Easy Fix (Not future-proof)"
    Open the `scr_neoconsole_enable` script we created earlier, and add the following **highlighted code** to it :
    ```py linenums="1" hl_lines="4 6 7" title="scr_neoconsole_enable"
    function scr_neoconsole_enable()
        {
            if instance_exists(o_neoconsole)
            {
                global.neoconsole_enabled = (!global.neoconsole_enabled)
                global.consoleEnabled = global.neoconsole_enabled
            }
        }
    ```

    ---

    This will **hijack** and **toggle** the **original console's global variable** and prevent opening your inventory and such when your console is **open**.

??? abstract "Method 2 - Harder Fix (Standalone & future-proof)"
    We are going to be **replacing** the places in the game where it checks if the **original console** is **opened** to check if **our console is opened** instead.  

    The **problem** with this approach is that some of these **scripts** will simply **^^not compile back when edited^^**.  
    The only way to **force it to compile** is by editing the **bytecode (assembly)** instead of the **decompiled code**.

    This is due to a **limitation** with **UMT**.   
    As it's using an **outdated compiler**, it cannot recognize some **newer features of GML** and won't be able to compile.

    ---

    In the **following scripts**,  
    Replace `if (!global.consoleEnabled)` with `if (!global.consoleEnabled && !global.neoconsole_enabled)` :

    - *gml_GlobalScript_scr_is_pressed_key*
    - *gml_GlobalScript_scr_is_key*
    - *gml_GlobalScript_scr_keyboard_control*
    - *gml_Object_oCamera_Step_1*
    - *gml_Object_o_abilities_Step_0*
    - *gml_Object_o_Attitude_Step_0*

    ---

    In **gml_Object_o_music_button_Step_1** :

    - Replace `if ((!global.consoleEnabled) && (!pressed))`
    - With `if ((!global.consoleEnabled) && (!global.neoconsole_enabled) && (!pressed))`

    ---

    In the **gml_Object_o_inv_switch_Other_10**,  
    
    - Replace `if global.consoleEnabled`
    - With `if global.consoleEnabled || global.neoconsole_enabled`

    ---

    Now come the **2 annoying scripts** that will **require you to edit bytecode** :

    In **gml_Object_o_button_actionkey_Step_1** :

    - Replace
    ```py
    :[0]
    pushglb.v global.consoleEnabled
    conv.v.b
    not.b
    bf [2]

    :[1]
    push.v self.pressed
    conv.v.b
    not.b
    b [3]
    ```

    - With
    ```py
    :[0]
    pushglb.v global.consoleEnabled
    conv.v.b
    not.b
    bf [800]

    pushglb.v global.neoconsole_enabled
    conv.v.b
    not.b
    b [801]

    :[800]
    push.e 0

    :[801]
    bf [2]

    :[1]
    push.v self.pressed
    conv.v.b
    not.b
    b [3]
    ```

    ---

    In **gml_Object_o_player_Step_0** :

    - Replace
    ```py
    :[151]
    pushglb.v global.consoleEnabled
    conv.v.b
    not.b
    bf [209]

    :[152]
    push.v self.lock_movement
    conv.v.b
    not.b
    bf [209]
    ```
    - With
    ```py
    :[151]
    pushglb.v global.consoleEnabled
    conv.v.b
    not.b
    bf [800]

    pushglb.v global.neoconsole_enabled
    conv.v.b
    not.b
    b [801]

    :[800]
    push.e 0

    :[801]
    bf [209]

    :[152]
    push.v self.lock_movement
    conv.v.b
    not.b
    bf [209]
    ```


---

## Issues

| Issue Number | Priority | Complexity |Description |
| :---: | :---: | :---: | :--- |
| 1 | Mid | ? | Deleting text in the console is **inconsistent**. Not sure what causes this. |
| 2 | Low | Hard | The `log` **command** currently only supports writing with the **default color**.</br>Should add a way to write with **any**.</br>Will require **rewriting** the entire **rendering** side of the console.
| 3 | High | Hard | There is no **scrolling feature** for the console, the help command **can't be displayed completely** because of this.
| 4 | Low | Medium | **Importing scripts** has gotten better, but it still **takes time and isn't very convenient**.</br>Need to write a **.csx script** to **import** them in a **given order**.
| 5 | Low | Hard | Some of the **modifications** are slow and painful, it would need to be **fully automated with a .csx script**.
| 6 | Low | Medium | Some scripts **don't work** and need to be **fixed**.