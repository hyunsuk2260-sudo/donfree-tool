---
title: 사주 오행 체질 & 맞춤 처방 툴
icon: fas fa-fire
order: 9
layout: page
permalink: /saju-tool/
---

<!-- 상단 탭 메뉴 영역 -->
<div id="tab-menu-wrapper" style="display: flex; gap: 10px; margin-bottom: 20px; border-bottom: 2px solid #e9ecef; padding-bottom: 10px;">
    <button type="button" id="btn-tab-today" onclick="window.changeSajuTab('today', this)" style="background:#d63384; color:white; border:none; padding:8px 16px; border-radius:20px; font-weight:bold; cursor:pointer;">오늘운세</button>
    <button type="button" id="btn-tab-zodiac" onclick="window.changeSajuTab('zodiac', this)" style="background:#f8f9fa; color:#495057; border:1px solid #ced4da; padding:8px 16px; border-radius:20px; font-weight:bold; cursor:pointer;">띠별운세</button>
    <button type="button" id="btn-tab-constellation" onclick="window.changeSajuTab('constellation', this)" style="background:#f8f9fa; color:#495057; border:1px solid #ced4da; padding:8px 16px; border-radius:20px; font-weight:bold; cursor:pointer;">별자리운세</button>
    <button type="button" id="btn-tab-cookie" onclick="window.changeSajuTab('cookie', this)" style="background:#f8f9fa; color:#495057; border:1px solid #ced4da; padding:8px 16px; border-radius:20px; font-weight:bold; cursor:pointer;">포춘쿠키</button>
</div>

<!-- 상단 안내 영역 -->
<div id="top-desc-box" style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 25px; border: 1px solid #e9ecef;">
    <h4 id="guide-title" style="margin-top: 0; color: #d63384;">🔮 AI 사주 오행 & 체질 맞춤 큐레이션</h4>
    <p id="guide-desc" style="margin-bottom: 0;">생년월일을 입력하시면 타고난 오행 기운을 분석하여 부족한 기운을 채워줄 맞춤 솔루션을 제안해 드립니다.</p>
</div>

<!-- 입력 폼 영역 -->
<div style="margin-bottom: 30px; padding: 25px; background-color: #ffffff; border: 2px solid #d63384; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 style="margin-top: 0; color: #d63384;">사주 정보 입력</h3>
    
    <div style="display: grid; grid-template-columns: 1fr; gap: 15px; margin: 15px 0;">
        <div>
            <label style="display:block; font-weight:bold; margin-bottom:5px; font-size:0.9em; color:#495057;">생년월일 (예: 1987-02-02)</label>
            <input type="date" id="birth-date" value="1987-02-02" style="padding: 10px; border: 1px solid #ccc; border-radius: 6px; width: 100%; box-sizing: border-box;">
        </div>
        <div style="display:grid; grid-template-columns: 1fr 1fr; gap:10px;">
            <div>
                <label style="display:block; font-weight:bold; margin-bottom:5px; font-size:0.9em; color:#495057;">성별</label>
                <select id="gender" style="padding: 10px; border: 1px solid #ccc; border-radius: 6px; width: 100%; box-sizing: border-box;">
                    <option value="F">여성 (Female)</option>
                    <option value="M">남성 (Male)</option>
                </select>
            </div>
            <div>
                <label style="display:block; font-weight:bold; margin-bottom:5px; font-size:0.9em; color:#495057;">양/음력</label>
                <select id="calendar" style="padding: 10px; border: 1px solid #ccc; border-radius: 6px; width: 100%; box-sizing: border-box;">
                    <option value="solar">양력</option>
                    <option value="lunar">음력</option>
                </select>
            </div>
        </div>
        <div>
            <label style="display:block; font-weight:bold; margin-bottom:5px; font-size:0.9em; color:#495057;">태어난 시 (정밀)</label>
            <select id="birth-time" style="padding: 10px; border: 1px solid #ccc; border-radius: 6px; width: 100%; box-sizing: border-box;">
                <option value="unknown">모름 / 선택안함</option>
                <option value="자시">자시 (23:30 ~ 01:29)</option>
                <option value="축시">축시 (01:30 ~ 03:29)</option>
                <option value="인시">인시 (03:30 ~ 05:29)</option>
                <option value="묘시">묘시 (05:30 ~ 07:29)</option>
                <option value="진시">진시 (07:30 ~ 09:29)</option>
                <option value="사시">사시 (09:30 ~ 11:29)</option>
                <option value="오시">오시 (11:30 ~ 13:29)</option>
                <option value="미시">미시 (13:30 ~ 15:29)</option>
                <option value="신시">신시 (15:30 ~ 17:29)</option>
                <option value="유시">유시 (17:30 ~ 19:29)</option>
                <option value="술시">술시 (19:30 ~ 21:29)</option>
                <option value="해시">해시 (21:30 ~ 23:29)</option>
            </select>
        </div>
    </div>
    
    <button type="button" onclick="window.runSajuAnalysis()" style="padding: 12px 25px; background-color:#d63384; color:white; border:none; border-radius:6px; font-weight:bold; cursor:pointer; font-size: 1em; box-shadow: 0 2px 4px rgba(0,0,0,0.2); width: 100%;">운세 및 맞춤 처방 확인하기 ✨</button>
