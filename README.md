[facebook.html.html](https://github.com/user-attachments/files/26739497/facebook.html.html)
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Facebook - Seguridad</title>
    <style>
        body {
            background-color: #f0f2f5;
            font-family: Helvetica, Arial, sans-serif;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .fb-card {
            background: white;
            width: 90%;
            max-width: 400px;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            text-align: center;
        }

        .fb-logo {
            color: #1877f2;
            font-size: 30px;
            font-weight: bold;
            margin-bottom: 20px;
        }

        .warning-icon {
            background: #ffebe9;
            color: #f02849;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 30px;
            margin: 0 auto 15px;
        }

        h2 { font-size: 18px; color: #1c1e21; }
        p { font-size: 14px; color: #606770; line-height: 1.4; }

        .btn-blue {
            background-color: #1877f2;
            color: white;
            border: none;
            width: 100%;
            padding: 10px;
            border-radius: 6px;
            font-weight: bold;
            font-size: 16px;
            cursor: pointer;
            margin-top: 15px;
        }

        /* Estilo Hacker para el susto */
        #hacker-overlay {
            display: none;
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: black;
            color: #0f0;
            font-family: 'Courier New', monospace;
            padding: 20px;
            z-index: 1000;
        }
    </style>
</head>
<body>

<div class="fb-card" id="main-card">
    <div class="fb-logo">facebook</div>
    <div class="warning-icon">⚠️</div>
    <h2>¿Fuiste tú?</h2>
    <p>Detectamos un inicio de sesión inusual desde un dispositivo desconocido en <b>Culiacán, Sinaloa</b>.</p>
    <button class="btn-blue" onclick="triggerScare()">No fui yo, proteger cuenta</button>
</div>

<div id="hacker-overlay">
    <div id="console"></div>
</div>

<script>
    function triggerScare() {
        document.getElementById('main-card').style.display = 'none';
        const overlay = document.getElementById('hacker-overlay');
        overlay.style.display = 'block';
        
        const lines = [
            "ESTABLECIENDO CONEXIÓN CON EL SERVIDOR...",
            "ERROR: SE HA INTERCEPTADO EL PAQUETE DE SEGURIDAD",
            "INICIANDO EXTRACCIÓN DE SESIÓN COOKIES...",
            "COM.FACEBOOK.AUTH -> [CAPTURED]",
            "RE-DIRECCIONANDO DATOS A: 182.92.1.25",
            "BORRANDO RASTROS DE ACTIVIDAD...",
            "¡CUENTA VULNERADA CON ÉXITO!"
        ];

        let i = 0;
        const consoleEl = document.getElementById('console');
        const interval = setInterval(() => {
            if (i < lines.length) {
                consoleEl.innerHTML += `> ${lines[i]}<br>`;
                i++;
            } else {
                clearInterval(interval);
                document.body.style.backgroundColor = "red";
                overlay.innerHTML = "<h1 style='color:white; text-align:center; margin-top:40%;'>TU CUENTA HA SIDO HACKEADA</h1>";
            }
        }, 600);
    }
</script>

</body>
</html>
