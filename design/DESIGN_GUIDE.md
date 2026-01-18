알겠습니다. 첨부된 이미지의 디자인 스타일을 참고하여 10개의 화면을 디자인하고, HTML 프로토타입을 제공하겠습니다.

# UI/UX 디자인

## 컬러 시스템
- Primary: #B2FF59
- Secondary: #A2FF00
- Accent: #FFFFFF
- Background: #121212
- Text: #FFFFFF

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
    background: #121212;
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
    background: #000000;
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
    background: #000000;
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
    border-bottom: 1px solid rgba(255,255,255,0.1);
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
    background: #B2FF59;
    color: #000000;
    border: none;
    padding: 14px 28px;
    border-radius: 12px;
    font-size: 16px;
    font-weight: 600;
    cursor: pointer;
    width: 100%;
    transition: all 0.3s ease;
    box-shadow: 0 4px 12px rgba(178, 255, 89, 0.3);
}

.btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(178, 255, 89, 0.5);
}

.card {
    background: #1E1E1E;
    border-radius: 16px;
    padding: 20px;
    margin-bottom: 15px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    transition: all 0.3s ease;
}

.card:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 16px rgba(0,0,0,0.15);
}

.input-field {
    width: 100%;
    padding: 12px 16px;
    border: 1px solid #333333;
    border-radius: 8px;
    font-size: 16px;
    margin-bottom: 12px;
    background-color: #000000;
    color: #FFFFFF;
}

.input-field:focus {
    outline: none;
    border-color: #B2FF59;
}

.social-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 12px;
    border-radius: 8px;
    border: 1px solid #333333;
    margin-bottom: 10px;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

.social-btn:hover {
    background-color: #222222;
}

.social-btn img {
    width: 24px;
    margin-right: 10px;
}

.profile-image {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    object-fit: cover;
    margin-bottom: 10px;
}

.level-badge {
    background-color: #B2FF59;
    color: #000000;
    padding: 5px 10px;
    border-radius: 5px;
    font-size: 12px;
    font-weight: bold;
}

.running-summary {
    display: flex;
    justify-content: space-around;
    margin-bottom: 20px;
}

.summary-item {
    text-align: center;
}

.navigation-bar {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background-color: #1E1E1E;
    display: flex;
    justify-content: space-around;
    padding: 10px 0;
    border-top: 1px solid #333333;
}

.nav-item {
    text-align: center;
    cursor: pointer;
}

.nav-item img {
    width: 24px;
    margin-bottom: 5px;
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
    background-color: #000000;
    color: #FFFFFF;
}

.result-data {
    display: flex;
    justify-content: space-around;
    margin-bottom: 20px;
}

.result-item {
    text-align: center;
}

.graph-container {
    width: 100%;
    height: 200px;
    background-color: #000000;
    border-radius: 10px;
    margin-bottom: 20px;
}

.feed-item {
    margin-bottom: 20px;
    padding: 15px;
    border-radius: 10px;
    background-color: #1E1E1E;
}

.feed-item h3 {
    margin-bottom: 5px;
}

.settings-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px;
    border-bottom: 1px solid #333333;
}

.toggle-switch {
    position: relative;
    display: inline-block;
    width: 40px;
    height: 20px;
}

.toggle-switch input {
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
    background-color: #333333;
    transition: .4s;
    border-radius: 20px;
}

.slider:before {
    position: absolute;
    content: "";
    height: 16px;
    width: 16px;
    left: 2px;
    bottom: 2px;
    background-color: white;
    transition: .4s;
    border-radius: 50%;
}

input:checked + .slider {
    background-color: #B2FF59;
}

input:focus + .slider {
    box-shadow: 0 0 1px #B2FF59;
}

