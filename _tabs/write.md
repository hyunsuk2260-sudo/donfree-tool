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

.write-section {
  margin-bottom: 24px;
}

.write-label {
  display: block;
  font-weight: 700;
  font-size: 15px;
  margin-bottom: 8px;
}

.write-input,
.write-select,
.write-textarea {
  width: 100%;
  box-sizing: border-box;
  border: 1px solid #d9d9d9;
  border-radius: 8px;
  padding: 12px 14px;
  font-size: 15px;
  background: #fff;
  color: #222;
}

.write-input:focus,
.write-select:focus,
.write-textarea:focus,
.editor:focus {
  outline: none;
  border-color: #777;
}

.write-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.editor {
  min-height: 600px;
  width: 100%;
  box-sizing: border-box;
  border: 1px solid #d9d9d9;
  border-radius: 8px;
  padding: 18px;
  background: #fff;
  color: #222;
  font-size: 16px;
  line-height: 1.8;
  overflow-wrap: break-word;
}

.editor:empty:before {
  content: attr(data-placeholder);
  color: #aaa;
  pointer-events: none;
}

.editor p {
  margin: 0 0 12px;
}

.editor h2 {
  font-size: 25px;
  margin: 25px 0 12px;
}

.editor h3 {
  font-size: 21px;
  margin: 22px 0 10px;
}

.editor a {
  text-decoration: underline;
}

.editor-image-wrap {
  position: relative;
  display: block;
  width: 70%;
  margin: 20px auto;
  line-height: 0;
}

.editor-image-wrap.selected {
  outline: 2px solid #555;
}

.editor-image {
  display: block;
  width: 100%;
  height: auto;
  max-width: 100%;
  cursor: pointer;
  border-radius: 4px;
}

.image-resizer {
  position: absolute;
  width: 12px;
  height: 12px;
  right: -6px;
  bottom: -6px;
  background: #333;
  border: 2px solid #fff;
  border-radius: 50%;
  cursor: nwse-resize;
  display: none;
}

.editor-image-wrap.selected .image-resizer {
  display: block;
}

.editor-toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-bottom: 8px;
}

.editor-toolbar button,
.action-button,
.image-button {
  border: 1px solid #d5d5d5;
  background: #fff;
  color: #222;
  border-radius: 7px;
  padding: 8px 12px;
  cursor: pointer;
  font-size: 14px;
}

.editor-toolbar button:hover,
.action-button:hover,
.image-button:hover {
  background: #f4f4f4;
}

.primary-button {
  background: #222 !important;
  color: #fff !important;
  border-color: #222 !important;
}

.danger-button {
  color: #c62828 !important;
}

.image-upload-box {
  border: 1px dashed #bbb;
  border-radius: 8px;
  padding: 18px;
  background: #fafafa;
}

.image-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  gap: 14px;
  margin-top: 16px;
}

.image-item {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 8px;
  background: #fff;
}

.image-item-thumb {
  width: 100%;
  height: 130px;
  object-fit: cover;
  display: block;
  border-radius: 5px;
  background: #f2f2f2;
}

.image-item-name {
  font-size: 12px;
  color: #555;
  margin: 8px 2px;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.image-item-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 5px;
}

.image-item-buttons button {
  flex: 1;
  min-width: 70px;
  padding: 7px 5px;
  border: 1px solid #ddd;
  background: #fff;
  border-radius: 6px;
  cursor: pointer;
  font-size: 12px;
}

.image-item-buttons button:hover {
  background: #f5f5f5;
}

.featured-badge {
  display: inline-block;
  margin-top: 5px;
  font-size: 11px;
  font-weight: 700;
}

.featured-box {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 15px;
  background: #fafafa;
}

.featured-preview {
  margin-top: 12px;
}

.featured-preview img {
  display: block;
  max-width: 260px;
  max-height: 180px;
  object-fit: cover;
  border-radius: 6px;
}

.button-row {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 20px;
}

.preview-box {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 24px;
  margin-top: 20px;
  background: #fff;
}

.preview-box img {
  max-width: 100%;
  height: auto;
}

.preview-title {
  font-size: 30px;
  font-weight: 800;
  margin-bottom: 20px;
}

.small-help {
  font-size: 12px;
  color: #777;
  margin-top: 6px;
}

.status-message {
  margin-top: 10px;
  font-size: 13px;
  color: #555;
}

