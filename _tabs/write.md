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
  font-weight: 700;
  margin-bottom: 8px;
}

.write-input {
  width: 100%;
  box-sizing: border-box;
  padding: 12px 14px;
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
  padding: 8px 12px;
  border: 1px solid #d5d5d5;
  border-radius: 7px;
  background: #fff;
  cursor: pointer;
  font-size: 14px;
}

.toolbar button:hover,
.action-button:hover {
  background: #f4f4f4;
}

.primary-button {
  background: #222 !important;
  color: #fff !important;
  border-color: #222 !important;
}

.image-upload {
  padding: 18px;
  border: 1px dashed #bbb;
  border-radius: 8px;
  background: #fafafa;
}

.help {
  margin-top: 7px;
  font-size: 12px;
  color: #777;
}

.image-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  gap: 15px;
  margin-top: 18px;
}

.image-card {
  padding: 8px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background: #fff;
}

.image-card img {
  display: block;
  width: 100%;
  height: 140px;
  object-fit: cover;
  border-radius: 5px;
}

.image-name {
  margin: 8px 2px;
  font-size: 12px;
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
  border-radius: 5px;
  background: #fff;
  cursor: pointer;
  font-size: 12px;
}

.image-buttons button:hover {
  background: #f4f4f4;
}

.featured-badge {
  margin: 5px 0;
  font-size: 11px;
  font-weight: 700;
}

.featured-preview {
  margin-top: 12px;
}

.featured-preview img {
  display: block;
  width: 220px;
  max-height: 160px;
  object-fit: cover;
  border-radius: 6px;
}

.button-row {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 20px;
}

.status {
  margin-top: 10px;
  font-size: 13px;
  color: #555;
}

.preview {
  display: none;
  margin-top: 30px;
  padding: 25px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background: #fff;
}

.preview-title {
  margin-bottom: 25px;
  font-size: 30px;
  font-weight: 800;
}

.preview-content {
  font-size: 16px;
  line-height: 1.8;
  overflow-wrap: break-word;
}

.preview-content img {
  display: block;
  max-width: 100%;
  height: auto;
  margin: 20px auto;
}

.preview-content h2 {
  margin-top: 30px;
}

