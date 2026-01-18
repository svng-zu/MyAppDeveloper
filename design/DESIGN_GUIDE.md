알겠습니다. 첨부된 이미지를 참고하여 화면 기획서에 따라 UI/UX 디자인을 진행하겠습니다.

# UI/UX 디자인

## 컬러 시스템
- Primary: #DCFF00 (이미지의 형광 녹색)
- Secondary: #333333 (어두운 회색, 배경의 강조색)
- Accent: #FFFFFF (흰색, 주요 텍스트)
- Background: #121212 (매우 어두운 회색, 전체 배경)
- Text: #E0E0E0 (밝은 회색, 일반 텍스트)

## 화면별 디자인

### 스플래시 화면
**레이아웃:**
- 화면 중앙에 앱 로고와 이름 배치
- 하단에 로딩 인디케이터와 버전 정보 표시
- 전체적으로 어두운 배경에 형광 녹색 포인트 컬러 사용

**구성 요소:**
- 앱 로고: 벡터 이미지, 형광 녹색 강조
- 앱 이름: 흰색, 굵은 서체
- 로딩 인디케이터: 원형 프로그레스 바, 형광 녹색
- 버전 정보: 밝은 회색, 작은 서체

**인터랙션:**
- 자동 로그인 체크 후 메인 화면 또는 로그인 화면으로 전환

### 로그인/회원가입 화면
**레이아웃:**
- 상단에 앱 로고 배치
- 중앙에 이메일/아이디, 비밀번호 입력 필드, 로그인/회원가입 버튼 배치
- 하단에 소셜 로그인 버튼 및 비밀번호 찾기 링크 배치
- 전체적으로 어두운 배경에 형광 녹색 포인트 컬러 사용

**구성 요소:**
- 이메일/아이디 입력 필드: 흰색 텍스트, 회색 배경, 둥근 모서리
- 비밀번호 입력 필드: 흰색 텍스트, 회색 배경, 둥근 모서리
- 로그인 버튼: 형광 녹색 배경, 검은색 텍스트, 둥근 모서리
- 회원가입 버튼: 흰색 텍스트, 투명 배경, 둥근 모서리
- 소셜 로그인 버튼: 각 소셜 플랫폼 로고, 둥근 모서리
- 비밀번호 찾기 링크: 밝은 회색, 작은 서체

**인터랙션:**
- 입력 필드 터치 시 포커스 효과
- 로그인/회원가입 버튼 터치 시 애니메이션 효과
- 소셜 로그인 버튼 터치 시 해당 플랫폼 인증 페이지로 이동

### 메인 대시보드
**레이아웃:**
- 상단에 프로필 이미지와 인사말 배치
- 중앙에 오늘의 런닝 요약 카드, 이번 주 통계 카드 배치
- 하단에 빠른 런닝 시작 버튼, 진행 중인 대결 알림, 최근 대결 결과 미리보기 배치
- 하단 네비게이션 바 고정

**구성 요소:**
- 프로필 이미지: 원형, 사용자 프로필 사진
- 인사말: 흰색, 굵은 서체
- 오늘의 런닝 요약 카드: 회색 배경, 흰색 텍스트, 둥근 모서리
- 이번 주 통계 카드: 회색 배경, 흰색 텍스트, 둥근 모서리
- 빠른 런닝 시작 버튼: 형광 녹색 배경, 검은색 텍스트, 둥근 모서리
- 진행 중인 대결 알림: 강조색, 둥근 모서리
- 최근 대결 결과 미리보기: 작은 카드 형태, 둥근 모서리
- 하단 네비게이션 바: 홈, 기록, 대결, 프로필 아이콘

**인터랙션:**
- 각 카드 터치 시 해당 화면으로 이동
- 빠른 런닝 시작 버튼 터치 시 런닝 기록 화면으로 이동
- 하단 네비게이션 바 아이콘 터치 시 해당 화면으로 이동

### 런닝 기록 화면
**레이아웃:**
- 상단에 지도 뷰 (GPS 경로 표시)
- 하단에 실시간 통계 패널, 시작/일시정지/정지 버튼, 음성 안내 토글, 음악 컨트롤러, 현재 위치 버튼, 목표 설정 영역 배치
- 전체적으로 어두운 배경에 형광 녹색 포인트 컬러 사용

