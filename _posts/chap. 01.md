# 1-1 강화학습

강화학습이란 주어진 상황에서 어떠한 행동을 취할지를 학습해 최대의 보상(또는 이득)을 취할 수 있는 optiaml policy를 찾아내는 문제이다. 

이때 학습자(agent)는 어떤 행동을 취할지에 대해 어떠한 지침도 받지않고(지도학습과 달리) 오로지 시행착오를 통해 최대의 보상을 가져다주는 행동을 찾아내야 한다.

강화학습은 다른 머신러닝 분야들 지도학습,비지도학습과는 다른 성격을 갖는다. 지도 학습은 올바르게 학습을 하는 지침 (label)데이터가 포함되어 있다. 비지도 학습은 지침이 없는 데이터 셋 안에서 숨겨진 구조를 찾는다는 점에서 강화 학습이 비지도 학습의 한 종류로 생각할 수도있으나 강화학습의 목표는 보상을 최대로 만들기 위해 노력할 뿐 숨겨진 구조를 찾으려는 것은 아니다. 물론 숨겨진 구조를 찾는 것이 강화학습의 보상을 늘리는데 도움을 주긴 하지만 그것만으론 보상을 최대로 만들기엔 부족하다.

또한 다른 학습과는 달리 강화학습은 **탐험(exploration)**과 **활용(exploitaion)**이라는 개념이 추가된다. 학습자는 좋은 보상을 얻기위해 과거의 기억들을 다시 끄집어 활용하는 활용,그리고 여러 경우를 탐색하며 어느 값이 더 좋은지를 찾아내기위해 탐험을 사용한다.

강화학습의 또 다른 핵심은 불확실한 주변환경과 상호작용하는 목표 지향적인 학습자에 대한 모든 문제를 분명하게 고려한다는 점이다.이는 다른 문제들에서 여러 하위문제를 하나의 커다란 문제로 병합하는 방법을 제시하지 않은채 하위문제들만을 고려하는 다른 많은 방법과 구분되는 특성이다.

강화학습은 상호작용을 하는 완전하고 목표 지향적인 학습자(agent)를 처음부터 고려한 상태로 시작한다는 점에서 다른 학습법과는 정 반대의 접근법을 취한다. 모든 강화학습 학습자는 분명한 목표가 있고 주변환경의 여러 측면글 감지해 그 환경에 영향을 주기 위한 행동을 선택할 수 있다.더욱이, 학습자는 자신이 마주한 환경이 불확실하더라도 학습을 해야한다는 사실을 인지한 상태로 학습을 시작한다. 

이러 저러한 이유로 강화학습은 탐색과 학습같은 일반적인 원리에 기반한 방법을'약한 학습'이라고 인식한 반면 특정 지식에 기반한 방법을'강한 학습'이라고 생각했지만 지배적인 생각은 아니다.결과적으로 이러한 생각은 성급하다. 이러한 생각은 일반적인 원리를 발견하기 위해 충분히 노력해 보기도 전에 일반적인 방법은 존재하지 않을 것이라고 단정 지어버렸다.

현대 인공지능 연구의 상당수는 학습과 탐색, 의사결정의 일반 원리를 찾으려고 노력한다. 이러한 원리를 찾기위해 얼마나 더 먼 길을 가야 할 지는 모르지만, 좀 더 단순하고 포괄적인 일반 원리를 찾기 위한 여정에서 강화학습은 분명 거쳐가야 할 지점이다.

# 1-2 예제

강화학습을 적용하는 예제를 두가지 살펴보자



숙련된 체스 선수가 말을 옮길 때 어느 위치로 말을 옮기는 것이 좋을지는 상대의 대응과 그에 대한 재대응을 예상하는 계획, 그리고 즉각적이고 직관적인 판단을 통해 결정된다.

새끼 가젤은 태어난 지 몇 분 지나지 않아 어렵게 혼자 힘으로 일어서고, 30분 후에는 시속 30km의 속도로 달릴 수 있다. 



