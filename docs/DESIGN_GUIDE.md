# UI/UX 디자인 가이드

## 컬러 팔레트
- Primary: #6366F1 (메인 액션, 버튼)
- Secondary: #10B981 (성공, 완료 상태)
- Accent: #F59E0B (강조, 알림)
- Background: #0F172A (배경)
- Surface: #1E293B (카드, 모달)
- Text: #F8FAFC (텍스트)
- Text Secondary: #94A3B8 (보조 텍스트)

## 주요 화면
1. 로그인 화면
2. 메인 대시보드 (광고 배너 포함)
3. 러닝 기록 화면
4. 런닝 트래킹 화면
5. 커뮤니티 피드
6. 프로필/통계 화면

<!-- INTERACTIVE PROTOTYPE START -->
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RunTogether - Interactive Prototype</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #0F172A 0%, #1E293B 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .prototype-container {
            display: flex;
            gap: 20px;
            justify-content: center;
            flex-wrap: wrap;
            max-width: 1200px;
            margin: 0 auto;
        }

        .phone-mockup {
            width: 320px;
            background: linear-gradient(135deg, #334155, #475569);
            border-radius: 30px;
            padding: 10px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.6);
            transition: all 0.3s ease;
            cursor: pointer;
            position: relative;
        }

        .phone-mockup:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 30px 80px rgba(99, 102, 241, 0.4);
        }

        .phone-mockup.active {
            transform: scale(1.1);
            z-index: 10;
        }

        .screen {
            background: #0F172A;
            border-radius: 25px;
            height: 640px;
            overflow-y: auto;
            position: relative;
        }

        .screen-header {
            background: #1E293B;
            padding: 15px 20px;
            border-radius: 25px 25px 0 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .screen-title {
            color: #F8FAFC;
            font-size: 18px;
            font-weight: 600;
        }

        .screen-content {
            padding: 20px;
        }

        /* 로그인 화면 */
        .login-container {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100%;
            padding: 40px 30px;
        }

        .logo {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, #6366F1, #8B5CF6);
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 20px;
            font-size: 32px;
        }

        .app-name {
            color: #F8FAFC;
            font-size: 28px;
            font-weight: 700;
            margin-bottom: 10px;
        }

        .app-tagline {
            color: #94A3B8;
            font-size: 16px;
            margin-bottom: 40px;
            text-align: center;
        }

        .input-group {
            width: 100%;
            margin-bottom: 15px;
        }

        .input-field {
            width: 100%;
            padding: 15px;
            background: #1E293B;
            border: 2px solid #334155;
            border-radius: 12px;
            color: #F8FAFC;
            font-size: 16px;
            transition: border-color 0.3s ease;
        }

        .input-field:focus {
            outline: none;
            border-color: #6366F1;
        }

        .primary-btn {
            width: 100%;
            padding: 16px;
            background: linear-gradient(135deg, #6366F1, #8B5CF6);
            border: none;
            border-radius: 12px;
            color: white;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            margin: 10px 0;
        }

        .primary-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(99, 102, 241, 0.4);
        }

        .social-login {
            display: flex;
            gap: 10px;
            width: 100%;
            margin-top: 20px;
        }

        .social-btn {
            flex: 1;
            padding: 12px;
            border: 2px solid #334155;
            border-radius: 8px;
            background: transparent;
            color: #F8FAFC;
            font-size: 14px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .social-btn:hover {
            border-color: #6366F1;
            background: rgba(99, 102, 241, 0.1);
        }

        /* 메인 대시보드 */
        .dashboard-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .user-greeting {
            color: #F8FAFC;
            font-size: 20px;
            font-weight: 600;
        }

        .user-subtitle {
            color: #94A3B8;
            font-size: 14px;
        }

        .notification-btn {
            width: 40px;
            height: 40px;
            background: #1E293B;
            border: none;
            border-radius: 10px;
            color: #F8FAFC;
            cursor: pointer;
        }

        .ad-banner {
            background: linear-gradient(135deg, #F59E0B, #F97316);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 20px;
            color: white;
            text-align: center;
            cursor: pointer;
            transition: transform 0.3s ease;
        }

        .ad-banner:hover {
            transform: scale(1.02);
        }

        .stats-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 20px;
        }

        .stat-card {
            background: #1E293B;
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            transition: transform 0.3s ease;
        }

        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.3);
        }

        .stat-number {
            color: #6366F1;
            font-size: 24px;
            font-weight: 700;
        }

        .stat-label {
            color: #94A3B8;
            font-size: 12px;
            margin-top: 5px;
        }

        .quick-actions {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }

        .action-btn {
            flex: 1;
            padding: 15px;
            background: #1E293B;
            border: 2px solid #334155;
            border-radius: 12px;
            color: #F8FAFC;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: center;
        }

        .action-btn:hover {
            border-color: #6366F1;
            background: rgba(99, 102, 241, 0.1);
        }

        .action-btn.primary {
            background: linear-gradient(135deg, #6366F1, #8B5CF6);
            border-color: transparent;
        }

        /* 러닝 기록 화면 */
        .running-header {
            text-align: center;
            margin-bottom: 30px;
        }

        .running-status {
            color: #10B981;
            font-size: 16px;
            font-weight: 600;
            margin-bottom: 10px;
        }

        .running-time {
            color: #F8FAFC;
            font-size: 48px;
            font-weight: 700;
            font-family: 'Courier New', monospace;
        }

        .metrics-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 30px;
        }

        .metric-card {
            background: #1E293B;
            border-radius: 15px;
            padding: 20px;
            text-align: center;
        }

        .metric-value {
            color: #F8FAFC;
            font-size: 20px;
            font-weight: 600;
        }

        .metric-unit {
            color: #94A3B8;
            font-size: 12px;
        }

        .metric-label {
            color: #94A3B8;
            font-size: 14px;
            margin-top: 5px;
        }

        .map-placeholder {
            background: #1E293B;
            border-radius: 15px;
            height: 200px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #94A3B8;
            margin-bottom: 20px;
            position: relative;
            overflow: hidden;
        }

        .running-path {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 80%;
            height: 60%;
            border: 3px solid #10B981;
            border-radius: 20px;
            border-style: dashed;
            animation: pathGlow 2s infinite;
        }

        @keyframes pathGlow {
            0%, 100% { opacity: 0.6; }
            50% { opacity: 1; }
        }

        .control-buttons {
            display: flex;
            gap: 10px;
        }

        .control-btn {
            flex: 1;
            padding: 15px;
            border: none;
            border-radius: 12px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .stop-btn {
            background: #EF4444;
            color: white;
        }

        .pause-btn {
            background: #F59E0B;
            color: white;
        }

        /* 커뮤니티 피드 */
        .feed-post {
            background: #1E293B;
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 15px;
            transition: transform 0.3s ease;
        }

        .feed-post:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.3);
        }

        .post-header {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }

        .user-avatar {
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, #6366F1, #8B5CF6);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: 600;
            margin-right: 10px;
        }

        .post-user-info {
            flex: 1;
        }

        .post-username {
            color: #F8FAFC;
            font-weight: 600;
            font-size: 14px;
        }

        .post-time {
            color: #94A3B8;
            font-size: 12px;
        }

        .post-content {
            color: #F8FAFC;
            line-height: 1.5;
            margin-bottom: 15px;
        }

        .post-stats {
            display: flex;
            gap: 20px;
            margin-bottom: 15px;
        }

        .post-stat {
            color: #94A3B8;
            font-size: 12px;
        }

        .post-stat.highlight {
            color: #10B981;
            font-weight: 600;
        }

        .post-actions {
            display: flex;
            gap: 15px;
            padding-top: 15px;
            border-top: 1px solid #334155;
        }

        .post-action {
            background: none;
            border: none;
            color: #94A3B8;
            cursor: pointer;
            font-size: 14px;
            transition: color 0.3s ease;
        }

        .post-action:hover {
            color: #6366F1;
        }

        .post-action.liked {
            color: #EF4444;
        }

        /* 네비게이션 */
        .bottom-nav {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: #1E293B;
            padding: 15px;
            border-radius: 0 0 25px 25px;
            display: flex;
            justify-content: space-around;
        }

        .nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            color: #94A3B8;
            cursor: pointer;
            transition: color 0.3s ease;
            font-size: 12px;
        }

        .nav-item:hover, .nav-item.active {
            color: #6366F1;
        }

        .nav-icon {
            font-size: 20px;
            margin-bottom: 5px;
        }

        /* 공통 애니메이션 */
        .fade-in {
            animation: fadeIn 0.5s ease-in;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .pulse {
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }

        /* 반응형 */
        @media (max-width: 768px) {
            .prototype-container {
                flex-direction: column;
                align-items: center;
            }
            
            .phone-mockup {
                width: 90%;
                max-width: 360px;
            }
        }

        /* 프로토타입 네비게이션 */
        .prototype-nav {
            text-align: center;
            margin-bottom: 20px;
        }

        .prototype-nav h1 {
            color: #F8FAFC;
            margin-bottom: 10px;
            font-size: 28px;
        }

        .prototype-nav p {
            color: #94A3B8;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <div class="prototype-nav">
        <h1>🏃‍♂️ RunTogether</h1>
        <p>인터랙티브 프로토타입 - 각 화면을 클릭해보세요!</p>
    </div>

    <div class="prototype-container">
        <!-- 로그인 화면 -->
        <div class="phone-mockup" onclick="toggleScreen(this)">
            <div class="screen">
                <div class="login-container fade-in">
                    <div class="logo">🏃‍♂️</div>
                    <h1 class="app-name">RunTogether</h1>
                    <p class="app-tagline">러너들의 기록과 커뮤니티</p>
                    
                    <div class="input-group">
                        <input type="email" class="input-field" placeholder="이메일 주소" />
                    </div>
                    <div class="input-group">
                        <input type="password" class="input-field" placeholder="비밀번호" />
                    </div>
                    
                    <button class="primary-btn" onclick="showAlert('로그인 성공!')">로그인</button>
                    
                    <div class="social-login">
                        <button class="social-btn">Google</button>
                        <button class="social-btn">Apple</button>
                        <button class="social-btn">카카오</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- 메인 대시보드 -->
        <div class="phone-mockup" onclick="toggleScreen(this)">
            <div class="screen">
                <div class="screen-header">
                    <span class="screen-title">대시보드</span>
                    <button class="notification-btn">🔔</button>
                </div>
                <div class="screen-content fade-in">
                    <div class="dashboard-header">
                        <div>
                            <div class="user-greeting">안녕하세요, 러너님!</div>
                            <div class="user-subtitle">오늘도 건강한 하루 되세요</div>
                        </div>
                    </div>

                    <div class="ad-banner pulse" onclick="showAlert('광고 클릭!')">
                        <h3>🎯 Nike 러닝화 특가!</h3>
                        <p>지금 구매하면 30% 할인</p>
                    </div>

                    <div class="stats-grid">
                        <div class="stat-card">
                            <div class="stat-number">42.1</div>
                            <div class="stat-label">이번 주 총 거리(km)</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number">5</div>
                            <div class="stat-label">이번 주 런닝 횟수</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number">4:32</div>
                            <div class="stat-label">평균 페이스(/km)</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number">1,240</div>
                            <div class="stat-label">총 칼로리 소모</div>
                        </div>
                    </div>

                    <div class="quick-actions">
                        <button class="action-btn primary" onclick="showAlert('런닝 시작!')">🏃‍♂️ 런닝 시작</button>
                        <button class="action-btn" onclick="showAlert('기록 보기')">📊 기록 보기</button>
                    </div>
                </div>
                <div class="bottom-nav">
                    <div class="nav-item active">
                        <div class="nav-icon">🏠</div>
                        <div>홈</div>
                    </div>
                    <div class="nav-item">
                        <div class="nav-icon">🏃‍♂️</div>
                        <div>런닝</div>
                    </div>
                    <div class="nav-item">
                        <div class="nav-icon">👥</div>
                        <div>커뮤니티</div>
                    </div>
                    <div class="nav-item">
                        <div class="nav-icon">👤</div>
                        <div>프로필</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- 런닝 트래킹 화면 -->
        <div class="phone-mockup" onclick="toggleScreen(this)">
            <div class="screen">
                <div class="screen-header">
                    <span class="screen-title">런닝 중</span>
                    <button class="notification-btn">⏸️</button>
                </div>
                <div class="screen-content fade-in">
                    <div class="running-header">
                        <div class="running-status">🔴 진행 중</div>
                        <div class="running-time">23:45</div>
                    </div>

                    <div class="metrics-grid">
                        <div class="metric-card">
                            <div class="metric-value">5.2</div>
                            <div class="metric-unit">km</div>
                            <div class="metric-label">거리</div>
                        </div>
                        <div class="metric-card">
                            <div class="metric-value">4:34</div>
                            <div class="metric-unit">/km</div>
                            <div class="metric-label">페이스</div>
                        </div>
                        <div class="metric-card">
                            <div class="metric-value">13.1</div>
                            <div class="metric-unit">km/h</div>
                            <div class="metric-label">속도</div>
                        </div>
                        <div class="metric-card">
                            <div class="metric-value">312</div>
                            <div class="metric-unit">kcal</div>
                            <div class="metric-label">칼로리</div>
                        </div>
                    </div>

                    <div class="map-placeholder">
                        <div class="running-path"></div>
                        <div style="z-index: 1;">📍 실시간 경로 추적중</div>
                    </div>

                    <div class="control-buttons">
                        <button class="control-btn pause-btn" onclick="showAlert('일시정지')">⏸️ 일시정지</button>
                        <button class="control-btn stop-btn" onclick="showAlert('런닝 종료')">⏹️ 종료</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- 커뮤니티 피드 -->
        <div class="phone-mockup" onclick="toggleScreen(this)">
            <div class="screen">
                <div class="screen-header">
                    <span class="screen-title">커뮤니티</span>
                    <button class="notification-btn">✏️</button>
                </div>
                <div class="screen-content fade-in">
                    <div class="feed-post">
                        <div class="post-header">
                            <div class="user-avatar">김</div>
                            <div class="post-user-info">
                                <div class="post-username">김민수</div>
                                <div class="post-time">2시간 전</div>
                            </div>
                        </div>
                        <div class="post-content">
                            오늘 첫 10km 완주 성공! 🎉 목표했던 1시간을 1분 단축했어요. 너무 뿌듯합니다!
                        </div>
                        <div class="post-stats">
                            <div class="post-stat highlight">10.0km</div>
                            <div class="post-stat">59:32</div>
                            <div class="post-stat">평균 5:57/km</div>
                        </div>
                        <div class="post-actions">
                            <button class="post-action liked" onclick="toggleLike(this)">❤️ 좋아요 12</button>
                            <button class="post-action" onclick="showAlert('댓글 작성')">💬 댓글 3</button>
                            <button class="post-action" onclick="showAlert('공유하기')">📤 공유</button>
                        </div>
                    </div>

                    <div class="feed-post">
                        <div class="post-header">
                            <div class="user-avatar">박</div>
                            <div class="post-user-info">
                                <div class="post-username">박지영</div>
                                <div class="post-time">5시간 전</div>
                            </div>
                        </div>
                        <div class="post-content">
                            새벽 런닝 루트 추천해주세요! 한강공원 말고 다른 곳도 가보고 싶어요 🌅
                        </div>
                        <div class="post-stats">
                            <div class="post-stat">질문</div>
                        </div>
                        <div class="post-actions">
                            <button class="post-action" onclick="toggleLike(this)">❤️ 좋아요 8</button>
                            <button class="post-action" onclick="showAlert('댓글 작성')">💬 댓글 15</button>
                            <button class="post-action" onclick="showAlert('공유하기')">📤 공유</button>
                        </div>
                    </div>

                    <div class="ad-banner" onclick="showAlert('광고 클릭!')">
                        <h4>🏃‍♀️ Garmin 러닝워치</h4>
                        <p>정확한 기록 측정의 시작</p>
                    </div>

                    <div class="feed-post">
                        <div class="post-header">
                            <div class="user-avatar">이</div>
                            <div class="post-user-info">
                                <div class="post-username">이성호</div>
                                <div class="post-time">1일 전</div>
                            </div>
                        </div>
                        <div class="post-content">
                            마라톤 대회 준비중인 분들! 효과적인 페이스 훈련 방법 공유합니다 💪
                        </div>
                        <div class="post-stats">
                            <div class="post-stat highlight">42.2km</div>
                            <div class="post-stat">3:45:20</div>
                            <div class="post-stat">평균 5:20/km</div>
                        </div>
                        <div class="post-actions">
                            <button class="post-action" onclick="toggleLike(this)">❤️ 좋아요 24</button>
                            <button class="post-action" onclick="showAlert('댓글 작성')">💬 댓글 8</button>
                            <button class="post-action" onclick="showAlert('공유하기')">📤 공유</button>
                        </div>
                    </div>
                </div>
                <div class="bottom-nav">
                    <div class="nav-item">
                        <div class="nav-icon">🏠</div>
                        <div>홈</div>
                    </div>
                    <div class="nav-item">
                        <div class="nav-icon">🏃‍♂️</div>
                        <div>런닝</div>
                    </div>
                    <div class="nav-item active">
                        <div class="nav-icon">👥</div>
                        <div>커뮤니티</div>
                    </div>
                    <div class="nav-item">
                        <div class="nav-icon">👤</div>
                        <div>프로필</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- 프로필/통계 화면 -->
        <div class="phone-mockup" onclick="toggleScreen(this)">
            <div class="screen">
                <div class="screen-header">
                    <span class="screen-title">내 프로필</span>
                    <button class="notification-btn">⚙️</button>
                </div>
                <div class="screen-content fade-in">
                    <div style="text-align: center; margin-bottom: 30px;">
                        <div style="width: 80px; height: 80px; background: linear-gradient(135deg, #6366F1, #8B5CF6); border-radius: 50%; display: flex; align-items: center; justify-content: center; color: white; font-size: 32px; margin: 0 auto 15px;">👤</div>
                        <h2 style="color: #F8FAFC; margin-bottom: 5px;">김민수</h2>
                        <p style="color: #94A3B8;">초보 러너 • 6개월차</p>
                    </div>

                    <div class="stats-grid" style="grid-template-columns: 1fr 1fr 1fr; gap: 10px; margin-bottom: 20px;">
                        <div class="stat-card">
                            <div class