**구성 요소:**
- 지도 뷰: Google Maps API 사용
- 실시간 통계 패널: 거리, 시간, 페이스, 칼로리 표시, 흰색 텍스트
- 시작/일시정지/정지 버튼: 큰 원형 버튼, 형광 녹색 배경
- 음성 안내 토글: 스위치 형태, 형광 녹색 활성화
- 음악 컨트롤러: 재생/일시정지, 이전 곡, 다음 곡 버튼
- 현재 위치 버튼: 지도 위에 아이콘 형태
- 목표 설정 영역: 작은 팝업 창

**인터랙션:**
- 시작/일시정지/정지 버튼 터치 시 상태 변경
- 음성 안내 토글 터치 시 활성화/비활성화
- 현재 위치 버튼 터치 시 지도 중심 현재 위치로 이동

### 기록 상세 화면
**레이아웃:**
- 상단에 경로 지도
- 중앙에 상세 통계, 구간별 페이스 그래프
- 하단에 사진/메모 영역, 공유 버튼, 삭제/수정 옵션 배치

**구성 요소:**
- 경로 지도: Google Maps API 사용, 런닝 경로 표시
- 상세 통계: 거리, 시간, 평균/최고 속도, 칼로리, 고도 표시, 흰색 텍스트
- 구간별 페이스 그래프: 막대 그래프 형태, 형광 녹색 강조
- 사진/메모 영역: 이미지 뷰, 텍스트 입력 필드
- 공유 버튼: 아이콘 형태, 형광 녹색
- 삭제/수정 옵션: 아이콘 형태

**인터랙션:**
- 경로 지도 터치 시 확대/축소
- 공유 버튼 터치 시 공유 옵션 표시
- 삭제/수정 옵션 터치 시 해당 기능 실행

### 대결 목록 화면
**레이아웃:**
- 상단에 탭 메뉴 (진행중, 완료, 초대받은)
- 중앙에 대결 카드 리스트
- 하단에 새 대결 생성 FAB 버튼
- 검색 기능 (상단 또는 하단)

**구성 요소:**
- 탭 메뉴: 형광 녹색 활성화, 흰색 텍스트
- 대결 카드: 상대방 프로필 사진, 대결 제목 및 조건, 진행 상황 바, D-day 표시, 회색 배경, 둥근 모서리
- 새 대결 생성 FAB 버튼: 형광 녹색 배경, "+" 아이콘
- 검색 바: 입력 필드, 검색 아이콘

**인터랙션:**
- 탭 메뉴 터치 시 해당 목록 표시
- 대결 카드 터치 시 대결 상세 화면으로 이동
- 새 대결 생성 FAB 버튼 터치 시 대결 생성 화면으로 이동

### 대결 생성 화면
**레이아웃:**
- 상단에 상대방 선택 (친구 목록)
- 중앙에 대결 조건 설정, 제목 입력, 내기 설정
- 하단에 생성 버튼 배치

**구성 요소:**
- 친구 목록: 프로필 사진, 닉네임, 선택 체크박스
- 대결 조건 설정: 드롭다운 메뉴, 텍스트 입력 필드
- 제목 입력: 텍스트 입력 필드
- 내기 설정: 텍스트 입력 필드 (선택 사항)
- 생성 버튼: 형광 녹색 배경, 검은색 텍스트, 둥근 모서리

**인터랙션:**
- 친구 선택 시 체크박스 활성화
- 대결 조건 설정 변경 시 유효성 검증
- 생성 버튼 터치 시 대결 생성 요청

### 대결 상세 화면
**레이아웃:**
- 상단에 상대방 정보, 대결 조건 요약
- 중앙에 진행 상황 비교 차트
- 하단에 일별 기록 타임라인, 채팅 영역, 포기 버튼 배치

**구성 요소:**
- 상대방 정보: 프로필 사진, 닉네임
- 대결 조건 요약: 텍스트 표시
- 진행 상황 비교 차트: 막대 그래프 또는 라인 그래프
- 일별 기록 타임라인: 날짜별 기록 표시
- 채팅 영역: 메시지 입력 필드, 전송 버튼
- 포기 버튼: 빨간색 배경, 흰색 텍스트, 둥근 모서리

