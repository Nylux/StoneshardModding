# Useful Functions

## Description

This here is an **unsorted** list of **random functions** you may or may not find useful during your modding journey.  
Functions that are [built into Gamemaker Studio](https://manual-en.yoyogames.com/GameMaker_Language/GameMaker_Language_Index.htm) should **not** be listed here.

This will **eventually get sorted** into something more useful/readable, but for now, this will do.

Please **test functions thoroughly and make sure you understand what they do** before adding them to the documentation.

---

## Functions

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
