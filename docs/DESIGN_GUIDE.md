# UI/UX 디자인 가이드

## 컬러 팔레트
- Primary: #FF6B6B (메인 액션, 러닝 버튼)
- Secondary: #4ECDC4 (성공, 완료 상태)
- Accent: #FFE66D (강조, 기록 하이라이트)
- Background: #2C3E50 (배경)
- Surface: #34495E (카드 배경)
- Text: #ECF0F1 (메인 텍스트)
- Text-Secondary: #BDC3C7 (보조 텍스트)

## 주요 화면
1. 로그인/회원가입
2. 메인 대시보드 (광고 배너 포함)
3. 러닝 트래킹 화면
4. 러닝 완료 & 기록
5. 커뮤니티 피드
6. 프로필 & 통계

<!-- INTERACTIVE PROTOTYPE START -->
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RunTogether - 인터랙티브 프로토타입</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #2C3E50, #34495E);
            min-height: 100vh;
            padding: 20px;
            overflow-x: auto;
        }
        
        .prototype-container {
            display: flex;
            gap: 20px;
            justify-content: center;
            flex-wrap: wrap;
            max-width: 1400px;
            margin: 0 auto;
        }
        
        .phone-mockup {
            width: 320px;
            background: linear-gradient(145deg, #34495E, #2C3E50);
            border-radius: 30px;
            padding: 15px;
            box-shadow: 
                0 20px 60px rgba(0,0,0,0.4),
                inset 0 1px 0 rgba(255,255,255,0.1);
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            cursor: pointer;
        }
        
        .phone-mockup:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 
                0 30px 80px rgba(255, 107, 107, 0.3),
                inset 0 1px 0 rgba(255,255,255,0.2);
        }
        
        .screen {
            background: #2C3E50;
            border-radius: 20px;
            height: 600px;
            overflow: hidden;
            position: relative;
            border: 2px solid #34495E;
        }
        
        .screen-header {
            background: #34495E;
            padding: 15px 20px;
            color: #ECF0F1;
            font-weight: 600;
            border-bottom: 1px solid #4A5F7A;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .screen-content {
            padding: 20px;
            height: calc(100% - 60px);
            overflow-y: auto;
            color: #ECF0F1;
        }
        
        /* 로그인 화면 */
        .login-form {
            display: flex;
            flex-direction: column;
            gap: 20px;
            margin-top: 60px;
        }
        
        .logo {
            text-align: center;
            margin-bottom: 40px;
        }
        
        .logo h1 {
            color: #FF6B6B;
            font-size: 28px;
            margin-bottom: 5px;
        }
        
        .logo p {
            color: #BDC3C7;
            font-size: 14px;
        }
        
        .input-group {
            position: relative;
        }
        
        .input-group input {
            width: 100%;
            padding: 15px;
            border: 2px solid #4A5F7A;
            border-radius: 12px;
            background: #34495E;
            color: #ECF0F1;
            font-size: 16px;
            transition: all 0.3s ease;
        }
        
        .input-group input:focus {
            outline: none;
            border-color: #FF6B6B;
            box-shadow: 0 0 0 3px rgba(255, 107, 107, 0.1);
        }
        
        .btn {
            padding: 15px 25px;
            border: none;
            border-radius: 12px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: center;
        }
        
        .btn-primary {
            background: #FF6B6B;
            color: white;
        }
        
        .btn-primary:hover {
            background: #FF5252;
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(255, 107, 107, 0.4);
        }
        
        .btn-social {
            background: #4ECDC4;
            color: white;
            margin-top: 10px;
        }
        
        .btn-social:hover {
            background: #26D0CE;
        }
        
        /* 대시보드 */
        .dashboard-stats {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .stat-card {
            background: #34495E;
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            border: 1px solid #4A5F7A;
            transition: all 0.3s ease;
        }
        
        .stat-card:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(255, 230, 109, 0.2);
        }
        
        .stat-value {
            font-size: 24px;
            font-weight: bold;
            color: #FFE66D;
            margin-bottom: 5px;
        }
        
        .stat-label {
            color: #BDC3C7;
            font-size: 12px;
        }
        
        .ad-banner {
            background: linear-gradient(45deg, #FF6B6B, #4ECDC4);
            padding: 15px;
            border-radius: 12px;
            margin: 20px 0;
            text-align: center;
            color: white;
            position: relative;
            overflow: hidden;
        }
        
        .ad-banner::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255,255,255,0.1), transparent);
            animation: shimmer 3s infinite;
        }
        
        @keyframes shimmer {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        .quick-actions {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-top: 20px;
        }
        
        .action-btn {
            background: #34495E;
            border: 2px solid #4A5F7A;
            padding: 20px;
            border-radius: 15px;
            color: #ECF0F1;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .action-btn:hover {
            background: #FF6B6B;
            border-color: #FF6B6B;
            transform: scale(1.05);
        }
        
        /* 러닝 트래킹 */
        .running-display {
            text-align: center;
            margin: 40px 0;
        }
        
        .running-time {
            font-size: 48px;
            font-weight: bold;
            color: #FFE66D;
            margin-bottom: 10px;
            font-family: 'Courier New', monospace;
        }
        
        .running-stats {
            display: flex;
            justify-content: space-around;
            margin: 30px 0;
        }
        
        .running-stat {
            text-align: center;
        }
        
        .running-stat-value {
            font-size: 20px;
            font-weight: bold;
            color: #4ECDC4;
        }
        
        .running-stat-label {
            font-size: 12px;
            color: #BDC3C7;
            margin-top: 5px;
        }
        
        .control-buttons {
            display: flex;
            gap: 15px;
            justify-content: center;
            margin-top: 40px;
        }
        
        .btn-control {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            border: none;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            transition: all 0.3s ease;
        }
        
        .btn-pause {
            background: #FFE66D;
            color: #2C3E50;
        }
        
        .btn-stop {
            background: #FF6B6B;
            color: white;
        }
        
        .btn-control:hover {
            transform: scale(1.1);
        }
        
        /* 커뮤니티 피드 */
        .post {
            background: #34495E;
            border-radius: 15px;
            padding: 15px;
            margin-bottom: 15px;
            border: 1px solid #4A5F7A;
            transition: all 0.3s ease;
        }
        
        .post:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.2);
        }
        
        .post-header {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
        }
        
        .post-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: #FF6B6B;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            margin-right: 10px;
        }
        
        .post-info h4 {
            color: #ECF0F1;
            font-size: 14px;
            margin-bottom: 2px;
        }
        
        .post-info span {
            color: #BDC3C7;
            font-size: 12px;
        }
        
        .post-content {
            color: #ECF0F1;
            margin: 10px 0;
            line-height: 1.5;
        }
        
        .post-stats {
            display: flex;
            gap: 20px;
            margin: 10px 0;
            padding: 10px;
            background: #2C3E50;
            border-radius: 8px;
        }
        
        .post-stat {
            font-size: 12px;
            color: #4ECDC4;
        }
        
        .post-actions {
            display: flex;
            gap: 15px;
            margin-top: 10px;
        }
        
        .post-action {
            background: none;
            border: none;
            color: #BDC3C7;
            cursor: pointer;
            padding: 5px 10px;
            border-radius: 20px;
            transition: all 0.3s ease;
            font-size: 12px;
        }
        
        .post-action:hover {
            background: #4A5F7A;
            color: #ECF0F1;
        }
        
        .fab {
            position: absolute;
            bottom: 20px;
            right: 20px;
            width: 56px;
            height: 56px;
            border-radius: 50%;
            background: #FF6B6B;
            border: none;
            color: white;
            font-size: 24px;
            cursor: pointer;
            box-shadow: 0 8px 25px rgba(255, 107, 107, 0.4);
            transition: all 0.3s ease;
        }
        
        .fab:hover {
            transform: scale(1.1);
        }
        
        /* 프로필 */
        .profile-header {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .profile-avatar {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            background: #FF6B6B;
            margin: 0 auto 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 24px;
            font-weight: bold;
        }
        
        .profile-name {
            color: #ECF0F1;
            font-size: 20px;
            margin-bottom: 5px;
        }
        
        .profile-stats {
            display: flex;
            justify-content: space-around;
            margin: 20px 0;
        }
        
        .profile-stat {
            text-align: center;
        }
        
        .profile-stat-value {
            font-size: 18px;
            font-weight: bold;
            color: #4ECDC4;
        }
        
        .profile-stat-label {
            font-size: 12px;
            color: #BDC3C7;
            margin-top: 3px;
        }
        
        .screen-title {
            color: #ECF0F1;
            font-size: 18px;
            text-align: center;
            margin-bottom: 10px;
        }
        
        .status-indicator {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background: #4ECDC4;
            display: inline-block;
            margin-left: 10px;
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.5; }
            100% { opacity: 1; }
        }
        
        .screen.active {
            transform: scale(1.05);
            box-shadow: 0 0 30px rgba(255, 107, 107, 0.5);
        }
        
        /* 반응형 */
        @media (max-width: 768px) {
            .prototype-container {
                flex-direction: column;
                align-items: center;
            }
            
            .phone-mockup {
                width: 300px;
            }
        }
        
        /* 스크롤바 스타일 */
        .screen-content::-webkit-scrollbar {
            width: 4px;
        }
        
        .screen-content::-webkit-scrollbar-track {
            background: #2C3E50;
        }
        
        .screen-content::-webkit-scrollbar-thumb {
            background: #4A5F7A;
            border-radius: 2px;
        }
    </style>
