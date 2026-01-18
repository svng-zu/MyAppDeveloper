알겠습니다. 전문 UI/UX 디자이너로서 기획서 내용을 기반으로 모든 화면을 디자인하고 HTML 프로토타입을 제공하겠습니다.

# UI/UX 디자인

## 컬러 시스템
- Primary: #4CAF50 (밝은 녹색, 런닝의 활력과 건강함 상징)
- Secondary: #2E7D32 (진한 녹색, Primary의 보조 색상)
- Accent: #FFC107 (밝은 노란색, 포인트 컬러)
- Background: #F5F5F5 (밝은 회색, 깔끔하고 가독성 높임)
- Text: #212121 (진한 회색, 가독성 확보)

## 화면별 디자인

### 스플래시/로그인 화면
**레이아웃:**
화면 중앙에 앱 로고를 배치하고, 하단에 소셜 로그인 버튼 및 게스트 모드 버튼을 배치합니다. 배경은 Primary 컬러를 사용하거나, 관련 이미지(러닝하는 사람)를 사용합니다.

**구성 요소:**
- 앱 로고: 중앙 배치, 앱 아이덴티티 강조
- 소셜 로그인 버튼 (구글, 카카오, 애플): 하단 가로 배치, 각 플랫폼의 디자인 가이드라인 준수
- 이용약관 및 개인정보처리방침 링크: 하단 텍스트 링크, 작은 글씨 크기
- 게스트 모드 진입 버튼: 하단 소셜 로그인 버튼 아래 배치, 덜 강조된 스타일

**인터랙션:**
- 소셜 로그인 버튼 클릭 시 해당 플랫폼 로그인 화면으로 이동
- 이용약관 및 개인정보처리방침 링크 클릭 시 해당 내용 표시
- 게스트 모드 진입 버튼 클릭 시 메인 홈 화면으로 이동 (제한된 기능)

### 메인 홈 화면
**레이아웃:**
상단에 프로필 및 알림 아이콘, 중간에 오늘의 런닝 요약 카드 및 통계 그래프, 하단에 "런닝 시작" 버튼 및 기타 기능 버튼을 배치합니다.

**구성 요소:**
- 상단 프로필 아이콘 및 알림 아이콘: 우측 상단 배치, 원형 프로필 이미지 및 알림 배지
- 오늘의 런닝 요약 카드 (거리, 시간, 칼로리): 중앙 상단 배치, 직관적인 숫자 및 아이콘 표시
- 주간/월간 통계 그래프: 오늘의 런닝 요약 카드 아래 배치, 막대 또는 선 그래프
- "런닝 시작" 메인 버튼: 화면 중앙 하단 배치, Primary 컬러, 크고 눈에 띄는 스타일
- "실시간 대결" 버튼: "런닝 시작" 버튼 옆에 배치, Secondary 컬러
- 최근 대결 결과 미리보기: 하단 배치, 작은 카드 형태
- 날씨 정보 위젯: 상단 좌측 배치, 날씨 아이콘 및 온도 표시
- 추천 코스 카드: 하단 배치, 이미지와 간단한 설명

**인터랙션:**
- 프로필 아이콘 클릭 시 프로필 화면으로 이동
- 알림 아이콘 클릭 시 알림 목록 화면으로 이동
- "런닝 시작" 버튼 클릭 시 런닝 준비 화면으로 이동
- "실시간 대결" 버튼 클릭 시 실시간 대결 화면으로 이동
- 최근 대결 결과 미리보기 클릭 시 해당 대결 결과 화면으로 이동
- 추천 코스 카드 클릭 시 해당 코스 상세 정보 화면으로 이동

### 런닝 준비 화면
**레이아웃:**
상단에 목표 설정 섹션, 중간에 런닝 모드 선택 및 음악 연동 버튼, 하단에 GPS 신호 상태 표시 및 "시작하기" 버튼을 배치합니다.

