---
title: 글쓰기
icon: fas fa-pen
order: 99
layout: page
permalink: /write/
---

<style>
.donfree-editor {
  max-width: 1000px;
  margin: 0 auto;
}

.donfree-editor h2 {
  margin-top: 10px;
  margin-bottom: 8px;
}

.editor-desc {
  color: #777;
  font-size: 14px;
  margin-bottom: 25px;
}

.editor-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 18px;
}

.editor-field {
  margin-bottom: 18px;
}

.editor-field.full {
  grid-column: 1 / -1;
}

.editor-field label {
  display: block;
  font-size: 13px;
  font-weight: 700;
  margin-bottom: 7px;
}

.editor-field input,
.editor-field select,
.editor-field textarea {
  width: 100%;
  box-sizing: border-box;
  border: 1px solid #ddd;
  border-radius: 7px;
  padding: 11px 12px;
  font-size: 14px;
  background: #fff;
}

.editor-field input:focus,
.editor-field select:focus,
.editor-field textarea:focus {
  outline: none;
  border-color: #333;
}

#post-body {
  min-height: 500px;
  resize: vertical;
  line-height: 1.7;
}

.editor-help {
  font-size: 12px;
  color: #888;
  margin-top: 6px;
}

.image-box {
  border: 1px dashed #ccc;
  border-radius: 8px;
  padding: 18px;
  background: #fafafa;
}

.image-box input {
  border: 0;
  padding: 0;
}

.image-preview {
  margin-top: 15px;
}

.image-preview img {
  max-width: 100%;
  max-height: 300px;
  border-radius: 8px;
  display: block;
  margin-bottom: 8px;
}

.image-name {
  font-size: 12px;
  color: #777;
}

.editor-buttons {
  display: flex;
  gap: 7px;
  flex-wrap: wrap;
  margin-top: 15px;
}

.editor-buttons button {
  border: 0;
  border-radius: 6px;
  padding: 10px 15px;
  cursor: pointer;
  font-weight: 700;
}

.btn-preview {
  background: #111827;
  color: white;
}

.btn-save {
  background: #2563eb;
  color: white;
}

.btn-file {
  background: #16a34a;
  color: white;
}

.btn-clear {
  background: #e5e7eb;
  color: #333;
}

.preview-box {
  display: none;
  margin-top: 30px;
  padding: 25px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background: white;
}

.preview-box h3 {
  margin-top: 0;
}

.preview-content {
  line-height: 1.8;
}

.preview-content img {
  max-width: 100%;
  height: auto;
  border-radius: 8px;
  margin: 15px 0;
}

.status-message {
  margin-top: 10px;
  font-size: 13px;
  color: #777;
}

@media (max-width: 700px) {
  .editor-grid {
    grid-template-columns: 1fr;
  }

  .editor-field.full {
    grid-column: auto;
  }

  #post-body {
    min-height: 400px;
  }
}
</style>

<div class="donfree-editor">

<h2>✍️ 돈프리 글쓰기</h2>

<p class="editor-desc">
검색 유입용 콘텐츠를 작성하고 미리보기할 수 있습니다.
</p>

<div class="editor-grid">

  <div class="editor-field">
    <label>글 제목</label>
    <input
      type="text"
      id="post-title"
      placeholder="예: 인스타 릴스 다운로드 방법, 앱 없이 저장하는 법"
    >
  </div>

  <div class="editor-field">
    <label>URL 슬러그</label>
    <input
      type="text"
      id="post-slug"
      placeholder="instagram-reels-download"
    >
  </div>

  <div class="editor-field">
    <label>카테고리</label>
    <select id="post-category">
      <option value="생활정보">생활정보</option>
      <option value="SNS">SNS</option>
      <option value="돈버는정보">돈버는정보</option>
      <option value="IT">IT</option>
      <option value="육아">육아</option>
      <option value="여행">여행</option>
      <option value="리빙">리빙</option>
    </select>
  </div>

  <div class="editor-field">
    <label>태그</label>
    <input
      type="text"
      id="post-tags"
      placeholder="인스타, 릴스, 다운로드"
    >
  </div>

  <div class="editor-field">
    <label>SEO 제목</label>
    <input
      type="text"
      id="seo-title"
      placeholder="검색 결과에 표시될 제목"
    >
  </div>

  <div class="editor-field">
    <label>SEO 설명</label>
    <input
      type="text"
      id="seo-description"
      placeholder="검색 결과에 표시될 설명"
    >
  </div>

  <div class="editor-field full">

    <label>대표 이미지</label>

    <div class="image-box">

      <input
        type="file"
        id="featured-image"
        accept="image/*"
      >

      <div class="editor-help">
        JPG, PNG, WEBP 이미지를 선택하세요.
      </div>

      <div
        id="image-preview"
        class="image-preview"
      ></div>

    </div>

  </div>

  <div class="editor-field full">

    <label>본문</label>

    <textarea
      id="post-body"
      placeholder="여기에 글을 작성하세요.

