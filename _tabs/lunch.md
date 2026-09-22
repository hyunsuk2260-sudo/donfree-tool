---
layout: page
title: "점심 메뉴 복불복 뽑기"
permalink: /lunch/
---

<script src="https://cdn.tailwindcss.com"></script>

<style>
#panel-wrapper { display: none !important; }
#core-wrapper, .col-12, .col-lg-11, .col-xl-9 { 
    max-width: 100% !important; 
    flex: 100% !important; 
}
/* 선물 상자 흔들리는 애니메이션 */
@keyframes shake {
    0%, 100% { transform: rotate(0deg); }
    25% { transform: rotate(-10deg); }
    50% { transform: rotate(10deg); }
    75% { transform: rotate(-10deg); }
}
.shake-animation {
    animation: shake 0.5s ease-in-out infinite;
}
</style>

<div class="max-w-lg mx-auto bg-white p-6 sm:p-8 rounded-3xl shadow-lg border border-gray-100 text-center mt-6" markdown="0">
    
    <!-- 1️⃣ [보내는 사람 화면] 메뉴를 뽑고 공유하는 곳 -->
    <div id="sender-view" style="display: none;">
        <h2 class="text-2xl font-extrabold text-gray-800 mb-2">오늘 뭐 먹지? 🍱</h2>
        <p class="text-gray-500 mb-6 text-sm">랜덤으로 메뉴를 뽑고 친구에게 결과를 보내세요!</p>
        
        <div class="bg-gray-50 p-6 rounded-2xl mb-6 border border-gray-100">
            <div id="roulette-box" class="text-5xl mb-4">❓</div>
            <p id="roulette-text" class="text-lg font-bold text-gray-700">어떤 메뉴가 나올까요?</p>
        </div>

        <button id="pick-btn" onclick="generateMenu()" class="w-full bg-blue-600 hover:bg-blue-700 text-white font-bold py-4 rounded-xl shadow-md transition-all text-lg mb-3">
            랜덤 메뉴 뽑기 🎯
        </button>

        <div id="share-box" style="display: none;" class="mt-6 p-5 bg-green-50 rounded-xl border border-green-200">
            <p class="text-sm text-green-700 font-bold mb-3">✅ 메뉴가 결정되었습니다! 결과를 친구에게 보내세요.</p>
            <button onclick="copyShareLink()" class="w-full bg-green-500 hover:bg-green-600 text-white font-bold py-3 rounded-lg shadow transition-all flex items-center justify-center gap-2">
                <span>🔗 카톡/문자로 링크 복사해서 보내기</span>
            </button>
        </div>
    </div>

    <!-- 2️⃣ [받는 사람 화면] 친구가 열어보는 곳 -->
    <div id="receiver-view" style="display: none;">
        <h2 class="text-2xl font-extrabold text-gray-800 mb-2">💌 도착한 점심 초대장</h2>
        <p class="text-gray-500 mb-8 text-sm">친구가 당신을 위해 점심 메뉴를 뽑았습니다!</p>
        
        <div id="gift-box" class="cursor-pointer" onclick="openGift()">
            <div class="text-8xl mb-6 shake-animation">🎁</div>
            <p class="text-blue-600 font-bold animate-pulse">상자를 터치해서 결과를 확인하세요!</p>
        </div>

        <div id="result-box" style="display: none;" class="transform scale-90 opacity-0 transition-all duration-500">
            <div class="bg-gradient-to-br from-blue-50 to-indigo-50 p-8 rounded-3xl border border-blue-100 shadow-inner mb-6">
                <div id="result-image" class="text-7xl mb-4 drop-shadow-md"></div>
                <h3 id="result-name" class="text-3xl font-extrabold text-blue-700"></h3>
            </div>
            
            <p class="text-gray-600 font-medium mb-6">오늘 점심은 이거 어때요? 😋</p>
            
            <button onclick="location.href='/lunch/'" class="w-full bg-gray-800 hover:bg-gray-900 text-white font-bold py-3 rounded-xl shadow transition-all">
                나도 친구한테 메뉴 뽑아주기 🚀
            </button>
        </div>
    </div>

