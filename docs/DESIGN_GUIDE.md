# UI/UX 디자인 가이드

## 컬러 팔레트
```
## 컬러 팔레트
- Primary: #0D6EFF (나이키 블루)
- Secondary: #FFFFFF (화이트)
- Accent: #FF0000 (나이키 레드)
```

## 주요 화면
```
## 주요 화면
1.  로그인/회원가입 화면
2.  메인 화면 (배틀 매칭)
3.  배틀 진행 화면
4.  결과 화면
```

## HTML 프로토타입
```html
<!-- INTERACTIVE PROTOTYPE START -->
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>RunBattle</title>
<style>
/* CSS */
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
    color: #333;
}

.container {
    max-width: 600px;
    margin: 20px auto;
    padding: 20px;
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
    color: #0D6EFF; /* Primary Color */
}

.button {
    display: block;
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: none;
    background-color: #0D6EFF; /* Primary Color */
    color: white;
    text-align: center;
    text-decoration: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
}

.button:hover {
    background-color: #0056b3;
}

.input-group {
    margin-bottom: 15px;
}

.input-group label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
}

.input-group input {
    width: 100%;
    padding: 8px;
    border: 1px solid #ddd;
    border-radius: 4px;
    box-sizing: border-box;
}

/* Nike Style Enhancements */
body {
    background-color: #000; /* Black Background */
    color: #fff; /* White Text */
}

.container {
    background-color: rgba(255, 255, 255, 0.05); /* Slightly transparent white */
    box-shadow: 0 0 20px rgba(255, 0, 0, 0.3); /* Red glow effect */
}

h1 {
    color: #FF0000; /* Nike Red */
    text-transform: uppercase;
    letter-spacing: 2px;
}

.button {
    background-color: #FF0000; /* Nike Red */
    border: 2px solid #fff; /* White border */
}

.button:hover {
    background-color: #b30000;
}

/* 배틀 화면 스타일 */
#battleScreen {
    display: none;
    text-align: center;
}

#battleScreen h2 {
    color: #FF0000;
    margin-bottom: 20px;
}

#battleProgress {
    width: 80%;
    margin: 20px auto;
    height: 30px;
    background-color: #222;
    border-radius: 15px;
    overflow: hidden;
}

#myProgress, #opponentProgress {
    height: 100%;
    background-color: #0D6EFF;
    width: 0%;
    transition: width 0.5s ease;
}

.progressLabel {
    display: block;
    margin-top: 5px;
    font-size: 0.8em;
}

/* 결과 화면 스타일 */
#resultScreen {
    display: none;
    text-align: center;
}

#resultScreen h2 {
    color: #FF0000;
    margin-bottom: 20px;
}
</style>
</head>
<body>

<div class="container" id="loginScreen">
    <h1>RunBattle</h1>
    <a href="#" class="button" onclick="showMainScreen()">SNS 로그인 (구글)</a>
    <a href="#" class="button" onclick="showMainScreen()">SNS 로그인 (카카오)</a>
    <a href="#" class="button" onclick="showMainScreen()">SNS 로그인 (애플)</a>
</div>

<div class="container" id="mainScreen" style="display:none;">
    <h1>RunBattle</h1>
    <p>환영합니다, 러너!</p>
    <button class="button" onclick="findBattle()">배틀 찾기 (1km)</button>
    <button class="button" onclick="findBattle()">배틀 찾기 (3km)</button>
    <button class="button" onclick="findBattle()">배틀 찾기 (5km)</button>
</div>

<div class="container" id="battleScreen" style="display:none;">
    <h2>실시간 배틀 중!</h2>
    <p>상대를 기다리는 중...</p>

    <div id="battleProgress">
        <div id="myProgress"></div>
    </div>
    <span class="progressLabel">나의 진행률</span>

    <div id="battleProgress">
        <div id="opponentProgress"></div>
    </div>
    <span class="progressLabel">상대방 진행률</span>

    <button class="button" onclick="endBattle()">포기하기</button>
</div>

<div class="container" id="resultScreen" style="display:none;">
    <h2>배틀 결과</h2>
    <p id="resultMessage"></p>
    <button class="button" onclick="showMainScreen()">메인 화면으로</button>
</div>

<script>
// JavaScript
function showMainScreen() {
    document.getElementById('loginScreen').style.display = 'none';
    document.getElementById('mainScreen').style.display = 'block';
}

function findBattle() {
    document.getElementById('mainScreen').style.display = 'none';
    document.getElementById('battleScreen').style.display = 'block';

    // 임시로 3초 후 배틀 시작
    setTimeout(startBattle, 3000);
}

function startBattle() {
    // 시뮬레이션: 10초 동안 진행률 증가
    let myProgress = 0;
    let opponentProgress = 0;
    const interval = setInterval(() => {
        myProgress += Math.random() * 10; // 랜덤 진행률
        opponentProgress += Math.random() * 10;

        myProgress = Math.min(myProgress, 100);
        opponentProgress = Math.min(opponentProgress, 100);

        document.getElementById('myProgress').style.width = myProgress + '%';
        document.getElementById('opponentProgress').style.width = opponentProgress + '%';

        if (myProgress >= 100 || opponentProgress >= 100) {
            clearInterval(interval);
            endBattle(myProgress >= 100); // 나의 승리 여부
        }
    }, 500);
}

function endBattle(iWon = false) {
    document.getElementById('battleScreen').style.display = 'none';
    document.getElementById('resultScreen').style.display = 'block';

    const resultMessage = iWon ? "승리하셨습니다!" : "패배하셨습니다.";
    document.getElementById('resultMessage').innerText = resultMessage;
}
</script>

</body>
</html>
<!-- INTERACTIVE PROTOTYPE END -->
```