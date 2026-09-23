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

.write-button.small {
  padding: 7px 10px;
  font-size: 12px;
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
  cursor: pointer;
  user-select: none;
}

.editor-image.selected {
  outline: 2px solid #1769aa;
  outline-offset: 3px;
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

/* 첨부 이미지 목록 */

.image-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  gap: 12px;
  margin-top: 15px;
}

.image-item {
  border: 1px solid #d9dee4;
  border-radius: 9px;
  padding: 9px;
  background: #fff;
}

.image-item-thumb {
  width: 100%;
  height: 120px;
  object-fit: contain;
  display: block;
  border-radius: 6px;
  background: #f5f6f7;
}

.image-item-name {
  font-size: 12px;
  color: #555;
  margin-top: 7px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.image-item-buttons {
  display: flex;
  gap: 5px;
  flex-wrap: wrap;
  margin-top: 8px;
}

.image-item-buttons button {
  border: 1px solid #d5d9de;
  background: #fff;
  border-radius: 5px;
  padding: 5px 7px;
  cursor: pointer;
  font-size: 11px;
}

.image-item-buttons button:hover {
  background: #f1f3f5;
}

.image-item-buttons .image-delete {
  color: #c0392b;
}

/* 대표 이미지 표시 */

.image-item.featured-selected {
  border: 2px solid #1769aa;
}

.featured-badge {
  display: none;
  font-size: 11px;
  color: #1769aa;
  font-weight: 700;
  margin-top: 5px;
}

.image-item.featured-selected .featured-badge {
  display: block;
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

  .image-list {
    grid-template-columns: repeat(2, 1fr);
  }

  .image-item-thumb {
    height: 100px;
  }
}
</style>


<div class="write-page">

  <div class="write-field">
    <label for="postTitle">글 제목</label>
    <input
      id="postTitle"
      type="text"
      placeholder="글 제목을 입력하세요">
  </div>


  <div class="write-field">
    <label for="postSlug">주소용 영문 이름</label>
    <input
      id="postSlug"
      type="text"
      placeholder="예: instagram-reels-download">
  </div>


  <div class="write-field">
    <label for="postCategory">카테고리</label>
    <input
      id="postCategory"
      type="text"
      placeholder="예: 생활정보">
  </div>


  <div class="write-field">
    <label for="postTags">태그</label>
    <input
      id="postTags"
      type="text"
      placeholder="인스타, 릴스, 다운로드">
  </div>


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
      아래 첨부 사진 중 하나를 대표 이미지로 지정할 수 있습니다.
    </div>

    <div class="featured-buttons">

      <label
        for="featuredImageInput"
        class="write-button primary">
        대표 이미지 직접 선택
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

사진을 넣으려면 아래 첨부 사진에서 '본문에 넣기'를 누르세요.">
      </div>

      <div
        id="resizeHandle"
        class="resize-handle">
      </div>

    </div>


    <div class="editor-help">
      본문 사진을 클릭한 뒤 오른쪽 아래 파란 점을 드래그하면 크기를 조절할 수 있습니다.
    </div>

  </div>


  <!-- 사진 추가 -->

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
      여러 장을 한꺼번에 선택할 수 있습니다.
    </div>

    <div
      id="imageList"
      class="image-list">
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

  const imageList =
    document.getElementById("imageList");


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


  let attachedImages = [];

  let featuredImage = null;

  let selectedImage = null;

  let resizing = false;

  let resizeStartX = 0;

  let resizeStartWidth = 0;


  function showStatus(message) {

    statusMessage.textContent = message;

  }


  /*
  ========================================
  이미지 첨부 목록
  ========================================
  */

  function renderImageList() {

    imageList.innerHTML = "";


    attachedImages.forEach(
      function (imageData, index) {

        const item =
          document.createElement("div");

        item.className =
          "image-item";


        if (
          featuredImage &&
          featuredImage.id === imageData.id
        ) {

          item.classList.add(
            "featured-selected"
          );

        }


        const thumbnail =
          document.createElement("img");

        thumbnail.className =
          "image-item-thumb";

        thumbnail.src =
          imageData.src;

        thumbnail.alt =
          imageData.name;


        const name =
          document.createElement("div");

        name.className =
          "image-item-name";

        name.textContent =
          imageData.name;


        const badge =
          document.createElement("div");

        badge.className =
          "featured-badge";

        badge.textContent =
          "★ 대표 이미지";


        const buttons =
          document.createElement("div");

        buttons.className =
          "image-item-buttons";


        const insertButton =
          document.createElement("button");

        insertButton.type =
          "button";

        insertButton.textContent =
          "본문에 넣기";


        insertButton.addEventListener(
          "click",
          function () {

            insertImage(
              imageData.src,
              imageData.name
            );

          }
        );


        const featuredButton =
          document.createElement("button");

        featuredButton.type =
          "button";

        featuredButton.textContent =
          "대표 이미지";


        featuredButton.addEventListener(
          "click",
          function () {

            setFeaturedImage(
              imageData
            );

          }
        );


        const deleteButton =
          document.createElement("button");

        deleteButton.type =
          "button";

        deleteButton.className =
          "image-delete";

        deleteButton.textContent =
          "삭제";


        deleteButton.addEventListener(
          "click",
          function () {

            if (
              featuredImage &&
              featuredImage.id === imageData.id
            ) {

              featuredImage = null;

              featuredPreview.style.display =
                "none";

              featuredPreviewImage.removeAttribute(
                "src"
              );

            }


            attachedImages.splice(
              index,
              1
            );


            renderImageList();

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


        item.appendChild(
          thumbnail
        );

        item.appendChild(
          name
        );

        item.appendChild(
          badge
        );

        item.appendChild(
          buttons
        );


        imageList.appendChild(
          item
        );

      }
    );

  }


  /*
  ========================================
  대표 이미지
  ========================================
  */

  function setFeaturedImage(
    imageData
  ) {

    featuredImage = {
      id: imageData.id,
      name: imageData.name,
      src: imageData.src
    };


    featuredPreviewImage.src =
      imageData.src;


    featuredPreview.style.display =
      "block";


    renderImageList();

    saveDraft();


    showStatus(
      "대표 이미지를 지정했습니다."
    );

  }


  featuredInput.addEventListener(
    "change",
    function () {

      const file =
        featuredInput.files &&
        featuredInput.files[0];


      if (!file) {
        return;
      }


      if (
        !file.type ||
        !file.type.startsWith("image/")
      ) {

        showStatus(
          "이미지 파일만 선택할 수 있습니다."
        );

        return;

      }


      const reader =
        new FileReader();


      reader.onload =
        function (event) {

          const imageData = {

            id:
              "featured-" +
              Date.now(),

            name:
              file.name,

            src:
              event.target.result

          };


          featuredImage =
            imageData;


          featuredPreviewImage.src =
            imageData.src;


          featuredPreview.style.display =
            "block";


          saveDraft();


          showStatus(
            "대표 이미지를 지정했습니다."
          );

        };


      reader.onerror =
        function () {

          showStatus(
            "대표 이미지를 읽지 못했습니다."
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


        renderImageList();

        saveDraft();


        showStatus(
          "대표 이미지를 삭제했습니다."
        );

      }
    );


  /*
  ========================================
  본문 이미지 파일 선택
  ========================================
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


      let completed = 0;


      files.forEach(
        function (file) {

          if (
            !file.type ||
            !file.type.startsWith("image/")
          ) {

            completed++;

            return;

          }


          const reader =
            new FileReader();


          reader.onload =
            function (event) {

              attachedImages.push({

                id:
                  "image-" +
                  Date.now() +
                  "-" +
                  Math.random()
                    .toString(36)
                    .slice(2),

                name:
                  file.name,

                src:
                  event.target.result

              });


              completed++;


              renderImageList();


              if (
                completed === files.length
              ) {

                saveDraft();

                showStatus(
                  files.length +
                  "장의 사진을 첨부했습니다."
                );

              }

            };


          reader.onerror =
            function () {

              completed++;


              if (
                completed === files.length
              ) {

                renderImageList();

                saveDraft();

                showStatus(
                  "일부 사진을 읽지 못했습니다."
                );

              }

            };


          reader.readAsDataURL(file);

        }
      );


      bodyImageInput.value = "";

    }
  );


  /*
  ========================================
  에디터 커서
  ========================================
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
  ========================================
  본문 이미지 삽입
  ========================================
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


    range.deleteContents();


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


    const wrapper =
      document.createElement("div");

    wrapper.style.textAlign =
      "center";

    wrapper.style.margin =
      "18px 0";


    wrapper.appendChild(
      image
    );


    const after =
      document.createElement("div");

    after.innerHTML =
      "<br>";


    range.insertNode(
      wrapper
    );


    wrapper.parentNode.insertBefore(
      after,
      wrapper.nextSibling
    );


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


    selectImage(
      image
    );


    saveDraft();


    showStatus(
      "이미지를 본문에 넣었습니다."
    );

  }


  /*
  ========================================
  이미지 선택
  ========================================
  */

  function selectImage(
    image
  ) {

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
  ========================================
  크기 조절 핸들
  ========================================
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
  ========================================
  이미지 크기 드래그
  ========================================
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
  ========================================
  Delete 이미지
  ========================================
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
  ========================================
  서식
  ========================================
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
  ========================================
  HTML → Markdown
  ========================================
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
  ========================================
  미리보기
  ========================================
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
  ========================================
  데이터
  ========================================
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

      attachedImages:
        attachedImages,

      featuredImage:
        featuredImage

    };

  }


  /*
  ========================================
  임시저장
  ========================================
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
  ========================================
  임시저장 불러오기
  ========================================
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


          attachedImages =
            Array.isArray(
              data.attachedImages
            )
              ? data.attachedImages
              : [];


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


          renderImageList();


          deselectImage();


          showStatus(
            "임시저장한 글을 불러왔습니다."
          );

        } catch (error) {

          console.error(
            error
          );


          showStatus(
            "저장된 글을 불러오는 중 오류가 발생했습니다."
          );

        }

      }
    );


  /*
  ========================================
  글 파일 만들기
  ========================================
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
  ========================================
  전체 초기화
  ========================================
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


        attachedImages = [];

        featuredImage = null;


        featuredInput.value = "";

        bodyImageInput.value = "";


        featuredPreviewImage.removeAttribute(
          "src"
        );


        featuredPreview.style.display =
          "none";


        imageList.innerHTML = "";


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
  ========================================
  자동 저장
  ========================================
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
  ========================================
  바깥 클릭
  ========================================
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
