---
layout: page
title: 글쓰기
icon: fas fa-pen
order: 10
---

<style>
.write-wrap {
  max-width: 1000px;
  margin: 0 auto;
}

.write-box {
  margin-bottom: 25px;
}

.write-label {
  display: block;
  font-weight: 700;
  margin-bottom: 8px;
}

.write-input {
  width: 100%;
  box-sizing: border-box;
  padding: 13px;
  border: 1px solid #d9d9d9;
  border-radius: 8px;
  font-size: 15px;
  background: white;
}

.write-input:focus,
.write-body:focus {
  outline: none;
  border-color: #777;
}

.write-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 15px;
}

.write-body {
  width: 100%;
  min-height: 550px;
  box-sizing: border-box;
  padding: 18px;
  border: 1px solid #d9d9d9;
  border-radius: 8px;
  font-size: 16px;
  line-height: 1.8;
  resize: vertical;
  font-family: inherit;
  background: white;
}

.image-upload {
  padding: 18px;
  border: 1px dashed #bbb;
  border-radius: 8px;
  background: #fafafa;
}

.image-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  gap: 15px;
  margin-top: 18px;
}

.image-card {
  background: white;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 8px;
}

.image-card img {
  width: 100%;
  height: 140px;
  object-fit: cover;
  border-radius: 5px;
  display: block;
}

