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

.donfree-editor h1 {
    margin-bottom: 8px;
}

.editor-description {
    color: #777;
    margin-bottom: 25px;
}

.editor-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 15px;
    margin-bottom: 15px;
}

.editor-box {
    margin-bottom: 18px;
}

.editor-box label {
    display: block;
    font-weight: 700;
    margin-bottom: 7px;
}

.editor-input,
.editor-textarea,
.editor-select {
    width: 100%;
    box-sizing: border-box;
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 11px 13px;
    background: #fff;
    font-size: 15px;
}

.editor-textarea {
    min-height: 450px;
    resize: vertical;
    line-height: 1.7;
    font-family: inherit;
}

.editor-actions {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    margin: 20px 0;
}

.editor-btn {
    border: 0;
    border-radius: 8px;
    padding: 11px 18px;
    cursor: pointer;
    font-weight: 700;
    font-size: 14px;
}

.btn-preview {
    background: #111827;
    color: white;
}

.btn-save {
    background: #2563eb;
    color: white;
}

.btn-download {
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
    border-radius: 12px;
    background: white;
}

.preview-box.active {
    display: block;
}

.preview-title {
    font-size: 30px;
    font-weight: 800;
    margin-bottom: 20px;
}

.preview-content {
    line-height: 1.8;
}

.editor-status {
    font-size: 13px;
    color: #777;
    margin-top: 5px;
}

@media (max-width: 700px) {
    .editor-row {
        grid-template-columns: 1fr;
    }

    .editor-textarea {
        min-height: 350px;
    }

    .preview-title {
        font-size: 24px;
    }
}
</style>


<div class="donfree-editor">

    <h1>✍️ 돈프리 글쓰기</h1>

    <p class="editor-description">
        검색 유입용 콘텐츠를 작성하고 미리보기할 수 있습니다.
    </p>


    <!-- 제목 / URL -->
    <div class="editor-row">

        <div class="editor-box">
            <label for="post-title">글 제목</label>

            <input
                id="post-title"
                class="editor-input"
                type="text"
                placeholder="예: 인스타 릴스 다운로드 방법, 앱 없이 저장하는 법"
            >
        </div>


        <div class="editor-box">
            <label for="post-slug">URL 슬러그</label>

            <input
                id="post-slug"
                class="editor-input"
                type="text"
                placeholder="instagram-reels-download"
            >
        </div>

    </div>


    <!-- 카테고리 / 태그 -->
    <div class="editor-row">

        <div class="editor-box">

            <label for="post-category">
                카테고리
            </label>

            <select
                id="post-category"
                class="editor-select">

                <option value="생활정보">
                    생활정보
                </option>

                <option value="영상">
                    영상
                </option>

                <option value="폰트">
                    폰트
                </option>

                <option value="PDF">
                    PDF
                </option>

                <option value="특수문자">
                    특수문자
                </option>

                <option value="사주">
                    사주
                </option>

                <option value="기타">
                    기타
                </option>

            </select>

        </div>


        <div class="editor-box">

            <label for="post-tags">
                태그
            </label>

            <input
                id="post-tags"
                class="editor-input"
                type="text"
                placeholder="인스타, 릴스, 다운로드"
            >

        </div>

    </div>


    <!-- SEO -->
    <div class="editor-row">

        <div class="editor-box">

            <label for="seo-title">
                SEO 제목
            </label>

            <input
                id="seo-title"
                class="editor-input"
                type="text"
                placeholder="검색 결과에 표시될 제목"
            >

        </div>


        <div class="editor-box">

            <label for="seo-description">
                SEO 설명
            </label>

            <input
                id="seo-description"
                class="editor-input"
                type="text"
                placeholder="검색 결과에 표시될 설명"
            >

        </div>

    </div>


    <!-- 본문 -->
    <div class="editor-box">

        <label for="post-content">
            본문
        </label>

        <textarea
            id="post-content"
            class="editor-textarea"
            placeholder="여기에 글을 작성하세요.

