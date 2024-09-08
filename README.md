<!DOCTYPE html>
<html>
<head>
    <title>Ma Page Web</title>
</head>
<body>
    <h1>Bienvenue sur ma page web !</h1>
    <p>Contrôlez votre Arduino via cette page.</p>
    <button onclick="sendCommand('A')">Activer Sortie 1</button>
    <button onclick="sendCommand('B')">Activer Sortie 2</button>
    <input type="range" min="0" max="255" id="slider" onchange="sendSliderValue()">
    <script>
        function sendCommand(command) {
            fetch('http://adresse-ip-de-votre-arduino/' + command)
            .then(response => response.text())
            .then(data => console.log(data));
        }

        function sendSliderValue() {
            var value = document.getElementById('slider').value;
            fetch('http://adresse-ip-de-votre-arduino/slider/' + value)
            .then(response => response.text())
            .then(data => console.log(data));
        }
    </script>
</body>
</html>
