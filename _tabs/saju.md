---
title: 종합 운세 & 체질 맞춤 큐레이션
icon: fas fa-star
order: 9
layout: page
permalink: /saju-tool/
---

<style>
.fortune-container {
    max-width: 700px;
    margin: 0 auto;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    color: #333;
}
.fortune-header {
    font-size: 1.4em;
    font-weight: bold;
    margin-bottom: 15px;
}
.tab-menu {
    display: flex;
    border-bottom: 2px solid #e1e4e8;
    margin-bottom: 25px;
    gap: 20px;
}
.tab-btn {
    background: none;
    border: none;
    font-size: 1.1em;
    font-weight: bold;
    padding: 10px 0;
    cursor: pointer;
    color: #666;
    position: relative;
}
.tab-btn.active {
    color: #03c75a;
}
.tab-btn.active::after {
    content: '';
    position: absolute;
    bottom: -2px;
    left: 0;
    width: 100%;
    height: 3px;
    background-color: #03c75a;
}
.input-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
    margin-bottom: 15px;
}
.input-select {
    width: 100%;
    padding: 12px;
    border: 1px solid #d1d5db;
    border-radius: 8px;
    background: #fff;
    font-size: 0.95em;
    box-sizing: border-box;
}
.date-row {
    margin-bottom: 20px;
}
.date-input {
    width: 100%;
    padding: 12px;
    border: 1px solid #d1d5db;
    border-radius: 8px;
    font-size: 0.95em;
    box-sizing: border-box;
}
.submit-btn {
    width: 100%;
    padding: 15px;
    background-color: #03c75a;
    color: white;
    border: none;
    border-radius: 8px;
    font-size: 1.1em;
    font-weight: bold;
    cursor: pointer;
    margin-bottom: 30px;
}
.submit-btn:hover {
    background-color: #02b350;
}
.result-card {
    background: #f8fafc;
    border: 1px solid #e2e8f0;
    border-radius: 12px;
    padding: 25px;
    margin-bottom: 30px;
}
.fortune-content-box {
    line-height: 1.8;
    font-size: 1.05em;
    color: #2d3748;
}
.coupang-box {
    margin-top: 25px;
    padding: 22px;
    background-color: #ffffff;
    border-radius: 10px;
    border: 1.5px dashed #03c75a;
    text-align: center;
}
.coupang-btn {
    display: inline-block;
    padding: 14px 30px;
    background-color: #ff2f6e;
    color: #ffffff;
    text-decoration: none;
    border-radius: 8px;
    font-weight: bold;
    box-shadow: 0 4px 8px rgba(255,47,110,0.3);
}
.ad-box {
    text-align: center;
    margin: 40px 0;
    min-height: 100px;
}
</style>

<div class="fortune-container">
    <div class="fortune-header">운세</div>
    
    <!-- 탭 메뉴 -->
    <div class="tab-menu">
        <button class="tab-btn active" onclick="switchTab('today', this)">오늘운세</button>
        <button class="tab-btn" onclick="switchTab('zodiac', this)">띠별운세</button>
        <button class="tab-btn" onclick="switchTab('constellation', this)">별자리운세</button>
        <button class="tab-btn" onclick="switchTab('fortunecookie', this)">포춘쿠키</button>
    </div>

    <!-- 입력 폼 영역 -->
    <div class="input-grid">
        <select id="gender" class="input-select">
            <option value="M">성별 (남성)</option>
            <option value="F" selected>성별 (여성)</option>
        </select>
        <select id="calendar-type" class="input-select">
            <option value="solar" selected>양력</option>
            <option value="lunar">음력</option>
        </select>
        <select id="birth-time" class="input-select">
            <option value="unknown" selected>태어난시, 모름</option>
            <option value="morning">오전 (00~11시)</option>
            <option value="afternoon">오후 (12~23시)</option>
        </select>
    </div>

    <div class="date-row">
        <input type="date" id="birth-date" value="1987-02-02" class="date-input">
    </div>

    <button type="button" class="submit-btn" id="run-btn">운세 확인하기</button>

    <!-- 결과 출력 영역 -->
    <div id="result-box" class="result-card" style="display:none;">
        <h3 id="res-title" style="margin-top:0; color:#03c75a; font-size:1.3em;"></h3>
        <div id="res-desc" class="fortune-content-box"></div>

        <!-- 오늘운세 전용 체질/쿠팡 추천 영역 -->
        <div id="coupang-section" class="coupang-box" style="display:none;">
            <h4 id="rec-item-title" style="margin-top:0; color:#333;">🌿 부족한 기운 채우기 추천템</h4>
            <p id="rec-item-desc" style="font-size:0.9em; color:#666; margin-bottom:15px;"></p>
            <a id="coupang-link" href="#" target="_blank" class="coupang-btn">내 체질 맞춤상품 보러가기 ↗</a>
            <p style="font-size: 0.75em; color: #888; margin-top: 15px; margin-bottom: 0; line-height: 1.4;">
                이 포스팅은 쿠팡 파트너스 활동의 일환으로, 이에 따른 일정액의 수수료를 제공받습니다.
            </p>
        </div>
    </div>

    <!-- 구글 애드센스 광고 영역 -->
    <div class="ad-box">
        <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
    </div>
</div>

