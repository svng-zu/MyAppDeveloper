# UI/UX 디자인 가이드

알겠습니다. 새로운 앱 기획을 기반으로 인터랙티브 HTML 프로토타입을 생성하겠습니다.

**앱 아이디어:** 운동 습관 형성을 돕는 앱

**해결하고자 하는 문제:** 운동을 꾸준히 하기 어렵고, 동기 부여가 부족함

**타겟 사용자층:** 운동 초보자, 운동을 꾸준히 하고 싶지만 의지가 약한 사람

**참고 서비스:** Nike Training Club, 삼성 헬스

**출력 형식:**

1. 컬러 팔레트 (마크다운)
```
## 컬러 팔레트
- Primary: #4F46E5  // Indigo-500 (운동 강조)
- Secondary: #34D399 // Teal-400 (성장, 활력)
- Accent: #FCD34D    // Yellow-300 (알림, 포인트)
- Background: #111827 // Gray-900 (다크 모드)
- Text: #E5E7EB      // Gray-200 (가독성)
```

2. 주요 화면 (마크다운)
```
## 주요 화면
1. 메인 화면 (오늘의 운동, 진행 상황)
2. 기록 화면 (운동 기록, 통계)
3. 챌린지 화면 (다른 사용자들과 경쟁)
4. 프로필 화면 (개인 정보, 설정)
```

3. HTML 프로토타입 (완전한 HTML 문서)
```html
<!-- INTERACTIVE PROTOTYPE START -->
<!DOCTYPE html>
<html>
<head>
<title>운동 습관 형성 앱 프로토타입</title>
<style>
body { background: #111827; font-family: -apple-system, sans-serif; padding: 20px; color: #E5E7EB; }
.phone-mockup {
    width: 320px;
    background: linear-gradient(135deg, #1e293b, #334155);
    border-radius: 30px;
    padding: 15px;
    cursor: pointer;
    transition: all 0.3s;
    margin: 0 auto;
}
.phone-mockup:hover { transform: translateY(-5px); }
.screen { background: #111827; border-radius: 20px; padding: 20px; height: 550px; overflow: auto; }
h1 { color: #4F46E5; }
h2 { margin-bottom: 10px; }
.menu { display: flex; justify-content: space-around; padding: 10px 0; border-top: 1px solid #374151; }
.menu a { color: #E5E7EB; text-decoration: none; }
.menu a:hover { color: #4F46E5; }
.workout-card { background: #1E293B; padding: 15px; border-radius: 10px; margin-bottom: 10px; }
.workout-card:hover { background: #374151; }
.progress-bar { width: 100%; height: 10px; background: #374151; border-radius: 5px; overflow: hidden; }
.progress-bar-fill { height: 10px; background: #34D399; width: 60%; display: block; }

/* 화면 전환 스타일 (숨김 처리) */
.screen-section { display: none; }
.screen-section.active { display: block; }
</style>
</head>
<body>

<div class="phone-mockup">
    <div class="screen">

        <!-- 메인 화면 -->
        <div id="main" class="screen-section active">
            <h1>오늘의 운동</h1>
            <div class="workout-card">
                <h2>푸쉬업 10회</h2>
                <p>3세트</p>
                <div class="progress-bar">
                    <span class="progress-bar-fill"></span>
                </div>
            </div>
            <div class="workout-card">
                <h2>스쿼트 15회</h2>
                <p>3세트</p>
                <div class="progress-bar">
                    <span class="progress-bar-fill" style="width: 30%;"></span>
                </div>
            </div>
        </div>

        <!-- 기록 화면 -->
        <div id="history" class="screen-section">
            <h1>운동 기록</h1>
            <p>최근 7일간 운동 시간: 5시간 30분</p>
            <p>이번 달 운동 횟수: 12회</p>
            <p>최고 기록: 스쿼트 30회</p>
        </div>

        <!-- 챌린지 화면 -->
        <div id="challenge" class="screen-section">
            <h1>챌린지</h1>
            <p>이번 주 챌린지: 매일 30분 운동하기</p>
            <p>현재 순위: 5위</p>
            <button style="background: #4F46E5; color: white; border: none; padding: 10px 20px; border-radius: 5px;">챌린지 참여</button>
        </div>

        <!-- 프로필 화면 -->
        <div id="profile" class="screen-section">
            <h1>프로필</h1>
            <p>이름: 홍길동</p>
            <p>나이: 30세</p>
            <p>목표: 건강한 습관 만들기</p>
            <button style="background: #4F46E5; color: white; border: none; padding: 10px 20px; border-radius: 5px;">설정 변경</button>
        </div>

        <div class="menu">
            <a href="#" onclick="showScreen('main')">메인</a>
            <a href="#" onclick="showScreen('history')">기록</a>
            <a href="#" onclick="showScreen('challenge')">챌린지</a>
            <a href="#" onclick="showScreen('profile')">프로필</a>
        </div>

    </div>
</div>

<script>
function showScreen(screenId) {
    const screens = document.querySelectorAll('.screen-section');
    screens.forEach(screen => screen.classList.remove('active'));
    document.getElementById(screenId).classList.add('active');
}
</script>

</body>
</html>
<!-- INTERACTIVE PROTOTYPE END -->
```
**설명:**

*   **컬러 팔레트:** 어두운 배경에 눈에 띄는 색상을 사용하여 사용성을 높였습니다.
*   **HTML:** 각 화면을 `div`로 나누고, JavaScript를 사용하여 화면 전환을 구현했습니다.
*   **CSS:** 기본적인 스타일을 적용하여 프로토타입의 시각적인 완성도를 높였습니다.
*   **JavaScript:** `showScreen` 함수를 통해 각 화면을 보여주고 숨기는 기능을 구현했습니다. 메뉴 클릭 시 해당 화면이 표시됩니다.
*   **핵심 UI:** 각 화면에 필요한 핵심적인 UI 요소만 포함하여 간결하게 만들었습니다.
*   **인터랙션:** 메뉴를 클릭하면 해당 화면으로 전환되는 간단한 인터랙션을 추가했습니다.
*   **반응형:** `phone-mockup` 클래스를 사용하여 모바일 화면에 최적화된 디자인을 제공합니다.

**추가 설명:**

*   더 많은 기능을 추가하려면 JavaScript를 사용하여 각 UI 요소에 대한 인터랙션을 구현할 수 있습니다.
*   CSS를 사용하여 디자인을 더욱 세련되게 만들 수 있습니다.
*   API를 사용하여 실제 데이터를 가져와서 표시할 수 있습니다.
