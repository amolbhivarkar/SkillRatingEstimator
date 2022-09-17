# SkillRatingEstimator
Estimate individual player’s skill level for a game on the basis of game win/loss, involving multiple players in each game.

This enables implementing a competitive ladder mechanism based on skill level / skill rating to find out the right competition / opponents for players to play in the competitive ladder so as to create balanced matches. The end objective is to match players with similar abilities together.

# Solution Approach
Implement a player skill rating mechanism based on the popular Elo rating/scoring system.

## Step 1: Calculate the player’s expected score
If Player A has the ranking Ra and Player B has the ranking Rb, then we can calculate Player A’s Expected Score (Ea) in a match against Player B as follows:

        Ea = 1 / (1 + 10^((Rb - Ra)/400))
        
        where 400 is the scaling factor. 
        
Using the standard Elo formula, a player that has a 400 point rating advantage over an opponent would be 10 times as likely to win (or have an Expected Score that is 10 times larger) than their opponent. 

If the scaling factor is 800, a player should have an 800 rating advantage over the opponent to be 10 times more likely to win than the opponent. 

## Step 2: Update the player skill rating
The rating is updated based on Win or Loss

        New rating = rating + 32(score - expected score)

where 32 is a scaling or weighing factor for updating the rating 
score = 1 in case of a win
score = 0 in case of a loss


