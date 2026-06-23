# Weather-Dashboard-Project
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Weather Dashboard</title>

<style>
body{
    font-family: Arial, sans-serif;
    background:#f4f4f4;
    text-align:center;
    margin-top:50px;
}

.container{
    width:350px;
    margin:auto;
    background:white;
    padding:20px;
    border-radius:10px;
    box-shadow:0 2px 10px rgba(0,0,0,0.2);
}

input{
    width:70%;
    padding:10px;
}

button{
    padding:10px;
    cursor:pointer;
}

.weather{
    margin-top:20px;
}

h2{
    color:#333;
}
</style>
</head>
<body>

<div class="container">
    <h2>🌤 Weather Dashboard</h2>
    <input type="text" id="city" placeholder="Enter City">
    <button onclick="getWeather()">Search</button>
    <div class="weather">
        <h3 id="cityName"></h3>
        <p id="temp"></p>
        <p id="humidity"></p>
        <p id="wind"></p>
        <p id="condition"></p>
    </div>
</div>

<script>
async function getWeather(){

    const city =
    document.getElementById("city").value;

    const apiKey = "YOUR_API_KEY";

    const url =
    `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`;

    try{

        const response = await fetch(url);
        const data = await response.json();

        document.getElementById("cityName").innerText =
        data.name;

        document.getElementById("temp").innerText =
        "Temperature: " + data.main.temp + " °C";

        document.getElementById("humidity").innerText =
        "Humidity: " + data.main.humidity + "%";

        document.getElementById("wind").innerText =
        "Wind Speed: " + data.wind.speed + " m/s";

        document.getElementById("condition").innerText =
        "Condition: " + data.weather[0].description;

    }catch(error){

        alert("City not found!");
    }
}
</script>

</body>
</html>
