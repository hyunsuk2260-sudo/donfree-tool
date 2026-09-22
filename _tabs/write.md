---
layout: page
title: 글쓰기
permalink: /write/
---

<style>
.write-wrap {
  max-width: 900px;
  margin: 0 auto;
}

.write-wrap label {
  display: block;
  font-weight: 700;
  margin: 18px 0 7px;
}

.write-wrap input,
.write-wrap select,
.write-wrap textarea {
  width: 100%;
  box-sizing: border-box;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 11px 13px;
  font-size: 15px;
  background: #fff;
}

.write-wrap textarea {
  min-height: 500px;
  resize: vertical;
  line-height: 1.8;
}

.write-toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 7px;
  margin: 10px 0;
}

.write-toolbar button,
.write-actions button {
  border: 0;
  border-radius: 7px;
  padding: 9px 14px;
  cursor: pointer;
  font-weight: 700;
  background: #f1f3f5;
}

.write-toolbar button:hover,
.write-actions button:hover {
  opacity: .85;
}

.write-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 15px;
}

.btn-primary {
  background: #111 !important;
  color: #fff;
}

.btn-danger {
  background: #ffe8e8 !important;
  color: #c00;
}

.image-box {
  border: 1px solid #eee;
  border-radius: 10px;
  padding: 12px;
  margin-top: 10px;
}

.image-list {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-top: 12px;
}

.image-item {
  width: 150px;
  border: 1px solid #ddd;
  border-radius: 8px;
  overflow: hidden;
  background: #fff;
}

.image-item img {
  width: 100%;
  height: 100px;
  object-fit: cover;
  display: block;
}

.image-item .image-info {
  padding: 8px;
}

.image-item input {
  font-size: 12px;
  padding: 6px;
  margin-bottom: 5px;
}

.image-item button {
  width: 100%;
  border: 0;
  padding: 6px;
  cursor: pointer;
  background: #f1f1f1;
}

.preview-box {
  margin-top: 30px;
  border-top: 1px solid #ddd;
  padding-top: 25px;
}

.preview-content {
  border: 1px solid #eee;
  border-radius: 10px;
  padding: 25px;
  line-height: 1.8;
}

.preview-content img {
  max-width: 100%;
  height: auto;
  display: block;
  margin: 20px auto;
  border-radius: 8px;
}

.preview-content a {
  color: #0066cc;
  text-decoration: underline;
}

.status {
  margin-top: 10px;
  color: #666;
  font-size: 13px;
}

.help-box {
  background: #f7f7f7;
  border-radius: 8px;
  padding: 12px 15px;
  margin-top: 10px;
  font-size: 14px;
  line-height: 1.6;
}
</style>

<div class="write-wrap">

  <h1>글쓰기</h1>

  <div class="help-box">
    본문에서 링크를 넣고 싶은 글자를 드래그한 뒤
    <strong>🔗 링크</strong> 버튼을 눌러주세요.
  </div>

  <label for="postTitle">제목</label>
  <input
    type="text"
    id="postTitle"
    placeholder="글 제목을 입력하세요"
  >

  <label for="postSlug">URL 슬러그</label>
  <input
    type="text"
    id="postSlug"
    placeholder="예: instagram-reels-download"
  >

  <label for="postCategory">카테고리</label>
  <input
    type="text"
    id="postCategory"
    placeholder="예: 생활정보"
  >

  <label for="postTags">태그</label>
  <input
    type="text"
    id="postTags"
    placeholder="예: 인스타, 릴스, 다운로드"
  >

  <label for="seoTitle">SEO 제목</label>
  <input
    type="text"
    id="seoTitle"
    placeholder="검색 결과에 표시될 제목"
  >

  <label for="seoDescription">SEO 설명</label>
  <input
    type="text"
    id="seoDescription"
    placeholder="검색 결과에 표시될 설명"
  >

  <label>이미지</label>

  <div class="image-box">

    <input
      type="file"
      id="imageInput"
      accept="image/*"
      multiple
    >

    <div class="help-box">
      여러 장의 이미지를 한 번에 선택할 수 있습니다.
      원하는 위치에 커서를 놓고 이미지의
      <strong>본문에 넣기</strong> 버튼을 누르세요.
    </div>

    <div id="imageList" class="image-list"></div>

  </div>

  <label for="postBody">본문</label>

  <div class="write-toolbar">

    <button type="button" onclick="insertBold()">
      굵게
    </button>

    <button type="button" onclick="insertH2()">
      H2
    </button>

    <button type="button" onclick="insertLink()">
      🔗 링크
    </button>

    <button type="button" onclick="insertLine()">
      구분선
    </button>

  </div>

  <textarea
    id="postBody"
    placeholder="본문을 작성하세요."
  ></textarea>

  <div class="write-actions">

    <button
      type="button"
      class="btn-primary"
      onclick="previewPost()"
    >
      👀 미리보기
    </button>

    <button
      type="button"
      onclick="saveDraft()"
    >
      💾 임시저장
    </button>

    <button
      type="button"
      onclick="loadDraft()"
    >
      📂 불러오기
    </button>

    <button
      type="button"
      class="btn-danger"
      onclick="clearAll()"
    >
      🗑️ 초기화
    </button>

    <button
      type="button"
      class="btn-primary"
      onclick="downloadPost()"
    >
      📄 글 파일 만들기
    </button>

  </div>

  <div id="status" class="status"></div>

  <div class="preview-box">

    <h2>미리보기</h2>

    <div
      id="previewContent"
      class="preview-content"
    >
      작성한 글이 여기에 표시됩니다.
    </div>

  </div>

