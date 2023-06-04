# Useful Functions

## Description

This here is an **unsorted** list of **random functions** you may or may not find useful during your modding journey.  
Functions that are [built into Gamemaker Studio](https://manual-en.yoyogames.com/GameMaker_Language/GameMaker_Language_Index.htm) should be listed in their own section.

This will **eventually get sorted** into something more useful/readable, but for now, this will do.

!!! Info
	Please **test functions thoroughly and make sure you understand what they do** before adding them to the documentation.

---

##  **^^GML Functions^^**

### is_undefined()

Syntax : `is_undefined(variable)`

Returns true if the passed variable was never initialized to a value.
Returns false otherwise.
Not to mistake with `variable_instance_exists()` or `variable_global_exists()`.
---

###  variable_global_exists()

Syntax : `variable_global_exists("global_var_name")`

Returns true if a global variable with the named passed as a string exists. It doesn't need to be initialized.
Returns false if it doesn't.
---
### instance_destroy()

Syntax : `instance_destroy(gameobject)`

Deletes passed gameobject if passed. 
Deletes the gameobject this was called from if no gameobject was passed.
---
### event_user()

Syntax : `event_user(event_number)`

Fires passed user event on the gameobject calling this.
`event_number` should be between 0 and 15.
---
### script_execute()

Syntax : `script_execute(scr, arg0, arg1, arg2..., etc...)`

Calls the passed script with given arguments.

---
### show_message()

Syntax : `show_message("message")`

Creates a pop-up window with given message.

---
### audio_play_sound()

Syntax : `audio_play_sound(snd_index, priority, looping)`

Plays the passed sound index.
Priority is an int, higher means higher priority.
Looping is a boolean, if true the sound will loop.

e.g. : `audio_play_sound(snd_PlayerDead, 10, false)`

---
</br>

##  **^^Stoneshard Functions^^**

### scr_actionsLogUpdate()

Syntax : `scr_actionsLogUpdate("message")`

Prints message in the action log at the bottom left of the screen.  
Useful for debugging.

---

### scr_id_get_name()

Syntax : `scr_id_get_name(id)`

Returns name for given ID.  
e.g. `scr_id_get_name(3126)` --> `"o_player"`

---

### script_execute()

Syntax : `script_execute(scriptName, _argumentsArray)`

Executes script with array of arguments.

---

### scr_inventory_add_item()

Syntax :

```
with(o_inventory)
	scr_inventory_add_item(item_name_or_id)
```

Adds item by id or by name to player's inventory.

---

### scr_smoothSaveAuto()

Syntax : `scr_smoothSaveAuto()`

Uses the built-in autosave feature to save the game.

---
