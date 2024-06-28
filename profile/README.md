# 🤖 Imaginairy-Web
## 목차
| 순번 | 목차 항목 |
| :-: | :-: |
| 1 | [팀원 소개](#팀원-소개) |
| 2 | [프로젝트 기간](#프로젝트-기간) |
| 3 | [추진 배경](#추진-배경) |
| 4 | [프로젝트 목표](#프로젝트-목표) |
| 5 | [시스템 설계도](#시스템-설계도) |
| 6 | [기능 정리](#기능-정리) |
| 7 | [기능 평가](#기능-평가) |

## 팀원 소개

| _이름_ | 정규원 |
|:-----:|:----:|
| ___역할___ | FE, BE, AI, DevOps
| ___Github___ | <a href="https://github.com/digitpic"><img src="https://avatars.githubusercontent.com/u/63178849?v=4" width="64" height="64"></a> |

## 프로젝트 기간
- 23.09 ~ 23.12

## 추진 배경
- Imaginairy 라는 Stable Diffusion 기반 오픈소스 이미지 생성 AI가 있는데 로컬환경에서만 동작되게 되어 있음
- 웹 서비스를 통해 사용자들이 자체 GPU를 사용하지 않아도 되면서, 해당 모델을 보다 더 쉽게 사용할 수 있도록 함
  
## 프로젝트 목표
- 텍스트 기반으로 이미지를 생성, 편집, 업스케일링을 할 수 있으며 이전에 생성했던 이미지들을 조회하고 관리할 수 있는 웹 서비스 구축
- Docker 를 통한 서비스 별 컨테이너 분리
- K8s 를 통한 MSA 환경 구축
- Jenkins 를 통한 CI, CD 파이프라인 구축

## 시스템 설계도
![arch](https://github.com/DKU-CloudComputing/.github/assets/63178849/7bbd5291-46db-44d7-a3a8-a641b1b545c7)<br>

1. 웹 서비스 구현: 사용자 인터페이스로 이미지 생성, 편집, 업스케일링의 기능을 제공한다.
   - React를 사용하여 Front-end Page 구현
   - Spring Boot를 사용하여 Back-end API 구현
   - Imaginairy는 Google Colab에서 사용
     - Google Colab에서 Flask를 이용하여 API 구현
       - Ngrok을 통해 Flask를 외부에서 접근 가능하게 구현
   - MariaDB를 사용하여 Database를 구축
     - Spring Boot에서 Hibernate를 통한 연동
     - 이전에 생성한 이미지들을 조회하고 관리할 수 있게 하는 기능 구현

2. 사용자 인증: 회원가입을 통해 인증된 사용자만 서비스를 이용할 수 있게 한다.
   - Spring security를 사용해서 ID/PW 기반으로 회원가입, 로그인을 진행
   - Spring Boot와 Google Colab 연결
     - Spring Boot
       - React로부터 받은 텍스트를 Google Colab으로 보내고, Google Colab으로부터 이미지를 받는다.
     - Google Colab
       - Spring Boot로부터 텍스트를 받고, 이미지를 생성, 편집, 업스케일링 한 뒤 이미지를 Spring Boot로 보낸다.

## 기능 정리
| 순번 | 기능 목록 | 이미지 |
| :-: | :-: | :-: |
| 1 | 회원가입 | <img width="296" alt="회원가입" src="https://github.com/DKU-CloudComputing/.github/assets/63178849/a16d255f-1aa3-40b0-bcdc-7044e4c06d4e"> |
| 2 | 회원정보 수정 | <img width="291" alt="회원정보변경" src="https://github.com/DKU-CloudComputing/.github/assets/63178849/ea2e7c74-3be2-40e4-8625-5e36619d5d34"> |
| 3 | 로그인 | <img width="296" alt="로그인" src="https://github.com/DKU-CloudComputing/.github/assets/63178849/0a8ca68c-aaad-4940-b57b-daae211f97bf"> |
| 4 | 로그아웃 | <img width="296" alt="로그아웃" src="https://github.com/DKU-CloudComputing/.github/assets/63178849/9f23a443-495f-40d9-8f49-7a715f6cec4f"> |
| 5 | 이미지 생성 | <img width="899" alt="이미지생성" src="https://github.com/DKU-CloudComputing/.github/assets/63178849/bef76a52-93ec-482d-9b06-0fbf343c016d"> |
| 6 | 이미지 편집 | <img width="898" alt="이미지편집" src="https://github.com/DKU-CloudComputing/.github/assets/63178849/603a549a-cf8b-4e70-9446-84ec3da1db88"> |
| 7 | 이미지 업스케일링 | <img width="502" alt="이미지업스케일링" src="https://github.com/DKU-CloudComputing/.github/assets/63178849/1e06a209-cdb9-4e50-bec3-23b6890da73c"> |
| 8 | 이미지 다운로드 | <img width="897" alt="이미지다운로드" src="https://github.com/DKU-CloudComputing/.github/assets/63178849/0e17371e-af30-41b7-90fc-84ebece4a21b"> |
| 9 | 이미지 삭제 | <img width="898" alt="이미지삭제" src="https://github.com/DKU-CloudComputing/.github/assets/63178849/4cc6a778-7478-4232-8b30-fee930f32dcc"> |
| 10 | 대시보드 | <img width="296" alt="대시보드" src="https://github.com/DKU-CloudComputing/.github/assets/63178849/c2291138-7b0d-4e46-9a9f-ce2b6b18bd1c"> |

## 기능 평가

> 정량적 평가

| 평가 항목 | 정량적 목표 | 평가 방법 | 평가 결과| 비고 |
| :-: | :-: | :-: | :-: | :-: |
| 5,000명 동시 접속 | 20ms 이내 응답 | Apache JMeter | <img width="1153" alt="5000명" src="https://github.com/DKU-CloudComputing/.github/assets/63178849/7c24780c-5930-4a84-97e6-1253d20f13d3"> | 성공 | 
| 10,000명 동시 접속 | 20ms 이내 응답 | Apache JMeter | <img width="1153" alt="10000명" src="https://github.com/DKU-CloudComputing/.github/assets/63178849/1a5d68ae-5ee2-4aaa-963d-6de80fc75f5a"> | 실패 |
<br>

> 정성적 평가

| 평가 항목 | 정성적 목표 | 평가 방법 | 비고 |
| :-: | :-: | :-: | :-: |
| 기능 완성도 | 목표 기능 구현 완성도 | 목표 기능 정상 동작 확인 | 성공 |
| 사용자 입력과 관련된 내용의 이미지 생성 | 사용자의 입력에 기반한 이미지 생성 | 이미지가 생성 되었는지 확인 | 성공 |
| 사용자 입력과 관련된 내용의 이미지 편집 | 사용자의 입력에 기반한 이미지 편집 | 이미지 편집이 이루어졌는지 확인 | 성공 |
| 사용자 입력과 관련된 이미지 업스케일링 | 사용자의 입력에 기반한 이미지 업스케일링 | 업스케일링이 이루어졌는지 확인 | 성공 |