input:checked + .slider:before {
    transform: translateX(20px);
}
</style>
</head>
<body>
<div class="screen-container">
    <!-- 1. 온보딩/로그인 -->
    <div class="phone-frame">
        <div class="screen">
            <div class="screen-title">환영합니다!</div>
            <div class="screen-content">
                <h1>러닝 앱</h1>
                <p>새로운 러닝 경험을 시작하세요!</p>
                <div class="social-btn">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Google_%22G%22_Logo.svg/2048px-Google_%22G%22_Logo.svg.png" alt="Google">
                    Google로 로그인
                </div>
                <div class="social-btn">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Apple_logo_black.svg/1667px-Apple_logo_black.svg.png" alt="Apple">
                    Apple로 로그인
                </div>
                <div class="social-btn">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/KakaoTalk_logo.svg/2048px-KakaoTalk_logo.svg.png" alt="Kakao">
                    Kakao로 로그인
                </div>
                <p>이용약관 및 개인정보처리방침에 동의합니다.</p>
                <button class="btn">동의하고 시작하기</button>
            </div>
        </div>
    </div>

    <!-- 2. 메인 홈 -->
    <div class="phone-frame">
        <div class="screen">
            <div class="screen-title">홈</div>
            <div class="screen-content">
                <img src="https://via.placeholder.com/80" alt="프로필 이미지" class="profile-image">
                <h2>사용자 닉네임</h2>
                <span class="level-badge">레벨 10</span>
                <div class="running-summary">
                    <div class="summary-item">
                        <h3>거리</h3>
                        <p>10km</p>
                    </div>
                    <div class="summary-item">
                        <h3>시간</h3>
                        <p>1시간 30분</p>
                    </div>
                    <div class="summary-item">
                        <h3>칼로리</h3>
                        <p>500kcal</p>
                    </div>
                </div>
                <button class="btn">혼자 런닝 시작</button>
                <button class="btn">1:1 대결 시작</button>
                <div class="card">
                    <h3>진행 중인 대결</h3>
                    <p>상대: 라이벌</p>
                    <p>현재 거리: 5km</p>
                </div>
                <div class="card">
                    <h3>최근 활동</h3>
                    <p>새로운 챌린지 참가!</p>
                </div>
            </div>
            <div class="navigation-bar">
                <div class="nav-item">
                    <img src="https://cdn-icons-png.flaticon.com/512/25/25694.png" alt="홈">
                    <p>홈</p>
                </div>
                <div class="nav-item">
                    <img src="https://cdn-icons-png.flaticon.com/512/3519/3519375.png" alt="대결">
                    <p>대결</p>
                </div>
                <div class="nav-item">
                    <img src="https://cdn-icons-png.flaticon.com/512/256/256554.png" alt="커뮤니티">
                    <p>커뮤니티</p>
                </div>
                <div class="nav-item">
                    <img src="https://cdn-icons-png.flaticon.com/512/1077/1077114.png" alt="프로필">
                    <p>프로필</p>
                </div>
            </div>
        </div>
    </div>

    <!-- 3. 런닝 기록 -->
    <div class="phone-frame">
        <div class="screen">
            <div class="screen-title">런닝 기록</div>
            <div class="screen-content">
                <img src="https://via.placeholder.com/350x200" alt="지도">
                <p>거리: 5.5 km</p>
                <p>시간: 30분 15초</p>
                <p>속도: 6분/km</p>
                <button class="btn">일시정지</button>
                <button class="btn">종료</button>
            </div>
        </div>
    </div>

    <!-- 4. 1:1 대결 -->
    <div class="phone-frame">
        <div class="screen">
            <div class="screen-title">1:1 대결</div>
            <div class="screen-content">
                <img src="https://via.placeholder.com/50" alt="상대 프로필">
                <h2>상대: 라이벌</h2>
                <p>거리: 5km vs 4.8km</p>
                <img src="https://via.placeholder.com/350x150" alt="실시간 비교 차트">
                <button class="btn">응원 메시지 보내기</button>
                <button class="btn">대결 포기</button>
            </div>
        </div>
    </div>

    <!-- 5. 대결 매칭 -->
    <div class="phone-frame">
        <div class="screen">
            <div class="screen-title">대결 매칭</div>
            <div class="screen-content">
                <div class="match-condition">
                    <label for="distance">거리:</label>
                    <select id="distance">
                        <option value="5">5km</option>
                        <option value="10">10km</option>
                        <option value="15">15km</option>
                    </select>
                </div>
                <div class="match-condition">
                    <label for="level">레벨:</label>
                    <select id="level">
                        <option value="10">10 이상</option>
                        <option value="20">20 이상</option>
                        <option value="30">30 이상</option>
                    </select>
                </div>
                <div class="card">
                    <img src="https://via.placeholder.com/50" alt="상대 프로필">
                    <h3>상대: 도전자</h3>
                    <p>레벨: 25</p>
                    <button class="btn">대결 신청</button>
                </div>
                <button class="btn">매칭 대기</button>
            </div>
        </div>
    </div>

    <!-- 6. 대결 결과 -->
    <div class="phone-frame">
        <div class="screen">
            <div class="screen-title">대결 결과</div>
            <div class="screen-content">
                <h1>승리!</h1>
                <p>획득 포인트: +100</p>
                <div class="result-data">
                    <div class="result-item">
                        <h3>내 기록</h3>
                        <p>5km, 25분</p>
                    </div>
                    <div class="result-item">
                        <h3>상대 기록</h3>
                        <p>5km, 27분</p>
                    </div>
                </div>
                <button class="btn">상대방 평가하기</button>
                <button class="btn">SNS 공유</button>
            </div>
        </div>
    </div>

    <!-- 7. 런닝 기록 상세 -->
    <div class="phone-frame">
        <div class="screen">
            <div class="screen-title">런닝 기록 상세</div>
            <div class="screen-content">
                <img src="https://via.placeholder.com/350x200" alt="경로 지도">
                <p>날짜: 2024년 10월 27일</p>
                <p>거리: 5.5 km</p>
                <p>시간: 30분 15초</p>
                <div class="graph-container">
                    <!-- 그래프 -->
                </div>
                <button class="btn">메모 추가</button>
            </div>
        </div>
    </div>

    <!-- 8. 커뮤니티 -->
    <div class="phone-frame">
        <div class="screen">
            <div class="screen-title">커뮤니티</div>
            <div class="screen-content">
                <div class="feed-item">
                    <h3>사용자 A</h3>
                    <p>오늘 런닝 최고 기록 달성!</p>
                    <button>좋아요</button>
                    <button>댓글</button>
                </div>
                <div class="feed-item">
                    <h3>사용자 B</h3>
                    <p>새로운 챌린지 참가합니다!</p>
                    <button>좋아요</button>
                    <button>댓글</button>
                </div>
                <button class="btn">게시글 작성</button>
            </div>
        </div>
    </div>

    <!-- 9. 프로필 -->
    <div class="phone-frame">
        <div class="screen">
            <div class="screen-title">프로필</div>
            <div class="screen-content">
                <img src="https://via.placeholder.com/100" alt="프로필 사진" class="profile-image">
                <h2>사용자 닉네임</h2>
                <p>총 거리: 100km</p>
                <p>총 시간: 50시간</p>
                <button class="btn">프로필 편집</button>
                <button class="btn">친구 관리</button>
            </div>
        </div>
    </div>

    <!-- 10. 설정 -->
    <div class="phone-frame">
        <div class="screen">
            <div class="screen-title">설정</div>
            <div class="screen-content">
                <div class="settings-item">
                    <p>알림 설정</p>
                    <label class="toggle-switch">
                        <input type="checkbox">
                        <span class="slider"></span>
                    </label>
                </div>
                <div class="settings-item">
                    <p>개인정보 보호 설정</p>
                    <label class="toggle-switch">
                        <input type="checkbox">
                        <span class="slider"></span>
                    </label>
                </div>
                <div class="settings-item">
                    <p>단위 설정 (km/mile)</p>
                    <select>
                        <option value="km">km</option>
                        <option value="mile">mile</option>
                    </select>
                </div>
                <button class="btn">로그아웃</button>
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

**참고사항:**

*   이미지 호스팅을 사용하여 실제 이미지를 표시할 수 있습니다.
*   CSS 스타일을 조정하여 디자인을 더욱 개선할 수 있습니다.
*   JavaScript를 사용하여 인터랙션을 추가할 수 있습니다.
*   그래프 라이브러리를 사용하여 그래프를 표시할 수 있습니다.