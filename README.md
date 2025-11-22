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
#### POLICY:
<img width="738" height="135" alt="image" src="https://github.com/user-attachments/assets/cd9aaad4-7bf4-42cb-97ae-08615f9fea70" />


#### STATE VALUE FUNCTION:
<img width="673" height="133" alt="image" src="https://github.com/user-attachments/assets/7c2c8da1-4939-4df4-8426-d58b8d82c974" />


#### SUCCESS:
<img width="595" height="43" alt="image" src="https://github.com/user-attachments/assets/43b99c97-ab5d-40d1-adda-fc1d26a5d3a9" />

### 2. Policy, Value function and success rate for the Improved Policy
#### POLICY:
<img width="539" height="136" alt="image" src="https://github.com/user-attachments/assets/0271e0fb-70d9-44b5-8621-0b7a5a0778ec" />


#### STATE VALUE FUNCTION:
<img width="504" height="133" alt="image" src="https://github.com/user-attachments/assets/12cd6259-a3cf-46fd-9ff8-cb19c4b42e98" />


#### SUCCESS:
<img width="648" height="28" alt="image" src="https://github.com/user-attachments/assets/59b46549-83bf-444b-8edc-bae7d0818690" />


<img width="413" height="33" alt="image" src="https://github.com/user-attachments/assets/ab6544c9-9a97-45e7-bd1f-d4b9c8cbd43d" />



### 3. Policy, Value function and success rate after policy iteration
#### POLICY:
<img width="804" height="133" alt="image" src="https://github.com/user-attachments/assets/66750855-732e-486a-8f97-9446dbb8796e" />


#### STATE VALUE FUNCTION:
<img width="879" height="119" alt="image" src="https://github.com/user-attachments/assets/9bb6ba80-3765-4ad6-92ec-0943cdf1696f" />


#### SUCCESS:
<img width="645" height="32" alt="image" src="https://github.com/user-attachments/assets/38439437-a5a5-4b4f-9ce5-9f7b1c44345e" />




## RESULT:
Thus the program to iterate the policy evaluation and policy improvement is executed successfully.
