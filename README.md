# Neighbus Application
**지역 커뮤니티 플랫폼의 React Native 모바일 앱**  
**담당**: iOS 앱 개발 (UI/UX + React Native 전체 구현)

---

## 내가 한 일

**웹의 모든 기능을 React Native로 iOS 앱으로 재구현했습니다.**

-  **전체 UI/UX 설계** (모든 화면)
-  **TypeScript + React Native로 완전 개발**
-  **Google Maps Geocoding API 지도 기능**
-  **STOMP + WebSocket 실시간 채팅 구현**
-  **웹 API 연동** (팀원과 협력)

**결과**: 웹과 동일한 기능을 네이티브 같은 성능으로 제공

---

## 구현한 주요 기능

| 기능 | 상세 |
|------|------|
| **로그인/회원가입** | AsyncStorage 기반 자동 로그인 |
| **홈** | 카테고리별 동아리 목록, 신규 모임, 인기 게시글 |
| **지도** | Google Maps + Geocoding으로 모임 장소 지정 |
| **동아리** | 동아리 검색, 가입, 상세 정보 확인 |
| **모임** | 오프라인 모임 생성, 지도 기반 장소 선택 |
| **실시간 채팅** | STOMP + WebView 하이브리드로 안정적 구현 |
| **게시판** | 자유게시판, 갤러리, 공지사항 (글/댓글/반응) |
| **마이페이지** | 내 정보 수정, 가입 동아리, 작성 글 관리 |

---

## 기술적 도전

### 1️⃣ 실시간 채팅 구현 (가장 어려움)

**문제**: React Native 환경에서 WebSocket 기반 실시간 통신 구현

**해결**:
```javascript
// STOMP + WebView 하이브리드 방식
- WebView 내에서 WebSocket 연결 및 STOMP 처리
- React Native ↔ WebView postMessage로 통신
- 복잡한 네이티브 모듈 설정 제거
```

**결과**: 
-  안정적인 실시간 채팅
-  앱 리소스 부담 최소화

### 2️⃣ 지오코딩 (Geocoding) 기능

**문제**: 사용자가 선택한 좌표를 주소로 자동 변환

**해결**:
```javascript
// Google Maps API 연동
1. react-native-maps에서 좌표 획득
2. Google Geocoding API로 주소로 변환
3. 사용자 친화적 주소 표시
```

**결과**:
-  직관적인 장소 설정
-  도로명 주소 자동 변환

### 3️⃣ 네비게이션 복잡성

**문제**: 8개 이상의 화면을 체계적으로 관리

**해결**:
```javascript
// React Navigation 활용
- Bottom Tab Navigator (홈/채팅/마이페이지)
- Stack Navigator (상세 페이지)
- 계층화된 네비게이션 구조
```

**결과**:
- 깔끔한 화면 전환
- 유지보수 용이

---

## 🛠 기술 스택

**Frontend**
- React Native + TypeScript
- React Navigation (Bottom Tab + Stack)
- AsyncStorage (로컬 상태 저장)
- React Context API (전역 상태)

**Real-time Communication**
- `@stomp/stompjs` (STOMP 프로토콜)
- `react-native-webview` (WebSocket 하이브리드)

**Location & Maps**
- `react-native-maps` (지도 UI)
- Google Maps Geocoding API (좌표 ↔ 주소 변환)

**Platform**
- iOS (Swift 래퍼) - 당신이 구현
- Android (Java 래퍼) - 팀원이 구현

**Development**
- TypeScript (타입 안정성)
- ESLint + Prettier (코드 품질)
- Jest (단위 테스트)

---

## 프로젝트 구조

```
src/
├── screens/                 # 화면 컴포넌트
│   ├── auth/                # 로그인/회원가입
│   ├── home/                # 홈 탭
│   ├── chat/                # 채팅 탭
│   ├── mypage/              # 마이페이지 탭
│   ├── club/                # 동아리 상세
│   ├── meeting/             # 모임 상세
│   └── board/               # 게시판
├── navigation/              # React Navigation 설정
├── api/                     # REST API 호출
├── context/                 # Context API (상태 관리)
├── components/              # 재사용 컴포넌트
├── utils/                   # 유틸리티 함수
└── types/                   # TypeScript 타입 정의
```

---

## 배운 점

### React Native의 한계와 극복
```
한계: 
- 웹과 다른 네이티브 환경
- 라이브러리 의존성 관리 어려움
- 플랫폼별 차이 처리

극복:
- WebView 하이브리드로 WebSocket 안정화
- 팀원과의 소통으로 플랫폼 차이 해결
- TypeScript로 타입 안정성 확보
```

### 모바일 UX의 중요성
```
웹: 마우스/키보드 중심
앱: 터치/제스처/모션 중심

→ 같은 기능도 화면 구성과 상호작용은 완전히 달라야 함
→ 모바일 첫 사고방식(Mobile-First) 필수
```

### 지도 기능의 복잡성
```
단순 표시 X
→ 사용자가 직접 위치 선택
→ 좌표 ↔ 주소 자동 변환
→ 오프라인 모임의 핵심 기능
```

---
