# UI/UX 디자인 가이드

알겠습니다. 런닝 배틀 앱의 PRD를 기반으로 디자인 컨셉, 주요 화면, HTML 프로토타입을 생성해 드리겠습니다.

## 1. 컬러 팔레트

```
## 컬러 팔레트
- Primary: #4CAF50 (싱그러운 런닝을 연상시키는 녹색)
- Secondary: #2196F3 (활동적이고 시원한 느낌의 파란색)
- Accent: #FF9800 (에너지 넘치는 주황색, 강조 색상)
```

## 2. 주요 화면

```
## 주요 화면
1.  로그인/회원가입 화면
2.  프로필 설정 화면
3.  메인 화면 (배틀 찾기, 내 기록, 친구 목록)
4.  배틀 매칭 화면
5.  실시간 배틀 화면
6.  배틀 결과 화면
```

## 3. HTML 프로토타입

```html
<!-- INTERACTIVE PROTOTYPE START -->
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>RunBattle</title>
<style>
/* CSS */
body {
    font-family: 'Arial', sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
    color: #333;
}

.container {
    max-width: 600px;
    margin: 20px auto;
    padding: 20px;
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1, h2 {
    color: #4CAF50;
    text-align: center;
}

button {
    background-color: #4CAF50;
    color: white;
    padding: 10px 20px;
    margin: 5px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
}

button:hover {
    opacity: 0.8;
}

input[type="text"], input[type="password"] {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}

.profile-image {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    object-fit: cover;
    margin: 10px auto;
    display: block;
}

.battle-stats {
    display: flex;
    justify-content: space-around;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
    margin-bottom: 10px;
}

.battle-stats div {
    text-align: center;
}

#map {
    height: 300px;
    background-color: #eee;
    margin-bottom: 10px;
    text-align: center;
    line-height: 300px;
}

/* 추가 스타일 (선택 사항) */
.social-login {
    display: flex;
    justify-content: center;
    margin-top: 15px;
}

.social-login button {
    background-color: #2196F3; /* 파란색 계열 */
    margin: 0 5px;
}

.footer {
    text-align: center;
    margin-top: 20px;
    color: #777;
}
</style>
</head>
<body>

<div class="container">
    <h1>RunBattle</h1>

    <!-- 로그인/회원가입 화면 -->
    <div id="login-screen">
        <h2>로그인</h2>
        <input type="text" id="username" placeholder="사용자 이름">
        <input type="password" id="password" placeholder="비밀번호">
        <button onclick="goToMain()">로그인</button>
        <p>또는</p>
        <div class="social-login">
            <button>Google</button>
            <button>Kakao</button>
        </div>
        <p>계정이 없으신가요? <a href="#" onclick="showSignup()">회원가입</a></p>
    </div>

    <div id="signup-screen" style="display:none;">
        <h2>회원가입</h2>
        <input type="text" id="new-username" placeholder="사용자 이름">
        <input type="password" id="new-password" placeholder="비밀번호">
        <button onclick="goToMain()">회원가입</button>
        <p>이미 계정이 있으신가요? <a href="#" onclick="showLogin()">로그인</a></p>
    </div>

    <!-- 프로필 설정 화면 -->
    <div id="profile-screen" style="display:none;">
        <h2>프로필 설정</h2>
        <img src="placeholder-profile.png" alt="프로필 사진" class="profile-image">
        <input type="text" id="nickname" placeholder="닉네임">
        <input type="text" id="running-level" placeholder="런닝 레벨 (초급, 중급, 고급)">
        <button onclick="goToMain()">저장</button>
    </div>

    <!-- 메인 화면 -->
    <div id="main-screen" style="display:none;">
        <h2>메인 화면</h2>
        <button onclick="goToMatch()">배틀 찾기</button>
        <button onclick="showRecords()">내 기록</button>
        <button onclick="showFriends()">친구 목록</button>
    </div>

    <!-- 배틀 매칭 화면 -->
    <div id="match-screen" style="display:none;">
        <h2>배틀 매칭</h2>
        <p>상대방을 찾는 중...</p>
        <button onclick="startBattle()">매칭 시작</button>
    </div>

    <!-- 실시간 배틀 화면 -->
    <div id="battle-screen" style="display:none;">
        <h2>실시간 배틀</h2>
        <div class="battle-stats">
            <div>내 페이스: <span id="my-pace">4:30</span></div>
            <div>상대 페이스: <span id="opponent-pace">4:45</span></div>
        </div>
        <div id="map">지도 (GPS 연동)</div>
        <button onclick="endBattle()">포기</button>
    </div>

    <!-- 배틀 결과 화면 -->
    <div id="result-screen" style="display:none;">
        <h2>배틀 결과</h2>
        <p>승리!</p>
        <p>획득한 점수: +10</p>
        <button onclick="goToMain()">메인으로</button>
    </div>

    <div class="footer">
        &copy; 2024 RunBattle
    </div>
</div>

<script>
// JavaScript
function goToMain() {
    document.getElementById('login-screen').style.display = 'none';
    document.getElementById('signup-screen').style.display = 'none';
    document.getElementById('profile-screen').style.display = 'none';
    document.getElementById('main-screen').style.display = 'block';
    document.getElementById('match-screen').style.display = 'none';
    document.getElementById('battle-screen').style.display = 'none';
    document.getElementById('result-screen').style.display = 'none';
}

function goToMatch() {
    document.getElementById('main-screen').style.display = 'none';
    document.getElementById('match-screen').style.display = 'block';
}

function startBattle() {
    document.getElementById('match-screen').style.display = 'none';
    document.getElementById('battle-screen').style.display = 'block';
}

function endBattle() {
    document.getElementById('battle-screen').style.display = 'none';
    document.getElementById('result-screen').style.display = 'block';
}

function showRecords() {
    alert('내 기록 화면으로 이동');
}

function showFriends() {
    alert('친구 목록 화면으로 이동');
}

function showSignup() {
    document.getElementById('login-screen').style.display = 'none';
    document.getElementById('signup-screen').style.display = 'block';
}

function showLogin() {
    document.getElementById('signup-screen').style.display = 'none';
    document.getElementById('login-screen').style.display = 'block';
}

// 초기 화면 설정 (로그인 화면)
document.getElementById('login-screen').style.display = 'block';
</script>

</body>
</html>
<!-- INTERACTIVE PROTOTYPE END -->
```

