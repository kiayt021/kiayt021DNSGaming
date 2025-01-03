# kiayt021DNSGaming
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ساخت DNS</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #89f7fe, #66a6ff);
            color: white;
            text-align: center;
            padding: 20px;
            margin: 0;
            overflow-x: hidden;
        }
        h1, h2 {
            margin-bottom: 20px;
        }
        .header {
            font-size: 1.2em;
            margin-bottom: 20px;
            color: #ffeb3b;
        }
        input[type="password"], button {
            padding: 10px 20px;
            margin: 10px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
        }
        input[type="password"] {
            width: 80%;
            background-color: #ffffff;
            color: #333;
            border-radius: 8px;
            border: 1px solid #ccc;
        }
        button {
            background-color: #28a745;
            color: white;
            cursor: pointer;
        }
        .menu, .dns-list {
            display: none;
        }
        .menu.show, .dns-list.show {
            display: block;
        }
        .btn {
            padding: 12px 30px;
            margin: 10px;
            border: none;
            border-radius: 8px;
            background: linear-gradient(90deg, #f85032, #e73827);
            color: white;
            font-size: 16px;
            cursor: pointer;
        }
        .dns-item {
            margin: 15px 0;
            display: flex;
            justify-content: space-between;
            background-color: rgba(255, 255, 255, 0.1);
            padding: 12px;
            border-radius: 8px;
        }
        .dns-item button {
            background-color: #28a745;
            padding: 8px 15px;
            border-radius: 5px;
        }
        .social-links {
            margin-top: 30px;
            color: white;
        }
        .social-links a {
            color: #ffd700;
            text-decoration: none;
            font-size: 1.2em;
            margin: 0 15px;
        }
        .copy-alert {
            position: fixed;
            top: 10%;
            right: 10%;
            background: rgba(0, 0, 0, 0.8);
            color: white;
            padding: 10px 20px;
            border-radius: 5px;
            z-index: 1000;
            display: none;
        }
        .report {
            color: red;
            font-size: 1.2em;
            margin-top: 20px;
        }
        .report-form {
            margin-top: 20px;
        }
        .report-form textarea {
            width: 80%;
            padding: 10px;
            font-size: 16px;
            border-radius: 5px;
            border: 1px solid #ccc;
        }
        .gaming-title {
            color: #ff6347; /* رنگ متفاوت برای "DNS Gaming" */
        }
        .footer-message {
            margin-top: 40px;
            color: white;
            font-size: 1.1em;
        }
        .created-by {
            margin-top: 20px;
            color: white;
            font-size: 1.1em;
        }
        .legal-notice {
            margin-top: 20px;
            padding: 10px;
            background-color: rgba(0, 0, 0, 0.6);
            color: white;
            font-size: 1.1em;
            text-align: center;
            border-radius: 8px;
        }
    </style>
    <script>
        function checkPassword() {
            const password = document.getElementById("password").value;
            const report = document.querySelector(".report"); // گزارش ورود اشتباه
            const reportForm = document.querySelector(".report-form"); // فرم ارسال گزارش

            if (password === "KIA_YT021 _DNS_VVIP") {
                // ورود موفق
                document.querySelector(".login").style.display = "none";
                document.querySelector(".menu").classList.add("show");
                document.querySelector(".welcome-message").innerHTML = `
                    <h1>به پنل دی آن اس گیمینگ KIA_YT021 خوش آمدید</h1>
                    <h2 class="gaming-title">DNS Gaming</h2>
                `;
                // مخفی کردن گزارش و فرم پس از ورود صحیح
                report.style.display = "none";
                reportForm.style.display = "none"; 
            } else {
                // رمز عبور اشتباه
                report.style.display = "block"; // نمایش گزارش در صورت اشتباه بودن پسورد
                reportForm.style.display = "block"; // نمایش فرم ارسال گزارش
            }
        }

        // لیست DNSهای ثابت شما
        const dnsList = {
            codm: {
                vip: [
                    "85.27.205.239",
                    "2001:db8::1",
                    "192.168.1.1",
                    "2001:db8::2"
                ],
                silver: [
                    "10.202.10.10",
                    "2001:db8::3",
                    "10.202.10.12",
                    "2001:db8::4"
                ],
                custom: [
                    "192.168.1.1",
                    "2001:db8::5",
                    "192.168.1.2",
                    "2001:db8::6"
                ]
            },
            pubg: {
                gold: [
                    "172.20.10.1",
                    "2607:f0d0:1002:51::4",
                    "172.20.10.2",
                    "2607:f0d0:1002:51::5"
                ],
                diamond: [
                    "203.0.113.1",
                    "2607:f0d0:2002:51::4",
                    "203.0.113.2",
                    "2607:f0d0:2002:51::6"
                ],
                silver: [
                    "198.51.100.1",
                    "2607:f0d0:3002:51::4",
                    "198.51.100.2",
                    "2607:f0d0:3002:51::5"
                ]
            }
        };

        // DNS رندوم
        const randomDns = [
            "109.61.18.10",
            "78.157.42.100",
            "10.202.10.10",
            "209.38.219.120",
            "138.68.131.245",
            "78.157.42.101",
            "10.202.10.202",
            "109.61.18.194",
            "209.97.185.72",
            "164.92.240.141",
            "5.200.200.200",
            "188.114.96.88",
            "206.189.126.132",
            "206.189.126.131",
            "164.92.170.179",
            "164.92.170.180",
            "217.195.200.194",
            "217.195.200.195",
            "217.195.200.196"
        ];

        function showDNS(serverType, game) {
            const dnsItems = document.getElementById("dns-items");
            let dnsData = "";

            // اضافه کردن DNS ثابت شما
            if (game === "codm") {
                dnsData = dnsList.codm[serverType].map(dns => `
                    <div class="dns-item">
                        <span>${dns}</span> 
                        <button onclick="copyDNS(this)">کپی کن</button>
                    </div>
                `).join("");
            } else if (game === "pubg") {
                dnsData = dnsList.pubg[serverType].map(dns => `
                    <div class="dns-item">
                        <span>${dns}</span> 
                        <button onclick="copyDNS(this)">کپی کن</button>
                    </div>
                `).join("");
            }

            // اضافه کردن DNS رندوم
            const randomDnsIndex = Math.floor(Math.random() * randomDns.length);
            dnsData += `
                <div class="dns-item">
                    <span>${randomDns[randomDnsIndex]}</span> 
                    <button onclick="copyDNS(this)">کپی کن</button>
                </div>
            `;

            dnsItems.innerHTML = dnsData;
            document.querySelector(".dns-list").classList.add("show");
        }

        function copyDNS(button) {
            const dns = button.previousElementSibling.textContent;  // گرفتن DNS از متن
            const textArea = document.createElement("textarea");
            textArea.value = dns;
            document.body.appendChild(textArea);
            textArea.select();
            document.execCommand("copy");
            document.body.removeChild(textArea);

            const alertBox = document.querySelector(".copy-alert");
            alertBox.textContent = "کپی شد!";
            alertBox.style.display = "block";

            setTimeout(() => {
                document.querySelector(".copy-alert").style.display = "none"; // پنهان کردن پیام بعد از چند ثانیه
            }, 2000); // 2 ثانیه بعد پیام پنهان می‌شود
        }
    </script>
</head>
<body>
    <!-- صفحه ورود -->
    <div class="login">
        <h2 class="header">لطفاً رمز عبور خود را وارد کنید:</h2>
        <input type="password" id="password" placeholder="رمز عبور">
        <button onclick="checkPassword()">ورود</button>

        <!-- دکمه جدید برای دریافت پسورد ورد پنل -->
        <button onclick="window.location.href='YOUR_LINK_HERE'">برای دریافت پسورد پنل ورود کیلیک کنید</button>

        <!-- حذف پیام اشتباه -->
        <div class="report-form" style="display:block;">
            <h3>ارسال گزارش و نظرات درباره سایت:</h3>
            <button onclick="window.location.href='https://t.me/KIA_YT021_Gaming_site_Bot'">ارسال گزارش و نظرات</button>
        </div>
    </div>

    <!-- صفحه اصلی بعد از ورود -->
    <div class="menu">
        <div class="welcome-message"></div>
        <div class="btn" onclick="showDNS('vip', 'codm')">کد DNS سرور VIP برای CODM</div>
        <div class="btn" onclick="showDNS('silver', 'codm')">کد DNS سرور Silver برای CODM</div>
        <div class="btn" onclick="showDNS('gold', 'pubg')">کد DNS سرور Gold برای PUBG</div>
        <div class="btn" onclick="showDNS('diamond', 'pubg')">کد DNS سرور Diamond برای PUBG</div>
        <div class="btn" onclick="showDNS('custom', 'codm')">کد DNS سرور سفارشی برای CODM</div>
    </div>

    <!-- لیست DNS ها -->
    <div class="dns-list">
        <div id="dns-items"></div>
    </div>

    <!-- پیام کپی شدن DNS -->
    <div class="copy-alert">کپی شد!</div>

    <!-- لینک‌های شبکه‌های اجتماعی -->
    <div class="social-links">
        <a href="https://www.instagram.com/kia_yt021/profilecard/?igsh=d3VyYWVlMHE3MGM2" target="_blank">اینستاگرام KIAYT</a>
        <a href="https://t.me/KIA_YT0610" target="_blank">کانال تلگرام KIAYT</a>
        <a href="https://youtube.com/@kia_yt021?si=OB0q114xNRkfSAuY" target="_blank">چنل یوتیوب KIAYT</a>
    </div>

    <!-- پیام پایین -->
    <div class="footer-message">
        <p>برای استفاده از پنل، لینک‌های گذاشته شده فالو کنید</p>
    </div>

    <!-- اطلاعات حقوقی و مراجع -->
    <div class="legal-notice">
        <p>تمامی حقوق این وبسایت متعلق به KIA_YT021 است. این سایت صرفاً برای استفاده شخصی و غیر تجاری است. استفاده از این سایت و سرویس‌ها به عهده خود کاربران است.</p>
    </div>

    <!-- اطلاعات سازنده -->
    <div class="created-by">
        <p>طراحی و توسعه توسط KIA_YT021</p>
    </div>
</body>
</html>
