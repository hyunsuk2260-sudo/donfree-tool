---
title: 비디오 다운로더
icon: fas fa-download
order: 5
layout: page
permalink: /video/
---

<div style="background-color:#f8f9fa;padding:20px;border-radius:8px;margin-bottom:30px;line-height:1.6;border:1px solid #e9ecef;">
    <h4 style="margin-top:0;color:#007bff;">🎬 비디오 다운로더 이용 안내</h4>

    <p>
        워터마크 없는 고화질 동영상을 무료로 다운로드하세요.
        틱톡(TikTok), 인스타그램 릴스, 유튜브 쇼츠 등
        다양한 숏폼 플랫폼의 영상을 저장할 수 있습니다.
    </p>

    <h5 style="margin-bottom:5px;">📌 사용 방법</h5>

    <ol style="margin-top:0;padding-left:20px;">
        <li>다운로드할 동영상의 공유 주소(URL)를 복사합니다.</li>
        <li>아래 입력창에 주소를 붙여넣습니다.</li>
        <li><b>다운로드 링크 생성</b>을 누릅니다.</li>
        <li>생성된 다운로드 버튼을 눌러 저장합니다.</li>
    </ol>

    <p style="font-size:0.85em;color:#dc3545;margin-bottom:0;margin-top:15px;">
        <i>
        *주의사항: 본 툴은 개인 소장 용도로만 사용 가능하며,
        저작권이 있는 영상의 무단 배포 및 상업적 이용을 금지합니다.*
        </i>
    </p>
</div>


<div id="downloader-box" style="text-align:center;margin:40px 0;">

    <input
        type="text"
        id="videoUrl"
        placeholder="다운로드할 동영상 링크를 붙여넣으세요"
        style="
            width:70%;
            padding:12px;
            border:1px solid #ccc;
            border-radius:5px;
            box-sizing:border-box;
        "
    >

    <button
        id="startBtn"
        onclick="startDownload()"
        style="
            padding:12px 25px;
            margin-top:10px;
            background-color:#007bff;
            color:white;
            border:none;
            border-radius:5px;
            cursor:pointer;
            font-weight:bold;
        "
    >
        다운로드 링크 생성
    </button>

</div>


<div
    id="timer-box"
    style="
        display:none;
        text-align:center;
        color:#007bff;
        font-weight:bold;
        margin-bottom:20px;
    "
>
    고화질 원본 영상을 추출하고 있습니다...
    <span id="timeCount" style="font-size:1.2em;">5</span>초
</div>


<div
    id="result-box"
    style="
        text-align:center;
        margin-bottom:30px;
    "
></div>


<!-- 애드센스 -->
<div style="text-align:center;margin:20px 0;min-height:100px;">

    <script
        async
        src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1922344740086878"
        crossorigin="anonymous">
    </script>

    <ins
        class="adsbygoogle"
        style="display:block"
        data-ad-client="ca-pub-1922344740086878"
        data-ad-slot="6535711038"
        data-ad-format="auto"
        data-full-width-responsive="true">
    </ins>

    <script>
        (adsbygoogle = window.adsbygoogle || []).push({});
    </script>

</div>


<script data-proofer-ignore>

let currentVideoUrl = '';



function startDownload() {

    const urlInput =
        document.getElementById('videoUrl').value.trim();

    if (!urlInput) {

        alert('동영상 링크를 입력해주세요!');

        return;
    }


    const startBtn =
        document.getElementById('startBtn');

    const timerBox =
        document.getElementById('timer-box');

    const resultBox =
        document.getElementById('result-box');

    const timeCount =
        document.getElementById('timeCount');


    startBtn.disabled = true;

    timerBox.style.display = 'block';

    resultBox.innerHTML = '';

    let timeLeft = 5;

    timeCount.innerText = timeLeft;


    const timer = setInterval(function() {

        timeLeft--;

        timeCount.innerText = timeLeft;


        if (timeLeft <= 0) {

            clearInterval(timer);

            timerBox.style.display = 'none';

            fetchVideoData(urlInput);

        }

    }, 1000);
}



