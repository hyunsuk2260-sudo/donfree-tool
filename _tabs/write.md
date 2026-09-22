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

.write-box {
  margin-bottom: 22px;
}

.write-label {
  display: block;
  font-weight: 700;
  margin-bottom: 8px;
  font-size: 15px;
}

.write-input,
.write-select,
.write-textarea {
  width: 100%;
  box-sizing: border-box;
  border: 1px solid #ddd;
  border-radius: 10px;
  padding: 12px 14px;
  font-size: 15px;
  background: #fff;
}

.write-input:focus,
.write-select:focus,
.write-textarea:focus {
  outline: none;
  border-color: #777;
}

.editor-toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 7px;
  margin-bottom: 10px;
}

.editor-toolbar button,
.action-btn {
  border: 1px solid #ddd;
  background: #fff;
  border-radius: 8px;
  padding: 9px 13px;
  cursor: pointer;
  font-size: 14px;
}

.editor-toolbar button:hover,
.action-btn:hover {
  background: #f5f5f5;
}

.editor-toolbar button.primary {
  background: #222;
  color: #fff;
  border-color: #222;
}

.editor-area {
  min-height: 550px;
  max-height: 700px;
  overflow-y: auto;
  border: 1px solid #ddd;
  border-radius: 12px;
  padding: 20px;
  background: #fff;
  line-height: 1.8;
  font-size: 16px;
  box-sizing: border-box;
}

.editor-area:focus {
  outline: none;
  border-color: #777;
}

.editor-area:empty:before {
  content: "여기에 글을 작성하세요.";
  color: #aaa;
}

.editor-area img {
  display: block;
  max-width: 100%;
  height: auto;
  margin: 18px auto;
  border-radius: 8px;
}

.editor-area a {
  color: #1677ff;
  text-decoration: underline;
}

.preview-box {
  border: 1px solid #ddd;
  border-radius: 12px;
  padding: 24px;
  background: #fff;
  margin-top: 20px;
}

.preview-title {
  font-size: 28px;
  font-weight: 800;
  margin-bottom: 25px;
}

.preview-content {
  line-height: 1.8;
  font-size: 16px;
}

.preview-content img {
  display: block;
  max-width: 100%;
  height: auto;
  margin: 20px auto;
  border-radius: 8px;
}

.preview-content a {
  color: #1677ff;
  text-decoration: underline;
}

.bottom-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-top: 20px;
}

.bottom-buttons button {
  border: 0;
  border-radius: 10px;
  padding: 13px 18px;
  cursor: pointer;
  font-weight: 700;
}

.btn-preview {
  background: #eee;
  color: #222;
}

.btn-save {
  background: #222;
  color: #fff;
}

.btn-download {
  background: #1677ff;
  color: #fff;
}

.btn-clear {
  background: #f3f3f3;
  color: #555;
}

.write-help {
  font-size: 13px;
  color: #888;
  margin-top: 7px;
  line-height: 1.5;
}

.image-input {
  display: none;
}

.status-message {
  margin-top: 12px;
  font-size: 14px;
  color: #555;
}

@media (max-width: 768px) {
  .editor-area {
    min-height: 450px;
    padding: 15px;
  }

  .preview-box {
    padding: 18px;
  }

  .preview-title {
    font-size: 24px;
  }
}
</style>

