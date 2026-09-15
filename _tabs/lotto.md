---
title: 무료 로또 번호 생성기
icon: fas fa-ticket-alt
order: 6
layout: page
permalink: /lotto/
---

{% raw %}
<!-- 상단 안내 영역 -->
<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 20px; border: 1px solid #e9ecef;">
    <h4 style="margin-top: 0; color: #28a745;">🍀 이번 주 대박 기원 로또 번호 추첨기</h4>
    <p style="margin-bottom: 0;">나의 생년월일을 바탕으로 한 명리학 기운 분석을 통해 나만의 행운 번호를 무료로 추출해 드립니다.</p>
</div>

<!-- 역대 TOP 7 & 전회차 당첨 번호 확인 영역 -->
<div style="display: flex; flex-wrap: wrap; gap: 15px; margin-bottom: 30px;">
    <div style="flex: 1; min-width: 250px; background-color: #fff; padding: 15px; border-radius: 8px; border: 1px solid #dee2e6; text-align: center;">
        <h5 style="margin: 0 0 10px 0; color: #495057;">📊 역대 최다 출현 숫자 TOP 7</h5>
        <div style="font-size: 1.2em; font-weight: bold; color: #333; letter-spacing: 2px;">
            <span style="color:#b0d840;">43</span>, <span style="color:#aaa;">34</span>, <span style="color:#ff7272;">27</span>, <span style="color:#69c8f2;">17</span>, <span style="color:#fbc400;">1</span>, <span style="color:#69c8f2;">13</span>, <span style="color:#69c8f2;">12</span>
        </div>
    </div>
    <div style="flex: 1; min-width: 250px; background-color: #fff; padding: 15px; border-radius: 8px; border: 1px solid #dee2e6; text-align: center;">
        <h5 style="margin: 0 0 10px 0; color: #495057;">🏆 전회차 당첨 번호 확인</h5>
        <div style="margin-top: 10px;">
            <a href="https://dhlottery.co.kr/gameResult.do?method=byWin" target="_blank" style="display:inline-block; padding:10px 25px; background-color:#28a745; color:white; text-decoration:none; border-radius:5px; font-weight:bold; font-size:1em;">공식 사이트에서 바로 확인하기 ↗</a>
        </div>
    </div>
</div>

