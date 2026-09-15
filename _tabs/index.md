<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>심플이모지 - 1초 복사 이모지/특수문자</title>
    <meta name="description" content="인스타, 유튜브, 블로그에 쓰기 좋은 감성 이모지와 특수문자 즉시 복사 사이트">
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        .toast {
            transition: all 0.3s cubic-bezier(0.68, -0.55, 0.26, 1.55);
        }
    </style>
</head>
<body class="bg-gray-50 text-gray-800 min-h-screen flex flex-col selection:bg-pink-200">

    <!-- 상단 헤더 & 검색바 -->
    <header class="bg-white border-b border-gray-200 sticky top-0 z-20 shadow-sm">
        <div class="max-w-xl mx-auto px-4 py-3">
            <div class="flex items-center justify-between mb-2">
                <h1 class="text-lg font-bold text-gray-900 flex items-center gap-1.5">
                    <span>✨</span> 이지이모지
                </h1>
                <span class="text-xs text-gray-400 bg-gray-100 px-2 py-1 rounded-full">클릭하면 복사됨</span>
            </div>
            <input type="text" id="searchInput" placeholder="이모지 검색 (예: 하트, 불, 웃음, 고양이)..." 
                class="w-full px-4 py-2.5 bg-gray-100 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-pink-500 focus:bg-white transition-all">
        </div>
    </header>

    <!-- 상단 광고 영역 (디스플레이 / 전면광고 유도용 배너) -->
    <div class="max-w-xl mx-auto w-full px-4 mt-3">
        <div class="bg-gray-200 border border-dashed border-gray-300 rounded-xl h-16 flex items-center justify-center text-xs text-gray-400">
            <!-- [광고코드 삽입: 상단 배너] -->
            ADs Area (Top Banner)
        </div>
    </div>

    <!-- 카테고리 탭 -->
    <nav class="max-w-xl mx-auto w-full px-4 mt-3">
        <div class="flex gap-1.5 overflow-x-auto pb-2 scrollbar-none" id="categoryTabs">
            <button onclick="filterCategory('all', this)" class="cat-btn active px-3.5 py-1.5 rounded-full text-xs font-medium bg-gray-900 text-white transition-all whitespace-nowrap">전체</button>
            <button onclick="filterCategory('face', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-white text-gray-600 border border-gray-200 hover:bg-gray-100 transition-all whitespace-nowrap">😀 표정/감정</button>
            <button onclick="filterCategory('heart', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-white text-gray-600 border border-gray-200 hover:bg-gray-100 transition-all whitespace-nowrap">💖 하트/손가락</button>
            <button onclick="filterCategory('animal', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-white text-gray-600 border border-gray-200 hover:bg-gray-100 transition-all whitespace-nowrap">🐶 동물/자연</button>
            <button onclick="filterCategory('symbol', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-white text-gray-600 border border-gray-200 hover:bg-gray-100 transition-all whitespace-nowrap">⚡ 특수/심볼</button>
        </div>
    </nav>

    <!-- 메인 이모지 그리드 영역 -->
    <main class="max-w-xl mx-auto w-full px-4 flex-1 pb-12 mt-2">
        <div id="emojiGrid" class="grid grid-cols-6 sm:grid-cols-8 gap-2 bg-white p-4 rounded-2xl border border-gray-100 shadow-sm">
            <!-- 자바스크립트로 렌더링됨 -->
        </div>

        <!-- 중간 인라인 광고 영역 (클릭 유도선 내배치) -->
        <div class="mt-6 bg-gray-200 border border-dashed border-gray-300 rounded-xl h-24 flex items-center justify-center text-xs text-gray-400">
            <!-- [광고코드 삽입: 인라인/네이티브 광고] -->
            ADs Area (Mid Feed)
        </div>
    </main>

    <!-- 복사완료 토스트 메시지 -->
    <div id="toast" class="fixed bottom-6 left-1/2 -translate-x-1/2 bg-gray-900 text-white text-xs px-4 py-2.5 rounded-full shadow-lg opacity-0 pointer-events-none toast flex items-center gap-1.5 z-50">
        <span>✨</span> <span id="toastText">클립보드에 복사되었습니다!</span>
    </div>

    <!-- 푸터 -->
    <footer class="text-center py-6 text-xs text-gray-400 border-t border-gray-100 bg-white">
        <p>&copy; 2026 EasyEmoji. Fast Copy & Paste Utility.</p>
    </footer>

    <!-- 자바스크립트 로직 -->
    <script>
        const emojiData = [
            // 표정/감정 (face)
            { e: '😀', c: 'face', k: '웃음 스마일 미소' },
            { e: '😃', c: 'face', k: '웃음 활짝 기쁨' },
            { e: '😁', c: 'face', k: '활짝 웃음' },
            { e: '😅', c: 'face', k: '식은땀 웃음 당황' },
            { e: '😆', c: 'face', k: '눈감고 웃음' },
            { e: '🥹', c: 'face', k: '감동 눈물렁렁' },
            { e: '😎', c: 'face', k: '선글라스 멋진 쿨' },
            { e: '😍', c: 'face', k: '하트눈 반함 러브' },
            { e: '🥰', c: 'face', k: '하트 애교 사랑' },
            { e: '🤩', c: 'face', k: '눈이휘둥그레 반짝' },
            { e: '🤔', c: 'face', k: '고민 생각 추측' },
            { e: '🫡', c: 'face', k: '경례 충성 넵' },
            { e: '🤫', c: 'face', k: '쉿 비밀 조용' },
            { e: '🤭', c: 'face', k: '킥킥 입가린' },
            { e: '🫠', c: 'face', k: '녹아내림 멘붕 더위' },
            { e: '🥳', c: 'face', k: '파티 축하 생일' },

            // 하트/손가락 (heart)
            { e: '❤️', c: 'heart', k: '빨간 하트' },
            { e: '🩷', c: 'heart', k: '핑크 하트' },
            { e: '🧡', c: 'heart', k: '주황 하트' },
            { e: '💛', c: 'heart', k: '노란 하트' },
            { e: '💚', c: 'heart', k: '초록 하트' },
            { e: '💙', c: 'heart', k: '파란 하트' },
            { e: '💜', c: 'heart', k: '보라 하트' },
            { e: '🖤', c: 'heart', k: '검은 하트' },
            { e: '🤍', c: 'heart', k: '하얀 하트' },
            { e: '💖', c: 'heart', k: '반짝 하트' },
            { e: '💘', c: 'heart', k: '화살표 하트' },
            { e: '💝', c: 'heart', k: '선물 하트' },
            { e: '🫰', c: 'heart', k: '손가락 하트' },
            { e: '🫶', c: 'heart', k: '두손 하트' },
            { e: '👍', c: 'heart', k: '좋아요 엄지' },
            { e: '👏', c: 'heart', k: '박수 치하' },
            { e: '🔥', c: 'heart', k: '불꽃 핫 인기' },
            { e: '✨', c: 'heart', k: '반짝이 별' },

            // 동물/자연 (animal)
            { e: '🐶', c: 'animal', k: '강아지 개' },
            { e: '🐱', c: 'animal', k: '고양이 냥이' },
            { e: '🐰', c: 'animal', k: '토끼' },
            { e: '🐻', c: 'animal', k: '곰돌이 곰' },
            { e: '🐼', c: 'animal', k: '판다' },
            { e: '🦊', c: 'animal', k: '여우' },
            { e: '🦁', c: 'animal', k: '사자' },
            { e: '🐯', c: 'animal', k: '호랑이' },
            { e: '🦄', c: 'animal', k: '유니콘 환상' },
            { e: '🍀', c: 'animal', k: '클로버 네잎클로버 행운' },
            { e: '🌸', c: 'animal', k: '벚꽃 꽃잎' },
            { e: '🌻', c: 'animal', k: '해바라기' },

            // 특수/심볼 (symbol)
            { e: '✅', c: 'symbol', k: '체크 완료 확인' },
            { e: '❌', c: 'symbol', k: '엑스 취소' },
            { e: '⭐', c: 'symbol', k: '별 별점' },
            { e: '🌟', c: 'symbol', k: '빛나는 별' },
            { e: '💬', c: 'symbol', k: '말풍선 대화' },
            { e: '📢', c: 'symbol', k: '확성기 공지' },
            { e: '📌', c: 'symbol', k: '핀 고정' },
            { e: '💡', c: 'symbol', k: '전구 아이디어' },
            { e: '🎉', c: 'symbol', k: '폭죽 파티' },
            { e: '🚀', c: 'symbol', k: '로켓 성장 급상승' },
            { e: '💰', c: 'symbol', k: '돈 주머니 부자' },
            { e: '🕒', c: 'symbol', k: '시계 시간' }
        ];

        let currentCat = 'all';
        let searchQuery = '';

        const gridEl = document.getElementById('emojiGrid');
        const searchInput = document.getElementById('searchInput');

        function renderEmojis() {
            const filtered = emojiData.filter(item => {
                const matchCat = currentCat === 'all' || item.c === currentCat;
                const matchSearch = searchQuery === '' || item.k.includes(searchQuery) || item.e.includes(searchQuery);
                return matchCat && matchSearch;
            });

            if (filtered.length === 0) {
                gridEl.innerHTML = `<div class="col-span-full py-8 text-center text-xs text-gray-400">검색 결과가 없습니다 😢</div>`;
                return;
            }

            gridEl.innerHTML = filtered.map(item => `
                <button onclick="copyEmoji('${item.e}')" 
                    class="h-11 sm:h-12 flex items-center justify-center text-xl sm:text-2xl hover:bg-pink-50 hover:scale-110 active:scale-95 rounded-xl transition-all duration-150 cursor-pointer"
                    title="${item.k}">
                    ${item.e}
                </button>
            `).join('');
        }

        function copyEmoji(emoji) {
            navigator.clipboard.writeText(emoji).then(() => {
                showToast(`'${emoji}' 복사완료!`);
            }).catch(() => {
                // 구형 브라우저 fallback
                const textarea = document.createElement('textarea');
                textarea.value = emoji;
                document.body.appendChild(textarea);
                textarea.select();
                document.execCommand('copy');
                document.body.removeChild(textarea);
                showToast(`'${emoji}' 복사완료!`);
            });
        }

        function showToast(text) {
            const toast = document.getElementById('toast');
            const toastText = document.getElementById('toastText');
            toastText.textContent = text;
            toast.classList.remove('opacity-0', 'pointer-events-none');
            toast.classList.add('opacity-100');
            setTimeout(() => {
                toast.classList.remove('opacity-100');
                toast.classList.add('opacity-0', 'pointer-events-none');
            }, 1500);
        }

        function filterCategory(cat, btn) {
            currentCat = cat;
            document.querySelectorAll('.cat-btn').forEach(b => {
                b.classList.remove('bg-gray-900', 'text-white');
                b.classList.add('bg-white', 'text-gray-600', 'border', 'border-gray-200');
            });
            btn.classList.remove('bg-white', 'text-gray-600', 'border', 'border-gray-200');
            btn.classList.add('bg-gray-900', 'text-white');
            renderEmojis();
        }

        searchInput.addEventListener('input', (e) => {
            searchQuery = e.target.value.trim();
            renderEmojis();
        });

        // 초기 렌더링
        renderEmojis();
    </script>
</body>
</html>
