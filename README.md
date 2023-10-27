#### MARL Survey

- Multi-Agent Reinforcement Learning : A Selective overview of Theories and Algorithsm

---
- Abstract

      MARL?
      : Reinforcement Learning with includes more than 2 agents.
      
      # FrameWorks
        1. Markov Games
        2. Extensive-Form Games
    
      # Task types
        1. Fully Cooperative
        2. Fully Competitive
        3. Mixed Setting 
 
---

- Introduction
  
      Solving MARL problem?
      : MARL addresses the sequential decision-making problem of multiple agents that operates in a common env,
      each of which aims to optimize its own long-term return by interacting with the env and other agents.


- Task types

      # Cooperative setting 
      : multiple agents collaborate to optimize a common long-term return
      
      # Competitive setting
      : the return of agents usually sum up to zero.
      
      # The mixed setting
      : involves both cooperative and competitive agents, with general-sum returns 

---

- Background : Single Agent (Fully observable / No delay) 

      By Markovian property, the optimal polic can be obtained by dynamic programming 
        - Value Iteration
        - Policy Iteration
          
      But, VI, PI requires the knowledge of model (transition kernal, reward function)
      Then, learning the policy without knowing the model? Learns the policy from experiences!
        - Value Based  
        - Policy Based 

          *Value Based  
            - Monte Carlo : SARSA, MCTS(UCB1)   
            - Temporal Difference : Q-Learning, DQN 
    
          *Policy Based
            - REINFORCE, A2C
            - DDPG, TD3
            - TRPO, PPO 
            - SAC 

---

- Background : Multi Agent
      
      Both the evolution of the system state and the reward received by each agent are influenced by the joint actions.
      Each agent has its own long-term reward to optimize, which becomes a function of policies of all other agents.

      # Frameworks
      - Markov Games (MDP)
      - Extensive-Form Games (POMDP)
    
      * ---------------- Markov Games ---------------- *  

      The most common solution concept : Nash Equilibrium (NE)
      - NE always exists for finite-space infinite-horizon discounted MG. (May not be unique.)
      

      # Task types
      1. Cooperative Setting (Markov Teams / Team Markov Games)

      - Common reward  
      : all agents share a common reward function. R1 = R2 ... = R.
      V, Q function are identical to all agents, which enables the single-agent RL algorithms to be applied, 
      if all agents are coordinated as one decision maker.

      - Team-average reward 
      : Agents are allowed to have different reward functions, which may be kept private to each agent, 
      while the goal for cooperation is to optimize the long-term reward, corresponding to the average reward.
      This allows more heterogeneity among agents, and perserves privany, and facilitates the development of 
      'decentralized' MARL algorithms.


      2. Competitive Setting 

      - Zero-Sum Markov Games 
      : The reward of one agent is exactly the loss of the other. 


      3. Mixed Setting 

      - General-Sum Makov Games
      : No restriction is imposed on the goal and relationship among agents.
      Each agent is self-interested, whose reward may be conflicting with others'.
        

      * ---------------- Extensive-Form Games ---------------- *

      Markov Games can only handle the fully observed case. (Need perfect information on the systems.)      
      Then what aboutn imperfect information? Another framework named 'Extensive-Form Games' can hand it!
      That is, Extensive-Form Games can handle imperfect information for multi-agent decision-making.

      - Imperfect information in extensive-form games? 
      : the imperfect information of an extensive-form games is reflected by the fact that
      agent cannot distinguish between histories in the same information state 's'. 

          * information state S?
          : S is the partition of H. Histories in the same information states are indistinguishable to the agent. 
      
      - Perfect recall
      : We assume throughout that the game features 'perfect recall', which implies that each agent
      remembers the sequence of the information states and actions that have led to its current information state.

      By Kuhn's theorem, under this assumption, to find the set of NE, it suffices to restrict the derivation 
      to the set of behavioral policies which map each information set s to a probability distirubtion over A(s).  

      * See the equations of paper  
        1. reach probability of h under π.
        2. reach probability of s under π.
        3. the expected utility of agent i.
        4. ε-Nash equilibrium (naive NE, when ε = 0)

      # Task types
      Extensive-Form games are usually used to model 'non-cooperative setting'.
    
      1. Competitive Setting
      - Zero-sum / Constant-sum utility in competitive setting.

      2. Mixed Setting
      - General-sum utility in the mixed setting. 

      + A perfect information game. 
        - |s| = 1
      
      + An imperfect information game.
        - |s| > 1
        : the information state s used for decision-making represents more than one possible history,
        and the agent cannnot distinguish between them.

      ** Among these, 'zero-sum imperfect information setting' is the main focus.
    

---

- Challenges in MARL
    
      1. Non-unique Learning Goals
      2. Non-stationary issue
      3. Scalability issue (combinatorial nature)
      4. Various Information Structure (who knows what)

---
  



