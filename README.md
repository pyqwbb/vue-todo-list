# Vue Todo List

## 📌 1. 프로젝트 소개

Vue 3를 활용하여 구현한 Todo List 애플리케이션입니다.  
할 일의 추가, 수정, 삭제, 완료 처리 기능을 제공하며,  
localStorage를 통해 데이터를 유지하도록 구현했습니다.

또한 Option API로 구현한 코드를  
Composition API로 리팩토링하며 구조 개선을 진행했습니다.

## ✨ 2. 주요 기능

- 할 일 추가 / 수정 / 삭제
- 완료 상태 토글
- 필터링 (전체 / 완료)
- localStorage를 통한 데이터 유지

## 🛠️ 3. 기술 스택

- HTML / CSS
- Vue 3
- Option API / Composition API
- localStorage

## 📂 4. 프로젝트 구조

```bash
src/
 ┣ components/
 ┃ ┣ TodoHeader.vue   # 탭 (전체 / 완료)
 ┃ ┣ TodoList.vue     # 투두 목록 및 수정/삭제
 ┃ ┗ TodoInput.vue    # 입력 영역
 ┣ App.vue            # 상태 관리 및 핵심 로직
 ┗ main.js
```

## 🔀 5. 브랜치 안내

- main
  - Option API 기반으로 구현된 기본 Todo 애플리케이션
- composition
  - Composition API로 리팩토링한 버전
  - `<script setup>`을 활용하여 코드 간결화 및 가독성 개선

## 🚀 6. 실행 방법

```bash
# Option API 버전
git checkout main
npm install
npm run dev
```

```bash
# Composition API 리팩토링 버전
git checkout composition
npm install
npm run dev
```

## 🖼️ 7. 실행 화면 (이미지 추천)

#### 1. 할 일 추가

![Image](https://github.com/user-attachments/assets/41c300cf-c9dc-4e39-88ed-5bf098d89b91)

#### 2. 완료 처리 및 필터링

![Image](https://github.com/user-attachments/assets/602388ec-05a0-447d-89ea-288089fe97cb)

#### 3. 할 일 수정

![Image](https://github.com/user-attachments/assets/7fa2e3e9-9e7a-4260-8cf5-f97c29825dd2)

#### 4. 완료 항목 삭제

![Image](https://github.com/user-attachments/assets/8327ee3b-def1-4e46-a7d8-c228749a6049)

## 🌱 8. 프로젝트를 통해 배운 점

- Vue 컴포넌트 구조 설계 및 props / emits를 통한 데이터 흐름 이해
- localStorage를 활용한 클라이언트 데이터 저장 방식 이해
- Option API → Composition API로의 리팩토링 경험
- Composition API 기반 코드 구조 및 설계 방식 학습

## 🚧 9. 추가 개선 예정

- 할 일 및 완료 항목 개수 표시
- 삭제 전 확인 모달(경고창) 추가
- UI/UX 개선 및 스타일 고도화
