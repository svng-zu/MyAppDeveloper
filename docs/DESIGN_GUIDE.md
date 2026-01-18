# UI/UX 디자인 가이드

# RunConnect 앱 UI/UX 디자인 가이드

## 1. 사용자 여정 맵 (User Journey)

### 1.1 신규 사용자 여정
```
온보딩 → 소셜 로그인 → 프로필 설정 → 권한 허용 → 튜토리얼 → 첫 런닝/매칭 시도
```

### 1.2 기존 사용자 여정 (일반 런닝)
```
앱 실행 → 홈 화면 → 런닝 시작 → GPS 추적 → 결과 확인 → 기록 저장
```

### 1.3 기존 사용자 여정 (매칭 런닝)
```
앱 실행 → 홈 화면 → 매칭 런닝 선택 → 매칭 대기 → 매칭 성공 → 실시간 경쟁 런닝 → 결과 비교 → 기록 저장
```

## 2. 주요 화면 구조 및 와이어프레임 설명

### 2.1 주요 화면 목록
1. **온보딩/로그인 화면**
2. **홈 대시보드**
3. **런닝 모드 선택**
4. **매칭 대기 화면**
5. **실시간 런닝 추적 화면**
6. **버츄얼 런닝 화면** (매칭된 상태)
7. **런닝 결과 화면**
8. **런닝 히스토리**
9. **프로필/설정 화면**

### 2.2 화면별 상세 구조

#### 홈 대시보드
- **상단**: 사용자 프로필, 알림, 설정 아이콘
- **중앙**: 
  - 이번 주 런닝 요약 (거리, 시간, 칼로리)
  - "솔로 런닝" / "매칭 런닝" 큰 버튼 2개
- **하단**: 최근 런닝 기록 3개 미리보기
- **광고**: 하단 배너 광고 영역

#### 실시간 런닝 추적 화면
- **상단**: 현재 시간, GPS 신호 상태
- **중앙**: 
  - 큰 타이머 (MM:SS)
  - 현재 페이스, 거리 표시
  - 지도 뷰 (런닝 경로 표시)
- **하단**: 일시정지/정지 버튼

#### 버츄얼 런닝 화면 (매칭 상태)
- **상단**: 상대방 프로필 & 내 프로필 비교
- **중앙**: 
  - 실시간 경쟁 현황 (속도, 거리 바 차트)
  - 작은 지도 뷰
- **하단**: 음성 채팅 버튼, 런닝 컨트롤

## 3. 컬러 팔레트

### 3.1 메인 컬러
- **Primary**: #FF6B35 (활동적이고 에너지 넘치는 주황색 - 런닝의 역동성 표현, 주요 버튼과 액션)
- **Secondary**: #2E86AB (신뢰감 있는 블루 - 안정성과 기술적 신뢰감, 보조 버튼과 정보 영역)
- **Accent**: #F18F01 (따뜻한 오렌지 - 성취감과 동기부여, 알림과 하이라이트)

### 3.2 서포트 컬러
- **Background**: #FAFBFC (매우 연한 그레이 - 전체 배경, 눈의 피로도 최소화)
- **Surface**: #FFFFFF (순백색 - 카드, 모달 등 주요 콘텐츠 영역)
- **Text Primary**: #1A1D23 (진한 차콜 그레이 - 주요 텍스트, 가독성 최우선)
- **Text Secondary**: #6B7280 (중간 그레이 - 보조 정보, 설명 텍스트)
- **Success**: #10B981 (런닝 완료, 목표 달성 시)
- **Warning**: #F59E0B (주의사항, 중요 알림)
- **Error**: #EF4444 (오류, 위험 상황)

## 4. 타이포그래피 가이드

### 4.1 폰트 패밀리
- **iOS**: SF Pro Display (시스템 기본)
- **Android**: Roboto (시스템 기본)

### 4.2 텍스트 스타일
```
H1 (페이지 타이틀): 28px, Bold, Letter spacing -0.5px
H2 (섹션 헤더): 24px, SemiBold, Letter spacing -0.3px
H3 (서브 헤더): 20px, SemiBold, Letter spacing -0.2px
Body Large (주요 정보): 18px, Regular, Line height 1.5
Body Medium (일반 텍스트): 16px, Regular, Line height 1.4
Body Small (보조 정보): 14px, Regular, Line height 1.3
Caption (라벨, 힌트): 12px, Medium, Letter spacing 0.5px
Number Display (런닝 데이터): 32px, Bold, Tabular numbers
```

### 4.3 런닝 데이터 전용 폰트
- **숫자 표시**: Tabular numbers 사용으로 데이터 정렬 일관성 유지
- **시간 표시**: Monospace 특성 활용하여 시간 카운터 안정성 확보

## 5. 주요 UI 컴포넌트 명세

