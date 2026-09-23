---
layout: page
title: 글쓰기
icon: fas fa-pen
order: 1
---

<style>
.write-wrap {
  max-width: 1000px;
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
  border: 1px solid #d8d8d8;
  border-radius: 8px;
  padding: 11px;
  font-size: 14px;
  background: #fff;
}

.write-wrap textarea {
  min-height: 420px;
  resize: vertical;
  line-height: 1.8;
}

.write-help {
  margin-top: 6px;
  color: #777;
  font-size: 12px;
}

.write-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin: 14px 0;
}

.write-buttons button,
.image-actions button {
  border: 0;
  border-radius: 7px;
  padding: 9px 13px;
  cursor: pointer;
  font-size: 13px;
  font-weight: 700;
  background: #333;
  color: #fff;
}

.write-buttons button:hover,
.image-actions button:hover {
  opacity: .8;
}

button.primary {
  background: #1677ff;
}

button.danger {
  background: #d9363e;
}

.editor-box {
  margin-top: 22px;
  padding: 18px;
  border: 1px solid #ddd;
  border-radius: 10px;
  background: #fafafa;
}

.editor-box h3 {
  margin-top: 0;
  font-size: 17px;
}

.image-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(230px, 1fr));
  gap: 14px;
  margin-top: 15px;
}

.image-item {
  padding: 12px;
  border: 1px solid #ddd;
  border-radius: 10px;
  background: #fff;
}

.image-item img {
  display: block;
  width: 100%;
  height: 135px;
  object-fit: contain;
  border-radius: 6px;
  background: #f3f3f3;
  margin-bottom: 10px;
}

.image-name {
  font-size: 12px;
  color: #555;
  word-break: break-all;
  margin-bottom: 8px;
}

.image-number {
  font-weight: 700;
  margin-bottom: 8px;
}

.image-size-row {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 10px;
}

.image-size-row label {
  margin: 0;
  white-space: nowrap;
  font-size: 12px;
}

.image-size-row select {
  padding: 7px;
}

.image-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}

.image-actions button {
  padding: 7px 9px;
  font-size: 12px;
}

.preview-box {
  margin-top: 25px;
  padding: 22px;
  border: 1px solid #ddd;
  border-radius: 10px;
  background: #fff;
}

.preview-box h2 {
  margin-top: 0;
}

#previewContent {
  line-height: 1.8;
  word-break: break-word;
}

#previewContent img {
  display: block;
  max-width: 100%;
  height: auto;
  margin: 18px auto;
}

#previewContent a {
  color: #1677ff;
  text-decoration: underline;
}

#previewContent h1,
#previewContent h2,
#previewContent h3 {
  margin-top: 25px;
}

.empty-image {
  color: #888;
  font-size: 13px;
}
</style>

<div class="write-wrap">

  <label for="postTitle">글 제목</label>
  <input id="postTitle" type="text" placeholder="글 제목을 입력하세요">

  <label for="postSlug">주소용 슬러그</label>
  <input id="postSlug" type="text" placeholder="예: instagram-reels-download">

  <div class="write-help">
    영문과 숫자, 하이픈을 사용하는 것이 좋습니다.
  </div>

  <label for="postCategory">카테고리</label>
  <input id="postCategory" type="text" placeholder="예: 생활정보">

  <label for="postTags">태그</label>
  <input id="postTags" type="text" placeholder="예: 인스타, 릴스, 다운로드">

  <label for="seoTitle">SEO 제목</label>
  <input id="seoTitle" type="text" placeholder="검색 결과에 표시할 제목">

  <label for="seoDescription">SEO 설명</label>
  <input id="seoDescription" type="text" placeholder="검색 결과에 표시할 설명">

  <label for="postBody">본문</label>
  <textarea id="postBody" placeholder="본문을 작성하세요.

