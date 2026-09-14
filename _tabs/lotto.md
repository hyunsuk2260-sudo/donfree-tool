---
title: 무료 로또 번호 생성기
icon: fas fa-ticket-alt
order: 6
layout: page
permalink: /lotto/
---

<!-- SEO 및 애드센스 승인을 위한 안내 텍스트 -->
<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 30px; line-height: 1.6; border: 1px solid #e9ecef;">
    <h4 style="margin-top: 0; color: #28a745;">🍀 이번 주 대박 기원 로또 번호 추첨기</h4>
    <p>난수 발생 알고리즘을 활용하여 이번 주 행운의 로또 6/45 예상 번호를 무료로 추출해 드립니다. 가장 빠르고 직관적으로 나만의 행운 번호를 만들어보세요.</p>
    
    <h5 style="margin-bottom: 5px;">📌 이용 안내</h5>
    <ul style="margin-top: 0; padding-left: 20px;">
        <li>아래 <b>'행운의 번호 뽑기'</b> 버튼을 누르면 1부터 45까지의 숫자 중 중복 없는 6개의 번호가 무작위로 추첨됩니다.</li>
        <li>마음에 드는 번호 조합이 나올 때까지 횟수 제한 없이 무제한으로 생성할 수 있습니다.</li>
        <li>뽑힌 번호들은 보기 쉽게 오름차순으로 자동 정렬되며, 로또 공식 기준에 맞춰 숫자 대역별로 색상이 다르게 표시됩니다.</li>
    </ul>
    
    <p style="font-size: 0.85em; color: #6c757d; margin-bottom: 0; margin-top: 15px;">
        <i>*본 서비스는 재미와 참고용으로 제공되며, 당첨을 보장하지 않습니다. 과도한 몰입은 삼가시고 건전하게 즐겨주세요.*</i>
    </p>
</div>

<!-- 로또 추출기 본체 -->
<div id="lotto-box" style="text-align: center; margin: 40px 0; padding: 30px; background-color: #ffffff; border: 2px dashed #28a745; border-radius: 15px;">
    <div id="ball-container" style="display: flex; justify-content: center; gap: 10px; margin: 20px 0; min-height: 60px; flex-wrap: wrap;">
        <!-- 번호 공이 들어갈 자리 -->
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
function generateLotto() {
    const numbers = [];
    while (numbers.length < 6) {
        const num = Math.floor(Math.random() * 45) + 1;
        if (!numbers.includes(num)) {
            numbers.push(num);
        }
    }
    
    // 숫자 오름차순 정렬
    numbers.sort((a, b) => a - b);
    
    const container = document.getElementById('ball-container');
    container.innerHTML = '';
    
    numbers.forEach(num => {
        const ball = document.createElement('div');
        ball.innerText = num;
        
        // 실제 로또 공 색상 적용 (노, 파, 빨, 회, 초)
        let bgColor = '#fbc400'; 
        let fontColor = '#333';
        if (num > 10 && num <= 20) bgColor = '#69c8f2';
        else if (num > 20 && num <= 30) bgColor = '#ff7272';
        else if (num > 30 && num <= 40) {
            bgColor = '#aaa';
            fontColor = '#fff';
        }
        else if (num > 40 && num <= 45) bgColor = '#b0d840';
        
        ball.style.width = '55px';
        ball.style.height = '55px';
        ball.style.lineHeight = '55px';
        ball.style.borderRadius = '50%';
        ball.style.backgroundColor = bgColor;
        ball.style.color = fontColor;
        ball.style.fontWeight = 'bold';
        ball.style.fontSize = '1.3em';
        ball.style.boxShadow = '0 2px 4px rgba(0,0,0,0.2)';
        
        container.appendChild(ball);
    });
}
</script>
