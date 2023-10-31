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

      By Markovian property, the optimal policy can be obtained by dynamic programming 
        - Value Iteration (VI)
        - Policy Iteration (PI)
          
      But, VI, PI requires the knowledge of model (transition kernal, reward function)
      Then, learning the policy without knowing the model? Learns the policy from experiences!
        - Value Based  
        - Policy Based 

          *Value Based  
            - Monte Carlo : SARSA, MCTS(UCB1)   
            - Temporal Difference : Q-Learning, DQN 
    
          *Policy Based (Gradient Descent)
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
      This allows more heterogeneity among agents, and preserves privacy, and facilitates the development of 
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
      Then what about imperfect information? Another framework named 'Extensive-Form Games' can handle it!
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
    
      1. Non-unique Learning Goals issue.
      : The learning goals of MARL can be vague at times. The most common goal is the convergence to NE.
      This is a reasonable goal in game theory, under the assumption that the agents are all rational, and are
      capable of perfectly reasoning and infinte mutual modeling of agents. 
      However, with bounded rationality, the agents may only be able to perform finite mutual modeling. 
      So, convergence to NE may not be justifiable for practical MARL agents. 
     
      Convergence is the dominant performance criterion for MARL algorithms so far. 
      But, value-based MARL algorithms fail to converge to the stationary NE in general-sum MG.
      -> Cyclic equilibrium are proposed. (not convergence to any NE policy.) 


      2. Non-stationary issue.
      : Multiple agents usually learns concurrently, causing the env faced by each agent to be 'non-stationary'.
      The action, taken by one agent affects the reward of other agents, and the evolution of the state. 
      As a result, the learning agent is required to account for how the other agents behave and adapt 
      to the 'joint behavior'.

      This invalidates the *stationary assumption for establishing the convergence of single agent RL algorithms.
      And this precludes the direct use of mathematical tools for single-agent RL analysis in MARL. 

        * stationary Markovian Property 
        : The indivisual reward and current state depend only on the previous state and action taken.

      Theoretically, if the agent ignores this issue and optimizes its own policy assuming a stationary env, 
      the algirithms may fail to converge. (We call independant learner.)
      But practically, it works well. 


      3. Scalability issue (combinatorial nature of MARL.)
      : To handle non-stationary problems mentioned above, each agent may need to account for the joint action space, 
      whose dimension increases exponentially with the number of agents. 

      One possible remedy for this issue is to assume additionally the factorized structures 
      of either value or reward fucntions with regard to the action dependence.  


      4. Various Information Structure issue (who knows what).
      : Compared to the single-agent, the information structure of MARL is more involved at the training and execution.
      In the framework of Markov Games, it suffices to observe the instantaneous state s, in order for each agent to make decisions.
      On the other hand, for Extensive-Form Games, each agent may need to recall the history of past decisions, 
      under the common perfect recall assumption. 

      Furthermore, as self-interested agents, each agent cannot access either the policy or the rewards of the opponents,
      at most the action samples taken by them. This partial information aggravates the issues caused by non-stationarity.

      To mitigate this partial information issue, people assumes the existence of a 'central controller', that can 
      collect information such as joint actions, joint rewards, and joint observations.
      This is a popular learning scheme of 'centralized-learning-decentralized-execution'.
      
      - Cooperative Setting
      : this scheme greatly simplifies the analysis, allowing the use of tools for single agent RL analysis.
      
      - Non-Coorperative Setting
      : this scheme does not that simplify the analysis, as the learning goals of the agents are not aligned. 
  
      And such a central controller doe not exist in many cases. 
      As a consequence, a fully decentralized and a decentralized learning with networked agents are proposed.
      Independent learning is a special case of a fully decentralized learning. But for solving non-convergence issue in independent learning, 
      agents are usually allowed to share local info with their neighbors over a communication network. 


---
  
- MARL Algorithms with Theory


    : A selective review of MARL algorithms. And categorizes them according to the tasks to address.


1. Cooperative Setting
2. Competitive Setting
3. Mixed Setting


