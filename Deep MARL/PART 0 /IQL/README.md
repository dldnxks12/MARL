#### IQL summary

- Multi-Agent Reinforcement Learning : Independent vs Cooperative. (1990s)

---

        # IQL : Independent vs Cooperative. 

            : Q-Learning을 MARL로 확장한 가장 기본적인 형태. 
            : 각자의 Agent가 독립적인 Q function을 학습. 
            : Joint action에 대한 고려없이, 자신의 action만 고려.
            : But, 다른 agent로 부터의 정보를 이용. (state-space grows.) 

        # Key investigations.

            1. Given the same number of agents, will cooperative agents outperform independent agents who not communicate during learning?
            2. What is the price for that cooperation?

            * Indentifies 3 ways of cooperation.

                Communicating / Sharing  
                1) Sensory information 2) Episodic experinece 3) Learned knowledge.

        # Results.

            * - Goods - *

            : cooperative agents can learn faster and coverge sonner than independent agents, 
            via sharing learned policies or solution episodes.  
            : Cooperative agents can also broaden their sensation via mutual scouting, 
            and can handle joint tasks via sensing other partners. 

            * - Bads - *

            : Extra sensory information can hinder learning.
            : Shareing knowledge or episodes comes with a communication cost.
            : It can take a larger state space to learn cooperative behavior for joint task.

            * Future works / issues.
        
            1. sensation must be selective because the size of a state sapce can grows exponentially.
            2. information exchanging among agents incurs communication costs. 
                Can agents learn to communicate? 
                This learning task gets complicated when the content of communication can be instantaneous.
            3. Can homogeneous agents learn to have job division and to specialize differently?
            4. Can heterogeneous agents learn to cooperate? (scouting agent, blind hunter).

---

#### Key results from Experiments. 

        # test environemnt 
            : Catch-up Game with prey and hunter in 10 x 10 grid world. 

        * Case 1 : sharing sensation.
            : Sensory information from another agent is beneficial if the information is relevant and sufficient for learning.
            But, when the shared information is not sufficient or irrelevant?
                -> hinders learning. 

        * Case 2 : sharing episode and policy.
            ** sharing policy
            1. use the same policy.
                : 하나의 policy를 여러 agent가 본인의 상황에 맞게 update. 
                -> 즉, agent가 받아들이는 모든 정보를 공유하여 policy가 update.
            2. exchange their indivisual policy at various frequencies.
                agent들이 같은 task를 해도 다른 영역을 탐색하면 decision policy가 학습 과정에서 다를 수 있음.
                : agent들이 각자의 policy를 갖되, 주기적으로 그들의 policy들을 평균 내서 사용.
                : same policy의 경우와 달리 policy 동기화를 상황에 맞추어, 또는 입맛에 맞추어 다른 agent의 policy를 가져다 쓸 수 있음.
                
            
            ** sharing episode. 
            1. exchange among peer hunters. 
            2. exchange between peer and expert hunters. 
                -> novices can learn much quickly from experts.

            : sharing polices and episodes speed-up learning.


        * Case 3 : joint task.
            : cooperative agents who sense their partners or communicate their sensations
            with each other can outperform the independent agents.


        