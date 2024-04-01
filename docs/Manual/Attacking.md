# Attacking
Our `Attacking` is a simple amie and fire system to damage the NPCs in the environment.

This also correlates to the health bar on the NPCs. If the NPC doesn't have a health bar over it, you will not be able to attack it.

## Attacking Script

### Modifyable Variables 
These variables are open to your configuration to customize your controller the attck you want.

- **Stats** A reference to the player states.
- **Projectile** A reference to the projectile that the attack will use.
- **Fire Position** This is the position the projectile will be fire at.
- **Speed** This is how fast the projectile shoots out.
- **Target Time** This is the cool down time between attacks.

## Projectile Script

This is the basic projectile that your attack will use.

### Modifyable Variables

- **Destroy Time** This is the amount of time it will take before the projectile is destroy if it dosn't hit something.