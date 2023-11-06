#### COMA summary

- Counterfactual Multi-Agent Policy Gradient (COMA, 2017)

---

        # Credit Assignment Problem.  

        : MARL의 가장 큰 challenge 중에 하나는 Credit Assignment Problem.
        : Cooperative case에서 환경은 전체를 합산한 scalar 값의 global reward를 준다. 
        : 따라서 이 reward가 어느 agent의 기여로 인한 것인지 추론하기 위해서는 단일 agent보다 더 많은 고려를 해주어야한다.

---

- Abstract + Introduction

        1) joint space :
        Cooperative multi-agent system에서 일반적인 Single Agent RL 알고리즘을 사용하게 되면 굉장히 큰 joint space를 다루게 되기 때문에,
        에이전트 각자가 자신이 관측할 수 있는 정보만을 기반으로 행동을 결정할 수 있는, 즉 decentralized policy를 학습할 수 있는 새로운 방법이 필요하다.
        단순히 joint space의 크기로 인한 문제 뿐만 아니라, partially obervability, communication contraint 등으로 인해서도 decentralized policy learning이 필요하다.
        특정 상황에서는, 각 에이전트들의 학습 자체가 모두 독립적으로 일어나야하는 경우가 있는데, 일반적으로는 추가적인 state information이 이용가능하고, 에이전트 간의 통신이 자유로운, 시뮬레이터 상에서 학습이 진행되는 경우가 대부분이다.
        이런 centralized training of decentralized policies (decentralized policy들을 중앙에서 학습)가 2017년 당시 Multi-Agent planning에 가장 standard한 패러다임.

        2) credit assignment problem : 
        cooperative system에서는 일반적으로 joint action에 대한 global reward를 Return 받기 때문에 각각의 에이전트가 해당 global reward에 얼만큼 기여했는지 파악하기가 어렵다.
  
        위 두 가지 문제를 적절히 해결하기 위해 COMA라고 부르는 새로운 Multi-Agent Actor-Critic 방법을 제안한다.
  
        Answer 1)
                - COMA는 해당 system state에서 각 에이전트들의 joint action에 대한 Q-function을 estimate하기 위해 state information과 joint action에 대해 centralized critic을 학습한다.
                또한 각 에이전트들의 policy를 최적화시키기 위해 decentralized actor를 사용하고, 각 actor는 자신의 action-observation history만을 기반으로 행동을 결정한다.
  
        Answer 2)
                - Cooperative system에서의 credit assignment problem을 해결하기 위해 counterfactual baseline을 제안한다.
        
                이 방법은 global reward랑 다른 에이전트들의 행동을 고정시킨 채 특정 에이전트의 행동만 default action으로 바꾸었을 때 얻는 shaped global reward와의 차이를 비교해서,
                해당 에이전트의 행동이 global reward에 어떠한 기여를 하는 지를 알아보는 difference reward 개념에서 착안한 방법.

                이 방법은 credit assignment 문제에 대한 좋은 접근법이기는 하지만, 행동을 바꾸었을 때의 global reward를 또 받아봐야하기 때문에 simulator에 여러 번 접근해야한다는 단점과
                default action을 선택하는 기준이 불명확하다는 단점이 있다.
        
                COMA는 centralized Critic을 이용해서 현재 joint action에 대한 global return이랑, 다른 에이전트들의 행동을 모두 고정시킨 채 하나의 에이전트의 행동에 대한 marginalilze한 것은 비교하는
                agent-specific advantage-function을 구해서 이 문제를 해결한다. 
          
                - 또한, counterfactual baseline을 보다 효율적으로 계산하기 위한 방법으로 critic representation을 사용한다.
                한 번의 forward pass로 다른 모든 에이전트들의 행동에 대해서 특정 에이전트가 할 수 있는 모든 action에 대한 Q function을 계산한다. 
        
                
                - COMA를 StarCraft unit micro-management 벤치마크를 partially observable 상황으로 만들어 테스트하였다.
                - 결론적으로 COMA는 state가 fully observable힌 centralized control 환경에서보다 더 좋은 성능을 보여주었다.
                  

---

- Introduction



---

- Background

---

- proposed method

---

- Experiment

---

- Result

---

            



    



