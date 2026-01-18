알겠습니다. 첨부된 이미지와 기획서를 바탕으로 4개의 화면 (로그인, 메인, 내 달리기 현황, 프로필)을 디자인하고 HTML 프로토타입을 제공하겠습니다. 이미지의 어두운 배경과 네온 컬러를 활용하여 현대적인 느낌을 살리겠습니다.

# UI/UX 디자인

## 컬러 시스템
- Primary: #A3FF12 (밝은 형광 녹색, 이미지의 버튼 색상)
- Secondary: #333333 (어두운 회색, 배경 요소)
- Accent: #FFFFFF (흰색, 텍스트 및 아이콘)
- Background: #121212 (아주 어두운 회색, 앱 배경)
- Text: #FFFFFF (흰색, 기본 텍스트 색상)

## HTML 프로토타입

```html
<!-- INTERACTIVE PROTOTYPE START -->
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    background-color: #121212;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 40px 20px;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    color: #FFFFFF;
}

.screen-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(375px, 1fr));
    gap: 40px;
    max-width: 1600px;
    margin: 0 auto;
}

.phone-frame {
    width: 375px;
    height: 812px;
    background: #1a1a1a;
    border-radius: 50px;
    padding: 12px;
    box-shadow: 0 30px 60px rgba(0, 0, 0, 0.5);
    position: relative;
    transition: transform 0.3s ease;
    margin: 0 auto;
}

.phone-frame:hover {
    transform: translateY(-10px);
}

.phone-frame::before {
    content: '';
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 150px;
    height: 30px;
    background: #1a1a1a;
    border-radius: 0 0 20px 20px;
    z-index: 10;
}

.screen {
    width: 100%;
    height: 100%;
    background: #121212;
    border-radius: 40px;
    overflow-y: auto;
    overflow-x: hidden;
    position: relative;
    color: #FFFFFF;
}

.screen::-webkit-scrollbar {
    width: 4px;
}

.screen::-webkit-scrollbar-thumb {
    background: rgba(255,255,255,0.2);
    border-radius: 2px;
}

.screen-title {
    position: sticky;
    top: 0;
    background: rgba(18, 18, 18, 0.95);
    backdrop-filter: blur(10px);
    padding: 20px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    font-size: 18px;
    font-weight: 700;
    text-align: center;
    z-index: 5;
}

.screen-content {
    padding: 20px;
}

/* 공통 UI 컴포넌트 */
.btn {
    background-color: #A3FF12;
    color: #000000; /* 텍스트 색상을 검정으로 변경 */
    border: none;
    padding: 14px 28px;
    border-radius: 12px;
    font-size: 16px;
    font-weight: 600;
    cursor: pointer;
    width: 100%;
    transition: all 0.3s ease;
    box-shadow: 0 4px 12px rgba(163, 255, 18, 0.3);
}

.btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(163, 255, 18, 0.5);
}

.card {
    background: #1a1a1a; /* 카드 배경색을 어둡게 변경 */
    border-radius: 16px;
    padding: 20px;
    margin-bottom: 15px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.3);
    transition: all 0.3s ease;
}

.card:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 16px rgba(0,0,0,0.4);
}

.input-field {
    width: 100%;
    padding: 12px 16px;
    border: 1px solid #333333; /* 테두리 색상을 어둡게 변경 */
    border-radius: 8px;
    font-size: 16px;
    margin-bottom: 12px;
    background-color: #121212; /* 배경색을 어둡게 변경 */
    color: #FFFFFF;
}

.input-field:focus {
    outline: none;
    border-color: #A3FF12;
}

/* 추가 스타일 */
.logo {
    font-size: 24px;
    font-weight: 700;
    margin-bottom: 20px;
    text-align: center;
}

.social-login {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin-top: 20px;
}

.social-login button {
    background: none;
    border: 1px solid #A3FF12;
    color: #A3FF12;
    padding: 8px 16px;
    border-radius: 8px;
    cursor: pointer;
    transition: all 0.3s ease;
}

.social-login button:hover {
    background-color: #A3FF12;
    color: #000000;
}

.profile-icon {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    background-color: #333333;
    margin-right: 15px;
    display: inline-block;
    vertical-align: middle;
}

.match-condition {
    margin-bottom: 15px;
}

.match-condition label {
    display: block;
    margin-bottom: 5px;
}

.match-condition select {
    width: 100%;
    padding: 10px;
    border-radius: 8px;
    border: 1px solid #333333;
    background-color: #121212;
    color: #FFFFFF;
}

.running-record {
    display: flex;
    justify-content: space-between;
    margin-bottom: 8px;
}

.settings-menu {
    list-style: none;
    padding: 0;
}

.settings-menu li {
    padding: 12px 0;
    border-bottom: 1px solid #333333;
}

.settings-menu li:last-child {
    border-bottom: none;
}

.settings-menu a {
    color: #FFFFFF;
    text-decoration: none;
    display: block;
}

.tab-bar {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background-color: #1a1a1a;
    display: flex;
    justify-content: space-around;
    padding: 10px 0;
    border-top: 1px solid #333333;
}

.tab-bar a {
    color: #FFFFFF;
    text-decoration: none;
}
</style>
</head>
<body>
<div class="screen-container">
    <!-- 로그인 화면 -->
    <div class="phone-frame">
        <div class="screen">
            <div class="screen-title">로그인</div>
            <div class="screen-content">
                <div class="logo">RunTogether</div>
                <input type="email" class="input-field" placeholder="이메일">
                <input type="password" class="input-field" placeholder="비밀번호">
                <button class="btn">로그인</button>
                <a href="#" style="display: block; text-align: center; margin-top: 10px; color: #A3FF12;">비밀번호 찾기</a>
                <div class="social-login">
                    <button>카카오</button>
                    <button>구글</button>
                </div>
                <p style="text-align: center; margin-top: 20px;">계정이 없으신가요? <a href="#" style="color: #A3FF12;">회원가입</a></p>
            </div>
        </div>
    </div>

    <!-- 메인 화면 -->
    <div class="phone-frame">
        <div class="screen">
            <div class="screen-title">메인</div>
            <div class="screen-content">
                <div style="display: flex; align-items: center; margin-bottom: 20px;">
                    <div class="profile-icon"></div>
                    <div>
                        <p>안녕하세요, 사용자님!</p>
                        <p style="color: #A3FF12;">오늘도 즐거운 러닝 되세요!</p>
                    </div>
                </div>
                <div class="match-condition">
                    <label for="distance">거리 설정</label>
                    <select id="distance">
                        <option value="1">1km</option>
                        <option value="3">3km</option>
                        <option value="5">5km</option>
                        <option value="10">10km</option>
                    </select>
                </div>
                <div class="match-condition">
                    <label for="pace">페이스 설정</label>
                    <select id="pace">
                        <option>여유롭게</option>
                        <option>보통</option>
                        <option>빠르게</option>
                    </select>
                </div>
                <div class="match-condition">
                    <label for="gender">성별 선택</label>
                    <select id="gender">
                        <option>무관</option>
                        <option>남성</option>
                        <option>여성</option>
                    </select>
                </div>
                <button class="btn">매칭 시작</button>
                <p style="text-align: center; margin-top: 20px;">매칭 대기 중...</p>
            </div>
            <div class="tab-bar">
                <a href="#">메인</a>
                <a href="#">내 기록</a>
                <a href="#">프로필</a>
            </div>
        </div>
    </div>

    <!-- 내 달리기 현황 화면 -->
    <div class="phone-frame">
        <div class="screen">
            <div class="screen-title">내 달리기 현황</div>
            <div class="screen-content">
                <div class="card">
                    <h3>이번 달 총 거리</h3>
                    <p style="font-size: 24px;">42.195 km</p>
                </div>
                <div class="card">
                    <h3>이번 달 총 러닝 횟수</h3>
                    <p style="font-size: 24px;">10 회</p>
                </div>
                <div class="card">
                    <h3>평균 페이스</h3>
                    <p style="font-size: 24px;">5'30" /km</p>
                </div>
                <h3>최근 러닝 기록</h3>
                <div class="card">
                    <div class="running-record">
                        <p>2024-01-20</p>
                        <p>5.2 km</p>
                    </div>
                    <div class="running-record">
                        <p>시간</p>
                        <p>30분</p>
                    </div>
                </div>
                 <div class="card">
                    <div class="running-record">
                        <p>2024-01-15</p>
                        <p>7.8 km</p>
                    </div>
                    <div class="running-record">
                        <p>시간</p>
                        <p>45분</p>
                    </div>
                </div>
                <button class="btn">목표 설정</button>
            </div>
             <div class="tab-bar">
                <a href="#">메인</a>
                <a href="#">내 기록</a>
                <a href="#">프로필</a>
            </div>
        </div>
    </div>

    <!-- 프로필 화면 -->
    <div class="phone-frame">
        <div class="screen">
            <div class="screen-title">프로필</div>
            <div class="screen-content">
                <div style="text-align: center; margin-bottom: 20px;">
                    <div class="profile-icon" style="width: 80px; height: 80px; margin: 0 auto;"></div>
                    <p style="font-size: 20px; margin-top: 10px;">사용자 닉네임</p>
                    <p>러닝 레벨: 중급</p>
                </div>
                <ul class="settings-menu">
                    <li><a href="#">프로필 정보 수정</a></li>
                    <li><a href="#">러닝 선호도 설정</a></li>
                    <li><a href="#">알림 설정</a></li>
                    <li><a href="#">계정 관리</a></li>
                    <li><a href="#">로그아웃</a></li>
                    <li><a href="#">회원탈퇴</a></li>
                </ul>
            </div>
             <div class="tab-bar">
                <a href="#">메인</a>
                <a href="#">내 기록</a>
                <a href="#">프로필</a>
            </div>
        </div>
    </div>
</div>
<script>
// 인터랙션
</script>
</body>
</html>
<!-- INTERACTIVE PROTOTYPE END -->
```

