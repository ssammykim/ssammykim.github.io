---
title:  "Facebook open source chatbot blog review"
date: May 02, 2020
categories:
  - review
tags:
  - NLP
  - open_source_chatbot
comments: true
published: true
excerpt_separator: "<!--more-->"
---

깃헙 블로그 만드느라 정신없었더니 저번엔 구글이 이번엔 페북이 또...🤦‍♀️ 외개인 분발해야겠다...(아자아자) 구글 미나도 놀라웠는데 페북이 이번에 SOTA 기냥 찍어주셨나 봄. 논문도 ~~급하게(?)~~ 읽고 있는 중인데 일단 블로그에 올라온 요약문 정리하면서(라기 보단 거의 그냥 읽는 수준) 본 것 나중에 참고용으로 포스팅. <!--more-->


이번 페북 오픈소스 챗봇은,
> The culmination of years of research in conversational AI, this is the first chatbot to blend a diverse set of conversational skills — including empathy, knowledge, and personality — together in one system.

**key ingredients**
- large-scale neural models (of course)
- ⭐️⭐️⭐️techniques for blending skills and detailed generation⭐️⭐️⭐️

blog: <https://ai.facebook.com/blog/state-of-the-art-open-source-chatbot>  
AI Facebook: <https://ai.facebook.com/>  
article: <https://arxiv.org/pdf/2004.13637.pdf>

<br>

# Blog Post 정리 내용
그냥 읽으면서 정리한 것이기 때문에 두서 없음 주의* (논문은 따로... ^^7)

> Conversation is an art that we practice every day

크흐... art 맞지... rgrg  

실제로 사람처럼 "대화"할 수 있다는 건 이런 걸 할 수 있다는 것과도 같음 
- sking and answering a wide range of questions,
- displaying knowledge,
- and being empathetic, personable, engaging, serious, or fun, as circumstances dictate.  

지금까지는... 이미 specialized, preprogrammed tasks, (정해진 경로에 따라 수행하기만 하면 되는 것들... 항공권 예약과 같은 것)에 대한 고도화 작업이 이루어 졌음...

> But truly intelligent, human-level AI systems must effortlessly understand the broader context of the conversation and how specific topics relate to each other.

= 는 자연스러운 대화 챗봇을 만들기 위해서 모든 사람들이 꿈꾸는 것이기도 함...  

그래서 페북이 준비한 Open-sourced Blender, the largest-ever open-domain chatbot
> This is the first time a chatbot has learned to blend several conversational skills — including the ability to assume a persona, discuss nearly any topic, and show empathy — in natural, 14-turn conversation flows.

(데모를 보긴 봤는데... 끊임없이 말을 하게 하는 듯ㅋㅋ 한국어가 아니라서 그렇게 와닿지 않는 느낌적인 느낌)

# Chatbot recipe: Scale, blending skills, and generation strategies
## Scale
- 다른 챗봇이랑 마찬가지로 large-scale training 고고
- 뉴럴넷이 겁나 커서 줄이는 기술 쓰고 해서 효율적으로 함 어쩌고 저쩌고 ㅇㅇ (이건 다른 챗봇들도 똑같이 신경써서 하는 거니까 패스)
- 이게 중요하다는 거 다들 안다. 하지만 좋은 대화를 만드는 데에 이것만 필요한 건 아님. 다른 것도 필요함 그게 페북이 말하려고 하는→ ✌️Blending skills✌️

## blending skills
> In fact, if not done carefully, it can make the model imitate poor or even toxic behavior.  

이게 잘 되지 않으면... 그냥 말 멍청하게 따라하기만 함...  

그래서 BST(Blended Skill Talk) ~~(BTS라고 읽을뻔)~~ consists of following skills 
- Engaging use of personality (PersonaChat)
- Engaging use of knowledge (Wizard of Wikipedia) 
- Display of empathy (Empathetic Dialogues) 
- Ability to blend all three seamlessly (BST)

이거 블랜딩하는 거 very 어.렵.다. *WHY?* 
- it must be able to switch between different tasks when appropriate 
  - 농담하다가 진지해지면 그것에 맞게 (알아차리고) 변경해야하니까 
  - 근데 쨌든 BST 모델로 파인 튜닝하니까 완전 쩔게? 됨ㅋㅋ;; 
  - (dramatic effect on human evaluations of the bot’s conversational ability) 그렇다고 합니다... 이 놈의 human evaluation은 믿을 수가 있어야지...🍒🍒

