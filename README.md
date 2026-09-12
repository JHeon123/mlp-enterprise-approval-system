<img width="915" height="357" alt="image" src="https://github.com/user-attachments/assets/5c72b8e2-5658-4ab5-bb29-03238d900bee" />

# <p align="center"> 🧩 비즈포털 BizPortal <p>
### <p align="center">
&nbsp;&nbsp;&nbsp;전자결재 · 일정 · 회의 · 채팅 · 공유함 · 메일 · AI 챗봇을 한 곳에서 🏢✨ <p>
&nbsp;&nbsp;&nbsp;결재·일정·조직을 한 곳에 모아 “요약 → 결정 → 실행” 흐름을 만드는 전자결재 중심 그룹웨어 <br>
&nbsp;&nbsp;&nbsp;&nbsp;<br>
##### <p align="center"> URL : {www.bizportal.pro} <p>
<br>

## 📌 Table of Contents
- [Overview](#-overview)
- [Demo](#-demo)
- [System Architecture](#-system-architecture)
- [Tech Stack](#-tech-stack)
- [Core Features](#-core-features)
- [ERD](#-erd)
- [API](#-api)
- [How to Start](#-how-to-start)
- [Directory Structure](#-directory-structure)
- [Members](#-members)

<br>

## ✨ Overview
**비즈포털(BizPortal)** 은 전자결재를 중심으로 회사 업무 흐름을 한 곳에서 처리할 수 있도록 만든 **그룹웨어 서비스**입니다.  
공지/게시판/일정/회의/전자결재 데이터를 **Elasticsearch 통합검색**으로 빠르게 찾고,  
사내 규정은 **RAG 기반 챗봇**으로 질의응답하며,  
**채팅(WebSocket)** 과 **실시간 알림(SSE + Redis Pub/Sub)** 으로 업무 커뮤니케이션을 끊기지 않게 연결합니다.

<br>

## 🎥 Demo
|**메인 / 통합검색**|**전자결재**|
|:-------------------:|:---------:|
|<img width="390" height="220" alt="Main Search" src="https://github.com/user-attachments/assets/0bbae82d-2cca-4247-8342-29d8def712e7">|<img width="390" height="220" alt="Approval" src="https://github.com/user-attachments/assets/7e21d87f-9346-4409-9c48-2edaf2cab927">|
|**AI 챗봇 (RAG + TTS)**|**회의 (STT/요약)**|
|<img width="390" height="220" alt="Chatbot" src="https://github.com/user-attachments/assets/05f5da3d-3ff5-415a-83a8-fd0bc304fb82">|<img width="390" height="220" alt="Meeting" src="https://github.com/user-attachments/assets/83c851d0-ced1-4c88-8849-f6c861849763">|
|**채팅 (WebSocket)**|**알림함 (SSE)**|
|<img width="390" height="220" alt="Chat" src="https://github.com/user-attachments/assets/4038e3a6-ba37-4fdb-b992-dbbcad73401f">|<img width="390" height="220" alt="Notification" src="https://github.com/user-attachments/assets/e92c48c5-c4c1-490d-a1b3-61a420ddc87b">|

<br>

## 🚨 System Architecture

<img width="820" height="448" alt="image" src="https://github.com/user-attachments/assets/bc9dffc9-c99b-45cc-a4ee-ea37aaace74f" />

### Traffic Flow
`HTTPS → Load Balancer(ALB) → Ingress(EKS) → Spring Boot(Tomcat) / FastAPI(Uvicorn) → DB/Cache/Search/VectorDB`

### Infra / Data Stores
- **CI/CD**: Jenkins  
- **Compute**: AWS **EC2**, **EKS(Kubernetes)**  
- **DB**: MySQL (**Amazon RDS**), Redis (**ElastiCache**), **MongoDB Atlas**  
- **Search**: **Elasticsearch** (EKS에 Pod로 운영 + **EBS PVC**)  
- **Vector DB**: **Weaviate** (EKS에 Pod로 운영 + **EBS PVC**)  
- **External API**: OpenAI (FastAPI 연동)

<br>

## 🛠 Tech stack 
<br>
<div align =center>

분야| 사용 기술|
:--------:|:------------------------------:|
**Frontend** | ![Thymeleaf](https://img.shields.io/badge/Thymeleaf-%23005C0F.svg?style=for-the-badge&logo=Thymeleaf&logoColor=white) 
**Backend** | ![Spring](https://img.shields.io/badge/spring-%236DB33F.svg?style=for-the-badge&logo=spring&logoColor=white) ![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi) ![JWT](https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=JSON%20web%20tokens) ![FFmpeg](https://shields.io/badge/FFmpeg-%23171717.svg?logo=ffmpeg&style=for-the-badge&labelColor=171717&logoColor=5cb85c) ![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white) ![Elasticsearch](https://img.shields.io/badge/elasticsearch-%230377CC.svg?style=for-the-badge&logo=elasticsearch&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white) ![Redis](https://img.shields.io/badge/redis-%23DD0031.svg?style=for-the-badge&logo=redis&logoColor=white) ![ChatGPT](https://img.shields.io/badge/chatGPT-74aa9c?style=for-the-badge&logo=openai&logoColor=white)
**DevOps** | ![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white) ![Jenkins](https://img.shields.io/badge/jenkins-%232C5263.svg?style=for-the-badge&logo=jenkins&logoColor=white)  ![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white) ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white) ![Helm](https://img.shields.io/badge/helm-%230F1689.svg?style=for-the-badge&logo=helm&logoColor=white)
**Monitoring** |   <img src="https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=black">
**etc** | ![Slack](https://img.shields.io/static/v1?style=for-the-badge&message=Slack&color=4A154B&logo=Slack&logoColor=FFFFFF&label=) ![Notion](https://img.shields.io/static/v1?style=for-the-badge&message=Notion&color=000000&logo=Notion&logoColor=FFFFFF&label=) ![Figma](https://img.shields.io/static/v1?style=for-the-badge&message=Figma&color=F24E1E&logo=Figma&logoColor=FFFFFF&label=) ![Discord](https://img.shields.io/badge/Discord-%235865F2.svg?style=for-the-badge&logo=discord&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)
</div>

</div>

<br>

## 💡 Core Features
### 1) 전자결재
- 결재 문서 작성/상신/승인/반려 등 전자결재 프로세스 지원  
- 업무 흐름(결재 라인/상태)에 맞춘 문서 관리

### 2) 통합검색 (Elasticsearch)
- 공지/게시판/일정/전자결재/회의 등 주요 데이터 **통합 검색**
- **Nori 형태소 분석** 기반으로 한국어 검색 품질 강화

### 3) AI 챗봇 (RAG + Text-to-SQL + Agent)
- 사내 규정 문서를 **RAG**로 검색해 근거 기반 답변
- 질문에 따라 **DB 조회(Text-to-SQL)** / **RAG** / **Hybrid**로 분기해 응답 성능 개선
- **Redis 세션**으로 사용자별 문맥 유지
- 문서 **공개/비공개 접근 제어**로 권한 기반 질의 제한
- 청크 단위 스트리밍(자연스러운 답변 흐름)

### 4) 회의 AI (STT/요약)
- 회의 녹음/파일 기반 **Whisper(STT)** 로 전사
- FastAPI AI 서비스에서 요약 생성 후 백엔드로 전달(콜백 방식)

### 5) 채팅 (WebSocket)
- 사원 간 1:1/그룹 채팅 지원  
- 실시간 메시지 송수신으로 협업 속도 향상

### 6) 실시간 알림 (SSE + Redis Pub/Sub)
- 알림 이벤트 발생 시 **SSE**로 클라이언트에 실시간 전달
- 멀티 인스턴스 환경에서 **Redis Pub/Sub**로 이벤트 브로드캐스팅
- 알림함 누적 저장 및 클릭 시 관련 화면 이동

<br>

## 💎 ERD
<img width="692" height="728" alt="image" src="https://github.com/user-attachments/assets/1164d58b-9876-4c1d-bd60-fe5b78379ed4" />
URL : (https://www.notion.so/2c9f831b95c8806c89f5ccbc102432ea?source=copy_link)

<br>

## 📙 API
<img width="1459" height="615" alt="image" src="https://github.com/user-attachments/assets/e0b2413c-5469-4384-871e-b2adc875326b" />
