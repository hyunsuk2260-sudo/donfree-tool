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
    /* 스크롤바 숨기기 (모바일 스와이프용) */
    .scrollbar-none::-webkit-scrollbar {
        display: none;
    }
    .scrollbar-none {
        -ms-overflow-style: none;
        scrollbar-width: none;
    }
</style>

<script src="https://cdn.tailwindcss.com"></script>

<div class="bg-gray-50 text-gray-800 flex flex-col selection:bg-pink-200" style="min-height: 80vh;">
    <!-- 상단 헤더 & 검색바 -->
    <header class="bg-white border-b border-gray-200 sticky top-0 z-20 shadow-sm rounded-t-xl mt-4">
        <div class="max-w-xl mx-auto px-4 py-3">
            <div class="flex items-center justify-between mb-2">
                <h1 class="text-lg font-bold text-gray-900 flex items-center gap-1.5" style="margin:0;">
                    <span>✨</span> 이지이모지 PRO
                </h1>
                <span class="text-xs text-gray-400 bg-gray-100 px-2 py-1 rounded-full">클릭 시 즉시 복사</span>
            </div>
            <input type="text" id="searchInput" placeholder="검색 (예: 하트, 맥주, 인사, 바다)..." 
                class="w-full px-4 py-2.5 bg-gray-100 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-pink-500 focus:bg-white transition-all">
        </div>
    </header>

    <!-- 세분화된 카테고리 탭 (가로 스크롤) -->
    <nav class="max-w-xl mx-auto w-full px-4 mt-3">
        <div class="flex gap-2 overflow-x-auto pb-2 scrollbar-none" id="categoryTabs">
            <button onclick="window.filterEmojiCat('all', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-gray-900 text-white transition-all whitespace-nowrap shadow-sm">전체</button>
            <button onclick="window.filterEmojiCat('face', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-white text-gray-600 border border-gray-200 hover:bg-gray-100 transition-all whitespace-nowrap shadow-sm">😀 표정</button>
            <button onclick="window.filterEmojiCat('hand', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-white text-gray-600 border border-gray-200 hover:bg-gray-100 transition-all whitespace-nowrap shadow-sm">👌 손가락</button>
            <button onclick="window.filterEmojiCat('people', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-white text-gray-600 border border-gray-200 hover:bg-gray-100 transition-all whitespace-nowrap shadow-sm">🏃 사람·모션</button>
            <button onclick="window.filterEmojiCat('food', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-white text-gray-600 border border-gray-200 hover:bg-gray-100 transition-all whitespace-nowrap shadow-sm">🍔 음식·음료</button>
            <button onclick="window.filterEmojiCat('place', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-white text-gray-600 border border-gray-200 hover:bg-gray-100 transition-all whitespace-nowrap shadow-sm">✈️ 장소·여행</button>
            <button onclick="window.filterEmojiCat('animal', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-white text-gray-600 border border-gray-200 hover:bg-gray-100 transition-all whitespace-nowrap shadow-sm">🐶 동물·자연</button>
            <button onclick="window.filterEmojiCat('symbol', this)" class="cat-btn px-3.5 py-1.5 rounded-full text-xs font-medium bg-white text-gray-600 border border-gray-200 hover:bg-gray-100 transition-all whitespace-nowrap shadow-sm">💖 하트·특수</button>
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
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
</div>

