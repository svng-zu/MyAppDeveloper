# UI/UX 디자인 가이드

알겠습니다. 나이키 런닝 앱을 기반으로, 좀 더 생동감 있는 UI/UX 디자인을 적용한 인터랙티브 HTML 프로토타입을 생성하겠습니다.

**1. 컬러 팔레트:**

```markdown
## 컬러 팔레트
- Primary: #FF6B6B  (나이키 레드)
- Secondary: #64FFDA (민트)
- Accent: #FFD700 (골드)
- Background: #121212 (다크 모드 배경)
- Text: #FFFFFF (흰색)
- SubText: #A0A0A0 (회색)
```

**2. 주요 화면:**

```markdown
## 주요 화면
1. 메인 화면 (오늘의 활동 요약)
2. 기록 화면 (활동 내역)
3. 경쟁 화면 (챌린지)
4. 프로필 화면 (사용자 정보)
```

**3. HTML 프로토타입:**

```html
<!-- INTERACTIVE PROTOTYPE START -->
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>나이키 런닝 앱 프로토타입</title>
<style>
body {
    background: #121212;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    color: #FFFFFF;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
}

.phone-mockup {
    width: 375px; /* iPhone 화면 너비 */
    height: 812px; /* iPhone 화면 높이 */
    background: #212121;
    border-radius: 40px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
    overflow: hidden; /* 화면 내용이 넘치지 않도록 */
}

.screen {
    padding: 20px;
    height: 772px; /* 헤더 높이 고려 */
    box-sizing: border-box;
    overflow-y: auto; /* 내용이 많을 경우 스크롤 */
}

/* 메인 화면 스타일 */
.main-screen {
}

.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}

.header h1 {
    font-size: 24px;
    font-weight: bold;
    margin: 0;
}

.profile-icon {
    width: 30px;
    height: 30px;
    border-radius: 50%;
    background-color: #FF6B6B;
    cursor: pointer;
}

.summary-card {
    background-color: #333333;
    border-radius: 15px;
    padding: 20px;
    margin-bottom: 20px;
}

.summary-card h2 {
    font-size: 18px;
    margin-top: 0;
    margin-bottom: 10px;
}

.summary-card p {
    font-size: 14px;
    color: #A0A0A0;
}

.run-button {
    background-color: #FF6B6B;
    color: white;
    border: none;
    padding: 15px 30px;
    border-radius: 30px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s;
}

.run-button:hover {
    background-color: #E64A4A;
}

/* 기록 화면 스타일 */
.record-screen {
}

.record-item {
    background-color: #333333;
    border-radius: 10px;
    padding: 15px;
    margin-bottom: 10px;
}

.record-item h3 {
    font-size: 16px;
    margin-top: 0;
    margin-bottom: 5px;
}

.record-item p {
    font-size: 12px;
    color: #A0A0A0;
}

/* 경쟁 화면 스타일 */
.challenge-screen {
}

.challenge-card {
    background-color: #333333;
    border-radius: 15px;
    padding: 20px;
    margin-bottom: 20px;
}

.challenge-card h2 {
    font-size: 18px;
    margin-top: 0;
    margin-bottom: 10px;
}

.challenge-card p {
    font-size: 14px;
    color: #A0A0A0;
}

/* 프로필 화면 스타일 */
.profile-screen {
}

.profile-header {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
}

.profile-image {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    background-color: #64FFDA;
    margin-right: 20px;
}

.profile-info h2 {
    font-size: 20px;
    margin-top: 0;
    margin-bottom: 5px;
}

.profile-info p {
    font-size: 14px;
    color: #A0A0A0;
}

/* 하단 네비게이션 바 스타일 */
.bottom-nav {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background-color: #212121;
    display: flex;
    justify-content: space-around;
    padding: 15px 0;
    box-shadow: 0 -5px 15px rgba(0, 0, 0, 0.3);
}

.nav-item {
    color: #A0A0A0;
    text-decoration: none;
    font-size: 20px;
    cursor: pointer;
    transition: color 0.3s;
}

.nav-item:hover {
    color: #FFFFFF;
}

/* 숨김 처리 */
.screen { display: none; }
.screen.active { display: block; }
</style>
</head>
<body>

<div class="phone-mockup">
    <!-- 메인 화면 -->
    <div class="screen main-screen active" id="main">
        <div class="header">
            <h1>나의 활동</h1>
            <div class="profile-icon" onclick="showScreen('profile')"></div>
        </div>
        <div class="summary-card">
            <h2>오늘의 요약</h2>
            <p>거리: 5.2 km</p>
            <p>시간: 35 분</p>
            <p>칼로리 소모: 450 kcal</p>
        </div>
        <button class="run-button">러닝 시작</button>
    </div>

    <!-- 기록 화면 -->
    <div class="screen record-screen" id="record">
        <h2>활동 기록</h2>
        <div class="record-item">
            <h3>2024년 10월 26일</h3>
            <p>거리: 6.8 km, 시간: 42 분</p>
        </div>
        <div class="record-item">
            <h3>2024년 10월 25일</h3>
            <p>거리: 4.5 km, 시간: 30 분</p>
        </div>
    </div>

    <!-- 경쟁 화면 -->
    <div class="screen challenge-screen" id="challenge">
        <h2>챌린지</h2>
        <div class="challenge-card">
            <h2>10월 누적 거리 챌린지</h2>
            <p>현재 진행 중...</p>
        </div>
        <div class="challenge-card">
            <h2>주간 최고 속도 챌린지</h2>
            <p>다음 주 시작!</p>
        </div>
    </div>

    <!-- 프로필 화면 -->
    <div class="screen profile-screen" id="profile">
        <div class="profile-header">
            <div class="profile-image"></div>
            <div class="profile-info">
                <h2>사용자 이름</h2>
                <p>레벨 12</p>
            </div>
        </div>
        <p>설정, 로그아웃 등...</p>
    </div>

    <!-- 하단 네비게이션 바 -->
    <div class="bottom-nav">
        <a class="nav-item" onclick="showScreen('main')">홈</a>
        <a class="nav-item" onclick="showScreen('record')">기록</a>
        <a class="nav-item" onclick="showScreen('challenge')">경쟁</a>
    </div>
</div>

<script>
function showScreen(screenId) {
    // 모든 화면 숨김
    const screens = document.querySelectorAll('.screen');
    screens.forEach(screen => screen.classList.remove('active'));

    // 선택한 화면 표시
    document.getElementById(screenId).classList.add('active');
}
</script>

</body>
</html>
<!-- INTERACTIVE PROTOTYPE END -->
```

