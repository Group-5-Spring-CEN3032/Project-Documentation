# Entity Statistics
The `Stats` component tracks a player or entity's Health, Mana, and Stamina. For simplicity, all agents are assummed to have these stats, but some special agents you create may not use them all.

`Stats` stores all the raw values as floats (`health`, `mana`, `stamina`) and limits them between 0 and a maximum value (`maxHealth`, `maxMana`, `maxStamina`).