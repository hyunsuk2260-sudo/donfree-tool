---
title: 트렌디 폰트 툴
icon: fas fa-font
order: 11
layout: page
permalink: /font-tool/
---

{% raw %}
<style>
/* 구글 웹폰트 */
@import url('https://fonts.googleapis.com/css2?family=Black+Han+Sans&family=Do+Hyeon&family=Dongle:wght@400;700&family=Gowun+Dodum&family=Jua&family=Noto+Sans+KR:wght@400;700&family=Single+Day&display=swap');
/* 프리텐다드 */
@import url("https://fastly.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.min.css");

/* 눈누 웹폰트 (트렌디 폰트들) */
@font-face { font-family: 'TheJamsil5Bold'; src: url('https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_2302_01@1.0/TheJamsil5Bold.woff2') format('woff2'); font-weight: 700; font-style: normal; }
@font-face { font-family: 'EF_jejudoldam'; src: url('https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_2210-EF@1.0/EF_jejudoldam.woff2') format('woff2'); font-weight: normal; font-style: normal; }
@font-face { font-family: 'yg-jalnan'; src: url('https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_four@1.2/JalnanOTF00.woff') format('woff'); font-weight: normal; font-style: normal; }
@font-face { font-family: 'SBAggroB'; src: url('https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_2108@1.1/SBAggroB.woff') format('woff'); font-weight: normal; font-style: normal; }
@font-face { font-family: 'Cafe24Ssurround'; src: url('https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_2105_2@1.0/Cafe24Ssurround.woff') format('woff'); font-weight: normal; font-style: normal; }
@font-face { font-family: 'CookieRun-Regular'; src: url('https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_2001@1.1/CookieRun-Regular.woff') format('woff'); font-weight: normal; font-style: normal; }
@font-face { font-family: 'GmarketSansMedium'; src: url('https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_2001@1.1/GmarketSansMedium.woff') format('woff'); font-weight: normal; font-style: normal; }
@font-face { font-family: 'TmonMonsori'; src: url('https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_two@1.0/TmonMonsori.woff') format('woff'); font-weight: normal; font-style: normal; }
@font-face { font-family: 'KCC-eunyoung'; src: url('https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_one@1.0/KCC-eunyoung.woff') format('woff'); font-weight: normal; font-style: normal; }
@font-face { font-family: 'ChangwonDangamAsak-Bold'; src: url('https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_2001@1.1/ChangwonDangamAsak-Bold.woff') format('woff'); font-weight: normal; font-style: normal; }
@font-face { font-family: 'Binggrae'; src: url('https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_one@1.0/Binggrae.woff') format('woff'); font-weight: normal; font-style: normal; }
@font-face { font-family: 'ChosunCentennial'; src: url('https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_2206-02@1.0/ChosunCentennial.woff2') format('woff2'); font-weight: normal; font-style: normal; }

/* 폰트 클래스 매핑 */
.font-pretendard { font-family: 'Pretendard', sans-serif; }
.font-jamsil { font-family: 'TheJamsil5Bold', sans-serif; }
.font-jeju { font-family: 'EF_jejudoldam', sans-serif; }
.font-jalnan { font-family: 'yg-jalnan', sans-serif; }
.font-aggro { font-family: 'SBAggroB', sans-serif; }
.font-cafe24 { font-family: 'Cafe24Ssurround', sans-serif; }
.font-cookierun { font-family: 'CookieRun-Regular', sans-serif; }
.font-gmarket { font-family: 'GmarketSansMedium', sans-serif; }
.font-tmon { font-family: 'TmonMonsori', sans-serif; }
.font-eunyoung { font-family: 'KCC-eunyoung', cursive; }
.font-dangam { font-family: 'ChangwonDangamAsak-Bold', sans-serif; }
.font-binggrae { font-family: 'Binggrae', sans-serif; }
.font-chosun { font-family: 'ChosunCentennial', sans-serif; }
.font-noto { font-family: 'Noto Sans KR', sans-serif; }
.font-dohyeon { font-family: 'Do Hyeon', sans-serif; }
.font-jua { font-family: 'Jua', sans-serif; }
.font-gowun { font-family: 'Gowun Dodum', sans-serif; }
.font-blackhan { font-family: 'Black Han Sans', sans-serif; }
.font-singleday { font-family: 'Single Day', cursive; }
.font-dongle { font-family: 'Dongle', sans-serif; font-size: 1.5em; line-height: 1; }
</style>

<script src="https://cdn.tailwindcss.com"></script>