**설명:**

*   **컬러 시스템:** 첨부 이미지의 어두운 배경과 형광 녹색 버튼 색상을 활용하여 컬러 시스템을 구성했습니다.
*   **HTML 구조:** 각 화면별로 `phone-frame`과 `screen` 클래스를 사용하여 구조를 잡았습니다.
*   **로그인 화면:** 이메일/비밀번호 입력 필드, 로그인 버튼, 소셜 로그인 옵션, 회원가입 링크를 포함했습니다.
*   **메인 화면:** 프로필 아이콘, 매칭 조건 설정 (거리, 페이스, 성별), 매칭 시작 버튼, 매칭 대기 상태 표시를 구현했습니다.
*   **내 달리기 현황 화면:** 이번 달 총 거리, 러닝 횟수, 평균 페이스, 최근 러닝 기록 리스트, 목표 설정 버튼을 포함했습니다.
*   **프로필 화면:** 프로필 사진, 닉네임, 러닝 레벨, 설정 메뉴 (정보 수정, 선호도 설정, 알림 설정, 계정 관리, 로그아웃, 회원탈퇴)를 구현했습니다.
*   **공통 스타일:** 버튼, 입력 필드, 카드 등의 UI 요소에 일관된 스타일을 적용했습니다.
*   **반응형 디자인:** `screen-container`에 `grid-template-columns: repeat(auto-fit, minmax(375px, 1fr))`를 사용하여 화면 크기에 따라 유연하게 배치되도록 했습니다.
*   **탭 바:** 메인, 내 기록, 프로필 화면 간의 이동을 위한 탭 바를 하단에 고정했습니다.

이 프로토타입은 기본적인 레이아웃과 스타일을 제공하며, JavaScript를 사용하여 인터랙션을 추가할 수 있습니다. 추가적인 기능이나 스타일 조정이 필요하시면 알려주세요.