</div>


<script>

let images = [];


/* =========================
   이미지 선택
========================= */

document
  .getElementById("imageInput")
  .addEventListener("change", function(e) {

    const files = Array.from(e.target.files);

    files.forEach(file => {

      const reader = new FileReader();

      reader.onload = function(event) {

        images.push({
          id: Date.now() + Math.random(),
          name: file.name,
          src: event.target.result,
          alt: file.name.replace(/\.[^/.]+$/, "")
        });

        renderImages();

      };

      reader.readAsDataURL(file);

    });

    e.target.value = "";

});


/* =========================
   이미지 목록 표시
========================= */

function renderImages() {

  const list = document.getElementById("imageList");

  list.innerHTML = "";

  images.forEach(image => {

    const item = document.createElement("div");

    item.className = "image-item";

    item.innerHTML = `

      <img src="${image.src}" alt="">

      <div class="image-info">

        <input
          type="text"
          value="${escapeHtml(image.alt)}"
          placeholder="이미지 설명"
          onchange="updateAlt('${image.id}', this.value)"
        >

        <button
          type="button"
          onclick="insertImage('${image.id}')"
        >
          본문에 넣기
        </button>

        <button
          type="button"
          onclick="removeImage('${image.id}')"
        >
          삭제
        </button>

      </div>

    `;

    list.appendChild(item);

  });

}


/* =========================
   이미지 설명 수정
========================= */

function updateAlt(id, value) {

  const image = images.find(
    item => String(item.id) === String(id)
  );

  if (image) {
    image.alt = value;
  }

}


/* =========================
   이미지 본문 삽입
========================= */

function insertImage(id) {

  const image = images.find(
    item => String(item.id) === String(id)
  );

  if (!image) return;

  const marker =
    `[[IMAGE:${image.id}]]`;

  insertAtCursor(marker);

}


/* =========================
   이미지 삭제
========================= */

function removeImage(id) {

  images = images.filter(
    item => String(item.id) !== String(id)
  );

  renderImages();

}


/* =========================
   커서 위치에 텍스트 삽입
========================= */

function insertAtCursor(text) {

  const textarea =
    document.getElementById("postBody");

  const start =
    textarea.selectionStart;

  const end =
    textarea.selectionEnd;

  const current =
    textarea.value;

  textarea.value =
    current.substring(0, start)
    + text
    + current.substring(end);

  textarea.focus();

  const newPosition =
    start + text.length;

  textarea.selectionStart =
    newPosition;

  textarea.selectionEnd =
    newPosition;

}


/* =========================
   굵게
========================= */

function insertBold() {

  const textarea =
    document.getElementById("postBody");

  const start =
    textarea.selectionStart;

  const end =
    textarea.selectionEnd;

  const selected =
    textarea.value.substring(start, end);

  if (!selected) {

    alert(
      "굵게 표시할 글자를 먼저 드래그해주세요."
    );

    return;

  }

  const replacement =
    `**${selected}**`;

  textarea.value =
    textarea.value.substring(0, start)
    + replacement
    + textarea.value.substring(end);

  textarea.focus();

}