**구성 요소:**
- 목표 설정 섹션 (거리/시간/칼로리): 상단 배치, 입력 필드 및 선택 옵션
- 런닝 모드 선택 (일반/대결 대기): 중간 배치, 라디오 버튼 또는 스위치
- 음악 연동 버튼: 중간 배치, Spotify/Apple Music 아이콘
- GPS 신호 상태 표시: 하단 배치, GPS 아이콘 및 신호 강도 표시
- 런닝 코스 미리보기 지도: 중간 배치, 작은 지도 영역
- "시작하기" 버튼: 하단 배치, Primary 컬러, 크고 눈에 띄는 스타일

**인터랙션:**
- 목표 설정 섹션에서 목표값 입력 및 선택
- 런닝 모드 선택 (일반/대결 대기)
- 음악 연동 버튼 클릭 시 해당 음악 앱 연동
- "시작하기" 버튼 클릭 시 런닝 기록 화면으로 이동

### 런닝 기록 화면
**레이아웃:**
상단에 실시간 지도, 중간에 주요 지표 (속도, 거리, 시간, 심박수), 하단에 랩타임 기록 버튼 및 일시정지/재개/종료 버튼을 배치합니다.

**구성 요소:**
- 실시간 지도 (현재 위치, 경로): 상단 배치, 지도 라이브러리 사용
- 주요 지표 (속도, 거리, 시간, 심박수): 중간 배치, 큰 숫자 및 단위 표시
- 랩타임 기록 버튼: 하단 배치, 버튼 스타일
- 일시정지/재개/종료 버튼: 하단 배치, 아이콘 및 텍스트
- 음성 코칭 on/off 스위치: 중간 배치, 스위치 스타일
- 대결 상대 정보 (대결 모드 시): 상단 배치, 프로필 이미지 및 닉네임

**인터랙션:**
- 랩타임 기록 버튼 클릭 시 랩타임 기록
- 일시정지 버튼 클릭 시 런닝 일시정지
- 재개 버튼 클릭 시 런닝 재개
- 종료 버튼 클릭 시 런닝 종료 및 런닝 결과 화면으로 이동
- 음성 코칭 on/off 스위치 전환

### 실시간 대결 화면
**레이아웃:**
상단에 대결 상대 프로필 정보 및 실시간 순위, 중간에 나와 상대방 진행 상황 비교 그래프, 하단에 응원 메시지 전송 버튼 및 포기/계속하기 버튼을 배치합니다.

**구성 요소:**
- 대결 상대 프로필 정보: 상단 배치, 프로필 이미지 및 닉네임
- 실시간 순위 표시: 상단 배치, 숫자 및 순위 아이콘
- 나와 상대방 진행 상황 비교 그래프: 중간 배치, 선 또는 막대 그래프
- 대결 조건 표시 (거리/시간 기준): 중간 배치, 텍스트 설명
- 응원 메시지 전송 버튼: 하단 배치, 메시지 아이콘 및 텍스트
- 포기/계속하기 버튼: 하단 배치, Primary 컬러 (계속하기), Secondary 컬러 (포기)
- 실시간 채팅 (선택사항): 하단 배치, 채팅 입력 필드 및 메시지 목록

**인터랙션:**
- 응원 메시지 전송 버튼 클릭 시 응원 메시지 전송
- 포기 버튼 클릭 시 대결 포기 및 패배 처리
- 계속하기 버튼 클릭 시 대결 계속 진행

### 런닝 결과 화면
**레이아웃:**
상단에 전체 경로 지도, 중간에 주요 성과 요약 (거리, 시간, 속도, 칼로리) 및 구간별 상세 분석, 하단에 대결 결과, 개인 기록 갱신 알림, SNS 공유 버튼, 저장하기 버튼을 배치합니다.

**구성 요소:**
- 전체 경로 지도: 상단 배치, 지도 라이브러리 사용
- 주요 성과 요약 (거리, 시간, 속도, 칼로리): 중간 배치, 큰 숫자 및 단위 표시
- 구간별 상세 분석 (랩타임, 페이스): 중간 배치, 표 또는 그래프
- 대결 결과 (승/패, 상대 정보): 하단 배치, 텍스트 및 프로필 이미지
- 개인 기록 갱신 알림: 하단 배치, 알림 메시지
- SNS 공유 버튼: 하단 배치, 각 SNS 아이콘
- 저장하기 버튼: 하단 배치, Primary 컬러

