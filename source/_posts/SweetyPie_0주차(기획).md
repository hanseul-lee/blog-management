---
title: "[프로젝트] SweetyPie - Airbnb 클론코딩 기획 TIL (0주차: 21.01.25 ~ 21.01.31)"
categories: [project]
tags: [Fastcampus, 프로젝트, SweetyPie]
thumbnailImage: logo.png
date: 2021-01-24 23:58:31
updated:
---

<!-- more -->
미니프로젝트 기획 TIL (0주차: 21.01.25 ~ 21.01.31)
- PM특강
- 주제 선정 및 전반적인 기획

<!-- excerpt -->
<!-- toc -->

## 1일차 - 21.01.25 월요일

- PM특강
  - 소프트웨어 개발 생명주기
  - Agile 방법론
- 백엔드분들과 첫 만남 - 나영원, 이재복, 임준철님
- 주제 선정 - Airbnb
- Requirement Analysis - 고객, 기능, 외부 인터페이스
  - 구현하고자하는 페이지 선정
  - 크롤링에 대한 고민(벡엔드)

- Wireframe 및 figma로 페이지 레이아웃 및 기능 설명 역할 분배

<br>

## 2일차 - 21.01.26 화요일

- Zoom 회의 1차 - FrontEnd
  - wireframe 및 기능 figma와 노션으로 정리
- Zoom 회의 2차 - FrontEnd & BackEnd
  - wireframe 변경사항 공유
  - 실제 레이아웃 디자인 노션에 정리한 것 공유
  - 각 페이지별 상세 기능 및 필요한 DB 정리 공유
  - DB에서 받을 수 있는 것과 default로 둘 것 논의

<br>

## 3일차 - 21.01.27 수요일

- 중간 기획 발표 준비

  - Wireframe 및 figma 다듬기

- 중간 기획 발표

- 중간 기획 발표 피드백

  - 기획에 필요한 계획들에 대한 내용이 많이 빠져있음
  - 결제 및 SNS와 연동한 로그인 부분(카카오, 페이스북 등) 뺄 것. 휴대폰 로그인 인증도 더미로 처리하는 것이 좋음.
  - 계획한 페이지가 너무 많아보임. 더 쳐내도 될 듯함.
  - API 문서화 필요
  - 그 외 백엔드 부분 피드백
  - 백엔드와 충분한 대화가 부족해 보임. 팀 프로젝트인 만큼 백엔드와 프론트가 서로 기능 및 인터페이스에 대해 사전에 충분히 논의할 것.

  => 불완전한 걸 많이 하기보다 조금이라도 완성도 있게 나가는 방향으로 할 것
  별 거 없지 하고 하다보면 계속 할일이 늘어날 것임.

  

- 중간 기획 발표 후 전체 회의

  - 매니저님 최종 프로젝트 당시 기획안 PPT 구경
    => 우리는 레이아웃만 준비한 것, 회사 및 매니저님 기획 발표에서 준비하는 것의 90% 이상이 빠져있었음. 
    따라서 강사님들의 피드백이 부족할 수밖에 없었음

  - 최종 기획 보충 및 추가할 내용 정리
  (목표, 주제 선정 이유, 세부 기능 정리, API Design, Directory Structure, 코딩 컨벤션, 팀 이름, Daily Scrum & Sprint 계획 등)

  - 피드백 바탕으로 빼야할 부분 정리

<br>


## 4일차 - 21.01.28 목요일

- 최종 기획 발표 준비
  1. 최종 기획안 발표 PPT 개요 짜기
  2. 공동목표 및 백엔드, 프론트엔드팀 목표 설정
  3. 각 페이지 별 세부 기능 정리(엑셀)
  4. API Design - DB mockup 설계 (JSON형식) 
  5. 1, 2차 구현 페이지 목표 설정
  6. 세부 페이지 레이아웃 수정 및 노션에 정리
  7. github project로 Sprint Backlog 준비

<br>

## 5일차 - 21.01.29 금요일

- 최종 기획 발표 준비
- 최종 기획 발표
  - slides.com/youngseo/deck
- 최종 기획 발표 피드백
  - 배포에 대한 계획과 실행이 빠져있음 - 보충할 것
  - 세션에서 인증 처리하는 것
  - 엑셀보다는 최대한 문서화를 줄이고 공유가능한 github 하나에만 집중할 것

<br>

## 6일차 - 21.01.30 토요일

- Tailwind Starter Kit 공부
- Tailwind 공식 문서 읽고 React에 적용
- react에서 Tailwind로 적용한 버튼 컴포넌트로 쪼개는 것 연습

<br>

## 7일차 - 21.01.31 일요일

- Tailwind Button.jsx 컴포넌트 완성

  ```js
  const ButtonColor = {
    pink:
      'bg-red-500 hover:bg-red-600 text-white font-bold rounded transition-all duration-150 shadow-md focus:outline-none hover:animation-gradient',
    gray:
      'bg-gray-400 hover:bg-gray-500 text-white font-bold rounded transition-all duration-150 shadow-md focus:outline-none ',
    white:
      'bg-white hover:bg-gray-100 text-grey-700 font-bold rounded transition-colors duration-150 shadow-md focus:outline-none focus:ring-2 focus:ring-indigo-400 border',
    green:
      'bg-green-600 hover:bg-green-700 text-white font-bold rounded transition-colors duration-150 shadow-md focus:outline-none ',
    black:
      'bg-black hover:bg-gray-600 text-white font-bold rounded transition-colors duration-150 shadow-md focus:outline-none ',
  };
  
  const ButtonSize = {
    sm: 'h-9 px-5 m-2 text-xs transform focus:scale-90 ',
    md: 'h-10 px-5 m-2 text-sm transform focus:scale-90',
    lg: 'w-full h-11 px-6 m-2 text-md transform focus:scale-90',
  };
  
  const Button = ({ color, size, children }) => {
    const classNames = ButtonColor[color] + ' ' + ButtonSize[size];
  
    return <button className={classNames}>{children}</button>;
  };
  
  export default Button;
  ```
<br>

{% image center button.png 600px%}

<br>

