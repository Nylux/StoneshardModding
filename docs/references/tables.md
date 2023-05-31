# Tables

This article will contain informations about **tables**.  
They're found in the `CODE` block in UMT and usually start with `gml_GlobalScript_table`.  
For more info on what those are see [this article](../guides/tables.md).  

For the tool used to convert tables into .csv files for better readability / editing, see [GML to CSV Converter](../tools/gmltocsv.md).  
To contribute to this page, you can use the [CSV to Markdown](https://tableconvert.com/csv-to-markdown) website.

---

## gml_GlobalScript_table_enemy_balance

**Version**

Last updated for `Stoneshard 0.8.1.9`

**Content** :  

This table contains various stats about the enemies present in Stoneshard, including their level, weapon types, factions, hit chances, resistances and many others.

**Table Format** :  

| name               | LVL | ID                   | type   | faction | pattern | spawn_type | weapon | armor | SU | size   | matter | EF  |  | XP | HP | MP | Head_DEF | Body_DEF | Arms_DEF | Legs_DEF |  | Hit_Chance | EVS | PRR | Block_Power | Block_Recovery | CRT | CRTD | CTA | FMB | Miscast_Chance | Fortitude | STL | Health_Restoration | MP_Restoration | Cooldown_Reduction | Knockback_Resistance | Stun_Resistance | Bleeding_Resistance |  | Bleeding_Chance | Stun_Chance | Daze_Chance | Knockback_Chance | Immob_Chance | Stagger_Chance |  | STR | AGL | Vitality | PRC | WIL |  | Damage_Returned | VIS | Bonus_Range | Lifesteal | Manasteal | Healing_Received | Avoiding_Chance |  | Head | Torso | Left_Leg | Right_Leg | Left_Hand | Right_Hand | IP | Pain_Resistance | Morale | Threat_Time |  | Bodypart_Damage | Magic_Power | Armor_Piercing | Slashing_Damage | Piercing_Damage | Blunt_Damage | Rending_Damage | Fire_Damage | Shock_Damage | Poison_Damage | Caustic_Damage | Frost_Damage | Arcane_Damage | Unholy_Damage | Sacred_Damage | Psionic_Damage | x | Physical_Resistance | Natural_Resistance | Magical_Resistance | x | Slashing_Resistance | Piercing_Resistance | Blunt_Resistance | Rending_Resistance | Fire_Resistance | Shock_Resistance | Poison_Resistance | Caustic_Resistance | Frost_Resistance | Arcane_Resistance | Unholy_Resistance | Sacred_Resistance | Psionic_Resistance | x | canBlock | canDisarm | canSwim | Swimming_Cost |
|--------------------|-----|----------------------|--------|---------|---------|------------|--------|-------|----|--------|--------|-----|---|----|----|----|----------|----------|----------|----------|---|------------|-----|-----|-------------|----------------|-----|------|-----|-----|----------------|-----------|-----|--------------------|----------------|--------------------|----------------------|-----------------|---------------------|---|-----------------|-------------|-------------|------------------|--------------|----------------|---|-----|-----|----------|-----|-----|---|-----------------|-----|-------------|-----------|-----------|------------------|-----------------|---|------|-------|----------|-----------|-----------|------------|----|-----------------|--------|-------------|---|-----------------|-------------|----------------|-----------------|-----------------|--------------|----------------|-------------|--------------|---------------|----------------|--------------|---------------|---------------|---------------|----------------|---|---------------------|--------------------|--------------------|---|---------------------|---------------------|------------------|--------------------|-----------------|------------------|-------------------|--------------------|------------------|-------------------|-------------------|-------------------|--------------------|---|----------|-----------|---------|---------------|
| Skeleton Swordsman | 4   | o_skeleton_swordsman | undead | Undead  | Melee   | Melee      | sword  | Light | 9  | medium | bones  | 461 |  | 70 | 65 | 40 |         | 2        | 1        | 1        |  | 70         |    | 10  | 10          | -5             |    |     |    | 30  |               |          |    | 0                  | 6              | 35                 |                     | 20              |                    |  | 10              |            |            |                 |             |               |  | 14  | 12  | 10       | 12  | 10  |  |                | 6   |            |          |          |                 |                |  | 1    | 1     | 1        | 1         | 1         | 1          | 75 | 100             |       |            |  | 5               |            | 10             | 13              |                |             |               |            |             |              |               |             |              | 2             |              |               |  |                    |                   |                   |  |                    |                    |                 |                   |                |                 |                  |                   |                 |                  |                  | -50               |                   |  | 1        |          |        | 2             |

**Attributes** :

| Type | Name | Description |
|:------:|:------:|:-------------|
| `String` | **name** | The name of the enemy. |
| `Integer` | **LVL** | The level of the enemy. |
| `String` | **ID** | The ID of the enemy. |
| `String` | **type** | The enemy type of the enemy. |
| `String` | **faction** | The faction the enemy belongs to. |
| `String` | **pattern** | The AI pattern for this enemy. |
| `String` | **spawn_type** | The type of spawn for the enemy. (?) |
| `String` | **weapon** | The type of weapon the enemy will spawn with. |
| `String` | **armor** | The type of armor the enemy will spawn with. |
| `Integer` | **SU** | Spawn weight for the enemy. |
| `String` | **size** | The size category for the enemy. |
| `String` | **matter** | The matter this enemy is mainly made out of. |
| `Integer` | **EF** | "Inner Calculating" according do a dev. (?) |
| `Integer` | **XP** | The amount of XP given when the enemy is killed.  |
| `Integer` | **HP** | The amount of HP the enemy has. |
| `Integer` | **MP** | The amount of MP the enemy has. |
| `Integer` | **Head_DEF** | (?) |
| `Integer` | **Body_DEF** | (?) |
| `Integer` | **Arms_DEF** | (?) |
| `Integer` | **Legs_DEF** | (?) |
| `Integer` | **Hit_Chance** | The % of chance the enemy's attack have to hit. |
| `Integer` | **EVS** | The % of chance the enemy has to dodge an attack. |
| `Integer` | **PRR** | The % of chance the enemy has to block an attack. |
| `Integer` | **Block_Power** | The maximum amount of damage the enemy can block. Recovers each turn. |
| `Integer` | **Block_Recovery** | The amount of block power the enemy recovers each turn. |
| `Integer` | **CRT** | The % of chance the enemy has to deal a critical hit. |
| `Integer` | **CRTD** | The additional damage the enemy deals on a critical hit. (?) |
| `Integer` | **CTA** | The % of chance the enemy has to counterattack when hit. |
| `Integer` | **FMB** | The % of chance the enemy has to fumble an attack. |
| `Integer` | **Miscast_Chance** | The % of chance the enemy has to miscast a spell. |
| `Integer` | **Fortitude** | (?) |
| `?` | **STL** | Stealthiness of the enemy. Currently not implemented in the game. |
| `Integer` | **Health_Restoration** | Either the amount of health, the % of health or the chance for the enemy to recover health. (?) |
| `Integer` | **MP_Restoration** | Same as Health_Restoration. |
| `Integer` | **Cooldown_Reduction** | (?) |
| `Integer` | **Knockback_Resistance** | (?) |
| `Integer` | **Stun_Resistance** | (?) |
| `Integer` | **Bleeding_Resistance** | (?) |
| `Integer` | **Bleeding_Chance** | (?) |
| `Integer` | **Stun_Chance** | (?) |
| `Integer` | **Daze_Chance** | (?) |
| `Integer` | **Knockback_Chance** | (?) |
| `Integer` | **Immob_Chance** | (?) |
| `Integer` | **Stagger_Chance** | (?) |
| `Integer` | **STR** | The Strength ability score of the enemy. |
| `Integer` | **AGL** | The Agility ability score of the enemy. |
| `Integer` | **Vitality** | The Vitality ability score of the enemy. |
| `Integer` | **PRC** | The Perception ability score of the enemy. |
| `Integer` | **WIL** | The Willpower ability score of the enemy.  |
| `Integer` | **Damage_Returned** | The amount of damage dealt to the attacker when the enemy is attacked. |
| `Integer` | **VIS** | The vision range of the enemy. |
| `Integer` | **Bonus_Range** | (?) |
| `Integer` | **Lifesteal** | Either the flat amount, the amount %, or the chance of stealing health when the enemy attacks. (?) |
| `Integer` | **Manasteal** | Either the flat amount, the amount %, or the chance of stealing mana when the enemy attacks. (?) |
| `Integer` | **Healing_Received** | (?) |
| `Integer` | **Avoiding_Chance** | (?) |
| `Integer` | **Head** | The amount of heads the enemy has (leave empty if none) |
| `Integer` | **Torso** | The amount of torsos the enemy has (leave empty if none) |
| `Integer` | **Left_Leg** | The amount of left legs the enemy has (leave empty if none) |
| `Integer` | **Right_Leg** | The amount of right legs the enemy has (leave empty if none) |
| `Integer` | **Left_Hand** | The amount of left hands the enemy has (leave empty if none) |
| `Integer` | **Right_Hand** | The amount of right hands the enemy has (leave empty if none) |
| `Integer` | **IP** | Injury Protection, the % of chance to not produce an injury when hit. |
| `Integer` | **Pain_Resistance** | (?) |
| `Integer` | **Morale** | (?) |
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
| `Integer` | **Swimming_Cost** | The amount of MP used for every tile travelled when swimming. |

---