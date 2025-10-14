# POLICY ITERATION ALGORITHM

## AIM
The aim of this experiment is to implement the Policy Iteration Algorithm in Reinforcement Learning to determine the optimal policy and corresponding value function for a given environment. Policy Iteration combines iterative policy evaluation and policy improvement steps to achieve convergence towards an optimal policy.

## PROBLEM STATEMENT
In Reinforcement Learning, the agent interacts with an environment modeled as a Markov Decision Process (MDP).
The challenge is to find an optimal policy that maximizes the long-term cumulative reward.
Policy Iteration addresses this by:

Evaluating the value of a given policy (Policy Evaluation).
Improving the policy based on the evaluated value function (Policy Improvement).
Repeating these steps until the policy converges to the optimal policy.

## POLICY ITERATION ALGORITHM
# STEP 1:
Initialization

Initialize an arbitrary policy π and value function V(s).

# STEP 2:
Policy Evaluation

For the current policy π, compute the value function V(s) for all states until convergence.

# STEP 3:
Policy Improvement

Update the policy by choosing actions that maximize the expected return using the current value function.
# STEP 4:
Check for Convergence

If the policy does not change (π′ = π), then the policy is optimal and the algorithm terminates.
Otherwise, repeat steps 2 and 3.

## POLICY IMPROVEMENT FUNCTION
### Name: M Sanjay
### Register Number: 212222240090
```
def policy_improvement(V, P, gamma=1.0):
    Q = np.zeros((len(P), len(P[0])), dtype=np.float64)

    for s in range(len(P)):
        for a in range(len(P[s])):
            for prob, next_state, reward, done in P[s][a]:
                Q[s][a] += prob * (reward + gamma * V[next_state] * (not done))

    new_pi = lambda s: {s: a for s, a in enumerate(np.argmax(Q, axis=1))}[s]

    return new_pi

```
## POLICY ITERATION FUNCTION
### Name: M Sanjay
### Register Number: 212222240090
```
def policy_iteration(P,gamma=1.0,theta=1e-10):
  random_actions=np.random.choice(tuple(P[0].keys()),len(P))
  pi=lambda s: {s:a for s, a in enumerate(random_actions)}[s]
  while True:
    old_pi={s: pi(s) for s in range(len(P))}
    V=policy_evaluation(pi,P,gamma,theta)
    pi=policy_improvement(V,P,gamma)
    if old_pi=={s:pi(s) for s in range(len(P))}:
      break
  return V,pi

```

## OUTPUT:
### 1. Policy, Value function and success rate for the Adversarial Policy
<img width="536" height="151" alt="image" src="https://github.com/user-attachments/assets/7368e742-ad1d-4501-bc2b-759d43eb592f" />
<img width="490" height="133" alt="image" src="https://github.com/user-attachments/assets/af687074-2962-40d6-886d-1e5c3b9a6cb4" />




### 2. Policy, Value function and success rate for the Improved Policy
<img width="497" height="145" alt="image" src="https://github.com/user-attachments/assets/323bce24-e211-4076-b353-746a67f9eb69" />
<img width="598" height="28" alt="image" src="https://github.com/user-attachments/assets/a5c68914-b53c-4934-8943-3fcd23264bee" />


### 3. Policy, Value function and success rate after policy iteration
<img width="741" height="144" alt="image" src="https://github.com/user-attachments/assets/8e2696bf-7fd2-4bfa-9f02-cb82570e855c" />
<img width="619" height="30" alt="image" src="https://github.com/user-attachments/assets/7eee594f-6eb5-43f6-b5e0-7ea2a38d8b72" />


## RESULT:
Therefore, policy iteration algorithm to find optimal policy by iteratively maximizing the value function is successfully implemented.
