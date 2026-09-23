---
layout: page
title: 글쓰기
icon: fas fa-pen
order: 1
---

<style>
.write-page {
  max-width: 100%;
}

.write-field {
  margin-bottom: 18px;
}

.write-field > label {
  display: block;
  font-weight: 700;
  margin-bottom: 7px;
}

.write-field input {
  width: 100%;
  box-sizing: border-box;
  border: 1px solid #d7dce2;
  border-radius: 8px;
  padding: 11px 12px;
  font-size: 15px;
  background: #fff;
  color: #222;
}

/* 대표 이미지 */

.featured-area {
  border: 1px dashed #c8ced6;
  border-radius: 10px;
  padding: 18px;
  margin: 22px 0;
  background: #fafbfc;
}

.featured-help {
  color: #777;
  font-size: 13px;
  margin-top: 6px;
}

.featured-preview {
  display: none;
  margin-top: 15px;
  text-align: center;
}

.featured-preview img {
  max-width: 100%;
  max-height: 300px;
  object-fit: contain;
  border-radius: 8px;
}

.featured-buttons {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
  margin-top: 12px;
}

.featured-input {
  display: none;
}

/* 버튼 */

.write-button {
  display: inline-block;
  border: 0;
  border-radius: 7px;
  padding: 9px 14px;
  cursor: pointer;
  background: #343a40;
  color: #fff;
  font-size: 14px;
  font-weight: 600;
  text-decoration: none;
}

.write-button:hover {
  opacity: .86;
}

.write-button.primary {
  background: #1769aa;
}

.write-button.danger {
  background: #c0392b;
}

/* 에디터 */

.editor-toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 7px;
  padding: 9px;
  border: 1px solid #d7dce2;
  border-bottom: 0;
  border-radius: 9px 9px 0 0;
  background: #f6f7f8;
}

.editor-toolbar button {
  border: 1px solid #d5d9de;
  background: #fff;
  color: #222;
  border-radius: 6px;
  padding: 7px 11px;
  cursor: pointer;
  font-size: 13px;
}

.editor-toolbar button:hover {
  background: #eef2f5;
}

.editor-wrapper {
  position: relative;
}

#postEditor {
  min-height: 500px;
  border: 1px solid #d7dce2;
  border-radius: 0 0 9px 9px;
  padding: 20px;
  background: #fff;
  color: #222;
  font-size: 16px;
  line-height: 1.8;
  outline: none;
  overflow-wrap: anywhere;
}

#postEditor:focus {
  border-color: #1769aa;
}

#postEditor:empty::before {
  content: attr(data-placeholder);
  color: #999;
  pointer-events: none;
  white-space: pre-line;
}

/* 본문 이미지 */

.editor-image {
  display: block;
  max-width: 100%;
  height: auto;
  margin: 18px auto;
  border-radius: 6px;
  cursor: default;
  user-select: none;
}

.editor-image.selected {
  outline: 2px solid #1769aa;
  outline-offset: 2px;
}

/* 크기 조절 핸들 */

.resize-handle {
  position: absolute;
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: #1769aa;
  border: 2px solid #fff;
  box-sizing: border-box;
  cursor: nwse-resize;
  display: none;
  z-index: 9999;
}

/* 안내 */

.editor-help {
  color: #777;
  font-size: 13px;
  margin-top: 8px;
}

/* 이미지 추가 */

.image-add-area {
  border: 1px dashed #bfc6ce;
  border-radius: 9px;
  padding: 16px;
  margin: 18px 0;
  background: #fafbfc;
}

.image-file-input {
  display: none;
}

/* 액션 */

.editor-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 20px;
}

/* 미리보기 */

.preview-box {
  display: none;
  border: 1px solid #dfe3e8;
  border-radius: 10px;
  padding: 22px;
  margin-top: 25px;
  background: #fff;
  color: #222;
  line-height: 1.8;
  overflow-wrap: anywhere;
}

.preview-box img {
  display: block;
  max-width: 100%;
  height: auto;
  margin: 20px auto;
  border-radius: 6px;
}

