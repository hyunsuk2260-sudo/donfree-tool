---
title: 사주 오행 체질 & 맞춤 처방 툴
icon: fas fa-fire
order: 9
layout: page
permalink: /saju-tool/
---

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 25px; border: 1px solid #e9ecef;">
    <h4 style="margin-top: 0; color: #d63384;">🔮 AI 사주 오행 & 체질 맞춤 큐레이션</h4>
    <p style="margin-bottom: 0;">생년월일을 입력하시면 타고난 오행 기운을 분석하여 부족한 기운을 채워줄 맞춤 솔루션을 제안해 드립니다.</p>
</div>

<div style="margin-bottom: 30px; padding: 25px; background-color: #ffffff; border: 2px solid #d63384; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 style="margin-top: 0; color: #d63384;">생년월일 및 성별 입력</h3>
    
    <div style="display: grid; grid-template-columns: 1fr; gap: 15px; margin: 15px 0;">
        <div>
            <label style="display:block; font-weight:bold; margin-bottom:5px; font-size:0.9em; color:#495057;">생년월일 (예: 1987-02-02)</label>
            <input type="date" id="birth-date" value="1987-02-02" style="padding: 10px; border: 1px solid #ccc; border-radius: 6px; width: 100%; box-sizing: border-box;">
        </div>
        <div>
            <label style="display:block; font-weight:bold; margin-bottom:5px; font-size:0.9em; color:#495057;">성별</label>
            <select id="gender" style="padding: 10px; border: 1px solid #ccc; border-radius: 6px; width: 100%; box-sizing: border-box;">
                <option value="F">여성 (Female)</option>
                <option value="M">남성 (Male)</option>
            </select>
        </div>
    </div>
    
    <button type="button" id="saju-submit-btn" style="padding: 12px 25px; background-color:#d63384; color:white; border:none; border-radius:6px; font-weight:bold; cursor:pointer; font-size: 1em; box-shadow: 0 2px 4px rgba(0,0,0,0.2); width: 100%;">내 체질 및 맞춤 처방 확인하기 ✨</button>
</div>

<div id="result-box" style="display:none; margin-bottom: 30px; padding: 25px; background-color: #fff8f9; border: 2px solid #ff85a1; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 id="res-title" style="margin-top: 0; color: #d63384;">분석 결과</h3>
    <p id="res-desc" style="color: #495057; line-height: 1.8; font-size: 1em;"></p>
    
    <div style="margin-top: 25px; padding: 20px; background-color: #ffffff; border-radius: 8px; border: 1px dashed #d63384; text-align: center;">
        <h4 id="rec-item-title" style="margin-top: 0; color: #333;">🌿 부족한 기운 채우기 추천템</h4>
        <p id="rec-item-desc" style="font-size: 0.9em; color: #666; margin-bottom: 15px;"></p>
        <a id="coupang-link" href="#" target="_blank" style="display:inline-block; padding: 14px 30px; background-color: #ff2f6e; color: #ffffff; text-decoration: none; border-radius: 8px; font-weight: bold; box-shadow: 0 4px 8px rgba(255,47,110,0.3);">내 체질 맞춤상품 보러가기 ↗</a>
        <!-- 공정위 문구 추가 -->
        <p style="font-size: 0.75em; color: #888; margin-top: 15px; margin-bottom: 0; line-height: 1.4;">
            이 포스팅은 쿠팡 파트너스 활동의 일환으로, 이에 따른 일정액의 수수료를 제공받습니다.
        </p>
    </div>
</div>

<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
</div>

