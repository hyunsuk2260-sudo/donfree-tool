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
  font-family: inherit;
}

/* 이미지 업로드 영역 */

.image-upload-box {
  border: 1px dashed #bbb;
  border-radius: 8px;
  padding: 18px;
  background: #fafafa;
}

.image-upload-box input[type="file"] {
  border: 0;
  padding: 0;
  background: transparent;
}

/* 이미지 목록 */

.image-list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
  margin-top: 18px;
}

.image-item {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 10px;
  background: white;
}

.image-item img {
  width: 100%;
  height: 140px;
  object-fit: cover;
  border-radius: 6px;
  display: block;
  margin-bottom: 8px;
}

.image-item-name {
  font-size: 11px;
  color: #777;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  margin-bottom: 8px;
}

.image-item button {
  width: 100%;
  border: 0;
  border-radius: 5px;
  padding: 7px;
  cursor: pointer;
  font-size: 12px;
  font-weight: 700;
  background: #111827;
  color: white;
}

.image-item button.remove-image {
  margin-top: 5px;
  background: #eee;
  color: #333;
}

/* 버튼 */

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

/* 미리보기 */

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
  display: block;
  margin: 20px 0;
  border-radius: 8px;
}

.status-message {
  margin-top: 10px;
  font-size: 13px;
  color: #777;
}

.editor-help {
  font-size: 12px;
  color: #888;
  margin-top: 7px;
}

@media (max-width: 700px) {

  .editor-grid {
    grid-template-columns: 1fr;
  }

  .editor-field.full {
    grid-column: auto;
  }

  .image-list {
    grid-template-columns: repeat(2, 1fr);
  }

  #post-body {
    min-height: 400px;
  }
}
</style>


<div class="donfree-editor">

<h2>✍️ 돈프리 글쓰기</h2>

<p class="editor-desc">
검색 유입용 콘텐츠를 작성하고 이미지를 넣어 미리볼 수 있습니다.
</p>


<div class="editor-grid">

  <!-- 제목 -->

  <div class="editor-field">

    <label>글 제목</label>

    <input
      type="text"
      id="post-title"
      placeholder="예: 인스타 릴스 다운로드 방법, 앱 없이 저장하는 법"
    >

  </div>


  <!-- URL -->

  <div class="editor-field">

    <label>URL 슬러그</label>

    <input
      type="text"
      id="post-slug"
      placeholder="instagram-reels-download"
    >

  </div>


  <!-- 카테고리 -->

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


  <!-- 태그 -->

  <div class="editor-field">

    <label>태그</label>

    <input
      type="text"
      id="post-tags"
      placeholder="인스타, 릴스, 다운로드"
    >

  </div>


  <!-- SEO -->

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


  <!-- 이미지 -->

  <div class="editor-field full">

    <label>본문 이미지</label>

    <div class="image-upload-box">

      <input
        type="file"
        id="post-images"
        accept="image/*"
        multiple
      >

      <div class="editor-help">
        여러 장을 한꺼번에 선택할 수 있습니다.
      </div>

      <div
        id="image-list"
        class="image-list"
      ></div>

    </div>

  </div>


  <!-- 본문 -->

  <div class="editor-field full">

    <label>본문</label>

    <textarea
      id="post-body"
      placeholder="여기에 글을 작성하세요."
    ></textarea>

    <div class="editor-help">
      이미지를 넣고 싶은 위치에 커서를 놓은 뒤,
      위 이미지의 「본문에 넣기」를 누르세요.
    </div>

  </div>

</div>


<!-- 버튼 -->

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


<!-- 미리보기 -->

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

/* ==========================================
   이미지 저장 배열
========================================== */

let uploadedImages = [];


/* ==========================================
   이미지 선택
========================================== */

document
  .getElementById("post-images")
  .addEventListener("change", function(event) {

    const files = Array.from(event.target.files);

    if (!files.length) return;


    files.forEach(function(file) {

      if (!file.type.startsWith("image/")) {
        return;
      }


      const reader = new FileReader();


      reader.onload = function(e) {

        const image = {

          id:
            Date.now() +
            Math.random(),

          name:
            file.name,

          data:
            e.target.result

        };


        uploadedImages.push(image);

        renderImages();

      };


      reader.readAsDataURL(file);

    });


    /*
      같은 파일을 다시 선택할 수 있도록
      input 값을 초기화
    */

    event.target.value = "";

  });


/* ==========================================
   이미지 목록 출력
========================================== */

