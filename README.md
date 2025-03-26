# POLICY ITERATION ALGORITHM

## AIM

To develop a Python program to find the optimal policy for the given MDP using the policy iteration algorithm.



PROBLEM STATEMENT
The aim of this experiment is to find optimal policy for the mdp using policy iteration. Policy iteration includes policy evaluation and policy improvement where evaluation function is used to find optimal value function of each state and then improvement function is used to find best policy by comparing all the action value function as well as policy.



POLICY ITERATION ALGORITHM
Step1 : We are going to do policy evaluation of each state to get the state value function where the initial policy is defined randomly to the MDP.

Step2: Once we obtain convergence in the policy evaluation then implement policy improvement where we are going to find best optimal policy until the previous and current policy are same.



POLICY IMPROVEMENT FUNCTION
Name :SUDHARSAN S
Register Number : 212224040335
```
def policy_improvement(V, P, gamma=1.0):
    Q = np.zeros((len(P), len(P[0])), dtype=np.float64)
    # Write your code here to improve the given policy
    for s in range(len(P)):
      for a in range(len(P[s])):
        for prob,next_state,reward,done in P[s][a]:
          Q[s][a]+=prob*(reward+gamma*V[next_state]*(not done))
          new_pi=lambda s:{s:a for s, a in enumerate(np.argmax(Q,axis=1))}[s]
    return new_pi
```



POLICY ITERATION FUNCTION
Name : SUDHARSAN S
Register Number : 212224040335
```
def policy_iteration(P, gamma=1.0, theta=1e-10):
  random_actions=np.random.choice(tuple(P[0].keys()),len(P))
   pi = lambda s: {s:a for s, a in enumerate(random_actions)}[s]
   while True:
    old_pi = {s:pi(s) for s in range(len(P))}
    V = policy_evaluation(pi, P,gamma,theta)
    pi = policy_improvement(V,P,gamma)
    if old_pi == {s:pi(s) for s in range(len(P))}:
      break
   return V, pieration function
```


## OUTPUT:
### 1. Policy, Value function and success rate for the Adversarial Policy

![image](https://github.com/user-attachments/assets/4387ba25-ea8b-4a12-9917-20fba3448521)

![image](https://github.com/user-attachments/assets/9c7e54c8-35f6-4445-9641-255096ab06f7)

![image](https://github.com/user-attachments/assets/43f30da5-2be8-4073-8532-6c2da5dcdd72)


### 2. Policy, Value function and success rate for the Improved Policy

![image](https://github.com/user-attachments/assets/2c3e6610-f063-407c-98f3-d75d7d747b2b)

![image](https://github.com/user-attachments/assets/7c40dd4f-38fe-4a5c-93e7-ee0ecb66a22b)

![image](https://github.com/user-attachments/assets/ee13db1b-ebd1-4c11-ab55-33b563e8cb60)

### 3. Policy, Value function and success rate after policy iteration

![image](https://github.com/user-attachments/assets/fadab101-6b65-45c6-be1f-69e1b00bc680)

![image](https://github.com/user-attachments/assets/13142381-3514-4713-b6c6-b126d3053f76)

![image](https://github.com/user-attachments/assets/da497700-53fc-46ee-8f0a-2cfb74886bc1)



## RESULT:
Thus, The Python program to find the optimal policy for the given MDP using the policy iteration algorithm is successfully executed.