**인터랙션:**
- SNS 공유 버튼 클릭 시 해당 SNS 공유 화면으로 이동
- 저장하기 버튼 클릭 시 운동 데이터 저장 및 메인 홈 화면으로 이동

### 기록 관리 화면
**레이아웃:**
상단에 날짜별 기록 리스트, 중간에 필터링 옵션 및 통계 차트, 하단에 개인 기록 현황 및 데이터 내보내기 버튼을 배치합니다.

**구성 요소:**
- 날짜별 기록 리스트: 상단 배치, 날짜, 거리, 시간 등 정보 표시
- 필터링 옵션 (기간, 거리, 대결 여부): 중간 배치, 드롭다운 또는 체크박스
- 통계 차트 (주간/월간/년간): 중간 배치, 막대 또는 선 그래프
- 개인 기록 현황: 하단 배치, 총 거리, 시간, 횟수 등 정보 표시
- 대결 승률 통계: 하단 배치, 파이 차트 또는 막대 그래프
- 즐겨찾기 코스: 하단 배치, 코스 목록
- 데이터 내보내기 버튼: 하단 배치, CSV/PDF 선택 옵션

**인터랙션:**
- 날짜별 기록 리스트에서 특정 기록 클릭 시 해당 기록 상세 정보 화면으로 이동
- 필터링 옵션 선택 시 기록 리스트 업데이트
- 데이터 내보내기 버튼 클릭 시 CSV/PDF 파일 다운로드

### 프로필 화면
**레이아웃:**
상단에 프로필 사진 및 닉네임, 중간에 총 런닝 통계 및 뱃지/업적 컬렉션, 하단에 개인정보 수정 버튼, 앱 설정, 로그아웃 버튼을 배치합니다.

**구성 요소:**
- 프로필 사진 및 닉네임: 상단 배치, 원형 프로필 이미지 및 텍스트
- 총 런닝 통계 (총 거리, 시간, 횟수): 중간 배치, 숫자 및 단위 표시
- 뱃지/업적 컬렉션: 중간 배치, 뱃지 이미지 및 설명
- 대결 전적 (승/무/패): 중간 배치, 숫자 및 텍스트
- 개인정보 수정 버튼: 하단 배치, 버튼 스타일
- 앱 설정 (알림, 단위, 음성안내): 하단 배치, 스위치 또는 체크박스
- 로그아웃 버튼: 하단 배치, Secondary 컬러

**인터랙션:**
- 프로필 사진 클릭 시 프로필 사진 변경 화면으로 이동
- 개인정보 수정 버튼 클릭 시 개인정보 수정 화면으로 이동
- 앱 설정 변경 시 해당 설정 저장
- 로그아웃 버튼 클릭 시 로그아웃 및 스플래시/로그인 화면으로 이동

### 랭킹 화면
**레이아웃:**
상단에 탭 메뉴 (전체/지역/친구), 중간에 기간별 랭킹 및 카테고리별 랭킹, 하단에 내 순위 하이라이트 및 상위 랭커 프로필을 배치합니다.

**구성 요소:**
- 탭 메뉴 (전체/지역/친구): 상단 배치, 탭 스타일
- 기간별 랭킹 (일간/주간/월간): 중간 배치, 라디오 버튼 또는 드롭다운
- 카테고리별 랭킹 (거리/시간/대결승률): 중간 배치, 라디오 버튼 또는 드롭다운
- 내 순위 하이라이트: 하단 배치, 강조된 스타일
- 상위 랭커 프로필: 하단 배치, 프로필 이미지 및 닉네임
- 시상대 UI (1,2,3위): 상단 배치, 시상대 이미지 및 프로필

