# UI/UX 디자인 가이드

## 컬러 팔레트
- Primary: #6366F1 (생생한 파랑/보라)
- Secondary: #10B981 (밝은 녹색)
- Accent: #F59E0B (따뜻한 주황)
- Background: #0F172A (깊은 네이비)
- Surface: #1E293B (어두운 회색)
- Text: #F8FAFC (밝은 흰색)

## 주요 화면
1. 로그인 화면
2. 메인 대시보드

```html
<!-- INTERACTIVE PROTOTYPE START -->
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Amazing App Prototype</title>
<style>
/* Reset & General Styles */
* { margin: 0; padding: 0; box-sizing: border-box; }
body {
    background: linear-gradient(135deg, #0F172A 0%, #1E293B 100%);
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    color: #F8FAFC;
    padding: 40px 20px;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

.container {
    max-width: 480px; /* 모바일 화면에 맞게 조정 */
    width: 100%;
    margin: 0 auto;
    padding: 20px;
}

/* Login Screen Styles */
.login-screen {
    background: rgba(30, 41, 59, 0.8);
    backdrop-filter: blur(15px);
    border: 1px solid rgba(148, 163, 184, 0.1);
    border-radius: 30px;
    padding: 40px;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
    text-align: center;
    animation: fadeInUp 0.5s ease-out;
}

.login-screen h1 {
    font-size: 36px;
    font-weight: 700;
    margin-bottom: 30px;
    background: linear-gradient(135deg, #6366F1, #8B5CF6);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}

.input-group {
    margin-bottom: 25px;
    text-align: left;
}

.input-group label {
    display: block;
    font-size: 16px;
    font-weight: 500;
    margin-bottom: 8px;
    color: #CBD5E1;
}

.input-field {
    width: 100%;
    padding: 14px 20px;
    font-size: 16px;
    border-radius: 12px;
    border: none;
    background-color: rgba(47, 57, 73, 0.8);
    color: #F8FAFC;
    outline: none;
    transition: all 0.3s;
}

.input-field:focus {
    box-shadow: 0 4px 12px rgba(99, 102, 241, 0.3);
}

.btn-primary {
    background: linear-gradient(135deg, #6366F1, #8B5CF6);
    color: white;
    border: none;
    padding: 16px 32px;
    border-radius: 16px;
    font-size: 18px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s;
    box-shadow: 0 4px 15px rgba(99, 102, 241, 0.4);
    width: 100%;
    margin-top: 20px;
}

.btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 25px rgba(99, 102, 241, 0.6);
}

.btn-primary:active {
    transform: translateY(0);
}

/* Dashboard Styles */
.dashboard {
    background: rgba(30, 41, 59, 0.8);
    backdrop-filter: blur(15px);
    border: 1px solid rgba(148, 163, 184, 0.1);
    border-radius: 30px;
    padding: 30px;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
    animation: fadeInUp 0.5s ease-out;
}

.dashboard-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 25px;
}

.dashboard-title {
    font-size: 28px;
    font-weight: 700;
    background: linear-gradient(135deg, #6366F1, #8B5CF6);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}

.profile-icon {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background-color: #334155;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 20px;
    font-weight: bold;
    cursor: pointer;
    transition: all 0.3s;
}

.profile-icon:hover {
    background-color: #475569;
}

.card {
    background: rgba(47, 57, 73, 0.6);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(148, 163, 184, 0.1);
    border-radius: 20px;
    padding: 20px;
    margin-bottom: 20px;
    transition: all 0.3s;
}

.card:hover {
    transform: translateY(-5px);
    border-color: rgba(99, 102, 241, 0.5);
    box-shadow: 0 10px 30px rgba(99, 102, 241, 0.2);
}

.card h3 {
    font-size: 20px;
    font-weight: 600;
    margin-bottom: 10px;
}

.card p {
    color: #CBD5E1;
    font-size: 15px;
    line-height: 1.6;
}

/* Animations */
@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* Utility Classes */
.hidden {
    display: none;
}
</style>
</head>
<body>
<div class="container">

    <!-- Login Screen -->
    <div id="loginScreen" class="login-screen">
        <h1>Welcome Back!</h1>
        <div class="input-group">
            <label for="email">Email</label>
            <input type="email" id="email" class="input-field" placeholder="your.email@example.com">
        </div>
        <div class="input-group">
            <label for="password">Password</label>
            <input type="password" id="password" class="input-field" placeholder="Your Password">
        </div>
        <button class="btn-primary" onclick="showDashboard()">Login</button>
    </div>

    <!-- Dashboard (Initially Hidden) -->
    <div id="dashboard" class="dashboard hidden">
        <div class="dashboard-header">
            <h2 class="dashboard-title">My Dashboard</h2>
            <div class="profile-icon">JD</div>
        </div>

        <div class="card">
            <h3>Daily Progress</h3>
            <p>Track your daily goals and achievements.</p>
        </div>

        <div class="card">
            <h3>Weekly Summary</h3>
            <p>Review your progress for the past week.</p>
        </div>
    </div>

</div>

<script>
function showDashboard() {
    // 간단한 인증 로직 (실제 앱에서는 더 복잡하게)
    const email = document.getElementById('email').value;
    const password = document.getElementById('password').value;

    if (email && password) {
        document.getElementById('loginScreen').classList.add('hidden');
        document.getElementById('dashboard').classList.remove('hidden');
    } else {
        alert('Please enter your email and password.');
    }
}
</script>
</body>
</html>
<!-- INTERACTIVE PROTOTYPE END -->
```
**설명:**

*   **컬러 팔레트**: 제공된 팔레트를 사용하여 디자인의 일관성을 유지합니다.
*   **글래스모피즘**: `backdrop-filter: blur()` 속성을 사용하여 반투명 효과를 구현합니다.
*   **애니메이션**: `transition` 속성을 사용하여 호버 효과 및 화면 전환에 부드러운 애니메이션을 적용합니다.
*   **시각적 계층**: 제목, 부제목, 카드 등의 텍스트 크기와 스타일을 조정하여 시각적 계층을 명확하게 합니다.
*   **인터랙티브 요소**: 버튼 클릭 시 화면이 전환되도록 JavaScript를 사용하여 간단한 상호 작용을 구현합니다.
*   **반응형 디자인**: `meta name="viewport"` 태그를 사용하여 모바일 화면에 최적화된 디자인을 제공합니다.
*   **애니메이션 효과**: 화면이 나타날 때 `fadeInUp` 애니메이션을 적용하여 부드러운 시각적 효과를 제공합니다.

**개선 사항:**

*   더 많은 화면 추가 (상세 화면, 프로필, 설정)
*   더 복잡한 상호 작용 (데이터 로딩, 폼 유효성 검사)
*   더 다양한 UI 요소 (차트, 그래프, 아이콘)
*   실제 데이터 통합 (API 호출)
*   접근성 고려 (키보드 탐색, 스크린 리더 지원)