@media (max-width: 700px) {
  .write-grid {
    grid-template-columns: 1fr;
  }

  .editor {
    min-height: 450px;
  }

  .image-list {
    grid-template-columns: repeat(2, 1fr);
  }

  .editor-image-wrap {
    width: 100%;
  }
}
</style>

<div class="write-wrap">

  <!-- 제목 -->
  <div class="write-section">
    <label class="write-label">제목</label>
    <input
      id="postTitle"
      class="write-input"
      type="text"
      placeholder="글 제목을 입력하세요"
    >
  </div>

  <!-- URL / 카테고리 -->
  <div class="write-section write-grid">

    <div>
      <label class="write-label">URL</label>
      <input
        id="postSlug"
        class="write-input"
        type="text"
        placeholder="예: instagram-reels-download"
      >
      <div class="small-help">
        비워두면 제목을 기준으로 자동 생성합니다.
      </div>
    </div>

    <div>
      <label class="write-label">카테고리</label>
      <input
        id="postCategory"
        class="write-input"
        type="text"
        placeholder="예: 생활정보"
      >
    </div>

  </div>

  <!-- 태그 -->
  <div class="write-section">
    <label class="write-label">태그</label>
    <input
      id="postTags"
      class="write-input"
      type="text"
      placeholder="예: 인스타, 릴스, 다운로드"
    >
  </div>

  <!-- SEO -->
  <div class="write-section write-grid">

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
  <div class="write-section">

    <label class="write-label">대표 이미지</label>

    <div class="featured-box">

      <input
        id="featuredInput"
        type="file"
        accept="image/*"
      >

      <div class="small-help">
        글 대표 이미지로 사용할 사진을 선택하세요.
      </div>

      <div id="featuredPreview" class="featured-preview"></div>

    </div>

  </div>

  <!-- 본문 -->
  <div class="write-section">

    <label class="write-label">본문</label>

    <div class="editor-toolbar">

      <button type="button" data-command="bold">
        굵게
      </button>

      <button type="button" data-command="formatBlock" data-value="h2">
        소제목
      </button>

      <button type="button" data-command="formatBlock" data-value="h3">
        작은 소제목
      </button>

      <button type="button" id="linkButton">
        링크
      </button>

      <button type="button" id="removeFormatButton">
        서식 제거
      </button>

    </div>

    <!-- ★ 실제 글쓰기 공간 -->
    <div
      id="editor"
      class="editor"
      contenteditable="true"
      data-placeholder="여기에 글을 작성하세요."
    ></div>

  </div>

  <!-- 본문 이미지 -->
  <div class="write-section">

    <label class="write-label">본문 이미지</label>

    <div class="image-upload-box">

      <input
        id="bodyImageInput"
        type="file"
        accept="image/*"
        multiple
      >

      <div class="small-help">
        사진을 여러 장 선택할 수 있습니다.
        첨부 후 원하는 사진만 「본문에 넣기」를 누르세요.
      </div>

      <div id="imageList" class="image-list"></div>

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
      class="action-button danger-button"
      type="button"
    >
      전체 삭제
    </button>

  </div>

  <div id="statusMessage" class="status-message"></div>

  <!-- 미리보기 -->
  <div id="previewBox" class="preview-box" style="display:none;"></div>

</div>

