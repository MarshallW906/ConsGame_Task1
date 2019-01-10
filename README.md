## Design Statement – Customized ‘Ghost Shooter’ Game

Note: Resources of this game mainly come from **Beginner’s Guild to Construct 2.** I followed this guide getting to know about Construct 2, then I put my own design into it, making this game up. Pics of items are from **Metal Slug**, some from *pubzi.com*.



###  0. Instructions

- Move: Arrow Keys

- Aim: Mouse Move

- Shoot: Left Click

- Special Shoot: Right Click



### 1. Game Start/Over/Restart

After the game launched, a clickable "Start" is displayed.  The game is on once "Start" is clicked.

A "player", which can move freely, is also instantiated on the background. But:

- It cannot shoot(Left Click doesn't make the player shoot) before the game start

The game is over when HP gets down to 0 or less. Then:

- Final score is displayed.
- Button "Restart" enabled.

 

### 2. HUD

HUD includes HP, SP (for Special Shoot), bullets (remaining bullet count)

[When bullets = 0], the default, normal weapon is used, with infinite bullets.



### 3. Combat System

#### 3a. Monster

- Emerged at random location.
- Initial HP: 9. 
- [When HP <= 5], moving speed double.
- [When HP <= 2], moving speed acceleration : 0 -> 20.
- [When HP <= 0], eliminated.
- **[Special]** Both eliminated when two monsters collide with each other, providing an SP point as a bonus.



#### 3b. "Player"

- Initial HP: 3.
- No maximum HP.
- [When collided with a monster], HP -1.
- [When collided with a heart], HP +1 (also the "heart" will be destroyed). 
- Initial Maximum Moving Speed: 200
- Initial Moving Speed Acceleration: 600



Special Shoot (SP):

- Cast a small rocket, which keeps moving to the mouse at a pace.
- Initial Count: 5. 
- Damage: Killing Blow.
- Vanish after killing 10 foes (for each shot).
- SP Count will only increase when two monsters eliminated due to collision with each other.

#### 3c. Items

Random items emerge on the ground periodically, at random locations.



Weapons: 4 types in total: D(default), H, R, C

- D: default pistol. Infinite bullets. Shooting Speed: normal. Damage: 1.
- H: Machine gun. Bullets (when picked up): 50. Shooting Speed: Fast. Damage: 3.
- R: Rockets. Bullets (when picked up): 15. Shooting Speed: normal. Damage: 2. **Guided missiles.**
- C: 100% Penetration gun. Bullets (when picked up): 5. Shooting Speed: Extremely Fast. Damage: **Killing Blow.** **100% Penetration & Infinite flying distance (inside the canvas).**
  - For H, R, C: If the same weapon is picked up, bullets will add up; if a different weapon is picked up, the previous weapon and its bullets will be abandoned.

Other Items:

- Heart: HP + 1. No maximum HP.
- Blue medal: Current Bullets + 100.  Cannot be picked up without an H/R/C weapon.
- Grey medal: Kill all monsters right away. Emerge only if more than 10 monsters exist.
- Blue ">>" mark: Player maximum moving speed +25%, Player moving speed acceleration+25%



**Hit-got punishment:** Whenever the "player" gets damaged, its special weapon is abandoned (back to D), moving speed & acceleration are reset to (200, 600).



PS: Didn't implement a shop due to the limit number of game events in evaluation version.



#### 3d. Score

Score +1 for every monster eliminated.



### 4. Stages

There is no explicit stage switch in this game. However, difficulty will increase as the player gets higher score. Here are the details (cumulatively):

- Lv.0(Score 0): Basic settings.
- Lv.1(Score 10): Monster Emerge Speed: +150%
- Lv.2(Score 35): Monster Basic Moving Speed: +25
- Lv.3(Score 70): Player Basic Moving Speed: +50%, Basic Moving Acceleration: +50%
- Lv.4(Score 115): Monster Emerge Speed: +66.7%
- Lv.5(Score 170): Monster Basic Moving Speed: +75
  - From this level on, missiles of special shoot can also "pick up" weapons for the player. 
  - **No weapon-switch-abandon any more.**
- Lv.6(Score 235): Player Basic Moving Speed: +50%, Basic Moving Acceleration: +50%, Basic Moving Deceleration +50% (will help with a faster move and faster stop)
- Lv.7(Score 310): Monster Emerge Speed: +50%
  - **No "hit-got punishment" any more.**
- Lv.8(Score 395): Monster Basic Moving Speed: +25
- Lv.9(Score 490): Player Basic Moving Speed: +50%, Basic Moving Acceleration: +50%, Basic Moving Deceleration +33.3% 
- Lv."subMax"(Score 666): Shooting Speed of D(default weapon): +50%
  - A text "666" will emerge as a HUD.
- Lv.Max(Score 777+): The text "666" will become "666Plus".



