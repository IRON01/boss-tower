#boss-tower
<!DOCTYPE html><html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Boss Tower Game</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: #1a1a2e;
            color: white;
            text-align: center;
            font-family: Arial, sans-serif;
        }
        canvas {
            display: block;
            background-color: #001f3f;
        }
        .ui {
            position: absolute;
            top: 10px;
            left: 50%;
            transform: translateX(-50%);
        }
    </style>
</head>
<body>
    <div class="ui">
        <h2>Floor: <span id="floor">1</span></h2>
        <h3>Boss Health: <span id="health">100</span></h3>
        <button onclick="attackBoss()">Attack</button>
        <button onclick="nextFloor()">Next Floor</button>
    </div>
    <canvas id="gameCanvas"></canvas>
    <script>
        const canvas = document.getElementById("gameCanvas");
        const ctx = canvas.getContext("2d");
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;let floor = 1;
    let bossHealth = 100;
    
    function updateUI() {
        document.getElementById("floor").innerText = floor;
        document.getElementById("health").innerText = bossHealth;
    }

    function attackBoss() {
        bossHealth -= 10;
        if (bossHealth <= 0) {
            alert("Boss defeated! Move to the next floor.");
        }
        updateUI();
    }

    function nextFloor() {
        if (bossHealth > 0) {
            alert("Defeat the boss first!");
            return;
        }
        floor++;
        bossHealth = 100 * floor;
        updateUI();
    }

    function draw() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        ctx.fillStyle = "white";
        ctx.font = "30px Arial";
        ctx.fillText("Boss Fight!", canvas.width / 2 - 80, canvas.height / 2);
        requestAnimationFrame(draw);
    }
    draw();
</script>

</body>
</html>