</head>
<body>
    <div class="prototype-container">
        <!-- 로그인 화면 -->
        <div class="phone-mockup" onclick="toggleActive(this)">
            <div class="screen">
                <div class="screen-header">
                    <span>로그인</span>
                    <span>9:41</span>
                </div>
                <div class="screen-content">
                    <div class="logo">
                        <h1>🏃‍♂️ RunTogether</h1>
                        <p>함께 뛰는 즐거움</p>
                    </div>
                    <div class="login-form">
                        <div class="input-group">
                            <input type="email" placeholder="이메일 주소" id="email">
                        </div>
                        <div class="input-group">
                            <input type="password" placeholder="비밀번호" id="password">
                        </div>
                        <button class="btn btn-primary" onclick="showAlert('로그인 성공!')">로그인</button>
                        <button class="btn btn-social">Google로 계속하기</button>
                        <button class="btn btn-social" style="background: #FFE66D; color: #2C3E50;">카카오로 계속하기</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- 메인 대시보드 -->
        <div class="phone-mockup" onclick="toggleActive(this)">
            <div class="screen">
                <div class="screen-header">
                    <span>대시보드</span>
                    <span class="status-indicator"></span>
                </div>
                <div class="screen-content">
                    <div class="screen-title">안녕하세요, 김민수님! 👋</div>
                    
                    <div class="dashboard-stats">
                        <div class="stat-card">
                            <div class="stat-value">12.5</div>
                            <div class="stat-label">이번 주 총 거리 (km)</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value">3</div>
                            <div class="stat-label">이번 주 러닝 횟수</div>
                        </div>
                    </div>
                    
                    <div class="ad-banner">
                        <strong>🎯 나이키 러닝화 특가!</strong><br>
                        <small>지금 구매하면 30% 할인 혜택</small>
                    </div>
                    
                    <div class="quick-actions">
                        <div class="action-btn" onclick="showAlert('러닝 시작!')">
                            🏃‍♂️<br>러닝 시작
                        </div>
                        <div class="action-btn" onclick="showAlert('기록 확인')">
                            📊<br>기록 보기
                        </div>
                        <div class="action-btn" onclick="showAlert('커뮤니티 이동')">
                            👥<br>커뮤니티
                        </div>
                        <div class="action-btn" onclick="showAlert('프로필 설정')">
                            ⚙️<br>설정
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- 러닝 트래킹 화면 -->
        <div class="phone-mockup" onclick="toggleActive(this)">
            <div class="screen">
                <div class="screen-header">
                    <span>러닝 중</span>
                    <span style="color: #FF6B6B;">● REC</span>
                </div>
                <div class="screen-content">
                    <div class="running-display">
                        <div class="running-time" id="runningTime">00:15:42</div>
                        <div style="color: #BDC3C7; margin-bottom: 30px;">진행 시간</div>
                        
                        <div class="running-stats">
                            <div class="running-stat">
                                <div class="running-stat-value">3.2</div>
                                <div class="running-stat-label">거리 (km)</div>
                            </div>
                            <div class="running-stat">
                                <div class="running-stat-value">5:12</div>
                                <div class="running-stat-label">평균 페이스</div>
                            </div>
                            <div class="running-stat">
                                <div class="running-stat-value">320</div>
                                <div class="running-stat-label">칼로리</div>
                            </div>
                        </div>
                        
                        <div style="background: #34495E; height: 150px; border-radius: 10px; margin: 20px 0; display: flex; align-items: center; justify-content: center; color: #BDC3C7;">
                            🗺️ GPS 경로 지도
                        </div>
                        
                        <div class="control-buttons">
                            <button class="btn-control btn-pause" onclick="pauseRunning()">⏸️</button>
                            <button class="btn-control btn-stop" onclick="showAlert('러닝 완료!')">⏹️</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- 커뮤니티 피드 -->
        <div class="phone-mockup" onclick="toggleActive(this)">
            <div class="screen">
                <div class="screen-header">
                    <span>커뮤니티</span>
                    <span>💬</span>
                </div>
                <div class="screen-content">
                    <div class="post">
                        <div class="post-header">
                            <div class="post-avatar">박</div>
                            <div class="post-info">
                                <h4>박지영</h4>
                                <span>2시간 전</span>
                            </div>
                        </div>
                        <div class="post-content">
                            오늘 아침 한강에서 10km 완주! 🎉<br>
                            날씨가 너무 좋아서 기분 최고였어요 ☀️
                        </div>
                        <div class="post-stats">
                            <span class="post-stat">📏 10.2km</span>
                            <span class="post-stat">⏱️ 58:24</span>
                            <span class="post-stat">🔥 520cal</span>
                        </div>
                        <div class="post-actions">
                            <button class="post-action" onclick="likePost(this)">👍 좋아요 (12)</button>
                            <button class="post-action">💬 댓글 (3)</button>
                            <button class="post-action">🔗 공유</button>
                        </div>
                    </div>
                    
                    <div class="post">
                        <div class="post-header">
                            <div class="post-avatar">이</div>
                            <div class="post-info">
                                <h4>이성호</h4>
                                <span>5시간 전</span>
                            </div>
                        </div>
                        <div class="post-content">
                            마라톤 준비하시는 분들께 팁! 💡<br>
                            장거리 훈련할 때는 심박수 관리가 정말 중요해요. 
                        </div>
                        <div class="post-stats">
                            <span class="post-stat">📏 21.1km</span>
                            <span class="post-stat">⏱️ 1:45:32</span>
                            <span class="post-stat">💓 평균 160bpm</span>
                        </div>
                        <div class="post-actions">
                            <button class="post-action" onclick="likePost(this)">👍 좋아요 (25)</button>
                            <button class="post-action">💬 댓글 (8)</button>
                            <button class="post-action">🔗 공유</button>
                        </div>
                    </div>
                    
                    <div class="ad-banner" style="margin: 15px 0;">
                        <strong>🍎 러닝 후 회복음료</strong><br>
                        <small>단백질과 전해질로 빠른 회복!</small>
                    </div>
                </div>
                <button class="fab" onclick="showAlert('새 게시글 작성')">✏️</button>
            </div>
        </div>

        <!-- 프로필 & 통계 -->
        <div class="phone-mockup" onclick="toggleActive(this)">
            <div class="screen">
                <div class="screen-header">
                    <span>프로필</span>
                    <span>⚙️</span>
                </div>
                <div class="screen-content">
                    <div class="profile-header">
                        <div class="profile-avatar">김</div>
                        <div class="profile-name">김민수</div>
                        <div style="color: #BDC3C7; font-size: 14px;">초보 러너 • 6개월차</div>
                    </div>
                    
                    <div class="profile-stats">
                        <div class="profile-stat">
                            <div class="profile-stat-value">127.5</div>
                            <div class="profile-stat-label">총 거리 (km)</div>
                        </div>
                        <div class="profile-stat">
                            <div class="profile-stat-value">32</div>
                            <div class="profile-stat-label">총 러닝 횟수</div>
                        </div>
                        <div class="profile-stat">
                            <div class="profile-stat-value">48</div>
                            <div class="profile-stat-label">팔로워</div>
                        </div>
                    </div>
                    
                    <div class="dashboard-stats">
                        <div class="stat-card">
                            <div class="stat-value">5:24</div>
                            <div class="stat-label">평균 페이스</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value">2,840</div>
                            <div class="stat-label">총 칼로리</div>
                        </div>
                    </div>
                    
                    <div class="quick-actions" style="grid-template-columns: 1fr;">
                        <div class="action-btn" onclick="showAlert('상세 통계 보기')">
                            📈 상세 통계 보기
                        </div>
                        <div class="action-btn" onclick="showAlert('러닝 기록')">
                            📋 러닝 기록
                        </div>
                        <div class="action-btn" onclick="showAlert('설정')">
                            ⚙️ 앱 설정
                        </div>
                        <div class="action-btn" onclick="showAlert('로그아웃')">
                            🚪 로그아웃
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- 러닝 완료 화면 -->
        <div class="phone-mockup" onclick="toggleActive(this)">
            <div class="screen">
                <div class="screen-header">
                    <span>러닝 완료</span>
                    <span>🎉</span>
                </div>
                <div class="screen-content">
                    <div class="running-display">
                        <div style="font-size: 24px; color: #4ECDC4; margin-bottom: 20px;">
                            🎊 훌륭해요! 🎊
                        </div>
                        
                        <div class="dashboard-stats">
                            <div class="stat-card">
                                <div class="stat-value">5.2</div>
                                <div class="stat-label">거리 (km)</div>
                            </div>
                            <div class="stat-card">
                                <div class="stat-value">28:15</div>
                                <div class="stat-label">시간</div>
                            </div>
                            <div class="stat-card">
                                <div class="stat-value">5:26</div>
                                <div class="stat-label">평균 페이스</div>
                            </div>
                            <div class="stat-card">
                                <div class="stat-value">420</div>
                                <div class="stat-label">칼로리</div>
                            </div>
                        </div>
                        
                        <div class="ad-banner" style="margin: 20px 0;">
                            <strong>🏆 개인 기록 달성!</strong><br>
                            <small>축하드립니다. 이번 달 목표의 80% 완성!</small>
                        </div>
                        
                        <div class="quick-actions">
                            <div class="action-btn" onclick="showAlert('커뮤니티에 공유')">
                                📤<br>공유하기
                            </div>
                            <div class="action-btn" onclick="showAlert('러닝 저장')">
                                💾<br>저장
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        let runningInterval;
        let seconds = 942; // 15:42
        
        function toggleActive(