예시:

인스타 릴스를 저장하고 싶은데
앱을 설치해야 할까요?

사실 간단한 방법이 있습니다.

...

### 인스타 릴스 다운로드 방법

1. 저장하고 싶은 릴스의 링크를 복사합니다.
2. 돈프리 비디오 다운로더를 엽니다.
3. 링크를 입력합니다.
4. 다운로드 버튼을 누릅니다.

[돈프리 비디오 다운로더 바로가기](/video/)
"></textarea>

        <div class="editor-status">
            작성한 내용은 현재 브라우저에 임시 저장할 수 있습니다.
        </div>

    </div>


    <!-- 버튼 -->
    <div class="editor-actions">

        <button
            type="button"
            class="editor-btn btn-preview"
            onclick="donfreePreview()">
            👁 미리보기
        </button>


        <button
            type="button"
            class="editor-btn btn-save"
            onclick="donfreeSave()">
            💾 임시저장
        </button>


        <button
            type="button"
            class="editor-btn btn-download"
            onclick="donfreeDownload()">
            📥 글 파일 만들기
        </button>


        <button
            type="button"
            class="editor-btn btn-clear"
            onclick="donfreeClear()">
            🗑 초기화
        </button>

    </div>


    <!-- 미리보기 -->
    <div
        id="donfree-preview"
        class="preview-box">

        <div
            id="preview-title"
            class="preview-title">
        </div>

        <div
            id="preview-content"
            class="preview-content">
        </div>

    </div>

</div>


<script>

