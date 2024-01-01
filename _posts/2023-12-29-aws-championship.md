---
title: 왕중왕전! AWS Rookie Championship 후기 [AWS상 수상]
author: jaehyeonee
date: 2023-12-30 16:20:07 +0800
categories: [Blogging, 회고]
tags: [회고]
pin: true
math: true
mermaid: true
image:
  path: https://github.com/Jaehyeonee/codingTest-study/assets/92504386/d292a14a-6a2a-4477-a690-11d679c31e4e
  
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: Responsive rendering 
---

<img width="488" alt="스크린샷 2024-01-02 오전 12 39 47" src="https://github.com/Jaehyeonee/codingTest-study/assets/92504386/bc779fb6-be0a-49e0-931a-a2e7db11b0c1">

드디어 기다리던 AWS Rookie Championship이 개최되었다.

__AWS Rookie Championship__ 은,<br>
2023년 AWS Univ Program에 참여한 팀 중 선발된 14개의 우수팀이 경쟁하는 Pitching 대회이다.

![IMG_8897](https://github.com/Jaehyeonee/codingTest-study/assets/92504386/11cad9e4-54f0-4849-9aef-46e0d619ff1c)

왕중왕전이라니 이름부터가 설레는 대회이다.<br><br>
감사하게도 우리 팀은 __뚜기두밥__ 이라는 팀명으로 __2023 숙명 X aws X streamlit X 오뚜기 Hakathon__ 에서 1등을 수상해, 본 대회에 참가할 기회를 얻었다. 

<img width="300" alt="스크린샷 2024-01-02 오전 12 39 47" src="https://github.com/Jaehyeonee/codingTest-study/assets/92504386/9720f0ea-bc54-4334-88a6-78b4933713d5">



<h6>(항상 이런 설레는 대회를 개최해주시는 AWS...너무 감사하다...🥰)</h6>
<br>

우리 팀의 주제는 이전 회고에서 작성했듯이<br>
__'오뚜기 몰 활성화를 위한 캐치프라이즈 생성 서비스'__ 였다. <br>


하지만 챔피온십을 준비하며, 서비스 도메인의 확장성을 위해 <br> <span style="color:blue">__'오뚜기 몰'에서 ➡️ '쇼핑 몰'로 서비스 범위를 넓혔다.__ </span>
<br>

최종 뚜기두밥 팀의 주제는,

>'쇼핑몰 리뷰 데이터를 활용한 캐치프레이즈 자동 생성 및 모니터링 시스템'이 되었다.
{: .prompt-tip }


Championship인만큼, 기존 streamlit 프로토타입 형태에서 발전된 개발을 진행했다.

__기존 프로토타입에서는,__
- BERT를 활용한 keyword 추출 및 긍/부정 Sentimental 분석을 통한 라벨링
- 부정 리뷰 데이터 수집
- 생성 AI를 활용한 긍정 리뷰 기반의 홍보 캐치프레이즈 작성 자동화
- Amazon SNS로 고객 리뷰 피드백 컨택
<br>총 4가지의 서비스를 개발하고 데모에 적용했다.



<br>

__디벨롭 시킨 결과물에는,__

실제로 홍보 및 연구팀 담당자가 Slack을 활용해 활발한 피드백을 받고, streamlit으로 모니터링 할 수 있도록 추가했다.  

<img width="748" alt="IMG_8894" src="https://github.com/Jaehyeonee/codingTest-study/assets/92504386/9bb9d548-4665-4573-a4c8-1fe70b6086c6">

### 1. 홍보팀 담당자는 Slack으로 전달된 최다 부정 리뷰에 대해 [수락/반려]를 선택하여, 개선이 필요한 부정 리뷰를 연구팀으로 전달 할 수 있다.
   <img width="727" alt="스크린샷 2024-01-02 오전 1 44 02" src="https://github.com/Jaehyeonee/codingTest-study/assets/92504386/5ee16574-4167-42c3-8a34-662d51817036">
   
   
### 2. 연구 개발팀은 Slack에 전달된 부정 리뷰를 기반으로, 채널에서 봇을 이용해 생성 AI에게 발전 방향성을 도움받을 수 있다.
<img width="745" alt="스크린샷 2024-01-02 오전 1 41 54" src="https://github.com/Jaehyeonee/codingTest-study/assets/92504386/9ad0925c-2041-4012-bd84-ad23ffb38403">
![IMG_8893](https://github.com/Jaehyeonee/codingTest-study/assets/92504386/c6a26f79-a130-4817-8461-ad821d08391e)

### 3. 실제 개선된 제품이 전달되면,생성 AI는 streamlit에서 개선점을 기반으로 홍보 캐치프레이즈를 생성하여 홍보팀 담당자가 홍보 문구를 피드백 할 수 있도록 한다.
   <img width="627" alt="스크린샷 2024-01-02 오전 1 45 40" src="https://github.com/Jaehyeonee/codingTest-study/assets/92504386/c08cc58c-bf3b-44d9-b6ab-63fcb028c5d6">
   
   <img width="500" alt="스크린샷 2024-01-02 오전 1 51 35" src="https://github.com/Jaehyeonee/codingTest-study/assets/92504386/aefe3f60-9c33-498c-804e-97695c279f6f">




## 후기
나름 열심히 했다고 생각하며 대회 장소에 도착했는데 다른 팀들의 결과물들과 피칭이 매우 뛰어나서 수상에 대한 기대를 놓고 있었다,,

|||
|:------------|:-------------------------:|
| <img width="459" alt="스크린샷 2024-01-02 오전 1 56 42" src="https://github.com/Jaehyeonee/codingTest-study/assets/92504386/d10bd603-5c75-4b2f-aaa5-45c7a0134a68"> | <img width="459" alt="스크린샷 2024-01-02 오전 1 56 42" src="https://github.com/Jaehyeonee/codingTest-study/assets/92504386/5478131e-88ec-4d1c-a14c-389b1d01a40f"> |

그저 AWS에서 준비해주신 치킨을 야무지게 먹으며 발표를 듣고 있었다.
(다들 진짜 너무 대단하고 멋있었다..👍🏻)<br>
마지막 수상 발표에서는 기대를 걸어보았던 등수에서도 호명되지 않아 더더욱이 포기했는데..! <br> 

![IMG_8895](https://github.com/Jaehyeonee/codingTest-study/assets/92504386/9dea2ae6-209a-4fc0-83f2-7372d3075b35)

<h3>영예의 1등을 얻게 되었다..🫨</h3>

![image](https://github.com/Jaehyeonee/codingTest-study/assets/92504386/a58755a6-329a-4293-975f-d15af121b4d0)

시상 상품은 팀원 각 AWS 1주!! AWS의 (소)주주가 되었다! <br>
상품과는 별개로, 그저 AWS상을 수상했다는 것 자체만으로도 너무 떨떠름했고 다른 훌륭한 팀들 사이에서 좋은 평을 받았다는 것이 뿌듯했다.<br> 


AWS 툴도 익숙하지 않았고, 더욱이 Slack bot 개발은 처음이라 매우 낯설었다.
개발과정이 순탄하지는 않았지만, 팀원들과 함께 끝까지 완주해 내었음에 연말의 뿌듯함을 더욱 느낄 수 있었다.
<br><br>
🍀 아마 2023년 연말 최고의 선물인 듯 하다!

<br>
2024년에는 더욱 발전하며, 익숙하지 않던 aws툴을 잘 다룰 수 있도록 공부해야겠다고 다짐하게 되었다!
























