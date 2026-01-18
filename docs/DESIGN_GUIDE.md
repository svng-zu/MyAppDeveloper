# UI/UX 디자인 가이드

알겠습니다. 앱 아이디어를 기반으로 조금 더 구체적인 PRD를 가정하고, 사용자 인터페이스를 개선하여 실제 앱 디자인에 더 가깝도록 인터랙티브 HTML 프로토타입을 생성하겠습니다.

**가정 PRD:**

1.  **앱의 기본 아이디어나 컨셉:** 건강한 식습관 형성을 돕는 앱. 영양 정보 기록, 맞춤형 식단 추천, 진행 상황 시각화 기능을 제공.
2.  **해결하고자 하는 문제나 니즈:** 바쁜 현대인들이 건강한 식습관을 유지하기 어려움. 영양 불균형, 식단 관리의 어려움을 해결.
3.  **대략적인 타겟 사용자층:** 20-40대 직장인, 건강에 관심 있는 사용자, 식단 관리가 필요한 사용자.
4.  **참고하고 있는 유사 서비스:** MyFitnessPal, Noom

**출력 형식:**

1.  **컬러 팔레트 (마크다운)**

```
## 컬러 팔레트
- Primary: #3B82F6  /* Blue-500 */
- Secondary: #6EE7B7 /* Green-300 */
- Accent: #FCD34D    /* Yellow-300 */
- Background: #111827 /* Gray-900 */
- Text: #E5E7EB      /* Gray-200 */
```

2.  **주요 화면 (마크다운)**

```
## 주요 화면
1. 메인 화면 (오늘의 식단 기록)
2. 기록 화면 (식단 기록 추이)
3. 추천 화면 (맞춤형 식단 추천)
4. 프로필 화면 (사용자 정보 및 설정)
```

3.  **HTML 프로토타입 (완전한 HTML 문서)**

```html
<!-- INTERACTIVE PROTOTYPE START -->
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>식단 관리 앱 프로토타입</title>
    <style>
        body {
            background: #111827;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            color: #E5E7EB;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .phone-mockup {
            width: 375px; /* iPhone SE width */
            height: 667px; /* iPhone SE height */
            background: #1F2937;
            border-radius: 30px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
            overflow: hidden;
        }

        .screen {
            padding: 20px;
            height: 587px; /* Adjusted for header */
            overflow-y: auto;
        }

        /* Header */
        .header {
            background-color: #3B82F6;
            color: #fff;
            padding: 15px;
            text-align: center;
            font-size: 1.2em;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        /* Navigation */
        .navigation {
            background-color: #1F2937;
            display: flex;
            justify-content: space-around;
            padding: 10px 0;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        .nav-item {
            color: #9CA3AF;
            text-decoration: none;
            padding: 8px 16px;
            border-radius: 5px;
            transition: background-color 0.3s, color 0.3s;
        }

        .nav-item:hover, .nav-item.active {
            background-color: #374151;
            color: #E5E7EB;
        }

        /* UI Elements */
        .card {
            background-color: #374151;
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 15px;
        }

        .input-field {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border: none;
            border-radius: 5px;
            background-color: #4B5563;
            color: #E5E7EB;
        }

        button {
            background-color: #3B82F6;
            color: #fff;
            padding: 10px 15px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: #2563EB;
        }
    </style>
</head>
<body>

<div class="phone-mockup">
    <div class="header">식단 관리</div>

    <div class="screen" id="main-screen">
        <h2>오늘의 식단</h2>
        <div class="card">
            <input type="text" class="input-field" placeholder="음식 이름">
            <input type="number" class="input-field" placeholder="칼로리">
            <button onclick="alert('기록 완료!')">기록하기</button>
        </div>
    </div>

    <div class="screen" id="record-screen" style="display:none;">
        <h2>식단 기록</h2>
        <div class="card">
            <p>최근 7일 칼로리 추이 그래프 (미구현)</p>
        </div>
    </div>

    <div class="screen" id="recommend-screen" style="display:none;">
        <h2>추천 식단</h2>
        <div class="card">
            <p>오늘의 추천 식단: 닭가슴살 샐러드</p>
        </div>
    </div>

    <div class="screen" id="profile-screen" style="display:none;">
        <h2>프로필</h2>
        <div class="card">
            <p>사용자 이름: 홍길동</p>
            <p>목표 칼로리: 2000kcal</p>
        </div>
    </div>

    <div class="navigation">
        <a href="#" class="nav-item active" onclick="showScreen('main-screen'); return false;">홈</a>
        <a href="#" class="nav-item" onclick="showScreen('record-screen'); return false;">기록</a>
        <a href="#" class="nav-item" onclick="showScreen('recommend-screen'); return false;">추천</a>
        <a href="#" class="nav-item" onclick="showScreen('profile-screen'); return false;">프로필</a>
    </div>
</div>

<script>
    function showScreen(screenId) {
        // Hide all screens
        document.querySelectorAll('.screen').forEach(screen => {
            screen.style.display = 'none';
        });

        // Show the selected screen
        document.getElementById(screenId).style.display = 'block';

        // Update active navigation item
        document.querySelectorAll('.nav-item').forEach(item => {
            item.classList.remove('active');
            if (item.getAttribute('href') === '#' && item.getAttribute('onclick').includes(screenId)) {
                item.classList.add('active');
            }
        });
    }
</script>

</body>
</html>
<!-- INTERACTIVE PROTOTYPE END -->
```

**설명:**

*   **컬러 팔레트:** Tailwind CSS에서 영감을 받아 현대적이고 접근성이 좋은 색상 조합을 선택했습니다.
*   **HTML 구조:**
    *   `phone-mockup` 클래스를 사용하여 휴대폰 모양을 시뮬레이션했습니다.
    *   각 화면은 `screen` 클래스를 가진 `div`로 구현되었으며, 초기에는 메인 화면만 표시됩니다.
    *   `navigation` 클래스는 화면 전환을 위한 하단 네비게이션 바입니다.
*   **CSS 스타일:**
    *   전체적인 디자인을 현대적이고 깔끔하게 유지했습니다.
    *   각 요소에 적절한 패딩, 마진, 폰트 크기를 적용하여 가독성을 높였습니다.
*   **JavaScript:**
    *   `showScreen()` 함수는 클릭된 네비게이션 아이템에 따라 해당 화면을 표시하고 다른 화면을 숨깁니다.
    *   네비게이션 아이템의 `active` 클래스를 업데이트하여 현재 활성화된 화면을 시각적으로 나타냅니다.
*   **UI 요소:**
    *   각 화면에 간단한 입력 필드와 버튼을 추가하여 사용자 인터랙션을 시뮬레이션했습니다.
    *   `card` 클래스를 사용하여 각 화면의 콘텐츠를 그룹화하고 시각적으로 분리했습니다.

이 프로토타입은 가상의 식단 관리 앱의 기본적인 기능과 사용자 인터페이스를 보여줍니다. 실제 앱 개발에서는 데이터베이스 연동, API 호출, 더 복잡한 UI 요소 및 로직이 필요합니다.