**인터랙션:**
- 채팅 메시지 전송 시 실시간 업데이트
- 포기 버튼 터치 시 확인 팝업 표시

### 프로필 화면
**레이아웃:**
- 상단에 프로필 사진 및 기본 정보
- 중앙에 레벨 및 뱃지 시스템, 누적 통계, 최근 활동 그래프 배치
- 하단에 달성 뱃지 갤러리, 개인 기록 배치

**구성 요소:**
- 프로필 사진: 원형, 사용자 프로필 사진
- 기본 정보: 닉네임, 소개 글
- 레벨 및 뱃지 시스템: 레벨 표시, 획득한 뱃지 아이콘
- 누적 통계: 총 거리, 시간, 대결 승률 표시
- 최근 활동 그래프: 라인 그래프 또는 막대 그래프
- 달성 뱃지 갤러리: 뱃지 아이콘 리스트
- 개인 기록: 최장 거리, 최고 속도 등 표시

**인터랙션:**
- 프로필 사진 터치 시 프로필 수정 화면으로 이동
- 뱃지 아이콘 터치 시 뱃지 상세 정보 표시

### 설정 화면
**레이아웃:**
- 목록 형태로 계정 설정, 알림 설정, 단위 설정, 음성 안내 설정, 개인정보 처리방침, 로그아웃/회원탈퇴 배치

**구성 요소:**
- 각 설정 항목: 텍스트, 스위치 또는 드롭다운 메뉴
- 로그아웃/회원탈퇴: 빨간색 텍스트

**인터랙션:**
- 각 설정 항목 터치 시 해당 설정 화면으로 이동
- 스위치 터치 시 활성화/비활성화
- 드롭다운 메뉴 터치 시 옵션 목록 표시

### 친구 목록 화면
**레이아웃:**
- 상단에 친구 검색 바
- 중앙에 친구 목록, 친구 요청 탭, 추천 친구 영역 배치
- 하단에 초대 버튼 배치

**구성 요소:**
- 친구 검색 바: 입력 필드, 검색 아이콘
- 친구 목록: 프로필 사진, 닉네임, 최근 활동
- 친구 요청 탭: 친구 요청 리스트, 수락/거절 버튼
- 추천 친구 영역: 추천 친구 리스트
- 초대 버튼: 형광 녹색 배경, 검은색 텍스트, 둥근 모서리

**인터랙션:**
- 친구 검색 시 검색 결과 표시
- 친구 요청 수락/거절 시 목록 업데이트
- 초대 버튼 터치 시 앱 초대 메시지 발송

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
  background-color: #121212;
  color: #E0E0E0;
  margin: 0;
  padding: 0;
}
.container {
  max-width: 400px;
  margin: 20px auto;
  padding: 20px;
  background-color: #222222;
  border-radius: 10px;
}
button {
  background-color: #DCFF00;
  color: #000;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}
input[type="text"], input[type="password"] {
  width: 100%;
  padding: 10px;
  margin: 5px 0;
  border: none;
  background-color: #333333;
  color: #fff;
  border-radius: 5px;
}
/* 스플래시 화면 스타일 */
#splash-screen {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
#splash-screen img {
  width: 100px;
}
/* 메인 대시보드 스타일 */
.dashboard-card {
  background-color: #333333;
  padding: 15px;
  margin-bottom: 10px;
  border-radius: 5px;
}
/* 네비게이션 바 스타일 */
nav {
  background-color: #333333;
  padding: 10px;
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: space-around;
}
nav a {
  color: #E0E0E0;
  text-decoration: none;
}
/* 런닝 기록 화면 스타일 */
#running-screen {
  padding: 20px;
}
#map {
  height: 300px;
  background-color: #444444;
  margin-bottom: 10px;
}
#start-button {
  background-color: #DCFF00;
  color: #000;
  border: none;
  padding: 15px 30px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}
</style>
</head>
<body>