function renderImages() {

  const container =
    document.getElementById("image-list");


  container.innerHTML = "";


  uploadedImages.forEach(function(image, index) {

    const item =
      document.createElement("div");

    item.className =
      "image-item";


    item.innerHTML = `

      <img
        src="${image.data}"
        alt="${escapeHtml(image.name)}"
      >

      <div class="image-item-name">
        ${escapeHtml(image.name)}
      </div>

      <button
        type="button"
        onclick="insertImage(${index})"
      >
        본문에 넣기
      </button>

      <button
        type="button"
        class="remove-image"
        onclick="removeImage(${index})"
      >
        삭제
      </button>

    `;


    container.appendChild(item);

  });

}


/* ==========================================
   이미지 본문 삽입
========================================== */

function insertImage(index) {

  const textarea =
    document.getElementById("post-body");

  const image =
    uploadedImages[index];


  if (!image) return;


  /*
    이미지 ID를 본문에 삽입
  */

  const marker =
    `[[IMAGE:${image.id}]]`;


  const start =
    textarea.selectionStart;

  const end =
    textarea.selectionEnd;


  const before =
    textarea.value.substring(0, start);

  const after =
    textarea.value.substring(end);


  textarea.value =
    before +
    "\n\n" +
    marker +
    "\n\n" +
    after;


  /*
    커서를 이미지 뒤로 이동
  */

  const newPosition =
    start +
    marker.length +
    4;


  textarea.focus();

  textarea.setSelectionRange(
    newPosition,
    newPosition
  );

}


/* ==========================================
   이미지 삭제
========================================== */

function removeImage(index) {

  if (
    !confirm("이 이미지를 삭제할까요?")
  ) {
    return;
  }


  const image =
    uploadedImages[index];


  /*
    본문에 들어간 이미지 표시도 제거
  */

  const textarea =
    document.getElementById("post-body");


  textarea.value =
    textarea.value.replace(
      new RegExp(
        "\\[\\[IMAGE:" +
        escapeRegExp(String(image.id)) +
        "\\]\\]",
        "g"
      ),
      ""
    );


  uploadedImages.splice(
    index,
    1
  );


  renderImages();

}


/* ==========================================
   정규식 특수문자 처리
========================================== */

function escapeRegExp(text) {

  return text.replace(
    /[.*+?^${}()|[\]\\]/g,
    "\\$&"
  );

}


/* ==========================================
   HTML 이스케이프
========================================== */

function escapeHtml(text) {

  return String(text)

    .replace(
      /&/g,
      "&amp;"
    )

    .replace(
      /</g,
      "&lt;"
    )

    .replace(
      />/g,
      "&gt;"
    )

    .replace(
      /"/g,
      "&quot;"
    )

    .replace(
      /'/g,
      "&#039;"
    );

}


/* ==========================================
   본문 → HTML
========================================== */

function markdownToHtml(text) {

  let html =
    escapeHtml(text);


  /*
    이미지 표시
  */

  uploadedImages.forEach(function(image) {

    const marker =
      escapeRegExp(
        `[[IMAGE:${image.id}]]`
      );


    const imageHtml = `
      <img
        src="${image.data}"
        alt="${escapeHtml(image.name)}"
      >
    `;


    html =
      html.replace(
        new RegExp(marker, "g"),
        imageHtml
      );

  });


  /*
    제목
  */

  html =
    html.replace(
      /^### (.*)$/gm,
      "<h4>$1</h4>"
    );


  html =
    html.replace(
      /^## (.*)$/gm,
      "<h3>$1</h3>"
    );


  html =
    html.replace(
      /^# (.*)$/gm,
      "<h2>$1</h2>"
    );


  /*
    굵게
  */

  html =
    html.replace(
      /\*\*(.*?)\*\*/g,
      "<strong>$1</strong>"
    );


  /*
    줄바꿈
  */

  html =
    html.replace(
      /\n\n/g,
      "</p><p>"
    );


  html =
    "<p>" +
    html +
    "</p>";


  html =
    html.replace(
      /\n/g,
      "<br>"
    );


  return html;

}


/* ==========================================
   미리보기
========================================== */

function showPreview() {

  const title =
    document
      .getElementById("post-title")
      .value
      .trim();


  const body =
    document
      .getElementById("post-body")
      .value;


  if (!title) {

    alert(
      "글 제목을 입력해주세요."
    );

    return;

  }


  document
    .getElementById("preview-title")
    .textContent =
    title;


  document
    .getElementById("preview-content")
    .innerHTML =
    markdownToHtml(body);


  document
    .getElementById("preview-box")
    .style.display =
    "block";


  document
    .getElementById("preview-box")
    .scrollIntoView({
      behavior: "smooth"
    });

}


/* ==========================================
   임시저장
========================================== */

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
      document
        .getElementById("seo-description")
        .value,

    body:
      document.getElementById("post-body").value,

    images:
      uploadedImages

  };


  localStorage.setItem(
    "donfree-post-draft",
    JSON.stringify(data)
  );


  document
    .getElementById("status-message")
    .textContent =
    "✓ 임시저장되었습니다.";

}


