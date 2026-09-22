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
  margin-top: 20px;
  margin-bottom: 7px;
  font-weight: 700;
}

.write-wrap input,
.write-wrap select,
.write-wrap textarea {
  width: 100%;
  box-sizing: border-box;
  padding: 12px;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-size: 15px;
  background: #fff;
}

.write-wrap textarea {
  min-height: 500px;
  resize: vertical;
  line-height: 1.8;
}

.help {
  margin-top: 8px;
  padding: 12px 14px;
  background: #f6f6f6;
  border-radius: 8px;
  font-size: 13px;
  line-height: 1.6;
}

.toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 7px;
  margin: 10px 0;
}

.toolbar button,
.actions button {
  border: 0;
  border-radius: 7px;
  padding: 9px 14px;
  cursor: pointer;
  font-weight: 700;
}

.toolbar button {
  background: #f1f1f1;
}

.actions {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 15px;
}

.actions button {
  background: #111;
  color: white;
}

.actions .danger {
  background: #eee;
  color: #333;
}

.image-list {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-top: 12px;
}

.image-item {
  width: 160px;
  border: 1px solid #ddd;
  border-radius: 8px;
  overflow: hidden;
  background: #fff;
}

.image-item img {
  display: block;
  width: 100%;
  height: 110px;
  object-fit: cover;
}

.image-info {
  padding: 8px;
}

.image-info input {
  width: 100%;
  box-sizing: border-box;
  padding: 6px;
  font-size: 12px;
  margin-bottom: 6px;
}

.image-info button {
  width: 100%;
  border: 0;
  padding: 7px;
  margin-top: 4px;
  border-radius: 5px;
  cursor: pointer;
  background: #f1f1f1;
}

.image-info .insert-btn {
  background: #111;
  color: white;
}

.preview-wrap {
  margin-top: 35px;
  padding-top: 25px;
  border-top: 1px solid #ddd;
}

.preview {
  padding: 25px;
  border: 1px solid #eee;
  border-radius: 10px;
  line-height: 1.8;
  overflow-wrap: break-word;
}

.preview img {
  display: block;
  max-width: 100%;
  height: auto;
  margin: 20px auto;
  border-radius: 8px;
}

.preview h2 {
  margin-top: 30px;
}

.preview a {
  color: #06c;
  text-decoration: underline;
}

.status {
  margin-top: 10px;
  font-size: 13px;
  color: #666;
}
</style>


<div class="write-wrap">

<h1>글쓰기</h1>

<div class="help">
본문을 작성한 뒤 원하는 위치에 커서를 놓고 이미지를 선택하면
해당 위치에 이미지가 바로 들어갑니다.<br>
링크는 링크로 만들 문장을 드래그한 뒤 <strong>🔗 링크</strong> 버튼을 누르면 됩니다.
</div>


<!-- 제목 -->

<label>제목</label>

<input
  type="text"
  id="postTitle"
  placeholder="글 제목을 입력하세요"
>


<!-- URL -->

<label>URL 슬러그</label>

<input
  type="text"
  id="postSlug"
  placeholder="예: instagram-reels-download"
>


<!-- 카테고리 -->

<label>카테고리</label>

<input
  type="text"
  id="postCategory"
  placeholder="예: 생활정보"
>


<!-- 태그 -->

<label>태그</label>

<input
  type="text"
  id="postTags"
  placeholder="예: 인스타, 릴스, 다운로드"
>


<!-- SEO 제목 -->

<label>SEO 제목</label>

<input
  type="text"
  id="seoTitle"
  placeholder="검색 결과에 표시될 제목"
>


<!-- SEO 설명 -->

<label>SEO 설명</label>

<input
  type="text"
  id="seoDescription"
  placeholder="검색 결과에 표시될 설명"
>


<!-- 이미지 -->

<label>이미지 첨부</label>

<input
  type="file"
  id="imageInput"
  accept="image/*"
  multiple
>

<div class="help">
여러 장을 한 번에 선택할 수 있습니다.
선택한 이미지는 현재 본문 커서 위치에 자동으로 삽입됩니다.
</div>

<div
  id="imageList"
  class="image-list"
></div>


<!-- 본문 -->

<label>본문</label>

<div class="toolbar">

<button
  type="button"
  onclick="makeBold()"
>
굵게
</button>

<button
  type="button"
  onclick="makeH2()"
>
H2
</button>

<button
  type="button"
  onclick="makeLink()"
>
🔗 링크
</button>

<button
  type="button"
  onclick="makeDivider()"