</div>

<script>
// 71개의 상세 메뉴 데이터 (이미지 역할을 하는 이모지 포함)
const menus = [
    // 한식
    { id: 1, name: '김치찌개', img: '🍲' }, { id: 2, name: '된장찌개', img: '🍲' }, { id: 3, name: '부대찌개', img: '🥘' },
    { id: 4, name: '순두부찌개', img: '🥘' }, { id: 5, name: '동태찌개', img: '🐟' }, { id: 6, name: '청국장', img: '🍲' },
    { id: 7, name: '뼈해장국', img: '🍖' }, { id: 8, name: '순대국', img: '🥣' }, { id: 9, name: '돼지국밥', img: '🥣' },
    { id: 10, name: '소머리국밥', img: '🥣' }, { id: 11, name: '설렁탕', img: '🥣' }, { id: 12, name: '곰탕', img: '🥣' },
    { id: 13, name: '갈비탕', img: '🍖' }, { id: 14, name: '삼계탕', img: '🐔' }, { id: 15, name: '닭볶음탕', img: '🍗' },
    { id: 16, name: '제육볶음', img: '🥓' }, { id: 17, name: '오징어볶음', img: '🦑' }, { id: 18, name: '낙지볶음', img: '🐙' },
    { id: 19, name: '뚝배기불고기', img: '🍲' }, { id: 20, name: '비빔밥', img: '🥗' }, { id: 21, name: '돌솥비빔밥', img: '🥘' },
    { id: 22, name: '볶음밥', img: '🍛' }, { id: 23, name: '오므라이스', img: '🍳' }, { id: 24, name: '김치볶음밥', img: '🍛' },
    { id: 25, name: '육회비빔밥', img: '🥩' }, { id: 26, name: '보쌈정식', img: '🥬' }, { id: 27, name: '생선구이', img: '🐟' },
    { id: 28, name: '게장백반', img: '🦀' }, { id: 29, name: '칼국수', img: '🍜' }, { id: 30, name: '수제비', img: '🥣' },
    { id: 31, name: '잔치국수', img: '🍜' }, { id: 32, name: '비빔국수', img: '🍝' }, { id: 33, name: '콩국수', img: '🍜' },
    { id: 34, name: '냉면', img: '🧊' }, { id: 35, name: '쫄면', img: '🍝' },
    // 중식
    { id: 36, name: '짜장면', img: '🍜' }, { id: 37, name: '짬뽕', img: '🌶️' }, { id: 38, name: '중국식 볶음밥', img: '🍛' },
    { id: 39, name: '탕수육', img: '🍖' }, { id: 40, name: '마파두부밥', img: '🍛' }, { id: 41, name: '잡채밥', img: '🍝' },
    { id: 42, name: '유산슬밥', img: '🍲' }, { id: 43, name: '마라탕', img: '🌶️' }, { id: 44, name: '마라샹궈', img: '🥘' },
    { id: 45, name: '꿔바로우', img: '🥓' },
    // 일식
    { id: 46, name: '돈까스', img: '🍱' }, { id: 47, name: '치즈돈까스', img: '🧀' }, { id: 48, name: '생선까스', img: '🍤' },
    { id: 49, name: '우동', img: '🍜' }, { id: 50, name: '냉모밀', img: '🧊' }, { id: 51, name: '초밥', img: '🍣' },
    { id: 52, name: '회덮밥', img: '🐟' }, { id: 53, name: '가츠동', img: '🍛' }, { id: 54, name: '사케동', img: '🍣' },
    { id: 55, name: '카레라이스', img: '🍛' }, { id: 56, name: '라멘', img: '🍜' },
    // 양식
    { id: 57, name: '토마토파스타', img: '🍝' }, { id: 58, name: '크림파스타', img: '🍝' }, { id: 59, name: '로제파스타', img: '🍝' },
    { id: 60, name: '봉골레파스타', img: '🍝' }, { id: 61, name: '피자', img: '🍕' }, { id: 62, name: '수제버거', img: '🍔' },
    { id: 63, name: '샌드위치', img: '🥪' }, { id: 64, name: '샐러드', img: '🥗' }, { id: 65, name: '스테이크', img: '🥩' },
    // 분식 및 기타
    { id: 66, name: '떡볶이', img: '🌶️' }, { id: 67, name: '라면', img: '🍜' }, { id: 68, name: '김밥', img: '🍙' },
    { id: 69, name: '모듬튀김', img: '🍤' }, { id: 70, name: '순대', img: '🌭' }, { id: 71, name: '핫도그', img: '🌭' }
];