.image-name {
  font-size: 12px;
  margin: 8px 2px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.image-buttons {
  display: flex;
  gap: 5px;
}

.image-buttons button {
  flex: 1;
  padding: 7px 4px;
  border: 1px solid #ddd;
  background: white;
  border-radius: 5px;
  cursor: pointer;
  font-size: 12px;
}

.image-buttons button:hover {
  background: #f3f3f3;
}

.featured {
  font-size: 11px;
  font-weight: bold;
  margin-top: 5px;
}

.featured-preview {
  margin-top: 12px;
}

.featured-preview img {
  width: 220px;
  max-height: 160px;
  object-fit: cover;
  border-radius: 6px;
}

.toolbar {
  display: flex;
  gap: 7px;
  flex-wrap: wrap;
  margin-bottom: 8px;
}

.toolbar button,
.action-button {
  padding: 9px 13px;
  border: 1px solid #d5d5d5;
  background: white;
  border-radius: 7px;
  cursor: pointer;
}

.toolbar button:hover,
.action-button:hover {
  background: #f3f3f3;
}

.primary {
  background: #222 !important;
  color: white !important;
  border-color: #222 !important;
}

.button-row {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
  margin-top: 20px;
}

.preview {
  display: none;
  margin-top: 30px;
  padding: 25px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background: white;
}

.preview-title {
  font-size: 30px;
  font-weight: 800;
  margin-bottom: 25px;
}

.preview-content {
  font-size: 16px;
  line-height: 1.8;
}

.preview-content img {
  max-width: 100%;
  height: auto;
  display: block;
  margin: 20px auto;
}

.help {
  font-size: 12px;
  color: #777;
  margin-top: 6px;
}

.status {
  margin-top: 10px;
  font-size: 13px;
  color: #555;
}

@media (max-width: 700px) {

  .write-grid {
    grid-template-columns: 1fr;
  }

  .write-body {
    min-height: 450px;
  }

  .image-list {
    grid-template-columns: repeat(2, 1fr);
  }

}
</style>


<div class="write-wrap">

  <!-- 제목 -->
  <div class="write-box">

    <label class="write-label">제목</label>

    <input
      id="title"
      class="write-input"
      type="text"
      placeholder="글 제목을 입력하세요"
    >

  </div>


  <!-- 기본 정보 -->
  <div class="write-box write-grid">

    <div>

      <label class="write-label">URL</label>

      <input
        id="slug"
        class="write-input"
        type="text"
        placeholder="예: instagram-reels-download"
      >

    </div>

    <div>

      <label class="write-label">카테고리</label>

      <input
        id="category"
        class="write-input"
        type="text"
        placeholder="예: 생활정보"
      >

    </div>

  </div>


  <!-- 태그 -->
  <div class="write-box">

    <label class="write-label">태그</label>

    <input
      id="tags"
      class="write-input"
      type="text"
      placeholder="예: 인스타, 릴스, 다운로드"
    >

  </div>


  <!-- SEO -->
  <div class="write-box write-grid">

    <div>

      <label class="write-label">SEO 제목</label>

      <input
        id="seoTitle"
        class="write-input"
        type="text"
        placeholder="검색 결과에 표시될 제목"
      >

    </div>

    <div>

      <label class="write-label">SEO 설명</label>

      <input
        id="seoDescription"
        class="write-input"
        type="text"
        placeholder="검색 결과에 표시될 설명"
      >

    </div>

  </div>


  <!-- 대표 이미지 -->
  <div class="write-box">

    <label class="write-label">대표 이미지</label>

    <div class="image-upload">

      <input
        id="featuredInput"
        type="file"
        accept="image/*"
      >

      <div class="help">
        아래 본문 이미지 중 하나를 대표 이미지로 지정할 수도 있습니다.
      </div>

      <div
        id="featuredPreview"
        class="featured-preview"
      ></div>

    </div>

  </div>


  <!-- 본문 -->
  <div class="write-box">

    <label class="write-label">본문</label>

    <div class="toolbar">

      <button type="button" id="boldButton">
        굵게
      </button>

      <button type="button" id="headingButton">
        소제목
      </button>

      <button type="button" id="linkButton">
        링크
      </button>

    </div>


    <!-- ★ 실제 글을 쓰는 공간 -->
    <textarea
      id="body"
      class="write-body"
      placeholder="여기에 글을 작성하세요.

예:
인스타 릴스를 저장하고 싶은데
앱을 설치해야 하는 경우가 많죠.

오늘은 별도 앱 없이
간단하게 저장하는 방법을 정리해볼게요."
    ></textarea>

  </div>


  <!-- 본문 이미지 -->
  <div class="write-box">

    <label class="write-label">
      본문 이미지
    </label>

    <div class="image-upload">

      <input
        id="imageInput"
        type="file"
        accept="image/*"
        multiple
      >

      <div class="help">
        사진을 여러 장 선택하면 아래에 사진이 바로 표시됩니다.
        원하는 사진의 「본문에 넣기」를 눌러주세요.
      </div>

      <div
        id="imageList"
        class="image-list"
      ></div>

    </div>

  </div>


  <!-- 버튼 -->
  <div class="button-row">

    <button
      id="previewButton"
      class="action-button"
      type="button"
    >
      미리보기
    </button>

    <button
      id="saveButton"
      class="action-button"
      type="button"
    >
      임시저장
    </button>

    <button
      id="downloadButton"
      class="action-button primary"
      type="button"
    >
      Markdown 다운로드
    </button>

    <button
      id="clearButton"
      class="action-button"
      type="button"
    >
      전체 삭제
    </button>

  </div>


  <div
    id="status"
    class="status"
  ></div>


  <!-- ★ 미리보기 -->
  <div
    id="preview"
    class="preview"
  >

    <div
      id="previewTitle"
      class="preview-title"
    ></div>

    <div
      id="previewContent"
      class="preview-content"
    ></div>

  </div>

</div>


<script>
(function () {

  var STORAGE_KEY = "donfree_write_simple_v1";

  var title = document.getElementById("title");
  var slug = document.getElementById("slug");
  var category = document.getElementById("category");
  var tags = document.getElementById("tags");

  var seoTitle = document.getElementById("seoTitle");
  var seoDescription = document.getElementById("seoDescription");

  var body = document.getElementById("body");

  var imageInput = document.getElementById("imageInput");
  var imageList = document.getElementById("imageList");

  var featuredInput = document.getElementById("featuredInput");
  var featuredPreview = document.getElementById("featuredPreview");

  var preview = document.getElementById("preview");
  var previewTitle = document.getElementById("previewTitle");
  var previewContent = document.getElementById("previewContent");

  var status = document.getElementById("status");

  var images = [];
  var featured = null;


  /* =========================
     상태 메시지
  ========================= */

  function showStatus(message) {

    status.textContent = message;

    setTimeout(function () {

      if (status.textContent === message) {
        status.textContent = "";
      }

    }, 2500);

  }


  /* =========================
     ID
  ========================= */

  function makeId() {

    return "image_" +
      Date.now() +
      "_" +
      Math.random()
        .toString(36)
        .substring(2, 8);

  }


  /* =========================
     대표 이미지
  ========================= */

  function renderFeatured() {

    featuredPreview.innerHTML = "";

    if (!featured) {
      return;
    }

    var img = document.createElement("img");

    img.src = featured.src;
    img.alt = featured.name;

    featuredPreview.appendChild(img);

  }


  featuredInput.addEventListener(
    "change",
    function () {

      var file = this.files[0];

      if (!file) {
        return;
      }

      var reader = new FileReader();

      reader.onload = function (event) {

        featured = {
          id: makeId(),
          name: file.name,
          src: event.target.result
        };

        renderFeatured();
        save();

        showStatus("대표 이미지가 등록됐습니다.");

      };

      reader.readAsDataURL(file);

    }
  );


  /* =========================
     이미지 첨부
  ========================= */

  imageInput.addEventListener(
    "change",
    function () {

      var files = Array.from(this.files);

      if (!files.length) {
        return;
      }

      var count = 0;

      files.forEach(function (file) {

        var reader = new FileReader();

        reader.onload = function (event) {

          images.push({
            id: makeId(),
            name: file.name,
            src: event.target.result
          });

          count++;

          renderImages();

          if (count === files.length) {

            save();

            showStatus(
              files.length + "장의 사진이 첨부됐습니다."
            );

            imageInput.value = "";

          }

        };

        reader.readAsDataURL(file);

      });

    }
  );


  /* =========================
     이미지 목록
  ========================= */

  function renderImages() {

    imageList.innerHTML = "";

    images.forEach(function (item) {

      var card = document.createElement("div");

      card.className = "image-card";


      var img = document.createElement("img");

      img.src = item.src;
      img.alt = item.name;


      var name = document.createElement("div");

      name.className = "image-name";
      name.textContent = item.name;


      var buttons = document.createElement("div");

      buttons.className = "image-buttons";


      /* 본문에 넣기 */

      var insertButton = document.createElement("button");

      insertButton.type = "button";
      insertButton.textContent = "본문에 넣기";

      insertButton.addEventListener(
        "click",
        function () {

          insertImage(item);

        }
      );


      /* 대표 이미지 */

      var featureButton = document.createElement("button");

      featureButton.type = "button";
      featureButton.textContent = "대표 이미지";

      featureButton.addEventListener(
        "click",
        function () {

          featured = {
            id: item.id,
            name: item.name,
            src: item.src
          };

          renderFeatured();
          renderImages();
          save();

          showStatus(
            "대표 이미지로 지정했습니다."
          );

        }
      );


      /* 삭제 */

      var deleteButton = document.createElement("button");

      deleteButton.type = "button";
      deleteButton.textContent = "삭제";

      deleteButton.addEventListener(
        "click",
        function () {

          images = images.filter(
            function (image) {
              return image.id !== item.id;
            }
          );

          if (
            featured &&
            featured.id === item.id
          ) {

            featured = null;
            renderFeatured();

          }

          renderImages();
          save();

          showStatus("사진을 삭제했습니다.");

        }
      );


      buttons.appendChild(insertButton);
      buttons.appendChild(featureButton);
      buttons.appendChild(deleteButton);


      card.appendChild(img);
      card.appendChild(name);


      if (
        featured &&
        featured.id === item.id
      ) {

        var badge = document.createElement("div");

        badge.className = "featured";
        badge.textContent = "★ 대표 이미지";

        card.appendChild(badge);

      }


      card.appendChild(buttons);

      imageList.appendChild(card);

    });

  }


  /* =========================
     본문에 이미지 넣기
  ========================= */

  function insertImage(item) {

    /*
     * textarea에는 실제 사진 대신
     * Markdown 이미지 문법을 넣습니다.
     *
     * 미리보기에서는 이 값을 실제 이미지로 보여줍니다.
     */

    var imageCode =
      "\n\n!["
      + item.name
      + "]("
      + item.src
      + ")\n\n";


    var start = body.selectionStart;
    var end = body.selectionEnd;

    var before = body.value.substring(0, start);
    var after = body.value.substring(end);

    body.value =
      before +
      imageCode +
      after;


    var newPosition =
      start + imageCode.length;

    body.focus();

    body.setSelectionRange(
      newPosition,
      newPosition
    );

    save();

    showStatus(
      "본문에 사진을 넣었습니다."
    );

  }


  /* =========================
     굵게
  ========================= */

  document.getElementById("boldButton")
    .addEventListener(
      "click",
      function () {

        insertAroundSelection(
          "**",
          "**"
        );

      }
    );


  /* =========================
     소제목
  ========================= */

  document.getElementById("headingButton")
    .addEventListener(
      "click",
      function () {

        var start = body.selectionStart;
        var end = body.selectionEnd;

        var selected =
          body.value.substring(start, end);

        if (!selected) {
          selected = "소제목";
        }

        var replacement =
          "## " + selected;

        body.setRangeText(
          replacement,
          start,
          end,
          "end"
        );

        save();

      }
    );


  /* =========================
     링크
  ========================= */

  document.getElementById("linkButton")
    .addEventListener(
      "click",
      function () {

        var url = prompt(
          "링크 주소를 입력하세요."
        );

        if (!url) {
          return;
        }

        var start = body.selectionStart;
        var end = body.selectionEnd;

        var selected =
          body.value.substring(start, end);

        if (!selected) {
          selected = url;
        }

        var replacement =
          "[" +
          selected +
          "](" +
          url +
          ")";

        body.setRangeText(
          replacement,
          start,
          end,
          "end"
        );

        save();

      }
    );


  function insertAroundSelection(
    beforeText,
    afterText
  ) {

    var start = body.selectionStart;
    var end = body.selectionEnd;

    var selected =
      body.value.substring(start, end);

    var replacement =
      beforeText +
      selected +
      afterText;

    body.setRangeText(
      replacement,
      start,
      end,
      "end"
    );

    save();

  }


  /* =========================
     미리보기
  ========================= */

  document.getElementById("previewButton")
    .addEventListener(
      "click",
      function () {

        previewTitle.textContent =
          title.value || "제목 없음";


        var html =
          markdownToHtml(
            body.value
          );


        previewContent.innerHTML =
          html;


        preview.style.display =
          "block";


        preview.scrollIntoView({
          behavior: "smooth",
          block: "start"
        });

      }
    );


  /* =========================
     Markdown → 미리보기 HTML
  ========================= */

  function markdownToHtml(text) {

    var html =
      escapeHtml(text);


    /*
     * 이미지
     */

    html = html.replace(
      /!\[([^\]]*)\]\((data:image\/[^)]+)\)/g,
      function (
        match,
        alt,
        src
      ) {

        return (
          '<img src="' +
          src +
          '" alt="' +
          alt +
          '">'
        );

      }
    );


    /*
     * 링크
     */

    html = html.replace(
      /\[([^\]]+)\]\((https?:\/\/[^)]+)\)/g,
      function (
        match,
        text,
        url
      ) {

        return (
          '<a href="' +
          url +
          '" target="_blank">' +
          text +
          '</a>'
        );

      }
    );


    /*
     * 제목
     */

    html = html.replace(
      /^### (.+)$/gm,
      "<h3>$1</h3>"
    );

    html = html.replace(
      /^## (.+)$/gm,
      "<h2>$1</h2>"
    );


    /*
     * 굵게
     */

    html = html.replace(
      /\*\*(.*?)\*\*/g,
      "<strong>$1</strong>"
    );


    /*
     * 줄바꿈
     */

    html = html.replace(
      /\n/g,
      "<br>"
    );


    return html;

  }


  function escapeHtml(text) {

    var div =
      document.createElement("div");

    div.textContent = text;

    return div.innerHTML;

  }


  /* =========================
     저장
  ========================= */

  function getData() {

    return {

      title: title.value,
      slug: slug.value,
      category: category.value,
      tags: tags.value,

      seoTitle:
        seoTitle.value,

      seoDescription:
        seoDescription.value,

      body:
        body.value,

      images:
        images,

      featured:
        featured

    };

  }


  function save() {

    try {

      localStorage.setItem(
        STORAGE_KEY,
        JSON.stringify(
          getData()
        )
      );

    } catch (error) {

      console.warn(
        "자동 저장에 실패했습니다.",
        error
      );

    }

  }


  [
    title,
    slug,
    category,
    tags,
    seoTitle,
    seoDescription,
    body

  ].forEach(
    function (element) {

      element.addEventListener(
        "input",
        save
      );

    }
  );


  document.getElementById("saveButton")
    .addEventListener(
      "click",
      function () {

        save();

        showStatus(
          "임시저장했습니다."
        );

      }
    );


  /* =========================
     기존 글 불러오기
  ========================= */

  function load() {

    try {

      var saved =
        localStorage.getItem(
          STORAGE_KEY
        );

      if (!saved) {
        return;
      }

      var data =
        JSON.parse(saved);


      title.value =
        data.title || "";

      slug.value =
        data.slug || "";

      category.value =
        data.category || "";

      tags.value =
        data.tags || "";

      seoTitle.value =
        data.seoTitle || "";

      seoDescription.value =
        data.seoDescription || "";

      body.value =
        data.body || "";

      images =
        Array.isArray(data.images)
          ? data.images
          : [];

      featured =
        data.featured || null;


      renderImages();
      renderFeatured();

    } catch (error) {

      console.warn(
        "저장된 글을 불러오지 못했습니다.",
        error
      );

    }

  }


  /* =========================
     Markdown 다운로드
  ========================= */

  document.getElementById("downloadButton")
    .addEventListener(
      "click",
      function () {

        if (!title.value.trim()) {

          alert(
            "제목을 먼저 입력해주세요."
          );

          title.focus();

          return;

        }


        var today =
          new Date();

        var date =
          today.getFullYear() +
          "-" +
          String(
            today.getMonth() + 1
          ).padStart(2, "0") +
          "-" +
          String(
            today.getDate()
          ).padStart(2, "0");


        var postSlug =
          slug.value.trim();


        if (!postSlug) {

          postSlug =
            title.value
              .trim()
              .replace(/\s+/g, "-");

        }


        var tagArray =
          tags.value
            .split(",")
            .map(
              function (item) {
                return item.trim();
              }
            )
            .filter(Boolean);


        var markdown =
          "---\n";

        markdown +=
          'title: "' +
          title.value.replace(
            /"/g,
            '\\"'
          ) +
          '"\n';

        markdown +=
          "date: " +
          date +
          "\n";

        if (category.value.trim()) {

          markdown +=
            "categories: [" +
            category.value.trim() +
            "]\n";

        }

        if (tagArray.length) {

          markdown +=
            "tags: [" +
            tagArray.join(", ") +
            "]\n";

        }

        if (
          seoDescription.value.trim()
        ) {

          markdown +=
            'description: "' +
            seoDescription.value
              .replace(
                /"/g,
                '\\"'
              ) +
            '"\n';

        }


        markdown +=
          "---\n\n";


        markdown +=
          body.value;


        var blob =
          new Blob(
            [markdown],
            {
              type:
                "text/markdown;charset=utf-8"
            }
          );


        var url =
          URL.createObjectURL(
            blob
          );


        var link =
          document.createElement("a");

        link.href = url;

        link.download =
          date +
          "-" +
          postSlug +
          ".md";


        document.body.appendChild(
          link
        );

        link.click();

        link.remove();

        URL.revokeObjectURL(
          url
        );


        showStatus(
          "Markdown 파일을 만들었습니다."
        );

      }
    );


  /* =========================
     전체 삭제
  ========================= */

  document.getElementById("clearButton")
    .addEventListener(
      "click",
      function () {

        if (
          !confirm(
            "작성 중인 글을 모두 삭제할까요?"
          )
        ) {

          return;

        }


        title.value = "";
        slug.value = "";
        category.value = "";
        tags.value = "";

        seoTitle.value = "";
        seoDescription.value = "";

        body.value = "";

        images = [];
        featured = null;

        imageInput.value = "";
        featuredInput.value = "";

        imageList.innerHTML = "";
        featuredPreview.innerHTML = "";

        preview.style.display =
          "none";

        previewContent.innerHTML =
          "";

        localStorage.removeItem(
          STORAGE_KEY
        );

        showStatus(
          "작성 내용을 삭제했습니다."
        );

      }
    );


  /*
   * 시작
   */

  load();

})();
</script>
