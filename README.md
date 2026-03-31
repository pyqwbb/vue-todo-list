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
- 필터링 (전체 / 남은 일 / 완료)
- 할 일 개수 표시 (전체 / 남은 일 / 완료)
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
 ┃ ┣ TodoHeader.vue   # 탭 및 개수 표시
 ┃ ┣ TodoList.vue     # 투두 목록 및 수정/삭제
 ┃ ┗ TodoInput.vue    # 입력 영역
 ┣ App.vue            # 상태 관리 및 핵심 로직
 ┗ main.js
```

## 🔀 5. 브랜치 안내

- main
  - Option API 기반 기본 Todo 애플리케이션
- composition
  - Composition API 리팩토링 및 기능 확장 버전
  - 할 일 개수 표시 및 필터 기능 개선 포함

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

## 🖼️ 7. 실행 화면

> Composition API 브랜치에서 실행한 화면입니다.  
> 기본 기능에 더해 개수 표시 및 필터링 기능이 확장되었습니다.

![Image](https://github.com/user-attachments/assets/ff81a201-10c3-4e4c-b908-b8f742b862bd)

## 🌱 8. 프로젝트를 통해 배운 점

- Vue 컴포넌트 구조 설계 및 props / emits를 통한 데이터 흐름 이해
- localStorage를 활용한 클라이언트 데이터 저장 방식 이해
- Option API → Composition API로의 리팩토링 경험
- Composition API 기반 코드 구조 및 설계 방식 학습

## 🚧 9. 추가 개선 예정

- 삭제 전 확인 모달(경고창) 추가
- UI/UX 개선 및 스타일 고도화

### ✅ 완료된 개선 사항

- 할 일 개수 표시 (전체 / 남은 일 / 완료)
- 남은 일 필터링 기능 추가
