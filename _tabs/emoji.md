---
title: 이모지 1초 복사 툴
icon: fas fa-smile
order: 10
layout: page
permalink: /emoji-tool/
---

{% raw %}
<style>
    .toast {
        transition: all 0.3s cubic-bezier(0.68, -0.55, 0.26, 1.55);
    }
</style>

<script src="https://cdn.tailwindcss.com"></script>

<div class="bg-gray-50 text-gray-800 flex flex-col selection:bg-pink-200" style="min-height: 80vh;">
    <!-- 상단 헤더 & 검색바 -->
    <header class="bg-white border-b border-gray-200 sticky top-0 z-20 shadow-sm rounded-t-xl mt-4">
        <div class="max-w-xl mx-auto px-4 py-3">
            <div class="flex items-center justify-between mb-2">
                <h1 class="text-lg font-bold text-gray-900 flex items-center gap-1.5" style="margin:0;">
                    <span>✨</span> 이지이모지
                </h1>
                <span class="text-xs text-gray-400 bg-gray-100 px-2 py-1 rounded-full">클릭하면 복사됨</span>
            </div>
            <input type="text" id="searchInput" placeholder="이모지 검색 (예: 하트, 불, 웃음, 고양이)..." 
                class="w-full px-4 py-2.5 bg-gray-100 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-pink-500 focus:bg-white transition-all">
        </div>
    </header>

    <!-- 카테고리 탭 -->
    <nav class="max-w-xl mx-auto w-full px-4 mt-3">
        <div class="flex gap-1.5 overflow-x-auto pb-2 scrollbar-none" id="categoryTabs">
            <button onclick="window.filterEmojiCat('all', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-gray-900 text-white transition-all whitespace-nowrap">전체</button>
            <button onclick="window.filterEmojiCat('face', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-white text-gray-600 border border-gray-200 hover:bg-gray-100 transition-all whitespace-nowrap">😀 표정/감정</button>
            <button onclick="window.filterEmojiCat('heart', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-white text-gray-600 border border-gray-200 hover:bg-gray-100 transition-all whitespace-nowrap">💖 하트/손가락</button>
            <button onclick="window.filterEmojiCat('animal', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-white text-gray-600 border border-gray-200 hover:bg-gray-100 transition-all whitespace-nowrap">🐶 동물/자연</button>
            <button onclick="window.filterEmojiCat('symbol', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-white text-gray-600 border border-gray-200 hover:bg-gray-100 transition-all whitespace-nowrap">⚡ 특수/심볼</button>
        </div>
    </nav>

    <!-- 메인 이모지 그리드 영역 -->
    <main class="max-w-xl mx-auto w-full px-4 flex-1 pb-12 mt-2">
        <div id="emojiGrid" class="grid grid-cols-6 sm:grid-cols-8 gap-2 bg-white p-4 rounded-2xl border border-gray-100 shadow-sm">
            <!-- 자바스크립트로 렌더링됨 -->
        </div>
    </main>

    <!-- 복사완료 토스트 메시지 -->
    <div id="toast" class="fixed bottom-6 left-1/2 -translate-x-1/2 bg-gray-900 text-white text-xs px-4 py-2.5 rounded-full shadow-lg opacity-0 pointer-events-none toast flex items-center gap-1.5 z-50">
        <span>✨</span> <span id="toastText">복사되었습니다!</span>
    </div>
</div>
{% endraw %}

<!-- 하단 구글 애드센스 광고 영역 -->
<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
</div>

