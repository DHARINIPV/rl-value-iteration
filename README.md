# VALUE ITERATION ALGORITHM

## AIM
To implement and demonstrate value iteration in a simple reinforcement learning problem (likely a grid-based environment) to find the optimal policy and state-value function.

## PROBLEM STATEMENT
The task is to implement the Value Iteration algorithm to find the optimal policy and state-value function for an agent navigating a grid-based environment, with the goal of maximizing the probability of reaching a specified goal state and optimizing cumulative rewards.

## POLICY ITERATION ALGORITHM

The Policy Iteration algorithm is typically composed of the following steps:

Initialization: Initialize a random policy for the agent.
Policy Evaluation: Evaluate the policy by calculating the state-value function, which represents the expected return when following the current policy.
Policy Improvement: Update the policy by making it greedy with respect to the calculated state-value function, improving the decision at each state.
Convergence Check: Repeat the process until the policy converges (i.e., no further improvements can be made).

## VALUE ITERATION FUNCTION
### Name: Dharini PV
### Register Number: 212222240024
```python
def value_iteration(P, gamma=1.0, theta=1e-10):
    V = np.zeros(len(P), dtype=np.float64)
    while True:
      Q=np.zeros((len(P),len(P[0])),dtype=np.float64)
      for s in range(len(P)):
        for a in range(len(P[s])):
          for prob,next_state,reward,done in P[s][a]:
            Q[s][a]+=prob*(reward+gamma*V[next_state]*(not done))
      if np.max(np.abs(V-np.max(Q,axis=1)))<theta:
        break
      V=np.max(Q,axis=1)
    pi=lambda s:{s:a for s,a in enumerate(np.argmax(Q,axis=1))}[s]
    return V, pi
```
## OUTPUT:
Mention the optimal policy, optimal value function , success rate for the optimal policy.

## RESULT:

Write your result here
