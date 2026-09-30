---
title: 비디오 다운로더
icon: fas fa-download
order: 5
layout: page
permalink: /video/
---

<!-- 🚨 {% raw %} 부터 {% endraw %} 사이는 깃허브 테마가 절대 건드리지 못하는 절대 보호 구역입니다. -->
{% raw %}
<div id="video-downloader-wrapper">
    <!-- 안내문 -->
    <div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 30px; line-height: 1.6; border: 1px solid #e9ecef;">
        <h4 style="margin-top: 0; color: #007bff;">🎬 비디오 다운로더 이용 안내</h4>
        <p>워터마크 없는 고화질 동영상을 무료로 다운로드하세요. 틱톡(TikTok), 인스타그램 릴스, 유튜브 쇼츠 등 다양한 숏폼 플랫폼의 원본 영상을 빠르고 안전하게 추출할 수 있습니다.</p>
        
        <h5 style="margin-bottom: 5px;">📌 사용 방법</h5>
        <ol style="margin-top: 0; padding-left: 20px;">
            <li>다운로드하고 싶은 동영상의 공유 주소(URL)를 복사합니다.</li>
            <li>아래 입력창에 주소를 붙여넣고 <b>'다운로드 링크 생성'</b> 버튼을 클릭합니다.</li>
            <li>5초 대기 후 생성되는 다운로드 버튼을 눌러 기기에 저장합니다.</li>
        </ol>
    </div>

    <!-- 입력부 -->
    <div style="text-align: center; margin: 40px 0;">
        <input type="text" id="videoUrl" placeholder="다운로드할 동영상 링크를 붙여넣으세요" style="width: 70%; padding: 12px; border: 1px solid #ccc; border-radius: 5px;">
        <!-- 버튼에 직접 onclick 명령을 달아 무조건 작동하게 고정했습니다 -->
        <button id="startBtn" onclick="window.startVidDownload()" style="padding: 12px 25px; margin-top: 10px; background-color: #007bff; color: white; border: none; border-radius: 5px; cursor: pointer; font-weight: bold;">다운로드 링크 생성</button>
    </div>

    <!-- 대기 시간 및 결과창 -->
    <div id="timer-box" style="display: none; text-align: center; color: #007bff; font-weight: bold; margin-bottom: 20px;">
        고화질 원본 영상을 안전하게 추출하고 있습니다... <span id="timeCount" style="font-size: 1.2em;">5</span>초 후 링크가 생성됩니다.
    </div>
    
    <div id="result-box" style="text-align: center; margin-bottom: 30px;"></div>

    <!-- 구글 애드센스 디스플레이 광고 -->
    <div style="text-align: center; margin: 20px 0; min-height: 100px;">
        <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878" crossorigin="anonymous"></script>
        <ins class="adsbygoogle"
             style="display:block"
             data-ad-client="ca-pub-1922344740086878"
             data-ad-slot="6535711038"
             data-ad-format="auto"
             data-full-width-responsive="true"></ins>
        <script>
             (adsbygoogle = window.adsbygoogle || []).push({});
        </script>
    </div>
</div>

<script>
// 전역 함수로 선언하여 테마의 영향을 받지 않습니다.
window.startVidDownload = function() {
    var urlInput = document.getElementById('videoUrl').value;
    if(!urlInput) {
        alert('링크를 입력해주세요!');
        return;
    }

    var btn = document.getElementById('startBtn');
    btn.disabled = true;
    document.getElementById('timer-box').style.display = 'block';
    document.getElementById('result-box').innerHTML = '';

    var timeLeft = 5;
    document.getElementById('timeCount').innerText = timeLeft;

    var timer = setInterval(function() {
        timeLeft--;
        document.getElementById('timeCount').innerText = timeLeft;

        if (timeLeft <= 0) {
            clearInterval(timer);
            document.getElementById('timer-box').style.display = 'none';
            
            document.getElementById('result-box').innerHTML = '<span style="color: gray;">비디오 파일을 추출하는 중입니다... 잠시만 기다려주세요.</span>';
            
            var apiUrl = 'https://download-all-in-one-ultimate.p.rapidapi.com/autolink?url=' + encodeURIComponent(urlInput);
            
            fetch(apiUrl, {
                method: 'GET',
                headers: {
                    'x-rapidapi-key': 'cac13e8cc6msha4ee1d5c412b577p1fd49ejsn92b2ab96d0b3',
                    'x-rapidapi-host': 'download-all-in-one-ultimate.p.rapidapi.com'
                }
            })
            .then(function(response) { return response.json(); })
            .then(function(result) {
                var downloadLink = '';
                if (result && result.medias && result.medias.length > 0) {
                    downloadLink = result.medias[0].url;
                }
                
                if(downloadLink) {
                    // 컴퓨터(클릭 다운로드) + 모바일(download 속성 지원) 모두 작동하는 HTML 코드입니다.
                    document.getElementById('result-box').innerHTML = 
                        '<a href="' + downloadLink + '" download="video.mp4" target="_blank" style="display: inline-block; padding: 15px 30px; background-color: #28a745; color: white; text-decoration: none; font-weight: bold; border-radius: 5px; margin-bottom: 10px;">' +
                        '📥 비디오 다운로드' +
                        '</a>';
                } else {
                    document.getElementById('result-box').innerHTML = '<span style="color: red;">비디오 파일을 찾을 수 없습니다.</span>';
                }
            })
            .catch(function(error) {
                document.getElementById('result-box').innerHTML = '<span style="color: red;">서버 통신 오류가 발생했습니다.</span>';
            })
            .finally(function() {
                btn.disabled = false;
            });
        }
    }, 1000);
};
</script>
{% endraw %}
<!-- 🚨 보호막 종료 -->