사진을 넣고 싶은 위치에 커서를 놓은 다음
아래의 사진 추가 버튼을 눌러주세요."></textarea>

  <div class="write-help">
    사진은 본문에 큰 이미지로 표시되지 않고,
    🖼 이미지 1, 🖼 이미지 2 형태로 표시됩니다.
    미리보기에서는 설정한 크기로 나타납니다.
  </div>

  <div class="write-buttons">
    <button type="button" id="addImageButton" class="primary">
      여러 사진 추가
    </button>

    <button type="button" id="boldButton">
      굵게
    </button>

    <button type="button" id="headingButton">
      소제목
    </button>

    <button type="button" id="linkButton">
      링크 삽입
    </button>

    <button type="button" id="previewButton">
      미리보기
    </button>

    <button type="button" id="saveButton">
      임시저장
    </button>

    <button type="button" id="loadButton">
      임시저장 불러오기
    </button>

    <button type="button" id="downloadButton" class="primary">
      글 파일 만들기
    </button>

    <button type="button" id="clearButton" class="danger">
      전체 초기화
    </button>
  </div>

  <input
    type="file"
    id="imageInput"
    accept="image/*"
    multiple
    hidden
  >

  <div class="editor-box">
    <h3>첨부한 사진</h3>

    <div class="write-help">
      사진을 여러 장 선택할 수 있습니다.
      각 사진의 크기를 개별적으로 설정할 수 있습니다.
    </div>

    <div id="imageList" class="image-list">
      <div class="empty-image">
        아직 첨부한 사진이 없습니다.
      </div>
    </div>
  </div>

  <div id="previewBox" class="preview-box" hidden>
    <h2 id="previewTitle"></h2>
    <div id="previewContent"></div>
  </div>

</div>

