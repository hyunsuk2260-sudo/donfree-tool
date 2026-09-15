---
title: PDF 통합 및 변환 툴
icon: fas fa-file-pdf
order: 8
layout: page
permalink: /pdf-tool/
---

{% raw %}
<!-- 상단 설명 영역 -->
<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 25px; border: 1px solid #e9ecef;">
    <h4 style="margin-top: 0; color: #dc3545;">📄 무료 온라인 브라우저 직행 이미지 PDF 변환 툴</h4>
    <p style="margin-bottom: 0;">외부 사이트로 이동할 필요 없이, 브라우저 안에서 이미지를 합쳐 즉시 PDF로 다운로드합니다.</p>
</div>

<!-- 1. 이미지 -> PDF 변환기 미니 툴 -->
<div style="margin-bottom: 30px; padding: 25px; background-color: #ffffff; border: 2px solid #dc3545; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 style="margin-top: 0; color: #dc3545;">1. 이미지 파일(JPG/PNG)을 PDF로 바로 변환·다운로드</h3>
    <p style="color: #6c757d; line-height: 1.6;">변환할 이미지들을 선택한 뒤 버튼을 누르면 즉시 PDF로 합쳐져 다운로드됩니다.</p>
    
    <div style="margin: 15px 0;">
        <input type="file" id="img-input" multiple accept="image/*" style="padding: 10px; border: 1px dashed #ccc; border-radius: 6px; width: 100%; box-sizing: border-box; cursor: pointer;">
    </div>
    
    <button type="button" id="convert-btn" onclick="convertImagesToPdfDirect()" style="padding: 12px 25px; background-color:#dc3545; color:white; border:none; border-radius:6px; font-weight:bold; cursor:pointer; font-size: 1em; box-shadow: 0 2px 4px rgba(0,0,0,0.2); width: 100%;">지금 바로 PDF 변환 및 다운로드 ⬇️</button>
    
    <div id="pdf-status" style="display:none; margin-top:15px; color:#155724; font-weight:bold; padding:12px; background-color:#d4edda; border:1px solid #c3e6cb; border-radius:6px; text-align: center;">
        <span id="status-text">PDF 생성 중입니다... 잠시만 기다려주세요!</span>
    </div>
</div>
{% endraw %}

<!-- 구글 애드센스 광고 영역 -->
<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
</div>

{% raw %}
<!-- 외부 전문 무료 툴 안전 링크 섹션 -->
<div style="margin-bottom: 25px; padding: 25px; background-color: #ffffff; border: 2px solid #6c757d; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 style="margin-top: 0; color: #495057;">2. 초대형 PDF 압축·분할이 필요할 때</h3>
    <p style="color: #6c757d; line-height: 1.6;">브라우저 용량을 넘어서는 수십 MB 대용량 문서 처리가 필요할 때 참고용 링크입니다.</p>
    <a href="https://www.ilovepdf.com/ko" target="_blank" style="display:inline-block; padding:12px 25px; background-color:#495057; color:white; text-decoration:none; border-radius:6px; font-weight:bold; box-shadow: 0 2px 4px rgba(0,0,0,0.2);">iLovePDF 참고하기 ↗</a>
</div>

<!-- jsPDF 라이브러리 CDN 로드 -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

<script>
window.convertImagesToPdfDirect = async function() {
    var fileInput = document.getElementById("img-input");
    var statusBox = document.getElementById("pdf-status");
    var statusText = document.getElementById("status-text");

    if (!fileInput || !fileInput.files || fileInput.files.length === 0) {
        alert("변환할 이미지 파일(JPG, PNG 등)을 선택해 주세요!");
        return;
    }

    statusBox.style.display = 'block';
    statusBox.style.backgroundColor = '#d4edda';
    statusBox.style.color = '#155724';
    statusText.innerText = "이미지 처리 및 PDF 조립 중 (" + fileInput.files.length + "개 파일)...";

    try {
        const { jsPDF } = window.jspdf;
        const pdf = new jsPDF({
            orientation: 'portrait',
            unit: 'mm',
            format: 'a4'
        });

        const files = Array.from(fileInput.files);

        for (let i = 0; i < files.length; i++) {
            const file = files[i];
            const dataUrl = await readFileAsDataURL(file);
            const imgProps = await getImageDimensions(dataUrl);

            // A4 비율 맞추기 (가로 210mm 기준)
            const pdfWidth = 210;
            const pdfHeight = (imgProps.height * pdfWidth) / imgProps.width;

            if (i > 0) {
                pdf.addPage();
            }

            // 페이지 높이가 A4(297mm)를 넘어가면 첫 페이지 안에 맞추거나 비율 스케일링
            const targetHeight = Math.min(297, pdfHeight);
            const targetWidth = (targetHeight * imgProps.width) / imgProps.height;
            const xOffset = (210 - targetWidth) / 2;

            pdf.addImage(dataUrl, 'JPEG', xOffset > 0 ? xOffset : 0, 0, targetWidth > 210 ? 210 : targetWidth, targetHeight);
        }

        pdf.save('donfree-converted.pdf');

        statusText.innerText = "✨ PDF 변환 및 다운로드 완료!";
        statusBox.style.backgroundColor = '#cce5ff';
        statusBox.style.color = '#004085';

    } catch (err) {
        console.error(err);
        statusBox.style.backgroundColor = '#f8d7da';
        statusBox.style.color = '#721c24';
        statusText.innerText = "변환 중 오류가 발생했습니다. 이미지 형식을 확인해 주세요.";
    }
};

function readFileAsDataURL(file) {
    return new Promise((resolve, reject) => {
        const reader = new FileReader();
        reader.onload = e => resolve(e.target.result);
        reader.reject = reject;
        reader.readAsDataURL(file);
    });
}

function getImageDimensions(dataUrl) {
    return new Promise((resolve, reject) => {
        const img = new Image();
        img.onload = () => resolve({ width: img.width, height: img.height });
        img.onerror = reject;
        img.src = dataUrl;
    });
}
</script>
{% endraw %}
