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
    <p style="margin-bottom: 0;">프로그램 설치 없이, 브라우저에서 안전하게 여러 장의 이미지를 PDF로 변환할 수 있습니다.</p>
</div>

<!-- 1. 이미지 -> PDF 변환기 미니 툴 -->
<div style="margin-bottom: 30px; padding: 25px; background-color: #ffffff; border: 2px solid #dc3545; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 style="margin-top: 0; color: #dc3545;">1. 이미지 파일(JPG/PNG)을 PDF로 변환하기</h3>
    <p style="color: #6c757d; line-height: 1.6;">변환할 이미지를 선택하신 후 아래 버튼을 누르시면 5초 후 전용 변환 페이지로 이동합니다.</p>
    
    <div style="margin: 15px 0;">
        <input type="file" id="img-input" multiple accept="image/*" style="padding: 10px; border: 1px dashed #ccc; border-radius: 6px; width: 100%; box-sizing: border-box; cursor: pointer;">
    </div>
    
    <!-- 버튼을 누르면 즉시 작동하는 인라인 함수 연결 -->
    <button type="button" id="convert-btn" onclick="window.runPdfTimer()" style="padding: 12px 25px; background-color:#dc3545; color:white; border:none; border-radius:6px; font-weight:bold; cursor:pointer; font-size: 1em; box-shadow: 0 2px 4px rgba(0,0,0,0.2); width: 100%;">PDF 변환 및 다운로드 ↗</button>
    
    <div id="pdf-timer" style="display:none; margin-top:15px; color:#dc3545; font-weight:bold; padding:10px; background-color:#f8d7da; border-radius:6px; text-align: center;">
        안전한 연결을 준비 중입니다... <span id="pdf-count" style="font-size: 1.2em;">5</span>초 후 이동합니다.
    </div>
</div>

<!-- 구글 애드센스 광고 영역 -->
<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
</div>

<!-- 외부 전문 무료 툴 안전 링크 섹션 -->
<div style="margin-bottom: 25px; padding: 25px; background-color: #ffffff; border: 2px solid #6c757d; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 style="margin-top: 0; color: #495057;">2. 전문 PDF 편집·분할·압축 사이트 바로가기</h3>
    <p style="color: #6c757d; line-height: 1.6;">용량이 큰 PDF를 압축하거나 편집할 때 사용하는 글로벌 무료 웹사이트입니다.</p>
    <a href="https://www.ilovepdf.com/ko" target="_blank" style="display:inline-block; padding:12px 25px; background-color:#495057; color:white; text-decoration:none; border-radius:6px; font-weight:bold; box-shadow: 0 2px 4px rgba(0,0,0,0.2);">iLovePDF 열기 ↗</a>
</div>

<script>
window.runPdfTimer = function() {
    var btn = document.getElementById("convert-btn");
    var timerBox = document.getElementById("pdf-timer");
    var countSpan = document.getElementById("pdf-count");

    if (!btn || btn.disabled) return;

    btn.disabled = true;
    btn.style.opacity = '0.5';
    btn.style.cursor = 'not-allowed';
    timerBox.style.display = 'block';

    var timeLeft = 5;
    if (countSpan) countSpan.innerText = timeLeft;

    var countdown = setInterval(function() {
        timeLeft--;
        if (countSpan) countSpan.innerText = timeLeft;

        if (timeLeft <= 0) {
            clearInterval(countdown);
            timerBox.innerHTML = '✨ 변환 준비 완료! 페이지가 열립니다.';
            
            // 새 창으로 변환 사이트 열기
            window.open('https://www.ilovepdf.com/ko/jpg_to_pdf', '_blank');

            setTimeout(function() {
                btn.disabled = false;
                btn.style.opacity = '1';
                btn.style.cursor = 'pointer';
                timerBox.style.display = 'none';
                // span 태그가 날아가지 않도록 안전하게 원복
                timerBox.innerHTML = '안전한 연결을 준비 중입니다... <span id="pdf-count" style="font-size: 1.2em;">5</span>초 후 이동합니다.';
                countSpan = document.getElementById("pdf-count");
            }, 2000);
        }
    }, 1000);
};
</script>
