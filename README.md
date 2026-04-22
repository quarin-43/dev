<!DOCTYPE html>
<html>
<head>
  <title>Density Simulator</title>
  <style>
    body {
      font-family: Arial;
      text-align: center;
      background: #eef;
    }
    .box {
      width: 200px;
      height: 200px;
      margin: 20px auto;
      background: lightblue;
      position: relative;
      border: 2px solid #333;
    }
    .object {
      width: 50px;
      height: 50px;
      background: red;
      position: absolute;
      left: 75px;
      transition: top 0.5s;
    }
  </style>
</head>
<body>

<h2>Density Simulator</h2>

<label>Mass (kg):</label>
<input type="range" id="mass" min="1" max="100" value="50"><br>

<label>Volume (L):</label>
<input type="range" id="volume" min="1" max="100" value="50"><br>

<p id="output"></p>

<div class="box">
  <div class="object" id="object"></div>
</div>

<script>
function update() {
  let mass = document.getElementById("mass").value;
  let volume = document.getElementById("volume").value;

  let density = mass / volume;

  let output = document.getElementById("output");
  output.innerHTML = "Density: " + density.toFixed(2) + " kg/L";

  let obj = document.getElementById("object");

  // Water density = 1 kg/L
  if (density > 1) {
    obj.style.top = "130px"; // sinks
  } else {
    obj.style.top = "10px"; // floats
  }
}

document.getElementById("mass").oninput = update;
document.getElementById("volume").oninput = update;

update();
</script>

</body>
</html>