<div class="bg-gray-50 text-gray-800 flex flex-col selection:bg-purple-200" style="min-height: 80vh;">
    <header class="bg-white border-b border-gray-200 sticky top-0 z-20 shadow-sm rounded-t-xl mt-4">
        <div class="max-w-3xl mx-auto px-4 py-4">
            <div class="flex items-center justify-between mb-3">
                <h1 class="text-lg font-bold text-gray-900 flex items-center gap-1.5" style="margin:0;">
                    <span>✨</span> 인스타/유튜브 트렌디 폰트
                </h1>
                <span class="text-xs text-purple-600 bg-purple-50 px-2 py-1 rounded-full font-bold border border-purple-200">100% 상업용 무료</span>
            </div>
            <input type="text" id="previewInput" value="구독과 좋아요 부탁드립니다!" placeholder="테스트할 문구를 입력해보세요..." 
                class="w-full px-4 py-3 bg-gray-100 rounded-xl text-base focus:outline-none focus:ring-2 focus:ring-purple-500 focus:bg-white transition-all text-center font-bold">
        </div>
    </header>

    <main class="max-w-3xl mx-auto w-full px-4 flex-1 py-6">
        <div id="fontGrid" class="grid grid-cols-1 sm:grid-cols-2 gap-4">
            <!-- 자바스크립트로 폰트 목록이 렌더링됩니다 -->
        </div>
    </main>
</div>

<!-- 하단 구글 애드센스 광고 영역 -->
<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
</div>

<script>
(function() {
    var fontData = [
        { name: '제주돌담체 (감성 릴스 추천)', css: 'font-jeju', url: 'https://noonnu.cc/font_page/1057' },
        { name: '더잠실체 (모던하고 세련된)', css: 'font-jamsil', url: 'https://noonnu.cc/font_page/1138' },
        { name: '여기어때 잘난체 (썸네일 어그로 탑)', css: 'font-jalnan', url: 'https://noonnu.cc/font_page/227' },
        { name: '티몬 몬소리체 (유튜브 자막 1티어)', css: 'font-tmon', url: 'https://noonnu.cc/font_page/208' },
        { name: '프리텐다드 (가장 완벽한 기본 폰트)', css: 'font-pretendard', url: 'https://noonnu.cc/font_page/835' },
        { name: '어그로체 (이름값 하는 독특함)', css: 'font-aggro', url: 'https://noonnu.cc/font_page/739' },
        { name: '카페24 써라운드 (뷰티/브이로그)', css: 'font-cafe24', url: 'https://noonnu.cc/font_page/703' },
        { name: '쿠키런체 (동글동글 귀여운)', css: 'font-cookierun', url: 'https://noonnu.cc/font_page/396' },
        { name: 'G마켓 산스 (신뢰감 주는 고딕)', css: 'font-gmarket', url: 'https://noonnu.cc/font_page/463' },
        { name: 'KCC 은영체 (진짜 손글씨 감성)', css: 'font-eunyoung', url: 'https://noonnu.cc/font_page/197' },
        { name: '창원단감아삭체 (톡톡 튀는 타이틀)', css: 'font-dangam', url: 'https://noonnu.cc/font_page/431' },
        { name: '조선100년체 (진지한 다큐/명조)', css: 'font-chosun', url: 'https://noonnu.cc/font_page/1000' },
        { name: '빙그레체 (따뜻하고 포근한)', css: 'font-binggrae', url: 'https://noonnu.cc/font_page/158' },
        { name: '배달의민족 도현체 (레트로 간판 느낌)', css: 'font-dohyeon', url: 'https://fonts.google.com/specimen/Do+Hyeon' },
        { name: '검은고딕 (굵직하고 강렬한)', css: 'font-blackhan', url: 'https://fonts.google.com/specimen/Black+Han+Sans' },
        { name: '배달의민족 주아체 (붓글씨 귀여움)', css: 'font-jua', url: 'https://fonts.google.com/specimen/Jua' },
        { name: '고운 돋움 (잔잔한 브이로그 자막)', css: 'font-gowun', url: 'https://fonts.google.com/specimen/Gowun+Dodum' },
        { name: '싱글데이체 (다이어리 꾸미기)', css: 'font-singleday', url: 'https://fonts.google.com/specimen/Single+Day' },
        { name: '동글체 (작고 앙증맞은)', css: 'font-dongle', url: 'https://fonts.google.com/specimen/Dongle' },
        { name: '노토 산스 KR (구글 기본 고딕)', css: 'font-noto', url: 'https://fonts.google.com/specimen/Noto+Sans+KR' }
    ];

    window.renderFonts = function() {
        var text = document.getElementById('previewInput').value || '테스트 문구를 입력하세요';
        var grid = document.getElementById('fontGrid');
        
        var htmlString = "";
        for (var i = 0; i < fontData.length; i++) {
            var font = fontData[i];
            htmlString += '<div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between hover:border-purple-300 hover:shadow-md transition-all">';
            htmlString += '  <div>';
            htmlString += '    <div class="text-xs text-gray-500 mb-4 font-bold flex justify-between items-center">';
            htmlString += '      <span>' + font.name + '</span>';
            htmlString += '    </div>';
            htmlString += '    <div class="' + font.css + ' text-3xl text-gray-900 break-keep mb-6 overflow-hidden leading-snug" style="min-height: 4.5rem; word-break: keep-all;">' + text + '</div>';
            htmlString += '  </div>';
            htmlString += '  <a href="' + font.url + '" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors shadow-sm">폰트 다운로드 가기</a>';
            htmlString += '</div>';
        }
        grid.innerHTML = htmlString;
    };

    var previewInput = document.getElementById('previewInput');
    if (previewInput) {
        previewInput.addEventListener('input', window.renderFonts);
    }

    // 초기 화면 렌더링
    window.renderFonts();
})();
</script>
{% endraw %}
