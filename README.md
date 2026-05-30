<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Smart Farm Dashboard</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial, sans-serif;
}

body{
    background-image:url('https://images.unsplash.com/photo-1500937386664-56d1dfef3854');
    background-size:cover;
    background-position:center;
    background-repeat:no-repeat;
    min-height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
}

.overlay{
    background:rgba(0,0,0,0.5);
    width:100%;
    min-height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
}

.container{
    width:85%;
    max-width:900px;
}

.bluetooth{
    text-align:center;
    margin-bottom:30px;
}

.bluetooth button{
    background:#2196F3;
    color:white;
    border:none;
    padding:15px 35px;
    border-radius:10px;
    font-size:18px;
    cursor:pointer;
}

.bluetooth button:hover{
    background:#1976D2;
}

.cards{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:20px;
}

.card{
    background:rgba(255,255,255,0.9);
    padding:30px;
    border-radius:15px;
    text-align:center;
    box-shadow:0 0 15px rgba(0,0,0,0.3);
}

.card h2{
    margin-bottom:15px;
    color:#2E7D32;
}

.value{
    font-size:35px;
    font-weight:bold;
    color:#333;
}

@media(max-width:768px){
    .cards{
        grid-template-columns:1fr;
    }
}
</style>
</head>

<body>

<div class="overlay">

<div class="container">

    <div class="bluetooth">
        <button onclick="connectBluetooth()">
            🔵 Connect Bluetooth
        </button>
    </div>

    <div class="cards">

        <div class="card">
            <h2>🌡 Temperature</h2>
            <div class="value" id="temp">25°C</div>
        </div>

        <div class="card">
            <h2>💧 Humidity</h2>
            <div class="value" id="humidity">60%</div>
        </div>

        <div class="card">
            <h2>🌱 Soil Moisture</h2>
            <div class="value" id="soil">45%</div>
        </div>

    </div>

</div>

</div>

<script>

async function connectBluetooth() {
    try {
        const device = await navigator.bluetooth.requestDevice({
            acceptAllDevices: true
        });

        alert("Connected to: " + device.name);
    }
    catch(error){
        console.log(error);
        alert("Bluetooth Connection Failed");
    }
}

// بيانات تجريبية
setInterval(() => {
    document.getElementById("temp").innerHTML =
        (20 + Math.floor(Math.random()*10)) + "°C";

    document.getElementById("humidity").innerHTML =
        (50 + Math.floor(Math.random()*30)) + "%";

    document.getElementById("soil").innerHTML =
        (30 + Math.floor(Math.random()*50)) + "%";
},3000);

</script>

</body>
</html>