>
구분선
</button>

</div>


<textarea
  id="postBody"
  placeholder="본문을 작성하세요."
></textarea>


<!-- 버튼 -->

<div class="actions">

<button
  type="button"
  onclick="showPreview()"
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
  onclick="downloadMarkdown()"
>
📄 글 파일 만들기
</button>

<button
  type="button"
  class="danger"
  onclick="clearEditor()"
>
🗑️ 초기화
</button>

</div>


<div
  id="status"
  class="status"
></div>


<!-- 미리보기 -->

<div class="preview-wrap">

<h2>미리보기</h2>

<div
  id="preview"
  class="preview"
>
작성한 글이 여기에 표시됩니다.
</div>

</div>

</div>


<script>

let uploadedImages = [];

let imageCounter = 0;


/* =========================================
   본문 커서 위치 기억
========================================= */

const textarea =
  document.getElementById("postBody");


let savedCursorStart = 0;
let savedCursorEnd = 0;


textarea.addEventListener("blur", function() {

  savedCursorStart =
    textarea.selectionStart;

  savedCursorEnd =
    textarea.selectionEnd;

});


textarea.addEventListener("click", function() {

  savedCursorStart =
    textarea.selectionStart;

  savedCursorEnd =
    textarea.selectionEnd;

});


textarea.addEventListener("keyup", function() {

  savedCursorStart =
    textarea.selectionStart;

  savedCursorEnd =
    textarea.selectionEnd;

});


/* =========================================
   이미지 선택
========================================= */

document
  .getElementById("imageInput")
  .addEventListener("change", function(event) {

    const files =
      Array.from(event.target.files);

    if (!files.length) return;


    /*
      이미지들을 순서대로 처리
    */

    files.forEach(function(file) {

      if (!file.type.startsWith("image/")) {
        return;
      }


      const reader =
        new FileReader();


      reader.onload = function(e) {

        imageCounter++;

        const image = {

          id:
            "image-" +
            Date.now() +
            "-" +
            imageCounter,

          name:
            file.name,

          alt:
            file.name
              .replace(/\.[^/.]+$/, ""),

          src:
            e.target.result

        };


        uploadedImages.push(image);


        renderImageList();


        /*
          이미지 선택 즉시
          현재 커서 위치에 삽입
        */

        insertImageAtCursor(image);

      };


      reader.readAsDataURL(file);

    });


    /*
      같은 파일을 다시 선택할 수 있도록 초기화
    */

    event.target.value = "";

});


/* =========================================
   이미지 목록
========================================= */

function renderImageList() {

  const container =
    document.getElementById("imageList");


  container.innerHTML = "";


  uploadedImages.forEach(function(image) {

    const item =
      document.createElement("div");

    item.className =
      "image-item";


    item.innerHTML = `

      <img
        src="${image.src}"
        alt=""
      >

      <div class="image-info">

        <input
          type="text"
          value="${escapeAttribute(image.alt)}"
          placeholder="이미지 설명"
          data-image-id="${image.id}"
        >

        <button
          type="button"
          class="insert-btn"
          data-insert-id="${image.id}"
        >
          본문에 넣기
        </button>

        <button
          type="button"
          data-delete-id="${image.id}"
        >
          삭제
        </button>

      </div>

    `;


    container.appendChild(item);


    /*
      이미지 설명 변경
    */

    const altInput =
      item.querySelector(
        `[data-image-id="${image.id}"]`
      );


    altInput.addEventListener(
      "input",
      function() {

        image.alt =
          altInput.value;

      }
    );


    /*
      본문에 다시 넣기
    */

    const insertButton =
      item.querySelector(
        `[data-insert-id="${image.id}"]`
      );


    insertButton.addEventListener(
      "click",
      function() {

        insertImageAtCursor(image);

      }
    );


    /*
      삭제
    */

    const deleteButton =
      item.querySelector(
        `[data-delete-id="${image.id}"]`
      );


    deleteButton.addEventListener(
      "click",
      function() {

        uploadedImages =
          uploadedImages.filter(
            function(item) {

              return item.id !== image.id;

            }
          );


        renderImageList();

      }
    );

  });

}


/* =========================================
   이미지 본문 삽입
========================================= */