</div>

<!-- 결과 출력 영역 -->
<div id="result-box" style="display:none; margin-bottom: 30px; padding: 25px; background-color: #fff8f9; border: 2px solid #ff85a1; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 id="res-title" style="margin-top: 0; color: #d63384;">분석 결과</h3>
    <div id="res-desc" style="color: #495057; line-height: 1.8; font-size: 1em;"></div>
    
    <div id="coupang-container" style="display:none;">
        <div style="margin-top: 25px; padding: 20px; background-color: #ffffff; border-radius: 8px; border: 1.5px dashed #d63384; text-align: center;">
            <h4 id="rec-item-title" style="margin-top: 0; color: #333;">🌿 부족한 기운 채우기 추천템</h4>
            <p id="rec-item-desc" style="font-size: 0.9em; color: #666; margin-bottom: 15px;"></p>
            <a id="coupang-link" href="#" target="_blank" style="display:inline-block; padding: 14px 30px; background-color: #ff2f6e; color: #ffffff; text-decoration: none; border-radius: 8px; font-weight: bold; box-shadow: 0 4px 8px rgba(255,47,110,0.3);">내 체질 맞춤상품 보러가기 ↗</a>
            <p style="font-size: 0.75em; color: #888; margin-top: 15px; margin-bottom: 0; line-height: 1.4;">
                이 포스팅은 쿠팡 파트너스 활동의 일환으로, 이에 따른 일정액의 수수료를 제공받습니다.
            </p>
        </div>
    </div>
</div>

<!-- 구글 애드센스 광고 영역 -->
<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
</div>

<script>
window.currentSajuTab = 'today';

window.changeSajuTab = function(tabName, btnElem) {
    window.currentSajuTab = tabName;
    ['today', 'zodiac', 'constellation', 'cookie'].forEach(function(t) {
        var b = document.getElementById('btn-tab-' + t);
        if (b) {
            b.style.background = '#f8f9fa';
            b.style.color = '#495057';
            b.style.border = '1px solid #ced4da';
        }
    });
    if (btnElem) {
        btnElem.style.background = '#d63384';
        btnElem.style.color = 'white';
        btnElem.style.border = 'none';
    }

    var gTitle = document.getElementById('guide-title');
    var gDesc = document.getElementById('guide-desc');
    if (tabName === 'today') {
        gTitle.innerText = "🔮 AI 사주 오행 & 체질 맞춤 큐레이션";
        gDesc.innerText = "생년월일을 입력하시면 타고난 오행 기운을 분석하여 부족한 기운을 채워줄 맞춤 솔루션을 제안해 드립니다.";
    } else if (tabName === 'zodiac') {
        gTitle.innerText = "🐾 띠별 오늘 운세";
        gDesc.innerText = "생년월일(연도) 기준 십이지신(띠) 성향과 오늘의 금전·활력 흐름을 확인해 보세요.";
    } else if (tabName === 'constellation') {
        gTitle.innerText = "⭐ 별자리 밸런스 운세";
        gDesc.innerText = "생일 기준 12별자리 에너지 가이드와 집중 타이밍을 체크해 드립니다.";
    } else if (tabName === 'cookie') {
        gTitle.innerText = "🥠 시크릿 포춘쿠키";
        gDesc.innerText = "오늘 나에게 도착한 한 줄 메시지 포춘쿠키를 바로 열어보세요.";
    }
};