위의 두 예제를 살펴보면 매우 기본적인 특징을 공유한다는 것을 알 수 있다. 두 예제는 학습자와 그를 둘러싼 주변 환경 사이의 상호작용(interaction)을 다루고 있다. 주변환경에는 불확실한(uncertainty)요소들이 있지만, 학습자는 목표(goal)을 이루기 위한 방법을 모색한다.

학습자는 자신의 행동이 환경의 미래모습(체스말을 옮기는 상황,가젤이 한번 걷는상황)에 영향을 미치고, 결국 미래에 자신이 취할수 있는 행동과 기회에 영향을 줄 수 있는 권리를 갖는다(미래가 자신의 행동에 영향을 받아 결정된다.)

하지만 모든 상황을 정확히 예측 할 수는 없다. 따라서 학습자는 주변환경을 자주 모니터링하고 적절한 대응을 해야한다. (학습자의 행동에 따라 주변환경이 실시간으로 변화하기 때문에)

위와 같은 예제에서 학습자는 경험을 바탕으로 행동의 능력을 키우게 된다. 이 과정에서 학습자가 행동을 결정하는 데에는 주변환경과의 상호작용이 필수적이다.



# 1-3 강화학습의 구성 요소

학습자(agent)와 주변환경(enviroment)를 제외하고 강화학습에는 네가지 중요한 구성요소가 있다.

1. <em>정책</em>
2. <em>보상신호</em>
3. <em>가치 함수</em>
4. <em>모델</em>



### 정책(policy)

정책은 특정 시점에서 학습자가 취하는 행동을 정의한다. 이 정책은 간단한 함수나 look up table로 구현될 수도 있고 더욱 복잡한 경우에는 탐색 과정에 필요한 방대한 양의 계산을 포함할 수도있다. 정책 그 자체만으로도 행동을 결정 할 수 있다는 점에서 정책은 강화학습 학습자에게 있어 핵심이 되는 부분이다.



### 보상신호(reward)

학습자는 매 시간마다 주변환경에 따라  보상을 하나의 숫자(보상신호)로 받게된다. 학습자의 유일한 목표는 장기간에 걸쳐 학습자가 획득하게 되는 보상의 총합을 최대로 만드는것이다.따라서 보상신호는 사용자가 한 행동이 좋은것인지 나쁜것인지 판단하는 지표가 된다. 보상신호는 학습자가 정책을 바꾸는데 주된 원인이 된다. 정책이 적은 보상을 가지게 된다면 다음에 유사한 상황에서는 다른 선택을 하도록 정책을 바꿀 수 있다.

일반적으로 보상신호는 호나경의 상태와 취해진 행동에 대해 확률적으로 그 값이 결정되는 확률론적(stochastic)함수가 될 수도 있다.



### 가치 함수(value)

보상신호가 무엇이 좋은가를 즉각적으로 알려주는 반면 가치함수는 장기적 관점에서 무엇이 좋은가를 알려준다. 간단히 말해 특정상태의 가치는 그 상태의 시작점에서부터 일정 시간동안 학습자가 기대할 수 있는 보상의 총량이다. 보상신호는 어떤 순간의 주변환경의 상태에 따른 점수를 나타낸다면 가치는 특정 시점 이후의 상태와 그 상태에 포함된 장점을 고려해 **장기적 관점(long term)** 으로 평가한 상태의 장점이라고 할 수 있다. 만약 어떤 상태의 매 순간 보상은 적지만 최종적으로 큰 보상을 받게된다면 그 상태는 높은 가치를 가지게 된다. 

어떤 의미에서 가치함수는 보상에 대한 예측이므로 부수적인 점수이다. 보상없이는 가치가 있을 수 없고 가치를 평가하는것도 오로지 보상을 더 많이 얻기 위해서 이다. 하지만 정책의 판단으로 많이 사용되는것은 가치이다. 이렇게 해야 가치가 높은것을 선택하는것이 장기적으로 큰 이득이다. 하지만 보상을 결정하는것 보다 가치의 크기를 결정하는것이 훨씬 힘들다. 가치의 크기를 어떻게 결정하게되는지가 강화학습의 핵심이다.



### 모델(model)