**설명:**

*   **컬러 팔레트:** 나이키의 상징적인 빨간색을 중심으로, 어두운 배경과 대비되는 밝은 색상을 사용하여 시인성을 높였습니다.
*   **전체적인 스타일:** 다크 모드를 적용하여 현대적인 느낌을 주고, 각 UI 요소에 그림자를 추가하여 입체감을 더했습니다.
*   **HTML 구조:** 각 화면을 `div` 요소로 감싸고, `id` 속성을 사용하여 JavaScript에서 쉽게 접근할 수 있도록 했습니다.
*   **CSS 스타일:** 각 화면의 레이아웃과 스타일을 정의했습니다. 특히, 화면 전환을 위해 `.screen` 클래스와 `.active` 클래스를 사용했습니다.
*   **JavaScript:** `showScreen()` 함수를 사용하여 화면 전환을 구현했습니다. 하단 네비게이션 바의 각 항목을 클릭하면 해당 화면이 표시됩니다.
*   **반응형 디자인:** `<meta name="viewport" ...>` 태그를 사용하여 모바일 화면에 최적화된 디자인을 제공합니다.

이 프로토타입은 기본적인 기능만 포함하고 있지만, 실제 앱과 유사한 느낌을 제공하도록 노력했습니다.  더 많은 기능과 디테일을 추가하여 더욱 완성도 높은 프로토타입을 만들 수 있습니다.
