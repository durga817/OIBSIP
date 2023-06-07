<!DOCTYPE html>
<html>
<head>
  <title>Temperature Converter</title>
  <style>
    /* Add your CSS styling here */
  </style>
</head>
<body align="center" bgcolor="pink">
  <h1>Temperature Converter</h1>

  <div>
    <label for="temperature">Temperature:</label>
    <input type="text" id="temperature" placeholder="Enter temperature" />
  </div>

  <div>
    <label for="unit">Unit:</label>
    <select id="unit">
      <option value="celsius">Celsius</option>
      <option value="fahrenheit">Fahrenheit</option>
      <option value="kelvin">Kelvin</option>
    </select>
  </div>

  <button onclick="convertTemperature()">Convert</button>

  <div>
    <h3>Converted Temperature:</h3>
    <p id="convertedTemperature"></p>
  </div>

  <script>
    function convertTemperature() {
      var temperatureInput = document.getElementById("temperature").value;
      var unitInput = document.getElementById("unit").value;
      var convertedTemperatureElement = document.getElementById("convertedTemperature");

      // Validate if temperatureInput is a number
      if (isNaN(temperatureInput)) {
        convertedTemperatureElement.textContent = "Invalid input. Please enter a valid number.";
        return;
      }

      var temperature = parseFloat(temperatureInput);
      var convertedTemperature;

      if (unitInput === "celsius") {
        convertedTemperature = convertCelsius(temperature);
      } else if (unitInput === "fahrenheit") {
        convertedTemperature = convertFahrenheit(temperature);
      } else if (unitInput === "kelvin") {
        convertedTemperature = convertKelvin(temperature);
      }

      convertedTemperatureElement.textContent = convertedTemperature + " " + unitInput;
    }

    function convertCelsius(temperature) {
      // Celsius to Fahrenheit conversion: F = (C * 9/5) + 32
      return (temperature * 9/5) + 32;
    }

    function convertFahrenheit(temperature) {
      // Fahrenheit to Celsius conversion: C = (F - 32) * 5/9
      return (temperature - 32) * 5/9;
    }

    function convertKelvin(temperature) {
      // Kelvin to Celsius conversion: C = K - 273.15
      // Kelvin to Fahrenheit conversion: F = (K - 273.15) * 9/5 + 32
      var celsius = temperature - 273.15;
      var fahrenheit = (temperature - 273.15) * 9/5 + 32;
      return celsius + "°C / " + fahrenheit + "°F";
    }
  </script>
</body>
</html>
