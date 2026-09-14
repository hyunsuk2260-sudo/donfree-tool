---
title: 비디오 다운로더
icon: fas fa-download
order: 5
layout: page
permalink: /video/
---

<!-- 안내문 HTML 박스 (무조건 화면에 출력됨) -->
<div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 30px; line-height: 1.6; border: 1px solid #e9ecef;">
    <h4 style="margin-top: 0; color: #007bff;">🎬 비디오 다운로더 이용 안내</h4>
    <p>워터마크 없는 고화질 동영상을 무료로 다운로드하세요. 틱톡(TikTok), 인스타그램 릴스, 유튜브 쇼츠 등 다양한 숏폼 플랫폼의 원본 영상을 빠르고 안전하게 추출할 수 있습니다.</p>
    
    <h5 style="margin-bottom: 5px;">📌 사용 방법</h5>
    <ol style="margin-top: 0; padding-left: 20px;">
        <li>다운로드하고 싶은 동영상의 공유 주소(URL)를 복사합니다.</li>
        <li>아래 입력창에 주소를 붙여넣고 <b>'다운로드 링크 생성'</b> 버튼을 클릭합니다.</li>
        <li>5초 대기 후 생성되는 다운로드 버튼을 눌러 기기에 저장합니다.</li>
    </ol>
    
    <p style="font-size: 0.85em; color: #dc3545; margin-bottom: 0; margin-top: 15px;">
        <i>*주의사항: 본 툴은 개인 소장 용도로만 사용 가능하며, 저작권이 있는 영상의 무단 배포 및 상업적 이용을 금지합니다.*</i>
    </p>
</div>

<div id="downloader-box" style="text-align: center; margin: 40px 0;">
    <input type="text" id="videoUrl" placeholder="다운로드할 동영상 링크를 붙여넣으세요" style="width: 70%; padding: 12px; border: 1px solid #ccc; border-radius: 5px;">
    <button id="startBtn" onclick="startDownload()" style="padding: 12px 25px; margin-top: 10px; background-color: #007bff; color: white; border: none; border-radius: 5px; cursor: pointer; font-weight: bold;">다운로드 링크 생성</button>
</div>

<!-- 구글 애드센스 디스플레이 광고 시작 (명당자리) -->
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
<!-- 구글 애드센스 디스플레이 광고 끝 -->

<div id="timer-box" style="display: none; text-align: center; color: #dc3545; font-weight: bold; margin-bottom: 20px;">
    광고를 시청하는 중입니다... <span id="timeCount" style="font-size: 1.2em;">5</span>초 후 링크가 생성됩니다.
</div>

<div id="result-box" style="text-align: center; margin-top: 20px;"></div>

<script>
function startDownload() {
    const urlInput = document.getElementById('videoUrl').value;
    if(!urlInput) {
        alert('링크를 입력해주세요!');
        return;
    }

    document.getElementById('startBtn').disabled = true;
    document.getElementById('timer-box').style.display = 'block';
    document.getElementById('result-box').innerHTML = '';

    let timeLeft = 5;
    document.getElementById('timeCount').innerText = timeLeft;

    const timer = setInterval(() => {
        timeLeft--;
        document.getElementById('timeCount').innerText = timeLeft;

        if (timeLeft <= 0) {
            clearInterval(timer);
            document.getElementById('timer-box').style.display = 'none';
            fetchVideoData(urlInput);
        }
    }, 1000);
}

async function fetchVideoData(videoUrl) {
    document.getElementById('result-box').innerHTML = '<span style="color: gray;">비디오 파일을 추출하는 중입니다... 잠시만 기다려주세요.</span>';

    const url = 'https://download-all-in-one-ultimate.p.rapidapi.com/autolink?url=' + encodeURIComponent(videoUrl);
    const options = {
        method: 'GET',
        headers: {
            'x-rapidapi-key': 'cac13e8cc6msha4ee1d5c412b577p1fd49ejsn92b2ab96d0b3',
            'x-rapidapi-host': 'download-all-in-one-ultimate.p.rapidapi.com'
        }
    };

    try {
        const response = await fetch(url, options);
        const result = await response.json();
        
        let downloadLink = '';
        if (result && result.medias && result.medias.length > 0) {
            downloadLink = result.medias[0].url;
        }
        
        if(downloadLink) {
            document.getElementById('result-box').innerHTML = '<a href="' + downloadLink + '" target="_blank" style="display: inline-block; padding: 15px 30px; background-color: #28a745; color: white; text-decoration: none; font-weight: bold; border-radius: 5px;">📥 워터마크 없는 비디오 다운로드</a>';
        } else {
            document.getElementById('result-box').innerHTML = '<span style="color: red;">비디오 파일을 찾을 수 없습니다. (지원되지 않는 링크이거나 비공개 영상입니다)</span>';
        }
    } catch (error) {
        document.getElementById('result-box').innerHTML = '<span style="color: red;">서버와 통신 중 오류가 발생했습니다.</span>';
    } finally {
        document.getElementById('startBtn').disabled = false;
    }
}
</script>
