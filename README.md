<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>藥師服務滿意度調查</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 0;
            padding: 20px;
        }
        .page {
            display: none;
        }
        .page.active {
            display: block;
        }
        .emotions {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-top: 20px;
        }
        .emotions img {
            width: 100px;
            height: 200px;
            cursor: pointer;
            transition: transform 0.2s;
        }
        .emotions img:hover {
            transform: scale(1.1);
        }
        img.coupon {
            max-width: 600px;
            cursor: pointer;
            transition: transform 0.2s;
        }
        img.coupon:hover {
            transform: scale(1.05);
        }
        button {
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <!-- Page 1: Satisfaction Survey -->
    <div class="page active" id="page1">
        <h1>藥師服務滿意度調查</h1>
        <div class="emotions">
            <img src="happy.png" alt="非常滿意" onclick="showPage('page2')">
            <img src="satisfied.png" alt="滿意" onclick="showPage('page2')">
            <img src="neutral.png" alt="普通" onclick="showPage('page2')">
            <img src="unsatisfied.png" alt="不滿意" onclick="showPage('page2')">
            <img src="very_unsatisfied.png" alt="非常不滿意" onclick="showPage('page2')">
        </div>
    </div>

    <!-- Page 2: Discount Coupon -->
    <div class="page" id="page2">
        <h1>10元商品優惠券</h1>
        <img src="coupon_image.png" alt="優惠券" class="coupon">
        <br><br>
        <button onclick="window.print()">列印優惠券</button>
        <p id="countdown">5秒後將自動返回調查頁面...</p>
    </div>

    <script>
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(page => page.classList.remove('active'));
            document.getElementById(pageId).classList.add('active');

            // 如果進入的是 page2，則 5 秒後自動回到 page1
            if (pageId === 'page2') {
                let countdown = 5;
                const countdownElement = document.getElementById('countdown');
                countdownElement.innerText = `${countdown} 秒後將自動返回調查頁面...`;

                const timer = setInterval(() => {
                    countdown--;
                    countdownElement.innerText = `${countdown} 秒後將自動返回調查頁面...`;
                    if (countdown <= 0) {
                        clearInterval(timer);
                        showPage('page1');
                    }
                }, 1000);
            }
        }
    </script>
</body>
</html>
