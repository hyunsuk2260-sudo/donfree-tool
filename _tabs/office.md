---
title: 무료 오피스 다운로드
icon: fas fa-file-excel
order: 7
layout: page
permalink: /office/
---

<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 25px; border: 1px solid #e9ecef;">
    <h4 style="margin-top: 0; color: #007bff;">💻 정품 인증 걱정 없는 무료 오피스 모음</h4>
    <p style="margin-bottom: 0;">엑셀, 워드, 파워포인트 파일을 비용 부담 없이 안전하게 열고 편집할 수 있는 합법적인 무료 프로그램 공식 다운로드 링크입니다.</p>
</div>

<!-- 1. LibreOffice -->
<div style="margin-bottom: 25px; padding: 25px; background-color: #ffffff; border: 2px solid #007bff; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 style="margin-top: 0; color: #007bff;">1. 리브레오피스 (LibreOffice) - 추천 ⭐</h3>
    <p style="color: #6c757d; line-height: 1.6;">마이크로소프트 오피스와 완벽하게 호환되는 전 세계에서 가장 유명한 오픈소스 무료 오피스 프로그램입니다.</p>
    
    <button type="button" class="dl-btn" data-url="https://ko.libreoffice.org/download/download/" style="padding: 12px 25px; background-color:#007bff; color:white; border:none; border-radius:6px; font-weight:bold; cursor:pointer; font-size: 1em; box-shadow: 0 2px 4px rgba(0,0,0,0.2);">다운로드 바로가기 ↗</button>
    
    <div class="timer-box" style="display:none; margin-top:15px; color:#dc3545; font-weight:bold; padding:10px; background-color:#f8d7da; border-radius:6px;">
        안전한 연결을 준비 중입니다... <span class="count-num" style="font-size: 1.2em;">5</span>초 후 이동합니다.
    </div>
</div>

<!-- 2. Microsoft Excel for the Web -->
<div style="margin-bottom: 25px; padding: 25px; background-color: #ffffff; border: 2px solid #28a745; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 style="margin-top: 0; color: #28a745;">2. 웹용 마이크로소프트 엑셀 (Excel for the Web)</h3>
    <p style="color: #6c757d; line-height: 1.6;">설치 없이 웹브라우저에서 마이크로소프트 정품 엑셀을 무료로 바로 사용할 수 있습니다.</p>
    
    <button type="button" class="dl-btn" data-url="https://www.microsoft.com/ko-kr/microsoft-365/free-office-online-for-the-web" style="padding: 12px 25px; background-color:#28a745; color:white; border:none; border-radius:6px; font-weight:bold; cursor:pointer; font-size: 1em; box-shadow: 0 2px 4px rgba(0,0,0,0.2);">다운로드 바로가기 ↗</button>
    
    <div class="timer-box" style="display:none; margin-top:15px; color:#dc3545; font-weight:bold; padding:10px; background-color:#f8d7da; border-radius:6px;">
        안전한 연결을 준비 중입니다... <span class="count-num" style="font-size: 1.2em;">5</span>초 후 이동합니다.
    </div>
</div>

<!-- 3. Hancom Office Viewer -->
<div style="margin-bottom: 25px; padding: 25px; background-color: #ffffff; border: 2px solid #ffc107; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05);">
    <h3 style="margin-top: 0; color: #d39e00;">3. 한컴오피스 뷰어 (Hancom Viewer)</h3>
    <p style="color: #6c757d; line-height: 1.6;">한글(HWP)뿐만 아니라 MS 엑셀, 워드, 파워포인트 문서까지 깔끔하게 열람할 수 있는 공식 무료 뷰어입니다.</p>
    
    <button type="button" class="dl-btn" data-url="https://www.hancom.com/cs/csDownload.do" style="padding: 12px 25px; background-color:#ffc107; color:#333; border:none; border-radius:6px; font-weight:bold; cursor:pointer; font-size: 1em; box-shadow: 0 2px 4px rgba(0,0,0,0.2);">다운로드 바로가기 ↗</button>
    
    <div class="timer-box" style="display:none; margin-top:15px; color:#dc3545; font-weight:bold; padding:10px; background-color:#f8d7da; border-radius:6px;">
        안전한 연결을 준비 중입니다... <span class="count-num" style="font-size: 1.2em;">5</span>초 후 이동합니다.
    </div>
</div>

<!-- 구글 애드센스 광고 영역 -->
<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
</div>

<script>
document.addEventListener("DOMContentLoaded", function() {
    var buttons = document.querySelectorAll(".dl-btn");
    
    buttons.forEach(function(btn) {
        btn.addEventListener("click", function() {
            var container = this.parentElement;
            var timerBox = container.querySelector(".timer-box");
            var countSpan = container.querySelector(".count-num");
            var targetUrl = this.getAttribute("data-url");
            
            if (btn.disabled) return;
            
            btn.disabled = true;
            btn.style.opacity = '0.5';
            btn.style.cursor = 'not-allowed';
            timerBox.style.display = 'block';
            
            var timeLeft = 5;
            countSpan.innerText = timeLeft;
            
            var countdown = setInterval(function() {
                timeLeft--;
                countSpan.innerText = timeLeft;
                
                if (timeLeft <= 0) {
                    clearInterval(countdown);
                    timerBox.innerHTML = '✨ 이동 준비 완료! 페이지가 열립니다.';
                    window.open(targetUrl, '_blank');
                    
                    setTimeout(function() {
                        btn.disabled = false;
                        btn.style.opacity = '1';
                        btn.style.cursor = 'pointer';
                        timerBox.style.display = 'none';
                        timerBox.innerHTML = '안전한 연결을 준비 중입니다... <span class="count-num" style="font-size: 1.2em;">5</span>초 후 이동합니다.';
                    }, 2000);
                }
            }, 1000);
        });
    });
});
</script>
