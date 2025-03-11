<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>انتظار الدفع</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap');

        body {
            font-family: 'Cairo', sans-serif;
            background: none;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        /* الخلفية المتحركة */
        body::before {
            content: "";
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('OIP.PNG') no-repeat center center/cover;
            filter: blur(10px);
            animation: moveBackground 10s infinite alternate ease-in-out;
            z-index: -1;
        }

        @keyframes moveBackground {
            0% { transform: scale(1); }
            100% { transform: scale(1.1); }
        }

        /* تصميم الكونتينر */
        .status-container {
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(20px);
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            width: 90%;
            max-width: 400px;
            animation: fadeIn 0.5s ease-in-out;
            color: rgb(20, 0, 0);
        }

        h2 {
            color: #0f0101;
            font-size: 24px;
            margin-bottom: 15px;
        }

        .message {
            font-size: 18px;
            padding: 15px;
            border-radius: 8px;
            font-weight: bold;
            transition: all 0.3s ease-in-out;
        }

        .pending {
            background: rgba(255, 215, 0, 0.7);
            color: black;
        }

        .success {
            background: rgba(40, 167, 69, 0.7);
            color: white;
            animation: successAnimation 0.8s ease-in-out;
        }

        .failed {
            background: rgba(220, 53, 69, 0.7);
            color: white;
            animation: failedAnimation 0.8s ease-in-out;
        }

        /* اللودينج */
        .loader {
            width: 60px;
            height: 60px;
            border: 6px solid rgba(255, 255, 255, 0.5);
            border-top-color: #ff4500;
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 20px auto;
        }

        .countdown {
            font-size: 18px;
            font-weight: bold;
            color: red;
            margin-top: 15px;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes successAnimation {
            0% { transform: scale(0.8); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        @keyframes failedAnimation {
            0% { transform: scale(1.2); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

    </style>
</head>
<body>

    <div class="status-container">
        <h2>جارٍ انتظار الدفع...</h2>
        <div class="loader" id="loading-animation"></div>
        <p class="message pending" id="status-msg">يرجى تحويل المبلغ المطلوب خلال <span id="timer">60</span> ثانية...</p>
    </div>

    <script>
    let orderId = new URLSearchParams(window.location.search).get('order_id');
    let timerElement = document.getElementById('timer');
    let messageElement = document.getElementById("status-msg");
    let loaderElement = document.getElementById("loading-animation");
    let timeLeft = 60; // 1 دقيقة

    function checkPaymentStatus() {
        fetch(`check_payment.php?order_id=${orderId}`)
            .then(response => response.json())
            .then(data => {
                if (data.status === "approved") {
                    loaderElement.style.display = "none";
                    messageElement.innerHTML = "✅ تم الدفع بنجاح، يرجى استلام المنتج.";
                    messageElement.classList.remove("pending");
                    messageElement.classList.add("success");
                    sendToESP32();
                } else if (data.status === "rejected") {
                    loaderElement.style.display = "none";
                    messageElement.innerHTML = "❌ فشلت العملية!";
                    messageElement.classList.remove("pending");
                    messageElement.classList.add("failed");
                    setTimeout(() => {
                        window.location.href = "index.html";
                    }, 20000);
                } else {
                    setTimeout(checkPaymentStatus, 5000);
                }
            });
    }

    function sendToESP32() {
        fetch(`send_to_esp.php?order_id=${orderId}`);
    }

    function updatePaymentStatus() {
        fetch(`update_payment.php?order_id=${orderId}&status=rejected`)
            .then(response => response.json())
            .then(data => {
                console.log("تم تحديث حالة الطلب إلى REJECTED");
            })
            .catch(error => console.error("حدث خطأ أثناء تحديث الحالة:", error));
    }

    let countdown = setInterval(() => {
        timeLeft--;
        timerElement.textContent = timeLeft;

        if (timeLeft <= 0) {
            clearInterval(countdown);
            loaderElement.style.display = "none";
            messageElement.innerHTML = "❌ فشلت العملية! لم يتم استلام المبلغ المطلوب.";
            messageElement.classList.remove("pending");
            messageElement.classList.add("rejected");

            // تحديث حالة الطلب في قاعدة البيانات إلى "REJECTED"
            updatePaymentStatus();

            setTimeout(() => {
                window.location.href = "index.html";
            }, 20000);
        }
    }, 1000);

    checkPaymentStatus();
</script>

</body>
</html>
