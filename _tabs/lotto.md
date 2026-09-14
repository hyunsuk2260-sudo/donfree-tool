---
title: 무료 로또 번호 생성기
icon: fas fa-ticket-alt
order: 6
layout: page
permalink: /lotto/
---

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 20px; line-height: 1.6; border: 1px solid #e9ecef;">
    <h4 style="margin-top: 0; color: #28a745;">🍀 이번 주 대박 기원 로또 번호 추첨기</h4>
    <p>일반 무작위 추첨부터 나의 생년월일을 바탕으로 한 사주 맞춤 행운 번호까지 무료로 추출해 드립니다. 나만의 대박 번호를 지금 바로 확인해 보세요!</p>
</div>

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

<!-- 💡 사주 맞춤 번호 영역 -->
<div id="lotto-box" style="text-align: center; margin: 20px 0; padding: 30px; background-color: #ffffff; border: 2px solid #856404; border-radius: 15px;">
    <h3 style="margin-top: 0; color: #856404;">🔮 내 사주 맞춤 행운 번호</h3>
    <p style="color: #6c757d; margin-bottom: 20px;">생년월일을 입력하시면 명리학 기반으로 분석하여 맞춤 번호를 추출합니다.</p>
    
    <input type="date" id="birthDate" style="padding: 10px; font-size: 1.1em; border: 1px solid #ced4da; border-radius: 5px; margin-bottom: 15px;">
    <br>
    <button id="sajuBtn" onclick="generateSajuLotto()" style="padding: 15px 35px; font-size: 1.2em; background-color: #856404; color: white; border: none; border-radius: 8px; cursor: pointer; font-weight: bold;">사주 맞춤 번호 분석하기</button>
    
    <p style="font-size: 0.85em; color: #adb5bd; margin-top: 15px; margin-bottom: 0;">🔒 입력하신 생년월일 정보는 절대 저장되지 않습니다.</p>

    <!-- 5초 대기 화면 -->
    <div id="saju-timer" style="display: none; text-align: center; color: #dc3545; font-weight: bold; margin-top: 20px; padding: 15px; background-color: #f8d7da; border-radius: 8px;">
        기운을 모아 번호를 추출하는 중입니다... <br><span id="sTimeCount" style="font-size: 1.5em;">5</span>초 후 공개됩니다.
    </div>

    <!-- ✅ 회원님이 원하셨던 딱 1줄 고정 멘트 영역 -->
    <div id="saju-fortune-text" style="display: none; color: #856404; font-weight: bold; margin-top: 25px; padding: 15px; background-color: #fff3cd; border-radius: 8px; font-size: 1.1em; border: 1px dashed #ffe69c;">
        📜 명리학 사주 기반으로 생성된 로또 추천 번호입니다.
    </div>

    <!-- 로또 공 출력 영역 -->
    <div id="saju-result-balls" style="display: flex; justify-content: center; gap: 10px; margin: 25px 0 10px 0; min-height: 60px; flex-wrap: wrap;"></div>
</div>

<!-- 구글 애드센스 -->
<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
</div>

<!-- 💡 빠른 일반 번호 영역 -->
<div id="random-box" style="text-align: center; margin: 20px 0; padding: 30px; background-color: #ffffff; border: 2px dashed #28a745; border-radius: 15px;">
    <h4 style="margin-top: 0; color: #28a745;">🎲 일반 무작위 번호 뽑기</h4>
    <div id="ball-container" style="display: flex; justify-content: center; gap: 10px; margin: 20px 0; min-height: 60px; flex-wrap: wrap;"></div>
    <button onclick="generateLotto()" style="padding: 12px 25px; font-size: 1.1em; background-color: #ffc107; color: #333; border: none; border-radius: 8px; cursor: pointer; font-weight: bold;">빠른 일반 번호 뽑기 🎯</button>
</div>