.preview-content a {
  text-decoration: underline;
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


  <!-- URL / 카테고리 -->
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

    <label class="write-label">본문</label>

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


    <!-- ★ 실제 글쓰기 공간 -->
    <textarea
      id="body"
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
        선택한 사진은 아래에 바로 표시됩니다.
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
      class="action-button primary-button"
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


<!--
  중요:
  HTML-Proofer가 이 JavaScript 내부의
  동적 URL을 HTML 링크로 오인하지 않도록
  전체 script를 검사 대상에서 제외합니다.
-->
<script data-proofer-ignore>
(function () {

  "use strict";


  var STORAGE_KEY =
    "donfree_write_final_v1";


  var title =
    document.getElementById("title");

  var slug =
    document.getElementById("slug");

  var category =
    document.getElementById("category");

  var tags =
    document.getElementById("tags");

  var seoTitle =
    document.getElementById("seoTitle");

  var seoDescription =
    document.getElementById("seoDescription");

  var body =
    document.getElementById("body");

  var imageInput =
    document.getElementById("imageInput");

  var imageList =
    document.getElementById("imageList");

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


  var images = [];

  var featured = null;


  /*
   * --------------------------------
   * 상태 메시지
   * --------------------------------
   */

  function showStatus(message) {

    status.textContent = message;

    setTimeout(function () {

      if (status.textContent === message) {
        status.textContent = "";
      }

    }, 2500);

  }


  /*
   * --------------------------------
   * ID
   * --------------------------------
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
   * --------------------------------
   * 대표 이미지
   * --------------------------------
   */

  function renderFeatured() {

    featuredPreview.innerHTML = "";

    if (!featured) {
      return;
    }

    var image =
      document.createElement("img");

    image.src = featured.src;

    image.alt =
      featured.name || "대표 이미지";

    featuredPreview.appendChild(image);

  }


  featuredInput.addEventListener(
    "change",
    function () {

      var file =
        this.files &&
        this.files[0];

      if (!file) {
        return;
      }

      var reader =
        new FileReader();

      reader.onload =
        function (event) {

          featured = {

            id: makeId(),

            name: file.name,

            src: event.target.result

          };

          renderFeatured();

          saveDraft();

          showStatus(
            "대표 이미지가 등록됐습니다."
          );

        };

      reader.readAsDataURL(file);

    }
  );


  /*
   * --------------------------------
   * 본문 이미지 첨부
   * --------------------------------
   */

  imageInput.addEventListener(
    "change",
    function () {

      var files =
        Array.from(
          this.files || []
        );

      if (!files.length) {
        return;
      }

      var completed = 0;


      files.forEach(
        function (file) {

          var reader =
            new FileReader();


          reader.onload =
            function (event) {

              images.push({

                id: makeId(),

                name: file.name,

                src: event.target.result

              });


              completed++;

              renderImages();


              if (
                completed ===
                files.length
              ) {

                saveDraft();

                showStatus(
                  files.length +
                  "장의 사진이 첨부됐습니다."
                );

                imageInput.value =
                  "";

              }

            };


          reader.readAsDataURL(file);

        }
      );

    }
  );


  /*
   * --------------------------------
   * 첨부 이미지 목록
   * --------------------------------
   */

  function renderImages() {

    imageList.innerHTML = "";


    images.forEach(
      function (item) {

        var card =
          document.createElement("div");

        card.className =
          "image-card";


        var image =
          document.createElement("img");

        image.src =
          item.src;

        image.alt =
          item.name || "첨부 이미지";


        var name =
          document.createElement("div");

        name.className =
          "image-name";

        name.textContent =
          item.name;


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

            insertImage(item);

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

            featured = {

              id: item.id,

              name: item.name,

              src: item.src

            };


            renderFeatured();

            renderImages();

            saveDraft();


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

            images =
              images.filter(
                function (image) {

                  return (
                    image.id !==
                    item.id
                  );

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

            saveDraft();


            showStatus(
              "사진을 삭제했습니다."
            );

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


        card.appendChild(
          image
        );

        card.appendChild(
          name
        );


        if (
          featured &&
          featured.id === item.id
        ) {

          var badge =
            document.createElement("div");

          badge.className =
            "featured-badge";

          badge.textContent =
            "★ 대표 이미지";

          card.appendChild(
            badge
          );

        }


        card.appendChild(
          buttons
        );

        imageList.appendChild(
          card
        );

      }
    );

  }


  /*
   * --------------------------------
   * 본문에 이미지 삽입
   * --------------------------------
   */

  function insertImage(item) {

    /*
     * textarea에는 Markdown 형식으로 넣습니다.
     */

    var imageCode =
      "\n\n!["
      + item.name
      + "]("
      + item.src
      + ")\n\n";


    var start =
      body.selectionStart;

    var end =
      body.selectionEnd;


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
      imageCode +
      after;


    var position =
      start +
      imageCode.length;


    body.focus();

    body.setSelectionRange(
      position,
      position
    );


    saveDraft();


    showStatus(
      "본문에 사진을 넣었습니다."
    );

  }


  /*
   * --------------------------------
   * 굵게
   * --------------------------------
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


  function wrapSelection(
    beforeText,
    afterText
  ) {

    var start =
      body.selectionStart;

    var end =
      body.selectionEnd;


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


    saveDraft();

  }


  /*
   * --------------------------------
   * 소제목
   * --------------------------------
   */

  document
    .getElementById("headingButton")
    .addEventListener(
      "click",
      function () {

        var start =
          body.selectionStart;

        var end =
          body.selectionEnd;


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


        saveDraft();

      }
    );


  /*
   * --------------------------------
   * 링크
   * --------------------------------
   */

  document
    .getElementById("linkButton")
    .addEventListener(
      "click",
      function () {

        var url =
          prompt(
            "링크 주소를 입력하세요."
          );


        if (!url) {
          return;
        }


        var start =
          body.selectionStart;

        var end =
          body.selectionEnd;


        var selected =
          body.value.substring(
            start,
            end
          );


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


        saveDraft();

      }
    );


  /*
   * --------------------------------
   * HTML escape
   * --------------------------------
   */

  function escapeHtml(text) {

    var div =
      document.createElement("div");

    div.textContent =
      text;

    return div.innerHTML;

  }


  /*
   * --------------------------------
   * 미리보기
   * --------------------------------
   */

  document
    .getElementById("previewButton")
    .addEventListener(
      "click",
      function () {

        previewTitle.textContent =
          title.value ||
          "제목 없음";


        previewContent.innerHTML =
          markdownToHtml(
            body.value
          );


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
   * --------------------------------
   * Markdown → HTML
   * --------------------------------
   */

  function markdownToHtml(text) {

    var html =
      escapeHtml(text);


    /*
     * 이미지
     *
     * '<img' 문자열을 코드에 직접
     * 작성하지 않습니다.
     */

    var imageTagStart =
      String.fromCharCode(60) +
      "img";


    var imageTagEnd =
      String.fromCharCode(62);


    html =
      html.replace(
        /!\[([^\]]*)\]\((data:image\/[^)]+)\)/g,
        function (
          match,
          alt,
          src
        ) {

          return (
            imageTagStart +
            ' src="' +
            src +
            '" alt="' +
            alt +
            '"' +
            imageTagEnd
          );

        }
      );


    /*
     * 링크
     */

    html =
      html.replace(
        /\[([^\]]+)\]\((https?:\/\/[^)]+)\)/g,
        function (
          match,
          text,
          url
        ) {

          var linkStart =
            String.fromCharCode(60) +
            "a";

          var linkEnd =
            String.fromCharCode(62);

          var closeLink =
            String.fromCharCode(60) +
            "/a" +
            String.fromCharCode(62);


          return (
            linkStart +
            ' href="' +
            url +
            '" target="_blank"' +
            linkEnd +
            text +
            closeLink
          );

        }
      );


    /*
     * 소제목
     */

    html =
      html.replace(
        /^### (.+)$/gm,
        "<h3>$1</h3>"
      );


    html =
      html.replace(
        /^## (.+)$/gm,
        "<h2>$1</h2>"
      );


    /*
     * 굵게
     */

    html =
      html.replace(
        /\*\*(.*?)\*\*/g,
        "<strong>$1</strong>"
      );


    /*
     * 줄바꿈
     */

    html =
      html.replace(
        /\n/g,
        "<br>"
      );


    return html;

  }


  /*
   * --------------------------------
   * 데이터
   * --------------------------------
   */

  function getData() {

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

      images:
        images,

      featured:
        featured

    };

  }


  /*
   * --------------------------------
   * 임시저장
   * --------------------------------
   */

  function saveDraft() {

    try {

      localStorage.setItem(
        STORAGE_KEY,
        JSON.stringify(
          getData()
        )
      );

    } catch (error) {

      console.warn(
        "임시저장 실패:",
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
        saveDraft
      );

    }
  );


  document
    .getElementById("saveButton")
    .addEventListener(
      "click",
      function () {

        saveDraft();

        showStatus(
          "임시저장했습니다."
        );

      }
    );


  /*
   * --------------------------------
   * 저장된 글 불러오기
   * --------------------------------
   */

  function loadDraft() {

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
        Array.isArray(
          data.images
        )
          ? data.images
          : [];


      featured =
        data.featured || null;


      renderImages();

      renderFeatured();

    } catch (error) {

      console.warn(
        "초안 불러오기 실패:",
        error
      );

    }

  }


  /*
   * --------------------------------
   * Markdown 다운로드
   * --------------------------------
   */

  document
    .getElementById("downloadButton")
    .addEventListener(
      "click",
      function () {

        if (
          !title.value.trim()
        ) {

          alert(
            "제목을 먼저 입력해주세요."
          );

          title.focus();

          return;

        }


        var now =
          new Date();


        var year =
          now.getFullYear();


        var month =
          String(
            now.getMonth() + 1
          ).padStart(
            2,
            "0"
          );


        var day =
          String(
            now.getDate()
          ).padStart(
            2,
            "0"
          );


        var date =
          year +
          "-" +
          month +
          "-" +
          day;


        var postSlug =
          slug.value.trim();


        if (!postSlug) {

          postSlug =
            title.value
              .trim()
              .toLowerCase()
              .replace(
                /\s+/g,
                "-"
              )
              .replace(
                /[^\w가-힣-]/g,
                ""
              );

        }


        var tagArray =
          tags.value
            .split(",")
            .map(
              function (tag) {
                return tag.trim();
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


        if (
          category.value.trim()
        ) {

          markdown +=
            "categories: [" +
            category.value.trim() +
            "]\n";

        }


        if (
          tagArray.length
        ) {

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


        link.href =
          url;


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


  /*
   * --------------------------------
   * 전체 삭제
   * --------------------------------
   */

  document
    .getElementById("clearButton")
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
          "작성 내용을 모두 삭제했습니다."
        );

      }
    );


  /*
   * --------------------------------
   * 시작
   * --------------------------------
   */

  loadDraft();

})();
</script>