async function fetchVideoData(videoUrl) {

    const resultBox =
        document.getElementById('result-box');

    resultBox.innerHTML =
        '<span style="color:gray;">비디오 파일을 추출하는 중입니다... 잠시만 기다려주세요.</span>';


    const apiUrl =
        'https://download-all-in-one-ultimate.p.rapidapi.com/autolink?url='
        + encodeURIComponent(videoUrl);


    const options = {

        method: 'GET',

        headers: {

            'x-rapidapi-key':
                'cac13e8cc6msha4ee1d5c412b577p1fd49ejs92b2ab96d0b3',

            'x-rapidapi-host':
                'download-all-in-one-ultimate.p.rapidapi.com'

        }

    };


    try {

        const response =
            await fetch(apiUrl, options);


        if (!response.ok) {

            throw new Error(
                'API response error: ' + response.status
            );

        }


        const result =
            await response.json();


        let downloadLink = '';


        if (
            result &&
            result.medias &&
            result.medias.length > 0
        ) {

            /*
             * 가능한 한 영상 파일을 우선 선택
             */
            const videoMedia =
                result.medias.find(function(media) {

                    if (!media || !media.url) {
                        return false;
                    }

                    const type =
                        String(media.type || '').toLowerCase();

                    const extension =
                        String(media.ext || '').toLowerCase();

                    return (
                        type.includes('video') ||
                        extension === 'mp4' ||
                        extension === 'mov' ||
                        extension === 'webm'
                    );

                });


            if (videoMedia) {

                downloadLink =
                    videoMedia.url;

            } else {

                downloadLink =
                    result.medias[0].url;

            }

        }


        if (!downloadLink) {

            resultBox.innerHTML =
                '<span style="color:red;">비디오 파일을 찾을 수 없습니다.<br>지원되지 않는 링크이거나 비공개 영상일 수 있습니다.</span>';

            return;
        }


        currentVideoUrl =
            downloadLink;


        /*
         * 모바일 다운로드 버튼
         */
        resultBox.innerHTML =

            '<div style="margin-bottom:12px;">' +

                '<button ' +
                    'type="button" ' +
                    'onclick="downloadVideo()" ' +
                    'style="' +
                        'display:inline-block;' +
                        'padding:15px 28px;' +
                        'background:#28a745;' +
                        'color:#fff;' +
                        'border:0;' +
                        'border-radius:7px;' +
                        'font-weight:700;' +
                        'font-size:16px;' +
                        'cursor:pointer;' +
                    '"' +
                '>' +

                    '📥 영상 다운로드' +

                '</button>' +

            '</div>' +

            '<div style="font-size:13px;color:#777;line-height:1.6;">' +

                '휴대폰에서는 다운로드 버튼을 누른 후<br>' +
                '잠시 기다려주세요.' +

            '</div>';

    }


    catch (error) {

        console.error(error);

        resultBox.innerHTML =
            '<span style="color:red;">서버와 통신 중 오류가 발생했습니다.<br>잠시 후 다시 시도해주세요.</span>';

    }


    finally {

        document.getElementById('startBtn').disabled = false;

    }

}



/*
 * 실제 영상 다운로드
 */
async function downloadVideo() {

    if (!currentVideoUrl) {

        alert('다운로드할 영상이 없습니다.');

        return;
    }


    const resultBox =
        document.getElementById('result-box');


    resultBox.innerHTML =

        '<div style="font-weight:bold;margin-bottom:10px;">' +
            '📥 영상을 다운로드하고 있습니다...' +
        '</div>' +

        '<div style="font-size:13px;color:#777;">' +
            '영상 크기에 따라 잠시 걸릴 수 있습니다.' +
        '</div>';


    try {

        /*
         * 영상 파일을 직접 가져옵니다.
         */
        const response =
            await fetch(currentVideoUrl);


        if (!response.ok) {

            throw new Error(
                'VIDEO_FETCH_ERROR'
            );

        }


        const blob =
            await response.blob();


        /*
         * Blob을 이용해 임시 다운로드 주소 생성
         */
        const blobUrl =
            URL.createObjectURL(blob);


        const link =
            document.createElement('a');


        link.href =
            blobUrl;


        link.download =
            'donfree-video.mp4';


        link.style.display =
            'none';


        document.body.appendChild(link);


        link.click();


        link.remove();


        /*
         * 잠시 후 임시 URL 삭제
         */
        setTimeout(function() {

            URL.revokeObjectURL(blobUrl);

        }, 5000);


        resultBox.innerHTML =

            '<div style="color:#28a745;font-weight:bold;">' +
                '✓ 다운로드가 시작되었습니다.' +
            '</div>' +

            '<div style="font-size:13px;color:#777;margin-top:8px;">' +
                '휴대폰에서는 파일 앱 또는 다운로드 폴더를 확인해주세요.' +
            '</div>';

    }


    catch (error) {

        console.error(error);


        /*
         * 모바일 브라우저에서 외부 영상 서버의
         * 직접 fetch가 차단되는 경우를 위한 fallback
         */
        resultBox.innerHTML =

            '<div style="font-weight:bold;margin-bottom:12px;">' +
                '영상 파일을 바로 저장할 수 없습니다.' +
            '</div>' +

            '<a ' +
                'href="' + currentVideoUrl + '" ' +
                'target="_blank" ' +
                'rel="noopener noreferrer" ' +
                'style="' +
                    'display:inline-block;' +
                    'padding:14px 24px;' +
                    'background:#007bff;' +
                    'color:#fff;' +
                    'text-decoration:none;' +
                    'border-radius:7px;' +
                    'font-weight:bold;' +
                '"' +
            '>' +

                '🎬 영상 열기' +

            '</a>' +

            '<div style="font-size:13px;color:#777;margin-top:10px;line-height:1.6;">' +

                '영상이 열리면 휴대폰의<br>' +
                '공유 또는 다운로드 기능으로 저장해주세요.' +

            '</div>';

    }

}

</script>
