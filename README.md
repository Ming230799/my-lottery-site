# my-lottery-site
1欧元参与，赢100欧元的抽奖网站”
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>抽奖网站 - 1欧元参与，赢100欧元</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f3f3f3;
            color: #333;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #4CAF50;
            color: white;
            padding: 20px;
            text-align: center;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        h2 {
            color: #333;
        }
        .instructions, .payment-info, .form-container, .progress, .winner-section {
            margin-bottom: 30px;
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }
        .progress-bar {
            background-color: #ccc;
            height: 30px;
            border-radius: 15px;
            overflow: hidden;
            position: relative;
        }
        .progress-bar span {
            background-color: #4CAF50;
            display: block;
            height: 100%;
            width: 0;
        }
        .form-container input, .form-container button {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 2px solid #ccc;
            border-radius: 5px;
            box-sizing: border-box;
        }
        .form-container button {
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
        }
        .form-container button:hover {
            background-color: #45a049;
        }
        .winner-section {
            display: none;
            text-align: center;
        }
        footer {
            text-align: center;
            padding: 20px;
            background-color: #4CAF50;
            color: white;
        }
    </style>
</head>
<body>

<header>
    <h1>1欧元参与，赢100欧元</h1>
    <p>每次我们累计到 300 欧元，就会抽出一个幸运儿，奖金额100欧元！</p>
</header>

<div class="container">
    <!-- 说明部分 -->
    <div class="instructions">
        <h2>如何参与</h2>
        <p>只需要支付 1 欧元，你就有机会赢得 100 欧元大奖！每当参与人数达到 300 人时，我们将从参与者中随机抽取 1 位幸运儿，送出 100 欧元。</p>
        <p><strong>付款方式：</strong><br>
            请通过以下方式支付 1 欧元：</p>
        <ul>
            <li>银行转账：账户号码 123456789</li>
            <li>Revolut 转账：用户名 your_revolut_username</li>
        </ul>
        <p>支付完成后，请填写下方表格提交您的信息。</p>
    </div>

    <!-- 进度部分 -->
    <div class="progress">
        <h2>当前参与人数</h2>
        <div class="progress-bar">
            <span id="progress-bar" style="width: 0%"></span>
        </div>
        <p id="progress-text">当前参与人数：0 / 300</p>
    </div>

    <!-- 用户信息填写 -->
    <div class="form-container">
        <h2>填写您的信息</h2>
        <input type="text" id="email" placeholder="请输入您的邮箱" required>
        <input type="text" id="phone" placeholder="请输入您的手机号" required>
        <input type="text" id="nickname" placeholder="请输入您的昵称" required>
        <input type="text" id="revolut" placeholder="请输入您的Revolut用户名" required>
        <button onclick="submitForm()">提交</button>
    </div>

    <!-- 中奖信息部分 -->
    <div class="winner-section" id="winner-section">
        <h2>恭喜您！您是本次的幸运中奖者！</h2>
        <p>我们会尽快通过您的联系方式与您联系。</p>
    </div>
</div>

<footer>
    <p>&copy; 2025 抽奖网站 - 1欧元参与，赢100欧元</p>
</footer>

<script>
    let participants = []; // 存储参与者信息
    const goal = 300; // 目标人数
    let currentParticipants = 0;

    // 生成一个随机中奖者
    function pickWinner() {
        if (currentParticipants >= goal) {
            const winner = participants[Math.floor(Math.random() * participants.length)];
            document.getElementById('winner-section').style.display = 'block';
            alert(`恭喜 ${winner.nickname}（邮箱：${winner.email}）中奖了！`);
        }
    }

    // 更新进度条
    function updateProgress() {
        const progressPercentage = (currentParticipants / goal) * 100;
        document.getElementById('progress-bar').style.width = progressPercentage + '%';
        document.getElementById('progress-text').innerText = `当前参与人数：${currentParticipants} / ${goal}`;
    }

    // 提交表单
    function submitForm() {
        const email = document.getElementById('email').value;
        const phone = document.getElementById('phone').value;
        const nickname = document.getElementById('nickname').value;
        const revolut = document.getElementById('revolut').value;

        if (email && phone && nickname && revolut) {
            participants.push({ email, phone, nickname, revolut });
            currentParticipants++;
            updateProgress();
            pickWinner();
            alert('您的信息已提交成功！感谢您的参与！');
            document.querySelector('.form-container').reset();
        } else {
            alert('请填写所有信息！');
        }
    }
</script>

</body>
</html>
