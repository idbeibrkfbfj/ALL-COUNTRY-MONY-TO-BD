
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Animated Name</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: url('https://source.unsplash.com/1920x1080/?space,stars') no-repeat center center/cover;
            color: #fff;
            text-align: center;
            padding: 0;
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            transition: background-color 0.3s ease;
        }

        .header {
            margin-top: 20px;
            padding: 20px;
            font-size: 2.5rem;
            font-weight: bold;
            background: rgba(255, 0, 0, 0.7); /* Red background */
            color: #ffd700;
            text-align: center;
            border-radius: 10px;
            display: inline-block;
            text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.5);
            border: 4px solid #ff4500;
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .header-text {
            margin-right: 35px;
        }

        .toggle-btn {
            font-size: 2rem; /* Increased font size for better fit */
            background: none;
            border: none;
            color: white;
            cursor: pointer;
            padding: 10px;
            margin-left: 20px; /* To give space between the text and the button */
        }

        .name {
            font-size: 3rem;
            font-weight: bold;
            margin-top: 10px;
            display: inline-block;
            animation: colorAnimation 3s infinite;
            text-shadow: 0 0 15px rgba(255, 255, 255, 0.8), 0 0 30px rgba(255, 255, 255, 0.6);
        }

        @keyframes colorAnimation {
            0%, 100% {
                color: #ff0000; /* Red */
                text-shadow: 0 0 15px #ff0000, 0 0 30px #ff4500;
            }
            25% {
                color: #00ff00; /* Green */
                text-shadow: 0 0 15px #00ff00, 0 0 30px #32cd32;
            }
            50% {
                color: #0000ff; /* Blue */
                text-shadow: 0 0 15px #0000ff, 0 0 30px #1e90ff;
            }
            75% {
                color: #ff4500; /* Orange */
                text-shadow: 0 0 15px #ff4500, 0 0 30px #ff6347;
            }
        }

        .converter-container {
            background: rgba(0, 0, 0, 0.7);
            border-radius: 15px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.5);
            display: inline-block;
            padding: 20px;
            margin-top: 20px;
            width: 90%;
            max-width: 400px;
            box-sizing: border-box;
        }

        select, input, button {
            padding: 10px;
            margin: 10px 0;
            width: 100%;
            max-width: 300px;
            border: none;
            border-radius: 5px;
            font-size: 1rem;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
        }

        select {
            background: #222;
            color: #fff;
            font-size: 1.2rem;
            border-radius: 10px;
            border: 2px solid #ff4500;
            padding: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        select option {
            background: #333;
            color: #fff;
            padding: 10px;
            font-size: 1rem;
        }

        select:hover, select:focus {
            background: #ff4500;
            color: #fff;
            border-color: #ffd700;
        }

        input {
            background: #f5f5f5;
            color: #333;
        }

        button {
            background: #ff4500;
            color: white;
            cursor: pointer;
            transition: background 0.3s ease;
        }

        button:hover {
            background: #e55d51;
        }

        .result {
            margin-top: 20px;
            font-size: 1.5rem;
            font-weight: bold;
            color: #fff;
            background: rgba(255, 255, 255, 0.2);
            padding: 10px;
            border-radius: 5px;
        }

        /* Dark mode styles */
        body.dark-mode {
            background-color: #121212;
            color: #fff;
        }

        body.dark-mode .header {
            background: rgba(0, 0, 0, 0.9);
            color: #ffd700;
            border-color: #ff4500;
        }

        body.dark-mode .converter-container {
            background: rgba(0, 0, 0, 0.9);
        }

        body.dark-mode button {
            background: #e55d51;
        }
    </style>
</head>
<body>
    <div class="header">
        <div class="header-text"></div>
        <button class="toggle-btn" onclick="toggleDarkMode()">☀️</button>
    </div>
    <div class="name">S H I H A B</div>

    <div class="converter-container">
        <select id="currency">
            <option value="USD">🪙 US Dollar (USD)</option>
            <option value="EUR">💶 Euro (EUR)</option>
            <option value="GBP">💷 British Pound (GBP)</option>
            <option value="INR">₹ Indian Rupee (INR)</option>
            <option value="JPY">💴 Japanese Yen (JPY)</option>
        </select>
        <input type="number" id="amount" placeholder="Enter amount" min="0">
        <button onclick="convertToBDT()">Convert</button>
        <div class="result" id="output">Enter details to see the result.</div>
    </div>

    <script>
        function toggleDarkMode() {
            document.body.classList.toggle('dark-mode');
            const icon = document.querySelector('.toggle-btn');
            if (document.body.classList.contains('dark-mode')) {
                icon.textContent = '🌚';  // Change icon to moon for dark mode
            } else {
                icon.textContent = '☀️';  // Change icon to sun for light mode
            }
        }

        function convertToBDT() {
            let amount = document.getElementById('amount').value;
            let currency = document.getElementById('currency').value;
            let output = document.getElementById('output');
            let conversionRate = 0;

            switch(currency) {
                case 'USD': conversionRate = 108; break;
                case 'EUR': conversionRate = 115; break;
                case 'GBP': conversionRate = 130; break;
                case 'INR': conversionRate = 1.5; break;
                case 'JPY': conversionRate = 0.75; break;
                default: conversionRate = 0; break;
            }

            let result = amount * conversionRate;

            if (currency === 'USD' || currency === 'EUR' || currency === 'GBP' || currency === 'INR' || currency === 'JPY') {
                output.innerHTML = `${amount} ${currency} = ${result.toFixed(2)} BDT`;
            } else {
                output.innerHTML = `${amount} ${currency} = ${result.toLocaleString('bn-BD')} BDT`;
            }
        }
    </script>
</body>
</html>