/* =========================
   H2
========================= */

function insertH2() {

  const textarea =
    document.getElementById("postBody");

  const start =
    textarea.selectionStart;

  const end =
    textarea.selectionEnd;

  const selected =
    textarea.value.substring(start, end);

  if (!selected) {

    alert(
      "제목으로 만들 글자를 먼저 드래그해주세요."
    );

    return;

  }

  const replacement =
    `## ${selected}`;

  textarea.value =
    textarea.value.substring(0, start)
    + replacement
    + textarea.value.substring(end);

  textarea.focus();

}


/* =========================
   🔗 링크 삽입
========================= */

function insertLink() {

  const textarea =
    document.getElementById("postBody");

  const start =
    textarea.selectionStart;

  const end =
    textarea.selectionEnd;

  const selected =
    textarea.value.substring(start, end);

  if (!selected) {

    alert(
      "먼저 링크로 만들 글자를 드래그해주세요."
    );

    return;

  }

  const url =
    prompt(
      "연결할 URL을 입력하세요.\n\n예:\nhttps://tool.donfree.co.kr/video/"
    );

  if (!url) return;

  const markdown =
    `[${selected}](${url})`;

  textarea.value =
    textarea.value.substring(0, start)
    + markdown
    + textarea.value.substring(end);

  textarea.focus();

  const newPosition =
    start + markdown.length;

  textarea.selectionStart =
    newPosition;

  textarea.selectionEnd =
    newPosition;

}


/* =========================
   구분선
========================= */

function insertLine() {

  insertAtCursor(
    "\n\n---\n\n"
  );

}


/* =========================
   미리보기
========================= */

function previewPost() {

  let body =
    document.getElementById("postBody").value;

  /* 이미지 처리 */

  images.forEach(image => {

    const marker =
      `[[IMAGE:${image.id}]]`;

    const imageHtml =
      `<img src="${image.src}" alt="${escapeHtml(image.alt)}">`;

    body =
      body.split(marker)
           .join(imageHtml);

  });


  /* HTML escape */

  body =
    escapeHtml(body);


  /* 이미지 태그는 다시 살림 */

  images.forEach(image => {

    const marker =
      `[[IMAGE:${image.id}]]`;

    const imageHtml =
      `<img src="${image.src}" alt="${escapeHtml(image.alt)}">`;

    body =
      body.split(
        escapeHtml(imageHtml)
      ).join(imageHtml);

  });


  /* Markdown 기본 변환 */

  body =
    body.replace(
      /^## (.*)$/gm,
      "<h2>$1</h2>"
    );

  body =
    body.replace(
      /\*\*(.*?)\*\*/g,
      "<strong>$1</strong>"
    );

  body =
    body.replace(
      /\[(.*?)\]\((https?:\/\/[^\s)]+)\)/g,
      '<a href="$2" target="_blank" rel="noopener">$1</a>'
    );

  body =
    body.replace(
      /\n/g,
      "<br>"
    );


  document
    .getElementById("previewContent")
    .innerHTML = body;

}


/* =========================
   임시저장
========================= */

function saveDraft() {

  const data = {

    title:
      document.getElementById("postTitle").value,

    slug:
      document.getElementById("postSlug").value,

    category:
      document.getElementById("postCategory").value,

    tags:
      document.getElementById("postTags").value,

    seoTitle:
      document.getElementById("seoTitle").value,

    seoDescription:
      document.getElementById("seoDescription").value,

    body:
      document.getElementById("postBody").value,

    images: images

  };


  try {

    localStorage.setItem(
      "donfreePostDraft",
      JSON.stringify(data)
    );

    showStatus(
      "임시저장했습니다."
    );

  } catch (error) {

    showStatus(
      "이미지가 너무 많거나 커서 저장하지 못했습니다."
    );

  }

}


/* =========================
   임시저장 불러오기
========================= */

