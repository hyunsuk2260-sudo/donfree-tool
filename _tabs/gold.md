---
title: 실시간 금 시세
icon: fas fa-coins
order: 6
layout: page
permalink: /gold/
---

<!-- 🚨 깃허브 테마 보호막 -->
{% raw %}
<div markdown="0">
    <div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 30px; line-height: 1.6; border: 1px solid #e9ecef;">
        <h4 style="margin-top: 0; color: #d4af37; font-weight: bold;">👑 실시간 국제 금 시세 조회</h4>
        <p>전 세계 금 거래소의 <b>실시간 금 시세(달러 기준)</b>를 24시간 언제나 확인할 수 있습니다.</p>
        <h5 style="margin-bottom: 5px; margin-top: 15px;">📌 차트 보는 법</h5>
        <ul style="margin-top: 0; padding-left: 20px; font-size: 0.95em;">
            <li>차트의 가격은 글로벌 표준인 <b>1온스(약 8.29돈) 당 달러(USD) 가격</b>입니다.</li>
            <li>손가락이나 마우스로 차트를 드래그하여 과거 시세를 확인할 수 있습니다.</li>
            <li>상단의 '1일', '5일', '1개월' 등 버튼을 눌러 기간별 흐름을 분석해 보세요.</li>
        </ul>
    </div>

    <!-- 실시간 금 시세 차트 (트레이딩뷰 엔진 - 가장 안정적인 OANDA:XAUUSD 심볼 적용) -->
    <div class="tradingview-widget-container" style="height: 500px; width: 100%; margin-bottom: 40px; border: 1px solid #ddd; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0,0,0,0.05);">
        <div id="tradingview_gold" style="height: calc(100% - 32px); width: 100%;"></div>
        <script type="text/javascript" src="https://s3.tradingview.com/tv.js"></script>
        <script type="text/javascript">
            new TradingView.widget({
                "autosize": true,
                "symbol": "OANDA:XAUUSD",
                "interval": "D",
                "timezone": "Asia/Seoul",
                "theme": "light",
                "style": "1",
                "locale": "kr",
                "enable_publishing": false,
                "backgroundColor": "#ffffff",
                "gridColor": "#f1f3f6",
                "hide_top_toolbar": false,
                "hide_legend": false,
                "save_image": false,
                "container_id": "tradingview_gold"
            });
        </script>
    </div>

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
{% endraw %}