예:
인스타 릴스를 보다 보면 나중에 다시 보고 싶은 영상이 하나씩 생깁니다.

오늘은 앱을 설치하지 않고 릴스를 저장하는 방법을 정리해볼게요."
    ></textarea>

    <div class="editor-help">
      이미지가 들어갈 위치에 [대표이미지]라고 입력하면 미리보기에서 이미지가 표시됩니다.
    </div>

  </div>

</div>

<div class="editor-buttons">

  <button
    type="button"
    class="btn-preview"
    onclick="showPreview()"
  >
    👁️ 미리보기
  </button>

  <button
    type="button"
    class="btn-save"
    onclick="saveDraft()"
  >
    💾 임시저장
  </button>

  <button
    type="button"
    class="btn-file"
    onclick="downloadPost()"
  >
    📄 글 파일 만들기
  </button>

  <button
    type="button"
    class="btn-clear"
    onclick="clearPost()"
  >
    🗑 초기화
  </button>

</div>

<div
  id="status-message"
  class="status-message"
></div>

<div
  id="preview-box"
  class="preview-box"
>

  <h3 id="preview-title"></h3>

  <div
    id="preview-content"
    class="preview-content"
  ></div>

</div>

</div>

<script>

let selectedImageData = "";
let selectedImageName = "";


/* --------------------------------
   이미지 선택
-------------------------------- */

document
  .getElementById("featured-image")
  .addEventListener("change", function(event) {

    const file = event.target.files[0];

    if (!file) return;

    selectedImageName = file.name;

    const reader = new FileReader();

    reader.onload = function(e) {

      selectedImageData = e.target.result;

      document.getElementById("image-preview").innerHTML = `
        <img src="${selectedImageData}" alt="대표 이미지">
        <div class="image-name">
          ${escapeHtml(file.name)}
        </div>
      `;

    };

    reader.readAsDataURL(file);

  });


/* --------------------------------
   HTML 이스케이프
-------------------------------- */

