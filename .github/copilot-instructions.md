# Copilot instructions (StickerSmash)

## 응답/커뮤니케이션

- 한글 답변을 기본으로 합니다.
- 코드 예시는 TypeScript/JavaScript 및 React Native 문법을 사용합니다.
- 리액트 경험은 있으나 리액트 네이티브 경험이 적은 사용자를 대상으로 설명합니다.
- Expo, expo-router 용어는 필요할 때만 간단히 풀이합니다.

## 아키텍처와 라우팅 구조

- Expo + expo-router 기반이며 entry는 package.json의 main 값 expo-router/entry 입니다.
- 라우팅은 app/ 파일 기반입니다. 루트 스택은 [app/\_layout.tsx](app/_layout.tsx)에서 탭 그룹만 노출합니다.
- 탭 내비게이션은 [app/(tabs)/\_layout.tsx](<app/(tabs)/_layout.tsx>)에서 구성하며 index/about 화면을 등록합니다.

## 핵심 화면 흐름(홈)

- [app/(tabs)/index.tsx](<app/(tabs)/index.tsx>)에서 이미지 선택 → 상태 저장 → ImageViewer 렌더링 흐름을 구현합니다.
- 이미지 선택은 expo-image-picker의 launchImageLibraryAsync 결과 중 assets[0].uri를 사용합니다.
- [components/ImageViewer.tsx](components/ImageViewer.tsx)는 selectedImage가 있으면 { uri }를, 없으면 placeholder 이미지를 사용합니다.
- [components/Button.tsx](components/Button.tsx)에서 theme="primary"만 onPress를 사용하고, 기본 버튼은 alert를 호출합니다.

## 코드 스타일/패턴

- 스타일은 각 화면/컴포넌트 내부에서 StyleSheet.create로 정의합니다.
- 기본 색상 조합은 어두운 배경 #25292e + 포인트 #ffd33d 입니다.
- 에셋 경로는 @/assets 별칭을 사용합니다(placeholder는 assets/images/background-image.png).

## 개발 워크플로우

- 실행: npm run start (expo start)
- 플랫폼별 실행: npm run ios | npm run android | npm run web
- 린트: npm run lint
- 초기화: npm run reset-project (scripts/reset-project.js)

## 외부 의존성/통합 포인트

- expo-router, expo-image-picker, @expo/vector-icons, @react-navigation/\*를 사용합니다.