**인터랙션:**
- 탭 메뉴 선택 시 해당 랭킹 화면으로 이동
- 기간별 랭킹 및 카테고리별 랭킹 선택 시 랭킹 업데이트
- 상위 랭커 프로필 클릭 시 해당 사용자 프로필 화면으로 이동

### 친구/커뮤니티 화면
**레이아웃:**
상단에 친구 목록 및 상태, 중간에 최근 활동 피드 및 커뮤니티 게시판, 하단에 그룹 대결 참여 버튼 및 메시지 기능을 배치합니다.

**구성 요소:**
- 친구 목록 및 상태: 상단 배치, 프로필 이미지, 닉네임, 상태 메시지
- 친구 추가 버튼 (ID/연락처): 상단 배치, 버튼 스타일
- 최근 활동 피드: 중간 배치, 활동 내용 및 시간 표시
- 커뮤니티 게시판: 중간 배치, 게시글 목록
- 그룹 대결 참여 버튼: 하단 배치, 버튼 스타일
- 메시지 기능: 하단 배치, 채팅 입력 필드 및 메시지 목록

**인터랙션:**
- 친구 목록에서 친구 클릭 시 해당 친구 프로필 화면으로 이동
- 친구 추가 버튼 클릭 시 친구 추가 화면으로 이동
- 활동 피드에서 게시글 클릭 시 해당 게시글 상세 정보 화면으로 이동
- 그룹 대결 참여 버튼 클릭 시 그룹 대결 참여 화면으로 이동
- 메시지 기능에서 메시지 전송

## HTML 프로토타입

