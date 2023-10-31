#### COMA summary

- Counterfactual Multi-Agent Policy Gradient (COMA, 2017)

---

        # COMA - Credit Assignment Problem.  

        : MARL의 가장 큰 challenge 중에 하나는 Credit Assignment Problem.
        : Cooperative case에서 환경은 전체를 합산한 scalar 값의 global reward를 준다. 
        : 따라서 이 reward가 어느 agent의 기여로 인한 것인지 추론하기 위해서는 단일 agent보다 더 많은 고려를 해주어야한다.

        # 3 main ideas.

        1. centralized critic, decentralized actor.
            * Critic
                : joint action에 대해 credit assignment problem을 완화할 수 있음.
                : observation이 아닌 state를 이용하기 때문에 개별 agent보다 정확한 value 계산 가능.

        2. counterfactual baseline.
            Agent가 받은 Global Reward와 현재의 Action이 아닌 Default Action을 취했을 때 받을 reward를 비교.
            
        3. 1 network forward pass.
            Computing efficiency.

            



    



