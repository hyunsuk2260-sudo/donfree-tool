---
title: PDF 통합 및 변환 툴
icon: fas fa-file-pdf
order: 8
layout: page
permalink: /pdf-tool/
---

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 25px; border: 1px solid #e9ecef;">
    <h4 style="margin-top: 0; color: #dc3545;">📄 무료 온라인 브라우저 직행 이미지 PDF 변환 툴</h4>
    <p style="margin-bottom: 0;">이미지 합치기와 PDF 다운로드는 **여기서 곧바로** 해결하세요!</p>
</div>

<div style="margin-bottom: 30px; padding: 25px; background-color: #ffffff; border: 2px solid #dc3545; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 style="margin-top: 0; color: #dc3545;">1. 이미지 파일(JPG/PNG)을 PDF로 바로 변환·다운로드</h3>
    <p style="color: #6c757d; line-height: 1.6;">변환할 이미지들을 선택한 뒤 버튼을 누르면 5초간 준비 로딩 후 즉시 PDF로 합쳐져 다운로드됩니다.</p>
    
    <div style="margin: 15px 0;">
        <input type="file" id="img-input" multiple accept="image/*" style="padding: 10px; border: 1px dashed #ccc; border-radius: 6px; width: 100%; box-sizing: border-box; cursor: pointer;">
    </div>
    
    <button type="button" id="convert-btn" onclick="window.doPdfConvert()" style="padding: 12px 25px; background-color:#dc3545; color:white; border:none; border-radius:6px; font-weight:bold; cursor:pointer; font-size: 1em; box-shadow: 0 2px 4px rgba(0,0,0,0.2); width: 100%;">5초 로딩 후 PDF 변환·다운로드 ⬇️</button>
    
    <div id="pdf-status" style="display:none; margin-top:15px; color:#155724; font-weight:bold; padding:12px; background-color:#d4edda; border:1px solid #c3e6cb; border-radius:6px; text-align: center;">
        <span id="status-text">준비 중...</span>
    </div>
</div>

<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
</div>

<div style="margin-bottom: 25px; padding: 25px; background-color: #ffffff; border: 2px solid #6c757d; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 style="margin-top: 0; color: #495057;">2. 세부 수정·압축·분할 등 추가 작업이 필요하다면?</h3>
    <p style="color: #6c757d; line-height: 1.6;">PDF 병합·변환은 위에서 끝내시고, 글자 수정·페이지 분할·초대형 용량 압축 같은 <b>추가 작업</b>이 필요할 때만 아래 전문 사이트를 참고용으로 이용하세요.</p>
    <a href="https://www.ilovepdf.com/ko" target="_blank" style="display:inline-block; padding:12px 25px; background-color:#495057; color:white; text-decoration:none; border-radius:6px; font-weight:bold; box-shadow: 0 2px 4px rgba(0,0,0,0.2);">추가 편집/압축 툴(iLovePDF) 열기 ↗</a>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

<script>
window.doPdfConvert = async function() {
    var fileInput = document.getElementById("img-input");
    var statusBox = document.getElementById("pdf-status");
    var statusText = document.getElementById("status-text");
    var btn = document.getElementById("convert-btn");

    if (!fileInput || !fileInput.files || fileInput.files.length === 0) {
        alert("변환할 이미지 파일(JPG, PNG 등)을 선택해 주세요!");
        return;
    }

    if (btn.disabled) return;
    btn.disabled = true;
    btn.style.opacity = '0.5';

    statusBox.style.display = 'block';
    statusBox.style.backgroundColor = '#d4edda';
    statusBox.style.color = '#155724';

    // 5초 카운트다운 로딩 연출
    for (let i = 5; i > 0; i--) {
        statusText.innerText = "⏳ PDF 변환 준비 중... " + i + "초 뒤 생성이 시작됩니다!";
        await new Promise(r => setTimeout(r, 1000));
    }

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
    } finally {
        btn.disabled = false;
        btn.style.opacity = '1';
    }
};

try { if (window.adsbygoogle) { (adsbygoogle = window.adsbygoogle || []).push({}); } } catch(e) {}
</script>