```html
<!-- INTERACTIVE PROTOTYPE START -->
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Running App Prototype</title>
<style>
/* 전체 스타일 */
body {
    font-family: sans-serif;
    margin: 0;
    padding: 0;
    background-color: #F5F5F5;
    color: #212121;
}

/* 공통 요소 스타일 */
.container {
    max-width: 600px;
    margin: 20px auto;
    padding: 20px;
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

button {
    background-color: #4CAF50;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #2E7D32;
}

input[type="text"],
input[type="number"] {
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
    margin-bottom: 10px;
}

/* 화면별 스타일 (예시) */
#splash-login {
    text-align: center;
}

#main-home .summary-card {
    background-color: #E8F5E9;
    padding: 15px;
    border-radius: 5px;
    margin-bottom: 10px;
}
</style>
</head>
<body>

<!-- 스플래시/로그인 화면 -->
<div id="splash-login" class="container">
    <h1>Running App</h1>
    <p>소셜 로그인</p>
    <button>Google 로그인</button><br><br>
    <button>카카오 로그인</button><br><br>
    <button>Apple 로그인</button><br><br>
    <button onclick="goToMainHome()">게스트 모드</button>
</div>

<!-- 메인 홈 화면 -->
<div id="main-home" class="container" style="display: none;">
    <h2>메인 홈</h2>
    <div class="summary-card">
        <h3>오늘의 런닝</h3>
        <p>거리: 2.5 km</p>
        <p>시간: 20 분</p>
        <p>칼로리: 150 kcal</p>
    </div>
    <button onclick="goToRunningPrepare()">런닝 시작</button>
    <button onclick="goToRealtimeBattle()">실시간 대결</button>
</div>

<!-- 런닝 준비 화면 -->
<div id="running-prepare" class="container" style="display: none;">
    <h2>런닝 준비</h2>
    <p>목표 설정</p>
    <input type="number" placeholder="거리 (km)"><br>
    <input type="number" placeholder="시간 (분)"><br>
    <button onclick="startRunning()">시작하기</button>
</div>

<!-- 런닝 기록 화면 -->
<div id="running-record" class="container" style="display: none;">
    <h2>런닝 기록</h2>
    <p>실시간 데이터</p>
    <p>속도: 5 km/h</p>
    <p>거리: 3 km</p>
    <p>시간: 25 분</p>
    <button onclick="endRunning()">종료</button>
</div>

<!-- 실시간 대결 화면 -->
<div id="realtime-battle" class="container" style="display: none;">
    <h2>실시간 대결</h2>
    <p>상대방 찾는 중...</p>
    <p>상대방: (미구현)</p>
    <button>포기</button>
</div>

<!-- 런닝 결과 화면 -->
<div id="running-result" class="container" style="display: none;">
    <h2>런닝 결과</h2>
    <p>총 거리: 5 km</p>
    <p>총 시간: 45 분</p>
    <p>평균 속도: 6.7 km/h</p>
    <button onclick="goToMainHome()">홈으로</button>
</div>

<!-- 기록 관리 화면 -->
<div id="record-management" class="container" style="display: none;">
    <h2>기록 관리</h2>
    <p>날짜별 기록</p>
    <p>(미구현)</p>
    <button onclick="goToMainHome()">홈으로</button>
</div>

<!-- 프로필 화면 -->
<div id="profile" class="container" style="display: none;">
    <h2>프로필</h2>
    <p>사용자 정보</p>
    <p>(미구현)</p>
    <button onclick="goToMainHome()">홈으로</button>
</div>

<!-- 랭킹 화면 -->
<div id="ranking" class="container" style="display: none;">
    <h2>랭킹</h2>
    <p>전체 랭킹</p>
    <p>(미구현)</p>
    <button onclick="goToMainHome()">홈으로</button>
</div>

<!-- 친구/커뮤니티 화면 -->
<div id="community" class="container" style="display: none;">
    <h2>커뮤니티</h2>
    <p>친구 목록</p>
    <p>(미구현)</p>
    <button onclick="goToMainHome()">홈으로</button>
</div>

<script>
// 화면 전환 함수
function hideAllScreens() {
    document.getElementById('splash-login').style.display = 'none';
    document.getElementById('main-home').style.display = 'none';
    document.getElementById('running-prepare').style.display = 'none';
    document.getElementById('running-record').style.display = 'none';
    document.getElementById('realtime-battle').style.display = 'none';
    document.getElementById('running-result').style.display = 'none';
    document.getElementById('record-management').style.display = 'none';
    document.getElementById('profile').style.display = 'none';
    document.getElementById('ranking').style.display = 'none';
    document.getElementById('community').style.display = 'none';
}

function goToMainHome() {
    hideAllScreens();
    document.getElementById('main-home').style.display = 'block';
}

function goToRunningPrepare() {
    hideAllScreens();
    document.getElementById('running-prepare').style.display = 'block';
}

function startRunning() {
    hideAllScreens();
    document.getElementById('running-record').style.display = 'block';
}

function endRunning() {
    hideAllScreens();
    document.getElementById('running-result').style.display = 'block';
}

function goToRealtimeBattle() {
    hideAllScreens();
    document.getElementById('realtime-battle').style.display = 'block';
}

// 초기 화면 설정
hideAllScreens();
document.getElementById('splash-login').style.display = 'block';
</script>
</body>
</html>
<!-- INTERACTIVE PROTOTYPE END -->
```

**참고사항:**
*   **디자인 상세:** 위 HTML은 기본적인 레이아웃과 화면 전환을 보여주는 프로토타입입니다. 실제 앱에서는 더 많은 CSS 스타일링, 이미지, 아이콘 및 인터랙션이 필요합니다.
*   **데이터:** HTML 프로토타입은 정적인 데이터만 포함하고 있습니다. 실제 앱에서는 API 연동을 통해 실시간 데이터를 표시해야 합니다.
*   **반응형 디자인:** 이 프로토타입은 반응형 디자인을 고려하지 않았습니다. 다양한 화면 크기를 지원하기 위해서는 미디어 쿼리를 사용해야 합니다.
*   **상태 관리:** 간단한 화면 전환만 구현되어 있습니다. 실제 앱에서는 상태 관리 라이브러리(예: React, Vue.js)를 사용하여 앱의 상태를 효율적으로 관리해야 합니다.

이 디자인 가이드라인과 HTML 프로토타입을 기반으로 실제 앱 개발을 진행하시면 됩니다. 추가적인 질문이나 수정 사항이 있으시면 언제든지 문의해주세요.
