World Camera Setting
·         height of 100 (total world height is 200)

 

Hero (Identical to Ex2)
·         Size: 5x5

·         Control model: Key-M toggles between mouse or keyboard control

o   Mouse control: Hero’s position follow that of the mouse at all time

§  This is the default control (easy for me to test)

o   Keyboard control: Up/Down (WS) keys gradually increases/decreases the Hero’s speed moving towards its Transform.up direction.

§  Initial speed: 20 units/second

·         Left/Right (AD) keys: turn the hero towards left/right at a rate of 45-degrees per second.

·         Space-bar: spawns an egg-projectile (refer to next section) at a rate of one egg every 0.2 seconds

 

Spawned Egg (Almost identical to Ex2)
·         Size: 1x1

·         Aligned with the Transform.up direction of the hero at the spawn time

·         Spawned eggs travers towards its Transform.up direction at a speed of 40 unit/sec

·         NEW: Spawned eggs expires when one of the following condition is true

o   It reaches the bounds of the world

o   It collides with an enemy

o   NEW: It collides with a waypoint

·         NEW: UI cool-down bar for egg spawning

o   Recall that the cool-down period is 0.2 second

o   The cool-down bar details:

§  A cool-down bar must be drawn reflecting the amount of time left in the cool-down

§  The cool-down bar size is always 200-pixel and (not 100-pixel) wide initially and decrease gradually to 0 pixels when egg spawning is allowed

§  Hint: I use a UI-Image, and control the RectTransform.sizeDelta [the Width/Height fields shown in the editor GUI]

 

Waypoint System (New)
There are six waypoint objects in the system, names A to F.

·         Their initial locations are: A:(-70, 70), B(70, -70), C(30, 0), D(-70, -70), E(70, 70), F(-30, 0)

·         When a waypoint object collides with an egg, it loses 25% of its opacity

o   This can be implemented by decrease the alpha channel of the SpriteRenderer color by 0.25

·         On the forth collision with an egg, a waypoint object will disappear and re-position itself in a new point that is randomly located at + or - 15 units in both X and Y from the initial position of the waypoint.

o   Note, the random position is measured from the initial position and NOT the current position.

o   This means, waypoints will never move more than 15-units away from its original position

·         H-key: toggles the hiding of the waypoint objects

 
Enemy and Spawning (new: with States)
·         Identical to Ex2:

·         Each enemy size is 5x5

·         There are always 10 enemies in the world

·         Enemies are within 90% of the world boundaries

·         When an enemy comes in contact:

o   With the hero, it is destroyed

o   With the egg: it loses 80% of its current energy (displayed as alpha-channel scaled by 80%):

GetComponent<Renderer>().material.color.a *= 0.8;

// Note, the above line does not run as Unity does not

// allow the modification of Color channels. You must

// create/modify/assign using a separate Color object

 

o   The 4th collision with an egg destroys an enemy

·         As soon as an enemy is destroyed, a new one is spawned subject to the above condition (maintain exactly 10, always within 90% of world boundaries)

·         New behaviors: Patrol

o   All spawned enemies travel at a constant speed of 20 unit/sec

o   Under the user control (refer to Game State), an enemy sequences through the waypoints in two one of two ways (J-Key toggles between the two)

§  Sequentially from A to F then back to A again

§  Randomly from one to the next random waypoint

o   Target waypoint, at all times an enemy travels towards a target waypoint. It must turn gradually towards the target waypoint at all times at a rate of 0.03/60. [call the PointAtPosition() function with this rate at each update].

o   When a Target waypoint is re-positioned (because it has received 4 shots of the egg), the enemy will move towards the new position

o   When an enemy is within 25 units of the current target waypoint, it should request and set the next way point to be its new target and begin turning.

 

 

Application Status 
·         The application status must be printed out including:

o   Identical to Ex2:

§  Hero

·         control mode: Mouse/Keyboard

·         Number of times hero touched the enemy

§  Egg:

·         Number of eggs that are currently in the world

§  Enemy

·         Total current enemy count

·         Number destroyed

o   New: Print out waypoint mode: random vs sequence

·         Q-key:

o   Quits the application

 

Note, you will lose points if Ex2 functionality stops working. E.g. if Hero mouse control does not work anymore, you will lose all of the associated points.

Credit Distribution
·         (2%) Camera Setting

o    Height of 100

·         (3%) Hero: If lost all Ex2 functionality: -30%

o    (2%) Size 5x5

o    (5%) Left/Right (AD) Keys: rotation

o    (5%) Key-M to toggle between mouse/keyboard control

o    (5%) In mouse mode: position is controlled by the mouse

o    (5%) In keyboard mode: Initial speed is 20 units/sec

o    (10%) In keyboard mode: Up/Down (WS) keys control speed smoothly

o    (10%) Space-bar spawns egg at 0.2 second per egg

o    (5%) Destroys an enemy when collided

·         (20%) Egg Behavior: 

o    (1%) Ex2 functionality: you can lose up to 25% if following stop working

§  (2%) Size 1x1

§  (10%) Orientation follows that of Hero’s transform.up

§  (10%) Travels towards its transform.up at 40 units/sec

§  (5%) Expires when collide with enemy

§  (10%) Expires when leaves the world bound

§  Graded based on proper application status echo of number of eggs currently in the world

o    (4%) Expires when collide with a waypoint

o    (5%) Cool-down bar disappears/re-appears representing spawning readiness

o    (10%) Cool-down bar size corresponds to amount of time left

 

·         (25%) Waypoint System

o    (5%) Proper initial positions

o    (5%) Collision response with an Egg: lost 25% opacity

o    (5%) The forth collision, way point disappears

o    (10%) Way point re-spawn randomly +- 15 units from original initial position

 

·         (35%) Enemies

o    (5%) Ex2 functions: you can lose up to 25% if following stop working

§  (2%) Size: 5x5

§  (5%) Maintains 10 enemies in the world

§  (10%) Spawned randomly within 90% of world boundaries

§  (5%) Destroyed by hero collision

§  (10%) Gradual loosing of power (alpha-channel) by Egg collision

§  (10%) Destroy by 4th Egg collision

o    (5%) Travel at constant speed of 20 unit/sec

o    (10%) Fly towards waypoints with turn rate (0.03/60) at proper distance (25)

o    (5%) Points towards target waypoint when it is re-positioned

o    (5%) Support sequencing/random switch

o    (5%) Proper A to F sequencing

o    (5%) Proper random sequencing

 

·         (5%) Application Status

o    (1%) Ex2 functions: you can lose up to 10% if following stop working

§  (5%) Hero control mode and collision with enemy count

§  (5%) Egg: number in the world

§  (5%) Enemy: total number in the world + number destroyed

o    (4%) Waypoint sequencing mode: Random/Sequence


·         (10%) Submissions

o     (10%) Submission with a zip

§  Unzip and run in the editor properly

o    (10%) Submission include an EXE folder 

§  Double click to run the game
