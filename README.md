<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50 px;
            background-color: #f5f5f5;
        }

        .calculator {
            width: 240px; 
            border: 1px solid #ccc;
            padding: 10px;
            display: inline-block;
            background-color: #b3c0c7;
            border-radius: 10px;
        }

        .calculator-screen {
            width: 94%;
            height: 50px;
            background-color: #e3edf3;
            border: none;
            text-align: right;
            padding-right: 10px;
            font-size: 24px;
            margin-bottom: 10px;
            border-radius: 5px;
            box-shadow: inset 0 0 5px #888;
        }

        .calculator-keys {
            width: 100%;
        }

        button {
            width: 50px;
            height: 50px;
            margin: 3px;
            font-size: 20px;
            border: none;
            cursor: pointer;
            border-radius: 5px;
            box-shadow: 0 2px #888;
        }

        button:active {
            box-shadow: none;
            transform: translateY(2px);
        }

        .operator {
            background-color: #8b9298;
            color: white;
        }

        .number-button {
            background-color: #e6e8ea;
        }

        .equal-sign {
            background-color: #f3931e;
            color: white;
            height: 50px;
            box-shadow: 0 2px #888;
        }

        .clear-button {
            background-color: #999ea1;
            color: white;
        }

        .calculator-row {
            display: flex;
            justify-content: space-between;
        }

        .wide-button {
            width:84px;
        }

        .decimal-button {
            width: 50px;
            height: 50px;
        }
    </style>
</head>
<body>

    <h2>Xây dựng trang web mô phỏng Calculator </h2>

    <div class="calculator">
        <input type="text" class="calculator-screen" id="screen" value="" disabled>
        <div class="calculator-keys">
            <div class="calculator-row">
                <button class="clear-button" onclick="clearScreen()">MC</button>
                <button class="operator" onclick="addToMemory()">M+</button>
                <button class="operator" onclick="subtractFromMemory()">M-</button>
                <button class="operator" onclick="recallMemory()">RM</button>
            </div>
            <div class="calculator-row">
                <button class="number-button" onclick="inputKey('7')">7</button>
                <button class="number-button" onclick="inputKey('8')">8</button>
                <button class="number-button" onclick="inputKey('9')">9</button>
                <button class="operator" onclick="inputKey('/')">÷</button>
            </div>
            <div class="calculator-row">
                <button class="number-button" onclick="inputKey('4')">4</button>
                <button class="number-button" onclick="inputKey('5')">5</button>
                <button class="number-button" onclick="inputKey('6')">6</button>
                <button class="operator" onclick="inputKey('*')">×</button>
            </div>
            <div class="calculator-row">
                <button class="number-button" onclick="inputKey('1')">1</button>
                <button class="number-button" onclick="inputKey('2')">2</button>
                <button class="number-button" onclick="inputKey('3')">3</button>
                <button class="operator" onclick="inputKey('+')">+</button>
            </div>
            <div class="calculator-row">
                <button class="operator wide-button" onclick="inputKey('^2')">x²</button> 
                <button class="operator wide-button" onclick="inputKey('√')">√</button> 
                <button class="operator" onclick="inputKey('-')">−</button>  
            </div>
            <div class="calculator-row">
                <button class="number-button wide-button" onclick="inputKey('0')">0</button>
                <button class="decimal-button" onclick="inputKey('.')">.</button>
                <button class="equal-sign wide-button" onclick="calculate()">=</button>
            </div>
        </div>
    </div>

    <script>
        let memory = 0;

       
        function inputKey(key) {
            document.getElementById("screen").value += key;
        }

      
        function calculate() {
            let screen = document.getElementById("screen").value;
            
            try {
                if (screen.includes('^2')) {
                   
                    let base = parseFloat(screen.replace('^2', ''));
                    document.getElementById("screen").value = Math.pow(base, 2);
                } else if (screen.includes('√')) {
                   
                    let number = parseFloat(screen.replace('√', ''));
                    document.getElementById("screen").value = Math.sqrt(number);
                } else {
                  
                    document.getElementById("screen").value = eval(screen);
                }
            } catch (e) {
                document.getElementById("screen").value = "Error"; 
            }
        }

       
        function clearScreen() {
            document.getElementById("screen").value = "";
        }

    
        function addToMemory() {
            let screen = document.getElementById("screen").value;
            memory += parseFloat(screen);
        }

       
        function subtractFromMemory() {
            let screen = document.getElementById("screen").value;
            memory -= parseFloat(screen);
        }

        
        function recallMemory() {
            document.getElementById("screen").value = memory;
        }
    </script>

</body>
</html>