.preview-box a {
  color: #1769aa;
}

.status-message {
  margin-top: 12px;
  color: #1769aa;
  font-size: 13px;
}

@media (max-width: 600px) {

  #postEditor {
    min-height: 450px;
    padding: 14px;
    font-size: 15px;
  }

  .editor-toolbar {
    gap: 5px;
  }

  .editor-toolbar button {
    padding: 6px 8px;
    font-size: 12px;
  }
}
</style>


<div class="write-page">

  <!-- 제목 -->

  <div class="write-field">
    <label for="postTitle">글 제목</label>

    <input
      id="postTitle"
      type="text"
      placeholder="글 제목을 입력하세요">
  </div>


  <!-- 주소 -->

  <div class="write-field">
    <label for="postSlug">주소용 영문 이름</label>

    <input
      id="postSlug"
      type="text"
      placeholder="예: instagram-reels-download">
  </div>


  <!-- 카테고리 -->

  <div class="write-field">
    <label for="postCategory">카테고리</label>

    <input
      id="postCategory"
      type="text"
      placeholder="예: 생활정보">
  </div>


  <!-- 태그 -->

  <div class="write-field">
    <label for="postTags">태그</label>

    <input
      id="postTags"
      type="text"
      placeholder="인스타, 릴스, 다운로드">
  </div>


  <!-- SEO -->

  <div class="write-field">
    <label for="seoTitle">SEO 제목</label>

    <input
      id="seoTitle"
      type="text"
      placeholder="검색 결과에 표시할 제목">
  </div>


  <div class="write-field">
    <label for="seoDescription">SEO 설명</label>

    <input
      id="seoDescription"
      type="text"
      placeholder="검색 결과에 표시할 설명">
  </div>


  <!-- 대표 이미지 -->

  <div class="featured-area">

    <strong>대표 이미지</strong>

    <div class="featured-help">
      블로그 글의 대표 이미지로 사용할 사진을 한 장 선택하세요.
    </div>

    <div class="featured-buttons">

      <label
        for="featuredImageInput"
        class="write-button primary">
        대표 이미지 선택
      </label>

      <input
        id="featuredImageInput"
        class="featured-input"
        type="file"
        accept="image/*">

      <button
        type="button"
        id="removeFeatured"
        class="write-button danger">
        대표 이미지 삭제
      </button>

    </div>

    <div
      id="featuredPreview"
      class="featured-preview">

      <img
        id="featuredPreviewImage"
        alt="대표 이미지">

    </div>

  </div>


  <!-- 본문 -->

  <div class="write-field">

    <label>본문</label>

    <div class="editor-toolbar">

      <button
        type="button"
        id="boldButton">
        굵게
      </button>

      <button
        type="button"
        id="headingButton">
        소제목
      </button>

      <button
        type="button"
        id="linkButton">
        링크
      </button>

      <button
        type="button"
        id="removeFormatButton">
        서식 제거
      </button>

    </div>


    <div
      id="editorWrapper"
      class="editor-wrapper">

      <div
        id="postEditor"
        contenteditable="true"
        data-placeholder="여기에 글을 작성하세요.

사진을 넣으려면 아래의 '사진 여러 장 추가'를 이용하세요.">
      </div>

      <div
        id="resizeHandle"
        class="resize-handle">
      </div>

    </div>


    <div class="editor-help">
      사진을 클릭하면 선택됩니다.
      오른쪽 아래 파란 점을 드래그하면 사진 크기를 바로 조절할 수 있습니다.
    </div>

  </div>


  <!-- 여러 장 이미지 -->

  <div class="image-add-area">

    <label
      for="bodyImageInput"
      class="write-button primary">
      사진 여러 장 추가
    </label>

    <input
      id="bodyImageInput"
      class="image-file-input"
      type="file"
      accept="image/*"
      multiple>

    <div class="editor-help">
      여러 장의 사진을 한꺼번에 선택할 수 있습니다.
    </div>

  </div>


  <!-- 버튼 -->

  <div class="editor-actions">

    <button
      type="button"
      id="previewButton"
      class="write-button">
      미리보기
    </button>

    <button
      type="button"
      id="saveButton"
      class="write-button primary">
      임시저장
    </button>

    <button
      type="button"
      id="loadButton"
      class="write-button">
      임시저장 불러오기
    </button>

    <button
      type="button"
      id="downloadButton"
      class="write-button primary">
      글 파일 만들기
    </button>

    <button
      type="button"
      id="clearButton"
      class="write-button danger">
      전체 초기화
    </button>

  </div>


  <div
    id="statusMessage"
    class="status-message">
  </div>


  <!-- 미리보기 -->

  <div
    id="previewBox"
    class="preview-box">
  </div>