### 5.1 버튼 컴포넌트
```
Primary Button:
- Background: #FF6B35
- Text: #FFFFFF
- Height: 56px
- Border radius: 28px
- Shadow: 0 4px 12px rgba(255, 107, 53, 0.3)

Secondary Button:
- Background: #FFFFFF
- Text: #FF6B35
- Border: 2px solid #FF6B35
- Height: 56px
- Border radius: 28px

Ghost Button:
- Background: Transparent
- Text: #2E86AB
- Height: 44px
- Border radius: 22px
```

### 5.2 카드 컴포넌트
```
Standard Card:
- Background: #FFFFFF
- Border radius: 16px
- Shadow: 0 2px 8px rgba(0, 0, 0, 0.06)
- Padding: 20px
- Margin bottom: 12px

Stat Card (런닝 데이터용):
- Background: #FFFFFF
- Border radius: 12px
- Shadow: 0 1px 4px rgba(0, 0, 0, 0.04)
- Padding: 16px
- Border left: 4px solid #FF6B35
```

### 5.3 입력 필드
```
Text Input:
- Height: 48px
- Border: 1px solid #E5E7EB
- Border radius: 12px
- Padding: 12px 16px
- Focus border: 2px solid #FF6B35
- Background: #FAFBFC
```

### 5.4 런닝 추적 UI
```
Timer Display:
- Font size: 48px
- Font weight: Bold
- Color: #1A1D23
- Background: Semi-transparent overlay

Pace/Distance Cards:
- Background: rgba(255, 255, 255, 0.9)
- Border radius: 8px
- Backdrop blur: 20px
```

### 5.5 매칭 상태 인디케이터
```
Matching Animation:
- Circular progress with pulsing effect
- Primary color: #FF6B35
- Animation duration: 2s infinite

Matched Indicator:
- Green checkmark animation
- Background: #10B981
- Size: 60px circle
```

## 6. iOS/Android 플랫폼별 디자인 가이드라인

### 6.1 iOS 특화 가이드라인

#### 네비게이션
- **상단 네비게이션**: Large Title 스타일 활용
- **탭바**: SF Symbols 아이콘 사용
- **백 버튼**: 시스템 기본 스타일 유지

#### 제스처
- **스와이프**: 히스토리 화면에서 스와이프로 항목 삭제
- **풀 투 리프레시**: 홈 화면과 히스토리에서 지원
- **3D Touch/Haptic**: 런닝 시작/정지 시 햅틱 피드백

#### iOS 특별 고려사항
```
Safe Area: 모든 화면에서 Safe Area 준수
Status Bar: 런닝 중에는 숨김 처리
Haptic Feedback: 중요한 액션에서 적절한 햅틱 사용
Dynamic Type: 시스템 폰트 크기 설정 대응
Dark Mode: 다크 모드 완전 지원
```

### 6.2 Android 특화 가이드라인

#### 네비게이션
- **액션바**: Material Design 가이드라인 준수
- **네비게이션 드로어**: 사이드 메뉴 방식 고려
- **플로팅 액션 버튼**: 런닝 시작 버튼으로 활용

#### Material Design 컴포넌트
```
Cards: Material Design Card 스타일
Buttons: Material Design Contained/Outlined 버튼
Bottom Sheets: 설정 및 옵션 선택에서 활용
Snackbar: 간단한 피드백 메시지용
```

#### Android 특별 고려사항
```
System Navigation: Gesture navigation 완전 지원
Adaptive Icons: 런처 아이콘 adaptive 형태로 제작
Permissions: 런타임 권한 요청 UX 최적화
Background Processing: 백그라운드 런닝 추적 최적화
Multiple Screen Sizes: 다양한 화면 크기/비율 대응
```

### 6.3 공통 접근성 가이드라인
```
- 최소 터치 영역: 44px × 44px (iOS), 48dp × 48dp (Android)
- 색상 대비비: WCAG AA 기준 4.5:1 이상
- 스크린 리더 지원: 모든 인터랙티브 요소에 적절한 레이블
- 키보드 네비게이션: 모든 기능을 키보드로도 접근 가능
- 모션 감소: 시스템 설정의 모션 감소 옵션 준수
```

### 6.4 런닝 특화 UX 고려사항
```
- 런닝 중 한 손 조작: 모든 주요 버튼을 엄지손가락으로 쉽게 접근
- 야외 가독성: 강한 햇빛에서도 읽기 쉬운 대비와 크기
- 배터리 최적화: GPS 사용 시 배터리 소모 최소화 UI 피드백
- 오프라인 모드: 네트워크 연결 불안정 시 기본 기능 유지
- 운동 중 알림: 방해되지 않는 선에서 필요한 정보만 표시
```

이 디자인 가이드를 바탕으로 개발팀과 긴밀히 협업하여 사용자에게 직관적이고 매력적인 런닝 경험을 제공하는 앱을 만들어보시기 바랍니다.