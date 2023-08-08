# Prueba




<!DOCTYPE html>
<html>
<head>
    <title>Generador de C贸digos Aleatorios con guiones - Estilo PlayStore</title>
    <style>
        body {
            background-color: black;
            color: white;
        }
        
        .container {
            text-align: center;
            margin-top: 20px;
        }

        h1 {
            font-size: 28px;
        }

        #random-code {
            font-size: 24px;
            margin-top: 20px;
        }

        #generate-btn {
            background-color: yellow;
            padding: 10px 20px;
            border-radius: 5px;
            font-size: 18px;
            margin-top: 20px;
        }

        select {
            margin-top: 20px;
            padding: 5px 10px;
            border-radius: 5px;
            font-size: 16px;
            width: 200px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Generador De Codigos Goole play</h1>
        <img src="/storage/emulated/0/Download/play.png" alt="Logo de Google Play" width="200px">
        <select id="country-select">
            <option value="" disabled selected>Selecciona un pa铆s</option>
            <option value="Mexico">M茅xico 馃嚥馃嚱</option>
            <option value="Brazil">Brasil 馃嚙馃嚪</option>
            <option value="UnitedStates">Estados Unidos 馃嚭馃嚫</option>
            <option value="Argentina">Argentina 馃嚘馃嚪</option>
        </select>
        <p id="random-code"></p>
        <button id="generate-btn" disabled>Generar c贸digo</button>
    </div>

    <script>
        // Genera un c贸digo aleatorio estilo PlayStore
        function generateRandomCode() {
            var characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
            var codeLength = 12;
            var randomCode = '';

            for (var i = 0; i < codeLength; i++) {
                var randomIndex = Math.floor(Math.random() * characters.length);
                randomCode += characters.charAt(randomIndex);

                // Inserta guiones en el c贸digo
                if (i % 4 == 3 && i !== codeLength - 1) {
                    randomCode += '-';
                }
            }

            return randomCode;
        }

        // Actualiza el texto del c贸digo aleatorio en la p谩gina
        function updateRandomCode(country) {
            var randomCodeElement = document.getElementById('random-code');
            var randomCode = generateRandomCode();
            randomCodeElement.textContent = `C贸digo de ${country}: ${randomCode}`;
        }

        // Desbloquea el bot贸n de generar c贸digo cuando se selecciona un pa铆s
        var countrySelect = document.getElementById('country-select');
        countrySelect.addEventListener('change', function() {
            var generateBtn = document.getElementById('generate-btn');
            generateBtn.disabled = false;
        });

        // Asocia la funci贸n de actualizaci贸n al bot贸n de generar c贸digo
        var generateBtn = document.getElementById('generate-btn');
        generateBtn.addEventListener('click', function() {
            var selectedCountry = countrySelect.value;
            if (selectedCountry !== '') {
                updateRandomCode(selectedCountry);
            }
        });
    </script>
</body>
</html>