<script>
(function() {
    try {
        if (window.adsbygoogle) {
            (adsbygoogle = window.adsbygoogle || []).push({});
        }
    } catch(e) {}

    const coupangLinks = {
        '목': 'https://link.coupang.com/a/g3rA2pUvK0',
        '화': 'https://link.coupang.com/a/g3rGUgf4Ue',
        '토': 'https://link.coupang.com/a/g3rPsoqhqK',
        '금': 'https://link.coupang.com/a/g3rUEbkg5A',
        '수': 'https://link.coupang.com/a/g3r7BtHQrY'
    };

    const ohaengInfo = {
        '목': { name: '목(木 - 성장·해독의 기운)', desc: '생각이 많고 추진력이 좋으나, 스트레스로 인해 눈이 쉽게 피로하고 긴장성 피로가 쌓이기 쉬운 체질입니다. 신선한 클렌즈·해독 성분으로 순환을 틔워줘야 합니다.', recName: '🌿 그린 디톡스/클렌즈 주스류', recDesc: '몸속 답답한 열기를 정돈하고 가벼운 활력을 채워줄 초록빛 해독 푸드' },
        '화': { name: '화(火 - 열정·활력의 기운)', desc: '행동력이 빠르고 열정이 넘치나, 에너지 소모가 커서 오후가 되면 체력 방전이 오고 속이 냉해지기 쉬운 체질입니다. 따뜻한 성질로 기력을 보강해야 합니다.', recName: '🔥 온기 충전 홍삼정 / 생강·대추차', recDesc: '떨어진 체온과 에너지를 속 깊이 데워줄 온열 활력 보조 식품' },
        '토': { name: '토(土 - 안정·위장의 기운)', desc: '중심을 잘 잡고 포용력이 있으나, 예민하거나 소화기가 약해지면 더부룩함과 가스가 쉽게 차는 체질입니다. 위장을 편안하게 보호하는 밸런스가 필요합니다.', recName: '🌾 위장 보호 양배추즙 / 유산균', recDesc: '예민해진 위장 장벽을 부드럽게 다스려 줄 베이직 케어 템' },
        '금': { name: '금(金 - 결단·호흡의 기운)', desc: '기준이 확실하고 깔끔하지만, 환절기나 건조할 때 기관지·호흡기 면역계가 예민해지기 쉬운 체질입니다. 폐와 호흡기 보호 관리가 핵심입니다.', recName: '🍐 호흡기 보호 도라지배즙 / 프로폴리스', recDesc: '건조하고 예민한 호흡기와 면역 밸런스를 든든하게 지켜줄 즙' },
        '수': { name: '수(水 - 순환·저력의 기운)', desc: '깊은 통찰력과 지구력이 있으나, 체내 수분 순환이 정체되거나 아침에 잘 붓고 하체가 무거워지기 쉬운 체질입니다. 깊은 혈행 순환이 보약입니다.', recName: '🖤 블랙푸드(서리태) 선식 / 혈행 개선 템', recDesc: '신장·순환 에너지를 묵직하게 채워줄 블랙 에너지 푸드' }
    };

    function runAnalysis() {
        var birthInput = document.getElementById("birth-date");
        if (!birthInput || !birthInput.value) {
            alert("생년월일을 선택해 주세요!");
            return;
        }

        var dateNums = birthInput.value.replace(/-/g, '');
        var sum = 0;
        for (var i = 0; i < dateNums.length; i++) {
            sum += parseInt(dateNums[i], 10);
        }
        
        const keys = ['목', '화', '토', '금', '수'];
        var selectedOhaeng = keys[sum % 5];
        
        var info = ohaengInfo[selectedOhaeng];
        var cLink = coupangLinks[selectedOhaeng];

        document.getElementById("res-title").innerText = "✨ 분석 완료: 당신의 타고난 체질은 [" + info.name + "] 입니다";
        document.getElementById("res-desc").innerText = info.desc;
        document.getElementById("rec-item-title").innerText = info.recName;
        document.getElementById("rec-item-desc").innerText = info.recDesc;
        document.getElementById("coupang-link").href = cLink;

        var resultBox = document.getElementById("result-box");
        resultBox.style.display = "block";
        resultBox.scrollIntoView({ behavior: 'smooth' });
    }

    var btn = document.getElementById("saju-submit-btn");
    if (btn) {
        btn.addEventListener("click", runAnalysis);
    }
})();
</script>
