---
title: 트렌디 폰트 툴
icon: fas fa-font
order: 11
layout: page
permalink: /font-tool/
---

{% raw %}
<style>
@import url('https://fonts.googleapis.com/css2?family=Black+Han+Sans&family=Do+Hyeon&family=Dongle:wght@400;700&family=Gowun+Dodum&family=Jua&family=Noto+Sans+KR:wght@400;700&family=Single+Day&display=swap');
@import url("https://fastly.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.min.css");

/* 와일드각체 & 꾸불림체(KOTRA 손글씨) 정밀 복구 주소 */
@font-face { font-family: 'WAGAK'; src: url('https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_2307-2@1.0/WAGAK.woff2') format('woff2'); font-weight: normal; font-style: normal; }
@font-face { font-family: 'KOTRA_BOLD'; src: url('https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_20-10@1.0/KOTRA_BOLD.woff') format('woff'); font-weight: normal; font-style: normal; }
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

.font-wagak { font-family: 'WAGAK', sans-serif; }
.font-kotra { font-family: 'KOTRA_BOLD', sans-serif; }
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

<div class="bg-gray-50 text-gray-800 flex flex-col" style="min-height: 80vh;">
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
            
            <!-- 와일드각체 -->
            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">와일드각체 (인스타 릴스 핫템 🔥)</div><div class="font-wagak text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://noonnu.cc/font_page/642" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <!-- 꾸불림체 -->
            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">꾸불림체 (감성 자막 찰떡 ✏️)</div><div class="font-kotra text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://noonnu.cc/font_page/454" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">제주돌담체 (감성 릴스 추천)</div><div class="font-jeju text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://noonnu.cc/font_page/1057" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">더잠실체 (모던하고 세련된)</div><div class="font-jamsil text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://noonnu.cc/font_page/1138" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">여기어때 잘난체 (썸네일 어그로 탑)</div><div class="font-jalnan text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://noonnu.cc/font_page/227" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">티몬 몬소리체 (유튜브 자막 1티어)</div><div class="font-tmon text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://noonnu.cc/font_page/208" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">프리텐다드 (가장 완벽한 기본 폰트)</div><div class="font-pretendard text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://noonnu.cc/font_page/835" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">어그로체 (이름값 하는 독특함)</div><div class="font-aggro text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://noonnu.cc/font_page/739" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">카페24 써라운드 (뷰티/브이로그)</div><div class="font-cafe24 text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://noonnu.cc/font_page/703" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">쿠키런체 (동글동글 귀여운)</div><div class="font-cookierun text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://noonnu.cc/font_page/396" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">G마켓 산스 (신뢰감 주는 고딕)</div><div class="font-gmarket text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://noonnu.cc/font_page/463" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">KCC 은영체 (진짜 손글씨 감성)</div><div class="font-eunyoung text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://noonnu.cc/font_page/197" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">창원단감아삭체 (톡톡 튀는 타이틀)</div><div class="font-dangam text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://noonnu.cc/font_page/431" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">조선100년체 (진지한 다큐/명조)</div><div class="font-chosun text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://noonnu.cc/font_page/1000" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">빙그레체 (따뜻하고 포근한)</div><div class="font-binggrae text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://noonnu.cc/font_page/158" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">배달의민족 도현체 (레트로 간판 느낌)</div><div class="font-dohyeon text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://fonts.google.com/specimen/Do+Hyeon" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">검은고딕 (굵직하고 강렬한)</div><div class="font-blackhan text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://fonts.google.com/specimen/Black+Han+Sans" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">배달의민족 주아체 (붓글씨 귀여움)</div><div class="font-jua text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://fonts.google.com/specimen/Jua" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">고운 돋움 (잔잔한 브이로그 자막)</div><div class="font-gowun text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://fonts.google.com/specimen/Gowun+Dodum" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">싱글데이체 (다이어리 꾸미기)</div><div class="font-singleday text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://fonts.google.com/specimen/Single+Day" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">동글체 (작고 앙증맞은)</div><div class="font-dongle text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://fonts.google.com/specimen/Dongle" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

            <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm flex flex-col justify-between">
                <div><div class="text-xs text-gray-500 mb-4 font-bold">노토 산스 KR (구글 기본 고딕)</div><div class="font-noto text-3xl text-gray-900 mb-6 preview-text" style="min-height:4.5rem;">구독과 좋아요 부탁드립니다!</div></div>
                <a href="https://fonts.google.com/specimen/Noto+Sans+KR" target="_blank" class="w-full text-center block px-4 py-3 bg-gray-900 text-white rounded-xl text-sm font-bold hover:bg-purple-600 transition-colors">폰트 다운로드 가기</a>
            </div>

        </div>
    </main>
</div>

<!-- 광고 영역 -->
<div style="text-align: center; margin: 40px 0; min-height: 100px; clear: both;">
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
</div>

<script>
    var input = document.getElementById('previewInput');
    if (input) {
        input.addEventListener('input', function() {
            var val = this.value || '테스트 문구를 입력하세요';
            var targets = document.getElementsByClassName('preview-text');
            for (var i = 0; i < targets.length; i++) {
                targets[i].innerText = val;
            }
        });
    }
</script>
{% endraw %}
