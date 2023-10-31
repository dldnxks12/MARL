### PART 0 : Background

#### 1. Multi-Agent Settings

        G=<S,U,P,r,Z,O,n,γ>

            S : agent가 위치한 state에 대한 전체 집합.
            U : 각 agent가 취할 수 있는 action에 대한 전체 집합.
            P : 한 state에서 joint action u에 의해 다음 state가 될 확률 (transition kernel).
            r : reward.
            Z : observation 전체 집합.
            O : observation function. O(s, a) : S x A -> Z , where 'a' indicates agent.
            n : Agent 수.
            γ : discount factor.
             

#### 2. Centralized vs Decentralized

        Centralized Control   : 전체를 총괄하는 하나의 Agent를 생성 (centralized controller).
            - joint action space를 사용하므로, action space의 exponential한 증가.
            - local observation 상황에서의 적용이 불가능. 

        Decentralized Control : Agent 각자 local policy를 사용.
            - action space에 대한 단점 극복 가능. 

#### 3. Value-based MARL

        1. Independent Q-Learning (IQL) : Q-Learning을 MARL로 확장한 형태.
        2. IQL + DQN : DQN의 Q-Learning을 IQL로 하여 MARL로 확장.
        3. DRQN : POMDP 환경에 대한 하나의 해결책 제시

#### 4. Policy-based MARL 

        1. Independent Actor-Critic (IAC) : IQL과 함께 agent가 주변 환경을 static하게 여기는 특성. 
        - MARL은 일반적으로 non-stationary환경. 이를 그냥 static한 것으로 여김. (이론적인 수렴에는 문제가 있지만, 실제로는 잘 동작)
        - IQL, IAC는 naive learning의 대표적인 방법. 
        