{% raw %}
<script>
(function() {
    try { if (window.adsbygoogle) { (adsbygoogle = window.adsbygoogle || []).push({}); } } catch(e) {}

    const emojiData = [
        // 1. 표정 (face)
        { e: '😀', c: 'face', k: '웃음 스마일 미소' }, { e: '😃', c: 'face', k: '웃음 활짝 기쁨' }, { e: '😁', c: 'face', k: '활짝 웃음 눈웃음' }, { e: '😅', c: 'face', k: '식은땀 당황 뻘쭘' }, { e: '😆', c: 'face', k: '눈감고 웃음 빵터짐' }, { e: '😂', c: 'face', k: '눈물 웃음 ㅋㅋㅋ' }, { e: '🤣', c: 'face', k: '구르며 웃음 폭소' }, { e: '🥹', c: 'face', k: '감동 눈물 글썽' }, { e: '😊', c: 'face', k: '부끄 미소' }, { e: '😇', c: 'face', k: '천사 착함' }, { e: '😍', c: 'face', k: '하트눈 반함 러브' }, { e: '🥰', c: 'face', k: '하트 애교 사랑' }, { e: '🤩', c: 'face', k: '별눈 눈부심 기대' }, { e: '😘', c: 'face', k: '뽀뽀 윙크' }, { e: '😋', c: 'face', k: '메롱 맛있다 핥기' }, { e: '😎', c: 'face', k: '선글라스 멋진 쿨' }, { e: '🤔', c: 'face', k: '고민 생각 추측' }, { e: '🫡', c: 'face', k: '경례 충성 넵 알겠습니다' }, { e: '🤫', c: 'face', k: '쉿 비밀 조용' }, { e: '🤭', c: 'face', k: '킥킥 입가린 어머' }, { e: '🫠', c: 'face', k: '녹아내림 멘붕 더위 피곤' }, { e: '🥳', c: 'face', k: '파티 축하 생일' }, { e: '🥺', c: 'face', k: '애절 부탁 불쌍' }, { e: '😭', c: 'face', k: '오열 슬픔 ㅠㅠ' }, { e: '😱', c: 'face', k: '비명 공포 헉' }, { e: '😡', c: 'face', k: '분노 화남 빡침' },

        // 2. 손가락/제스처 (hand)
        { e: '👋', c: 'hand', k: '안녕 인사 손흔들기 bye' }, { e: '🤚', c: 'hand', k: '멈춰 손등' }, { e: '🖐️', c: 'hand', k: '다섯 손바닥 하이파이브' }, { e: '✋', c: 'hand', k: '정지 손' }, { e: '🖖', c: 'hand', k: '외계인 스타트렉 스팍 인사' }, { e: '👌', c: 'hand', k: '오케이 ok 승인 좋아' }, { e: '🤌', c: 'hand', k: '이탈리아 꼬집기 맛있어' }, { e: '🤏', c: 'hand', k: '조금 작다 쪼끔' }, { e: '✌️', c: 'hand', k: '브이 v 승리 평화' }, { e: '🤞', c: 'hand', k: '행운 크로스 약속' }, { e: '🤟', c: 'hand', k: '사랑해 수어' }, { e: '🤘', c: 'hand', k: '록 스피릿 락 힙합' }, { e: '🤙', c: 'hand', k: '전화해 약속 하와이 쿨' }, { e: '👈', c: 'hand', k: '왼쪽 가리키기' }, { e: '👉', c: 'hand', k: '오른쪽 가리키기' }, { e: '👆', c: 'hand', k: '위쪽 가리키기' }, { e: '👇', c: 'hand', k: '아래쪽 가리키기' }, { e: '👍', c: 'hand', k: '따봉 최고 좋아요 엄지' }, { e: '👎', c: 'hand', k: '우우 별로 싫어요' }, { e: '✊', c: 'hand', k: '주먹 화이팅 결의' }, { e: '👊', c: 'hand', k: '주먹인사 펀치 👊' }, { e: '👏', c: 'hand', k: '박수 짝짝 칭찬' }, { e: '🙌', c: 'hand', k: '만세 환호' }, { e: '👐', c: 'hand', k: '양손 열기 포옹' }, { e: '🤲', c: 'hand', k: '두손 모으기 받기' }, { e: '🤝', c: 'hand', k: '악수 계약 동의' }, { e: '🙏', c: 'hand', k: '기도 제발 부탁 합장' }, { e: '✍️', c: 'hand', k: '필기 쓰기 메모' }, { e: '💪', c: 'hand', k: '근육 힘 파워 헬스' },

        // 3. 사람/모션 (people)
        { e: '🏃', c: 'people', k: '달리기 뛰기 러닝' }, { e: '🚶', c: 'people', k: '걷기 산책 보행' }, { e: '💃', c: 'people', k: '춤 댄스 여자 훌라' }, { e: '🕺', c: 'people', k: '춤 댄스 남자 디스코' }, { e: '🤦', c: 'people', k: '이마짚 아뿔싸 맙소사' }, { e: '🤷', c: 'people', k: '어깨으쓱 몰라 어쩌라고' }, { e: '🙇', c: 'people', k: '절 사과 엎드림 부탁' }, { e: '🙋', c: 'people', k: '손들기 질문 저요' }, { e: '🙅', c: 'people', k: '엑스 안돼 거절 금지' }, { e: '🙆', c: 'people', k: '오케이 정답 동의 원' }, { e: '💁', c: 'people', k: '안내 설명 어머' }, { e: '💆', c: 'people', k: '마사지 휴식 힐링' }, { e: '💇', c: 'people', k: '이발 미용실 머리자르기' }, { e: '🧘', c: 'people', k: '요가 명상 참선' }, { e: '🛌', c: 'people', k: '침대 누워있기 수면 잠' }, { e: '🛀', c: 'people', k: '목욕 반신욕 거품' }, { e: '🏄', c: 'people', k: '서핑 바다 파도' }, { e: '🏊', c: 'people', k: '수영 풀장 수영장' }, { e: '🚴', c: 'people', k: '자전거 라이딩 싸이클' }, { e: '🤸', c: 'people', k: '체조 덤블링 신남' }, { e: '👫', c: 'people', k: '커플 데이트 남녀 친구' }, { e: '👨‍👩‍👦', c: 'people', k: '가족 부부 아이 패밀리' },

        // 4. 음식/음료 (food)
        { e: '🍔', c: 'food', k: '햄버거 패스트푸드 빵' }, { e: '🍟', c: 'food', k: '감자튀김 프렌치프라이' }, { e: '🍕', c: 'food', k: '피자 이탈리아 치즈' }, { e: '🌭', c: 'food', k: '핫도그 소시지' }, { e: '🥪', c: 'food', k: '샌드위치 브런치 토스트' }, { e: '🌮', c: 'food', k: '타코 멕시칸' }, { e: '🌯', c: 'food', k: '부리또 랩' }, { e: '🥗', c: 'food', k: '샐러드 채소 다이어트 건강' }, { e: '🍿', c: 'food', k: '팝콘 영화 간식' }, { e: '🥓', c: 'food', k: '베이컨 고기 돼지' }, { e: '🥩', c: 'food', k: '스테이크 소고기 육류' }, { e: '🍗', c: 'food', k: '치킨 닭다리 통닭' }, { e: '🍖', c: 'food', k: '고기 만화고기 바베큐' }, { e: '🍙', c: 'food', k: '주먹밥 삼각김밥 밥' }, { e: '🍚', c: 'food', k: '밥 공기밥 쌀' }, { e: '🍜', c: 'food', k: '라면 국수 누들 우동' }, { e: '🍝', c: 'food', k: '파스타 스파게티 양식' }, { e: '🍣', c: 'food', k: '초밥 스시 회 일본' }, { e: '🍤', c: 'food', k: '새우튀김 튀김 덴푸라' }, { e: '🥟', c: 'food', k: '만두 딤섬 교자' }, { e: '🍰', c: 'food', k: '케이크 조각케익 디저트 생일' }, { e: '🎂', c: 'food', k: '생일케이크 파티 촛불' }, { e: '🧁', c: 'food', k: '컵케이크 머핀 달콤' }, { e: '🥧', c: 'food', k: '파이 타르트 빵' }, { e: '🍫', c: 'food', k: '초콜릿 발렌타인 단거' }, { e: '🍬', c: 'food', k: '사탕 캔디 화이트데이' }, { e: '🍭', c: 'food', k: '막대사탕 롤리팝' }, { e: '🍩', c: 'food', k: '도넛 도나스 달콤' }, { e: '🍪', c: 'food', k: '쿠키 비스킷 과자' }, { e: '🍨', c: 'food', k: '아이스크림 빙수 여름' }, { e: '☕', c: 'food', k: '커피 아메리카노 카페 따뜻' }, { e: '🍵', c: 'food', k: '녹차 찻잔 차 따뜻' }, { e: '🧃', c: 'food', k: '주스 팩음료' }, { e: '🥤', c: 'food', k: '콜라 음료수 컵' }, { e: '🍺', c: 'food', k: '맥주 술 호프 회식' }, { e: '🍻', c: 'food', k: '건배 짠 맥주 회식' }, { e: '🍷', c: 'food', k: '와인 포도주 분위기' }, { e: '🥂', c: 'food', k: '샴페인 짠 축하 파티' }, { e: '🥃', c: 'food', k: '위스키 양주 온더락' }, { e: '🍎', c: 'food', k: '사과 과일 애플' }, { e: '🍓', c: 'food', k: '딸기 과일 상큼' }, { e: '🍉', c: 'food', k: '수박 여름 과일' }, { e: '🍌', c: 'food', k: '바나나 과일' }, { e: '🥑', c: 'food', k: '아보카도 채소 건강' },

        // 5. 장소/여행 (place)
        { e: '✈️', c: 'place', k: '비행기 여행 공항 출국 탑승' }, { e: '🛫', c: 'place', k: '이륙 비행기 출발 여행' }, { e: '🛬', c: 'place', k: '착륙 도착 귀국 비행기' }, { e: '🚀', c: 'place', k: '로켓 우주 발사 급상승' }, { e: '🚁', c: 'place', k: '헬리콥터 헬기' }, { e: '🚂', c: 'place', k: '기차 증기기관차 기차역' }, { e: '🚄', c: 'place', k: 'KTX 고속열차 기차' }, { e: '🚇', c: 'place', k: '지하철 전철 메트로' }, { e: '🚌', c: 'place', k: '버스 대중교통 승합차' }, { e: '🚕', c: 'place', k: '택시 택시호출' }, { e: '🚗', c: 'place', k: '자동차 드라이브 차 자가용' }, { e: '🚲', c: 'place', k: '자전거 따릉이 라이딩' }, { e: '🛵', c: 'place', k: '스쿠터 오토바이 배달' }, { e: '🚢', c: 'place', k: '배 선박 크루즈 항해' }, { e: '🏠', c: 'place', k: '집 주택 홈 귀가' }, { e: '🏡', c: 'place', k: '집 마당 전원주택 홈' }, { e: '🏢', c: 'place', k: '빌딩 회사 사무실 건물' }, { e: '🏨', c: 'place', k: '호텔 숙소 호캉스 숙박' }, { e: '🏪', c: 'place', k: '편의점 마트 24시간 상점' }, { e: '🏫', c: 'place', k: '학교 학원 교육 등교' }, { e: '🏥', c: 'place', k: '병원 의원 약국 치료' }, { e: '🏦', c: 'place', k: '은행 금융 돈 저축' }, { e: '⛺', c: 'place', k: '텐트 캠핑 글램핑 야영' }, { e: '🎢', c: 'place', k: '롤러코스터 놀이공원 테마파크' }, { e: '🎡', c: 'place', k: '관람차 놀이동산 데이트' }, { e: '🏖️', c: 'place', k: '바다 해변 파라솔 바캉스 휴가' }, { e: '🏝️', c: 'place', k: '무인도 섬 야자수 휴양지' }, { e: '🏔️', c: 'place', k: '설산 산 등산 하이킹' }, { e: '🗼', c: 'place', k: '타워 도쿄타워 에펠탑 랜드마크' }, { e: '🗽', c: 'place', k: '자유의여신상 뉴욕 미국' }, { e: '🗺️', c: 'place', k: '지도 맵 길찾기 여행' }, { e: '🧭', c: 'place', k: '나침반 방향 탐험' },

        // 6. 동물/자연 (animal)
        { e: '🐶', c: 'animal', k: '강아지 개 멍멍이 퍼그' }, { e: '🐱', c: 'animal', k: '고양이 냥이 야옹이' }, { e: '🐭', c: 'animal', k: '쥐 햄스터 마우스' }, { e: '🐹', c: 'animal', k: '햄스터 찍찍이 귀여운' }, { e: '🐰', c: 'animal', k: '토끼 바니 깡총' }, { e: '🦊', c: 'animal', k: '여우 구미호 꼬리' }, { e: '🐻', c: 'animal', k: '곰 곰돌이 베어' }, { e: '🐼', c: 'animal', k: '판다 팬더 푸바오' }, { e: '🐻‍❄️', c: 'animal', k: '북극곰 백곰 폴라베어' }, { e: '🐨', c: 'animal', k: '코알라 호주 나무' }, { e: '🐯', c: 'animal', k: '호랑이 어흥 맹수' }, { e: '🦁', c: 'animal', k: '사자 라이온 킹 어흥' }, { e: '🐮', c: 'animal', k: '소 얼룩소 송아지' }, { e: '🐷', c: 'animal', k: '돼지 꿀꿀이 복' }, { e: '🐸', c: 'animal', k: '개구리 청개구리 양서류' }, { e: '🐵', c: 'animal', k: '원숭이 몽키 유인원' }, { e: '🐔', c: 'animal', k: '닭 치킨 꼬꼬' }, { e: '🐧', c: 'animal', k: '펭귄 뽀로로 남극' }, { e: '🐦', c: 'animal', k: '새 참새 짹짹' }, { e: '🐤', c: 'animal', k: '병아리 삐약 귀여움' }, { e: '🦆', c: 'animal', k: '오리 꽥꽥' }, { e: '🦉', c: 'animal', k: '부엉이 올빼미 밤' }, { e: '🦇', c: 'animal', k: '박쥐 배트맨 할로윈' }, { e: '🐺', c: 'animal', k: '늑대 울음 숲' }, { e: '🐗', c: 'animal', k: '멧돼지 야생' }, { e: '🐴', c: 'animal', k: '말 당나귀 승마' }, { e: '🦄', c: 'animal', k: '유니콘 뿔 환상 마법' }, { e: '🐝', c: 'animal', k: '꿀벌 윙윙 곤충' }, { e: '🐛', c: 'animal', k: '애벌레 벌레 곤충' }, { e: '🦋', c: 'animal', k: '나비 날개 봄' }, { e: '🐌', c: 'animal', k: '달팽이 느림 비' }, { e: '🐞', c: 'animal', k: '무당벌레 행운 곤충' }, { e: '🐜', c: 'animal', k: '개미 일개미 곤충' }, { e: '🕷️', c: 'animal', k: '거미 스파이더 곤충' }, { e: '🦂', c: 'animal', k: '전갈 독 곤충' }, { e: '🐢', c: 'animal', k: '거북이 닌자 바다 느림' }, { e: '🐍', c: 'animal', k: '뱀 독사 파충류' }, { e: '🦎', c: 'animal', k: '도마뱀 카멜레온 파충류' }, { e: '🦖', c: 'animal', k: '공룡 티라노 육식' }, { e: '🦕', c: 'animal', k: '공룡 브라키오 초식' }, { e: '🐙', c: 'animal', k: '문어 크라켄 바다' }, { e: '🦑', c: 'animal', k: '오징어 바다 해물' }, { e: '🦐', c: 'animal', k: '새우 해물 바다' }, { e: '🦞', c: 'animal', k: '랍스터 가재 해물' }, { e: '🦀', c: 'animal', k: '게 크랩 해물' }, { e: '🐡', c: 'animal', k: '복어 물고기 바다' }, { e: '🐠', c: 'animal', k: '열대어 니모 물고기' }, { e: '🐟', c: 'animal', k: '물고기 생선 낚시' }, { e: '🐬', c: 'animal', k: '돌고래 바다 똑똑함' }, { e: '🐳', c: 'animal', k: '고래 분수 바다' }, { e: '🐋', c: 'animal', k: '고래 큰고래 바다' }, { e: '🦈', c: 'animal', k: '상어 죠스 무서운 바다' }, { e: '🐊', c: 'animal', k: '악어 크로커다일 파충류' }, { e: '🐅', c: 'animal', k: '호랑이 표범 동물원' }, { e: '🐆', c: 'animal', k: '표범 치타 맹수' }, { e: '🦓', c: 'animal', k: '얼룩말 무늬 아프리카' }, { e: '🦍', c: 'animal', k: '고릴라 킹콩 힘' }, { e: '🦧', c: 'animal', k: '오랑우탄 유인원 원숭이' }, { e: '🐘', c: 'animal', k: '코끼리 덤보 큰동물' }, { e: '🦛', c: 'animal', k: '하마 큰입 아프리카' }, { e: '🦏', c: 'animal', k: '코뿔소 뿔 동물' }, { e: '🐪', c: 'animal', k: '낙타 사막 단봉' }, { e: '🐫', c: 'animal', k: '쌍봉낙타 사막' }, { e: '🦒', c: 'animal', k: '기린 목이긴 아프리카' }, { e: '🦘', c: 'animal', k: '캥거루 호주 점프' }, { e: '🐃', c: 'animal', k: '물소 소 아프리카' }, { e: '🐂', c: 'animal', k: '황소 소 농장' }, { e: '🐄', c: 'animal', k: '젖소 우유 농장' }, { e: '🐎', c: 'animal', k: '달리는말 경마 승마' }, { e: '🐖', c: 'animal', k: '돼지 돼지고기 농장' }, { e: '🐏', c: 'animal', k: '숫양 양 뿔' }, { e: '🐑', c: 'animal', k: '양 털 메에' }, { e: '🦙', c: 'animal', k: '알파카 라마 남미' }, { e: '🐐', c: 'animal', k: '염소 수염 농장' }, { e: '🦌', c: 'animal', k: '사슴 루돌프 크리스마스' }, { e: '🐕', c: 'animal', k: '개 강아지 멍멍이' }, { e: '🐩', c: 'animal', k: '푸들 개 애완견' }, { e: '🦮', c: 'animal', k: '안내견 맹인 돕는개' }, { e: '🐕‍🦺', c: 'animal', k: '서비스견 구조견 개' }, { e: '🐈', c: 'animal', k: '고양이 야옹이 애완묘' }, { e: '🐓', c: 'animal', k: '수탉 닭 아침' }, { e: '🦃', c: 'animal', k: '칠면조 추수감사절 새' }, { e: '🦚', c: 'animal', k: '공작 꼬리 화려한 새' }, { e: '🦜', c: 'animal', k: '앵무새 말하는새 새' }, { e: '🦢', c: 'animal', k: '백조 우아한 새 호수' }, { e: '🦩', c: 'animal', k: '홍학 플라밍고 분홍 새' }, { e: '🕊️', c: 'animal', k: '비둘기 평화 새' }, { e: '🐇', c: 'animal', k: '토끼 달리기 동물' }, { e: '🦝', c: 'animal', k: '너구리 라쿤 동물' }, { e: '🦨', c: 'animal', k: '스컹크 방귀 냄새 동물' }, { e: '🦡', c: 'animal', k: '오소리 동물 숲' }, { e: '🦦', c: 'animal', k: '수달 보노보노 귀여운 바다' }, { e: '🦥', c: 'animal', k: '나무늘보 느림 동물' }, { e: '🐁', c: 'animal', k: '생쥐 쥐 동물' }, { e: '🐀', c: 'animal', k: '시궁쥐 쥐 동물' }, { e: '🐿️', c: 'animal', k: '다람쥐 도토리 숲' }, { e: '🦔', c: 'animal', k: '고슴도치 가시 동물' }, { e: '🐾', c: 'animal', k: '발자국 발바닥 동물 펫' }, { e: '🐉', c: 'animal', k: '용 드래곤 전설' }, { e: '🐲', c: 'animal', k: '용머리 드래곤 전설' }, { e: '🌵', c: 'animal', k: '선인장 사막 식물' }, { e: '🎄', c: 'animal', k: '크리스마스트리 나무 겨울' }, { e: '🌲', c: 'animal', k: '소나무 상록수 숲' }, { e: '🌳', c: 'animal', k: '나무 잎 식물 숲' }, { e: '🌴', c: 'animal', k: '야자수 여름 바다' }, { e: '🌱', c: 'animal', k: '새싹 새생명 식물 봄' }, { e: '🌿', c: 'animal', k: '허브 잎 식물 자연' }, { e: '☘️', c: 'animal', k: '세잎클로버 식물' }, { e: '🍀', c: 'animal', k: '네잎클로버 행운 식물' }, { e: '🎍', c: 'animal', k: '대나무 소나무 장식 일본' }, { e: '🪴', c: 'animal', k: '화분 식물 집' }, { e: '🎋', c: 'animal', k: '칠석 대나무 장식 소원' }, { e: '🍃', c: 'animal', k: '나뭇잎 떨어지는잎 가을' }, { e: '🍂', c: 'animal', k: '낙엽 마른잎 가을' }, { e: '🍁', c: 'animal', k: '단풍잎 단풍 가을' }, { e: '🍄', c: 'animal', k: '버섯 독버섯 식물' }, { e: '🌾', c: 'animal', k: '벼 쌀 추수 식물' }, { e: '💐', c: 'animal', k: '꽃다발 축하 선물 꽃' }, { e: '🌷', c: 'animal', k: '튤립 꽃 봄' }, { e: '🌹', c: 'animal', k: '장미 꽃 사랑 정열' }, { e: '🥀', c: 'animal', k: '시든장미 이별 슬픔 꽃' }, { e: '🌺', c: 'animal', k: '무궁화 하와이꽃 꽃' }, { e: '🌸', c: 'animal', k: '벚꽃 봄 꽃' }, { e: '🌼', c: 'animal', k: '꽃 노란꽃 봄' }, { e: '🌻', c: 'animal', k: '해바라기 여름 꽃' },

        // 7. 하트/특수 (symbol)
        { e: '✅', c: 'symbol', k: '체크 완료 확인' }, { e: '❌', c: 'symbol', k: '엑스 취소' }, { e: '⭐', c: 'symbol', k: '별 별점' }, { e: '🌟', c: 'symbol', k: '빛나는 별 반짝' }, { e: '💬', c: 'symbol', k: '말풍선 대화 코멘트' }, { e: '📢', c: 'symbol', k: '확성기 공지 알림' }, { e: '📌', c: 'symbol', k: '핀 핀셋 고정 중요' }, { e: '💡', c: 'symbol', k: '전구 아이디어 깨달음' }, { e: '🎉', c: 'symbol', k: '폭죽 파티 축하' }, { e: '🔥', c: 'symbol', k: '불꽃 핫 화제 불' }, { e: '💰', c: 'symbol', k: '돈 주머니 부자 현금' }, { e: '🕒', c: 'symbol', k: '시계 시간 대기' }, { e: '⚠️', c: 'symbol', k: '경고 주의 느낌표' }, { e: '❓', c: 'symbol', k: '물음표 질문 궁금' }, { e: '❗', c: 'symbol', k: '느낌표 강조 중요' }, { e: '💯', c: 'symbol', k: '백점 만점 완벽 최고' }, { e: '🎵', c: 'symbol', k: '음표 음악 뮤직' }, { e: '💤', c: 'symbol', k: '수면 잠 피곤' }, { e: '💢', c: 'symbol', k: '분노 빠직 화남' }
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
            '<button type="button" onclick="window.copyEmojiData(\'' + item.e + '\')" class="h-11 sm:h-12 flex items-center justify-center text-2xl sm:text-3xl hover:bg-pink-50 hover:scale-110 active:scale-95 rounded-xl transition-all duration-150 cursor-pointer border border-transparent hover:border-pink-100" title="' + item.k + '">' + item.e + '</button>'
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
            b.classList.remove('bg-gray-900', 'text-white', 'shadow-md');
            b.classList.add('bg-white', 'text-gray-600', 'border', 'border-gray-200');
        });
        if(btn) {
            btn.classList.remove('bg-white', 'text-gray-600', 'border', 'border-gray-200');
            btn.classList.add('bg-gray-900', 'text-white', 'shadow-md');
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
{% endraw %}
