<script>
function startDownload() {
    const urlInput = document.getElementById('videoUrl').value.trim();

    if (!urlInput) {
        alert('링크를 입력해주세요!');
        return;
    }

    const startBtn = document.getElementById('startBtn');
    const timerBox = document.getElementById('timer-box');
    const resultBox = document.getElementById('result-box');

    startBtn.disabled = true;
    timerBox.style.display = 'block';
    resultBox.innerHTML = '';

    let timeLeft = 5;
    document.getElementById('timeCount').innerText = timeLeft;

    const timer = setInterval(() => {
        timeLeft--;
        document.getElementById('timeCount').innerText = timeLeft;

        if (timeLeft <= 0) {
            clearInterval(timer);
            timerBox.style.display = 'none';
            fetchVideoData(urlInput);
        }
    }, 1000);
}


async function fetchVideoData(videoUrl) {

    const resultBox = document.getElementById('result-box');

    resultBox.innerHTML =
        '<span style="color:gray;">비디오 파일을 추출하는 중입니다... 잠시만 기다려주세요.</span>';

    const apiUrl =
        'https://download-all-in-one-ultimate.p.rapidapi.com/autolink?url=' +
        encodeURIComponent(videoUrl);

    try {

        const response = await fetch(apiUrl, {
            method: 'GET',
            headers: {
                'x-rapidapi-key': 'cac13e8cc6msha4ee1d5c412b577p1fd49ejsn92b2ab96d0b3',
                'x-rapidapi-host': 'download-all-in-one-ultimate.p.rapidapi.com'
            }
        });

        if (!response.ok) {
            throw new Error('API 오류: ' + response.status);
        }

        const result = await response.json();

        console.log('RapidAPI 결과:', result);

        let downloadLink = '';

        if (
            result &&
            result.medias &&
            result.medias.length > 0
        ) {
            // 워터마크 없는 영상 우선 선택
            const noWatermark =
                result.medias.find(
                    media =>
                        media.type === 'video' &&
                        (
                            media.quality === 'hd_no_watermark' ||
                            media.quality === 'no_watermark'
                        )
                );

            if (noWatermark) {
                downloadLink = noWatermark.url;
            } else {

                const video =
                    result.medias.find(
                        media => media.type === 'video'
                    );

                if (video) {
                    downloadLink = video.url;
                }
            }
        }

        if (!downloadLink) {
            resultBox.innerHTML =
                '<span style="color:red;">비디오 파일을 찾을 수 없습니다. 지원되지 않는 링크이거나 비공개 영상일 수 있습니다.</span>';

            document.getElementById('startBtn').disabled = false;
            return;
        }


        /*
         * PC
         * 기존처럼 새 창에서 다운로드 URL 열기
         */
        if (!isMobileDevice()) {

            resultBox.innerHTML =
                '<a href="' + downloadLink + '" target="_blank" rel="noopener noreferrer" ' +
                'style="display:inline-block;padding:15px 30px;background:#28a745;color:white;text-decoration:none;font-weight:bold;border-radius:8px;">' +
                '📥 워터마크 없는 비디오 다운로드' +
                '</a>';

        }


        /*
         * 모바일
         */
        else {

            resultBox.innerHTML =
                '<button id="mobileDownloadBtn" ' +
                'style="display:inline-block;padding:16px 25px;background:#28a745;color:white;border:0;font-size:16px;font-weight:bold;border-radius:8px;cursor:pointer;">' +
                '📥 비디오 다운로드' +
                '</button>' +

                '<div style="margin-top:12px;font-size:13px;color:#777;">' +
                '버튼을 누르면 다운로드가 시작됩니다.' +
                '</div>';


            document
                .getElementById('mobileDownloadBtn')
                .addEventListener('click', function () {

                    downloadMobileVideo(downloadLink);

                });

        }

    } catch (error) {

        console.error(error);

        resultBox.innerHTML =
            '<span style="color:red;">서버와 통신 중 오류가 발생했습니다.</span>';

    } finally {

        document.getElementById('startBtn').disabled = false;

    }
}


/*
 * 모바일 기기 확인
 */
function isMobileDevice() {

    return /Android|iPhone|iPad|iPod|Mobile/i.test(
        navigator.userAgent
    );

}


/*
 * 모바일 다운로드
 */
async function downloadMobileVideo(downloadLink) {

    const btn =
        document.getElementById('mobileDownloadBtn');

    if (btn) {

        btn.disabled = true;
        btn.innerText = '⏳ 다운로드 준비 중...';

    }

    try {

        const response =
            await fetch(downloadLink);

        if (!response.ok) {
            throw new Error('영상 다운로드 실패');
        }

        const blob =
            await response.blob();

        const blobUrl =
            URL.createObjectURL(blob);

        const link =
            document.createElement('a');

        link.href = blobUrl;
        link.download = 'donfree-video.mp4';

        document.body.appendChild(link);

        link.click();

        link.remove();

        setTimeout(() => {
            URL.revokeObjectURL(blobUrl);
        }, 10000);

        if (btn) {
            btn.innerText = '✅ 다운로드 완료';
        }

    } catch (error) {

        console.error(
            '모바일 다운로드 오류:',
            error
        );

        /*
         * 모바일 브라우저가 TikTok CDN 직접 다운로드를
         * 차단하는 경우 영상 주소를 새 창으로 열어준다.
         */

        if (btn) {

            btn.disabled = false;
            btn.innerText = '📥 다시 다운로드';

        }

        const fallback =
            document.createElement('a');

        fallback.href = downloadLink;
        fallback.target = '_blank';
        fallback.rel = 'noopener noreferrer';

        document.body.appendChild(fallback);

        fallback.click();

        fallback.remove();

    }

}
</script>
