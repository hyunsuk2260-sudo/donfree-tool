---
title: 무료 로또 번호 생성기
icon: fas fa-ticket-alt
order: 6
layout: page
permalink: /lotto/
---

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 20px; line-height: 1.6; border: 1px solid #e9ecef;">
    <h4 style="margin-top: 0; color: #28a745;">🍀 이번 주 대박 기원 로또 번호 추첨기</h4>
    <p>나의 생년월일을 바탕으로 한 명리학 재물운 분석부터 행운 번호 추출까지 한 번에 확인해 보세요!</p>
    <div style="margin-top: 15px; padding: 15px; background-color: #fff3cd; border-left: 5px solid #ffc107; color: #856404; font-weight: bold; font-size: 0.95em;">
        📢 주의사항: 본 서비스는 재미와 참고용으로 제공되며, 당첨을 보장하지 않습니다. 건전하게 즐겨주세요.
    </div>
</div>

<div style="display: flex; flex-wrap: wrap; gap: 15px; margin-bottom: 30px;">
    <div style="flex: 1; min-width: 250px; background-color: #fff; padding: 15px; border-radius: 8px; border: 1px solid #dee2e6; text-align: center; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
        <h5 style="margin: 0 0 10px 0; color: #495057;">📊 역대 최다 출현 숫자 TOP 7</h5>
        <div style="font-size: 1.2em; font-weight: bold; color: #333; letter-spacing: 2px;">
            <span style="color:#b0d840;">43</span>, <span style="color:#aaa;">34</span>, <span style="color:#ff7272;">27</span>, <span style="color:#69c8f2;">17</span>, <span style="color:#fbc400;">1</span>, <span style="color:#69c8f2;">13</span>, <span style="color:#69c8f2;">12</span>
        </div>
    </div>
    <div style="flex: 1; min-width: 250px; background-color: #fff; padding: 15px; border-radius: 8px; border: 1px solid #dee2e6; text-align: center; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
        <h5 style="margin: 0 0 10px 0; color: #495057;">🏆 전회차 당첨 번호 확인</h5>
        <div style="margin-top: 10px;">
            <a href="https://dhlottery.co.kr/gameResult.do?method=byWin" target="_blank" style="display:inline-block; padding:10px 25px; background-color:#28a745; color:white; text-decoration:none; border-radius:5px; font-weight:bold; font-size:1em; box-shadow: 0 3px 5px rgba(0,0,0,0.2);">공식 사이트에서 바로 확인하기 ↗</a>
        </div>
    </div>
</div>

<!-- 1. 사주 운세 확인 영역 (번호랑 섞이지 않게 분리!) -->
<div id="fortune-box" style="text-align: center; margin: 20px 0; padding: 30px; background-color: #ffffff; border: 2px solid #856404; border-radius: 15px; box-shadow: 0 5px 15px rgba(0,0,0,0.1);">
    <h3 style="margin-top: 0; color: #856404;">🔮 오늘의 재물운 사주 풀이</h3>
    <p style="color: #6c757d; margin-bottom: 20px;">생년월일을 입력하여 오늘의 재물운을 먼저 확인하세요.</p>
    
    <input type="date" id="birthDate" style="padding: 10px; font-size: 1.1em; border: 1px solid #ced4da; border-radius: 5px; margin-bottom: 15px;">
    <br>
    <button onclick="checkFortune()" style="padding: 12px 30px; font-size: 1.1em; background-color: #856404; color: white; border: none; border-radius: 8px; cursor: pointer; font-weight: bold;">재물운 확인하기</button>
    <p style="font-size: 0.85em; color: #adb5bd; margin-top: 15px; margin-bottom: 0;">🔒 입력하신 생년월일은 서버에 절대 저장되지 않습니다.</p>

    <!-- 사주 멘트가 뜨는 곳 -->
    <div id="fortune-result" style="display: none; color: #856404; font-weight: bold; margin-top: 25px; padding: 15px; background-color: #fff3cd; border-radius: 8px; font-size: 1.1em; line-height: 1.5; border: 1px dashed #ffe69c;"></div>
</div>

<!-- 구글 애드센스 (명당자리) -->
<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
</div>

