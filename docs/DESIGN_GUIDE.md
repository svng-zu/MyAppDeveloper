# UI/UX 디자인 가이드

최고급 UI/UX 디자이너로서, 제공된 PRD를 기반으로 시각적으로 매력적인 인터랙티브 HTML 프로토타입을 생성하겠습니다.

## 컬러 팔레트
```
## 컬러 팔레트
- Primary: #6366F1 (생생한 파랑/보라)
- Secondary: #10B981 (밝은 녹색)
- Accent: #F59E0B (따뜻한 주황)
- Background: #0F172A (깊은 네이비)
- Surface: #1E293B (어두운 회색)
- Text: #F8FAFC (밝은 흰색)
```

## 주요 화면
```
## 주요 화면
1. 로그인 화면
2. 메인 대시보드
```

## HTML 프로토타입 (완전한 HTML 문서)
```html
<!-- INTERACTIVE PROTOTYPE START -->
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>반짝이는 앱 프로토타입</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap');

* { margin: 0; padding: 0; box-sizing: border-box; }

body {
    background: linear-gradient(135deg, #0F172A 0%, #1E293B 100%);
    font-family: 'Poppins', sans-serif;
    padding: 40px 20px;
    min-height: 100vh;
    color: #F8FAFC;
}

.container {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 80vh;
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
    background: rgba(30, 41, 59, 0.8);
    backdrop-filter: blur(15px);
    border: 1px solid rgba(148, 163, 184, 0.1);
    border-radius: 30px;
    padding: 30px;
    min-height: 600px;
    position: relative;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
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
    text-align: center;
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

.input-group {
    margin-bottom: 20px;
}

.input-group label {
    display: block;
    font-size: 14px;
    color: #94A3B8;
    margin-bottom: 8px;
}

.input-group input {
    width: 100%;
    padding: 14px 20px;
    border-radius: 12px;
    border: 1px solid rgba(148, 163, 184, 0.2);
    background: rgba(30, 41, 59, 0.6);
    color: #F8FAFC;
    font-size: 16px;
    transition: border-color 0.3s;
}

.input-group input:focus {
    outline: none;
    border-color: #6366F1;
}

.stats-box {
    background: rgba(30, 41, 59, 0.7);
    backdrop-filter: blur(10px);
    border-radius: 16px;
    padding: 20px;
    margin-bottom: 15px;
    text-align: center;
    transition: transform 0.3s;
    border: 1px solid rgba(148, 163, 184, 0.1);
}

.stats-box:hover {
    transform: translateY(-5px);
}

.stats-box h3 {
    font-size: 24px;
    font-weight: 600;
    margin-bottom: 5px;
}

.stats-box p {
    font-size: 14px;
    color: #94A3B8;
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

/* Responsive Design */
@media (max-width: 768px) {
    .container {
        padding: 20px;
    }

    .screen-grid {
        grid-template-columns: 1fr;
    }

    .phone-mockup {
        padding: 15px;
    }

    .screen {
        padding: 20px;
        min-height: auto;
    }

    .screen-title {
        font-size: 24px;
    }

    .btn-primary {
        padding: 14px 24px;
        font-size: 15px;
    }
}
</style>
</head>
<body>
<div class="container">
    <div class="screen-grid">
        <!-- 로그인 화면 -->
        <div class="phone-mockup">
            <div class="screen">
                <div>
                    <h2 class="screen-title">로그인</h2>
                    <div class="input-group">
                        <label for="username">아이디</label>
                        <input type="text" id="username" placeholder="아이디를 입력하세요">
                    </div>
                    <div class="input-group">
                        <label for="password">비밀번호</label>
                        <input type="password" id="password" placeholder="비밀번호를 입력하세요">
                    </div>
                </div>
                <button class="btn-primary" id="loginBtn">로그인</button>
            </div>
        </div>

        <!-- 메인 대시보드 -->
        <div class="phone-mockup">
            <div class="screen">
                <div>
                    <h2 class="screen-title">메인 대시보드</h2>
                    <div class="stats-box">
                        <h3>1,234</h3>
                        <p>오늘의 걸음 수</p>
                    </div>
                    <div class="stats-box">
                        <h3>$45.67</h3>
                        <p>이번 달 지출</p>
                    </div>
                    <div class="stats-box">
                        <h3>78%</h3>
                        <p>목표 달성률</p>
                    </div>
                </div>
                <button class="btn-primary" id="dashboardBtn">상세 정보 보기</button>
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

document.getElementById('loginBtn').addEventListener('click', function(e) {
    e.stopPropagation();
    this.textContent = '✓ 로그인 완료!';
    setTimeout(() => {
        this.textContent = '로그인';
    }, 1500);
});

document.getElementById('dashboardBtn').addEventListener('click', function(e) {
    e.stopPropagation();
    this.textContent = '✓ 로딩 중...';
    setTimeout(() => {
        this.textContent = '상세 정보 보기';
    }, 1500);
});

</script>
</body>
</html>
<!-- INTERACTIVE PROTOTYPE END -->
```

**핵심 구현 사항:**

*   **생동감 있는 그라데이션:** 배경 및 버튼에 적용.
*   **부드러운 애니메이션:** 호버 효과, 클릭 효과, 페이지 로딩 시 애니메이션.
*   **글래스모피즘 효과:** 카드 배경에 블러 및 투명도 적용.
*   **명확한 시각적 계층:** 제목, 부제목, 카드 강조.
*   **각 화면 고유 콘텐츠:** 로그인 화면과 메인 대시보드 구분.
*   **인터랙티브 요소:** 버튼 클릭 시 텍스트 변경.
*   **반응형 디자인:** 다양한 화면 크기 지원.
*   **폰트:** Poppins 폰트 사용 (구글 폰트 CDN 연결).
*   **스타일 가이드 준수:** 배경, 카드, 버튼, 폰트, 간격, 그림자 등 PRD 스타일 가이드 준수.

이 프로토타입은 디자인 요구 사항을 충족하며, 시각적으로 매력적이고 인터랙티브한 사용자 경험을 제공합니다.