**설명:**

*   **컬러 팔레트:** 런닝 앱에 어울리는 활기차고 건강한 느낌의 색상들을 선택했습니다.
*   **주요 화면:** PRD에 명시된 핵심 기능들을 중심으로 화면들을 구성했습니다.
*   **HTML 프로토타입:**
    *   각 화면을 `div`로 감싸고, CSS를 사용하여 기본적인 스타일을 적용했습니다.
    *   JavaScript를 사용하여 버튼 클릭 시 화면 전환이 가능하도록 구현했습니다.
    *   실제 앱처럼 보이도록 기본적인 UI 요소들을 추가했습니다.
    *   로그인, 메인, 매칭, 배틀, 결과 화면을 구현하고 JavaScript로 화면 전환을 시뮬레이션했습니다.
    *   프로필 설정 화면, 내 기록 화면, 친구 목록 화면은 간단한 알림으로 대체했습니다.
    *   지도는 간단한 placeholder로 표시했습니다.

**추가 설명:**

*   **반응형 디자인:** `<meta name="viewport" ...>` 태그를 사용하여 모바일 환경에서도 잘 보이도록 했습니다.
*   **프로필 사진:** `placeholder-profile.png` 파일이 필요합니다.  적절한 이미지를 추가하거나, CSS에서 배경색을 지정할 수 있습니다.
*   **GPS 연동:** 실제 지도 API (예: Google Maps API)를 사용하여 구현해야 합니다.
*   **실시간 배틀:** WebSocket 등을 사용하여 실시간 데이터 통신을 구현해야 합니다.
*   **데이터베이스 연동:** 사용자 데이터, 런닝 기록 등을 저장하고 관리하기 위해 데이터베이스 연동이 필요합니다.
*   **스타일:** CSS를 더 자세하게 작성하여 앱의 디자인을 개선할 수 있습니다.

이 프로토타입은 기본적인 기능을 시뮬레이션하는 데 중점을 두었으며, 실제 앱 개발을 위해서는 더 많은 기능과 디자인 개선이 필요합니다.
