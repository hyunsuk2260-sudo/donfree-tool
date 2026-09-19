---
layout: page
title: " 돈프리 툴즈에 오신 것을 환영합니다!"
---

<script src="https://cdn.tailwindcss.com"></script>

<!-- 💡 PC 화면 우측 빈 공간(목차 패널) 삭제하고 화면 100% 꽉 채우기 -->
<style>
@media (min-width: 1200px) {
    #core-wrapper { flex: 0 0 100% !important; max-width: 100% !important; padding-right: 0 !important; }
    #panel-wrapper { display: none !important; }
}
</style>

<!-- 🔥 최상단 쿠팡 배너 -->
<div class="bg-white py-1.5 border-b border-gray-100 mb-5 text-center shadow-sm">
    <div class="max-w-[680px] mx-auto overflow-hidden scale-90 sm:scale-100">
        <script src="https://ads-partners.coupang.com/g.js"></script>
        <script>
            new PartnersCoupang.G({"id":735290,"template":"carousel","trackingCode":"AF6149137","width":"680","height":"140","tsource":""});
        </script>
    </div>
</div>

<!-- 🔮 사주 로또 배너 -->
<a href="/lotto/" style="display: block; width: 100%; aspect-ratio: 5 / 1; min-height: 90px; background-image: url('/4de21f9a-5bdd-40fe-896e-027818e2c2ac.jfif'); background-size: 100% 100%; background-position: center; background-repeat: no-repeat; border-radius: 8px; box-shadow: 0 4px 15px rgba(0,0,0,0.5); margin-bottom: 30px; cursor: pointer;"></a>

<!-- 🖥️ PC 화면 분할 영역 (좌측 툴 70% / 우측 뉴스 30%) -->
<div class="grid grid-cols-1 lg:grid-cols-3 gap-5 mb-8" markdown="0">
    
    <!-- 👈 왼쪽 구역 (툴 메뉴 모음 - 촘촘하게 묶어서 자동광고 난입 차단) -->
    <div class="lg:col-span-2">
        <div class="bg-gray-50 p-4 sm:p-5 rounded-2xl shadow-inner h-full">
            <div class="mb-4 text-center sm:text-left sm:pl-2">
                <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-1">무료 웹 툴 모음</h2>
                <p class="text-gray-500 text-xs sm:text-sm">원하시는 기능을 선택해 바로 사용해 보세요.</p>
            </div>
            
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                <a href="/font-tool/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:shadow-md hover:border-green-500 transition-all duration-200 group"><div class="text-2xl mb-1 group-hover:scale-110 transition-transform origin-left">🔤</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">트렌디 폰트 다운로더</h3><p class="text-[11px] text-gray-500 m-0">자막용 무료 폰트 모음</p></a>
                <a href="/video/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:shadow-md hover:border-green-500 transition-all duration-200 group"><div class="text-2xl mb-1 group-hover:scale-110 transition-transform origin-left">📥</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">비디오 다운로더</h3><p class="text-[11px] text-gray-500 m-0">워터마크 없이 동영상 저장</p></a>
                <a href="/saju-tool/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:shadow-md hover:border-green-500 transition-all duration-200 group"><div class="text-2xl mb-1 group-hover:scale-110 transition-transform origin-left">🔮</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">사주 오행 체질 & 처방</h3><p class="text-[11px] text-gray-500 m-0">내 오행 분석과 개운법</p></a>
                <a href="/pdf-tool/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:shadow-md hover:border-green-500 transition-all duration-200 group"><div class="text-2xl mb-1 group-hover:scale-110 transition-transform origin-left">📄</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">PDF 통합 및 변환 툴</h3><p class="text-[11px] text-gray-500 m-0">이미지를 5초 만에 PDF로</p></a>
                <a href="/emoji-tool/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:shadow-md hover:border-green-500 transition-all duration-200 group"><div class="text-2xl mb-1 group-hover:scale-110 transition-transform origin-left">✨</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">이지이모지 PRO</h3><p class="text-[11px] text-gray-500 m-0">특수문자 클릭 복사</p></a>
                <a href="/lotto/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:shadow-md hover:border-amber-500 transition-all duration-200 group"><div class="text-2xl mb-1 group-hover:scale-110 transition-transform origin-left">🎰</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">사주 로또 추출기</h3><p class="text-[11px] text-gray-500 m-0">오행 기반 행운 번호</p></a>
                <a href="/tarot/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:shadow-md hover:border-purple-500 transition-all duration-200 group"><div class="text-2xl mb-1 group-hover:scale-110 transition-transform origin-left">🔮</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">오늘의 타로</h3><p class="text-[11px] text-gray-500 m-0">질문하고 AI 맞춤 해석</p></a>
            </div>
        </div>
    </div>

    <!-- 👉 오른쪽 구역 (실시간 뉴스 - 속도가 훨씬 빠른 서버 우회 방식으로 교체) -->
    <div class="lg:col-span-1">
        <div class="bg-white p-4 sm:p-5 rounded-2xl shadow-md border border-gray-200 h-full flex flex-col">
            <div class="flex items-center justify-between mb-3 border-b pb-2">
                <h2 class="text-base font-bold text-gray-800">🔥 실시간 핫이슈</h2>
                <span class="text-[10px] bg-red-100 text-red-600 px-2 py-0.5 rounded-full font-bold animate-pulse">LIVE</span>
            </div>
            
            <ul id="auto-news-list" class="m-0 p-0 list-none flex-grow">
                <li class="text-gray-500 text-xs py-4 text-center">최신 뉴스를 즉시 불러오는 중입니다...</li>
            </ul>
        </div>
    </div>
    