## Generation strategies (The choice of decoding algorithm)
~~잠깐 스쳐가는 외개인아가 '빙시나'의 추억(?)...ㅋㅋ~~  
모델을 트레이닝 하고 나면 보통 리서처들이 "to make sure conversational agents don’t repeat themselves or display other shortcomings" use a number of possible generation strategies, including 
- beam search 
- next token sampling 
- and n-gram blocking

> We find that the length of the agent’s utterances is important in achieving better results with human evaluators.<br>If they’re too short, the responses are dull and communicate a lack of interest

봇이 길게 말하는 거ㅎㅎㅎ... 제너레이션 측면에서 말했던 건 아니지만... 전반적인 디코딩 측면에서...(필요하다고 이야기 한 적이 있었음... 주절주절ㅋ) 아 물론 다음과 같은 문제도 있쥐

> if they’re too long, the chatbot seems to waffle and not listen.

결국 위와같은 Trade-off를 제어하기 위해 : tuning the minimum beam length gives important control over the “dull versus spicy” spectrum of responses.

근데 잠깐 논문의 예시를 보니까 자연스러운 길이라고 말할 수 있는지는 모르겠다는... ~~누가 말을 이렇게 맨날 꽉꽉채워 글자 제한 있는 트위터도 꽉꽉 안쓰...~~
 
## Putting our recipe to the test
Google Meena와 Pairwise human evaluation (약간 좀 못 믿겠는 결과...ㅋㅋ)

질문 항목 
 1. 누구랑 더 오래 대화하고 싶어?(showing engagingness) “Who would you prefer to talk to for a long conversation?” 
  - Facebook : 75%
  
 2. 누가 더 사람같아?(showing humanness) “Which speaker sounds more human?” 
  - Facebook : 65%

Human evaluation에서 드러난 blending skills and choosing a generation strategy 의 중요성
- 이것은 곧 nonrepetitive, detailed responses 생성을 의미하기도 함

`인간-인간`, `인간-Blender` 대화도 평가했는데, 데이터만 때려 박는다?고 해서 답은 아님ㅇㅇ..
- Blender fine-tuned w/BST 모델은 49% 선호
- 그냥 Public domain trained ver.은 36% 선호 

실제로 generation strategy fine-tuning 방법으로 쓰인 beam blocking and controlling for the minimum beam length 도 큰 영향을 미침
- minimum beam length constraint 제거시 모델 답변이 절반으로 짧아짐 : Performance 49% → 21%

물론 (실제 사람과 비교해서) 약점 여전히 있음
- Our latest model’s performance is nearly equal to human-level quality in this specific test setup.
- Though it’s rare, our best models still make mistakes, like contradiction or repetition, and can “hallucinate” knowledge


## 끝으로 페북이 하고 있는 것들
We’re also focused on ***building stronger classifiers to filter out harmful language in dialogues.*** 
- And we’ve seen preliminary success in studies to help mitigate gender bias in chatbots.

<br>

`기능-일상 블랜딩`도 중요하지만, `일상 대화 블랜딩` 자체도 엄청나게 어려운 테스크임은 분명하다. 전에 핑퐁 팀에 있을 때도 그렇고, 얼기설기인 것 처럼 보이지만 엄청나게 정교하게 작동하고 있는 사람의 언어 시스템을 모방한다는 건 정말 어려운 일인 것 같다. 그만큼 모델 성능에 영향을 미치는 모델 구조 그 자체나 데이터 선택도 어렵고 중요한 일이겠지. 그런 의미에서 크라우드 소싱도 ㅋㅋ 그냥 할 것이 생각보다(?) 아님 (조금만 울고...😭)... 쨌든 아직 논문을 다 읽어보진 못했지만, "hallucinate knowledge" 라는 것도 어떤 의미를 말하는 건지 제대로 봐야겠다. 일상 대화 기술과 외부 지식을 연동 시키는 일이 서비스 단에서는 매우 골치아픈 일이니까🤦‍♀️ . 두서없는 블로그 글과 두서없는 마무리란ㅋㅋㅋ 뿅.