let generatedUrl = '';

// 주소창을 확인하여 보내는 사람 화면인지, 받는 사람 화면인지 결정합니다.
function checkMode() {
    const urlParams = new URLSearchParams(window.location.search);
    const menuId = urlParams.get('m');

    if (menuId) {
        // 'm' 값이 있으면 받는 사람(친구) 화면을 띄웁니다.
        document.getElementById('receiver-view').style.display = 'block';
    } else {
        // 'm' 값이 없으면 메뉴를 뽑는(보내는 사람) 화면을 띄웁니다.
        document.getElementById('sender-view').style.display = 'block';
    }
}

// 랜덤 메뉴를 뽑고 공유 주소를 만듭니다.
function generateMenu() {
    const btn = document.getElementById('pick-btn');
    btn.innerText = '메뉴 고르는 중... ⏳';
    btn.disabled = true;

    // 슬롯머신 효과
    let count = 0;
    const interval = setInterval(() => {
        const randomItem = menus[Math.floor(Math.random() * menus.length)];
        document.getElementById('roulette-box').innerText = randomItem.img;
        document.getElementById('roulette-text').innerText = randomItem.name;
        count++;

        if (count >= 15) {
            clearInterval(interval);
            const finalItem = menus[Math.floor(Math.random() * menus.length)];
            
            document.getElementById('roulette-box').innerText = '🤫';
            document.getElementById('roulette-text').innerText = '결과가 상자에 담겼습니다!';
            
            // 공유할 고유 주소 생성 (예: https://tool.donfree.co.kr/lunch/?m=45)
            generatedUrl = window.location.origin + window.location.pathname + '?m=' + finalItem.id;
            
            document.getElementById('share-box').style.display = 'block';
            btn.style.display = 'none'; // 뽑기 버튼 숨김
        }
    }, 100);
}

// 링크 복사 기능
function copyShareLink() {
    navigator.clipboard.writeText(generatedUrl).then(() => {
        alert('링크가 복사되었습니다! 카톡이나 문자로 친구에게 붙여넣기(공유) 해주세요.');
    }).catch(err => {
        alert('복사 실패! 아래 주소를 직접 복사해주세요.\n' + generatedUrl);
    });
}

// 친구가 상자를 열었을 때 실행되는 함수
function openGift() {
    const urlParams = new URLSearchParams(window.location.search);
    const menuId = parseInt(urlParams.get('m'));
    
    // ID로 메뉴 찾기
    const finalMenu = menus.find(m => m.id === menuId) || menus[0];

    document.getElementById('gift-box').style.display = 'none';
    
    const resultBox = document.getElementById('result-box');
    resultBox.style.display = 'block';
    
    document.getElementById('result-image').innerText = finalMenu.img;
    document.getElementById('result-name').innerText = finalMenu.name;
    
    // 짠! 하고 나타나는 애니메이션 적용
    setTimeout(() => {
        resultBox.classList.remove('scale-90', 'opacity-0');
        resultBox.classList.add('scale-100', 'opacity-100');
    }, 50);
}

// 페이지 로드 시 즉시 모드 확인
document.addEventListener('DOMContentLoaded', checkMode);
</script>
