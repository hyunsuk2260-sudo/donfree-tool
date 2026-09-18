---
layout: page
icon: fas fa-star
title: 🔮 오늘의 타로
order: 6
permalink: /tarot/
---
<div id="tarot-app-container" markdown="0">
<script src="https://cdn.tailwindcss.com"></script>
<div class="bg-[#1a1a1a] text-white p-4 sm:p-8 rounded-2xl shadow-xl max-w-3xl mx-auto text-center mt-6 border border-gray-800">
<h2 class="text-2xl sm:text-3xl font-bold mb-2 text-purple-400">오늘의 운명 타로</h2>
<p class="text-gray-400 mb-6 text-xs sm:text-sm">마음속으로 질문을 3번 떠올린 후, 직감적으로 가장 끌리는 카드를 하나 뽑아보세요.</p>
<!-- 78장 카드 영역 -->
<div id="card-selection-area" class="flex flex-wrap justify-center gap-2 sm:gap-3 mb-4"></div>
<!-- 결과 화면 영역 -->
<div id="result-area" class="hidden mt-4 animate-fade-in">
<div class="inline-block p-1 bg-gradient-to-r from-yellow-400 to-yellow-600 rounded-xl mb-6 shadow-lg transform transition-all duration-500 hover:scale-105">
<div class="bg-gray-900 p-6 rounded-lg w-48 sm:w-56 mx-auto">
<div id="card-emoji" class="text-6xl sm:text-7xl mb-4 drop-shadow-md">🃏</div>
<h3 id="card-name" class="text-lg sm:text-xl font-bold text-yellow-400 font-serif">카드 이름</h3>
</div>
</div>
<div class="bg-gray-800 p-5 sm:p-6 rounded-xl border border-gray-700 text-left shadow-inner">
<h4 class="text-base sm:text-lg font-bold text-green-400 mb-2 flex items-center"><span class="mr-2">💡</span> 카드의 의미</h4>
<p id="card-meaning" class="text-gray-300 text-sm sm:text-base mb-5 leading-relaxed break-keep"></p>
<h4 class="text-base sm:text-lg font-bold text-blue-400 mb-2 flex items-center"><span class="mr-2">🤖</span> AI의 맞춤 조언</h4>
<p id="card-advice" class="text-gray-300 text-sm sm:text-base leading-relaxed break-keep"></p>
</div>
<button onclick="window.resetTarot()" class="mt-8 px-8 py-3 bg-gradient-to-r from-purple-600 to-indigo-600 hover:from-purple-500 hover:to-indigo-500 text-white font-bold rounded-full transition-all shadow-md hover:shadow-lg transform hover:-translate-y-1">다른 질문으로 다시 뽑기 ↻</button>
</div>
</div>
<style>
@keyframes fadeIn { from { opacity: 0; transform: translateY(15px); } to { opacity: 1; transform: translateY(0); } }
.animate-fade-in { animation: fadeIn 0.5s ease-out forwards; }
</style>
<script>
// 웹페이지 뼈대가 완전히 다 로딩된 후에 안전하게 카드를 깔도록 순서 보장
document.addEventListener("DOMContentLoaded", function() {
    const tarotDeck = [
        { name: "0. 바보 (The Fool)", emoji: "🚶‍♂️", meaning: "새로운 시작, 얽매이지 않는 자유, 무한한 가능성, 뜻밖의 모험", advice: "너무 완벽하게 준비하려 하지 마세요. 때로는 머리보다 가슴이 이끄는 대로 과감하게 첫발을 내디뎌 보는 것이 정답일 수 있습니다." },
        { name: "1. 마법사 (The Magician)", emoji: "🧙‍♂️", meaning: "무에서 유를 창조하는 힘, 자신감, 다재다능, 뛰어난 소통 능력", advice: "당신에게는 이미 상황을 변화시킬 충분한 재능과 도구가 갖춰져 있습니다. 스스로의 능력을 의심하지 말고 적극적으로 행동하세요." },
        { name: "2. 고위 여사제 (The Priestess)", emoji: "🧝‍♀️", meaning: "뛰어난 직관력, 통찰, 기다림, 숨겨진 지혜와 비밀", advice: "당장 눈앞에 보이는 현실보다, 당신의 직관과 내면의 목소리에 귀를 기울여야 할 때입니다. 섣부른 행동보다는 관망하세요." },
        { name: "3. 여황제 (The Empress)", emoji: "👸", meaning: "물질적 풍요, 모성애, 결실, 매력과 아름다움, 편안함", advice: "치열하게 경쟁하기보다 여유를 가지세요. 주변을 따뜻하게 돌보고, 다가오는 풍요로운 결실을 기쁘고 편안하게 받아들일 시기입니다." },
        { name: "4. 황제 (The Emperor)", emoji: "🤴", meaning: "권위, 확고한 체계, 책임감, 흔들리지 않는 안정, 리더십", advice: "감정에 휘둘려서는 안 됩니다. 철저하게 이성적이고 현실적인 판단이 필요하며, 규칙을 세우고 주도적으로 상황을 장악하세요." },
        { name: "5. 교황 (The Hierophant)", emoji: "🏛️", meaning: "전통, 교육, 신뢰할 수 있는 멘토, 정신적인 가르침", advice: "혼자서 끙끙 앓으며 해결하려 하지 마세요. 경험이 많은 전문가, 혹은 믿을 수 있는 윗사람에게 조언을 구하는 것이 가장 빠른 길입니다." },
        { name: "6. 연인 (The Lovers)", emoji: "💞", meaning: "사랑, 완벽한 조화, 중요한 갈림길에서의 선택, 강렬한 끌림", advice: "진심이 담긴 소통과 마음이 잘 맞는 사람과의 협력이 행운을 가져옵니다. 머리보다는 마음이 진정으로 끌리는 선택을 하세요." },
        { name: "7. 전차 (The Chariot)", emoji: "🐎", meaning: "강력한 추진력, 승리, 자신감, 내적 갈등의 극복과 전진", advice: "목표를 정했다면 장애물이 있어도 절대 망설이거나 브레이크를 밟지 마세요. 강하게 밀고 나가면 결국 승리는 당신의 것입니다." },
        { name: "8. 힘 (Strength)", emoji: "🦁", meaning: "부드러운 카리스마, 흔들리지 않는 인내심, 내면의 강인한 용기", advice: "상대를 힘으로 억누르려 하거나 강압적인 태도를 취하면 역효과가 납니다. 따뜻한 인내와 부드러운 포용력이 결국 가장 큰 힘을 발휘합니다." },
        { name: "9. 은둔자 (The Hermit)", emoji: "🏮", meaning: "내면의 탐구, 신중함, 고독을 통한 깨달음, 지혜", advice: "지금은 밖으로 나서기보다 혼자만의 시간을 가지며 생각을 정리할 때입니다. 내면의 소리에 집중하면 답을 찾을 수 있습니다." },
        { name: "10. 운명의 수레바퀴", emoji: "🎡", meaning: "인생의 전환점, 피할 수 없는 긍정적 변화, 행운, 완벽한 타이밍", advice: "상황이 당신에게 유리한 쪽으로 흘러가기 시작했습니다. 이 다가오는 기회와 변화의 큰 흐름에 자연스럽게 몸을 맡기고 즐기세요." },
        { name: "19. 태양 (The Sun)", emoji: "☀️", meaning: "눈부신 성공, 긍정적인 에너지, 생명력, 축하받을 일", advice: "가장 긍정적이고 밝은 기운이 함께하고 있습니다. 고민하던 일이 있다면 눈녹듯 사라지고 좋은 결과가 기다리고 있으니 활기차게 움직이세요." }
    ];

    function renderCards() {
        const container = document.getElementById('card-selection-area');
        if(!container) return; // 방어 코드
        container.innerHTML = ''; 
        
        for(let i = 0; i < 78; i++) {
            const cardElement = document.createElement('div');
            cardElement.className = "w-9 h-14 sm:w-12 sm:h-20 bg-gradient-to-br from-indigo-600 via-purple-700 to-pink-600 rounded border border-yellow-500 shadow-md flex items-center justify-center cursor-pointer hover:-translate-y-2 hover:shadow-lg transition-all duration-200 flex-shrink-0";
            cardElement.innerHTML = '<span class="text-[10px] sm:text-xs opacity-40 text-white">✨</span>';
            
            cardElement.addEventListener('click', function() {
                document.getElementById('card-selection-area').style.display = 'none';
                document.getElementById('result-area').style.display = 'block';
                
                const randomIndex = Math.floor(Math.random() * tarotDeck.length);
                const pickedCard = tarotDeck[randomIndex];
                
                document.getElementById('card-emoji').innerText = pickedCard.emoji;
                document.getElementById('card-name').innerText = pickedCard.name;
                document.getElementById('card-meaning').innerText = pickedCard.meaning;
                document.getElementById('card-advice').innerText = pickedCard.advice;
            });
            
            container.appendChild(cardElement);
        }
    }
    
    renderCards();

    window.resetTarot = function() {
        document.getElementById('result-area').style.display = 'none';
        document.getElementById('card-selection-area').style.display = 'flex';
    };
});
</script>
</div>
