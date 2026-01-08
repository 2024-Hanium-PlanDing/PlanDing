# 📖 손쉬운 일정 관리와 플래너 공유 플랫폼 PlanDing

<div align="center">

![PlanDing](https://github.com/user-attachments/assets/63bda6b3-45d4-4e55-9a5a-47829b9bebc0)

</div>

- **프로젝트 소개 영상** : https://youtu.be/a1mq1rUVoYg

<br>

## 📝 프로젝트 소개

**"개인과 팀의 조화를 위한 스마트한 스케줄링"**

PlanDing은 개인의 일정 관리와 팀 프로젝트의 협업을 한곳에서 연결하여 효율적인 소통을 돕는 실시간 일정 플랫폼입니다.
개인적으로는 체계적인 플래너로, 팀으로는 강력한 협업 도구로 활용할 수 있습니다.

<br>

## 🛠 Tech Stack

| Category          | Technologies                               |
| ----------------- | ------------------------------------------ |
| **Frontend**      | React, Redux, TailwindCSS                  |
| **State**         | Redux Toolkit                              |
| **Communication** | Axios, StompJS, EventSource-Polyfill (SSE) |
| **Utils**         | Day.js, Eslint, Prettier                   |

<br>

## ✨ Key Features

### 📅 시각화된 일정 관리

- **주간·일간 타임테이블**: 하루 일정을 직관적으로 확인하고 드래그 앤 드롭으로 손쉽게 관리할 수 있습니다.
- **실시간 공유**: 작성한 일정을 팀원들과 실시간으로 공유하고 조율하여 협업 효율을 극대화합니다.

### 👥 그룹 시스템 및 채팅

- **초대 시스템**: 그룹을 생성하고 팀원을 초대하여 우리만의 협업 스페이스를 구축합니다.
- **전용 채팅**: 그룹 내 채팅 기능을 통해 일정 변경 사항이나 중요 공지를 즉각적으로 공유합니다.

<br>

## 🏗 Project Structure

```bash
src
├── assets             # 이미지, 폰트 등 정적 리소스
├── components         # 재사용 가능한 UI 컴포넌트
│   ├── GroupPage
│   ├── ListPage
│   ├── LoginPage
│   ├── LoginProgressPage
│   ├── Modal          # 각종 모달 컴포넌트 모음
│   ├── PersonalPage
│   ├── ToDoPage
│   └── CustomCalendar.jsx
├── hooks              # 커스텀 React Hooks
├── pages              # 라우트 페이지 컴포넌트
│   ├── GroupPage.jsx
│   ├── ListPage.jsx
│   ├── LoginPage.jsx
│   ├── LoginProgressPage.jsx
│   ├── PersonalPage.jsx
│   └── ToDoPage.jsx
├── redux              # Redux 상태 관리 (Slices, Store)
├── services           # API 요청 및 비즈니스 로직
├── styles             # 전역 스타일 및 테마
├── utils              # 유틸리티 함수
├── App.jsx            # 메인 앱 컴포넌트
└── main.jsx           # 진입점 (Entry Point)
```

<br>

## ⚡ Trouble Shooting & Optimization

<details>
<summary><strong>1. STOMP 도입을 통한 메시징 구조 최적화</strong></summary>

### 🚨 Problem

단일 WebSocket 연결에서 채팅, 일정 업데이트, 알림 등 모든 메시지를 처리하려다 보니 프론트엔드의 메시지 분기 로직이 지나치게 비대해지고 유지보수가 어려워졌습니다.

### ✅ Solution

STOMP (Simple Text Oriented Messaging Protocol) 프로토콜을 도입하여 기능별(채팅, 일정, 알림)로 독립된 구독 채널(Topic)을 설계했습니다.

### � Result

다중 채널 구조를 통해 메시지 처리 로직을 분리함으로써 확장성을 강화하고 코드 가독성을 대폭 개선했습니다.

</details>

<details>
<summary><strong>2. 번들 최적화: Moment.js에서 Day.js로 전환</strong></summary>

### 🚨 Problem

초기 로딩 속도 분석 결과, 날짜 처리를 위해 사용하던 Moment.js가 전체 번들 크기의 약 55%(288KB)를 차지하며 성능 저하의 주 원인으로 파악되었습니다.

### ✅ Solution

Moment.js와 API 호환성이 높으면서도 Tree-shaking을 지원하는 경량 라이브러리인 Day.js로 전격 교체하였습니다.

### 📈 Result

날짜 처리 관련 번들 크기를 99% 이상(288KB → 2KB) 줄여 초기 로딩 속도를 획기적으로 개선했습니다.

</details>

<br>

## 🏆 Achievements & Lessons Learned

- **성능 중심의 개발 마인드**: 단순히 기능을 구현하는 것을 넘어, 번들 사이즈 분석을 통해 초기 로딩 속도를 개선(Day.js 도입)하며 사용자 경험을 최적화하는 과정을 경험했습니다.
- **실시간 데이터 동기화의 이해**: WebSocket과 STOMP, SSE를 활용하여 채팅과 일정 공유 기능을 구현하며 실시간 양방향 통신과 단방향 이벤트 스트림의 차이 및 적재적소 활용법을 익혔습니다.
- **협업과 커뮤니케이션**: Jira와 Confluence를 활용한 체계적인 일정 관리와 문서화를 통해, 4인 팀 프로젝트를 7개월간 성공적으로 이끌며 협업의 중요성을 체감했습니다.

<br>

## 👨‍👩‍👧‍👦 팀원 구성

<div align="center">

|                                                  박철현                                                   |                                                  김상운                                                   |                                                 박민수                                                  |                                                 이민규                                                  |
| :-------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------: |
| <img src="https://github.com/user-attachments/assets/b6afafac-bed6-4c35-acb0-7e588fa9d0cb" width="120" /> | <img src="https://github.com/user-attachments/assets/b6afafac-bed6-4c35-acb0-7e588fa9d0cb" width="120" /> | <img src="https://github.com/user-attachments/assets/b6afafac-bed6-4c35-acb0-7e588fa9d0cb" width="120"> | <img src="https://github.com/user-attachments/assets/b6afafac-bed6-4c35-acb0-7e588fa9d0cb" width="120"> |
|                                           **Web (Team Leader)**                                           |                                                **Backend**                                                |                                               **Android**                                               |                                               **Design**                                                |
|                                  [@hyeon](https://github.com/play3step)                                   |                              [@SangWoon123](https://github.com/SangWoon123)                               |                                 [@comst19](https://github.com/comst19)                                  |                                       [@22](https://github.com/)                                        |

</div>

<br>