function insertImageAtCursor(image) {

  const marker =
    `[[IMAGE:${image.id}]]`;


  const start =
    savedCursorStart;


  const end =
    savedCursorEnd;


  const current =
    textarea.value;


  textarea.value =
    current.substring(0, start)
    + marker
    + current.substring(end);


  /*
    삽입된 이미지 뒤로 커서 이동
  */

  const newPosition =
    start + marker.length;


  textarea.focus();


  textarea.selectionStart =
    newPosition;


  textarea.selectionEnd =
    newPosition;


  savedCursorStart =
    newPosition;


  savedCursorEnd =
    newPosition;


  showStatus(
    "이미지가 본문에 삽입되었습니다."
  );

}


/* =========================================
   굵게
========================================= */

function makeBold() {

  const start =
    textarea.selectionStart;

  const end =
    textarea.selectionEnd;


  const selected =
    textarea.value.substring(
      start,
      end
    );


  if (!selected) {

    alert(
      "굵게 만들 글자를 먼저 드래그해주세요."
    );

    return;

  }


  const result =
    `**${selected}**`;


  textarea.setRangeText(
    result,
    start,
    end,
    "end"
  );


  textarea.focus();

}


/* =========================================
   H2
========================================= */

function makeH2() {

  const start =
    textarea.selectionStart;

  const end =
    textarea.selectionEnd;


  const selected =
    textarea.value.substring(
      start,
      end
    );


  if (!selected) {

    alert(
      "H2로 만들 글자를 먼저 드래그해주세요."
    );

    return;

  }


  const result =
    `## ${selected}`;


  textarea.setRangeText(
    result,
    start,
    end,
    "end"
  );


  textarea.focus();

}


/* =========================================
   링크
========================================= */

function makeLink() {

  const start =
    textarea.selectionStart;

  const end =
    textarea.selectionEnd;


  const selected =
    textarea.value.substring(
      start,
      end
    );


  if (!selected) {

    alert(
      "링크로 만들 글자를 먼저 드래그해주세요."
    );

    return;

  }


  const url =
    prompt(
      "연결할 주소(URL)를 입력하세요.\n\n예:\nhttps://tool.donfree.co.kr/video/"
    );


  if (!url) return;


  const result =
    `[${selected}](${url})`;


  textarea.setRangeText(
    result,
    start,
    end,
    "end"
  );


  textarea.focus();


  showStatus(
    "링크가 삽입되었습니다."
  );

}


/* =========================================
   구분선
========================================= */

function makeDivider() {

  const start =
    textarea.selectionStart;


  const result =
    "\n\n---\n\n";


  textarea.setRangeText(
    result,
    start,
    textarea.selectionEnd,
    "end"
  );


  textarea.focus();

}


/* =========================================
   미리보기
========================================= */

function showPreview() {

  let body =
    textarea.value;


  /*
    이미지 마커를 이미지 HTML로 변경
  */

  uploadedImages.forEach(
    function(image) {

      const marker =
        `[[IMAGE:${image.id}]]`;


      const imageHTML =
        `<img src="${image.src}" alt="${escapeAttribute(image.alt)}">`;


      body =
        body.split(marker)
             .join(imageHTML);

    }
  );


  /*
    먼저 HTML 특수문자를 처리하되
    이미지 태그는 건드리지 않기 위해
    간단한 Markdown 변환 방식 사용
  */

  body =
    convertMarkdown(body);


  document
    .getElementById("preview")
    .innerHTML =
      body;

}


/* =========================================
   Markdown → 미리보기 HTML
========================================= */

function convertMarkdown(text) {

  /*
    이미지 태그를 임시 보관
  */

  const imageTags = [];

  text =
    text.replace(
      /<img\b[^>]*>/gi,
      function(match) {

        const key =
          `___DONFREE_IMAGE_${imageTags.length}___`;

        imageTags.push(match);

        return key;

      }
    );


  /*
    HTML escape
  */

  text =
    escapeHTML(text);


  /*
    H2
  */

  text =
    text.replace(
      /^## (.+)$/gm,
      "<h2>$1</h2>"
    );


  /*
    굵게
  */

  text =
    text.replace(
      /\*\*(.*?)\*\*/g,
      "<strong>$1</strong>"
    );


  /*
    링크
  */

  text =
    text.replace(
      /\[([^\]]+)\]\((https?:\/\/[^\s)]+)\)/g,
      '<a href="$2" target="_blank" rel="noopener">$1</a>'
    );


  /*
    구분선
  */

  text =
    text.replace(
      /^---$/gm,
      "<hr>"
    );


  /*
    줄바꿈
  */

  text =
    text.replace(
      /\n/g,
      "<br>"
    );


  /*
    이미지 복원
  */

  imageTags.forEach(
    function(tag, index) {

      text =
        text.replace(
          `___DONFREE_IMAGE_${index}___`,
          tag
        );

    }
  );


  return text;

}


