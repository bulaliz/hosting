<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sorpresa 4D para Mamá</title>
    <style>
        body, html {
            margin: 0; padding: 0;
            width: 100%; height: 100%;
            overflow: hidden;
            font-family: 'Arial', sans-serif;
            background-color: #1a1a1a; /* Fondo oscuro para resaltar el 3D */
            display: flex; justify-content: center; align-items: center;
        }

        /* --- CORTINA --- */
        #cortina {
            position: fixed; top: 0; left: 0;
            width: 100%; height: 100%;
            background: radial-gradient(circle, #ff4d4d, #b30000);
            display: flex; justify-content: center; align-items: center;
            z-index: 100;
            transition: transform 1.8s cubic-bezier(0.7, 0, 0.3, 1);
        }

        #cortina.abierta { transform: translateY(-100%); }

        #btn-abrir {
            padding: 20px 40px; font-size: 24px; cursor: pointer;
            border: none; border-radius: 50px; background: white;
            color: #b30000; font-weight: bold; box-shadow: 0 10px 20px rgba(0,0,0,0.3);
        }

        /* --- ESCENARIO 3D --- */
        .escenario {
            perspective: 800px; /* Profundidad */
            display: flex; flex-direction: column; align-items: center;
        }

        .texto {
            color: white; font-size: 30px; font-weight: bold;
            margin-top: 150px; opacity: 0;
            transition: 1s ease 1.5s;
            text-shadow: 0 0 15px #ff4d4d;
        }

        /* --- EL CORAZÓN 4D (Volumen + Rotación) --- */
        .corazon-4d {
            position: relative;
            width: 100px; height: 100px;
            transform-style: preserve-3d;
            animation: rotar4d 4s infinite linear;
        }

        /* Caras del corazón para dar volumen */
        .cara {
            position: absolute;
            width: 100px; height: 100px;
            background: #ff4d4d;
            transform-style: preserve-3d;
        }

        .cara::before, .cara::after {
            content: "";
            position: absolute;
            width: 100px; height: 100px;
            background: inherit;
            border-radius: 50%;
        }

        .cara::before { top: -50px; left: 0; }
        .cara::after { left: 50px; top: 0; }

        /* Posicionamiento de las caras para el efecto 3D */
        .cara.frontal { transform: translateZ(20px); background: #ff4d4d; }
        .cara.trasera { transform: translateZ(-20px) rotateY(180deg); background: #b30000; }
        .cara.relleno { transform: translateZ(0px) scale(1.05); background: #e60000; }

        /* Animación: Rotación (3D) + Pulsación (4ta Dimensión) */
        @keyframes rotar4d {
            0% { transform: rotateY(0deg) rotateX(0deg) scale(1); }
            50% { transform: rotateY(180deg) rotateX(20deg) scale(1.3); }
            100% { transform: rotateY(360deg) rotateX(0deg) scale(1); }
        }

        .visible { opacity: 1 !important; }
    </style>
</head>
<body>

    <div id="cortina">
        <button id="btn-abrir">¡TOCA PARA TU REGALO!</button>
    </div>

    <div class="escenario">
        <div class="corazon-4d" id="corazon">
            <div class="cara frontal"></div>
            <div class="cara trasera"></div>
            <div class="cara relleno"></div>
        </div>
        <div class="texto" id="texto">¡FELIZ DÍA DE LAS MADRES!</div>
    </div>

    <script>
        document.getElementById('btn-abrir').addEventListener('click', () => {
            document.getElementById('cortina').classList.add('abierta');
            document.getElementById('texto').classList.add('visible');
        });
    </script>

</body>
</html>