환경 모델은 환경의 변화를 모사 한다. 일반적으로는 환경이 어떻게 변화해 갈지를 추정할 수 있게 해준다. 예를들면 환경 모델은 현재 상태와 그에 따라 취해지는 행동으로부터 다음 상태와 보상을 예측한다. 모델은 **계획(planning)**을 위해  사용되는데 계획이란 미래의 상황을 실제로 경험하기 전에 가능성만 고려하여 일련의 행동을 결정하는 방법을 의미한다. 

모델과 계획윽 사용하여 강화학습의 문제를 해결하는 방법을 **모델기반(model based)**방법이라고 한다 

이와 반대로 학습자가 시행착오를 통해 학습하는 방법은 **모델이 없는(model-free)**이라고 한다. 

# 1-4한계와 범위

강화학습은 **상태(state)**라는 개념에 크게 의존하는데 상태라는 것은 정책과 가치함수의 입력이 되기도 하고 모델의 입력과 출력이 되기도 한다. 비 공식적으로 상태를 정의하자면 특정 시간에 어떤 모습을 하고있는지 학습자에게 전달하는 정보 라고 정의할 수 잇다.따라서 학습자는 이 상태 정보로 부터 학습자가 취해야 할 행동을 결정하는것 이다.

이 책에서 다루는 대부분의 강화학습 방법은 가치함수를 추정하기 위한것이다.하지만 강화학습이 반드시 가치함수를 추정해야만 풀 수 있는것은 아니다. 예를들어 유전자 알고리즘(genetic algorithm),유전자 프로그래밍(genetic programming),모의 담금질(similated annealing)같은 최적화 방법은 가치함수를 추정하지 않는다. 

위의 알고리즘들은 환경과 오랜시간동안 불연속적 시간간격으로 상호작용하는 다수의 정적 정책(static politcy)를 적용한다. 가장 큰 보상을 얻는 정책과 그것의 무작위 변형이 다음세대의 정책으로 전달되는 일련의 과정을 거친다. 이 방법을 생물이 진화하는것과 비슷하다 하여 **진화적(evolutionary)**방법이라고 부르는데,정책의 갯수가 충분히 적거나 좋은 정책을 쉽게 찾을수 있도록 구조화 된 상황이거나 시간이 충분한 경우 이러한 방법이 효과적이다.



하지만 이러한 학습은 개별 행동의 상호작용이 갖는 세부사항을 알기 힘들다. 진화적 방법들은 상태가 주어졌을때의 행동이 새로운 상태를 만드는 점을 고려하지 않고 작동한다.

# 1-5 예제:틱택토

익숙한 게임인 틱택토를 하는 상황을 고려해보자. 이 문제는 아주 간단한 문제지만 전통적인 방법으로는 쉽게 풀리지 않는다. 미니맥스 방법은 상대방이 특정한 방법으로 게임을 한다는 가정을 하기에 올바른 해결책은 아니다.

동적 프로그래밍 같은 순차적 결정 문제에 대한 전통적 최적화 방법은 어떤 상태방과 게임을 하더라도 최적의 해결책을 게산할 수는 있지만, 이 때 상대방에 대한 완벽한 정보가 필요하다. 

결국 최선의 방법은 먼저 상대방에 행동에 대한 모델을 어느정도 수치까지 학습하고 이 근사적 모델과 동적 프로그래밍을 적용하여 최적의 해결책을 계산하는것이다. 결국 이것은 강화학습의 몇몇 방법과 크게 다르지 않다. 

이 문제에 진화적 방법을 적용한다면 게임 참여자는 가능한 정책들을 직접 탐색하여 상대방을 이길 확률이 가장 높은 것을 찾으려고 할 것이다. 여기서의 정책이란  게임참여자에게 게임의 모든상황, 즉 게임판 위의 모든 X와 O의 조합에서 어떠한 선택을 해야하는지 알려주는 규칙이다. 

이는 상대방과 몇 차례 게임을 함으로써 얻을 수 있다. 이러한 확률계산을 통해 다음번에 어떤 선택을 할지 알 수 있다.이러한 진화적 방법은 정책들이 연속적으로 펼쳐진 언덕을 오르며 정책을 평가하고 더 향상된 정책을 찾아간다.

