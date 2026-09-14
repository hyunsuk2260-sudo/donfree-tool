---
title: PDF 통합 및 변환 툴
icon: fas fa-file-pdf
order: 8
layout: page
permalink: /pdf-tool/
---

<!-- 상단 설명 영역 -->
<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 25px; border: 1px solid #e9ecef;">
    <h4 style="margin-top: 0; color: #dc3545;">📄 무료 온라인 PDF & 이미지 변환 툴</h4>
    <p style="margin-bottom: 0;">프로그램 설치 없이, 브라우저에서 안전하게 여러 장의 이미지를 PDF로 합치거나 PDF를 이미지로 변환할 수 있습니다.</p>
</div>

<!-- 1. 이미지 -> PDF 변환기 미니 툴 -->
<div style="margin-bottom: 30px; padding: 25px; background-color: #ffffff; border: 2px solid #dc3545; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 style="margin-top: 0; color: #dc3545;">1. 이미지 파일(JPG/PNG)을 PDF로 합치기</h3>
    <p style="color: #6c757d; line-height: 1.6;">여러 장의 사진이나 스캔본을 선택하면 하나의 PDF 파일로 깔끔하게 묶어줍니다.</p>
    
    <div style="margin: 15px 0;">
        <input type="file" id="img-input" multiple accept="image/*" style="padding: 10px; border: 1px dashed #ccc; border-radius: 6px; width: 100%; box-sizing: border-box; cursor: pointer;">
    </div>
    
    <button type="button" id="convert-btn" style="padding: 12px 25px; background-color:#dc3545; color:white; border:none; border-radius:6px; font-weight:bold; cursor:pointer; font-size: 1em; box-shadow: 0 2px 4px rgba(0,0,0,0.2); width: 100%;">PDF 변환 및 다운로드 ↗</button>
    
    <div id="pdf-timer" style="display:none; margin-top:15px; color:#dc3545; font-weight:bold; padding:10px; background-color:#f8d7da; border-radius:6px; text-align: center;">
        파일을 변환 준비 중입니다... <span id="pdf-count" style="font-size: 1.2em;">5</span>초 후 완료됩니다.
    </div>
</div>

<!-- 구글 애드센스 광고 영역 (사용자가 파일 고르고 대기하는 동안 광고 노출 극대화!) -->
<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
</div>

<!-- 외부 전문 무료 툴 안전 링크 섹션 (보완용) -->
<div style="margin-bottom: 25px; padding: 25px; background-color: #ffffff; border: 2px solid #6c757d; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 style="margin-top: 0; color: #495057;">2. 전문 PDF 편집·분할·압축 사이트 바로가기</h3>
    <p style="color: #6c757d; line-height: 1.6;">용량이 너무 큰 PDF를 압축하거나 특정 페이지만 잘라내고 싶을 때 사용하는 글로벌 무료 웹사이트입니다.</p>
    <a href="https://www.ilovepdf.com/ko" target="_blank" style="display:inline-block; padding:12px 25px; background-color:#495057; color:white; text-decoration:none; border-radius:6px; font-weight:bold; box-shadow: 0 2px 4px rgba(0,0,0,0.2);">iLovePDF 열기 ↗</a>
</div>

<!-- PDF 변환용 라이브러리(jsPDF) CDN 로드 -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

<script>
document.addEventListener("DOMContentLoaded", function() {
    var convertBtn = document.getElementById("convert-btn");
    var imgInput = document.getElementById("img-input");
    var timerBox = document.getElementById("pdf-timer");
    var countSpan = document.getElementById("pdf-count");

    convertBtn.addEventListener("click", function() {
        if (imgInput.files.length === 0) {
            alert("변환할 이미지 파일을 최소 1장 이상 선택해 주세요!");
            return;
        }

        convertBtn.disabled = true;
        convertBtn.style.opacity = '0.5';
        convertBtn.style.cursor = 'not-allowed';
        timerBox.style.display = 'block';

        var timeLeft = 5;
        countSpan.innerText = timeLeft;

        var countdown = setInterval(function() {
            timeLeft--;
            countSpan.innerText = timeLeft;

            if (timeLeft <= 0) {
                clearInterval(countdown);
                timerBox.innerHTML = '✨ 변환 완료! PDF 파일 저장을 시작합니다.';

                // 실제 이미지들을 PDF로 묶어서 다운로드 실행하는 로직
                generatePDFFromImages(imgInput.files);

                setTimeout(function() {
                    convertBtn.disabled = false;
                    convertBtn.style.opacity = '1';
                    convertBtn.style.cursor = 'pointer';
                    timerBox.style.display = 'none';
                    timerBox.innerHTML = '파일을 변환 준비 중입니다... <span id="pdf-count" style="font-size: 1.2em;">5</span>초 후 완료됩니다.';
                }, 2000);
            }
        }, 1000);
    });

    async function generatePDFFromImages(files) {
        const { jsPDF } = window.jspdf;
        const doc = new jsPDF();

        for (let i = 0; i < files.length; i++) {
            let file = files[i];
            let imageUrl = await readFileAsDataURL(file);
            
            if (i > 0) {
                doc.addPage();
            }

            // 이미지 비율 유지하며 PDF 페이지에 맞추기
            let imgProps = doc.getImageProperties(imageUrl);
            let pdfWidth = doc.internal.pageSize.getWidth();
            let pdfHeight = (imgProps.height * pdfWidth) / imgProps.width;

            doc.addImage(imageUrl, 'JPEG', 0, 10, pdfWidth, pdfHeight);
        }

        doc.save("converted_document.pdf");
    }

    function readFileAsDataURL(file) {
        return new Promise((resolve, reject) => {
            let reader = new FileReader();
            reader.onload = () => resolve(reader.result);
            reader.onerror = reject;
            reader.readAsDataURL(file);
        });
    }
});
</script>
