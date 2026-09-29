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
  margin-bottom: 24px;
}

.write-label {
  display: block;
  margin-bottom: 8px;
  font-weight: 700;
}

.write-input {
  width: 100%;
  box-sizing: border-box;
  padding: 13px 14px;
  border: 1px solid #d9d9d9;
  border-radius: 8px;
  background: #fff;
  font-size: 15px;
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
  background: #fff;
  font-family: inherit;
  font-size: 16px;
  line-height: 1.8;
  resize: vertical;
}

.toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-bottom: 8px;
}

.toolbar button,
.action-button {
  padding: 9px 13px;
  border: 1px solid #d5d5d5;
  border-radius: 7px;
  background: #fff;
  cursor: pointer;
  font-size: 14px;
}

.toolbar button:hover,
.action-button:hover {
  background: #f3f3f3;
}

.primary-button {
  background: #222 !important;
  color: #fff !important;
  border-color: #222 !important;
}

.image-upload {
  padding: 18px;
  border: 1px dashed #bbb;
  border-radius: 10px;
  background: #fafafa;
}

.image-upload input[type="file"] {
  max-width: 100%;
}

.help {
  margin-top: 8px;
  font-size: 12px;
  line-height: 1.6;
  color: #777;
}

/* 이미지 목록 */
.image-count {
  margin-top: 18px;
  margin-bottom: 10px;
  font-size: 14px;
  font-weight: 700;
}

.image-empty {
  padding: 25px 15px;
  border: 1px solid #e5e5e5;
  border-radius: 8px;
  background: #fff;
  text-align: center;
  color: #888;
  font-size: 14px;
}

.image-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(190px, 1fr));
  gap: 15px;
  margin-top: 12px;
}

.image-card {
  overflow: hidden;
  padding: 9px;
  border: 1px solid #ddd;
  border-radius: 9px;
  background: #fff;
}

.image-card img {
  display: block;
  width: 100%;
  height: 145px;
  object-fit: cover;
  border-radius: 6px;
  background: #f3f3f3;
}

.image-number {
  margin-top: 8px;
  font-size: 11px;
  color: #888;
}

.image-name {
  margin: 5px 0 8px;
  font-size: 12px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.image-buttons {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 4px;
}

.image-buttons button {
  padding: 7px 3px;
  border: 1px solid #ddd;
  border-radius: 5px;
  background: #fff;
  cursor: pointer;
  font-size: 11px;
}

.image-buttons button:hover {
  background: #f3f3f3;
}

.featured-badge {
  margin: 5px 0 8px;
  font-size: 11px;
  font-weight: 700;
}

.featured-preview {
  margin-top: 15px;
}

.featured-preview-title {
  margin-bottom: 8px;
  font-size: 13px;
  font-weight: 700;
}

.featured-preview img {
  display: block;
  width: 240px;
  max-width: 100%;
  max-height: 180px;
  object-fit: cover;
  border-radius: 8px;
}

.button-row {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 20px;
}

.status {
  min-height: 20px;
  margin-top: 10px;
  font-size: 13px;
  color: #555;
}

/* 본문 안 이미지 표시 */
.body-image-marker {
  display: inline-block;
  margin: 4px 0;
  padding: 5px 9px;
  border-radius: 5px;
  background: #f1f1f1;
  color: #777;
  font-size: 12px;
}

/* 미리보기 */
.preview {
  display: none;
  margin-top: 35px;
  padding: 28px;
  border: 1px solid #ddd;
  border-radius: 10px;
  background: #fff;
}

.preview-title {
  margin-bottom: 25px;
  font-size: 30px;
  line-height: 1.35;
  font-weight: 800;
}

.preview-content {
  font-size: 16px;
  line-height: 1.85;
  overflow-wrap: break-word;
}

.preview-content h2 {
  margin: 32px 0 12px;
  font-size: 23px;
  line-height: 1.4;
}

.preview-content strong {
  font-weight: 800;
}

.preview-content a {
  text-decoration: underline;
}

.preview-image {
  display: block;
  max-width: 100%;
  height: auto;
  margin: 22px auto;
  border-radius: 9px;
}

.preview-error {
  padding: 12px;
  border-radius: 7px;
  background: #fff3f3;
  color: #b00020;
  font-size: 13px;
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
    gap: 10px;
  }

  .image-card img {
    height: 120px;
  }

  .preview {
    padding: 18px;
  }

  .preview-title {
    font-size: 24px;
  }
}
</style>


