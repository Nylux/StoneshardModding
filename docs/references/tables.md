# Tables

This article will contain informations about **tables**.  
They're found in the `CODE` block in UMT and usually start with `gml_GlobalScript_table`.  
For more info on what those are see [this article](../guides/working-with-tables.md).  

For the tool used to convert tables into [.csv files](https://simple.wikipedia.org/wiki/Comma-separated_values) for better readability / editing, see [GML to CSV Converter](../tools/gmltocsv.md).  
???+ Info 
    `Unnamed:XX` or `nan` in the table format section means the cell is empty.  
    It looks weird, but it's simply an issue with how we import tables in this documentation.  
    The actual gml table in your game will simply have empty cells at those locations.

    Attribute descriptions with the :warning: icon indicate untested, poorly understood or unknown behaviours.  
    No :warning: icon doesn't automatically mean the description is accurate or correct.
    
    As this is still a very early version of the documentation, errors can slip through, so feel free to contact [maintainers](../index.md#contributors) or to edit this page yourself.

---

??? abstract "gml_GlobalScript_table_enemy_balance"

    ## **gml_GlobalScript_table_enemy_balance**
    :octicons-tag-24: **0.8.1.9**

    **Content** :  
    This table contains various stats about the enemies present in Stoneshard, including their level, weapon types, factions, hit chances, resistances and many others.

    **Table Format** :  

    {{ read_csv('../assets/tables/gml_GlobalScript_table_enemy_balance.csv', sep=';') }}



    **Attributes** :

    | Type | Name | Description |
    |:------:|:------:|:-------------|
    | `String` | **name** | The name of the enemy. |
    | `Integer` | **LVL** | The level of the enemy. |
    | `String` | **ID** | The ID of the enemy. |
    | `String` | **type** | The enemy type of the enemy. |
    | `String` | **faction** | The faction the enemy belongs to. |
    | `String` | **pattern** | The AI pattern for this enemy. |
    | `String` | **spawn_type** | The type of spawn for the enemy. &nbsp; :warning: |
    | `String` | **weapon** | The type of weapon the enemy will spawn with. |
    | `String` | **armor** | The type of armor the enemy will spawn with. |
    | `Integer` | **SU** | Spawn weight for the enemy. |
    | `String` | **size** | The size category for the enemy. |
    | `String` | **matter** | The matter this enemy is mainly made out of. |
    | `Integer` | **EF** | "Inner Calculating" according do a dev. &nbsp; :warning: |
    | `Integer` | **XP** | The amount of XP given when the enemy is killed.  |
    | `Integer` | **HP** | The amount of HP the enemy has. |
    | `Integer` | **MP** | The amount of MP the enemy has. |
    | `Integer` | **Head_DEF** | &nbsp; :warning: |
    | `Integer` | **Body_DEF** | &nbsp; :warning: |
    | `Integer` | **Arms_DEF** | &nbsp; :warning: |
    | `Integer` | **Legs_DEF** | &nbsp; :warning: |
    | `Integer` | **Hit_Chance** | The % of chance the enemy's attack have to hit. |
    | `Integer` | **EVS** | The % of chance the enemy has to dodge an attack. |
    | `Integer` | **PRR** | The % of chance the enemy has to block an attack. |
    | `Integer` | **Block_Power** | The maximum amount of damage the enemy can block. Recovers each turn. |
    | `Integer` | **Block_Recovery** | The amount of block power the enemy recovers each turn. |
    | `Integer` | **CRT** | The % of chance the enemy has to deal a critical hit. |
    | `Integer` | **CRTD** | The additional damage the enemy deals on a critical hit. &nbsp; :warning: |
    | `Integer` | **CTA** | The % of chance the enemy has to counterattack when hit. |
    | `Integer` | **FMB** | The % of chance the enemy has to fumble an attack. |
    | `Integer` | **Miscast_Chance** | The % of chance the enemy has to miscast a spell. |
    | `Integer` | **Fortitude** | &nbsp; :warning: |
    | `?` | **STL** | Stealthiness of the enemy. Currently not implemented in the game. |
    | `Integer` | **Health_Restoration** | Either the amount of health, the % of health or the chance for the enemy to recover health. &nbsp; :warning: |
    | `Integer` | **MP_Restoration** | Same as Health_Restoration. &nbsp; :warning: |
    | `Integer` | **Cooldown_Reduction** | &nbsp; :warning: |
    | `Integer` | **Knockback_Resistance** | &nbsp; :warning: |
    | `Integer` | **Stun_Resistance** | &nbsp; :warning: |
    | `Integer` | **Bleeding_Resistance** | &nbsp; :warning: |
    | `Integer` | **Bleeding_Chance** | &nbsp; :warning: |
    | `Integer` | **Stun_Chance** | &nbsp; :warning: |
    | `Integer` | **Daze_Chance** | &nbsp; :warning: |
    | `Integer` | **Knockback_Chance** | &nbsp; :warning: |
    | `Integer` | **Immob_Chance** | &nbsp; :warning: |
    | `Integer` | **Stagger_Chance** | &nbsp; :warning: |
    | `Integer` | **STR** | The Strength ability score of the enemy. |
    | `Integer` | **AGL** | The Agility ability score of the enemy. |
    | `Integer` | **Vitality** | The Vitality ability score of the enemy. |
    | `Integer` | **PRC** | The Perception ability score of the enemy. |
    | `Integer` | **WIL** | The Willpower ability score of the enemy.  |
    | `Integer` | **Damage_Returned** | The amount of damage dealt to the attacker when the enemy is attacked. |
    | `Integer` | **VIS** | The vision range of the enemy. |
    | `Integer` | **Bonus_Range** | &nbsp; :warning: |
    | `Integer` | **Lifesteal** | Either the flat amount, the amount %, or the chance of stealing health when the enemy attacks. &nbsp; :warning: |
    | `Integer` | **Manasteal** | Either the flat amount, the amount %, or the chance of stealing mana when the enemy attacks. &nbsp; :warning: |
    | `Integer` | **Healing_Received** | &nbsp; :warning: |
    | `Integer` | **Avoiding_Chance** | &nbsp; :warning: |
    | `Integer` | **Head** | The amount of heads the enemy has (leave empty if none) |
    | `Integer` | **Torso** | The amount of torsos the enemy has (leave empty if none) |
    | `Integer` | **Left_Leg** | The amount of left legs the enemy has (leave empty if none) |
    | `Integer` | **Right_Leg** | The amount of right legs the enemy has (leave empty if none) |
    | `Integer` | **Left_Hand** | The amount of left hands the enemy has (leave empty if none) |
    | `Integer` | **Right_Hand** | The amount of right hands the enemy has (leave empty if none) |
    | `Integer` | **IP** | Injury Protection, the % of chance to not produce an injury when hit. |
    | `Integer` | **Pain_Resistance** | &nbsp; :warning: |
    | `Integer` | **Morale** | &nbsp; :warning: |
    | `Integer` | **Threat_Time** | The amount of time animals stay threatened before becoming hostile. |
    | `Integer` | **Bodypart_Damage** | The % of damage this enemy deals to bodyparts when attacking. |
    | `Integer` | **Magic_Power** | The damage effectiveness of the enemy's spells. |
    | `Integer` | **Armor_Piercing** | The % of the damage that will ignore armor. |
    | `Integer` | **Slashing_Damage** | The amount of slashing damage the enemy's attacks deal. |
    | `Integer` | **Piercing_Damage** | The amount of piercing damage the enemy's attacks deal. |
    | `Integer` | **Blunt_Damage** | The amount of blunt damage the enemy's attacks deal. |
    | `Integer` | **Rending_Damage** | The amount of rending damage the enemy's attacks deal. |
    | `Integer` | **Fire_Damage** | The amount of fire damage the enemy's attacks deal. |
    | `Integer` | **Shock_Damage** | The amount of shock damage the enemy's attacks deal. |
    | `Integer` | **Poison_Damage** | The amount of poison damage the enemy's attacks deal. |
    | `Integer` | **Caustic_Damage** | The amount of caustic damage the enemy's attacks deal. |
    | `Integer` | **Frost_Damage** | The amount of frost damage the enemy's attacks deal. |
    | `Integer` | **Arcane_Damage** | The amount of arcane damage the enemy's attacks deal. |
    | `Integer` | **Unholy_Damage** | The amount of unholy damage the enemy's attacks deal. |
    | `Integer` | **Sacred_Damage** | The amount of sacred damage the enemy's attacks deal. |
    | `Integer` | **Psionic_Damage** | The amount of psionic damage the enemy's attacks deal. |
    | `Integer` | **Physical_Resistance** | The % of reduction for all the Physical Damage the enemy receives. (Slashing, Piercing, Crushing, Rending). |
    | `Integer` | **Natural_Resistance** | The % of reduction for all the Nature Damage the enemy receives. (Fire, Frost, Shock, Poison, Caustic). |
    | `Integer` | **Slashing_Resistance** | The % of reduction for all the Slashing Damage the enemy receives. |
    | `Integer` | **Piercing_Resistance** | The % of reduction for all the Piercing Damage the enemy receives. |
    | `Integer` | **Blunt_Resistance** | The % of reduction for all the Blunt Damage the enemy receives. |
    | `Integer` | **Rending_Resistance** | The % of reduction for all the Rending Damage the enemy receives. |
    | `Integer` | **Fire_Resistance** | The % of reduction for all the Fire Damage the enemy receives. |
    | `Integer` | **Shock_Resistance** | The % of reduction for all the Shock Damage the enemy receives. |
    | `Integer` | **Poison_Resistance** | The % of reduction for all the Poison Damage the enemy receives. |
    | `Integer` | **Caustic_Resistance** | The % of reduction for all the Caustic Damage the enemy receives. |
    | `Integer` | **Frost_Resistance** | The % of reduction for all the Frost Damage the enemy receives. |
    | `Integer` | **Arcane_Resistance** | The % of reduction for all the Arcane Damage the enemy receives. |
    | `Integer` | **Unholy_Resistance** | The % of reduction for all the Unholy Damage the enemy receives. |
    | `Integer` | **Sacred_Resistance** | The % of reduction for all the Sacred Damage the enemy receives. |
    | `Integer` | **Psionic_Resistance** | The % of reduction for all the Psionic Damage the enemy receives. |
    | `Integer` | **canBlock** | Whether or not the enemy can block attacks. (1 for true, empty for false) |
    | `Integer` | **canDisarm** | Whether or not the enemy can be disarmed. (1 for true, empty for false) |
    | `Integer` | **canSwim** | Whether or not the enemy can swim. (1 for true, empty for false) |
    | `Integer` | **Swimming_Cost** | The amount of MP this enemy uses for every tile travelled when swimming. |


??? abstract "gml_GlobalScript_table_skills_stat"

    ## **gml_GlobalScript_table_skills_stat**
    :octicons-tag-24: **0.8.1.9**

    **Content** :  
    This table contains various stats about the skills in Stoneshard, like their cooldowns, buffs/debuffs durations, range, targetting method and more.

    **Table Format** :  

    {{ read_csv('../assets/tables/gml_GlobalScript_table_skills_stat.csv', sep=';') }}



    **Attributes** :

    | Type | Name | Description |
    |-|-|-|
    | `String` |  | The skill's name. Not to be confused with the skill's in-game name. </br>Note: Devs left this field unnamed for some reason...|
    | `String` | **Object** | The gameobject associated with this skill. |
    | `String` | **Target** | The targetting method for this skill.  </br> Possible values : `No Target`, `Target Object`, `Target Point`, `Target Area`. |
    | `Integer` | **Range** | The range this skill can be used at. </br> Special values : `0` for no range, `range` to use the weapon's range, `vis` to use the vision attribute. |
    | `Integer` | **KD** | The cooldown for this skill in turns. |
    | `Integer` | **MP** | The amount of energy used to use this skill. |
    | `Integer` | **Reserv** | &nbsp; :warning: |
    | `Integer` | **Duration** | The amount of turns the buff/debuff inflicted by this skill will last. &nbsp; :warning:|
    | `Integer` | **AOE_Lenght** | The amount of tiles covered by the AOE of this skill on the X axis. `0` if none. |
    | `Integer` | **AOE_Width** | The amount of tiles covered by the AOE of this skill on the Y axis. `0` if none. |
    | `Integer` | **is_movement** | Whether or not this skill moves the object casting it. |
    | `String` | **Pattern** | The pattern for this skill. </br> Possible values : `normal`, `five`, `line`, `circle`, ``pyramid` |
    | `String` | **Class** | The class for this skill. </br> Possible values : `skill`, `spell`, `attack`|
    | `Integer` | **Bonus_Range** | The bonus range added when using this skill. &nbsp; :warning: |
    | `String` | **Starcast** | The sprite used when this skill is used. </br> Note : The sprite name seems to be followed by an underscore (_). &nbsp; :warning: |
    | `String` | **Branch** | The skill tree this tree belong to. `none` if it belongs to none. |
    | `Integer` | **is_knockback** | Whether or not this skill causes knockback. |
    | `Integer` | **Crime** | Whether or not using this skill around friendly NPCs is considered a crime. &nbsp; :warning:|
    | `String` | **metacategory** | The metacategory this skill belongs to. Possible values : `weapon`. |
    | `Integer` | **FMB** | The chance for this skill to backfire. Special values : `0` for no backfire possible.  &nbsp; :warning: |
    | `Integer` | **AP** | &nbsp; :warning: |
    | `Integer` | **Attack** | Whether this skill is an attack or not. Spells don't seem to have this. &nbsp; :warning: |
    | `Integer` | **Stance** | Whether this skill is a stance or not. |
    | `Integer` | **Charge** | Whether this skill is a charge / a rush. |
    | `Integer` | **Maneuver** | Whether this skills is a maneuver. &nbsp; :warning: |
    | `Integer` | **Spell** | Whether this skill is a spell or not. |