---
title: 비디오 다운로더
layout: page
permalink: /video/
---

<div id="downloader-box" style="text-align: center; margin: 40px 0;">
    <input type="text" id="videoUrl" placeholder="다운로드할 동영상 링크를 붙여넣으세요" style="width: 70%; padding: 12px; border: 1px solid #ccc; border-radius: 5px;">
    <button id="startBtn" onclick="startDownload()" style="padding: 12px 25px; margin-top: 10px; background-color: #007bff; color: white; border: none; border-radius: 5px; cursor: pointer; font-weight: bold;">다운로드 링크 생성</button>
</div>

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
    document.getElementById('result-box').innerHTML = '<span style="color: gray;">데이터를 변환하는 중입니다... 잠시만 기다려주세요.</span>';

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
        if (result && result.url) {
            downloadLink = result.url;
        } else if (result && result.data && result.data.url) {
            downloadLink = result.data.url;
        } else if (result && result.video) {
            downloadLink = result.video;
        } else if (result && result.data && result.video_url) {
            downloadLink = result.video_url;
        }

        if(downloadLink) {
            document.getElementById('result-box').innerHTML = '<a href="' + downloadLink + '" target="_blank" style="display: inline-block; padding: 15px 30px; background-color: #28a745; color: white; text-decoration: none; font-weight: bold; border-radius: 5px;">📥 비디오 다운로드</a>';
        } else {
            document.getElementById('result-box').innerHTML = '<span style="color: red;">다운로드 링크를 찾을 수 없습니다. 올바른 주소인지 확인해 주세요.</span>';
        }
    } catch (error) {
        document.getElementById('result-box').innerHTML = '<span style="color: red;">서버와 통신 중 오류가 발생했습니다.</span>';
    } finally {
        document.getElementById('startBtn').disabled = false;
    }
}
</script>