<div class="write-wrap">

  <div class="write-box">
    <label class="write-label">제목</label>
    <input
      type="text"
      id="postTitle"
      class="write-input"
      placeholder="글 제목을 입력하세요"
    >
  </div>

  <div class="write-box">
    <label class="write-label">URL 슬러그</label>
    <input
      type="text"
      id="postSlug"
      class="write-input"
      placeholder="예: instagram-reels-download"
    >
    <div class="write-help">
      영문과 숫자, 하이픈(-)을 사용하는 것을 권장합니다.
    </div>
  </div>

  <div class="write-box">
    <label class="write-label">카테고리</label>
    <input
      type="text"
      id="postCategory"
      class="write-input"
      placeholder="예: 생활정보"
    >
  </div>

  <div class="write-box">
    <label class="write-label">태그</label>
    <input
      type="text"
      id="postTags"
      class="write-input"
      placeholder="예: 인스타, 릴스, 다운로드"
    >
  </div>

  <div class="write-box">
    <label class="write-label">SEO 제목</label>
    <input
      type="text"
      id="seoTitle"
      class="write-input"
      placeholder="검색 결과에 표시할 제목"
    >
  </div>

  <div class="write-box">
    <label class="write-label">SEO 설명</label>
    <input
      type="text"
      id="seoDescription"
      class="write-input"
      placeholder="검색 결과에 표시할 설명"
    >
  </div>

  <div class="write-box">

    <label class="write-label">본문</label>

    <div class="editor-toolbar">

      <button type="button" onclick="formatBold()">
        굵게
      </button>

      <button type="button" onclick="formatHeading()">
        소제목
      </button>

      <button type="button" onclick="insertLink()">
        🔗 링크
      </button>

      <button
        type="button"
        class="primary"
        onclick="openImagePicker()"
      >
        🖼 사진 넣기
      </button>

    </div>

    <input
      type="file"
      id="imageInput"
      class="image-input"
      accept="image/*"
      multiple
    >

    <div
      id="editor"
      class="editor-area"
      contenteditable="true"
      spellcheck="false"
    ></div>

    <div class="write-help">
      사진은 원하는 위치에 커서를 놓고 「사진 넣기」를 누르면 본문에 바로 들어갑니다.
    </div>

  </div>

  <div class="bottom-buttons">

    <button
      type="button"
      class="btn-preview"
      onclick="showPreview()"
    >
      미리보기
    </button>

    <button
      type="button"
      class="btn-save"
      onclick="saveDraft()"
    >
      임시저장
    </button>

    <button
      type="button"
      class="btn-download"
      onclick="downloadPost()"
    >
      글 파일 만들기
    </button>

    <button
      type="button"
      class="btn-clear"
      onclick="clearEditor()"
    >
      전체 지우기
    </button>

  </div>

  <div id="statusMessage" class="status-message"></div>

  <div
    id="previewArea"
    class="preview-box"
    style="display:none;"
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

<script>

