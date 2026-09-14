---
title: (수정완료) 무료 로또 생성기
icon: fas fa-ticket-alt
order: 6
layout: page
permalink: /lotto/
---

<!-- 💡 사주 멘트는 버튼과 상관없이 무조건 화면에 고정되어 있습니다! -->
<div style="background-color: #fff3cd; padding: 20px; border-radius: 8px; margin-bottom: 30px; border: 1px solid #ffe69c; text-align: center;">
    <h4 style="margin-top: 0; color: #856404;">🔮 사주명리학 기반 재물운 분석</h4>
    <p style="color: #664d03; font-weight: bold; margin-bottom: 0;">
        "타고난 금전운이 발복하는 시기입니다. 입력하신 생년월일의 기운과 가장 강하게 결합하는 당신만의 행운 번호입니다."
    </p>
</div>

<!-- 맞춤 번호 추첨 영역 (번호만 바뀝니다!) -->
<div id="lotto-box" style="text-align: center; margin: 20px 0; padding: 30px; background-color: #ffffff; border: 2px solid #28a745; border-radius: 15px;">
    <h3 style="margin-top: 0; color: #28a745;">🎯 내 사주 맞춤 번호 추출</h3>
    <p style="color: #6c757d; margin-bottom: 20px;">생년월일을 입력하고 번호를 추출해 보세요.</p>
    
    <input type="date" id="birthDate" style="padding: 10px; font-size: 1.1em; border: 1px solid #ced4da; border-radius: 5px; margin-bottom: 15px;">
    <br>
    <button id="sajuBtn" onclick="generateSajuLotto()" style="padding: 15px 35px; font-size: 1.2em; background-color: #28a745; color: white; border: none; border-radius: 8px; cursor: pointer; font-weight: bold;">행운 번호 뽑기 🎯</button>
    
    <p style="font-size: 0.85em; color: #adb5bd; margin-top: 15px; margin-bottom: 0;">🔒 입력하신 정보는 분석용으로만 사용되며, 절대 저장되지 않습니다.</p>

    <!-- 5초 대기 화면 -->
    <div id="saju-timer" style="display: none; text-align: center; color: #dc3545; font-weight: bold; margin-top: 20px; padding: 15px; background-color: #f8d7da; border-radius: 8px;">
        기운을 모아 번호를 추출하는 중입니다... <br><span id="sTimeCount" style="font-size: 1.5em;">5</span>초 후 공개
    </div>

    <!-- 로또 공 출력 영역 -->
    <div id="saju-result-balls" style="display: flex; justify-content: center; gap: 10px; margin: 25px 0 10px 0; min-height: 60px; flex-wrap: wrap;">
        <span style="color: gray; font-size: 1em;">버튼을 누르면 이곳에 번호가 표시됩니다.</span>
    </div>
</div>

<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
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

function generateSajuLotto() {
    var birthDate = document.getElementById('birthDate').value;
    if(!birthDate) {
        alert('생년월일을 먼저 입력해주세요!');
        return;
    }
    
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
            
            // 💡 번호만! 오직 로또 번호 6개만 새로 뽑습니다.
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
        }
    }, 1000);
}
</script>