<script>
(function() {
    try {
        if (window.adsbygoogle) {
            (adsbygoogle = window.adsbygoogle || []).push({});
        }
    } catch(e) {}

    let currentTab = 'today';

    window.switchTab = function(tabName, btnElem) {
        currentTab = tabName;
        document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
        btnElem.classList.add('active');

        // 포춘쿠키 탭이면 바로 결과 보여주기 연출
        if (tabName === 'fortunecookie') {
            runFortune('fortunecookie');
        }
    };

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

    const zodiacList = ['쥐띠', '소띠', '호랑이띠', '토끼띠', '용띠', '뱀띠', '말띠', '양띠', '원숭이띠', '닭띠', '개띠', '돼지띠'];
    const zodiacVibes = [
        "오늘은 주변의 협조가 돋보이는 날입니다. 작은 성과에 기뻐하며 내실을 다지세요.",
        "오후 시간대에 중요한 결정이 있다면 한 번 더 점검해 보세요. 무리한 이동은 삼가기.",
        "재물운과 인맥운이 가볍게 상승하는 흐름입니다. 가벼운 안부 연락이 길한 복을 부릅니다.",
        "감정 소모를 줄이고 휴식에 집중하는 것이 유리합니다. 따뜻한 차 한 잔의 여유를 가져보세요."
    ];

    const constellationList = ['양자리', '황소자리', '쌍둥이자리', '게자리', '사자자리', '처녀자리', '천칭자리', '전갈자리', '사수자리', '염소자리', '물병자리', '물고기자리'];
    const cookieMessages = [
        "“작은 변화가 내일의 큰 도약이 됩니다. 오늘 가볍게 산책이나 정리를 시작해보세요.”",
        "“생각치 못한 기분 좋은 소식이 찾아옵니다. 마음의 문을 살짝 열어두세요.”",
        "“오늘은 지갑보다는 마음의 여유를 채우는 날. 따뜻한 음료가 행운을 부릅니다.”",
        "“고민하던 일이 직관적인 선택 하나로 가볍게 풀리게 됩니다.”"
    ];

    function runFortune(modeType) {
        var mode = modeType || currentTab;
        var birthInput = document.getElementById("birth-date");
        var dateVal = birthInput ? birthInput.value : "1987-02-02";
        var dateNums = dateVal.replace(/-/g, '');
        var sum = 0;
        for (var i = 0; i < dateNums.length; i++) {
            sum += parseInt(dateNums[i], 10);
        }

        var resTitle = document.getElementById("res-title");
        var resDesc = document.getElementById("res-desc");
        var coupangSection = document.getElementById("coupang-section");
        var resultBox = document.getElementById("result-box");

        if (mode === 'today') {
            const keys = ['목', '화', '토', '금', '수'];
            var selectedOhaeng = keys[sum % 5];
            var info = ohaengInfo[selectedOhaeng];
            var cLink = coupangLinks[selectedOhaeng];

            resTitle.innerText = "✨ [오늘운세] 타고난 체질 [" + info.name + "] 맞춤 가이드";
            resDesc.innerHTML = `<p>${info.desc}</p><p style="margin-top:15px; color:#4a5568; background:#edf2f7; padding:12px; border-radius:8px;">💡 <strong>오늘의 팁:</strong> 오전 시간대에 가벼운 스트레칭과 수분 섭취로 바이오리듬을 깨워보세요.</p>`;
            
            document.getElementById("rec-item-title").innerText = info.recName;
            document.getElementById("rec-item-desc").innerText = info.recDesc;
            document.getElementById("coupang-link").href = cLink;
            coupangSection.style.display = "block";
        } else if (mode === 'zodiac') {
            var zIdx = sum % zodiacList.length;
            var zVibe = zodiacVibes[sum % zodiacVibes.length];
            resTitle.innerText = "🐾 [띠별운세] 오늘의 기운 흐름";
            resDesc.innerHTML = `<p><strong>선택 생년월일 기준 기운 성향:</strong> 활력 넘치는 하루의 시작점이자 귀인이 스치는 시점입니다.</p><p style="margin-top:10px;">🌟 <strong>오늘의 띠별/종합 총운:</strong> ${zVibe}</p>`;
            coupangSection.style.display = "none";
        } else if (mode === 'constellation') {
            var cIdx = (sum * 3) % constellationList.length;
            resTitle.innerText = "⭐ [별자리운세] 밸런스 큐레이션";
            resDesc.innerHTML = `<p><strong>오늘의 별자리 에너지:</strong> 감성과 이중적 직관이 조화롭게 작용하는 시간입니다.</p><p style="margin-top:10px;">✨ <strong>조언:</strong> 오후 2시~4시 사이 미뤄둔 루틴을 처리하면 효율이 2배로 상승합니다.</p>`;
            coupangSection.style.display = "none";
        } else if (mode === 'fortunecookie') {
            var msg = cookieMessages[sum % cookieMessages.length];
            resTitle.innerText = "🥠 [포춘쿠키] 오늘의 메시지 오픈!";
            resDesc.innerHTML = `<div style="text-align:center; padding:15px; font-size:1.15em; font-weight:bold; color:#03c75a;">${msg}</div>`;
            coupangSection.style.display = "none";
        }

        resultBox.style.display = "block";
        resultBox.scrollIntoView({ behavior: 'smooth' });
    }

    var btn = document.getElementById("run-btn");
    if (btn) {
        btn.addEventListener("click", function() {
            runFortune(currentTab);
        });
    }
})();
</script>
