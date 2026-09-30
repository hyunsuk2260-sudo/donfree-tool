---
title: 비디오 다운로더
icon: fas fa-download
order: 5
layout: page
permalink: /video/
---

<!-- 안내문 HTML 박스 -->
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

<div id="downloader-box" style="text-align: center; margin: 40px 0;">
    <input type="text" id="videoUrl" placeholder="다운로드할 동영상 링크를 붙여넣으세요" style="width: 70%; padding: 12px; border: 1px solid #ccc; border-radius: 5px;">
    <button id="startBtn" onclick="startDownload()" style="padding: 12px 25px; margin-top: 10px; background-color: #007bff; color: white; border: none; border-radius: 5px; cursor: pointer; font-weight: bold;">다운로드 링크 생성</button>
</div>

<div id="timer-box" style="display: none; text-align: center; color: #007bff; font-weight: bold; margin-bottom: 20px;">
    고화질 원본 영상을 추출하고 있습니다... <span id="timeCount" style="font-size: 1.2em;">5</span>초 후 버튼이 생성됩니다.
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
    document.getElementById('result-box').innerHTML = '<span style="color: gray;">서버에서 영상을 가져오는 중입니다...</span>';

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
            // 안내문 다 빼고, 강제 다운로드(Blob) 자바스크립트 함수를 연결했습니다.
            document.getElementById('result-box').innerHTML = `
                <button onclick="forceDownload('${downloadLink}', 'video.mp4')" style="padding: 15px 30px; background-color: #28a745; color: white; border: none; font-weight: bold; border-radius: 5px; cursor: pointer; font-size: 1.1em;">
                    📥 스마트폰에 직접 저장하기
                </button>
                <div id="download-progress" style="display:none; color: #007bff; margin-top: 15px; font-weight: bold;">
                    ⏳ 영상 데이터를 기기로 가져오고 있습니다... (잠시만 기다려주세요)
                </div>
            `;
        } else {
            document.getElementById('result-box').innerHTML = '<span style="color: red;">비디오 파일을 찾을 수 없습니다.</span>';
        }
    } catch (error) {
        document.getElementById('result-box').innerHTML = '<span style="color: red;">서버 오류가 발생했습니다.</span>';
    } finally {
        document.getElementById('startBtn').disabled = false;
    }
}

// 🚨 새 창이 열리는 것을 막고 핸드폰에 강제로 저장시키는 핵심 코드입니다.
window.forceDownload = async function(videoUrl, fileName) {
    const progress = document.getElementById('download-progress');
    progress.style.display = 'block';
    
    try {
        // 1. 영상 주소로 들어가서 데이터를 통째로 긁어옵니다.
        const response = await fetch(videoUrl);
        const blob = await response.blob();
        
        // 2. 스마트폰 메모리 안에 강제로 임시 주소를 만듭니다.
        const blobUrl = window.URL.createObjectURL(blob);
        
        // 3. 브라우저가 모르게 투명 버튼을 눌러 다운로드를 실행시킵니다.
        const a = document.createElement('a');
        a.style.display = 'none';
        a.href = blobUrl;
        a.download = fileName;
        document.body.appendChild(a);
        a.click();
        
        // 4. 흔적 지우기
        window.URL.revokeObjectURL(blobUrl);
        document.body.removeChild(a);
        
        progress.innerText = "✅ 핸드폰 저장 공간에 다운로드가 완료되었습니다!";
        progress.style.color = "green";
        
    } catch (error) {
        // 영상 서버에서 보안(CORS)으로 데이터 추출을 막은 경우 최후의 수단
        progress.style.display = 'none';
        alert("해당 영상 서버의 보안 차단으로 자동 저장이 실패했습니다. 열리는 창에서 영상을 꾹 눌러 저장해 주세요.");
        window.open(videoUrl, '_blank');
    }
};
</script>
