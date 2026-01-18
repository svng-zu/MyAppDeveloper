# UI/UX 디자인 가이드

## 컬러 팔레트
- Primary: #6366F1 (생생한 파랑/보라)
- Secondary: #10B981 (밝은 녹색)
- Accent: #F59E0B (따뜻한 주황)
- Background: #0F172A (깊은 네이비)
- Surface: #1E293B (어두운 회색)
- Text: #F8FAFC (밝은 흰색)

## 주요 화면
1. 메인 대시보드
2. 상세 화면
3. 프로필
4. 설정

```html
<!-- INTERACTIVE PROTOTYPE START -->
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Interactive Prototype</title>
<style>
/* Reset & General Styles */
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

/* Screen Grid Layout */
.screen-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 30px;
    margin-top: 30px;
}

/* Phone Mockup Styles */
.phone-mockup {
    background: linear-gradient(135deg, #1E293B, #334155);
    border-radius: 40px;
    padding: 20px;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1); /* 부드러운 애니메이션 */
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

/* Screen Styles */
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

/* Screen Title */
.screen-title {
    color: #F8FAFC;
    font-size: 28px;
    font-weight: 700;
    margin-bottom: 25px;
    background: linear-gradient(135deg, #6366F1, #8B5CF6);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}

/* Card Styles (Glassmorphism) */
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

/* Primary Button */
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

/* Fade-in Animation */
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

/* Apply Animation */
.phone-mockup {
    animation: fadeInUp 0.6s ease-out backwards;
}

.phone-mockup:nth-child(1) { animation-delay: 0.1s; }
.phone-mockup:nth-child(2) { animation-delay: 0.2s; }
.phone-mockup:nth-child(3) { animation-delay: 0.3s; }
.phone-mockup:nth-child(4) { animation-delay: 0.4s; }

/* Typography */
h1, h2, h3 {
    font-weight: 700;
    line-height: 1.2;
    margin-bottom: 10px;
}

p {
    font-size: 16px;
    line-height: 1.6;
    color: #94A3B8; /* 밝은 회색 */
}

/* Icon Styles */
.icon {
    display: inline-block;
    width: 24px;
    height: 24px;
    margin-right: 8px;
    vertical-align: middle;
}

/* Specific Screen Styles */
#dashboard-screen .card {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 150px;
}

#dashboard-screen .card h3 {
    margin-bottom: 5px;
}

#detail-screen ul {
    list-style: none;
    padding: 0;
}

#detail-screen li {
    padding: 15px 0;
    border-bottom: 1px solid rgba(148, 163, 184, 0.1);
}

#detail-screen li:last-child {
    border-bottom: none;
}

#profile-screen img {
    width: 120px;
    height: 120px;
    border-radius: 50%;
    object-fit: cover;
    margin-bottom: 20px;
}

#profile-screen p {
    margin-bottom: 10px;
}

#settings-screen .setting-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px 0;
    border-bottom: 1px solid rgba(148, 163, 184, 0.1);
}

#settings-screen .setting-item:last-child {
    border-bottom: none;
}
</style>
</head>
<body>
<div class="container">
    <div class="screen-grid">

        <!-- 1. 메인 대시보드 -->
        <div class="phone-mockup" id="dashboard-mockup">
            <div class="screen" id="dashboard-screen">
                <h2 class="screen-title">대시보드</h2>

                <div class="card">
                    <h3>오늘의 운동</h3>
                    <p>🔥 300 칼로리 소모</p>
                    <button class="btn-primary">운동 시작</button>
                </div>

                <div class="card">
                    <h3>이번 주 목표</h3>
                    <p>🏃‍♀️ 5km 달리기</p>
                </div>
            </div>
        </div>

        <!-- 2. 상세 화면 -->
        <div class="phone-mockup" id="detail-mockup">
            <div class="screen" id="detail-screen">
                <h2 class="screen-title">상세 정보</h2>
                <ul>
                    <li>
                        <strong>운동 종류:</strong> 달리기
                    </li>
                    <li>
                        <strong>시간:</strong> 30분
                    </li>
                    <li>
                        <strong>거리:</strong> 3.2km
                    </li>
                    <li>
                        <strong>칼로리 소모:</strong> 250kcal
                    </li>
                </ul>
                <button class="btn-primary">뒤로 가기</button>
            </div>
        </div>

        <!-- 3. 프로필 -->
        <div class="phone-mockup" id="profile-mockup">
            <div class="screen" id="profile-screen">
                <h2 class="screen-title">프로필</h2>
                <img src="https://randomuser.me/api/portraits/men/75.jpg" alt="프로필 사진">
                <p><strong>이름:</strong> 김철수</p>
                <p><strong>나이:</strong> 32세</p>
                <p><strong>이메일:</strong> example@example.com</p>
                <button class="btn-primary">프로필 편집</button>
            </div>
        </div>

        <!-- 4. 설정 -->
        <div class="phone-mockup" id="settings-mockup">
            <div class="screen" id="settings-screen">
                <h2 class="screen-title">설정</h2>
                <div class="setting-item">
                    <p>알림 설정</p>
                    <label class="switch">
                        <input type="checkbox">
                        <span class="slider round"></span>
                    </label>
                </div>
                <div class="setting-item">
                    <p>다크 모드</p>
                    <label class="switch">
                        <input type="checkbox">
                        <span class="slider round"></span>
                    </label>
                </div>
                <button class="btn-primary">저장</button>
            </div>
        </div>

    </div>
</div>

<style>
/* Toggle Switch Styles */
.switch {
  position: relative;
  display: inline-block;
  width: 60px;
  height: 34px;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: .4s;
  transition: .4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: .4s;
  transition: .4s;
}

input:checked + .slider {
  background-color: #2196F3;
}

input:focus + .slider {
  box-shadow: 0 0 1px #2196F3;
}

input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}

/* Rounded sliders */
.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}
</style>

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
            this.textContent = this.dataset.originalText || '시작하기'; // data-original-text 속성 사용
        }, 1500);
    });
    btn.dataset.originalText = btn.textContent; // 원래 텍스트 저장
});
</script>
</body>
</html>
<!-- INTERACTIVE PROTOTYPE END -->
```