/* ==========================================
   임시저장 불러오기
========================================== */

function loadDraft() {

  const saved =
    localStorage.getItem(
      "donfree-post-draft"
    );


  if (!saved) return;


  try {

    const data =
      JSON.parse(saved);


    document
      .getElementById("post-title")
      .value =
      data.title || "";


    document
      .getElementById("post-slug")
      .value =
      data.slug || "";


    document
      .getElementById("post-category")
      .value =
      data.category || "생활정보";


    document
      .getElementById("post-tags")
      .value =
      data.tags || "";


    document
      .getElementById("seo-title")
      .value =
      data.seoTitle || "";


    document
      .getElementById("seo-description")
      .value =
      data.seoDescription || "";


    document
      .getElementById("post-body")
      .value =
      data.body || "";


    uploadedImages =
      Array.isArray(data.images)
        ? data.images
        : [];


    renderImages();


  } catch(error) {

    console.log(error);

  }

}


/* ==========================================
   날짜
========================================== */

function getToday() {

  const now =
    new Date();


  const year =
    now.getFullYear();


  const month =
    String(
      now.getMonth() + 1
    ).padStart(
      2,
      "0"
    );


  const day =
    String(
      now.getDate()
    ).padStart(
      2,
      "0"
    );


  return `${year}-${month}-${day}`;

}


/* ==========================================
   YAML 문자열
========================================== */

function yamlText(text) {

  return String(text || "")
    .replace(
      /"/g,
      '\\"'
    );

}


/* ==========================================
   태그
========================================== */

function makeTags(tags) {

  if (!tags.trim()) {
    return "[]";
  }


  return "[" +

    tags
      .split(",")
      .map(function(tag) {

        return `"${yamlText(
          tag.trim()
        )}"`;

      })
      .filter(Boolean)
      .join(", ")

    + "]";

}


/* ==========================================
   글 파일 만들기
========================================== */

function downloadPost() {

  const title =
    document
      .getElementById("post-title")
      .value
      .trim();


  const slug =
    document
      .getElementById("post-slug")
      .value
      .trim();


  const category =
    document
      .getElementById("post-category")
      .value;


  const tags =
    document
      .getElementById("post-tags")
      .value;


  const seoTitle =
    document
      .getElementById("seo-title")
      .value
      .trim();


  const seoDescription =
    document
      .getElementById("seo-description")
      .value
      .trim();


  let body =
    document
      .getElementById("post-body")
      .value;


  if (!title) {

    alert(
      "글 제목을 입력해주세요."
    );

    return;

  }


  if (!slug) {

    alert(
      "URL 슬러그를 입력해주세요."
    );

    return;

  }


  if (!body.trim()) {

    alert(
      "본문을 입력해주세요."
    );

    return;

  }


  /*
    본문의 이미지 표시를
    실제 HTML 이미지로 변환
  */

  uploadedImages.forEach(function(image) {

    const marker =
      `[[IMAGE:${image.id}]]`;


    const imageHtml = `
<img
src="${image.data}"
alt="${escapeHtml(image.name)}"
>
`;


    body =
      body.split(marker)
        .join(imageHtml);

  });


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
    frontMatter +
    body;


  const blob =
    new Blob(
      [content],
      {
        type:
          "text/markdown;charset=utf-8"
      }
    );


  const url =
    URL.createObjectURL(blob);


  const link =
    document.createElement("a");


  link.href =
    url;


  link.download =
    `${date}-${slug}.md`;


  document
    .body
    .appendChild(link);


  link.click();


  document
    .body
    .removeChild(link);


  URL.revokeObjectURL(url);


  document
    .getElementById("status-message")
    .textContent =
    "✓ 글 파일이 만들어졌습니다.";

}


/* ==========================================
   초기화
========================================== */

function clearPost() {

  if (
    !confirm(
      "작성 중인 내용을 모두 삭제할까요?"
    )
  ) {

    return;

  }


  document
    .getElementById("post-title")
    .value = "";


  document
    .getElementById("post-slug")
    .value = "";


  document
    .getElementById("post-category")
    .value =
    "생활정보";


  document
    .getElementById("post-tags")
    .value = "";


  document
    .getElementById("seo-title")
    .value = "";


  document
    .getElementById("seo-description")
    .value = "";


  document
    .getElementById("post-body")
    .value = "";


  document
    .getElementById("post-images")
    .value = "";


  document
    .getElementById("image-list")
    .innerHTML = "";


  document
    .getElementById("preview-box")
    .style.display =
    "none";


  uploadedImages = [];


  localStorage.removeItem(
    "donfree-post-draft"
  );


  document
    .getElementById("status-message")
    .textContent = "";

}


/* ==========================================
   시작
========================================== */

loadDraft();

</script>