<!-- 스플래시 화면 -->
<div id="splash-screen">
  <img src="https://via.placeholder.com/100" alt="App Logo">
  <h1>Running App</h1>
  <p>Version 1.0</p>
</div>

<!-- 로그인/회원가입 화면 -->
<div id="login-screen" class="container" style="display:none;">
  <h2>Login</h2>
  <input type="text" placeholder="Email">
  <input type="password" placeholder="Password">
  <button onclick="showDashboard()">Login</button>
  <p><a href="#">Forgot Password?</a></p>
  <button>Sign Up</button>
</div>

<!-- 메인 대시보드 -->
<div id="dashboard-screen" class="container" style="display:none;">
  <h2>Welcome, User!</h2>
  <div class="dashboard-card">
    <h3>Today's Run</h3>
    <p>Distance: 0 km</p>
    <p>Time: 0:00</p>
  </div>
  <div class="dashboard-card">
    <h3>Weekly Stats</h3>
    <p>Distance: 0 km</p>
    <p>Time: 0:00</p>
  </div>
  <button onclick="showRunning()">Start Running</button>
</div>

<!-- 런닝 기록 화면 -->
<div id="running-screen" style="display:none;">
  <h2>Running</h2>
  <div id="map">
    <!-- 지도 표시 영역 -->
  </div>
  <p>Distance: <span id="distance">0</span> km</p>
  <p>Time: <span id="time">0:00</span></p>
  <button id="start-button" onclick="startRunning()">Start</button>
</div>

<nav>
  <a href="#" onclick="showDashboard()">Home</a>
  <a href="#">Records</a>
  <a href="#">Challenges</a>
  <a href="#">Profile</a>
</nav>

<script>
// 인터랙션
function showLogin() {
  document.getElementById('splash-screen').style.display = 'none';
  document.getElementById('login-screen').style.display = 'block';
}

function showDashboard() {
  document.getElementById('login-screen').style.display = 'none';
  document.getElementById('dashboard-screen').style.display = 'block';
  document.getElementById('running-screen').style.display = 'none';
}

function showRunning() {
  document.getElementById('dashboard-screen').style.display = 'none';
  document.getElementById('running-screen').style.display = 'block';
}

let running = false;
let startTime;
let distance = 0;
let interval;

function startRunning() {
  running = !running;
  if (running) {
    document.getElementById('start-button').innerText = 'Stop';
    startTime = new Date().getTime();
    interval = setInterval(updateTime, 1000);
  } else {
    document.getElementById('start-button').innerText = 'Start';
    clearInterval(interval);
  }
}

function updateTime() {
  const currentTime = new Date().getTime();
  const elapsedTime = currentTime - startTime;
  const seconds = Math.floor(elapsedTime / 1000);
  document.getElementById('time').innerText = secondsToHms(seconds);
}

function secondsToHms(d) {
    d = Number(d);
    var h = Math.floor(d / 3600);
    var m = Math.floor(d % 3600 / 60);
    var s = Math.floor(d % 3600 % 60);

    var hDisplay = h > 0 ? h + (h == 1 ? " hour, " : " hours, ") : "";
    var mDisplay = m > 0 ? m + (m == 1 ? " minute, " : " minutes, ") : "";
    var sDisplay = s > 0 ? s + (s == 1 ? " second" : " seconds") : "";
    return hDisplay + mDisplay + sDisplay;
}

// 스플래시 화면에서 로그인 화면으로 자동 전환 (3초 후)
setTimeout(showLogin, 3000);
</script>

</body>
</html>
<!-- INTERACTIVE PROTOTYPE END -->
```

**참고사항:**

- HTML 프로토타입은 기본적인 화면 전환과 간단한 인터랙션만 구현했습니다. 실제 앱에서는 더 복잡한 로직과 데이터 연동이 필요합니다.
- 스타일은 기본적인 CSS를 사용하여 구현했으며, 필요에 따라 더 세련된 스타일을 적용할 수 있습니다.
- 지도 기능은 Google Maps API를 사용해야 하며, API 키가 필요합니다.

이 디자인은 첨부된 이미지의 스타일을 최대한 반영했으며, 기획서의 내용을 충실히 따랐습니다. 필요에 따라 수정 및 개선할 수 있습니다.