<!-- 🔮 사주 맞춤 번호 추출 영역 -->
<div id="lotto-box" style="text-align: center; margin: 20px 0; padding: 30px; background-color: #ffffff; border: 2px solid #856404; border-radius: 15px;">
    <h3 style="margin-top: 0; color: #856404;">🔮 내 사주 맞춤 행운 번호</h3>
    <p style="color: #6c757d; margin-bottom: 20px;">생년월일을 입력하시면 명리학 기반으로 맞춤 번호를 추출합니다.</p>
    
    <input type="date" id="birthDate" style="padding: 10px; font-size: 1.1em; border: 1px solid #ced4da; border-radius: 5px; margin-bottom: 15px;">
    <br>
    <button id="sajuBtn" onclick="window.generateSajuLotto()" style="padding: 15px 35px; font-size: 1.2em; background-color: #856404; color: white; border: none; border-radius: 8px; cursor: pointer; font-weight: bold;">사주 맞춤 번호 추출하기</button>
    
    <p style="font-size: 0.85em; color: #adb5bd; margin-top: 15px; margin-bottom: 0;">🔒 입력하신 정보는 분석용으로만 사용되며, 절대 저장되지 않습니다.</p>

    <!-- 5초 대기 화면 -->
    <div id="saju-timer" style="display: none; text-align: center; color: #dc3545; font-weight: bold; margin-top: 20px; padding: 15px; background-color: #f8d7da; border-radius: 8px;">
        명운을 분석하여 번호를 추출하는 중입니다... <br><span id="sTimeCount" style="font-size: 1.5em;">5</span>초 후 공개
    </div>

    <!-- 고정 멘트 1줄 -->
    <div id="saju-fortune-text" style="display: none; color: #856404; font-weight: bold; margin-top: 25px; padding: 15px; background-color: #fff3cd; border-radius: 8px; font-size: 1.1em; border: 1px dashed #ffe69c;">
        📜 명리학 사주 기반으로 분석된 회원님의 맞춤 추천 번호입니다.
    </div>

    <!-- 로또 공 출력 영역 -->
    <div id="saju-result-balls" style="display: flex; justify-content: center; gap: 10px; margin: 25px 0 10px 0; min-height: 60px; flex-wrap: wrap;"></div>

    <!-- 💰 금전운/재물복 맞춤형 쿠팡 파트너스 추천 박스 (사주 번호 결과 하단 연동) -->
    <div id="lotto-coupang-box" style="display: none; margin-top: 30px; padding: 20px; background: linear-gradient(135deg, #fffdf0 0%, #fff3cd 100%); border: 1.5px solid #ffeeba; border-radius: 12px; text-align: left;">
        <div style="display: flex; align-items: center; gap: 8px; margin-bottom: 12px;">
            <span style="font-size: 1.4em;">💰</span>
            <h4 style="margin: 0; color: #856404; font-size: 1.1em;">행운의 번호와 함께 기운을 높여줄 재물복 아이템</h4>
        </div>
        <p style="font-size: 0.85em; color: #856404; margin-bottom: 15px;">추출된 행운의 기운을 집안과 지갑 속에 든든하게 채워줄 인기 풍수 소품입니다.</p>
        
        <div style="display: grid; grid-template-columns: 1fr; gap: 10px;">
            <!-- 상품 1: 해바라기 액자 (대표님 링크 반영) -->
            <a href="https://link.coupang.com/a/g4lMe8DHDE" target="_blank" style="display: flex; align-items: center; gap: 12px; background: #ffffff; padding: 12px; border-radius: 8px; border: 1px solid #fae184; text-decoration: none;">
                <div style="font-size: 1.8em; background: #fff8e1; width: 45px; height: 45px; display: flex; align-items: center; justify-content: center; border-radius: 6px; flex-shrink: 0;">🌻</div>
                <div>
                    <div style="font-size: 0.7em; font-weight: bold; color: #d97706; margin-bottom: 2px;">풍수지리 인테리어</div>
                    <div style="font-size: 0.85em; font-weight: bold; color: #1f2937; margin-bottom: 2px;">재물복 부르는 해바라기 황금 액자</div>
                    <div style="font-size: 0.75em; font-weight: bold; color: #2563eb;">쿠팡 최저가 특가 보러가기 ↗</div>
                </div>
            </a>
            <!-- 상품 2: 행운의 지갑 (대표님 링크 반영) -->
            <a href="https://link.coupang.com/a/g4mrK1xd4m" target="_blank" style="display: flex; align-items: center; gap: 12px; background: #ffffff; padding: 12px; border-radius: 8px; border: 1px solid #fae184; text-decoration: none;">
                <div style="font-size: 1.8em; background: #fff8e1; width: 45px; height: 45px; display: flex; align-items: center; justify-content: center; border-radius: 6px; flex-shrink: 0;">💼</div>
                <div>
                    <div style="font-size: 0.7em; font-weight: bold; color: #d97706; margin-bottom: 2px;">재물운 상승 아이템</div>
                    <div style="font-size: 0.85em; font-weight: bold; color: #1f2937; margin-bottom: 2px;">자산을 지켜주는 프리미엄 천연 가죽 장지갑</div>
                    <div style="font-size: 0.75em; font-weight: bold; color: #2563eb;">쿠팡 최저가 특가 보러가기 ↗</div>
                </div>
            </a>
        </div>

        <div style="font-size: 0.7em; color: #adb5bd; text-align: center; margin-top: 15px; margin-bottom: 0;">
            "이 포스팅은 쿠팡 파트너스 활동의 일환으로, 이에 따른 일정액의 수수료를 제공받습니다."
        </div>
    </div>
</div>

<!-- 구글 애드센스 광고 영역 -->
<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
</div>

<!-- 🎲 일반 랜덤 뽑기 영역 -->
<div id="random-box" style="text-align: center; margin: 20px 0; padding: 30px; background-color: #ffffff; border: 2px dashed #28a745; border-radius: 15px;">
    <h4 style="margin-top: 0; color: #28a745;">🎲 일반 무작위 번호 뽑기</h4>
    <div id="ball-container" style="display: flex; justify-content: center; gap: 10px; margin: 20px 0; min-height: 60px; flex-wrap: wrap;"></div>
    <button onclick="window.generateLotto()" style="padding: 12px 25px; font-size: 1.1em; background-color: #ffc107; color: #333; border: none; border-radius: 8px; cursor: pointer; font-weight: bold;">빠른 일반 번호 뽑기 🎯</button>
</div>

<!-- 🕒 추첨 기록 영역 -->
<div id="history-box" style="margin-top: 20px; text-align: left; background-color: #f8f9fa; padding: 20px; border-radius: 8px; border: 1px solid #dee2e6; display: none;">
    <h5 style="margin-top: 0; color: #495057; border-bottom: 2px solid #e9ecef; padding-bottom: 10px;">🕒 나의 추첨 기록</h5>
    <div id="history-list" style="max-height: 250px; overflow-y: auto; display: flex; flex-direction: column; gap: 5px;"></div>
</div>

