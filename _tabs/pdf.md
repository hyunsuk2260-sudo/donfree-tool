---
title: PDF 통합 및 변환 툴
icon: fas fa-file-pdf
order: 8
layout: page
permalink: /pdf-tool/
---

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 25px; border: 1px solid #e9ecef;">
    <h4 style="margin-top: 0; color: #dc3545;">📄 무료 온라인 브라우저 직행 이미지 PDF 변환 툴</h4>
    <p style="margin-bottom: 0;">외부 사이트로 이동할 필요 없이, 브라우저 안에서 이미지를 합쳐 즉시 PDF로 다운로드합니다.</p>
</div>

<div style="margin-bottom: 30px; padding: 25px; background-color: #ffffff; border: 2px solid #dc3545; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 style="margin-top: 0; color: #dc3545;">1. 이미지 파일(JPG/PNG)을 PDF로 바로 변환·다운로드</h3>
    <p style="color: #6c757d; line-height: 1.6;">변환할 이미지들을 선택한 뒤 버튼을 누르면 즉시 PDF로 합쳐져 다운로드됩니다.</p>
    
    <div style="margin: 15px 0;">
        <input type="file" id="img-input" multiple accept="image/*" style="padding: 10px; border: 1px dashed #ccc; border-radius: 6px; width: 100%; box-sizing: border-box; cursor: pointer;">
    </div>
    
    <button type="button" id="convert-btn" onclick="window.doPdfConvert()" style="padding: 12px 25px; background-color:#dc3545; color:white; border:none; border-radius:6px; font-weight:bold; cursor:pointer; font-size: 1em; box-shadow: 0 2px 4px rgba(0,0,0,0.2); width: 100%;">지금 바로 PDF 변환 및 다운로드 ⬇️</button>
    
    <div id="pdf-status" style="display:none; margin-top:15px; color:#155724; font-weight:bold; padding:12px; background-color:#d4edda; border:1px solid #c3e6cb; border-radius:6px; text-align: center;">
        <span id="status-text">PDF 생성 중입니다... 잠시만 기다려주세요!</span>
    </div>
</div>

<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
</div>

<div style="margin-bottom: 25px; padding: 25px; background-color: #ffffff; border: 2px solid #6c757d; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 style="margin-top: 0; color: #495057;">2. 초대형 PDF 압축·분할이 필요할 때</h3>
    <p style="color: #6c757d; line-height: 1.6;">브라우저 용량을 넘어서는 수십 MB 대용량 문서 처리가 필요할 때 참고용 링크입니다.</p>
    <a href="https://www.ilovepdf.com/ko" target="_blank" style="display:inline-block; padding:12px 25px; background-color:#495057; color:white; text-decoration:none; border-radius:6px; font-weight:bold; box-shadow: 0 2px 4px rgba(0,0,0,0.2);">iLovePDF 참고하기 ↗</a>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

<script>
window.doPdfConvert = async function() {
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
        const pdf = new jsPDF({ orientation: 'portrait', unit: 'mm', format: 'a4' });
        const files = Array.from(fileInput.files);

        for (let i = 0; i < files.length; i++) {
            const dataUrl = await new Promise((res, rej) => {
                const r = new FileReader();
                r.onload = e => res(e.target.result);
                r.onerror = rej;
                r.readAsDataURL(files[i]);
            });
            const dims = await new Promise((res, rej) => {
                const img = new Image();
                img.onload = () => res({ w: img.width, h: img.height });
                img.onerror = rej;
                img.src = dataUrl;
            });

            if (i > 0) pdf.addPage();
            const targetH = Math.min(297, (dims.h * 210) / dims.w);
            const targetW = (targetH * dims.w) / dims.h;
            const xOff = Math.max(0, (210 - targetW) / 2);
            pdf.addImage(dataUrl, 'JPEG', xOff, 0, targetW > 210 ? 210 : targetW, targetH);
        }

        pdf.save('donfree-converted.pdf');
        statusText.innerText = "✨ PDF 변환 및 다운로드 완료!";
        statusBox.style.backgroundColor = '#cce5ff';
        statusBox.style.color = '#004085';
    } catch (e) {
        console.error(e);
        statusBox.style.backgroundColor = '#f8d7da';
        statusBox.style.color = '#721c24';
        statusText.innerText = "변환 중 오류가 발생했습니다.";
    }
};

try { if (window.adsbygoogle) { (adsbygoogle = window.adsbygoogle || []).push({}); } } catch(e) {}
</script>
