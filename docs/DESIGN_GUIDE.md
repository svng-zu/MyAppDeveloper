# UI/UX 디자인 가이드

## 컬러 팔레트
- Primary: #FF6B35
- Secondary: #4ECDC4
- Accent: #45B7D1
- Background: #1A1A2E
- Text: #EAEAEA
- Card: #16213E

## 주요 화면
1. 로그인 화면
2. 메인 화면

```html
<!-- INTERACTIVE PROTOTYPE START -->
<!DOCTYPE html>
<html>
<head>
<style>
* { margin: 0; padding: 0; box-sizing: border-box; }
body { 
    background: linear-gradient(135deg, #1A1A2E, #16213E); 
    font-family: -apple-system, BlinkMacSystemFont, sans-serif; 
    padding: 20px; 
    min-height: 100vh;
}
.phone-mockup { 
    width: 320px; 
    background: linear-gradient(135deg, #2D2D44, #3A3A5C);
    border-radius: 25px; 
    padding: 8px;
    margin: 0 auto;
    box-shadow: 0 20px 40px rgba(0,0,0,0.3);
}
.screen { 
    background: #1A1A2E; 
    border-radius: 20px; 
    height: 640px; 
    overflow: hidden;
    position: relative;
}

/* 로그인 화면 */
.login-screen {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 40px 30px;
    text-align: center;
}
.logo {
    font-size: 36px;
    color: #FF6B35;
    font-weight: bold;
    margin-bottom: 10px;
}
.tagline {
    color: #EAEAEA;
    opacity: 0.8;
    margin-bottom: 50px;
    font-size: 14px;
}
.login-input {
    width: 100%;
    padding: 15px;
    margin: 10px 0;
    border: 2px solid #16213E;
    border-radius: 12px;
    background: #16213E;
    color: #EAEAEA;
    font-size: 16px;
}
.login-btn {
    width: 100%;
    padding: 15px;
    margin: 20px 0;
    border: none;
    border-radius: 12px;
    background: linear-gradient(135deg, #FF6B35, #FF8A65);
    color: white;
    font-size: 16px;
    font-weight: bold;
    cursor: pointer;
    transition: transform 0.2s;
}
.login-btn:hover {
    transform: translateY(-2px);
}
.social-btn {
    width: 100%;
    padding: 12px;
    margin: 8px 0;
    border: 2px solid #4ECDC4;
    border-radius: 12px;
    background: transparent;
    color: #4ECDC4;
    cursor: pointer;
    transition: all 0.2s;
}
.social-btn:hover {
    background: #4ECDC4;
    color: #1A1A2E;
}

/* 메인 화면 */
.main-screen {
    display: none;
    padding: 20px;
}
.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 30px;
}
.greeting {
    color: #EAEAEA;
    font-size: 18px;
}
.profile-pic {
    width: 40px;
    height: 40px;
    border-radius: 20px;
    background: linear-gradient(135deg, #FF6B35, #4ECDC4);
    cursor: pointer;
}
.stats-card {
    background: #16213E;
    border-radius: 16px;
    padding: 20px;
    margin-bottom: 20px;
}
.stats-title {
    color: #4ECDC4;
    font-size: 14px;
    margin-bottom: 10px;
}
.stats-value {
    color: #EAEAEA;
    font-size: 24px;
    font-weight: bold;
}
.start-run-btn {
    width: 100%;
    padding: 20px;
    background: linear-gradient(135deg, #FF6B35, #FF8A65);
    border: none;
    border-radius: 50px;
    color: white;
    font-size: 18px;
    font-weight: bold;
    cursor: pointer;
    margin: 20px 0;
    transition: transform 0.2s;
}
.start-run-btn:hover {
    transform: scale(1.05);
}
.ad-banner {
    background: linear-gradient(135deg, #45B7D1, #4ECDC4);
    border-radius: 12px;
    padding: 15px;
    color: white;
    text-align: center;
    margin: 15px 0;
    font-size: 14px;
    cursor: pointer;
}
.bottom-nav {
    position: absolute;
    bottom: 0;
    width: 100%;
    background: #16213E;
    display: flex;
    justify-content: space-around;
    padding: 15px 0;
}
.nav-item {
    color: #EAEAEA;
    opacity: 0.6;
    font-size: 12px;
    cursor: pointer;
    transition: opacity 0.2s;
}
.nav-item.active, .nav-item:hover {
    opacity: 1;
    color: #FF6B35;
}
</style>
</head>
<body>
<div class="phone-mockup">
    <!-- 로그인 화면 -->
    <div class="screen login-screen" id="loginScreen">
        <div class="logo">🏃‍♂️ RunTogether</div>
        <div class="tagline">함께 달리는 즐거움</div>
        
        <input type="email" class="login-input" placeholder="이메일">
        <input type="password" class="login-input" placeholder="비밀번호">
        
        <button class="login-btn" onclick="showMainScreen()">로그인</button>
        
        <div style="margin: 20px 0; color: #EAEAEA; opacity: 0.6;">또는</div>
        
        <button class="social-btn">🍎 Apple로 계속하기</button>
        <button class="social-btn">📱 카카오로 계속하기</button>
        <button class="social-btn">🌐 Google로 계속하기</button>
        
        <div style="margin-top: 30px; color: #EAEAEA; opacity: 0.6; font-size: 12px;">
            계정이 없으신가요? <span style="color: #FF6B35; cursor: pointer;">회원가입</span>
        </div>
    </div>

    <!-- 메인 화면 -->
    <div class="screen main-screen" id="mainScreen">
        <div class="header">
            <div>
                <div class="greeting">안녕하세요! 👋</div>
                <div style="color: #FF6B35; font-weight: bold;">김러너님</div>
            </div>
            <div class="profile-pic" onclick="showLoginScreen()"></div>
        </div>

        <div class="stats-card">
            <div class="stats-title">오늘의 기록</div>
            <div style="display: flex; justify-content: space-between;">
                <div>
                    <div class="stats-value">3.2km</div>
                    <div style="color: #EAEAEA; opacity: 0.6; font-size: 12px;">거리</div>
                </div>
                <div>
                    <div class="stats-value">24:15</div>
                    <div style="color: #EAEAEA; opacity: 0.6; font-size: 12px;">시간</div>
                </div>
            </div>
        </div>

        <button class="start-run-btn">🏃‍♂️ 러닝 시작하기</button>

        <div class="ad-banner">
                스포츠웨어 50% 할인! 지금 확인하세요 →
        </div>

        <div class="stats-card">
            <div class="stats-title">이주의 챌린지</div>
            <div style="color: #EAEAEA;">주 3회 이상 러닝하기</div>
            <div style="background: #FF6B35; height: 4px; border-radius: 2px; margin: 8px 0; width: 60%;"></div>
            <div style="color: #EAEAEA; opacity: 0.6; font-size: 12px;">2/3 완료</div>
        </div>

        <div class="bottom-nav">
            <div class="nav-item active">홈</div>
            <div class="nav-item">기록</div>
            <div class="nav-item">커뮤니티</div>
            <div class="nav-item">프로필</div>
        </div>
    </div>
</div>

<script>
function showMainScreen() {
    document.getElementById('loginScreen').style.display = 'none';
    document.getElementById('mainScreen').style.display = 'block';
}

function showLoginScreen() {
    document.getElementById('loginScreen').style.display = 'flex';
    document.getElementById('mainScreen').style.display = 'none';
}

// 네비게이션 클릭 효과
document.querySelectorAll('.nav-item').forEach(item => {
    item.addEventListener('click', function() {
        document.querySelectorAll('.nav-item').forEach(nav => nav.classList.remove('active'));
        this.classList.add('active');
    });
});

// 광고 배너 클릭 효과
document.querySelector('.ad-banner').addEventListener('click', function() {
    this.style.transform = 'scale(0.95)';
    setTimeout(() => {
        this.style.transform = 'scale(1)';
    }, 200);
});
</script>
</body>
</html>
<!-- INTERACTIVE PROTOTYPE END -->
```