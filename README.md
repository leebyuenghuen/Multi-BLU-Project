# 멀티캠퍼스 융복합 프로젝트 - 감정일기
- 진행기간 : 2022.05.25 ~ 2022.06.14
- 주제 : 감정 분석을 통한 스마트 일기 서비스 (BLU)
- 팀명 : 2편한세상
- 수상기록 : 최우수상

## 공동 작업 Organization
- 링크 : https://github.com/2zyworld/Cloud

## 서비스 내용
- 사용자가 일기를 쓰게 되면 해당 일기를 AI 모델이 감정분석하여 결과에 따른 서비스 ( 색, 노래추천, 무드등 등)를 사용자에게 제공한다.
- 이를 통해 사용자 스스로 자신의 감정을 돌이켜 볼 수 있는 계기를 주어 정신건강에 긍정적 치유가 되도록 한다.

## 1. 구성도
- 설계는 그 동안 멀티캠퍼스에서 배운 내용을 이용하여 AWS 친화적을 중점으로 설계하였다
![image](https://user-images.githubusercontent.com/97427442/176380663-944ad726-006e-47c4-a213-ab41b5e1aa80.png)
- 서비스 내부는 Kubernetes를 이용하여 설계하였다
![image](https://user-images.githubusercontent.com/97427442/176380918-b6c9a9af-5cfb-4847-b710-b9e1b7e3192c.png)

## 2. 설계상의 문제와 해결법
  2-1 AI 모델
- 설계초기 AWS Lambda를 이용하여 api통신을 IOT팀과 하려고 하였으나 GPU, CPU의 소스를 필요로 하는 AI 함수 특성상 개발은 EC2에서 진행하게 되었다.
- 어느 정도 개발 진행 된 EC2를 DOCKER를 이용하여 container 구조로 바꿔 Kubernetes에서 서비스를 배포하였다.

  2-2 IOT 통신
- Android studio와 AWS 서버와 통신하기 위해 API통신과, mosquitto를 이용하였다.
- API는 Django Rest framework로 생성하여 서버에서 일기에 대한 분석값을 리턴해주는 역활을 하였다
