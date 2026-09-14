---
title: 무료 로또 번호 생성기
icon: fas fa-ticket-alt
order: 6
layout: page
permalink: /lotto/
---

<!-- SEO 및 애드센스 승인을 위한 안내 텍스트 -->
<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 20px; line-height: 1.6; border: 1px solid #e9ecef;">
    <h4 style="margin-top: 0; color: #28a745;">🍀 이번 주 대박 기원 로또 번호 추첨기</h4>
    <p>난수 발생 알고리즘을 활용하여 이번 주 행운의 로또 6/45 예상 번호를 무료로 추출해 드립니다. 가장 빠르고 직관적으로 나만의 행운 번호를 만들어보세요.</p>
</div>

<!-- 통계 및 이전 회차 자동 불러오기 영역 -->
<div style="display: flex; flex-wrap: wrap; gap: 15px; margin-bottom: 30px;">
    <!-- 역대 최다 출현 번호 -->
    <div style="flex: 1; min-width: 250px; background-color: #fff3cd; padding: 15px; border-radius: 8px; border: 1px solid #ffe69c; text-align: center;">
        <h5 style="margin: 0 0 10px 0; color: #856404;">📊 역대 가장 많이 나온 숫자 TOP 7</h5>
        <div style="font-size: 1.2em; font-weight: bold; color: #333; letter-spacing: 2px;">
            <span style="color:#b0d840;">43</span>, <span style="color:#aaa;">34</span>, <span style="color:#ff7272;">27</span>, <span style="color:#69c8f2;">17</span>, <span style="color:#fbc400;">1</span>, <span style="color:#69c8f2;">13</span>, <span style="color:#69c8f2;">12</span>
        </div>
    </div>
    
    <!-- 최신 당첨 번호 (자동 업데이트) -->
    <div style="flex: 1; min-width: 250px; background-color: #d1ecf1; padding: 15px; border-radius: 8px; border: 1px solid #bee5eb; text-align: center;">
        <h5 style="margin: 0 0 10px 0; color: #0c5460;" id="last-round-title">🏆 전회차 당첨 번호 불러오는 중...</h5>
        <div id="last-round-balls" style="display: flex; justify-content: center; gap: 5px; flex-wrap: wrap; margin-bottom: 5px;"></div>
        <div style="font-size: 0.9em; font-weight: bold; color: #0c5460;" id="last-round-bonus"></div>
    </div>
</div>

<!-- 로또 추출기 본체 -->
<div id="lotto-box" style="text-align: center; margin: 40px 0; padding: 30px; background-color: #ffffff; border: 2px dashed #28a745; border-radius: 15px;">
    <div id="ball-container" style="display: flex; justify-content: center; gap: 10px; margin: 20px 0; min-height: 60px; flex-wrap: wrap;">
        <span style="color: gray; font-size: 1.1em;">버튼을 눌러 번호를 생성해 주세요.</span>
    </div>
    <button onclick="generateLotto()" style="padding: 15px 35px; font-size: 1.2em; background-color: #ffc107; color: #333; border: none; border-radius: 8px; cursor: pointer; font-weight: bold; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">행운의 번호 뽑기 🎯</button>
</div>

<!-- 구글 애드센스 디스플레이 광고 시작 -->
<div style="text-align: center; margin: 30px 0; min-height: 100px;">
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
    <ins class="adsbygoogle"
         style="display:block"
         data-ad-client="ca-pub-1922344740086878"
         data-ad-slot="6535711038"
         data-ad-format="auto"
         data-full-width-responsive="true"></ins>
    <script>
         (adsbygoogle = window.adsbygoogle || []).push({});
    </script>
</div>
<!-- 구글 애드센스 디스플레이 광고 끝 -->

<script>
function getBallHtml(num, size) {
    let bgColor = '#fbc400'; 
    let fontColor = '#333';
    if (num > 10 && num <= 20) bgColor = '#69c8f2';
    else if (num > 20 && num <= 30) bgColor = '#ff7272';
    else if (num > 30 && num <= 40) { bgColor = '#aaa'; fontColor = '#fff'; }
    else if (num > 40 && num <= 45) bgColor = '#b0d840';
    
    return '<div style="width:' + size + 'px; height:' + size + 'px; line-height:' + size + 'px; border-radius:50%; background-color:' + bgColor + '; color:' + fontColor + '; font-weight:bold; font-size:' + (size > 40 ? '1.3em' : '1em') + '; text-align:center; box-shadow:0 2px 4px rgba(0,0,0,0.2);">' + num + '</div>';
}

function generateLotto() {
    const numbers = [];
    while (numbers.length < 6) {
        const num = Math.floor(Math.random() * 45) + 1;
        if (!numbers.includes(num)) { numbers.push(num); }
    }
    numbers.sort((a, b) => a - b);
    
    const container = document.getElementById('ball-container');
    container.innerHTML = '';
    
    numbers.forEach(num => {
        const ballWrapper = document.createElement('div');
        ballWrapper.innerHTML = getBallHtml(num, 55);
        container.appendChild(ballWrapper.firstChild);
    });
}

async function loadLatestDraw() {
    const firstDraw = new Date("2002-12-07T20:45:00").getTime();
    const now = new Date().getTime();
    const currentRound = Math.floor((now - firstDraw) / (1000 * 60 * 60 * 24 * 7)) + 1;
    const lastRound = currentRound - 1;
    
    try {
        const targetUrl = 'https://www.dhlottery.co.kr/common.do?method=getLottoNumber&drwNo=' + lastRound;
        const proxyUrl = 'https://api.allorigins.win/get?url=' + encodeURIComponent(targetUrl);
        
        const response = await fetch(proxyUrl);
        const json = await response.json();
        const data = JSON.parse(json.contents);
        
        if (data.returnValue === 'success') {
            document.getElementById('last-round-title').innerText = '🏆 ' + lastRound + '회차 당첨 번호';
            
            const nums = [data.drwtNo1, data.drwtNo2, data.drwtNo3, data.drwtNo4, data.drwtNo5, data.drwtNo6];
            const ballHtml = nums.map(n => getBallHtml(n, 35)).join('');
            document.getElementById('last-round-balls').innerHTML = ballHtml;
            
            document.getElementById('last-round-bonus').innerHTML = '+ 보너스 ' + getBallHtml(data.bnusNo, 30);
            document.getElementById('last-round-bonus').style.display = 'flex';
            document.getElementById('last-round-bonus').style.alignItems = 'center';
            document.getElementById('last-round-bonus').style.justifyContent = 'center';
            document.getElementById('last-round-bonus').style.gap = '5px';
        } else {
            document.getElementById('last-round-title').innerText = '🏆 최신 당첨 번호';
        }
    } catch (e) {
        document.getElementById('last-round-title').innerText = '🏆 최신 당첨 번호 (불러오기 지연)';
    }
}

window.onload = loadLatestDraw;
</script>
