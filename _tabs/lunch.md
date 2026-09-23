---
layout: page
title: "🎁 도착한 점심 초대장"
description: "친구가 당신을 위해 점심 메뉴를 뽑았습니다! 상자를 터치해서 결과를 확인하세요."
image:
  path: "https://images.unsplash.com/photo-1549465220-1a8b9238cd48?q=80&w=1200&auto=format&fit=crop"
permalink: /lunch/
---

<style>

.lunch-page {
  max-width: 760px;
  margin: 0 auto;
  padding: 10px 15px 60px;
  text-align: center;
}

.lunch-title {
  font-size: 30px;
  font-weight: 800;
  margin: 10px 0 8px;
}

.lunch-desc {
  color: #777;
  font-size: 15px;
  margin-bottom: 28px;
}

.lunch-card {
  background: #fff;
  border-radius: 24px;
  padding: 30px 20px;
  box-shadow: 0 8px 30px rgba(0,0,0,.08);
  border: 1px solid #eee;
}

.menu-photo {
  width: 240px;
  height: 240px;
  margin: 0 auto 22px;
  border-radius: 22px;
  overflow: hidden;
  background: #f5f5f5;
  display: flex;
  align-items: center;
  justify-content: center;
}

.menu-photo img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.menu-photo-fallback {
  font-size: 80px;
}

.menu-name {
  font-size: 28px;
  font-weight: 800;
  margin: 8px 0 20px;
}

.lunch-button {
  width: 100%;
  max-width: 360px;
  border: 0;
  border-radius: 14px;
  padding: 16px 20px;
  font-size: 17px;
  font-weight: 700;
  cursor: pointer;
  margin: 5px auto;
}

.pick-button {
  background: #111;
  color: #fff;
}

.copy-button {
  background: #f1f1f1;
  color: #111;
}

.reset-button {
  background: #f7f7f7;
  color: #555;
}

.lunch-button:active {
  transform: scale(.98);
}

.gift-box {
  font-size: 110px;
  line-height: 1;
  cursor: pointer;
  margin: 30px auto;
  transition: transform .2s;
}

.gift-box:hover {
  transform: scale(1.05);
}

.gift-box.opening {
  animation: giftShake .7s ease;
}

@keyframes giftShake {

  0%,100% {
    transform: rotate(0);
  }

  20% {
    transform: rotate(-8deg) scale(1.05);
  }

  40% {
    transform: rotate(8deg) scale(1.05);
  }

  60% {
    transform: rotate(-6deg) scale(1.05);
  }

  80% {
    transform: rotate(6deg) scale(1.05);
  }

}

.result-box {
  display: none;
}

.result-box.show {
  display: block;
  animation: resultShow .5s ease;
}