<!-- 2. 맞춤 번호 추첨 영역 (5초 대기) -->
<div id="lotto-box" style="text-align: center; margin: 20px 0; padding: 30px; background-color: #ffffff; border: 2px dashed #28a745; border-radius: 15px;">
    <h3 style="margin-top: 0; color: #28a745;">🎯 사주 기반 행운 번호 추출</h3>
    <p style="color: #6c757d; margin-bottom: 20px;">위에서 확인한 기운을 바탕으로 번호를 추출합니다.</p>
    
    <button id="sajuBtn" onclick="generateSajuLotto()" style="padding: 15px 35px; font-size: 1.2em; background-color: #28a745; color: white; border: none; border-radius: 8px; cursor: pointer; font-weight: bold; box-shadow: 0 4px 6px rgba(0,0,0,0.2);">사주 맞춤 번호 뽑기 🎯</button>

    <div id="saju-timer" style="display: none; text-align: center; color: #dc3545; font-weight: bold; margin-top: 20px; padding: 15px; background-color: #f8d7da; border-radius: 8px;">
        기운을 모아 번호를 추출하는 중입니다... <br><span id="sTimeCount" style="font-size: 1.5em;">5</span>초 후 공개됩니다.
    </div>

    <!-- 로또 공이 뜨는 곳 -->
    <div id="saju-result-balls" style="display: flex; justify-content: center; gap: 10px; margin: 25px 0 10px 0; min-height: 60px; flex-wrap: wrap;"></div>
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
    tagSpan.style.color = '#28a745';
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

// 오직 사주 멘트만 띄우는 함수
function checkFortune() {
    var birthDate = document.getElementById('birthDate').value;
    if(!birthDate) {
        alert('사주 분석을 위해 생년월일을 입력해주세요!');
        return;
    }
    
    var fortunes = [
        "타고난 금전운이 강하게 발복하는 시기입니다. 뜻밖의 횡재수가 있으니 기회를 꽉 잡으세요.",
        "재물운의 흐름은 좋으나 구설수나 충동지출을 조심해야 하는 주간입니다. 소액으로 즐기시는 것을 권합니다.",
        "큰 물이 들어오듯 재물이 모이는 사주입니다. 평소보다 과감한 선택이 좋은 결과를 낳을 수 있습니다.",
        "횡재수보다는 꾸준히 쌓아온 덕이 빛을 발하는 형국입니다. 이번 주는 욕심을 조금 내려놓을 때 오히려 운이 트입니다.",
        "하늘이 돕는 천을귀인의 기운이 엿보이나, 주변 사람과 넉넉히 나누어야 액운을 막을 수 있는 사주입니다.",
        "문서운과 재물운이 함께 뻗치는 흐름입니다. 직관을 믿고 흔들림 없이 나아가보세요.",
        "흙 속에 묻힌 진주가 드디어 빛을 발하는 운세입니다. 하지만 조급함은 금물이니 차분히 때를 기다리세요.",
        "재물이 들어왔다 흩어지기 쉬운 기운이 스쳐갑니다. 큰 기대보다는 소소한 재미로 접근하는 것이 길합니다."
    ];
    
    var dateNum = parseInt(birthDate.replace(/-/g, ''));
    var todayNum = new Date().getDate();
    var pickFortune = fortunes[(dateNum + todayNum) % fortunes.length];
    
    document.getElementById('fortune-result').innerHTML = '📜 ' + pickFortune;
    document.getElementById('fortune-result').style.display = 'block';
}

// 오직 번호만 띄우는 함수 (5초 대기)
function generateSajuLotto() {
    document.getElementById('sajuBtn').disabled = true;
    document.getElementById('saju-timer').style.display = 'block';
    document.getElementById('saju-result-balls').innerHTML = '';
    
    var timeLeft = 5;
    document.getElementById('sTimeCount').innerText = timeLeft;
    
    var timer = setInterval(function() {
        timeLeft--;
        document.getElementById('sTimeCount').innerText = timeLeft;
        
        if (timeLeft <= 0) {
            clearInterval(timer);
            document.getElementById('saju-timer').style.display = 'none';
            document.getElementById('sajuBtn').disabled = false;
            
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
            addHistory(numbers, '사주추천');
        }
    }, 1000);
}
</script>
