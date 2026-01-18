## Model Versions and Reward/State Experiments (Snake RL)

### modelVer1

default configuration from forked repository

model is not able to properly prevent collisions with itself

### modelVer2

idea: differentiate between collision with boundaries and collision with itself.

did not work due bug:
agent.py 
    - getState: wrong directions. dir_r and dir_l instead of dir_u and dir_d

### modelVer3

trained model after bugfix in modelVer2

did not work due bug:
agent.py
    - getState: missing brackets

### modelVer4

model preparation since modelVer2 now evaluable
remember idea: differentiate between collision with boundaries and collision with itself.

evaluation: basically similar results

observation: modelVer1 and modelVer4 both seem to be kind of intelligent but sometimes they steer the sneak into dead ends. Sometimes there is enough space (2 or more lines) that the snake is able to get out but it seems to be randomly. 

possible approach: Define a "danger state" which indicates dead ends with one line.

Why should be dead ends with one line a danger state?
See examples below. Snake is marked with S and H while H is the head of the Snake. First example is a dead end which ends the game if the snake turns right. Second is also a dead end but the snake would be able to get out if it. Also available space will be used efficiently.

```text
Example 1:

####################
#      SSSSSSSSSS  #
#        H      S  #
#        SSSSSSSS  #
#                  #
#                  #
####################

Example 2:

####################
#      SSSSSSSSSS  #
#               S  #
#        H      S  #
#        SSSSSSSS  #
#                  #
####################

````

turning right in example 1 ends the game, while turning right in example 2 doesnt and it efficiently uses available space
