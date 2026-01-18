# UI/UX 디자인 가이드

## PRD 기반 러닝 앱 HTML 프로토타입 생성

러닝 앱 기획을 위한 PRD를 바탕으로 HTML 프로토타입을 생성합니다.

**1. 앱의 기본 아이디어나 컨셉:** 운동 습관 형성을 돕는 러닝 앱. 사용자의 수준에 맞는 맞춤형 러닝 플랜을 제공하고, 재미있는 도전 과제와 소셜 기능을 통해 지속적인 동기 부여를 제공합니다.

**2. 해결하고자 하는 문제나 니즈:**
*   러닝을 시작하기 어렵거나 꾸준히 유지하기 어려운 사람들을 돕습니다.
*   개인의 운동 능력과 목표에 맞는 맞춤형 러닝 경험을 제공합니다.
*   러닝을 더욱 재미있고 사회적인 활동으로 만들어줍니다.

**3. 대략적인 타겟 사용자층:**
*   러닝을 처음 시작하는 초보자
*   건강 관리를 위해 규칙적인 운동 습관을 만들고 싶은 사람
*   혼자 운동하는 것에 지루함을 느끼는 사람
*   러닝을 통해 새로운 사람들과 교류하고 싶은 사람

**4. 참고하고 있는 유사 서비스 (있다면):** Nike Run Club, Strava

이제 위에 정의된 PRD를 바탕으로 러닝 앱의 HTML 프로토타입을 생성합니다.

```
## 컬러 팔레트
- Primary: #2ecc71 (녹색 - 건강, 활력)
- Secondary: #3498db (파란색 - 신뢰, 안정)
- Accent: #f39c12 (주황색 - 에너지, 흥미)
```

```
## 주요 화면
1. 메인 화면 (오늘의 러닝 정보, 추천 플랜)
2. 러닝 기록 화면 (과거 러닝 데이터 시각화)
3. 플랜 화면 (맞춤형 러닝 플랜 제공)
4. 소셜 화면 (친구들과 챌린지, 기록 공유)
```

```html
<!-- INTERACTIVE PROTOTYPE START -->
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>러닝 앱 프로토타입</title>
<style>
/* CSS */
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
}

header {
    background-color: #2ecc71;
    color: white;
    text-align: center;
    padding: 20px 0;
}

nav {
    background-color: #3498db;
    color: white;
    padding: 10px 0;
    text-align: center;
}

nav a {
    color: white;
    text-decoration: none;
    padding: 10px 20px;
    display: inline-block;
}

.container {
    width: 80%;
    margin: 20px auto;
    background-color: white;
    padding: 20px;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.section-title {
    color: #2ecc71;
    border-bottom: 2px solid #2ecc71;
    padding-bottom: 5px;
    margin-bottom: 20px;
}

.running-info {
    display: flex;
    justify-content: space-around;
    margin-bottom: 20px;
}

.running-info div {
    text-align: center;
}

.plan-card {
    border: 1px solid #ddd;
    padding: 15px;
    margin-bottom: 15px;
    border-radius: 5px;
}

.plan-card h3 {
    color: #3498db;
}

footer {
    background-color: #333;
    color: white;
    text-align: center;
    padding: 10px 0;
    position: fixed;
    bottom: 0;
    width: 100%;
}
</style>
</head>
<body>

<header>
    <h1>러닝 앱</h1>
</header>

<nav>
    <a href="#">메인</a>
    <a href="#">기록</a>
    <a href="#">플랜</a>
    <a href="#">소셜</a>
</nav>

<div class="container">
    <section>
        <h2 class="section-title">오늘의 러닝</h2>
        <div class="running-info">
            <div>
                <h3>거리</h3>
                <p>5 km</p>
            </div>
            <div>
                <h3>시간</h3>
                <p>30 분</p>
            </div>
            <div>
                <h3>칼로리</h3>
                <p>300 kcal</p>
            </div>
        </div>
    </section>

    <section>
        <h2 class="section-title">추천 플랜</h2>
        <div class="plan-card">
            <h3>초보자를 위한 5K 플랜</h3>
            <p>8주 동안 5km 완주를 목표로 하는 플랜입니다.</p>
            <button>시작하기</button>
        </div>
        <div class="plan-card">
            <h3>인터벌 트레이닝 플랜</h3>
            <p>속도 향상을 위한 인터벌 트레이닝 플랜입니다.</p>
            <button>시작하기</button>
        </div>
    </section>
</div>

<footer>
    <p>&copy; 2023 러닝 앱</p>
</footer>

<script>
// JavaScript
// 간단한 예시: 버튼 클릭 시 알림창 표시
const buttons = document.querySelectorAll('button');
buttons.forEach(button => {
    button.addEventListener('click', () => {
        alert('플랜을 시작합니다!');
    });
});
</script>

</body>
</html>
<!-- INTERACTIVE PROTOTYPE END -->
```