(function() {

  const editor = document.getElementById("editor");
  const imageInput = document.getElementById("imageInput");
  const previewArea = document.getElementById("previewArea");

  let savedRange = null;

  let savedWindowScroll = 0;

  let savedEditorScroll = 0;


  /*
   * 현재 커서 위치 저장
   */

  function saveSelection() {

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


  /*
   * 현재 화면 위치 저장
   */

  function saveViewPosition() {

    savedWindowScroll = window.scrollY;

    savedEditorScroll = editor.scrollTop;

    saveSelection();

  }


  /*
   * 화면 위치 복원
   */

  function restoreViewPosition() {

    requestAnimationFrame(function() {

      window.scrollTo({
        top: savedWindowScroll,
        behavior: "instant"
      });

      editor.scrollTop = savedEditorScroll;

      requestAnimationFrame(function() {

        window.scrollTo({
          top: savedWindowScroll,
          behavior: "instant"
        });

        editor.scrollTop = savedEditorScroll;

      });

    });

  }


  /*
   * 에디터 선택 영역 감시
   */

  document.addEventListener("selectionchange", function() {

    const selection = window.getSelection();

    if (!selection || selection.rangeCount === 0) {
      return;
    }

    const range = selection.getRangeAt(0);

    if (editor.contains(range.commonAncestorContainer)) {

      savedRange = range.cloneRange();

    }

  });


  editor.addEventListener("keyup", saveSelection);

  editor.addEventListener("mouseup", saveSelection);

  editor.addEventListener("input", saveSelection);


  /*
   * 이미지 선택창 열기
   */

  window.openImagePicker = function() {

    saveViewPosition();

    imageInput.click();

  };


  /*
   * 이미지 파일 읽기
   */

  function readImage(file) {

    return new Promise(function(resolve, reject) {

      const reader = new FileReader();

      reader.onload = function(event) {

        resolve({
          src: event.target.result,
          alt: file.name.replace(/\.[^/.]+$/, "")
        });

      };

      reader.onerror = reject;

      reader.readAsDataURL(file);

    });

  }


  /*
   * 이미지 삽입
   */

  imageInput.addEventListener("change", async function(event) {

    const files = Array.from(event.target.files);

    if (!files.length) {
      return;
    }

    const restoreY = savedWindowScroll;

    const restoreEditorY = savedEditorScroll;

    try {

      const images = await Promise.all(
        files.map(readImage)
      );


      editor.focus({
        preventScroll: true
      });


      /*
       * 저장된 커서 위치가 있으면 복원
       */

      if (savedRange) {

        const selection = window.getSelection();

        selection.removeAllRanges();

        selection.addRange(savedRange);

      }


      /*
       * 여러 장을 순서대로 삽입
       */

      for (const imageData of images) {

        const img = document.createElement("img");

        img.src = imageData.src;

        img.alt = imageData.alt;

        img.className = "editor-image";

        img.setAttribute("data-donfree-image", "true");


        const selection = window.getSelection();

        let range;


        if (
          selection &&
          selection.rangeCount > 0 &&
          editor.contains(selection.getRangeAt(0).commonAncestorContainer)
        ) {

          range = selection.getRangeAt(0);

        } else {

          range = document.createRange();

          range.selectNodeContents(editor);

          range.collapse(false);

        }


        range.deleteContents();

        range.insertNode(img);


        /*
         * 이미지 뒤에서 계속 입력할 수 있도록
         */

        const br = document.createElement("br");

        img.parentNode.insertBefore(
          br,
          img.nextSibling
        );


        const newRange = document.createRange();

        newRange.setStartAfter(br);

        newRange.collapse(true);


        selection.removeAllRanges();

        selection.addRange(newRange);


        savedRange = newRange.cloneRange();


        /*
         * 이미지 로딩 후에도 화면 위치 복원
         */

        img.addEventListener(
          "load",
          restoreViewPosition,
          { once: true }
        );

      }


      /*
       * 최종 화면 복원
       */

      savedWindowScroll = restoreY;

      savedEditorScroll = restoreEditorY;

      restoreViewPosition();


      showStatus(
        images.length + "장의 사진이 본문에 삽입되었습니다."
      );

    } catch (error) {

      console.error(error);

      showStatus(
        "사진을 불러오는 중 문제가 발생했습니다."
      );

    }


    /*
     * 같은 파일을 다시 선택할 수 있도록 초기화
     */

    imageInput.value = "";

  });


  /*
   * 굵게
   */

  window.formatBold = function() {

    saveSelection();

    editor.focus({
      preventScroll: true
    });

    document.execCommand(
      "bold",
      false,
      null
    );

    saveSelection();

  };


  /*
   * 소제목
   */

  window.formatHeading = function() {

    saveSelection();

    editor.focus({
      preventScroll: true
    });

    document.execCommand(
      "formatBlock",
      false,
      "h2"
    );

    saveSelection();

  };


  /*
   * 링크 삽입
   */

  window.insertLink = function() {

    saveSelection();

    if (!savedRange || savedRange.collapsed) {

      alert(
        "먼저 링크로 만들 글자를 마우스로 선택해주세요."
      );

      return;

    }


    const url = prompt(
      "연결할 주소를 입력하세요.",
      "https://"
    );


    if (!url) {
      return;
    }


    if (
      !/^https?:\/\//i.test(url)
    ) {

      alert(
        "http:// 또는 https://로 시작하는 주소를 입력해주세요."
      );

      return;

    }


    editor.focus({
      preventScroll: true
    });


    const selection = window.getSelection();

    selection.removeAllRanges();

    selection.addRange(savedRange);


    document.execCommand(
      "createLink",
      false,
      url
    );


    /*
     * 생성된 링크에 보안 속성 추가
     */

    const links = editor.querySelectorAll("a");

    links.forEach(function(link) {

      if (
        link.href === url ||
        link.getAttribute("href") === url
      ) {

        link.target = "_blank";

        link.rel = "noopener noreferrer";

      }

    });


    saveSelection();

  };


  /*
   * 위험한 HTML 제거
   */

  function cleanHTML(html) {

    const parser = new DOMParser();

    const doc = parser.parseFromString(
      html,
      "text/html"
    );


    const forbidden = doc.querySelectorAll(
      "script, iframe, object, embed, form, input, button, textarea, style"
    );


    forbidden.forEach(function(element) {

      element.remove();

    });


    const links = doc.querySelectorAll("a");

    links.forEach(function(link) {

      const href = link.getAttribute("href") || "";

      if (!/^https?:\/\//i.test(href)) {

        link.removeAttribute("href");

      }

      link.target = "_blank";

      link.rel = "noopener noreferrer";

    });


    return doc.body.innerHTML;

  }


  /*
   * 미리보기
   */

  window.showPreview = function() {

    const title =
      document.getElementById("postTitle").value.trim();

    const html = cleanHTML(
      editor.innerHTML
    );


    document.getElementById(
      "previewTitle"
    ).textContent = title || "제목 없음";


    document.getElementById(
      "previewContent"
    ).innerHTML = html;


    previewArea.style.display = "block";


    setTimeout(function() {

      previewArea.scrollIntoView({
        behavior: "smooth",
        block: "start"
      });

    }, 50);

  };


  /*
   * 임시저장
   */

  window.saveDraft = function() {

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
        editor.innerHTML

    };


    try {

      localStorage.setItem(
        "donfree-writing-draft",
        JSON.stringify(data)
      );


      showStatus(
        "임시저장되었습니다."
      );

    } catch (error) {

      showStatus(
        "임시저장에 실패했습니다. 사진이 너무 많거나 용량이 큰 경우 발생할 수 있습니다."
      );

    }

  };


  /*
   * 임시저장 불러오기
   */

  function loadDraft() {

    const saved =
      localStorage.getItem(
        "donfree-writing-draft"
      );


    if (!saved) {
      return;
    }


    try {

      const data =
        JSON.parse(saved);


      document.getElementById(
        "postTitle"
      ).value =
        data.title || "";


      document.getElementById(
        "postSlug"
      ).value =
        data.slug || "";


      document.getElementById(
        "postCategory"
      ).value =
        data.category || "";


      document.getElementById(
        "postTags"
      ).value =
        data.tags || "";


      document.getElementById(
        "seoTitle"
      ).value =
        data.seoTitle || "";


      document.getElementById(
        "seoDescription"
      ).value =
        data.seoDescription || "";


      editor.innerHTML =
        cleanHTML(data.body || "");

    } catch (error) {

      console.error(error);

    }

  }


  /*
   * 날짜
   */

  function getLocalDate() {

    const now = new Date();

    const year =
      now.getFullYear();

    const month =
      String(
        now.getMonth() + 1
      ).padStart(2, "0");

    const day =
      String(
        now.getDate()
      ).padStart(2, "0");

    return (
      year +
      "-" +
      month +
      "-" +
      day
    );

  }


  /*
   * YAML 문자열 처리
   */

  function yamlString(value) {

    return String(value || "")
      .replace(/\\/g, "\\\\")
      .replace(/"/g, '\\"')
      .replace(/\n/g, " ");

  }


  /*
   * HTML → Markdown
   */

  function htmlToMarkdown(html) {

    const parser =
      new DOMParser();

    const doc =
      parser.parseFromString(
        html,
        "text/html"
      );


    function convert(node) {

      if (node.nodeType === Node.TEXT_NODE) {

        return node.nodeValue
          .replace(/\u00a0/g, " ");

      }


      if (node.nodeType !== Node.ELEMENT_NODE) {

        return "";

      }


      const tag =
        node.tagName.toLowerCase();


      let content = "";

      node.childNodes.forEach(function(child) {

        content += convert(child);

      });


      if (tag === "br") {

        return "\n";

      }


      if (
        tag === "strong" ||
        tag === "b"
      ) {

        return "**" +
          content +
          "**";

      }


      if (tag === "em" || tag === "i") {

        return "*" +
          content +
          "*";

      }


      if (tag === "h2") {

        return "\n\n## " +
          content.trim() +
          "\n\n";

      }


      if (tag === "h3") {

        return "\n\n### " +
          content.trim() +
          "\n\n";

      }


      if (tag === "a") {

        const href =
          node.getAttribute("href") || "";

        if (
          !/^https?:\/\//i.test(href)
        ) {

          return content;

        }

        return "[" +
          content +
          "](" +
          href +
          ")";

      }


      if (tag === "img") {

        const src =
          node.getAttribute("src") || "";

        const alt =
          node.getAttribute("alt") || "이미지";

        return (
          '\n\n<img src="' +
          src +
          '" alt="' +
          alt.replace(/"/g, "&quot;") +
          '">\n\n'
        );

      }


      if (tag === "li") {

        return (
          "- " +
          content.trim() +
          "\n"
        );

      }


      if (
        tag === "p" ||
        tag === "div"
      ) {

        return (
          content.trimEnd() +
          "\n\n"
        );

      }


      if (
        tag === "ul" ||
        tag === "ol"
      ) {

        return (
          content +
          "\n"
        );

      }


      return content;

    }


    return convert(doc.body)
      .replace(/\n{3,}/g, "\n\n")
      .trim();

  }


  /*
   * 글 파일 만들기
   */

  window.downloadPost = function() {

    const title =
      document.getElementById(
        "postTitle"
      ).value.trim();


    const slug =
      document.getElementById(
        "postSlug"
      ).value.trim();


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


    const category =
      document.getElementById(
        "postCategory"
      ).value.trim();


    const tags =
      document.getElementById(
        "postTags"
      ).value
        .split(",")
        .map(function(tag) {
          return tag.trim();
        })
        .filter(Boolean);


    const seoTitle =
      document.getElementById(
        "seoTitle"
      ).value.trim();


    const seoDescription =
      document.getElementById(
        "seoDescription"
      ).value.trim();


    const markdown =
      htmlToMarkdown(
        cleanHTML(
          editor.innerHTML
        )
      );


    const frontMatter =
`---
title: "${yamlString(title)}"
date: ${getLocalDate()} 00:00:00 +0900
categories:
  - "${yamlString(category)}"
tags:
${tags.map(function(tag) {
  return '  - "' + yamlString(tag) + '"';
}).join("\n")}
description: "${yamlString(seoDescription)}"
seo_title: "${yamlString(seoTitle)}"
permalink: /posts/${slug}/
---

${markdown}
`;


    const blob =
      new Blob(
        [frontMatter],
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
      getLocalDate() +
      "-" +
      slug +
      ".md";


    document.body.appendChild(a);

    a.click();

    a.remove();


    URL.revokeObjectURL(url);


    showStatus(
      "글 파일이 만들어졌습니다."
    );

  };


  /*
   * 전체 지우기
   */

  window.clearEditor = function() {

    if (
      !confirm(
        "작성한 내용을 모두 삭제할까요?"
      )
    ) {

      return;

    }


    document.getElementById(
      "postTitle"
    ).value = "";


    document.getElementById(
      "postSlug"
    ).value = "";


    document.getElementById(
      "postCategory"
    ).value = "";


    document.getElementById(
      "postTags"
    ).value = "";


    document.getElementById(
      "seoTitle"
    ).value = "";


    document.getElementById(
      "seoDescription"
    ).value = "";


    editor.innerHTML = "";


    previewArea.style.display =
      "none";


    localStorage.removeItem(
      "donfree-writing-draft"
    );


    showStatus(
      "작성 내용이 삭제되었습니다."
    );

  };


  /*
   * 상태 메시지
   */

  function showStatus(message) {

    const status =
      document.getElementById(
        "statusMessage"
      );


    status.textContent =
      message;


    setTimeout(function() {

      status.textContent = "";

    }, 3000);

  }


  /*
   * 페이지 처음 열 때 임시저장 불러오기
   */

  loadDraft();

})();

</script>