<div class="write-wrap">

  <!-- 제목 -->
  <div class="write-box">
    <label class="write-label" for="writeTitle">
      글 제목
    </label>

    <input
      id="writeTitle"
      class="write-input"
      type="text"
      placeholder="글 제목을 입력하세요"
    >
  </div>


  <!-- URL / 카테고리 -->
  <div class="write-box write-grid">

    <div>
      <label class="write-label" for="writeSlug">
        영문 URL
      </label>

      <input
        id="writeSlug"
        class="write-input"
        type="text"
        placeholder="예: instagram-reels-download"
      >
    </div>

    <div>
      <label class="write-label" for="writeCategory">
        카테고리
      </label>

      <input
        id="writeCategory"
        class="write-input"
        type="text"
        placeholder="예: 생활정보"
      >
    </div>

  </div>


  <!-- 태그 -->
  <div class="write-box">

    <label class="write-label" for="writeTags">
      태그
    </label>

    <input
      id="writeTags"
      class="write-input"
      type="text"
      placeholder="예: 인스타, 릴스, 다운로드"
    >

  </div>


  <!-- SEO -->
  <div class="write-box write-grid">

    <div>
      <label class="write-label" for="writeSeoTitle">
        SEO 제목
      </label>

      <input
        id="writeSeoTitle"
        class="write-input"
        type="text"
        placeholder="검색 결과에 표시될 제목"
      >
    </div>

    <div>
      <label class="write-label" for="writeSeoDescription">
        SEO 설명
      </label>

      <input
        id="writeSeoDescription"
        class="write-input"
        type="text"
        placeholder="검색 결과에 표시될 설명"
      >
    </div>

  </div>


  <!-- 대표 이미지 -->
  <div class="write-box">

    <label class="write-label">
      대표 이미지
    </label>

    <div class="image-upload">

      <input
        id="featuredInput"
        type="file"
        accept="image/*"
      >

      <div class="help">
        대표 이미지로 사용할 사진을 선택하세요.
      </div>

      <div
        id="featuredPreview"
        class="featured-preview"
      ></div>

    </div>

  </div>


  <!-- 본문 -->
  <div class="write-box">

    <label class="write-label">
      본문
    </label>

    <div class="toolbar">

      <button
        type="button"
        id="boldButton"
      >
        굵게
      </button>

      <button
        type="button"
        id="headingButton"
      >
        소제목
      </button>

      <button
        type="button"
        id="linkButton"
      >
        링크
      </button>

    </div>

    <textarea
      id="writeBody"
      class="write-body"
      placeholder="여기에 글을 작성하세요."
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
        사진을 여러 장 선택할 수 있습니다.
        사진을 선택하면 아래에 바로 표시됩니다.
      </div>

      <div
        id="imageCount"
        class="image-count"
      >
        첨부된 사진 0장
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
      id="loadButton"
      class="action-button"
      type="button"
    >
      임시저장 불러오기
    </button>

    <button
      id="downloadButton"
      class="action-button primary-button"
      type="button"
    >
      글 파일 만들기
    </button>

    <button
      id="clearButton"
      class="action-button"
      type="button"
    >
      전체 초기화
    </button>

  </div>


  <div
    id="status"
    class="status"
  ></div>


  <!-- 미리보기 -->
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