<script>
(function() {
    try { if (window.adsbygoogle) { (adsbygoogle = window.adsbygoogle || []).push({}); } } catch(e) {}

    const emojiData = [
        { e: '😀', c: 'face', k: '웃음 스마일 미소' }, { e: '😃', c: 'face', k: '웃음 활짝 기쁨' }, { e: '😁', c: 'face', k: '활짝 웃음' }, { e: '😅', c: 'face', k: '식은땀 웃음 당황' }, { e: '😆', c: 'face', k: '눈감고 웃음' }, { e: '🥹', c: 'face', k: '감동 눈물렁렁' }, { e: '😎', c: 'face', k: '선글라스 멋진 쿨' }, { e: '😍', c: 'face', k: '하트눈 반함 러브' }, { e: '🥰', c: 'face', k: '하트 애교 사랑' }, { e: '🤩', c: 'face', k: '눈이휘둥그레 반짝' }, { e: '🤔', c: 'face', k: '고민 생각 추측' }, { e: '🫡', c: 'face', k: '경례 충성 넵' }, { e: '🤫', c: 'face', k: '쉿 비밀 조용' }, { e: '🤭', c: 'face', k: '킥킥 입가린' }, { e: '🫠', c: 'face', k: '녹아내림 멘붕 더위' }, { e: '🥳', c: 'face', k: '파티 축하 생일' },
        { e: '❤️', c: 'heart', k: '빨간 하트' }, { e: '🩷', c: 'heart', k: '핑크 하트' }, { e: '🧡', c: 'heart', k: '주황 하트' }, { e: '💛', c: 'heart', k: '노란 하트' }, { e: '💚', c: 'heart', k: '초록 하트' }, { e: '💙', c: 'heart', k: '파란 하트' }, { e: '💜', c: 'heart', k: '보라 하트' }, { e: '🖤', c: 'heart', k: '검은 하트' }, { e: '🤍', c: 'heart', k: '하얀 하트' }, { e: '💖', c: 'heart', k: '반짝 하트' }, { e: '💘', c: 'heart', k: '화살표 하트' }, { e: '💝', c: 'heart', k: '선물 하트' }, { e: '🫰', c: 'heart', k: '손가락 하트' }, { e: '🫶', c: 'heart', k: '두손 하트' }, { e: '👍', c: 'heart', k: '좋아요 엄지' }, { e: '👏', c: 'heart', k: '박수 치하' }, { e: '🔥', c: 'heart', k: '불꽃 핫 인기' }, { e: '✨', c: 'heart', k: '반짝이 별' },
        { e: '🐶', c: 'animal', k: '강아지 개' }, { e: '🐱', c: 'animal', k: '고양이 냥이' }, { e: '🐰', c: 'animal', k: '토끼' }, { e: '🐻', c: 'animal', k: '곰돌이 곰' }, { e: '🐼', c: 'animal', k: '판다' }, { e: '🦊', c: 'animal', k: '여우' }, { e: '🦁', c: 'animal', k: '사자' }, { e: '🐯', c: 'animal', k: '호랑이' }, { e: '🦄', c: 'animal', k: '유니콘 환상' }, { e: '🍀', c: 'animal', k: '클로버 네잎클로버 행운' }, { e: '🌸', c: 'animal', k: '벚꽃 꽃잎' }, { e: '🌻', c: 'animal', k: '해바라기' },
        { e: '✅', c: 'symbol', k: '체크 완료 확인' }, { e: '❌', c: 'symbol', k: '엑스 취소' }, { e: '⭐', c: 'symbol', k: '별 별점' }, { e: '🌟', c: 'symbol', k: '빛나는 별' }, { e: '💬', c: 'symbol', k: '말풍선 대화' }, { e: '📢', c: 'symbol', k: '확성기 공지' }, { e: '📌', c: 'symbol', k: '핀 고정' }, { e: '💡', c: 'symbol', k: '전구 아이디어' }, { e: '🎉', c: 'symbol', k: '폭죽 파티' }, { e: '🚀', c: 'symbol', k: '로켓 성장 급상승' }, { e: '💰', c: 'symbol', k: '돈 주머니 부자' }, { e: '🕒', c: 'symbol', k: '시계 시간' }
    ];

    let currentCat = 'all';
    let searchQuery = '';
    const gridEl = document.getElementById('emojiGrid');
    const searchInput = document.getElementById('searchInput');

    window.renderEmojis = function() {
        if (!gridEl) return;
        const filtered = emojiData.filter(item => {
            const matchCat = currentCat === 'all' || item.c === currentCat;
            const matchSearch = searchQuery === '' || item.k.includes(searchQuery) || item.e.includes(searchQuery);
            return matchCat && matchSearch;
        });

        if (filtered.length === 0) {
            gridEl.innerHTML = '<div class="col-span-full py-8 text-center text-xs text-gray-400">검색 결과가 없습니다 😢</div>';
            return;
        }

        gridEl.innerHTML = filtered.map(item => 
            '<button type="button" onclick="window.copyEmojiData(\'' + item.e + '\')" class="h-11 sm:h-12 flex items-center justify-center text-xl sm:text-2xl hover:bg-pink-50 hover:scale-110 active:scale-95 rounded-xl transition-all duration-150 cursor-pointer" title="' + item.k + '">' + item.e + '</button>'
        ).join('');
    };

    window.copyEmojiData = function(emoji) {
        navigator.clipboard.writeText(emoji).then(() => {
            showToast("'" + emoji + "' 복사완료!");
        }).catch(() => {
            const textarea = document.createElement('textarea');
            textarea.value = emoji;
            document.body.appendChild(textarea);
            textarea.select();
            document.execCommand('copy');
            document.body.removeChild(textarea);
            showToast("'" + emoji + "' 복사완료!");
        });
    };

    function showToast(text) {
        const toast = document.getElementById('toast');
        const toastText = document.getElementById('toastText');
        if(!toast || !toastText) return;
        toastText.textContent = text;
        toast.classList.remove('opacity-0', 'pointer-events-none');
        toast.classList.add('opacity-100');
        setTimeout(() => {
            toast.classList.remove('opacity-100');
            toast.classList.add('opacity-0', 'pointer-events-none');
        }, 1500);
    }

    window.filterEmojiCat = function(cat, btn) {
        currentCat = cat;
        document.querySelectorAll('.cat-btn').forEach(b => {
            b.classList.remove('bg-gray-900', 'text-white');
            b.classList.add('bg-white', 'text-gray-600', 'border', 'border-gray-200');
        });
        if(btn) {
            btn.classList.remove('bg-white', 'text-gray-600', 'border', 'border-gray-200');
            btn.classList.add('bg-gray-900', 'text-white');
        }
        window.renderEmojis();
    };

    if (searchInput) {
        searchInput.addEventListener('input', (e) => {
            searchQuery = e.target.value.trim();
            window.renderEmojis();
        });
    }

    window.renderEmojis();
})();
</script>