function loadDraft() {

  const saved =
    localStorage.getItem(
      "donfreePostDraft"
    );

  if (!saved) {

    alert(
      "저장된 글이 없습니다."
    );

    return;

  }

  try {

    const data =
      JSON.parse(saved);

    document.getElementById("postTitle").value =
      data.title || "";

    document.getElementById("postSlug").value =
      data.slug || "";

    document.getElementById("postCategory").value =
      data.category || "";

    document.getElementById("postTags").value =
      data.tags || "";

    document.getElementById("seoTitle").value =
      data.seoTitle || "";

    document.getElementById("seoDescription").value =
      data.seoDescription || "";

    document.getElementById("postBody").value =
      data.body || "";

    images =
      data.images || [];

    renderImages();

    previewPost();

    showStatus(
      "임시저장한 글을 불러왔습니다."
    );

  } catch (error) {

    alert(
      "저장된 글을 불러오지 못했습니다."
    );

  }

}


/* =========================
   Markdown 파일 생성
========================= */

function downloadPost() {

  const title =
    document.getElementById("postTitle").value.trim();

  const slug =
    document.getElementById("postSlug").value.trim();

  const category =
    document.getElementById("postCategory").value.trim();

  const tags =
    document.getElementById("postTags").value.trim();

  const seoTitle =
    document.getElementById("seoTitle").value.trim();

  const seoDescription =
    document.getElementById("seoDescription").value.trim();

  let body =
    document.getElementById("postBody").value;


  if (!title) {

    alert("제목을 입력해주세요.");

    return;

  }


  if (!slug) {

    alert("URL 슬러그를 입력해주세요.");

    return;

  }


  /* 이미지 마커를 실제 이미지 HTML로 변경 */

  images.forEach(image => {

    const marker =
      `[[IMAGE:${image.id}]]`;

    const imageHtml =
      `<img src="${image.src}" alt="${image.alt}">`;

    body =
      body.split(marker)
           .join(imageHtml);

  });


  const today =
    new Date()
      .toISOString()
      .slice(0, 10);


  const tagArray =
    tags
      .split(",")
      .map(tag => tag.trim())
      .filter(Boolean);


  const tagText =
    tagArray.length
      ? "[" +
        tagArray
          .map(tag => `"${tag}"`)
          .join(", ") +
        "]"
      : "[]";


  const frontMatter = `---
title: "${escapeYaml(title)}"
date: ${today}
categories: ["${escapeYaml(category || "생활정보")}"]
tags: ${tagText}
description: "${escapeYaml(seoDescription)}"
---

`;


  const finalText =
    frontMatter + body;


  const blob =
    new Blob(
      [finalText],
      {
        type: "text/markdown;charset=utf-8"
      }
    );


  const url =
    URL.createObjectURL(blob);


  const a =
    document.createElement("a");

  a.href = url;

  a.download =
    `${today}-${slug}.md`;

  document.body.appendChild(a);

  a.click();

  a.remove();

  URL.revokeObjectURL(url);


  showStatus(
    "Markdown 파일을 만들었습니다."
  );

}


/* =========================
   초기화
========================= */

function clearAll() {

  if (
    !confirm(
      "작성 중인 내용을 모두 삭제할까요?"
    )
  ) {
    return;
  }


  document.getElementById("postTitle").value = "";

  document.getElementById("postSlug").value = "";

  document.getElementById("postCategory").value = "";

  document.getElementById("postTags").value = "";

  document.getElementById("seoTitle").value = "";

  document.getElementById("seoDescription").value = "";

  document.getElementById("postBody").value = "";

  images = [];

  renderImages();

  document.getElementById("previewContent").innerHTML =
    "작성한 글이 여기에 표시됩니다.";

  showStatus("");

}


/* =========================
   상태 메시지
========================= */

function showStatus(message) {

  document.getElementById("status").textContent =
    message;

}


/* =========================
   HTML escape
========================= */

function escapeHtml(value) {

  return String(value)
    .replace(/&/g, "&amp;")
    .replace(/</g, "&lt;")
    .replace(/>/g, "&gt;")
    .replace(/"/g, "&quot;")
    .replace(/'/g, "&#039;");

}


/* =========================
   YAML escape
========================= */

function escapeYaml(value) {

  return String(value)
    .replace(/\\/g, "\\\\")
    .replace(/"/g, '\\"')
    .replace(/\n/g, " ");

}

</script>