<script>
(function () {

  const editor = document.getElementById("editor");
  const postTitle = document.getElementById("postTitle");
  const postSlug = document.getElementById("postSlug");
  const postCategory = document.getElementById("postCategory");
  const postTags = document.getElementById("postTags");
  const seoTitle = document.getElementById("seoTitle");
  const seoDescription = document.getElementById("seoDescription");

  const featuredInput = document.getElementById("featuredInput");
  const featuredPreview = document.getElementById("featuredPreview");

  const bodyImageInput = document.getElementById("bodyImageInput");
  const imageList = document.getElementById("imageList");

  const previewButton = document.getElementById("previewButton");
  const saveButton = document.getElementById("saveButton");
  const downloadButton = document.getElementById("downloadButton");
  const clearButton = document.getElementById("clearButton");

  const previewBox = document.getElementById("previewBox");
  const statusMessage = document.getElementById("statusMessage");

  const STORAGE_KEY = "donfree_write_draft_v3";

  let attachedImages = [];
  let featuredImage = null;
  let savedRange = null;

  /*
   * -------------------------
   * 기본 유틸
   * -------------------------
   */

  function setStatus(message) {
    statusMessage.textContent = message;

    setTimeout(function () {
      if (statusMessage.textContent === message) {
        statusMessage.textContent = "";
      }
    }, 2500);
  }

  function escapeHtml(value) {
    return String(value || "")
      .replace(/&/g, "&amp;")
      .replace(/</g, "&lt;")
      .replace(/>/g, "&gt;")
      .replace(/"/g, "&quot;")
      .replace(/'/g, "&#039;");
  }

  function slugify(text) {
    return String(text || "")
      .trim()
      .toLowerCase()
      .replace(/\s+/g, "-")
      .replace(/[^\w가-힣-]/g, "")
      .replace(/-+/g, "-");
  }

  function makeId() {
    return "img_" + Date.now() + "_" + Math.random().toString(36).slice(2, 9);
  }

  /*
   * -------------------------
   * 커서 저장
   * -------------------------
   */

  function saveEditorSelection() {

    const selection = window.getSelection();

    if (!selection || selection.rangeCount === 0) {
      return;
    }

    const range = selection.getRangeAt(0);

    if (!editor.contains(range.commonAncestorContainer)) {
      return;
    }

    savedRange = range.cloneRange();
  }

  function restoreEditorSelection() {

    editor.focus();

    if (savedRange) {

      const selection = window.getSelection();

      selection.removeAllRanges();
      selection.addRange(savedRange);

      return;
    }

    const range = document.createRange();

    range.selectNodeContents(editor);
    range.collapse(false);

    const selection = window.getSelection();

    selection.removeAllRanges();
    selection.addRange(range);
  }

  editor.addEventListener("keyup", saveEditorSelection);
  editor.addEventListener("mouseup", saveEditorSelection);
  editor.addEventListener("input", saveEditorSelection);

  /*
   * -------------------------
   * 대표 이미지
   * -------------------------
   */

  function renderFeaturedImage() {

    featuredPreview.innerHTML = "";

    if (!featuredImage) {
      return;
    }

    const image = document.createElement("img");

    image.src = featuredImage.src;
    image.alt = featuredImage.name || "대표 이미지";

    featuredPreview.appendChild(image);
  }

  function setFeaturedImage(image) {

    featuredImage = {
      id: image.id || makeId(),
      name: image.name,
      src: image.src
    };

    renderFeaturedImage();
    saveDraft();

    setStatus("대표 이미지로 지정했습니다.");
  }

  featuredInput.addEventListener("change", function () {

    const file = this.files && this.files[0];

    if (!file) {
      return;
    }

    const reader = new FileReader();

    reader.onload = function (event) {

      featuredImage = {
        id: makeId(),
        name: file.name,
        src: event.target.result
      };

      renderFeaturedImage();
      saveDraft();

      setStatus("대표 이미지가 등록되었습니다.");
    };

    reader.readAsDataURL(file);
  });

  /*
   * -------------------------
   * 본문 이미지 첨부
   * -------------------------
   */

  bodyImageInput.addEventListener("change", function () {

    const files = Array.from(this.files || []);

    if (!files.length) {
      return;
    }

    let completed = 0;

    files.forEach(function (file) {

      const reader = new FileReader();

      reader.onload = function (event) {

        attachedImages.push({
          id: makeId(),
          name: file.name,
          src: event.target.result
        });

        completed++;

        renderImageList();

        if (completed === files.length) {

          saveDraft();

          setStatus(files.length + "장의 사진을 첨부했습니다.");

          bodyImageInput.value = "";
        }
      };

      reader.readAsDataURL(file);
    });

  });

  /*
   * -------------------------
   * 첨부 이미지 목록
   * -------------------------
   */

  function renderImageList() {

    imageList.innerHTML = "";

    attachedImages.forEach(function (item) {

      const box = document.createElement("div");

      box.className = "image-item";

      const thumb = document.createElement("img");

      thumb.className = "image-item-thumb";
      thumb.src = item.src;
      thumb.alt = item.name || "첨부 이미지";

      const name = document.createElement("div");

      name.className = "image-item-name";
      name.textContent = item.name || "이미지";

      const buttons = document.createElement("div");

      buttons.className = "image-item-buttons";

      const insertButton = document.createElement("button");

      insertButton.type = "button";
      insertButton.textContent = "본문에 넣기";

      insertButton.addEventListener("click", function () {
        insertImage(item);
      });

      const featureButton = document.createElement("button");

      featureButton.type = "button";
      featureButton.textContent = "대표 이미지";

      featureButton.addEventListener("click", function () {
        setFeaturedImage(item);
      });

      const deleteButton = document.createElement("button");

      deleteButton.type = "button";
      deleteButton.textContent = "삭제";

      deleteButton.addEventListener("click", function () {

        attachedImages = attachedImages.filter(function (image) {
          return image.id !== item.id;
        });

        if (featuredImage && featuredImage.id === item.id) {
          featuredImage = null;
          renderFeaturedImage();
        }

        renderImageList();
        saveDraft();

        setStatus("사진을 삭제했습니다.");
      });

      buttons.appendChild(insertButton);
      buttons.appendChild(featureButton);
      buttons.appendChild(deleteButton);

      box.appendChild(thumb);
      box.appendChild(name);

      if (featuredImage && featuredImage.id === item.id) {

        const badge = document.createElement("div");

        badge.className = "featured-badge";
        badge.textContent = "★ 대표 이미지";

        box.appendChild(badge);
      }

      box.appendChild(buttons);

      imageList.appendChild(box);
    });
  }

  /*
   * -------------------------
   * 본문 이미지 삽입
   * -------------------------
   */

  function insertImage(item) {

    restoreEditorSelection();

    const wrapper = document.createElement("div");

    wrapper.className = "editor-image-wrap";

    const image = document.createElement("img");

    image.className = "editor-image";
    image.src = item.src;
    image.alt = item.name || "이미지";

    const resizer = document.createElement("span");

    resizer.className = "image-resizer";

    wrapper.appendChild(image);
    wrapper.appendChild(resizer);

    const range = window.getSelection().getRangeAt(0);

    range.deleteContents();
    range.insertNode(wrapper);

    const after = document.createElement("p");

    after.innerHTML = "<br>";

    wrapper.parentNode.insertBefore(after, wrapper.nextSibling);

    const newRange = document.createRange();

    newRange.setStart(after, 0);
    newRange.collapse(true);

    const selection = window.getSelection();

    selection.removeAllRanges();
    selection.addRange(newRange);

    savedRange = newRange.cloneRange();

    attachImageEvents(wrapper);

    saveDraft();

    setStatus("본문에 사진을 넣었습니다.");
  }

  /*
   * -------------------------
   * 본문 이미지 선택 / 크기 조절
   * -------------------------
   */

  function attachImageEvents(wrapper) {

    const image = wrapper.querySelector(".editor-image");
    const resizer = wrapper.querySelector(".image-resizer");

    if (!image || !resizer) {
      return;
    }

    image.addEventListener("click", function (event) {

      event.stopPropagation();

      document.querySelectorAll(".editor-image-wrap.selected")
        .forEach(function (item) {
          item.classList.remove("selected");
        });

      wrapper.classList.add("selected");

      saveEditorSelection();
    });

    resizer.addEventListener("mousedown", function (event) {

      event.preventDefault();
      event.stopPropagation();

      const startX = event.clientX;
      const startWidth = wrapper.getBoundingClientRect().width;
      const editorWidth = editor.getBoundingClientRect().width;

      function resize(moveEvent) {

        const difference = moveEvent.clientX - startX;

        let newWidth = startWidth + difference;

        const minWidth = 100;
        const maxWidth = editorWidth;

        if (newWidth < minWidth) {
          newWidth = minWidth;
        }

        if (newWidth > maxWidth) {
          newWidth = maxWidth;
        }

        const percentage = (newWidth / editorWidth) * 100;

        wrapper.style.width = percentage + "%";
      }

      function stopResize() {

        document.removeEventListener("mousemove", resize);
        document.removeEventListener("mouseup", stopResize);

        saveDraft();
      }

      document.addEventListener("mousemove", resize);
      document.addEventListener("mouseup", stopResize);

    });
  }

  function attachAllImageEvents() {

    editor.querySelectorAll(".editor-image-wrap")
      .forEach(function (wrapper) {
        attachImageEvents(wrapper);
      });

  }

  editor.addEventListener("click", function (event) {

    if (!event.target.classList.contains("editor-image")) {
      return;
    }

    saveEditorSelection();
  });

  /*
   * -------------------------
   * 툴바
   * -------------------------
   */

  document.querySelectorAll(".editor-toolbar button[data-command]")
    .forEach(function (button) {

      button.addEventListener("mousedown", function (event) {
        event.preventDefault();
      });

      button.addEventListener("click", function () {

        restoreEditorSelection();

        const command = button.dataset.command;
        const value = button.dataset.value || null;

        document.execCommand(command, false, value);

        saveEditorSelection();
        saveDraft();
      });

    });

  document.getElementById("linkButton")
    .addEventListener("mousedown", function (event) {
      event.preventDefault();
    });

  document.getElementById("linkButton")
    .addEventListener("click", function () {

      restoreEditorSelection();

      const url = prompt("링크 주소를 입력하세요.");

      if (!url) {
        return;
      }

      document.execCommand("createLink", false, url);

      saveEditorSelection();
      saveDraft();
    });

  document.getElementById("removeFormatButton")
    .addEventListener("click", function () {

      restoreEditorSelection();

      document.execCommand("removeFormat", false, null);

      saveEditorSelection();
      saveDraft();
    });

  /*
   * -------------------------
   * 데이터 수집
   * -------------------------
   */

  function collectData() {

    let slug = postSlug.value.trim();

    if (!slug) {
      slug = slugify(postTitle.value);
    }

    return {
      title: postTitle.value.trim(),
      slug: slug,
      category: postCategory.value.trim(),
      tags: postTags.value.trim(),
      seoTitle: seoTitle.value.trim(),
      seoDescription: seoDescription.value.trim(),
      featuredImage: featuredImage,
      attachedImages: attachedImages,
      content: editor.innerHTML
    };
  }

  /*
   * -------------------------
   * 자동 저장
   * -------------------------
   */

  function saveDraft() {

    try {

      const data = collectData();

      localStorage.setItem(
        STORAGE_KEY,
        JSON.stringify(data)
      );

    } catch (error) {

      console.warn("임시저장 실패:", error);

    }
  }

  let saveTimer = null;

  function scheduleSave() {

    clearTimeout(saveTimer);

    saveTimer = setTimeout(function () {
      saveDraft();
    }, 500);

  }

  [
    postTitle,
    postSlug,
    postCategory,
    postTags,
    seoTitle,
    seoDescription
  ].forEach(function (element) {

    element.addEventListener("input", scheduleSave);

  });

  editor.addEventListener("input", scheduleSave);

  /*
   * -------------------------
   * 초안 불러오기
   * -------------------------
   */

  function loadDraft() {

    try {

      const saved = localStorage.getItem(STORAGE_KEY);

      if (!saved) {
        return;
      }

      const data = JSON.parse(saved);

      postTitle.value = data.title || "";
      postSlug.value = data.slug || "";
      postCategory.value = data.category || "";
      postTags.value = data.tags || "";
      seoTitle.value = data.seoTitle || "";
      seoDescription.value = data.seoDescription || "";

      editor.innerHTML = data.content || "";

      featuredImage = data.featuredImage || null;
      attachedImages = Array.isArray(data.attachedImages)
        ? data.attachedImages
        : [];

      renderFeaturedImage();
      renderImageList();
      attachAllImageEvents();

    } catch (error) {

      console.warn("초안 불러오기 실패:", error);

    }

  }

  /*
   * -------------------------
   * 미리보기
   * -------------------------
   */

  previewButton.addEventListener("click", function () {

    const data = collectData();

    previewBox.style.display = "block";

    previewBox.innerHTML = "";

    const title = document.createElement("div");

    title.className = "preview-title";
    title.textContent = data.title || "제목 없음";

    const content = document.createElement("div");

    content.innerHTML = data.content || "<p>본문이 없습니다.</p>";

    previewBox.appendChild(title);
    previewBox.appendChild(content);

    previewBox.scrollIntoView({
      behavior: "smooth",
      block: "start"
    });

  });

  /*
   * -------------------------
   * 임시저장
   * -------------------------
   */

  saveButton.addEventListener("click", function () {

    saveDraft();

    setStatus("현재 글을 임시저장했습니다.");

  });

  /*
   * -------------------------
   * Markdown 변환
   * -------------------------
   */

  function htmlToMarkdown(html) {

    const temp = document.createElement("div");

    temp.innerHTML = html;

    function convert(node) {

      if (node.nodeType === Node.TEXT_NODE) {
        return node.textContent;
      }

      if (node.nodeType !== Node.ELEMENT_NODE) {
        return "";
      }

      const tag = node.tagName.toLowerCase();

      let inner = "";

      node.childNodes.forEach(function (child) {
        inner += convert(child);
      });

      if (tag === "br") {
        return "\n";
      }

      if (tag === "strong" || tag === "b") {
        return "**" + inner + "**";
      }

      if (tag === "h2") {
        return "\n\n## " + inner.trim() + "\n\n";
      }

      if (tag === "h3") {
        return "\n\n### " + inner.trim() + "\n\n";
      }

      if (tag === "a") {

        const href = node.getAttribute("href") || "";

        return "[" + inner.trim() + "](" + href + ")";

      }

      if (tag === "img") {

        const src = node.getAttribute("src") || "";

        return "\n\n<img src=\"" +
          src +
          "\" style=\"max-width:100%;height:auto;\">\n\n";
      }

      if (tag === "div" || tag === "p") {
        return inner + "\n\n";
      }

      return inner;

    }

    return convert(temp)
      .replace(/\n{3,}/g, "\n\n")
      .trim();

  }

  /*
   * -------------------------
   * Markdown 다운로드
   * -------------------------
   */

  downloadButton.addEventListener("click", function () {

    const data = collectData();

    if (!data.title) {

      alert("제목을 먼저 입력하세요.");
      postTitle.focus();

      return;
    }

    const date = new Date();

    const yyyy = date.getFullYear();
    const mm = String(date.getMonth() + 1).padStart(2, "0");
    const dd = String(date.getDate()).padStart(2, "0");

    const dateString = yyyy + "-" + mm + "-" + dd;

    const category = data.category || "생활정보";

    const tags = data.tags
      ? data.tags
          .split(",")
          .map(function (tag) {
            return tag.trim();
          })
          .filter(Boolean)
      : [];

    let markdown = "";

    markdown += "---\n";

    markdown += "title: \"" +
      data.title.replace(/"/g, '\\"') +
      "\"\n";

    markdown += "date: " +
      dateString +
      "\n";

    markdown += "categories: [" +
      category +
      "]\n";

    if (tags.length) {

      markdown += "tags: [" +
        tags.join(", ") +
        "]\n";

    }

    if (data.seoTitle) {

      markdown += "description: \"" +
        data.seoDescription.replace(/"/g, '\\"') +
        "\"\n";

    }

    if (data.featuredImage) {

      /*
       * 대표 이미지는 현재 작성 도구에서 확인할 수 있도록
       * 이미지 데이터를 포함합니다.
       */
      markdown += "image:\n";
      markdown += "  path: \"" +
        data.featuredImage.src +
        "\"\n";

    }

    markdown += "---\n\n";

    markdown += htmlToMarkdown(data.content);

    const blob = new Blob(
      [markdown],
      {
        type: "text/markdown;charset=utf-8"
      }
    );

    const url = URL.createObjectURL(blob);

    const link = document.createElement("a");

    link.href = url;

    link.download =
      dateString +
      "-" +
      (data.slug || slugify(data.title)) +
      ".md";

    document.body.appendChild(link);

    link.click();

    link.remove();

    URL.revokeObjectURL(url);

    setStatus("Markdown 파일을 만들었습니다.");

  });

  /*
   * -------------------------
   * 전체 삭제
   * -------------------------
   */

  clearButton.addEventListener("click", function () {

    const confirmed = confirm(
      "작성 중인 글과 첨부 사진을 모두 삭제할까요?"
    );

    if (!confirmed) {
      return;
    }

    postTitle.value = "";
    postSlug.value = "";
    postCategory.value = "";
    postTags.value = "";
    seoTitle.value = "";
    seoDescription.value = "";

    editor.innerHTML = "";

    featuredImage = null;
    attachedImages = [];

    featuredInput.value = "";
    bodyImageInput.value = "";

    renderFeaturedImage();
    renderImageList();

    previewBox.style.display = "none";
    previewBox.innerHTML = "";

    localStorage.removeItem(STORAGE_KEY);

    setStatus("작성 내용을 모두 삭제했습니다.");

  });

  /*
   * -------------------------
   * 이미지 선택 해제
   * -------------------------
   */

  editor.addEventListener("click", function (event) {

    if (
      !event.target.closest(".editor-image-wrap") &&
      event.target !== editor
    ) {

      document.querySelectorAll(".editor-image-wrap.selected")
        .forEach(function (item) {
          item.classList.remove("selected");
        });

    }

  });

  /*
   * -------------------------
   * 시작
   * -------------------------
   */

  loadDraft();

})();
</script>
