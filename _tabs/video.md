---
title: 비디오 다운로더
icon: fas fa-download
order: 5
layout: page
permalink: /video/
---

<!-- 안내문 -->
<div style="background-color:#f8f9fa;padding:20px;border-radius:8px;margin-bottom:30px;line-height:1.6;border:1px solid #e9ecef;">

    <h4 style="margin-top:0;color:#007bff;">
        🎬 비디오 다운로더 이용 안내
    </h4>

    <p>
        워터마크 없는 고화질 동영상을 무료로 다운로드하세요.
        틱톡(TikTok), 인스타그램 릴스, 유튜브 쇼츠 등
        다양한 숏폼 플랫폼의 원본 영상을 빠르고 안전하게 추출할 수 있습니다.
    </p>

    <h5 style="margin-bottom:5px;">
        📌 사용 방법
    </h5>

    <ol style="margin-top:0;padding-left:20px;">
        <li>다운로드하고 싶은 동영상의 공유 주소(URL)를 복사합니다.</li>
        <li>아래 입력창에 주소를 붙여넣습니다.</li>
        <li><b>'다운로드 링크 생성'</b> 버튼을 클릭합니다.</li>
        <li>생성된 다운로드 버튼을 눌러 기기에 저장합니다.</li>
    </ol>

    <p style="font-size:0.85em;color:#dc3545;margin-bottom:0;margin-top:15px;">
        <i>
            *주의사항: 본 툴은 개인 소장 용도로만 사용 가능하며,
            저작권이 있는 영상의 무단 배포 및 상업적 이용을 금지합니다.*
        </i>
    </p>

</div>


<!-- URL 입력 -->
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


<!-- 추출 타이머 -->
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
    고화질 원본 영상을 안전하게 추출하고 있습니다...
    <span id="timeCount" style="font-size:1.2em;">5</span>초 후 링크가 생성됩니다.
</div>


<!-- 결과 -->
<div
    id="result-box"
    style="
        text-align:center;
        margin-bottom:30px;
    "
></div>


<!-- 구글 애드센스 -->
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

