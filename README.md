# 📘 Grow - 프론트엔드 (React Native)

Grow는 수강 정보, 실시간 채팅, 강의 리뷰 기능을 제공하는 **학생 맞춤형 교류 플랫폼**입니다.  
React Native 기반의 모바일 앱으로, Firebase Realtime Database와 PostgreSQL 백엔드 API를 연동하여 실시간성과 데이터 신뢰성을 모두 갖췄습니다.

<br/>
![image](https://github.com/user-attachments/assets/09ab95ed-7bff-4f7b-bc52-00888cf99f39)

## 🛠️ 주요 기술 스택

- **React Native**
- **TypeScript**
- **Firebase Realtime Database**
- **Firebase Authentication**
- **Axios** (백엔드 API 연동)
- **React Navigation**
- **AsyncStorage** (토큰 로컬 저장)

<br/>

## 🧩 주요 기능

| 기능 | 설명 |
|------|------|
| 🔐 회원가입 / 로그인 | Firebase Auth를 이용한 이메일 기반 인증 |
| 🧾 강의 목록 조회 | Madgrades 기반의 백엔드 API에서 강의 정보 불러오기 |
| 💬 수업별 채팅 | Firebase Realtime Database를 통한 **실시간 채팅** 기능 |
| ✍️ 리뷰 작성 및 수정 | 수강한 강의에 대한 리뷰 작성, 수정, 삭제 |
| 👤 유저 프로필 | 사용자 정보 수정 및 수강 과목 등록 UI |
| 📲 푸시 알림 (예정) | 실시간 채팅 푸시 알림 기능 예정 |

<br/>

## 🔐 인증 흐름

- Firebase Auth 기반 이메일 로그인
- 로그인 성공 시 토큰을 `AsyncStorage`에 저장
- 이후 Axios 요청 시 백엔드 API에 토큰 포함

<br/>

## 🚀 실행 방법

```bash
npm install
npx expo start

