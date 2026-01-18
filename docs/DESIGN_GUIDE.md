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
<title>운동 습관 형성 앱 프로토타입</title>
<style>
* { margin: 0; padding: 0; box-sizing: border-box; }

body {
    background: linear-gradient(135deg, #0F172A 0%, #1E293B 100%);
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    padding: 40px 20px;
    min-height: 100vh;
    color: #F8FAFC;
}

.container {
    max-width: 1400px;
    margin: 0 auto;
}

.screen-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 30px;
    margin-top: 30px;
}

.phone-mockup {
    background: linear-gradient(135deg, #1E293B, #334155);
    border-radius: 40px;
    padding: 20px;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    cursor: pointer;
    position: relative;
    overflow: hidden;
}

.phone-mockup::before {
    content: '';
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: linear-gradient(45deg, transparent, rgba(99, 102, 241, 0.1), transparent);
    transform: rotate(45deg);
    transition: all 0.6s;
}

.phone-mockup:hover::before {
    left: 100%;
}

.phone-mockup:hover {
    transform: translateY(-10px) scale(1.02);
    box-shadow: 0 30px 80px rgba(99, 102, 241, 0.4);
}

.screen {
    background: linear-gradient(135deg, #0F172A, #1a2332);
    border-radius: 30px;
    padding: 30px;
    min-height: 600px;
    position: relative;
    overflow: hidden;
}

.screen::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 3px;
    background: linear-gradient(90deg, #6366F1, #8B5CF6, #EC4899);
}

.screen-title {
    color: #F8FAFC;
    font-size: 28px;
    font-weight: 700;
    margin-bottom: 25px;
    background: linear-gradient(135deg, #6366F1, #8B5CF6);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}

.card {
    background: rgba(30, 41, 59, 0.8);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(148, 163, 184, 0.1);
    border-radius: 20px;
    padding: 25px;
    margin-bottom: 20px;
    transition: all 0.3s;
}

.card:hover {
    transform: translateY(-5px);
    border-color: rgba(99, 102, 241, 0.5);
    box-shadow: 0 10px 30px rgba(99, 102, 241, 0.2);
}

.btn-primary {
    background: linear-gradient(135deg, #6366F1, #8B5CF6);
    color: white;
    border: none;
    padding: 16px 32px;
    border-radius: 16px;
    font-size: 16px;
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

.phone-mockup {
    animation: fadeInUp 0.6s ease-out backwards;
}

.phone-mockup:nth-child(1) { animation-delay: 0.1s; }
.phone-mockup:nth-child(2) { animation-delay: 0.2s; }

/* 로그인 화면 스타일 */
.login-form {
    display: flex;
    flex-direction: column;
    gap: 15px;
}

.login-form input {
    background: rgba(30, 41, 59, 0.6);
    border: none;
    border-radius: 12px;
    padding: 14px 20px;
    font-size: 16px;
    color: #F8FAFC;
    outline: none;
    transition: all 0.3s;
}

.login-form input:focus {
    box-shadow: 0 2px 10px rgba(99, 102, 241, 0.3);
    border: 1px solid rgba(99, 102, 241, 0.2);
}

/* 메인 대시보드 스타일 */
.dashboard-stats {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 20px;
    margin-bottom: 20px;
}

.stat-box {
    background: rgba(30, 41, 59, 0.8);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(148, 163, 184, 0.1);
    border-radius: 16px;
    padding: 20px;
    text-align: center;
    transition: all 0.3s;
}

.stat-box:hover {
    transform: translateY(-5px);
    border-color: rgba(99, 102, 241, 0.5);
    box-shadow: 0 10px 30px rgba(99, 102, 241, 0.2);
}

.stat-value {
    font-size: 24px;
    font-weight: 700;
    margin-bottom: 5px;
}

.stat-label {
    font-size: 14px;
    color: #94A3B8;
}
</style>
</head>
<body>
<div class="container">
    <div class="screen-grid">
        <!-- 로그인 화면 -->
        <div class="phone-mockup">
            <div class="screen">
                <h2 class="screen-title">로그인</h2>
                <form class="login-form">
                    <input type="email" placeholder="이메일">
                    <input type="password" placeholder="비밀번호">
                    <button class="btn-primary">로그인</button>
                </form>
            </div>
        </div>

        <!-- 메인 대시보드 -->
        <div class="phone-mockup">
            <div class="screen">
                <h2 class="screen-title">오늘의 운동</h2>
                <div class="dashboard-stats">
                    <div class="stat-box">
                        <div class="stat-value">30</div>
                        <div class="stat-label">분 운동</div>
                    </div>
                    <div class="stat-box">
                        <div class="stat-value">150</div>
                        <div class="stat-label">칼로리 소모</div>
                    </div>
                    <div class="stat-box">
                        <div class="stat-value">5</div>
                        <div class="stat-label">일 연속</div>
                    </div>
                </div>
                <div class="card">
                    <p style="color: #94A3B8;">오늘의 운동 루틴을 확인하세요!</p>
                </div>
                <button class="btn-primary">운동 시작하기</button>
            </div>
        </div>
    </div>
</div>

<script>
// 인터랙티브 기능
document.querySelectorAll('.phone-mockup').forEach((phone, index) => {
    phone.addEventListener('click', function() {
        this.style.transform = this.style.transform.includes('scale(1.05)')
            ? 'translateY(-10px) scale(1.02)'
            : 'translateY(-10px) scale(1.05)';
    });
});

document.querySelectorAll('.btn-primary').forEach(btn => {
    btn.addEventListener('click', function(e) {
        e.stopPropagation();
        this.textContent = '✓ 완료';
        setTimeout(() => {
            this.textContent = '운동 시작하기';
        }, 1500);
    });
});
</script>
</body>
</html>
<!-- INTERACTIVE PROTOTYPE END -->
```