<script>
(function () {
  const titleInput = document.getElementById("postTitle");
  const slugInput = document.getElementById("postSlug");
  const categoryInput = document.getElementById("postCategory");
  const tagsInput = document.getElementById("postTags");
  const seoTitleInput = document.getElementById("seoTitle");
  const seoDescriptionInput = document.getElementById("seoDescription");
  const bodyInput = document.getElementById("postBody");

  const imageInput = document.getElementById("imageInput");
  const imageList = document.getElementById("imageList");

  const previewBox = document.getElementById("previewBox");
  const previewTitle = document.getElementById("previewTitle");
  const previewContent = document.getElementById("previewContent");

  let images = [];
  let nextImageNumber = 1;

  let savedCursorStart = 0;
  let savedCursorEnd = 0;
  let savedScrollTop = 0;

  function saveCursorPosition() {
    savedCursorStart = bodyInput.selectionStart;
    savedCursorEnd = bodyInput.selectionEnd;
    savedScrollTop = window.scrollY;
  }

  function restoreCursorPosition(position) {
    bodyInput.focus();
    bodyInput.setSelectionRange(position, position);
    window.scrollTo(0, savedScrollTop);
  }

  function escapeHtml(value) {
    return String(value)
      .replace(/&/g, "&amp;")
      .replace(/</g, "&lt;")
      .replace(/>/g, "&gt;")
      .replace(/"/g, "&quot;")
      .replace(/'/g, "&#039;");
  }

  function getMarker(number) {
    return `【🖼 이미지 ${number}】`;
  }

  function insertTextAtCursor(text) {
    const start = bodyInput.selectionStart;
    const end = bodyInput.selectionEnd;

    const before = bodyInput.value.substring(0, start);
    const after = bodyInput.value.substring(end);

    bodyInput.value = before + text + after;

    const newPosition = start + text.length;
    restoreCursorPosition(newPosition);
  }

  function openImagePicker() {
    saveCursorPosition();
    imageInput.click();
  }

  document
    .getElementById("addImageButton")
    .addEventListener("click", openImagePicker);

  imageInput.addEventListener("change", function (event) {
    const selectedFiles = Array.from(event.target.files || []);

    if (selectedFiles.length === 0) {
      return;
    }

    let insertPosition = savedCursorStart;
    let addedText = "";

    selectedFiles.forEach(function (file) {
      if (!file.type.startsWith("image/")) {
        return;
      }

      const reader = new FileReader();

      reader.onload = function (loadEvent) {
        const imageNumber = nextImageNumber++;

        images.push({
          number: imageNumber,
          name: file.name,
          src: loadEvent.target.result,
          size: "60"
        });

        renderImageList();

        const marker = getMarker(imageNumber);

        const currentStart = bodyInput.selectionStart;
        const currentEnd = bodyInput.selectionEnd;

        const before = bodyInput.value.substring(0, currentStart);
        const after = bodyInput.value.substring(currentEnd);

        const insertValue = "\n\n" + marker + "\n\n";

        bodyInput.value = before + insertValue + after;

        const newPosition = currentStart + insertValue.length;

        bodyInput.focus();
        bodyInput.setSelectionRange(newPosition, newPosition);
        window.scrollTo(0, savedScrollTop);

        saveDraftSilently();
      };

      reader.readAsDataURL(file);
    });

    imageInput.value = "";
  });

  function renderImageList() {
    imageList.innerHTML = "";

    if (images.length === 0) {
      imageList.innerHTML =
        '<div class="empty-image">아직 첨부한 사진이 없습니다.</div>';
      return;
    }

    images.forEach(function (image) {
      const item = document.createElement("div");
      item.className = "image-item";

      item.innerHTML = `
        <div class="image-number">이미지 ${image.number}</div>
        <img src="${image.src}" alt="${escapeHtml(image.name)}">

        <div class="image-name">
          ${escapeHtml(image.name)}
        </div>

        <div class="image-size-row">
          <label>사진 크기</label>
          <select class="image-size-select">
            <option value="40" ${image.size === "40" ? "selected" : ""}>
              작게 40%
            </option>
            <option value="60" ${image.size === "60" ? "selected" : ""}>
              보통 60%
            </option>
            <option value="80" ${image.size === "80" ? "selected" : ""}>
              크게 80%
            </option>
            <option value="100" ${image.size === "100" ? "selected" : ""}>
              원본 100%
            </option>
          </select>
        </div>

        <div class="image-actions">
          <button type="button" class="insert-image">
            본문에 넣기
          </button>

          <button type="button" class="remove-image danger">
            삭제
          </button>
        </div>
      `;

      const sizeSelect = item.querySelector(".image-size-select");

      sizeSelect.addEventListener("change", function () {
        image.size = sizeSelect.value;
        saveDraftSilently();
      });

      item
        .querySelector(".insert-image")
        .addEventListener("click", function () {
          saveCursorPosition();

          const marker = getMarker(image.number);
          const start = bodyInput.selectionStart;
          const end = bodyInput.selectionEnd;

          const before = bodyInput.value.substring(0, start);
          const after = bodyInput.value.substring(end);

          const insertValue = "\n\n" + marker + "\n\n";

          bodyInput.value = before + insertValue + after;

          restoreCursorPosition(start + insertValue.length);
          saveDraftSilently();
        });

      item
        .querySelector(".remove-image")
        .addEventListener("click", function () {
          const marker = getMarker(image.number);

          bodyInput.value = bodyInput.value
            .split(marker)
            .join("");

          images = images.filter(function (item) {
            return item.number !== image.number;
          });

          renderImageList();
          saveDraftSilently();
        });

      imageList.appendChild(item);
    });
  }

  function makeBold() {
    const start = bodyInput.selectionStart;
    const end = bodyInput.selectionEnd;

    if (start === end) {
      insertTextAtCursor("**굵게 입력할 문장**");
      return;
    }

    const selected = bodyInput.value.substring(start, end);

    bodyInput.value =
      bodyInput.value.substring(0, start) +
      "**" + selected + "**" +
      bodyInput.value.substring(end);

    restoreCursorPosition(end + 4);
  }

  function makeHeading() {
    const start = bodyInput.selectionStart;
    const end = bodyInput.selectionEnd;

    if (start === end) {
      insertTextAtCursor("\n\n## 소제목\n\n");
      return;
    }

    const selected = bodyInput.value.substring(start, end);

    bodyInput.value =
      bodyInput.value.substring(0, start) +
      "## " + selected +
      bodyInput.value.substring(end);

    restoreCursorPosition(end + 3);
  }

  function insertLink() {
    const url = prompt("링크 주소를 입력하세요.");

    if (!url) {
      return;
    }

    const text = prompt("링크에 표시할 문구를 입력하세요.", "자세히 보기");

    if (!text) {
      return;
    }

    insertTextAtCursor(`[${text}](${url})`);
  }

  document
    .getElementById("boldButton")
    .addEventListener("click", makeBold);

  document
    .getElementById("headingButton")
    .addEventListener("click", makeHeading);

  document
    .getElementById("linkButton")
    .addEventListener("click", insertLink);

  function replaceImageMarkers(text, forMarkdown) {
    images.forEach(function (image) {
      const marker = getMarker(image.number);
      const width = image.size || "60";

      const imageHtml = forMarkdown
        ? `<img src="${image.src}" alt="${escapeHtml(image.name)}" style="width:${width}%;max-width:100%;height:auto;">`
        : `<img src="${image.src}" alt="${escapeHtml(image.name)}" style="width:${width}%;max-width:100%;height:auto;">`;

      text = text.split(marker).join(imageHtml);
    });

    return text;
  }

  function markdownToHtml(markdown) {
    let html = escapeHtml(markdown);

    images.forEach(function (image) {
      const marker = getMarker(image.number);
      const escapedMarker = escapeHtml(marker);
      const width = image.size || "60";

      const imageHtml =
        `<img src="${image.src}" alt="${escapeHtml(image.name)}" ` +
        `style="width:${width}%;max-width:100%;height:auto;">`;

      html = html.split(escapedMarker).join(imageHtml);
    });

    html = html.replace(
      /\[([^\]]+)\]\((https?:\/\/[^\s)]+)\)/g,
      '<a href="$2" target="_blank" rel="noopener">$1</a>'
    );

    html = html.replace(/^### (.*)$/gm, "<h3>$1</h3>");
    html = html.replace(/^## (.*)$/gm, "<h2>$1</h2>");
    html = html.replace(/^# (.*)$/gm, "<h1>$1</h1>");

    html = html.replace(/\*\*(.*?)\*\*/g, "<strong>$1</strong>");

    html = html.replace(/\n/g, "<br>");

    return html;
  }

  function showPreview() {
    previewTitle.textContent = titleInput.value || "제목 없음";
    previewContent.innerHTML = markdownToHtml(bodyInput.value);
    previewBox.hidden = false;

    previewBox.scrollIntoView({
      behavior: "smooth",
      block: "start"
    });
  }

  document
    .getElementById("previewButton")
    .addEventListener("click", showPreview);

  function getDraftData() {
    return {
      title: titleInput.value,
      slug: slugInput.value,
      category: categoryInput.value,
      tags: tagsInput.value,
      seoTitle: seoTitleInput.value,
      seoDescription: seoDescriptionInput.value,
      body: bodyInput.value,
      images: images,
      nextImageNumber: nextImageNumber
    };
  }

  function saveDraftSilently() {
    try {
      localStorage.setItem(
        "donfree-write-draft",
        JSON.stringify(getDraftData())
      );
    } catch (error) {
      console.warn("임시저장 실패:", error);
    }
  }

  document
    .getElementById("saveButton")
    .addEventListener("click", function () {
      saveDraftSilently();
      alert("임시저장되었습니다.");
    });

  document
    .getElementById("loadButton")
    .addEventListener("click", function () {
      const saved = localStorage.getItem("donfree-write-draft");

      if (!saved) {
        alert("저장된 글이 없습니다.");
        return;
      }

      try {
        const data = JSON.parse(saved);

        titleInput.value = data.title || "";
        slugInput.value = data.slug || "";
        categoryInput.value = data.category || "";
        tagsInput.value = data.tags || "";
        seoTitleInput.value = data.seoTitle || "";
        seoDescriptionInput.value = data.seoDescription || "";
        bodyInput.value = data.body || "";

        images = Array.isArray(data.images) ? data.images : [];

        images.forEach(function (image, index) {
          if (!image.number) {
            image.number = index + 1;
          }

          if (!image.size) {
            image.size = "60";
          }
        });

        nextImageNumber =
          data.nextImageNumber ||
          Math.max(0, ...images.map(function (image) {
            return image.number;
          })) + 1;

        renderImageList();

        alert("임시저장한 글을 불러왔습니다.");
      } catch (error) {
        alert("임시저장 데이터를 불러오지 못했습니다.");
      }
    });

  function createMarkdownFile() {
    const title = titleInput.value.trim() || "donfree-post";

    const frontMatter =
`---
layout: post
title: "${title.replace(/"/g, '\\"')}"
date: ${new Date().toISOString()}
categories: [${categoryInput.value || "생활정보"}]
tags: [${tagsInput.value
  .split(",")
  .map(function (tag) {
    return tag.trim();
  })
  .filter(Boolean)
  .join(", ")}]
description: "${seoDescriptionInput.value.replace(/"/g, '\\"')}"
---

`;

    const content = replaceImageMarkers(bodyInput.value, true);

    const markdown = frontMatter + content;

    const blob = new Blob([markdown], {
      type: "text/markdown;charset=utf-8"
    });

    const url = URL.createObjectURL(blob);
    const link = document.createElement("a");

    link.href = url;
    link.download = (slugInput.value.trim() || "donfree-post") + ".md";

    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);

    URL.revokeObjectURL(url);
  }

  document
    .getElementById("downloadButton")
    .addEventListener("click", createMarkdownFile);

  document
    .getElementById("clearButton")
    .addEventListener("click", function () {
      const confirmed = confirm(
        "작성한 내용과 첨부 사진을 모두 삭제할까요?"
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
      bodyInput.value = "";

      images = [];
      nextImageNumber = 1;

      localStorage.removeItem("donfree-write-draft");

      renderImageList();
      previewBox.hidden = true;
    });

  bodyInput.addEventListener("input", function () {
    saveDraftSilently();
  });

  renderImageList();
})();
</script>