function escapeHtml(text) {

  return text
    .replace(/&/g, "&amp;")
    .replace(/</g, "&lt;")
    .replace(/>/g, "&gt;")
    .replace(/"/g, "&quot;")
    .replace(/'/g, "&#039;");

}


/* --------------------------------
   간단한 마크다운 변환
-------------------------------- */

function markdownToHtml(text) {

  let html = escapeHtml(text);

  html = html.replace(
    /\[대표이미지\]/g,
    selectedImageData
      ? `<img src="${selectedImageData}" alt="${escapeHtml(selectedImageName)}">`
      : ""
  );

  html = html.replace(
    /^### (.*)$/gm,
    "<h4>$1</h4>"
  );

  html = html.replace(
    /^## (.*)$/gm,
    "<h3>$1</h3>"
  );

  html = html.replace(
    /^# (.*)$/gm,
    "<h2>$1</h2>"
  );

  html = html.replace(
    /\*\*(.*?)\*\*/g,
    "<strong>$1</strong>"
  );

  html = html.replace(
    /\n\n/g,
    "</p><p>"
  );

  html = "<p>" + html + "</p>";

  html = html.replace(
    /\n/g,
    "<br>"
  );

  return html;

}


/* --------------------------------
   미리보기
-------------------------------- */

function showPreview() {

  const title =
    document.getElementById("post-title").value.trim();

  const body =
    document.getElementById("post-body").value;

  if (!title) {

    alert("글 제목을 입력해주세요.");

    return;

  }

  document.getElementById("preview-title").textContent =
    title;

  document.getElementById("preview-content").innerHTML =
    markdownToHtml(body);

  document.getElementById("preview-box").style.display =
    "block";

  document
    .getElementById("preview-box")
    .scrollIntoView({
      behavior: "smooth"
    });

}


/* --------------------------------
   임시저장
-------------------------------- */

function saveDraft() {

  const data = {

    title:
      document.getElementById("post-title").value,

    slug:
      document.getElementById("post-slug").value,

    category:
      document.getElementById("post-category").value,

    tags:
      document.getElementById("post-tags").value,

    seoTitle:
      document.getElementById("seo-title").value,

    seoDescription:
      document.getElementById("seo-description").value,

    body:
      document.getElementById("post-body").value,

    imageData:
      selectedImageData,

    imageName:
      selectedImageName

  };

  localStorage.setItem(
    "donfree-post-draft",
    JSON.stringify(data)
  );

  document.getElementById("status-message").textContent =
    "✓ 임시저장되었습니다.";

}


/* --------------------------------
   임시저장 불러오기
-------------------------------- */

function loadDraft() {

  const saved =
    localStorage.getItem("donfree-post-draft");

  if (!saved) return;

  try {

    const data = JSON.parse(saved);

    document.getElementById("post-title").value =
      data.title || "";

    document.getElementById("post-slug").value =
      data.slug || "";

    document.getElementById("post-category").value =
      data.category || "생활정보";

    document.getElementById("post-tags").value =
      data.tags || "";

    document.getElementById("seo-title").value =
      data.seoTitle || "";

    document.getElementById("seo-description").value =
      data.seoDescription || "";

    document.getElementById("post-body").value =
      data.body || "";

    selectedImageData =
      data.imageData || "";

    selectedImageName =
      data.imageName || "";

    if (selectedImageData) {

      document.getElementById("image-preview").innerHTML = `
        <img src="${selectedImageData}" alt="대표 이미지">
        <div class="image-name">
          ${escapeHtml(selectedImageName)}
        </div>
      `;

    }

  } catch (error) {

    console.log(error);

  }

}


/* --------------------------------
   날짜
-------------------------------- */

function getToday() {

  const now = new Date();

  const year =
    now.getFullYear();

  const month =
    String(now.getMonth() + 1)
      .padStart(2, "0");

  const day =
    String(now.getDate())
      .padStart(2, "0");

  return `${year}-${month}-${day}`;

}


/* --------------------------------
   YAML 안전 처리
-------------------------------- */

function yamlText(text) {

  return String(text || "")
    .replace(/"/g, '\\"');

}


/* --------------------------------
   태그 만들기
-------------------------------- */

function makeTags(tags) {

  if (!tags.trim()) return "[]";

  return "[" +
    tags
      .split(",")
      .map(tag => `"${yamlText(tag.trim())}"`)
      .filter(Boolean)
      .join(", ") +
    "]";

}


/* --------------------------------
   글 파일 만들기
-------------------------------- */

function downloadPost() {

  const title =
    document.getElementById("post-title").value.trim();

  const slug =
    document.getElementById("post-slug").value.trim();

  const category =
    document.getElementById("post-category").value;

  const tags =
    document.getElementById("post-tags").value;

  const seoTitle =
    document.getElementById("seo-title").value.trim();

  const seoDescription =
    document
      .getElementById("seo-description")
      .value
      .trim();

  const body =
    document.getElementById("post-body").value;

  if (!title) {

    alert("글 제목을 입력해주세요.");

    return;

  }

  if (!slug) {

    alert("URL 슬러그를 입력해주세요.");

    return;

  }

  if (!body.trim()) {

    alert("본문을 입력해주세요.");

    return;

  }


  let finalBody = body;


  /*
    대표 이미지가 있다면
    본문에서 [대표이미지] 위치에
    HTML 이미지 태그를 넣습니다.
  */

  if (selectedImageData) {

    const imageHtml =
      `<img src="${selectedImageData}" alt="${escapeHtml(selectedImageName)}">`;

    finalBody =
      finalBody.replace(
        /\[대표이미지\]/g,
        imageHtml
      );

  }


  const date =
    getToday();


  const frontMatter = `---
title: "${yamlText(title)}"
date: ${date}
categories: ["${yamlText(category)}"]
tags: ${makeTags(tags)}
description: "${yamlText(seoDescription)}"
seo_title: "${yamlText(seoTitle)}"
permalink: /posts/${slug}/
---

`;


  const content =
    frontMatter + finalBody;


  const blob =
    new Blob(
      [content],
      {
        type: "text/markdown;charset=utf-8"
      }
    );


  const url =
    URL.createObjectURL(blob);


  const link =
    document.createElement("a");

  link.href = url;

  link.download =
    `${date}-${slug}.md`;

  document.body.appendChild(link);

  link.click();

  document.body.removeChild(link);

  URL.revokeObjectURL(url);


  document.getElementById("status-message").textContent =
    "✓ 글 파일이 만들어졌습니다. _posts 폴더에 넣으면 됩니다.";

}


/* --------------------------------
   초기화
-------------------------------- */

function clearPost() {

  if (
    !confirm(
      "작성 중인 내용을 모두 삭제할까요?"
    )
  ) {

    return;

  }

  document.getElementById("post-title").value = "";

  document.getElementById("post-slug").value = "";

  document.getElementById("post-category").value =
    "생활정보";

  document.getElementById("post-tags").value = "";

  document.getElementById("seo-title").value = "";

  document.getElementById("seo-description").value = "";

  document.getElementById("post-body").value = "";

  document.getElementById("featured-image").value = "";

  document.getElementById("image-preview").innerHTML = "";

  document.getElementById("preview-box").style.display =
    "none";

  selectedImageData = "";

  selectedImageName = "";

  localStorage.removeItem(
    "donfree-post-draft"
  );

  document.getElementById("status-message").textContent =
    "";

}


/* --------------------------------
   페이지 열 때 임시저장 불러오기
-------------------------------- */

loadDraft();

</script>