가치함수를 이용한 방법은 게임에 나타날 수 있는 모든 상태에 대해 숫자를 부여해 숫자표를 만든다. 각 숫자는 해당 상태에서 게임 참여자가 승리할 확률에 대한 가장 최신의 추정값이다. 이 추정값을 **가치(value)**로 생각 하면 이제 전체표는 학습된 가치표가 된다. 상태 A가 B보다 승리할 확률이 크다면 A가 B보다 높은 가치를 가진다. 또는 더 낫다고 평가한다. 

틱택토 게임에서 X를 놓는 플레이어가 X를 3개 놓으면 승리하기 때문에 확률은 1이 된다.반대의 경우 X인 플레이어의 상태가 O가 3개인 상황이나 게임판이 다 채워졌다면 승리할 확률이 0이 된다. 

모든 확률을 0.5 즉 승리확률을 50%라고 설정하고 게임을 하는 상황을 보자

상대방과 여러번 게임을 진행하면서 가치표에 있는 값을 확인해 승리확률을 최대로 하는 값을 탐욕적으로 선택한다. 하지만 간혹 X를 표시할 위치를 랜덤하게 선택하기도 하는데 이는 랜덤하게 선택하지 않았다면 하지않을 상태또한 학습하기 위함이다. 이러한 선택을 **탐험적(exporatory)** 선택이라고 한다.

게임 하는동안 참여자는 상태의 확률을 계속해서 변화시킨다. 각각의 선택이후 결정될 상태의 가치를 선택이전의 상태에**보강(backup)**하는 방법으로 채우게 된다. 즉 이전상태의 현재가치가 나중 상태의 가치에 가까워지도록 그래서 장기적으로 봤을때의 가치를 가질 수 있도록 변경된다.이때 이전상태를 $S_t$라고 하고 선택 이후의 상태를 $S_{t+1}$라고 한다면 $S_t$의 가치 $V(s_t)$를 갱신하는 표현식은 다음과 같이 된다.

## $V(s_t) \larr  V(s_t)+\alpha[V(s_{t+1})-V(s_t)]$

이때 $\alpha$는 **시간 간격 파라미터(step-size parameter)**라고 불리는 작은양의 값으로서, 학습 속도에 영향을 준다. 

이 갱신 규칙은 **시간차 학습(tempotal-difference learning , TD)**방법의 일종이다. 갱신 과정의 변화량이 두 연속적인 시각의 추정값 차이

#### $V(s_{t+1})-V(s_t)$ 

에 의해 계산되기 때문에 시간차 학습으로 불린다. 

위의 강화학습 방법은 이 문제에 꽤 적합하다. 예를들어 시간 간격 파라미터가 시간이 지남에 따라 적절히 줄어든다는 것은 이 방법을 통해 숫자 표의 확률값이 각각의  상태로부터 승리할 확률을 참값으로 수렴한다는것을 의미한다. 

또한 진화적 방법과 가치함수를 학습하는 방법 사이의 차이점도 설명할 수 있게 된다. 정책을 평가하기 위해 진화적 방법은 정책을 고정한 채로 상대방과 많은 게임을 시도하거나 상대방의 모델을 이용해 수많은 게임을 시뮬레이션 해본다. 승리의 빈도수는 그 정책으로 승리할 확률에 대해 편차없는(unbiased)추정값을 의미하며, 다음 정책 선택의 지침이된다. 하지만 모든 정책의 수정은 많은 게임을 수행한 후에야 이루어지고 오로지 게임의 최종 결과만을 사용하게된다. 즉 중간의 과정을 생각하지 않게된다. 예를들어 게임 참여자가 승리하면 취했던 모든 행동들이 좋은값으로 신뢰를 받는다. 반면 가치함수를 이용하는 방법은 개별적인 상태를 평가 할 수 있게된다. 결국 진화적 알고리즘이나 가치 함수를 이용하는 방법 모두 정책을 탐색하지만 가치함수는 게임 중간에 발생한 정보를 활용할 수 있는 이점이 있다.

