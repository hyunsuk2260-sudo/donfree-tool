---
layout: page
title: " 돈프리 툴즈에 오신 것을 환영합니다!"
---

<script src="https://cdn.tailwindcss.com"></script>

<!-- 💡 PC 우측 빈 공간 날려버리는 Chirpy 테마 전용 저격 코드 -->
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

<!-- 🔮 로또 배너 -->
<a href="/lotto/" style="display: block; width: 100%; aspect-ratio: 5 / 1; min-height: 90px; background-image: url('/4de21f9a-5bdd-40fe-896e-027818e2c2ac.jfif'); background-size: 100% 100%; background-position: center; background-repeat: no-repeat; border-radius: 8px; box-shadow: 0 4px 15px rgba(0,0,0,0.5); margin-bottom: 30px; cursor: pointer;"></a>

<!-- 🖥️ PC 화면 분할 (좌 툴 / 우 뉴스) -->
<div class="grid grid-cols-1 lg:grid-cols-3 gap-6 mb-8">
    
    <!-- 👈 왼쪽 툴 모음 -->
    <div class="lg:col-span-2">
        <div class="bg-gray-50 p-4 sm:p-5 rounded-2xl shadow-inner h-full">
            <div class="mb-4 text-center sm:text-left sm:pl-2">
                <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-1">무료 웹 툴 모음</h2>
                <p class="text-gray-500 text-xs sm:text-sm">원하시는 기능을 선택해 바로 사용해 보세요.</p>
            </div>
            
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                <a href="/font-tool/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:border-green-500 transition-all"><div class="text-2xl mb-1">🔤</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">트렌디 폰트 다운로더</h3></a>
                <a href="/video/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:border-green-500 transition-all"><div class="text-2xl mb-1">📥</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">비디오 다운로더</h3></a>
                <a href="/saju-tool/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:border-green-500 transition-all"><div class="text-2xl mb-1">🔮</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">사주 오행 체질 & 처방</h3></a>
                <a href="/pdf-tool/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:border-green-500 transition-all"><div class="text-2xl mb-1">📄</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">PDF 통합 및 변환</h3></a>
                <a href="/emoji-tool/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:border-green-500 transition-all"><div class="text-2xl mb-1">✨</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">이지이모지 PRO</h3></a>
                <a href="/lotto/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:border-amber-500 transition-all"><div class="text-2xl mb-1">🎰</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">사주 로또 추출기</h3></a>
                <a href="/tarot/" class="block bg-white p-4 rounded-xl border border-gray-200 shadow-sm hover:border-purple-500 transition-all"><div class="text-2xl mb-1">🔮</div><h3 class="text-sm font-bold text-gray-900 mb-0.5">오늘의 타로</h3></a>
            </div>
        </div>
    </div>

    <!-- 👉 오른쪽 뉴스 피드 -->
    <div class="lg:col-span-1">
        <div class="bg-white p-4 sm:p-5 rounded-2xl shadow-md border border-gray-200 h-full flex flex-col">
            <div class="flex items-center justify-between mb-3 border-b pb-2">
                <h2 class="text-base font-bold text-gray-800">🔥 실시간 핫이슈</h2>
                <span class="text-[10px] bg-red-100 text-red-600 px-2 py-0.5 rounded-full font-bold animate-pulse">LIVE</span>
            </div>
            <ul id="auto-news-list" class="m-0 p-0 list-none flex-grow">
                <li class="text-gray-500 text-xs py-4 text-center">뉴스를 불러오는 중입니다...</li>
            </ul>
        </div>
    </div>
</div>

<script>
// 깃허브 테마 환경에서도 100% 뉴스를 가져오도록 아주 튼튼하게 짠 스크립트입니다.
function fetchNews() {
    const list = document.getElementById('auto-news-list');
    if(!list || list.dataset.loaded) return; 
    list.dataset.loaded = 'true'; // 중복 실행 방지

    // 가장 안정적인 구글 뉴스 RSS 파싱 서버
    fetch('https://api.rss2json.com/v1/api.json?rss_url=https%3A%2F%2Fnews.google.com%2Frss%3Fhl%3Dko%26gl%3DKR%26ceid%3DKR%3Ako')
    .then(res => res.json())
    .then(data => {
        list.innerHTML = ''; 
        data.items.slice(0,7).forEach(item => {
            let title = item.title.split(' - ')[0];
            list.innerHTML += `<li class="py-2.5 border-b border-gray-100 last:border-0"><a href="${item.link}" target="_blank" class="text-sm text-gray-800 hover:text-blue-600 font-medium leading-snug no-underline block">${title}</a></li>`;
        });
    })
    .catch(err => {
        list.innerHTML = '<li class="text-xs text-red-500 py-2 text-center">뉴스를 가져오지 못했습니다.</li>';
    });
}

// 창이 열리자마자 무조건 실행되게 강제 배정
setTimeout(fetchNews, 300);
document.addEventListener("DOMContentLoaded", fetchNews);
</script>