<script>
window.getBallHtml = function(num, size) {
    var bgColor = '#fbc400'; var fontColor = '#333';
    if (num > 10 && num <= 20) bgColor = '#69c8f2';
    else if (num > 20 && num <= 30) bgColor = '#ff7272';
    else if (num > 30 && num <= 40) { bgColor = '#aaa'; fontColor = '#fff'; }
    else if (num > 40 && num <= 45) bgColor = '#b0d840';
    return '<div style="width:' + size + 'px; height:' + size + 'px; line-height:' + size + 'px; border-radius:50%; background-color:' + bgColor + '; color:' + fontColor + '; font-weight:bold; font-size:' + (size > 40 ? '1.3em' : '1em') + '; text-align:center; box-shadow:0 2px 4px rgba(0,0,0,0.2);">' + num + '</div>';
};

window.addHistory = function(numbers, typeStr) {
    var historyBox = document.getElementById('history-box');
    var historyList = document.getElementById('history-list');
    if (!historyBox || !historyList) return;
    historyBox.style.display = 'block';
    
    var historyRow = document.createElement('div');
    historyRow.style.display = 'flex';
    historyRow.style.gap = '8px';
    historyRow.style.padding = '8px 0';
    historyRow.style.borderBottom = '1px dashed #ced4da';
    historyRow.style.alignItems = 'center';
    
    var d = new Date();
    var timeStr = String(d.getHours()).padStart(2, '0') + ':' + String(d.getMinutes()).padStart(2, '0') + ':' + String(d.getSeconds()).padStart(2, '0');
    
    var tagSpan = document.createElement('span');
    tagSpan.innerText = '[' + typeStr + ']';
    tagSpan.style.color = typeStr === '사주' ? '#856404' : '#28a745';
    tagSpan.style.fontWeight = 'bold';
    tagSpan.style.fontSize = '0.9em';
    historyRow.appendChild(tagSpan);

    var timeSpan = document.createElement('span');
    timeSpan.innerText = timeStr;
    timeSpan.style.color = '#868e96';
    timeSpan.style.marginRight = '10px';
    timeSpan.style.fontSize = '0.9em';
    historyRow.appendChild(timeSpan);

    numbers.forEach(function(num) {
        var hBall = document.createElement('div');
        hBall.innerHTML = window.getBallHtml(num, 30);
        historyRow.appendChild(hBall.firstChild);
    });
    historyList.insertBefore(historyRow, historyList.firstChild);
};

window.generateSajuLotto = function() {
    var birthDate = document.getElementById('birthDate').value;
    if(!birthDate) {
        alert('생년월일을 입력해주세요!');
        return;
    }
    
    var sajuBtn = document.getElementById('sajuBtn');
    var timerBox = document.getElementById('saju-timer');
    var resultBalls = document.getElementById('saju-result-balls');
    var fortuneText = document.getElementById('saju-fortune-text');
    var coupangBox = document.getElementById('lotto-coupang-box');
    
    if (sajuBtn) sajuBtn.disabled = true;
    if (timerBox) timerBox.style.display = 'block';
    if (resultBalls) resultBalls.innerHTML = '';
    if (fortuneText) fortuneText.style.display = 'none';
    if (coupangBox) coupangBox.style.display = 'none';
    
    var timeLeft = 5;
    var timeCount = document.getElementById('sTimeCount');
    if (timeCount) timeCount.innerText = timeLeft;
    
    var timer = setInterval(function() {
        timeLeft--;
        if (timeCount) timeCount.innerText = timeLeft;
        
        if (timeLeft <= 0) {
            clearInterval(timer);
            if (timerBox) timerBox.style.display = 'none';
            if (sajuBtn) sajuBtn.disabled = false;
            
            var numbers = [];
            while (numbers.length < 6) {
                var num = Math.floor(Math.random() * 45) + 1;
                if (!numbers.includes(num)) { numbers.push(num); }
            }
            numbers.sort(function(a, b){return a - b;});
            
            if (fortuneText) fortuneText.style.display = 'block';
            
            if (resultBalls) {
                resultBalls.innerHTML = '';
                numbers.forEach(function(num) {
                    var ballWrapper = document.createElement('div');
                    ballWrapper.innerHTML = window.getBallHtml(num, 55);
                    resultBalls.appendChild(ballWrapper.firstChild);
                });
            }
            
            if (coupangBox) coupangBox.style.display = 'block';
            window.addHistory(numbers, '사주');
        }
    }, 1000);
};

window.generateLotto = function() {
    var numbers = [];
    while (numbers.length < 6) {
        var num = Math.floor(Math.random() * 45) + 1;
        if (!numbers.includes(num)) { numbers.push(num); }
    }
    numbers.sort(function(a, b){return a - b;});
    
    var container = document.getElementById('ball-container');
    if (!container) return;
    container.innerHTML = '';
    numbers.forEach(function(num) {
        var ballWrapper = document.createElement('div');
        ballWrapper.innerHTML = window.getBallHtml(num, 55);
        container.appendChild(ballWrapper.firstChild);
    });
    window.addHistory(numbers, '일반');
};
</script>
{% endraw %}
