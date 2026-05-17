Q1. For q1 I created a copy of self to use V_{k-1} for all updates. In iteration k, I used values from k - 1 to not use partially updated k values. 
    In runValueIteration, I skipped the terminal states because they don't have any value and then I computed Q-values for all other actions by using the
    self.computeQValueFromValues(state, action) method. 

Q2. I changed answerNoise in analysis.py from 0.2 to 0.002. This low noise means a 0.2% chance of failing to move forward.

Q3. 
3a Prefer the close exit (+1), risking the cliff (-10). answerDiscount = 0.3, answerNoise = 0, answerLivingReward = -1.0. Low discount makes distance less attractive, no noise agent takes shortest path to exit even if it is near cliff. 
3b Prefer the close exit (+1), but avoiding the cliff (-10) answerDiscount = 0.2, answerNoise = 0.2, answerLivingReward = 0. Low discount makes agent prefer exit, noise and negative living reward makes agent think risky path is too dangerous, so agent will take safer, longer route.
3c Prefer the distant exit (+10), risking the cliff (-10) answerDiscount = 0.9, answerNoise = 0, answerLivingReward = 0. high discount makes distance more attractive, no noise or living reward means agent takes shortest path risking life for cliff. 
3d Prefer the distant exit (+10), avoiding the cliff (-10) answerDiscount = 0.9, answerNoise = 0.4, answerLivingReward = 0. high discount prefers longer exit, high noise makes agent take top safe path.
3e Avoid both exits and the cliff (so an episode should never terminate) answerDiscount = 0.1, answerNoise = 0.3, answerLivingReward = 100. very high living reward which makes staying alive priority, even more valuable than any exit which is why noise is at 0 so it doesn't get stuck.

Q4. retrieved the current state of pacman, then select state cyclically using mod, skipping terminal states so that nothing happens in that iteration. Then I got all possible actions for that state and computed Q value. 

Q5. Prioritized sweeping method updates states which have most wrong values. I build a map of predecessors by checking actions in states, then added next state if it was there. Then, I computed Q values and put every non terminal state as a temp_state in a priority queue based on how far it was from its actual Q value. In each iteration after that, priority queue pops the worst state, update the value, and recheck predecessor, readding only if the error is greater than theta. 

Q6. implemented QLearningAgent methods and also used util.Counter() to store q values.

Q7. got list of legal actions, used flip coin to decide whether to explore or not and if it is exploring use random to get random action. 

Q8. not possible with epsilon of 0 and was alternating between state(1,1) and state (0,1). it goes back and forth because all the q values were at 0 to start with, agent has no knowledge that cross the bridge will lead to higher reward. 

Q9. reinforcement learning worked after 2000 training episodes and pacman got 100/100 wins because the QLearningAgent.getAction() was random using flipcoin. my computeActionFromQValue also used random to break ties. 

Q10. implemented approximate q-learning by having getQValue return a dot product of weights and features. 