<script data-proofer-ignore>
(function () {

  "use strict";


  /*
   * --------------------------------------------------
   * 기본 설정
   * --------------------------------------------------
   */

  var STORAGE_KEY = "donfree_write_v3";


  /*
   * 페이지 요소
   */

  var title =
    document.getElementById("writeTitle");

  var slug =
    document.getElementById("writeSlug");

  var category =
    document.getElementById("writeCategory");

  var tags =
    document.getElementById("writeTags");

  var seoTitle =
    document.getElementById("writeSeoTitle");

  var seoDescription =
    document.getElementById("writeSeoDescription");

  var body =
    document.getElementById("writeBody");

  var imageInput =
    document.getElementById("imageInput");

  var imageList =
    document.getElementById("imageList");

  var imageCount =
    document.getElementById("imageCount");

  var featuredInput =
    document.getElementById("featuredInput");

  var featuredPreview =
    document.getElementById("featuredPreview");

  var preview =
    document.getElementById("preview");

  var previewTitle =
    document.getElementById("previewTitle");

  var previewContent =
    document.getElementById("previewContent");

  var status =
    document.getElementById("status");


  /*
   * 현재 첨부된 이미지
   *
   * 실제 File 객체를 보관한다.
   *
   * Base64를 본문이나 textarea에 넣지 않는다.
   */

  var images = [];

  var featuredId = null;


  /*
   * --------------------------------------------------
   * 상태 메시지
   * --------------------------------------------------
   */

  function showStatus(message) {

    if (!status) {
      return;
    }

    status.textContent = message;

    window.setTimeout(function () {

      if (
        status.textContent === message
      ) {
        status.textContent = "";
      }

    }, 2500);

  }


  /*
   * --------------------------------------------------
   * 이미지 ID
   * --------------------------------------------------
   */

  function makeId() {

    return (
      "img_" +
      Date.now() +
      "_" +
      Math.random()
        .toString(36)
        .substring(2, 8)
    );

  }


  /*
   * --------------------------------------------------
   * HTML 이스케이프
   * --------------------------------------------------
   */

  function escapeHtml(value) {

    return String(value || "")
      .replace(/&/g, "&amp;")
      .replace(/</g, "&lt;")
      .replace(/>/g, "&gt;")
      .replace(/"/g, "&quot;")
      .replace(/'/g, "&#039;");

  }


  /*
   * --------------------------------------------------
   * 이미지 미리보기 URL
   * --------------------------------------------------
   */

  function getImageUrl(item) {

    if (!item) {
      return "";
    }

    if (item.url) {
      return item.url;
    }

    if (item.file) {

      if (!item.objectUrl) {

        item.objectUrl =
          URL.createObjectURL(item.file);

      }

      return item.objectUrl;
    }

    return "";

  }


  /*
   * --------------------------------------------------
   * 대표 이미지 표시
   * --------------------------------------------------
   */

  function renderFeatured() {

    featuredPreview.innerHTML = "";

    if (!featuredId) {
      return;
    }

    var item =
      images.find(function (image) {

        return image.id === featuredId;

      });


    if (!item) {
      return;
    }


    var titleElement =
      document.createElement("div");

    titleElement.className =
      "featured-preview-title";

    titleElement.textContent =
      "현재 대표 이미지";


    var image =
      document.createElement("img");

    image.src =
      getImageUrl(item);

    image.alt =
      item.name || "대표 이미지";


    featuredPreview.appendChild(
      titleElement
    );

    featuredPreview.appendChild(
      image
    );

  }


  /*
   * --------------------------------------------------
   * 이미지 목록 표시
   * --------------------------------------------------
   */

  function renderImages() {

    imageList.innerHTML = "";


    imageCount.textContent =
      "첨부된 사진 " +
      images.length +
      "장";


    if (!images.length) {

      var empty =
        document.createElement("div");

      empty.className =
        "image-empty";

      empty.textContent =
        "아직 첨부된 사진이 없습니다.";

      imageList.appendChild(empty);

      renderFeatured();

      return;
    }


    images.forEach(
      function (item, index) {

        var card =
          document.createElement("div");

        card.className =
          "image-card";


        /*
         * 사진
         */

        var image =
          document.createElement("img");

        image.src =
          getImageUrl(item);

        image.alt =
          item.name || "첨부 이미지";


        /*
         * 번호
         */

        var number =
          document.createElement("div");

        number.className =
          "image-number";

        number.textContent =
          "이미지 " +
          (index + 1);


        /*
         * 파일명
         */

        var name =
          document.createElement("div");

        name.className =
          "image-name";

        name.textContent =
          item.name || "사진";


        /*
         * 대표 이미지 표시
         */

        if (
          featuredId === item.id
        ) {

          var badge =
            document.createElement("div");

          badge.className =
            "featured-badge";

          badge.textContent =
            "★ 대표 이미지";

          card.appendChild(badge);

        }


        /*
         * 버튼 영역
         */

        var buttons =
          document.createElement("div");

        buttons.className =
          "image-buttons";


        /*
         * 본문에 넣기
         */

        var insertButton =
          document.createElement("button");

        insertButton.type =
          "button";

        insertButton.textContent =
          "본문에 넣기";


        insertButton.addEventListener(
          "click",
          function () {

            insertImageMarker(item);

          }
        );


        /*
         * 대표 이미지
         */

        var featuredButton =
          document.createElement("button");

        featuredButton.type =
          "button";

        featuredButton.textContent =
          "대표 이미지";


        featuredButton.addEventListener(
          "click",
          function () {

            featuredId =
              item.id;

            renderImages();
            renderFeatured();

            showStatus(
              "대표 이미지로 지정했습니다."
            );

          }
        );


        /*
         * 삭제
         */

        var deleteButton =
          document.createElement("button");

        deleteButton.type =
          "button";

        deleteButton.textContent =
          "삭제";


        deleteButton.addEventListener(
          "click",
          function () {

            deleteImage(item.id);

          }
        );


        buttons.appendChild(
          insertButton
        );

        buttons.appendChild(
          featuredButton
        );

        buttons.appendChild(
          deleteButton
        );


        card.appendChild(image);
        card.appendChild(number);
        card.appendChild(name);
        card.appendChild(buttons);

        imageList.appendChild(card);

      }
    );


    renderFeatured();

  }


  /*
   * --------------------------------------------------
   * 이미지 삭제
   * --------------------------------------------------
   */

  function deleteImage(id) {

    var item =
      images.find(function (image) {

        return image.id === id;

      });


    if (
      item &&
      item.objectUrl
    ) {

      try {

        URL.revokeObjectURL(
          item.objectUrl
        );

      } catch (error) {}

    }


    images =
      images.filter(
        function (image) {

          return image.id !== id;

        }
      );


    if (
      featuredId === id
    ) {

      featuredId = null;

    }


    var marker =
      "[[IMAGE:" +
      id +
      "]]";


    body.value =
      body.value
        .split(marker)
        .join("");


    renderImages();
    renderFeatured();


    showStatus(
      "사진을 삭제했습니다."
    );

  }


  /*
   * --------------------------------------------------
   * 이미지 파일 첨부
   * --------------------------------------------------
   */

  imageInput.addEventListener(
    "change",
    function () {

      var files =
        Array.prototype.slice.call(
          this.files || []
        );


      if (!files.length) {
        return;
      }


      var validFiles =
        files.filter(
          function (file) {

            return (
              file.type &&
              file.type.indexOf(
                "image/"
              ) === 0
            );

          }
        );


      if (!validFiles.length) {

        showStatus(
          "이미지 파일을 선택해주세요."
        );

        return;

      }


      validFiles.forEach(
        function (file) {

          var item = {

            id: makeId(),

            name: file.name,

            file: file,

            objectUrl: null,

            url: null

          };


          images.push(item);

        }
      );


      renderImages();


      showStatus(
        validFiles.length +
        "장의 사진이 첨부됐습니다."
      );


      /*
       * 같은 파일을 다시 선택할 수 있도록 초기화
       */

      imageInput.value = "";

    }
  );


  /*
   * --------------------------------------------------
   * 대표 이미지 선택
   * --------------------------------------------------
   */

  featuredInput.addEventListener(
    "change",
    function () {

      var file =
        this.files &&
        this.files[0];


      if (!file) {
        return;
      }


      if (
        !file.type ||
        file.type.indexOf("image/") !== 0
      ) {

        showStatus(
          "이미지 파일을 선택해주세요."
        );

        return;

      }


      var item = {

        id: makeId(),

        name: file.name,

        file: file,

        objectUrl: null,

        url: null

      };


      images.push(item);

      featuredId =
        item.id;


      renderImages();
      renderFeatured();


      showStatus(
        "대표 이미지가 등록됐습니다."
      );


      featuredInput.value = "";

    }
  );


  /*
   * --------------------------------------------------
   * 본문에 이미지 넣기
   * --------------------------------------------------
   */

  function insertImageMarker(item) {

    if (!item) {
      return;
    }


    var marker =
      "\n\n[[IMAGE:" +
      item.id +
      "]]\n\n";


    var start =
      body.selectionStart || 0;

    var end =
      body.selectionEnd || 0;


    var before =
      body.value.substring(
        0,
        start
      );


    var after =
      body.value.substring(
        end
      );


    body.value =
      before +
      marker +
      after;


    var position =
      start +
      marker.length;


    body.focus();

    body.setSelectionRange(
      position,
      position
    );


    showStatus(
      "본문에 사진을 넣었습니다."
    );

  }


  /*
   * --------------------------------------------------
   * 선택 영역 감싸기
   * --------------------------------------------------
   */

  function wrapSelection(
    beforeText,
    afterText
  ) {

    var start =
      body.selectionStart || 0;

    var end =
      body.selectionEnd || 0;


    var selected =
      body.value.substring(
        start,
        end
      );


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


    body.focus();

  }


  /*
   * --------------------------------------------------
   * 굵게
   * --------------------------------------------------
   */

  document
    .getElementById("boldButton")
    .addEventListener(
      "click",
      function () {

        wrapSelection(
          "**",
          "**"
        );

      }
    );


  /*
   * --------------------------------------------------
   * 소제목
   * --------------------------------------------------
   */

  document
    .getElementById("headingButton")
    .addEventListener(
      "click",
      function () {

        var start =
          body.selectionStart || 0;

        var end =
          body.selectionEnd || 0;


        var selected =
          body.value.substring(
            start,
            end
          );


        if (!selected) {

          selected =
            "소제목";

        }


        var replacement =
          "## " +
          selected;


        body.setRangeText(
          replacement,
          start,
          end,
          "end"
        );


        body.focus();

      }
    );


  /*
   * --------------------------------------------------
   * 링크
   * --------------------------------------------------
   */

  document
    .getElementById("linkButton")
    .addEventListener(
      "click",
      function () {

        var url =
          window.prompt(
            "링크 주소를 입력하세요."
          );


        if (!url) {
          return;
        }


        var start =
          body.selectionStart || 0;

        var end =
          body.selectionEnd || 0;


        var selected =
          body.value.substring(
            start,
            end
          );


        if (!selected) {

          selected =
            "링크";

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


        body.focus();

      }
    );


  /*
   * --------------------------------------------------
   * 마크다운 줄을 미리보기 DOM으로 만들기
   * --------------------------------------------------
   */

  function renderPreview() {

    previewContent.innerHTML = "";


    var lines =
      body.value.split("\n");


    var paragraph = null;


    function ensureParagraph() {

      if (!paragraph) {

        paragraph =
          document.createElement("p");

        paragraph.style.margin =
          "0 0 16px";

      }

      return paragraph;

    }


    function flushParagraph() {

      if (
        paragraph &&
        paragraph.textContent
      ) {

        previewContent.appendChild(
          paragraph
        );

      }

      paragraph = null;

    }


    lines.forEach(
      function (line) {

        var trimmed =
          line.trim();


        /*
         * 빈 줄
         */

        if (!trimmed) {

          flushParagraph();

          return;

        }


        /*
         * 이미지
         */

        var imageMatch =
          trimmed.match(
            /^\[\[IMAGE:([^\]]+)\]\]$/
          );


        if (imageMatch) {

          flushParagraph();


          var imageItem =
            images.find(
              function (item) {

                return (
                  item.id ===
                  imageMatch[1]
                );

              }
            );


          if (imageItem) {

            var previewImage =
              document.createElement("img");

            previewImage.className =
              "preview-image";

            previewImage.src =
              getImageUrl(
                imageItem
              );

            previewImage.alt =
              imageItem.name ||
              "본문 이미지";


            previewContent.appendChild(
              previewImage
            );

          }

          return;

        }


        /*
         * 소제목
         */

        if (
          trimmed.indexOf("## ") === 0
        ) {

          flushParagraph();


          var heading =
            document.createElement("h2");

          heading.textContent =
            trimmed.substring(3);


          previewContent.appendChild(
            heading
          );

          return;

        }


        /*
         * 일반 문장
         */

        var p =
          ensureParagraph();


        appendInlineMarkdown(
          p,
          line
        );


        previewContent.appendChild(
          p
        );

        paragraph = null;

      }
    );


    flushParagraph();

  }


  /*
   * --------------------------------------------------
   * 일반 문장 Markdown 처리
   * --------------------------------------------------
   */

  function appendInlineMarkdown(
    parent,
    value
  ) {

    var remaining =
      String(value || "");


    /*
     * 굵게 / 링크를 간단하게 처리한다.
     */

    var pattern =
      /(\*\*([^*]+)\*\*)|(\[([^\]]+)\]\((https?:\/\/[^\s)]+)\))/g;


    var lastIndex = 0;

    var match;


    while (
      (match =
        pattern.exec(remaining)) !== null
    ) {

      if (
        match.index >
        lastIndex
      ) {

        parent.appendChild(
          document.createTextNode(
            remaining.substring(
              lastIndex,
              match.index
            )
          )
        );

      }


      /*
       * 굵게
       */

      if (match[1]) {

        var strong =
          document.createElement("strong");

        strong.textContent =
          match[2];

        parent.appendChild(
          strong
        );

      }


      /*
       * 링크
       */

      else if (match[3]) {

        var link =
          document.createElement("a");

        link.href =
          match[5];

        link.target =
          "_blank";

        link.rel =
          "noopener noreferrer";

        link.textContent =
          match[4];

        parent.appendChild(
          link
        );

      }


      lastIndex =
        pattern.lastIndex;

    }


    if (
      lastIndex <
      remaining.length
    ) {

      parent.appendChild(
        document.createTextNode(
          remaining.substring(
            lastIndex
          )
        )
      );

    }

  }


  /*
   * --------------------------------------------------
   * 미리보기
   * --------------------------------------------------
   */

  document
    .getElementById("previewButton")
    .addEventListener(
      "click",
      function () {

        previewTitle.textContent =
          title.value.trim() ||
          "제목 없음";


        renderPreview();


        preview.style.display =
          "block";


        preview.scrollIntoView({
          behavior: "smooth",
          block: "start"
        });


        showStatus(
          "미리보기를 표시했습니다."
        );

      }
    );


  /*
   * --------------------------------------------------
   * 현재 글 데이터
   * --------------------------------------------------
   */

  function getTextData() {

    return {

      title:
        title.value,

      slug:
        slug.value,

      category:
        category.value,

      tags:
        tags.value,

      seoTitle:
        seoTitle.value,

      seoDescription:
        seoDescription.value,

      body:
        body.value,

      featuredId:
        featuredId

    };

  }


  /*
   * --------------------------------------------------
   * 임시저장
   *
   * 사진 자체는 저장하지 않는다.
   * 따라서 localStorage 용량 문제가 생기지 않는다.
   * --------------------------------------------------
   */

  function saveDraft() {

    try {

      localStorage.setItem(
        STORAGE_KEY,
        JSON.stringify(
          getTextData()
        )
      );


      return true;

    } catch (error) {

      showStatus(
        "임시저장에 실패했습니다."
      );


      return false;

    }

  }


  /*
   * --------------------------------------------------
   * 임시저장 버튼
   * --------------------------------------------------
   */

  document
    .getElementById("saveButton")
    .addEventListener(
      "click",
      function () {

        if (
          saveDraft()
        ) {

          showStatus(
            "임시저장했습니다."
          );

        }

      }
    );


  /*
   * --------------------------------------------------
   * 임시저장 불러오기
   * --------------------------------------------------
   */

  document
    .getElementById("loadButton")
    .addEventListener(
      "click",
      function () {

        var saved =
          localStorage.getItem(
            STORAGE_KEY
          );


        if (!saved) {

          showStatus(
            "저장된 글이 없습니다."
          );

          return;

        }


        try {

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


          /*
           * 사진은 새로 첨부해야 한다.
           */

          featuredId = null;

          images = [];


          renderImages();
          renderFeatured();


          showStatus(
            "글 내용을 불러왔습니다. 사진은 다시 첨부해주세요."
          );

        } catch (error) {

          showStatus(
            "저장된 글을 불러오지 못했습니다."
          );

        }

      }
    );


  /*
   * --------------------------------------------------
   * 파일 생성용 이미지 읽기
   *
   * 다운로드할 때만 Base64로 변환한다.
   * --------------------------------------------------
   */

  function fileToDataUrl(
    file
  ) {

    return new Promise(
      function (
        resolve,
        reject
      ) {

        var reader =
          new FileReader();


        reader.onload =
          function (event) {

            resolve(
              event.target.result
            );

          };


        reader.onerror =
          function () {

            reject(
              new Error(
                "이미지를 읽을 수 없습니다."
              )
            );

          };


        reader.readAsDataURL(
          file
        );

      }
    );

  }


  /*
   * --------------------------------------------------
   * 이미지 마커 → Markdown 이미지
   * --------------------------------------------------
   */

  async function buildBodyForDownload() {

    var content =
      body.value;


    var markerPattern =
      /\[\[IMAGE:([^\]]+)\]\]/g;


    var matches =
      Array.from(
        content.matchAll(
          markerPattern
        )
      );


    for (
      var i = 0;
      i < matches.length;
      i++
    ) {

      var full =
        matches[i][0];

      var id =
        matches[i][1];


      var item =
        images.find(
          function (image) {

            return image.id === id;

          }
        );


      if (!item) {

        content =
          content
            .split(full)
            .join("");

        continue;

      }


      var dataUrl =
        "";


      if (item.file) {

        dataUrl =
          await fileToDataUrl(
            item.file
          );

      } else if (item.url) {

        dataUrl =
          item.url;

      }


      var markdownImage =
        "![" +
        item.name +
        "](" +
        dataUrl +
        ")";


      content =
        content
          .split(full)
          .join(
            markdownImage
          );

    }


    return content;

  }


  /*
   * --------------------------------------------------
   * Front Matter
   * --------------------------------------------------
   */

  function yamlQuote(
    value
  ) {

    var text =
      String(value || "")
        .replace(/\\/g, "\\\\")
        .replace(/"/g, '\\"')
        .replace(/\n/g, " ");


    return '"' +
      text +
      '"';

  }


  /*
   * --------------------------------------------------
   * 글 파일 만들기
   * --------------------------------------------------
   */

  document
    .getElementById("downloadButton")
    .addEventListener(
      "click",
      async function () {

        if (
          !title.value.trim()
        ) {

          showStatus(
            "글 제목을 먼저 입력해주세요."
          );

          title.focus();

          return;

        }


        showStatus(
          "글 파일을 만드는 중입니다..."
        );


        try {

          var finalBody =
            await buildBodyForDownload();


          var tagArray =
            tags.value
              .split(",")
              .map(
                function (tag) {

                  return tag.trim();

                }
              )
              .filter(
                function (tag) {

                  return tag;

                }
              );


          var tagText =
            tagArray.join(", ");


          var featuredItem =
            images.find(
              function (image) {

                return (
                  image.id ===
                  featuredId
                );

              }
            );


          var featuredLine = "";


          if (featuredItem) {

            var featuredData =
              "";


            if (
              featuredItem.file
            ) {

              featuredData =
                await fileToDataUrl(
                  featuredItem.file
                );

            } else if (
              featuredItem.url
            ) {

              featuredData =
                featuredItem.url;

            }


            featuredLine =
              "image:\n" +
              "  path: " +
              yamlQuote(
                featuredData
              ) +
              "\n";

          }


          var markdown =
            "---\n" +

            "layout: post\n" +

            "title: " +
            yamlQuote(
              title.value
            ) +
            "\n" +

            "date: " +
            new Date()
              .toISOString()
              .substring(
                0,
                10
              ) +
            " 12:00:00 +0900\n" +

            "categories: [" +
            yamlQuote(
              category.value
            ) +
            "]\n" +

            "tags: [" +
            tagText
              .split(",")
              .filter(
                function (tag) {

                  return tag.trim();

                }
              )
              .map(
                function (tag) {

                  return yamlQuote(
                    tag.trim()
                  );

                }
              )
              .join(", ") +
            "]\n";


          if (
            seoTitle.value.trim()
          ) {

            markdown +=
              "description: " +
              yamlQuote(
                seoDescription.value
              ) +
              "\n";

          }


          markdown +=
            featuredLine +

            "---\n\n" +

            finalBody;


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
            document.createElement(
              "a"
            );


          var filename =
            slug.value.trim() ||
            "new-post";


          filename =
            filename
              .replace(
                /[^a-zA-Z0-9-_]/g,
                "-"
              );


          link.href =
            url;

          link.download =
            filename +
            ".md";


          document.body.appendChild(
            link
          );


          link.click();


          document.body.removeChild(
            link
          );


          window.setTimeout(
            function () {

              URL.revokeObjectURL(
                url
              );

            },
            1000
          );


          showStatus(
            "글 파일을 만들었습니다."
          );

        } catch (error) {

          console.error(
            error
          );


          showStatus(
            "파일을 만드는 중 오류가 발생했습니다."
          );

        }

      }
    );


  /*
   * --------------------------------------------------
   * 전체 초기화
   * --------------------------------------------------
   */

  document
    .getElementById("clearButton")
    .addEventListener(
      "click",
      function () {

        var confirmed =
          window.confirm(
            "작성한 글과 첨부 사진을 모두 삭제할까요?"
          );


        if (!confirmed) {
          return;
        }


        /*
         * Object URL 정리
         */

        images.forEach(
          function (item) {

            if (
              item.objectUrl
            ) {

              try {

                URL.revokeObjectURL(
                  item.objectUrl
                );

              } catch (error) {}

            }

          }
        );


        title.value = "";
        slug.value = "";
        category.value = "";
        tags.value = "";
        seoTitle.value = "";
        seoDescription.value = "";
        body.value = "";


        images = [];
        featuredId = null;


        featuredInput.value = "";
        imageInput.value = "";


        localStorage.removeItem(
          STORAGE_KEY
        );


        preview.style.display =
          "none";


        renderImages();
        renderFeatured();


        showStatus(
          "전체 초기화했습니다."
        );

      }
    );


  /*
   * --------------------------------------------------
   * 자동 저장
   *
   * 글 텍스트만 저장한다.
   * --------------------------------------------------
   */

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
        function () {

          saveDraft();

        }
      );

    }
  );


  /*
   * --------------------------------------------------
   * 초기 화면
   * --------------------------------------------------
   */

  renderImages();
  renderFeatured();


})();
</script>