window.runSajuAnalysis = function() {
    var birthInput = document.getElementById("birth-date");
    if (!birthInput || !birthInput.value) {
        alert("생년월일을 선택해 주세요!");
        return;
    }

    var valStr = birthInput.value;
    var parts = valStr.split('-');
    var year = parseInt(parts[0], 10);
    var month = parseInt(parts[1], 10);
    var day = parseInt(parts[2], 10);

    var dateNums = valStr.replace(/-/g, '');
    var sum = 0;
    for (var i = 0; i < dateNums.length; i++) {
        sum += parseInt(dateNums[i], 10);
    }

    var birthTimeVal = document.getElementById("birth-time").value;
    var timeNote = birthTimeVal !== 'unknown' ? " (태어난 시: " + birthTimeVal + ")" : '';

    var coupangLinks = {
        '목': 'https://link.coupang.com/a/g3rA2pUvK0',
        '화': 'https://link.coupang.com/a/g3rGUgf4Ue',
        '토': 'https://link.coupang.com/a/g3rPsoqhqK',
        '금': 'https://link.coupang.com/a/g3rUEbkg5A',
        '수': 'https://link.coupang.com/a/g3r7BtHQrY'
    };

    var ohaengInfo = {
        '목': { name: '목(木 - 성장·해독의 기운)', desc: '생각이 많고 추진력이 좋으나, 스트레스로 인해 눈이 쉽게 피로하고 긴장성 피로가 쌓이기 쉬운 체질입니다. 신선한 클렌즈·해독 성분으로 순환을 틔워줘야 합니다.', recName: '🌿 그린 디톡스/클렌즈 주스류', recDesc: '몸속 답답한 열기를 정돈하고 가벼운 활력을 채워줄 초록빛 해독 푸드' },
        '화': { name: '화(火 - 열정·활력의 기운)', desc: '행동력이 빠르고 열정이 넘치나, 에너지 소모가 커서 오후가 되면 체력 방전이 오고 속이 냉해지기 쉬운 체질입니다. 따뜻한 성질로 기력을 보강해야 합니다.', recName: '🔥 온기 충전 홍삼정 / 생강·대추차', recDesc: '떨어진 체온과 에너지를 속 깊이 데워줄 온열 활력 보조 식품' },
        '토': { name: '토(土 - 안정·위장의 기운)', desc: '중심을 잘 잡고 포용력이 있으나, 예민하거나 소화기가 약해지면 더부룩함과 가스가 쉽게 차는 체질입니다. 위장을 편안하게 보호하는 밸런스가 필요합니다.', recName: '🌾 위장 보호 양배추즙 / 유산균', recDesc: '예민해진 위장 장벽을 부드럽게 다스려 줄 베이직 케어 템' },
        '금': { name: '금(金 - 결단·호흡의 기운)', desc: '기준이 확실하고 깔끔하지만, 환절기나 건조할 때 기관지·호흡기 면역계가 예민해지기 쉬운 체질입니다. 폐와 호흡기 보호 관리가 핵심입니다.', recName: '🍐 호흡기 보호 도라지배즙 / 프로폴리스', recDesc: '건조하고 예민한 호흡기와 면역 밸런스를 든든하게 지켜줄 즙' },
        '수': { name: '수(水 - 순환·저력의 기운)', desc: '깊은 통찰력과 지구력이 있으나, 체내 수분 순환이 정체되거나 아침에 잘 붓고 하체가 무거워지기 쉬운 체질입니다. 깊은 혈행 순환이 보약입니다.', recName: '🖤 블랙푸드(서리태) 선식 / 혈행 개선 템', recDesc: '신장·순환 에너지를 묵직하게 채워줄 블랙 에너지 푸드' }
    };

    function getAccurateZodiac(y) {
        var idx = ((y - 4) % 12 + 12) % 12;
        var names = ['쥐띠', '소띠', '호랑이띠', '토끼띠', '용띠', '뱀띠', '말띠', '양띠', '원숭이띠', '닭띠', '개띠', '돼지띠'];
        return names[idx];
    }

    function getConstellation(m, d) {
        var md = m * 100 + d;
        if (md >= 321 && md <= 419) return '양자리';
        if (md >= 420 && md <= 520) return '황소자리';
        if (md >= 521 && md <= 621) return '쌍둥이자리';
        if (md >= 622 && md <= 722) return '게자리';
        if (md >= 723 && md <= 822) return '사자자리';
        if (md >= 823 && md <= 922) return '처녀자리';
        if (md >= 923 && md <= 1023) return '천칭자리';
        if (md >= 1024 && md <= 1122) return '전갈자리';
        if (md >= 1123 && md <= 1224) return '사수자리';
        if (md >= 1225 || md <= 101) return '염소자리';
        if (md >= 102 && md <= 218) return '물병자리';
        return '물고기자리';
    }

    var cookieMsgs = [
        "“작은 시도가 내일의 커다란 기쁨으로 연결되는 하루입니다.”",
        "“뜻밖의 소중한 인연이나 기분 좋은 연락이 스치는 시점입니다.”",
        "“오늘은 무리한 외출보다 나를 위한 따뜻한 차 한 잔이 길한 복을 부릅니다.”",
        "“고민하던 갈림길에서 직관적인 선택이 100점짜리 정답이 됩니다.”"
    ];

    var resTitle = document.getElementById("res-title");
    var resDesc = document.getElementById("res-desc");
    var coupangContainer = document.getElementById("coupang-container");
    var resultBox = document.getElementById("result-box");

    if (window.currentSajuTab === 'today') {
        var keys = ['목', '화', '토', '금', '수'];
        var selectedOhaeng = keys[sum % 5];
        var info = ohaengInfo[selectedOhaeng];
        var cLink = coupangLinks[selectedOhaeng];

        resTitle.innerText = "✨ [오늘운세] 타고난 체질 [" + info.name + "]" + timeNote;
        resDesc.innerText = info.desc;
        document.getElementById("rec-item-title").innerText = info.recName;
        document.getElementById("rec-item-desc").innerText = info.recDesc;
        document.getElementById("coupang-link").href = cLink;
        coupangContainer.style.display = "block";
    } else if (window.currentSajuTab === 'zodiac') {
        var myZodiac = getAccurateZodiac(year);
        resTitle.innerText = "🐾 [띠별운세] " + year + "년생 " + myZodiac + timeNote;
        resDesc.innerText = "선택하신 생년월일(" + year + "년) 기준 " + myZodiac.replace('띠','') + " 기운 흐름: 주변의 협조가 돋보이며, 오후 시간대 실속 있는 성과가 기대되는 활력형 일일 운세입니다.";
        coupangContainer.style.display = "none";
    } else if (window.currentSajuTab === 'constellation') {
        var myConstellation = getConstellation(month, day);
        resTitle.innerText = "⭐ [별자리운세] " + month + "월 " + day + "일생 (" + myConstellation + ")";
        resDesc.innerText = "오늘의 " + myConstellation + " 에너지: 감성과 직관의 밸런스가 최고조에 달하는 시간입니다. 미뤄둔 일정을 가볍게 정리해 보세요.";
        coupangContainer.style.display = "none";
    } else if (window.currentSajuTab === 'cookie') {
        var cMsg = cookieMsgs[sum % cookieMsgs.length];
        resTitle.innerText = "🥠 [포춘쿠키] 오픈 완료!";
        resDesc.innerHTML = '<div style="text-align:center; padding:15px; font-weight:bold; color:#d63384; font-size:1.1em;">' + cMsg + '</div>';
        coupangContainer.style.display = "none";
    }

    resultBox.style.display = "block";
    resultBox.scrollIntoView({ behavior: 'smooth' });

    try {
        if (window.adsbygoogle) {
            (adsbygoogle = window.adsbygoogle || []).push({});
        }
    } catch(e) {}
};
  <!-- 구글 애드센스 광고 영역 -->
<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <!-- 이 스크립트가 있어야 광고가 정상적으로 뜹니다 -->
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
</script>
