#### IQL+DQN summary

- Multi-Agent Cooperation and Competition with Deep Reinforcement Learning (2015)
---

        # IQL+DQN
            
            : DQN과 IQL을 합친 framework.
            : 각자의 agent가 각각 동시에 Q-network를 학습.
            : 하지만 각 agent의 학습은 다른 agent에게 non-stationary environment를 만들어냄.
            : 즉, Markovian property violation을 야기하지만, 이를 단순히 stationary로 간주하고 수행.
            : 이론적으로 수렴성에는 문제가 있지만, practical하게 사용해봤을 때는 성능이 나쁘지 않음. 


        # Summary

            : 2개의 DQN agent를 이용하여 Pong Game 수행 (fully cooperative | fully competitive | mixed).
            : Decentralized learning of multi-agents in complex environments. 
            : state, reward는 joint action에 기반하여 변화.

                * Decentralized Learning 
                : no explicit information exchanges with each other. 
                : Each agent makes decisions based on its local observations, without any coordination and/or aggregatiopn of data.
                : The local observations that vary across agents may contain some global information.
                e.g., the joint actions of other agents, 

            : Non-stationary environment에 대한 convergence issue 무시. But, practically works.
            
        # Issue 

            : Overestimation - Double Q-Learning 등으로 해결 가능. 