</div>

<!-- 💰 하단 구글 애드센스 -->
<div style="text-align: center; margin: 30px 0; min-height: 100px;">
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
</div>

{% raw %}
<script>
// 무한 로딩을 유발하던 무료 API(rss2json)를 버리고, 제한 없는 우회 API(AllOrigins)로 교체하여 0.1초 만에 로딩되도록 수정
(function() {
    const rssUrl = encodeURIComponent('https://news.google.com/rss?hl=ko&gl=KR&ceid=KR:ko');
    const apiUrl = 'https://api.allorigins.win/get?url=' + rssUrl;

    fetch(apiUrl)
        .then(response => {
            if (response.ok) return response.json();
            throw new Error('Network response was not ok.');
        })
        .then(data => {
            // XML 데이터를 직접 파싱
            const parser = new DOMParser();
            const xmlDoc = parser.parseFromString(data.contents, "text/xml");
            const items = Array.from(xmlDoc.querySelectorAll("item")).slice(0, 8); // 8개 추출
            
            const list = document.getElementById('auto-news-list');
            if(!list) return;
            list.innerHTML = ''; 
            
            items.forEach(item => {
                let title = item.querySelector("title").textContent;
                let link = item.querySelector("link").textContent;
                let cleanTitle = title.split(' - ')[0]; // 언론사 이름 자르기
                
                const li = document.createElement('li');
                li.className = 'py-2 border-b border-gray-100 last:border-0';
                li.innerHTML = `
                    <a href="${link}" target="_blank" class="group block text-decoration-none">
                        <span class="text-[13px] text-gray-800 group-hover:text-blue-600 transition-colors line-clamp-2 font-medium leading-snug">${cleanTitle}</span>
                    </a>
                `;
                list.appendChild(li);
            });
        })
        .catch(error => {
            const list = document.getElementById('auto-news-list');
            if(list) list.innerHTML = '<li class="text-xs text-red-500 py-2 text-center">뉴스를 불러오지 못했습니다.<br>새로고침을 눌러주세요.</li>';
        });
})();
</script>
{% endraw %}