</div>


<script>
(function () {

  "use strict";


  const editor =
    document.getElementById("postEditor");

  const editorWrapper =
    document.getElementById("editorWrapper");

  const resizeHandle =
    document.getElementById("resizeHandle");

  const statusMessage =
    document.getElementById("statusMessage");

  const previewBox =
    document.getElementById("previewBox");


  const titleInput =
    document.getElementById("postTitle");

  const slugInput =
    document.getElementById("postSlug");

  const categoryInput =
    document.getElementById("postCategory");

  const tagsInput =
    document.getElementById("postTags");

  const seoTitleInput =
    document.getElementById("seoTitle");

  const seoDescriptionInput =
    document.getElementById("seoDescription");


  const featuredInput =
    document.getElementById("featuredImageInput");

  const featuredPreview =
    document.getElementById("featuredPreview");

  const featuredPreviewImage =
    document.getElementById("featuredPreviewImage");


  const bodyImageInput =
    document.getElementById("bodyImageInput");


  let featuredImage = null;

  let selectedImage = null;

  let resizing = false;

  let resizeStartX = 0;

  let resizeStartWidth = 0;


  /*
  ----------------------------------------
  상태 메시지
  ----------------------------------------
  */

  function showStatus(message) {

    statusMessage.textContent = message;

  }


  /*
  ----------------------------------------
  대표 이미지
  ----------------------------------------
  */

  featuredInput.addEventListener(
    "change",
    function () {

      const file =
        featuredInput.files &&
        featuredInput.files[0];

      if (!file) {
        return;
      }


      const reader =
        new FileReader();


      reader.onload =
        function (event) {

          featuredImage = {
            name: file.name,
            src: event.target.result
          };


          featuredPreviewImage.src =
            featuredImage.src;


          featuredPreview.style.display =
            "block";


          saveDraft();


          showStatus(
            "대표 이미지를 지정했습니다."
          );

        };


      reader.readAsDataURL(file);

    }
  );


  document
    .getElementById("removeFeatured")
    .addEventListener(
      "click",
      function () {

        featuredImage = null;

        featuredInput.value = "";

        featuredPreviewImage.removeAttribute(
          "src"
        );

        featuredPreview.style.display =
          "none";

        saveDraft();

        showStatus(
          "대표 이미지를 삭제했습니다."
        );

      }
    );


  /*
  ----------------------------------------
  본문 이미지 여러 장 추가
  ----------------------------------------
  */

  bodyImageInput.addEventListener(
    "change",
    function () {

      const files =
        Array.from(
          bodyImageInput.files || []
        );


      if (!files.length) {
        return;
      }


      files.forEach(
        function (file) {

          if (
            !file.type ||
            !file.type.startsWith("image/")
          ) {
            return;
          }


          const reader =
            new FileReader();


          reader.onload =
            function (event) {

              insertImage(
                event.target.result,
                file.name
              );

            };


          reader.readAsDataURL(file);

        }
      );


      bodyImageInput.value = "";

    }
  );


  /*
  ----------------------------------------
  현재 커서 위치
  ----------------------------------------
  */

  function getEditorRange() {

    const selection =
      window.getSelection();


    if (
      !selection ||
      !selection.rangeCount
    ) {

      return null;

    }


    const range =
      selection.getRangeAt(0);


    if (
      editor.contains(
        range.commonAncestorContainer
      )
    ) {

      return range;

    }


    return null;

  }


  /*
  ----------------------------------------
  이미지 삽입
  ----------------------------------------
  */

  function insertImage(
    src,
    filename
  ) {

    editor.focus();


    let range =
      getEditorRange();


    if (!range) {

      range =
        document.createRange();

      range.selectNodeContents(
        editor
      );

      range.collapse(false);

    }


    const image =
      document.createElement("img");


    image.className =
      "editor-image";


    image.src =
      src;


    image.alt =
      filename || "이미지";


    image.style.width =
      "70%";


    image.style.height =
      "auto";


    /*
    이미지 앞에 줄
    */

    const before =
      document.createElement("div");

    before.innerHTML =
      "<br>";


    /*
    이미지 뒤에 줄
    */

    const after =
      document.createElement("div");

    after.innerHTML =
      "<br>";


    range.deleteContents();

    range.insertNode(after);

    range.insertNode(image);

    range.insertNode(before);


    /*
    이미지 뒤에 커서
    */

    const newRange =
      document.createRange();


    newRange.setStartAfter(
      after
    );


    newRange.collapse(true);


    const selection =
      window.getSelection();


    selection.removeAllRanges();

    selection.addRange(
      newRange
    );


    selectImage(image);


    saveDraft();


    showStatus(
      "이미지를 본문에 추가했습니다."
    );

  }


  /*
  ----------------------------------------
  이미지 선택
  ----------------------------------------
  */

  function selectImage(image) {

    if (selectedImage) {

      selectedImage.classList.remove(
        "selected"
      );

    }


    selectedImage =
      image;


    selectedImage.classList.add(
      "selected"
    );


    positionHandle();

  }


  /*
  ----------------------------------------
  이미지 선택 해제
  ----------------------------------------
  */

  function deselectImage() {

    if (selectedImage) {

      selectedImage.classList.remove(
        "selected"
      );

    }


    selectedImage = null;


    resizeHandle.style.display =
      "none";

  }


  /*
  ----------------------------------------
  이미지 클릭
  ----------------------------------------
  */

  editor.addEventListener(
    "click",
    function (event) {

      if (
        event.target &&
        event.target.tagName === "IMG"
      ) {

        event.preventDefault();

        selectImage(
          event.target
        );

      }

    }
  );


  /*
  ----------------------------------------
  크기 조절점 위치
  ----------------------------------------
  */

  function positionHandle() {

    if (!selectedImage) {

      resizeHandle.style.display =
        "none";

      return;

    }


    const imageRect =
      selectedImage.getBoundingClientRect();


    const wrapperRect =
      editorWrapper.getBoundingClientRect();


    resizeHandle.style.display =
      "block";


    resizeHandle.style.left =
      (
        imageRect.right -
        wrapperRect.left -
        7
      ) + "px";


    resizeHandle.style.top =
      (
        imageRect.bottom -
        wrapperRect.top -
        7
      ) + "px";

  }


  window.addEventListener(
    "resize",
    positionHandle
  );


  /*
  ----------------------------------------
  드래그 시작
  ----------------------------------------
  */

  resizeHandle.addEventListener(
    "mousedown",
    function (event) {

      if (!selectedImage) {
        return;
      }


      event.preventDefault();

      event.stopPropagation();


      resizing = true;


      resizeStartX =
        event.clientX;


      resizeStartWidth =
        selectedImage.getBoundingClientRect().width;


      document.body.style.userSelect =
        "none";

    }
  );


  /*
  ----------------------------------------
  드래그 중
  ----------------------------------------
  */

  document.addEventListener(
    "mousemove",
    function (event) {

      if (
        !resizing ||
        !selectedImage
      ) {
        return;
      }


      const difference =
        event.clientX -
        resizeStartX;


      const editorWidth =
        editor.clientWidth - 40;


      let newWidth =
        resizeStartWidth +
        difference;


      newWidth =
        Math.max(
          100,
          Math.min(
            newWidth,
            editorWidth
          )
        );


      selectedImage.style.width =
        newWidth + "px";


      selectedImage.style.height =
        "auto";


      positionHandle();

    }
  );


  /*
  ----------------------------------------
  드래그 종료
  ----------------------------------------
  */

  document.addEventListener(
    "mouseup",
    function () {

      if (!resizing) {
        return;
      }


      resizing = false;


      document.body.style.userSelect =
        "";


      saveDraft();


      showStatus(
        "이미지 크기를 변경했습니다."
      );

    }
  );


  /*
  ----------------------------------------
  Delete 키로 이미지 삭제
  ----------------------------------------
  */

  document.addEventListener(
    "keydown",
    function (event) {

      if (
        event.key !== "Delete" ||
        !selectedImage
      ) {

        return;

      }


      if (
        document.activeElement !== editor
      ) {

        return;

      }


      event.preventDefault();


      selectedImage.remove();


      selectedImage = null;


      resizeHandle.style.display =
        "none";


      saveDraft();


      showStatus(
        "선택한 이미지를 삭제했습니다."
      );

    }
  );


  /*
  ----------------------------------------
  굵게
  ----------------------------------------
  */

  document
    .getElementById("boldButton")
    .addEventListener(
      "click",
      function () {

        editor.focus();

        document.execCommand(
          "bold",
          false,
          null
        );

        saveDraft();

      }
    );


  /*
  ----------------------------------------
  소제목
  ----------------------------------------
  */

  document
    .getElementById("headingButton")
    .addEventListener(
      "click",
      function () {

        editor.focus();

        document.execCommand(
          "formatBlock",
          false,
          "h2"
        );

        saveDraft();

      }
    );


  /*
  ----------------------------------------
  링크
  ----------------------------------------
  */

  document
    .getElementById("linkButton")
    .addEventListener(
      "click",
      function () {

        const url =
          prompt(
            "링크 주소를 입력하세요."
          );


        if (!url) {
          return;
        }


        editor.focus();


        document.execCommand(
          "createLink",
          false,
          url
        );


        saveDraft();

      }
    );


  /*
  ----------------------------------------
  서식 제거
  ----------------------------------------
  */

  document
    .getElementById(
      "removeFormatButton"
    )
    .addEventListener(
      "click",
      function () {

        editor.focus();


        document.execCommand(
          "removeFormat",
          false,
          null
        );


        saveDraft();

      }
    );


  /*
  ----------------------------------------
  HTML 요소 → 글 파일용 HTML
  ----------------------------------------
  */

  function nodeToOutput(node) {

    if (
      node.nodeType ===
      Node.TEXT_NODE
    ) {

      return node.textContent;

    }


    if (
      node.nodeType !==
      Node.ELEMENT_NODE
    ) {

      return "";

    }


    const tag =
      node.tagName.toLowerCase();


    /*
    이미지 태그는 문자열을
    조합해서 생성한다.

    GitHub HTML-Proofer가
    JavaScript 안의 <img src=...
    를 실제 HTML로 오인하지 않도록
    처리한다.
    */

    if (tag === "img") {

      const src =
        node.getAttribute("src") || "";


      const alt =
        node.getAttribute("alt") ||
        "image";


      const width =
        node.style.width ||
        "70%";


      const imageOpen =
        String.fromCharCode(60) +
        "img";


      const imageClose =
        String.fromCharCode(62);


      return (
        imageOpen +
        ' src="' +
        src +
        '" alt="' +
        alt.replace(
          /"/g,
          "&quot;"
        ) +
        '" style="width:' +
        width +
        ';max-width:100%;height:auto;"' +
        imageClose
      );

    }


    let content = "";


    Array.from(
      node.childNodes
    ).forEach(
      function (child) {

        content +=
          nodeToOutput(child);

      }
    );


    if (
      tag === "strong" ||
      tag === "b"
    ) {

      return (
        "**" +
        content +
        "**"
      );

    }


    if (tag === "h1") {

      return (
        "\n\n# " +
        content +
        "\n\n"
      );

    }


    if (tag === "h2") {

      return (
        "\n\n## " +
        content +
        "\n\n"
      );

    }


    if (tag === "h3") {

      return (
        "\n\n### " +
        content +
        "\n\n"
      );

    }


    if (tag === "a") {

      const href =
        node.getAttribute("href") ||
        "";


      return (
        "[" +
        content +
        "](" +
        href +
        ")"
      );

    }


    if (tag === "br") {

      return "\n";

    }


    if (
      tag === "div" ||
      tag === "p"
    ) {

      return (
        "\n\n" +
        content +
        "\n\n"
      );

    }


    return content;

  }


  /*
  ----------------------------------------
  본문 가져오기
  ----------------------------------------
  */

  function getPostBody() {

    let result = "";


    Array.from(
      editor.childNodes
    ).forEach(
      function (node) {

        result +=
          nodeToOutput(node);

      }
    );


    return result
      .replace(
        /\n{4,}/g,
        "\n\n"
      )
      .trim();

  }


  /*
  ----------------------------------------
  미리보기
  ----------------------------------------
  */

  document
    .getElementById("previewButton")
    .addEventListener(
      "click",
      function () {

        previewBox.innerHTML =
          editor.innerHTML;


        previewBox.style.display =
          "block";


        previewBox.scrollIntoView({
          behavior: "smooth",
          block: "start"
        });

      }
    );


  /*
  ----------------------------------------
  저장 데이터
  ----------------------------------------
  */

  function collectData() {

    return {

      title:
        titleInput.value,

      slug:
        slugInput.value,

      category:
        categoryInput.value,

      tags:
        tagsInput.value,

      seoTitle:
        seoTitleInput.value,

      seoDescription:
        seoDescriptionInput.value,

      body:
        editor.innerHTML,

      featuredImage:
        featuredImage

    };

  }


  /*
  ----------------------------------------
  임시저장
  ----------------------------------------
  */

  function saveDraft() {

    try {

      localStorage.setItem(
        "donfreeWriteDraft",
        JSON.stringify(
          collectData()
        )
      );

    } catch (error) {

      console.warn(
        "임시저장 실패",
        error
      );

    }

  }


  document
    .getElementById("saveButton")
    .addEventListener(
      "click",
      function () {

        saveDraft();


        showStatus(
          "현재 글을 임시저장했습니다."
        );

      }
    );


  /*
  ----------------------------------------
  임시저장 불러오기
  ----------------------------------------
  */

  document
    .getElementById("loadButton")
    .addEventListener(
      "click",
      function () {

        const saved =
          localStorage.getItem(
            "donfreeWriteDraft"
          );


        if (!saved) {

          showStatus(
            "저장된 글이 없습니다."
          );

          return;

        }


        try {

          const data =
            JSON.parse(saved);


          titleInput.value =
            data.title || "";


          slugInput.value =
            data.slug || "";


          categoryInput.value =
            data.category || "";


          tagsInput.value =
            data.tags || "";


          seoTitleInput.value =
            data.seoTitle || "";


          seoDescriptionInput.value =
            data.seoDescription || "";


          editor.innerHTML =
            data.body || "";


          featuredImage =
            data.featuredImage || null;


          if (featuredImage) {

            featuredPreviewImage.src =
              featuredImage.src;


            featuredPreview.style.display =
              "block";

          } else {

            featuredPreview.style.display =
              "none";

          }


          deselectImage();


          showStatus(
            "임시저장한 글을 불러왔습니다."
          );

        } catch (error) {

          showStatus(
            "저장된 글을 불러오는 중 오류가 발생했습니다."
          );

        }

      }
    );


  /*
  ----------------------------------------
  글 파일 만들기
  ----------------------------------------
  */

  document
    .getElementById("downloadButton")
    .addEventListener(
      "click",
      function () {

        const title =
          titleInput.value.trim() ||
          "untitled";


        const slug =
          slugInput.value.trim() ||
          "untitled";


        const category =
          categoryInput.value.trim() ||
          "생활정보";


        const tags =
          tagsInput.value
            .split(",")
            .map(
              function (tag) {

                return tag.trim();

              }
            )
            .filter(Boolean);


        const seoTitle =
          seoTitleInput.value.trim() ||
          title;


        const seoDescription =
          seoDescriptionInput.value.trim() ||
          "";


        const today =
          new Date();


        const dateString =
          today.getFullYear() +
          "-" +
          String(
            today.getMonth() + 1
          ).padStart(2, "0") +
          "-" +
          String(
            today.getDate()
          ).padStart(2, "0");


        const body =
          getPostBody();


        /*
        대표 이미지는
        현재 선택한 이미지를
        front matter에 기록한다.
        */

        let imageFrontMatter = "";


        if (featuredImage) {

          imageFrontMatter =
            "image:\n" +
            "  path: \"" +
            featuredImage.src +
            "\"\n";

        }


        const frontMatter =
          "---\n" +

          "title: \"" +
          title.replace(
            /"/g,
            '\\"'
          ) +
          "\"\n" +

          "date: " +
          dateString +
          "\n" +

          "categories: [\"" +
          category.replace(
            /"/g,
            '\\"'
          ) +
          "\"]\n" +

          "tags: [" +

          tags.map(
            function (tag) {

              return (
                '"' +
                tag.replace(
                  /"/g,
                  '\\"'
                ) +
                '"'
              );

            }
          ).join(", ") +

          "]\n" +

          "description: \"" +
          seoDescription.replace(
            /"/g,
            '\\"'
          ) +
          "\"\n" +

          "seo_title: \"" +
          seoTitle.replace(
            /"/g,
            '\\"'
          ) +
          "\"\n" +

          imageFrontMatter +

          "permalink: /posts/" +
          slug +
          "/\n" +

          "---\n\n";


        const finalContent =
          frontMatter +
          body;


        const blob =
          new Blob(
            [finalContent],
            {
              type:
                "text/markdown;charset=utf-8"
            }
          );


        const downloadUrl =
          URL.createObjectURL(blob);


        const link =
          document.createElement("a");


        link.href =
          downloadUrl;


        link.download =
          dateString +
          "-" +
          slug +
          ".md";


        document.body.appendChild(
          link
        );


        link.click();


        link.remove();


        URL.revokeObjectURL(
          downloadUrl
        );


        showStatus(
          "글 파일을 만들었습니다."
        );

      }
    );


  /*
  ----------------------------------------
  전체 초기화
  ----------------------------------------
  */

  document
    .getElementById("clearButton")
    .addEventListener(
      "click",
      function () {

        const confirmed =
          confirm(
            "작성한 글과 이미지를 모두 삭제할까요?"
          );


        if (!confirmed) {
          return;
        }


        titleInput.value = "";

        slugInput.value = "";

        categoryInput.value = "";

        tagsInput.value = "";

        seoTitleInput.value = "";

        seoDescriptionInput.value = "";


        editor.innerHTML = "";


        featuredImage = null;


        featuredInput.value = "";


        featuredPreviewImage.removeAttribute(
          "src"
        );


        featuredPreview.style.display =
          "none";


        bodyImageInput.value = "";


        deselectImage();


        localStorage.removeItem(
          "donfreeWriteDraft"
        );


        previewBox.innerHTML = "";

        previewBox.style.display =
          "none";


        showStatus(
          "전체 내용을 초기화했습니다."
        );

      }
    );


  /*
  ----------------------------------------
  자동 임시저장
  ----------------------------------------
  */

  editor.addEventListener(
    "input",
    function () {

      saveDraft();

    }
  );


  [
    titleInput,
    slugInput,
    categoryInput,
    tagsInput,
    seoTitleInput,
    seoDescriptionInput

  ].forEach(
    function (input) {

      input.addEventListener(
        "input",
        function () {

          saveDraft();

        }
      );

    }
  );


  /*
  ----------------------------------------
  바깥 클릭 시 선택 해제
  ----------------------------------------
  */

  document.addEventListener(
    "click",
    function (event) {

      if (
        event.target === selectedImage ||
        event.target === resizeHandle
      ) {

        return;

      }


      if (
        event.target.closest &&
        event.target.closest(
          "#postEditor"
        )
      ) {

        return;

      }


      deselectImage();

    }
  );


})();
</script>