@keyframes resultShow {

  from {
    opacity: 0;
    transform: translateY(15px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }

}

.result-title {
  font-size: 17px;
  color: #777;
  margin-bottom: 12px;
}

.share-box {
  display: none;
  margin-top: 25px;
  padding-top: 25px;
  border-top: 1px solid #eee;
}

.share-box.show {
  display: block;
}

.share-title {
  font-size: 16px;
  font-weight: 700;
  margin-bottom: 10px;
}

.share-url {
  background: #f6f6f6;
  border-radius: 10px;
  padding: 12px;
  font-size: 12px;
  word-break: break-all;
  color: #666;
  margin-bottom: 10px;
}

.loading-text {
  font-size: 18px;
  font-weight: 700;
  margin-top: 10px;
  min-height: 28px;
}

.hidden {
  display: none !important;
}

@media (max-width: 600px) {

  .lunch-card {
    padding: 25px 15px;
  }

  .lunch-title {
    font-size: 25px;
  }

  .menu-photo {
    width: 210px;
    height: 210px;
  }

  .menu-name {
    font-size: 25px;
  }

}

</style>


<div class="lunch-page">

  <div class="lunch-title">
    🎁 도착한 점심 초대장
  </div>

  <div class="lunch-desc">
    오늘 점심 메뉴를 친구가 골라줬어요.
  </div>


  <!-- 보내는 사람 화면 -->

  <div id="sender-view" class="lunch-card">

    <div id="sender-photo" class="menu-photo"></div>

    <div id="sender-menu-name" class="menu-name">
      오늘의 점심은?
    </div>

    <div id="loading-text" class="loading-text"></div>

    <button
      id="pick-button"
      class="lunch-button pick-button"
      type="button">
      🎲 점심 메뉴 뽑기
    </button>


    <div id="share-box" class="share-box">

      <div class="share-title">
        🎁 친구에게 이 점심을 보내보세요
      </div>

      <div id="share-url" class="share-url"></div>

      <button
        id="copy-button"
        class="lunch-button copy-button"
        type="button">
        🔗 링크 복사하기
      </button>

      <button
        id="reset-button"
        class="lunch-button reset-button"
        type="button">
        🔄 다시 뽑기
      </button>

    </div>

  </div>


  <!-- 받는 사람 화면 -->

  <div id="receiver-view" class="lunch-card hidden">

    <div id="gift-box" class="gift-box">
      🎁
    </div>

    <div id="gift-guide">
      친구가 점심 메뉴를 골라줬어요.<br>
      선물 상자를 눌러 확인해보세요!
    </div>


    <div id="result-box" class="result-box">

      <div class="result-title">
        오늘 친구가 골라준 메뉴는
      </div>

      <div id="result-photo" class="menu-photo"></div>

      <div id="result-menu-name" class="menu-name"></div>

      <button
        id="new-lunch-button"
        class="lunch-button pick-button"
        type="button">
        🍚 나도 점심 메뉴 뽑기
      </button>

    </div>

  </div>

</div>


<script data-proofer-ignore>

(function () {

  /*
   * ==========================================
   * 점심 메뉴
   * ==========================================
   */

  const menus = [

    { id: 1,  name: "김치찌개",     emoji: "🍲" },
    { id: 2,  name: "된장찌개",     emoji: "🍲" },
    { id: 3,  name: "부대찌개",     emoji: "🍲" },
    { id: 4,  name: "순두부찌개",   emoji: "🍲" },
    { id: 5,  name: "동태찌개",     emoji: "🍲" },
    { id: 6,  name: "청국장",       emoji: "🍲" },
    { id: 7,  name: "뼈해장국",     emoji: "🍲" },
    { id: 8,  name: "순대국",       emoji: "🍲" },
    { id: 9,  name: "꼬리곰탕",     emoji: "🍲" },
    { id: 10, name: "뼈리곰탕",     emoji: "🍲" },

    { id: 11, name: "설렁탕",       emoji: "🍲" },
    { id: 12, name: "곰탕",         emoji: "🍲" },
    { id: 13, name: "갈비탕",       emoji: "🍲" },
    { id: 14, name: "삼계탕",       emoji: "🍗" },
    { id: 15, name: "닭볶음탕",     emoji: "🍗" },
    { id: 16, name: "제육볶음",     emoji: "🥘" },
    { id: 17, name: "오징어볶음",   emoji: "🦑" },
    { id: 18, name: "뚝배기불고기", emoji: "🥘" },
    { id: 19, name: "불고기",       emoji: "🥩" },
    { id: 20, name: "비빔밥",       emoji: "🍚" },

    { id: 21, name: "돌솥비빔밥",   emoji: "🍚" },
    { id: 22, name: "볶음밥",       emoji: "🍚" },
    { id: 23, name: "오므라이스",   emoji: "🍳" },
    { id: 24, name: "김치볶음밥",   emoji: "🍚" },
    { id: 25, name: "육회비빔밥",   emoji: "🥩" },
    { id: 26, name: "보쌈정식",     emoji: "🥩" },
    { id: 27, name: "생선구이",     emoji: "🐟" },
    { id: 28, name: "게장백반",     emoji: "🦀" },
    { id: 29, name: "제육정식",     emoji: "🥘" },
    { id: 30, name: "수제비",       emoji: "🍲" },

    { id: 31, name: "잔치국수",     emoji: "🍜" },
    { id: 32, name: "비빔국수",     emoji: "🍜" },
    { id: 33, name: "콩국수",       emoji: "🍜" },
    { id: 34, name: "냉면",         emoji: "🍜" },
    { id: 35, name: "쫄면",         emoji: "🍜" },
    { id: 36, name: "짜장면",       emoji: "🍜" },
    { id: 37, name: "짬뽕",         emoji: "🍜" },
    { id: 38, name: "중국식 볶음밥", emoji: "🍚" },
    { id: 39, name: "탕수육",       emoji: "🥩" },
    { id: 40, name: "마파두부밥",   emoji: "🍚" },

    { id: 41, name: "잡채밥",       emoji: "🍚" },
    { id: 42, name: "유산슬밥",     emoji: "🍚" },
    { id: 43, name: "마라탕",       emoji: "🍲" },
    { id: 44, name: "마라샹궈",     emoji: "🥘" },
    { id: 45, name: "꿔바로우",     emoji: "🥩" },
    { id: 46, name: "돈까스",       emoji: "🍱" },
    { id: 47, name: "치즈돈까스",   emoji: "🧀" },
    { id: 48, name: "생선까스",     emoji: "🐟" },
    { id: 49, name: "치킨까스",     emoji: "🍗" },
    { id: 50, name: "냉모밀",       emoji: "🍜" },

    { id: 51, name: "초밥",         emoji: "🍣" },
    { id: 52, name: "회덮밥",       emoji: "🍚" },
    { id: 53, name: "가츠동",       emoji: "🍚" },
    { id: 54, name: "사케동",       emoji: "🍣" },
    { id: 55, name: "카레라이스",   emoji: "🍛" },
    { id: 56, name: "라멘",         emoji: "🍜" },
    { id: 57, name: "토마토파스타", emoji: "🍝" },
    { id: 58, name: "크림파스타",   emoji: "🍝" },
    { id: 59, name: "알리오올리오", emoji: "🍝" },
    { id: 60, name: "봉골레파스타", emoji: "🍝" },

    { id: 61, name: "피자",         emoji: "🍕" },
    { id: 62, name: "수제버거",     emoji: "🍔" },
    { id: 63, name: "샌드위치",     emoji: "🥪" },
    { id: 64, name: "샐러드",       emoji: "🥗" },
    { id: 65, name: "스테이크",     emoji: "🥩" },
    { id: 66, name: "떡볶이",       emoji: "🌶️" },
    { id: 67, name: "라면",         emoji: "🍜" },
    { id: 68, name: "김밥",         emoji: "🍙" },
    { id: 69, name: "모듬튀김",     emoji: "🍤" },
    { id: 70, name: "순대",         emoji: "🥢" },
    { id: 71, name: "핫도그",       emoji: "🌭" }

  ];


  /*
   * ==========================================
   * 이미지 자동 연결
   * ==========================================
   *
   * 1번 → 01.jpg
   * 2번 → 02.jpg
   * ...
   * 71번 → 71.jpg
   *
   */

  menus.forEach(function (menu) {

    menu.img =
      "/assets/img/lunch/" +
      String(menu.id).padStart(2, "0") +
      ".jpg";

  });


  /*
   * ==========================================
   * 요소
   * ==========================================
   */

  const senderView =
    document.getElementById("sender-view");

  const receiverView =
    document.getElementById("receiver-view");

  const senderPhoto =
    document.getElementById("sender-photo");

  const senderMenuName =
    document.getElementById("sender-menu-name");

  const resultPhoto =
    document.getElementById("result-photo");

  const resultMenuName =
    document.getElementById("result-menu-name");

  const pickButton =
    document.getElementById("pick-button");

  const shareBox =
    document.getElementById("share-box");

  const shareUrl =
    document.getElementById("share-url");

  const copyButton =
    document.getElementById("copy-button");

  const resetButton =
    document.getElementById("reset-button");

  const giftBox =
    document.getElementById("gift-box");

  const giftGuide =
    document.getElementById("gift-guide");

  const resultBox =
    document.getElementById("result-box");

  const newLunchButton =
    document.getElementById("new-lunch-button");


  /*
   * ==========================================
   * 음식 사진 표시
   * ==========================================
   */

  function showMenuPhoto(container, menu) {

    container.innerHTML = "";

    const img =
      document.createElement("img");

    img.src = menu.img;
    img.alt = menu.name;
    img.loading = "eager";

    img.onerror = function () {

      container.innerHTML = "";

      const fallback =
        document.createElement("div");

      fallback.className =
        "menu-photo-fallback";

      fallback.textContent =
        menu.emoji || "🍽️";

      container.appendChild(fallback);

    };

    container.appendChild(img);

  }


  /*
   * ==========================================
   * URL 확인
   * ==========================================
   */

  const params =
    new URLSearchParams(
      window.location.search
    );

  const menuId =
    params.get("m");


  /*
   * ==========================================
   * 받는 사람 화면
   * ==========================================
   */

  function openReceiver(menu) {

    senderView.classList.add("hidden");

    receiverView.classList.remove("hidden");

    giftBox.addEventListener(
      "click",
      function () {

        giftBox.classList.add("opening");

        setTimeout(function () {

          giftBox.classList.add("hidden");

          giftGuide.classList.add("hidden");

          showMenuPhoto(
            resultPhoto,
            menu
          );

          resultMenuName.textContent =
            menu.name;

          resultBox.classList.add("show");

        }, 650);

      }
    );

  }


  /*
   * ==========================================
   * 점심 메뉴 뽑기
   * ==========================================
   */

  function pickMenu() {

    pickButton.disabled = true;

    shareBox.classList.remove("show");

    let count = 0;

    const animation =
      setInterval(function () {

        const randomIndex =
          Math.floor(
            Math.random() * menus.length
          );

        const randomMenu =
          menus[randomIndex];

        showMenuPhoto(
          senderPhoto,
          randomMenu
        );

        senderMenuName.textContent =
          randomMenu.name;

        count++;

        if (count >= 12) {

          clearInterval(animation);

          setTimeout(function () {

            const finalIndex =
              Math.floor(
                Math.random() * menus.length
              );

            const finalMenu =
              menus[finalIndex];

            showMenuPhoto(
              senderPhoto,
              finalMenu
            );

            senderMenuName.textContent =
              finalMenu.name;

            const generatedUrl =
              window.location.origin +
              window.location.pathname +
              "?m=" +
              finalMenu.id;

            shareUrl.textContent =
              generatedUrl;

            shareBox.classList.add("show");

            window.lunchGeneratedUrl =
              generatedUrl;

            pickButton.disabled = false;

          }, 300);

        }

      }, 100);

  }


  /*
   * ==========================================
   * 링크 복사
   * ==========================================
   */

  function copyLink() {

    const url =
      window.lunchGeneratedUrl;

    if (!url) return;

    if (
      navigator.clipboard &&
      navigator.clipboard.writeText
    ) {

      navigator.clipboard
        .writeText(url)
        .then(function () {

          copyButton.textContent =
            "✅ 링크가 복사됐어요!";

          setTimeout(function () {

            copyButton.textContent =
              "🔗 링크 복사하기";

          }, 1800);

        })
        .catch(function () {

          fallbackCopy(url);

        });

    } else {

      fallbackCopy(url);

    }

  }


  /*
   * ==========================================
   * 복사 기능 보조
   * ==========================================
   */

  function fallbackCopy(text) {

    const textarea =
      document.createElement("textarea");

    textarea.value = text;

    textarea.style.position =
      "fixed";

    textarea.style.opacity =
      "0";

    document.body.appendChild(
      textarea
    );

    textarea.select();

    try {

      document.execCommand("copy");

      copyButton.textContent =
        "✅ 링크가 복사됐어요!";

    } catch (e) {

      copyButton.textContent =
        "링크를 직접 복사해주세요.";

    }

    document.body.removeChild(
      textarea
    );

  }


  /*
   * ==========================================
   * 다시 뽑기
   * ==========================================
   */

  function resetLunch() {

    window.location.href =
      window.location.pathname;

  }


  /*
   * ==========================================
   * 새 메뉴 뽑기
   * ==========================================
   */

  function newLunch() {

    window.location.href =
      window.location.pathname;

  }


  /*
   * ==========================================
   * 버튼 이벤트
   * ==========================================
   */

  pickButton.addEventListener(
    "click",
    pickMenu
  );

  copyButton.addEventListener(
    "click",
    copyLink
  );

  resetButton.addEventListener(
    "click",
    resetLunch
  );

  newLunchButton.addEventListener(
    "click",
    newLunch
  );


  /*
   * ==========================================
   * 첫 화면
   * ==========================================
   */

  if (menuId) {

    const selectedMenu =
      menus.find(function (menu) {

        return String(menu.id) ===
          String(menuId);

      });

    if (selectedMenu) {

      openReceiver(selectedMenu);

    } else {

      senderView.classList.remove(
        "hidden"
      );

      receiverView.classList.add(
        "hidden"
      );

    }

  } else {

    senderView.classList.remove(
      "hidden"
    );

    receiverView.classList.add(
      "hidden"
    );

    showMenuPhoto(
      senderPhoto,
      menus[0]
    );

  }

})();

</script>
