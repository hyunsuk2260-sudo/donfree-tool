---
layout: page
title: " 돈프리 툴즈에 오신 것을 환영합니다!"
---

<script src="https://cdn.tailwindcss.com"></script>

<style>
#panel-wrapper { display: none !important; }
#core-wrapper, .col-12, .col-lg-11, .col-xl-9 { 
    max-width: 100% !important; 
    flex: 100% !important; 
    padding-right: 0 !important; 
    padding-left: 0 !important; 
}
</style>

<!-- 🔥 상단 쿠팡 배너 -->
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

<!-- 🖥️ PC 화면 분할 (좌측 툴 / 우측 뉴스) -->
<div class="grid grid-cols-1 lg:grid-cols-3 gap-6 mb-8" markdown="0">
    
    <!-- 👈 왼쪽 툴 모음 -->
    <div class="lg:col-span-2">
        <div class="bg-gray-50 p-4 sm:p-5 rounded-2xl shadow-inner h-full">
            <div class="mb-4 text-center sm:text-left sm:pl-2">
                <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-1">무료 웹 툴 모음</h2>
                <p class="text-gray-500 text-xs sm:text-sm">원하시는 기능을 선택해 바로 사용해 보세요.</p>
            </div>
            
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                <a href="/font-tool/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:border-green-500 transition-all group"><div class="text-2xl mb-1 group-hover:scale-110 transition-transform origin-left">🔤</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">트렌디 폰트 다운로더</h3></a>
                <a href="/video/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:border-green-500 transition-all group"><div class="text-2xl mb-1 group-hover:scale-110 transition-transform origin-left">📥</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">비디오 다운로더</h3></a>
                <a href="/saju-tool/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:border-green-500 transition-all group"><div class="text-2xl mb-1 group-hover:scale-110 transition-transform origin-left">🔮</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">사주 오행 체질 & 처방</h3></a>
                <a href="/pdf-tool/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:border-green-500 transition-all group"><div class="text-2xl mb-1 group-hover:scale-110 transition-transform origin-left">📄</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">PDF 통합 및 변환</h3></a>
                <a href="/emoji-tool/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:border-green-500 transition-all group"><div class="text-2xl mb-1 group-hover:scale-110 transition-transform origin-left">✨</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">이지이모지 PRO</h3></a>
                <a href="/lotto/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:border-amber-500 transition-all group"><div class="text-2xl mb-1 group-hover:scale-110 transition-transform origin-left">🎰</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">사주 로또 추출기</h3></a>
                <a href="/tarot/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:border-purple-500 transition-all group"><div class="text-2xl mb-1 group-hover:scale-110 transition-transform origin-left">🔮</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">오늘의 타로</h3></a>
            </div>
        </div>
    </div>

    <!-- 👉 오른쪽 실시간 뉴스 피드 -->
    <div class="lg:col-span-1">
        <div class="bg-white p-4 sm:p-5 rounded-2xl shadow-md border border-gray-200 h-full flex flex-col">
            <div class="flex items-center justify-between mb-3 border-b pb-2">
                <h2 class="text-base font-bold text-gray-800">🔥 실시간 핫이슈</h2>
                <span class="text-[10px] bg-red-100 text-red-600 px-2 py-0.5 rounded-full font-bold animate-pulse">LIVE</span>
            </div>
            <ul id="auto-news-list" class="m-0 p-0 list-none flex-grow">
                <li class="text-gray-500 text-xs py-8 text-center">뉴스를 불러오는 중입니다...</li>
            </ul>
        </div>
    </div>
</div>

<!-- 💰 하단 애드센스 -->
<div style="text-align: center; margin: 30px 0; min-height: 100px;">
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
</div>

{% raw %}
<script>
function renderNewsItems() {
    const list = document.getElementById('auto-news-list');
    if (!list) return;

    // 툴 돈프리 사이트의 절대 주소로 확실하게 지정
    const targetUrl = 'https://tool.donfree.co.kr/assets/news.json?v=' + new Date().getTime();

    fetch(targetUrl)
        .then(res => {
            if (!res.ok) throw new Error("파일 접속 실패 (404)");
            return res.json();
        })
        .then(items => {
            if (items && items.length > 0) {
                list.innerHTML = '';
                items.forEach(item => {
                    list.innerHTML += `<li class="py-2.5 border-b border-gray-100 last:border-0"><a href="${item.link}" target="_blank" class="text-[13px] text-gray-800 hover:text-blue-600 font-medium leading-snug no-underline block line-clamp-2">${item.title}</a></li>`;
                });
            }
        })
        .catch(err => {
            // 원인을 바로 알 수 있도록 에러 메시지 출력
            list.innerHTML = `<li class="text-xs text-red-500 py-8 text-center">에러: ${err.message}</li>`;
        });
}

// 딜레이 없이 스크립트 강제 즉시 실행
renderNewsItems();
setTimeout(renderNewsItems, 500);
</script>
{% endraw %}