function startDownload() {

    const urlInput =
        document.getElementById('videoUrl').value.trim();

    if (!urlInput) {

        alert('링크를 입력해주세요!');

        return;
    }


    document.getElementById('startBtn').disabled = true;

    document.getElementById('timer-box').style.display = 'block';

    document.getElementById('result-box').innerHTML = '';


    let timeLeft = 5;

    document.getElementById('timeCount').innerText = timeLeft;


    const timer = setInterval(function() {

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

    document.getElementById('result-box').innerHTML =
        '<span style="color:gray;">비디오 파일을 추출하는 중입니다... 잠시만 기다려주세요.</span>';


    const url =
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
            await fetch(url, options);


        const result =
            await response.json();


        let downloadLink = '';


        if (
            result &&
            result.medias &&
            result.medias.length > 0
        ) {

            downloadLink =
                result.medias[0].url;

        }


        if (downloadLink) {

            showDownloadButtons(downloadLink);

        } else {

            document.getElementById('result-box').innerHTML =
                '<span style="color:red;">비디오 파일을 찾을 수 없습니다. (지원되지 않는 링크이거나 비공개 영상입니다)</span>';

        }

    }

    catch (error) {

        console.error(error);

        document.getElementById('result-box').innerHTML =
            '<span style="color:red;">서버와 통신 중 오류가 발생했습니다.</span>';

    }

    finally {

        document.getElementById('startBtn').disabled = false;

    }

}


/*
--------------------------------------------------
PC / 모바일 다운로드 버튼 분리
--------------------------------------------------
*/

function showDownloadButtons(downloadLink) {

    const resultBox =
        document.getElementById('result-box');


    /*
     * 현재 접속 기기가 모바일인지 확인
     */

    const isMobile =
        /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(
            navigator.userAgent
        );


    /*
     * PC
     * 기존 다운로드 방식을 그대로 유지
     */

    if (!isMobile) {

        resultBox.innerHTML =

            '<a href="' + downloadLink + '" target="_blank" rel="noopener noreferrer" ' +

            'style="' +
                'display:inline-block;' +
                'padding:15px 30px;' +
                'background-color:#28a745;' +
                'color:white;' +
                'text-decoration:none;' +
                'font-weight:bold;' +
                'border-radius:5px;' +
            '">' +

                '📥 워터마크 없는 비디오 다운로드' +

            '</a>';

        return;
    }


    /*
     * 모바일
     */

    resultBox.innerHTML =

        '<button ' +

            'type="button" ' +

            'onclick="mobileDownload(\'' +
                encodeURIComponent(downloadLink) +
            '\')" ' +

            'style="' +
                'display:inline-block;' +
                'padding:15px 30px;' +
                'background-color:#28a745;' +
                'color:white;' +
                'border:none;' +
                'font-weight:bold;' +
                'border-radius:5px;' +
                'font-size:16px;' +
                'cursor:pointer;' +
            '"' +

        '>' +

            '📥 휴대폰에 다운로드' +

        '</button>' +

        '<div style="margin-top:12px;font-size:13px;color:#777;line-height:1.6;">' +

            '휴대폰에서 버튼을 눌러<br>' +
            '영상을 저장해주세요.' +

        '</div>';

}


/*
--------------------------------------------------
모바일 다운로드
--------------------------------------------------
*/

async function mobileDownload(encodedUrl) {

    const downloadLink =
        decodeURIComponent(encodedUrl);


    const resultBox =
        document.getElementById('result-box');


    resultBox.innerHTML =

        '<div style="font-weight:bold;margin-bottom:10px;">' +
            '📥 다운로드 준비 중입니다...' +
        '</div>' +

        '<div style="font-size:13px;color:#777;">' +
            '잠시만 기다려주세요.' +
        '</div>';


    try {

        /*
         * 영상 파일을 직접 가져오기
         */

        const response =
            await fetch(downloadLink);


        if (!response.ok) {

            throw new Error('DOWNLOAD_FAILED');

        }


        const blob =
            await response.blob();


        /*
         * 영상 파일을 임시 주소로 변환
         */

        const blobUrl =
            URL.createObjectURL(blob);


        /*
         * 다운로드용 링크 생성
         */

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


        document.body.removeChild(link);


        /*
         * 임시 주소 정리
         */

        setTimeout(function() {

            URL.revokeObjectURL(blobUrl);

        }, 10000);


        resultBox.innerHTML =

            '<div style="color:#28a745;font-weight:bold;">' +

                '✓ 다운로드가 시작되었습니다.' +

            '</div>' +

            '<div style="margin-top:8px;font-size:13px;color:#777;">' +

                '휴대폰의 다운로드 폴더 또는 파일 앱에서 확인해주세요.' +

            '</div>';

    }


    catch (error) {

        console.log(error);


        /*
         * 모바일 브라우저가 외부 영상 파일의
         * 직접 다운로드를 막는 경우
         *
         * 기존 방식처럼 영상을 열 수 있도록 함
         */

        resultBox.innerHTML =

            '<div style="font-weight:bold;margin-bottom:12px;">' +

                '영상 다운로드를 준비할 수 없습니다.' +

            '</div>' +

            '<a ' +

                'href="' + downloadLink + '" ' +

                'target="_blank" ' +

                'rel="noopener noreferrer" ' +

                'style="' +

                    'display:inline-block;' +
                    'padding:15px 30px;' +
                    'background-color:#007bff;' +
                    'color:white;' +
                    'text-decoration:none;' +
                    'font-weight:bold;' +
                    'border-radius:5px;' +

                '"' +

            '>' +

                '🎬 영상 열기' +

            '</a>' +

            '<div style="margin-top:10px;font-size:13px;color:#777;line-height:1.6;">' +

                '영상이 열린 후 휴대폰의 공유 또는 저장 기능을 이용해주세요.' +

            '</div>';

    }

}

</script>
