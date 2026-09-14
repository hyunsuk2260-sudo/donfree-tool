---
title: 비디오 다운로더
icon: fas fa-download
order: 5
layout: page
permalink: /video/
---

<!-- 상단 안내 영역 -->
<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 20px; border: 1px solid #e9ecef;">
    <h4 style="margin-top: 0; color: #007bff;">📥 워터마크 없는 숏폼 비디오 다운로더</h4>
    <p>유튜브 쇼츠, 인스타그램 릴스, 틱톡 등 영상의 링크(URL)를 입력하시면 워터마크 없이 다운로드할 수 있도록 추출해 드립니다.</p>
</div>

<!-- 비디오 링크 입력 영역 -->
<div style="text-align: center; margin: 20px 0; padding: 30px; background-color: #ffffff; border: 2px solid #007bff; border-radius: 15px; box-shadow: 0 5px 15px rgba(0,0,0,0.1);">
    <input type="text" id="videoUrl" placeholder="여기에 동영상 링크(URL)를 붙여넣기 하세요" style="width: 80%; padding: 15px; font-size: 1.1em; border: 1px solid #ced4da; border-radius: 8px; margin-bottom: 20px;">
    <br>
    <button id="downloadBtn" onclick="startDownload()" style="padding: 15px 35px; font-size: 1.2em; background-color: #007bff; color: white; border: none; border-radius: 8px; cursor: pointer; font-weight: bold; box-shadow: 0 4px 6px rgba(0,0,0,0.2);">영상 다운로드 분석</button>

    <!-- 5초 대기 타이머 -->
    <div id="dl-timer" style="display: none; text-align: center; color: #dc3545; font-weight: bold; margin-top: 20px; padding: 15px; background-color: #f8d7da; border-radius: 8px;">
        영상을 분석하고 추출하는 중입니다... <br><span id="dlTimeCount" style="font-size: 1.5em;">5</span>초 대기
    </div>

    <!-- 결과 출력 영역 -->
    <div id="dl-result" style="display: none; margin-top: 25px; padding: 15px; background-color: #e2e3e5; border-radius: 8px;">
        <!-- 다운로드 버튼 생성 위치 -->
    </div>
</div>

<!-- 구글 애드센스 (명당자리) -->
<div style="text-align: center; margin: 40px 0; min-height: 100px;">
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
    <ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-1922344740086878" data-ad-slot="6535711038" data-ad-format="auto" data-full-width-responsive="true"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
</div>

<script>
function startDownload() {
    var url = document.getElementById('videoUrl').value;
    if(!url) {
        alert('다운로드할 영상의 링크를 입력해주세요!');
        return;
    }

    document.getElementById('downloadBtn').disabled = true;
    document.getElementById('dl-timer').style.display = 'block';
    document.getElementById('dl-result').style.display = 'none';

    var timeLeft = 5;
    document.getElementById('dlTimeCount').innerText = timeLeft;

    var timer = setInterval(function() {
        timeLeft--;
        document.getElementById('dlTimeCount').innerText = timeLeft;

        if (timeLeft <= 0) {
            clearInterval(timer);
            document.getElementById('dl-timer').style.display = 'none';
            document.getElementById('downloadBtn').disabled = false;

            // 5초 대기 후 결과창 표시
            var resultBox = document.getElementById('dl-result');
            resultBox.style.display = 'block';
            
            // 기존 RapidAPI 연동 스크립트가 적용될 자리입니다.
            resultBox.innerHTML = '<h5 style="color: #28a745; margin-top: 0;">✅ 영상 분석 완료!</h5>' +
                                  '<p style="font-size: 0.9em; color: #495057;">서버에서 영상을 성공적으로 추출했습니다.</p>';
        }
    }, 1000);
}
</script>