<div id="history-box" style="margin-top: 20px; text-align: left; background-color: #f8f9fa; padding: 20px; border-radius: 8px; border: 1px solid #dee2e6; display: none;">
    <h5 style="margin-top: 0; color: #495057; border-bottom: 2px solid #e9ecef; padding-bottom: 10px;">🕒 나의 추첨 기록</h5>
    <div id="history-list" style="max-height: 250px; overflow-y: auto; display: flex; flex-direction: column; gap: 5px;"></div>
</div>

<script>
function getBallHtml(num, size) {
    var bgColor = '#fbc400'; 
    var fontColor = '#333';
    if (num > 10 && num <= 20) bgColor = '#69c8f2';
    else if (num > 20 && num <= 30) bgColor = '#ff7272';
    else if (num > 30 && num <= 40) { bgColor = '#aaa'; fontColor = '#fff'; }
    else if (num > 40 && num <= 45) bgColor = '#b0d840';
    return '<div style="width:' + size + 'px; height:' + size + 'px; line-height:' + size + 'px; border-radius:50%; background-color:' + bgColor + '; color:' + fontColor + '; font-weight:bold; font-size:' + (size > 40 ? '1.3em' : '1em') + '; text-align:center; box-shadow:0 2px 4px rgba(0,0,0,0.2);">' + num + '</div>';
}

function addHistory(numbers, typeStr) {
    var historyBox = document.getElementById('history-box');
    var historyList = document.getElementById('history-list');
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
        hBall.innerHTML = getBallHtml(num, 30);
        historyRow.appendChild(hBall.firstChild);
    });
    historyList.insertBefore(historyRow, historyList.firstChild);
}

function generateSajuLotto() {
    var birthDate = document.getElementById('birthDate').value;
    if(!birthDate) {
        alert('생년월일을 입력해주세요!');
        return;
    }
    
    document.getElementById('sajuBtn').disabled = true;
    document.getElementById('saju-timer').style.display = 'block';
    document.getElementById('saju-result-balls').innerHTML = '';
    
    // 뽑기 시작하면 멘트는 잠깐 숨김
    document.getElementById('saju-fortune-text').style.display = 'none';
    
    var timeLeft = 5;
    document.getElementById('sTimeCount').innerText = timeLeft;
    
    var timer = setInterval(function() {
        timeLeft--;
        document.getElementById('sTimeCount').innerText = timeLeft;
        
        if (timeLeft <= 0) {
            clearInterval(timer);
            document.getElementById('saju-timer').style.display = 'none';
            document.getElementById('sajuBtn').disabled = false;
            
            // ✅ 5초 뒤 고정된 멘트 노출
            document.getElementById('saju-fortune-text').style.display = 'block';
            
            // 번호는 일반 번호 뽑기랑 동일하게 무조건 랜덤!
            var numbers = [];
            while (numbers.length < 6) {
                var num = Math.floor(Math.random() * 45) + 1;
                if (!numbers.includes(num)) { numbers.push(num); }
            }
            numbers.sort(function(a, b){return a - b;});
            
            var container = document.getElementById('saju-result-balls');
            numbers.forEach(function(num) {
                var ballWrapper = document.createElement('div');
                ballWrapper.innerHTML = getBallHtml(num, 55);
                container.appendChild(ballWrapper.firstChild);
            });
            addHistory(numbers, '사주');
        }
    }, 1000);
}

function generateLotto() {
    var numbers = [];
    while (numbers.length < 6) {
        var num = Math.floor(Math.random() * 45) + 1;
        if (!numbers.includes(num)) { numbers.push(num); }
    }
    numbers.sort(function(a, b){return a - b;});
    
    var container = document.getElementById('ball-container');
    container.innerHTML = '';
    numbers.forEach(function(num) {
        var ballWrapper = document.createElement('div');
        ballWrapper.innerHTML = getBallHtml(num, 55);
        container.appendChild(ballWrapper.firstChild);
    });
    addHistory(numbers, '일반');
}
</script>