(function () {

    const titleInput =
        document.getElementById('post-title');

    const slugInput =
        document.getElementById('post-slug');

    const categoryInput =
        document.getElementById('post-category');

    const tagsInput =
        document.getElementById('post-tags');

    const seoTitleInput =
        document.getElementById('seo-title');

    const seoDescriptionInput =
        document.getElementById('seo-description');

    const contentInput =
        document.getElementById('post-content');


    /*
     * 제목을 입력하면 URL 슬러그 자동 생성
     */
    titleInput.addEventListener('input', function () {

        if (slugInput.value.trim() !== '') {
            return;
        }

        let slug = this.value
            .toLowerCase()
            .trim()
            .replace(/[^\w가-힣\s-]/g, '')
            .replace(/\s+/g, '-');

        slugInput.value = slug;

    });


    /*
     * 임시저장
     */
    window.donfreeSave = function () {

        const data = {

            title: titleInput.value,

            slug: slugInput.value,

            category: categoryInput.value,

            tags: tagsInput.value,

            seoTitle: seoTitleInput.value,

            seoDescription: seoDescriptionInput.value,

            content: contentInput.value

        };


        localStorage.setItem(
            'donfree-writing-draft',
            JSON.stringify(data)
        );


        alert('임시저장했습니다.');

    };


    /*
     * 저장된 글 불러오기
     */
    const saved =
        localStorage.getItem(
            'donfree-writing-draft'
        );


    if (saved) {

        try {

            const data =
                JSON.parse(saved);

            titleInput.value =
                data.title || '';

            slugInput.value =
                data.slug || '';

            categoryInput.value =
                data.category || '생활정보';

            tagsInput.value =
                data.tags || '';

            seoTitleInput.value =
                data.seoTitle || '';

            seoDescriptionInput.value =
                data.seoDescription || '';

            contentInput.value =
                data.content || '';

        } catch (e) {

            console.error(e);

        }

    }


    /*
     * 간단한 Markdown → HTML 변환
     */
    function markdownToHtml(text) {

        let html =
            text
            .replace(/&/g, '&amp;')
            .replace(/</g, '&lt;')
            .replace(/>/g, '&gt;');


        html = html.replace(
            /^### (.*)$/gm,
            '<h3>$1</h3>'
        );

        html = html.replace(
            /^## (.*)$/gm,
            '<h2>$1</h2>'
        );

        html = html.replace(
            /^# (.*)$/gm,
            '<h1>$1</h1>'
        );

        html = html.replace(
            /\*\*(.*?)\*\*/g,
            '<strong>$1</strong>'
        );

        html = html.replace(
            /\[(.*?)\]\((.*?)\)/g,
            '<a href="$2">$1</a>'
        );

        html = html.replace(
            /\n/g,
            '<br>'
        );

        return html;

    }


    /*
     * 미리보기
     */
    window.donfreePreview = function () {

        const preview =
            document.getElementById(
                'donfree-preview'
            );

        document.getElementById(
            'preview-title'
        ).textContent =
            titleInput.value ||
            '제목을 입력해주세요.';


        document.getElementById(
            'preview-content'
        ).innerHTML =
            markdownToHtml(
                contentInput.value
            );


        preview.classList.add('active');

        preview.scrollIntoView({
            behavior: 'smooth'
        });

    };


    /*
     * Markdown 파일 생성
     */
    window.donfreeDownload = function () {

        const title =
            titleInput.value.trim();

        const slug =
            slugInput.value.trim();

        const category =
            categoryInput.value;

        const tags =
            tagsInput.value
                .split(',')
                .map(function (tag) {
                    return tag.trim();
                })
                .filter(Boolean);


        const seoTitle =
            seoTitleInput.value.trim();

        const seoDescription =
            seoDescriptionInput.value.trim();

        const content =
            contentInput.value;


        if (!title) {

            alert(
                '글 제목을 입력해주세요.'
            );

            titleInput.focus();

            return;

        }


        if (!content.trim()) {

            alert(
                '본문을 입력해주세요.'
            );

            contentInput.focus();

            return;

        }


        const now =
            new Date();


        const yyyy =
            now.getFullYear();

        const mm =
            String(
                now.getMonth() + 1
            ).padStart(2, '0');

        const dd =
            String(
                now.getDate()
            ).padStart(2, '0');


        const date =
            yyyy +
            '-' +
            mm +
            '-' +
            dd;


        const safeSlug =
            slug ||
            'donfree-post';


        let frontMatter =
`---
layout: post
title: "${title.replace(/"/g, '\\"')}"
date: ${date} 12:00:00 +0900
categories: [${category}]
tags: [${tags.join(', ')}]
description: "${seoDescription.replace(/"/g, '\\"')}"
`;


        if (seoTitle) {

            frontMatter +=
`seo_title: "${seoTitle.replace(/"/g, '\\"')}"
`;

        }


        frontMatter +=
`permalink: /posts/${safeSlug}/
---

${content}
`;


        const fileName =
            date +
            '-' +
            safeSlug +
            '.md';


        const blob =
            new Blob(
                [frontMatter],
                {
                    type:
                        'text/markdown;charset=utf-8'
                }
            );


        const url =
            URL.createObjectURL(blob);


        const link =
            document.createElement('a');

        link.href = url;

        link.download =
            fileName;

        document.body.appendChild(link);

        link.click();

        link.remove();

        URL.revokeObjectURL(url);


        alert(
            '글 파일을 만들었습니다.\\n\\n' +
            fileName +
            '\\n\\n' +
            '이 파일을 GitHub의 _posts 폴더에 올리면 게시됩니다.'
        );

    };


    /*
     * 초기화
     */
    window.donfreeClear = function () {

        if (
            !confirm(
                '작성 중인 내용을 모두 삭제할까요?'
            )
        ) {
            return;
        }


        titleInput.value = '';

        slugInput.value = '';

        categoryInput.value =
            '생활정보';

        tagsInput.value = '';

        seoTitleInput.value = '';

        seoDescriptionInput.value = '';

        contentInput.value = '';


        localStorage.removeItem(
            'donfree-writing-draft'
        );


        document
            .getElementById(
                'donfree-preview'
            )
            .classList.remove('active');

    };


})();

</script>
