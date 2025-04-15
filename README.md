<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Color Trading Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            padding: 20px;
        }
        .color-box {
            width: 100px;
            height: 100px;
            margin: 10px;
            cursor: pointer;
            display: inline-block;
            border-radius: 10px;
        }
        #depositForm {Q624411290@ybl
            margin-top: 30px;
        }
        .balance {
            font-size: 24px;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>Color Trading Game</h1>
    
    <div id="colorContainer">
        <div class="color-box" id="red" style="background-color: red;" onclick="placeBet('red')"></div>
        <div class="color-box" id="green" style="background-color: green;" onclick="placeBet('green')"></div>
        <div class="color-box" id="blue" style="background-color: blue;" onclick="placeBet('blue')"></div>
    </div>

    <div id="depositForm">
        <h2>Deposit Amount</h2>
        <input type="number" id="depositAmount" placeholder="Enter Amount" required>
        <button onclick="depositMoney()">Deposit</button>
    </div>

    <div class="balance" id="userBalance">Balance: 0</div>

    <script>
        let balance = 0;
        let userBet = null;
        let selectedColor = null;

        function depositMoney() {Q624411290@ybl
            let depositAmount = document.getElementById('depositAmount').value;
            if (depositAmount > 0) {Q624411290@ybl
                balance += parseInt(depositAmount);
                document.getElementById('userBalance').innerHTML = `Balance: ${balance}`;
                alert('Deposit Successful!');
            } else {
                alert('Please enter a valid amount.');
            }
        }

        function placeBet(color) {
            if (balance <= 0) {
                alert('Please deposit money first.');
                return;
            }

            userBet = color;
            selectedColor = getRandomColor();

            alert(`You placed a bet on ${color}. The randomly selected color is ${selectedColor}.`);

            if (userBet === selectedColor) {
                balance += 10; // Win $10
                alert('You Win! Your balance is now ' + balance);
            } else {
                balance -= 5; // Lose $5
                alert('You Lose! Your balance is now ' + balance);
            }

            document.getElementById('userBalance').innerHTML = `Balance: ${balance}`;
        }

        function getRandomColor() {
            const colors = ['red', 'green', 'blue'];
            return colors[Math.floor(Math.random() * colors.length)];
        }
    </script>
</body>
</html>