위의 예제를 통해 우리는 강화학습의 몇가지 핵심 특정을 설명할 수 있다.

첫째 강화학습은 주변 환경과 상호작용하며 학습하는것을 강조한다.틱택토의 경우 주변환경은 상대방이다.

둘째 강화학습에는 확실한 목표가 있고 올바른 행동을 위해 학습자가 선택한 행동의 지연된 효과를 고려하는 계획 또는 에지가 필요하다.미래의 정보를 통해 학습하는것이 상대방을 예측하는 모델이나 가능한 상태의 탐색 없이도 계획과 예지의 효과를 낼 수 있는것이 강화학습의 놀라운 특징이다.

틱택토가 너무 간단해 복잡한 문제에 적용될 때에 많은 한계를 드러낼것 같은 인상을 주지만 실제로 강화학습이 가지는 한계는 그보다 적다.

틱택토는 두명이 하는게임이지만 강화학습은 외부로부터 작용이 없는 즉 '자연을 상대로 한 게임'의 경우에도 적용할 수 있다. 또한 틱택토처럼 마지막 에피소드에서만 보상이 주어지는 문제 뿐만아니라 무한히 계속되고 다양한 크기의 보상이 언제든지 주어지는 경우에도 적용될 수 있다.

강화학습은 틱택토 게임처럼 이산적인(descrete)시간 간격으로 분해되지 않는 문제에도 적용할 수 있다.

틱택토 게임은 상태의 갯수도 적고 유한하지만 상태집합이 매우 큰, 심지어 무한한 경우에도 적용될 수 있다. 예를들어, 게리 테사우로는 위의 설명한 알고리즘을 인공 신경망과 결합해 대략 $10^{20}$개의 상태를 갖는 백게먼으 학습하게 했다. 이 경우에 상태가 너무 많기에 일부분만 경험할 수있었지만 이전의 어떤 프로그램보다 게임을 훨씬 더 잘하도록 학습되었고 결국에는 인간 세계 챔피언보다 더 잘했다. 인공신경망을 결합함으로써 새로운 상태를 접했을대 이전에 경험했던 유사한 상태로부터 저장한 정보를 기반으로 인공신경망으로 부터 행동을 결정했다.

틱택토 게임은 규칙이외의 사전 정보 없이 학습이 시작되지만 강화학습이 지능과 학습에 대해 아무생각이 없는것은 아니다 오히려 여러 사전정보를 강화학습에 녹여들게 할 수 있다.마지막으로 틱택토 게임 참여자는 앞을 내다보고 자신의 선택에 따른 상태의 결과를 알 수 있었다. 이렇게 하려면 실제로 취하지 않을 선택에 대해 환경이 어떻게 변할지를 에측할 수 있게 해 주는 게임의 모델이 있어야 한다.

많은 문제들이 이와같은 모델을 가지고 있지만 어떤 문제에는 행동의 결과를 짧은 기간동안(보상)예측하는 모델도 결여되어 있다. 강화학습에는 예측모델이 필요없기 때문에 어떠한 문제에도 강화학습을 적용 할 수 있다.모델이 있으면 사용하면 되고 없으면 없는대로 하면 되는 것이다.

반면 어떠한 종류의 모델도 사용하지 않는 강화학습 방법이 있다.모델 없는(model-free)시스템은 심지어 하나의 행동이 환경을 어떻게 변경시킬지를 생각할 능력도 없다.이러한 점에서 틱택토 게임 참여자는 상대방에 대한 어떠한 종류의 모델도 갖고 있지 않다. 모델이 도움이 되려면 충분히 정확한 모델이어야 하기때문에, 충분히 정확한 모델을 만드는 어려움이 문제해결의 걸림돌이 되는 상황에서는 복잡한 방법 보다는 모델이 없는 방법이 더 도움이 될 수 있다.



### 핵심 단어:

정책(policy)

가치(value)

보상(reward)

모델이 없는 강화학습(model-free)

모델이 있는 강화학습(model based)

탐색(exploration)

활용(exploitaion)

시간간격 파라미터(step-size parameter)

시간차 학습(temporal-difference learning)