/* =========================================
   임시저장
========================================= */

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
      textarea.value,

    images:
      uploadedImages

  };


  try {

    localStorage.setItem(
      "donfree-write-draft",
      JSON.stringify(data)
    );


    showStatus(
      "임시저장했습니다."
    );

  } catch(error) {

    alert(
      "이미지가 너무 커서 임시저장하지 못했습니다."
    );

  }

}


/* =========================================
   임시저장 불러오기
========================================= */

function loadDraft() {

  const saved =
    localStorage.getItem(
      "donfree-write-draft"
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


    textarea.value =
      data.body || "";


    uploadedImages =
      data.images || [];


    renderImageList();


    showPreview();


    showStatus(
      "임시저장한 글을 불러왔습니다."
    );


  } catch(error) {

    alert(
      "임시저장한 글을 불러오지 못했습니다."
    );

  }

}


/* =========================================
   Markdown 파일 만들기
========================================= */

function downloadMarkdown() {

  const title =
    document.getElementById("postTitle").value.trim();


  const slug =
    document.getElementById("postSlug").value.trim();


  const category =
    document.getElementById("postCategory").value.trim();


  const tags =
    document.getElementById("postTags").value.trim();


  const seoDescription =
    document
      .getElementById("seoDescription")
      .value
      .trim();


  if (!title) {

    alert(
      "제목을 입력해주세요."
    );

    return;

  }


  if (!slug) {

    alert(
      "URL 슬러그를 입력해주세요."
    );

    return;

  }


  let body =
    textarea.value;


  /*
    이미지 마커를 실제 HTML 이미지로 변경
  */

  uploadedImages.forEach(
    function(image) {

      const marker =
        `[[IMAGE:${image.id}]]`;


      const imageHTML =
        `<img src="${image.src}" alt="${image.alt}">`;


      body =
        body.split(marker)
             .join(imageHTML);

    }
  );


  const today =
    new Date()
      .toISOString()
      .substring(0, 10);


  const tagList =
    tags
      .split(",")
      .map(
        function(tag) {

          return tag.trim();

        }
      )
      .filter(Boolean);


  const tagText =
    "[" +
    tagList
      .map(
        function(tag) {

          return `"${escapeYAML(tag)}"`;

        }
      )
      .join(", ") +
    "]";


  const markdown =
`---
title: "${escapeYAML(title)}"
date: ${today}
categories: ["${escapeYAML(category || "생활정보")}"]
tags: ${tagText}
description: "${escapeYAML(seoDescription)}"
---

${body}
`;


  const blob =
    new Blob(
      [markdown],
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
    `${today}-${slug}.md`;


  document.body.appendChild(link);


  link.click();


  link.remove();


  URL.revokeObjectURL(url);


  showStatus(
    "Markdown 파일을 만들었습니다."
  );

}


/* =========================================
   초기화
========================================= */

function clearEditor() {

  const confirmed =
    confirm(
      "작성 중인 내용을 모두 삭제할까요?"
    );


  if (!confirmed) return;


  document.getElementById("postTitle").value = "";

  document.getElementById("postSlug").value = "";

  document.getElementById("postCategory").value = "";

  document.getElementById("postTags").value = "";

  document.getElementById("seoTitle").value = "";

  document.getElementById("seoDescription").value = "";

  textarea.value = "";


  uploadedImages = [];


  renderImageList();


  document.getElementById("preview").innerHTML =
    "작성한 글이 여기에 표시됩니다.";


  showStatus("");

}


/* =========================================
   상태 메시지
========================================= */

function showStatus(message) {

  document.getElementById("status").textContent =
    message;

}


/* =========================================
   HTML escape
========================================= */

function escapeHTML(value) {

  return String(value)
    .replace(/&/g, "&amp;")
    .replace(/</g, "&lt;")
    .replace(/>/g, "&gt;")
    .replace(/"/g, "&quot;")
    .replace(/'/g, "&#039;");

}


/* =========================================
   Attribute escape
========================================= */

function escapeAttribute(value) {

  return String(value)
    .replace(/&/g, "&amp;")
    .replace(/"/g, "&quot;")
    .replace(/</g, "&lt;")
    .replace(/>/g, "&gt;");

}


/* =========================================
   YAML escape
========================================= */

function escapeYAML(value) {

  return String(value)
    .replace(/\\/g, "\\\\")
    .replace(/"/g, '\\"')
    .replace(/\r?\n/g, " ");

}

</script>
