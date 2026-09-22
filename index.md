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

<!-- 🖥️ PC 화면 분할 -->
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
                <li class="text-gray-500 text-xs py-8 text-center" id="news-loading-text">뉴스를 확인 중입니다...</li>
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

<script>
function displayNews(items) {
    var list = document.getElementById('auto-news-list');
    if (!list || !items || items.length === 0) return;
    
    var htmlContent = '';
    for (var i = 0; i < items.length; i++) {
        htmlContent += '<li class="py-2.5 border-b border-gray-100 last:border-0"><a href="' + items[i].link + '" target="_blank" class="text-[13px] text-gray-800 hover:text-blue-600 font-medium leading-snug no-underline block line-clamp-2">' + items[i].title + '</a></li>';
    }
    list.innerHTML = htmlContent;
}

function loadDoubleCheckedNews() {
    // 플랜 A: 깃허브 서버의 파일(news.json)을 텍스트로 먼저 읽어 빈 파일인지 확인합니다.
    fetch('/assets/news.json?v=' + new Date().getTime())
        .then(function(response) { return response.text(); })
        .then(function(textData) {
            // 빈 파일이면 강제로 에러를 발생시켜 플랜 B로 넘깁니다.
            if (!textData || textData.trim() === '') throw new Error('파일이 비어있음');
            displayNews(JSON.parse(textData));
        })
        .catch(function(error) {
            // 플랜 B: 파일이 비어있거나 에러가 나면, 즉시 외부 프록시를 통해 구글 뉴스를 다이렉트로 긁어옵니다.
            var backupApiUrl = 'https://api.allorigins.win/get?url=' + encodeURIComponent('https://news.google.com/rss?hl=ko&gl=KR&ceid=KR:ko');
            
            fetch(backupApiUrl)
                .then(function(res) { return res.json(); })
                .then(function(data) {
                    var parser = new DOMParser();
                    var xmlDoc = parser.parseFromString(data.contents, "text/xml");
                    var itemNodes = Array.from(xmlDoc.querySelectorAll("item")).slice(0, 7);
                    
                    var backupItems = itemNodes.map(function(node) {
                        return {
                            title: node.querySelector("title").textContent.split(' - ')[0],
                            link: node.querySelector("link").textContent
                        };
                    });
                    displayNews(backupItems);
                })
                .catch(function(finalError) {
                    var loading = document.getElementById('news-loading-text');
                    if (loading) loading.innerHTML = '<span class="text-red-500">뉴스를 일시적으로 불러올 수 없습니다.</span>';
                });
        });
}

// 안전하게 스크립트 즉시 실행
if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', loadDoubleCheckedNews);
} else {
    loadDoubleCheckedNews();
}
document.addEventListener('turbolinks:load', loadDoubleCheckedNews);
</script>
