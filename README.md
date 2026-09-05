# prl-agv-simulator-Mostrar-m-s-l-neas
Simulador gamificado de PRL y flotas autónomas para entornos industriales. Mostrar más líneas
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simulador PRL & Flotas Autónomas - Ford Almussafes</title>
    <style>
        body {
            background-color: #003366;
            color: #fff;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            padding: 20px;
            margin: 0;
            font-size: 18px;
        }
        .container {
            max-width: 1050px;
            margin: 0 auto;
            background-color: #004080;
            padding: 35px;
            border: 3px solid #e6b800;
            border-radius: 10px;
            box-shadow: 0 6px 20px rgba(0,0,0,0.4);
        }
        h1 {
            font-size: 30px;
            text-align: center;
            color: #e6b800;
            margin-bottom: 25px;
        }
        h2 {
            font-size: 24px;
            text-align: center;
            color: #e6b800;
        }
        h3 {
            font-size: 22px;
            color: #e6b800;
        }
        .hidden {
            display: none;
        }
        button {
            background-color: #e6b800;
            color: #003366;
            border: none;
            padding: 14px 26px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            margin: 10px;
            border-radius: 6px;
            transition: 0.2s;
        }
        button:hover {
            background-color: #ffcc00;
        }
        input[type="text"] {
            padding: 14px;
            font-size: 18px;
            border: none;
            border-radius: 6px;
            margin-bottom: 12px;
            width: calc(100% - 28px);
            box-sizing: border-box;
        }
        .module-card {
            background-color: #002244;
            border: 2px solid #e6b800;
            padding: 20px 25px;
            margin-bottom: 18px;
            border-radius: 8px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
        }
        .module-info {
            flex: 1;
            min-width: 320px;
        }
        .module-info strong {
            font-size: 21px;
        }
        .module-info span {
            font-size: 16px;
        }
        .module-actions {
            display: flex;
            gap: 12px;
            align-items: center;
        }
        .btn-pptx {
            background-color: #00509e;
            color: #fff;
            border: 2px solid #e6b800;
            text-decoration: none;
            padding: 12px 18px;
            border-radius: 6px;
            font-weight: bold;
            font-size: 16px;
            display: inline-block;
        }
        .btn-pptx:hover {
            background-color: #0066cc;
            color: #fff;
        }
        .question-box {
            background-color: #002244;
            padding: 25px;
            border-left: 6px solid #e6b800;
            border-radius: 6px;
            font-size: 22px;
            line-height: 1.4;
            margin-bottom: 25px;
        }
        .option {
            background-color: #00509e;
            padding: 18px 20px;
            margin-bottom: 14px;
            border-radius: 6px;
            font-size: 19px;
            line-height: 1.35;
        }
        .hub-team-row {
            display: grid;
            grid-template-columns: 1fr auto;
            align-items: center;
            background: #001a33;
            padding: 14px 20px;
            margin-bottom: 10px;
            border-radius: 6px;
            border: 1px solid #00509e;
            gap: 15px;
            width: 100%;
            box-sizing: border-box;
            font-size: 19px;
        }
        .vote-row {
            display: grid;
            grid-template-columns: 1fr auto;
            align-items: center;
            background-color: #002244;
            padding: 16px 20px;
            margin-bottom: 12px;
            border: 2px solid #e6b800;
            border-radius: 6px;
            gap: 15px;
            width: 100%;
            box-sizing: border-box;
            font-size: 20px;
        }
        .vote-row select {
            width: 160px;
            justify-self: end;
        }
        select {
            padding: 12px;
            font-size: 18px;
            font-weight: bold;
        }
        .ranking-bar {
            background-color: #002244;
            width: 100%;
            height: 24px;
            border-radius: 12px;
            margin-top: 8px;
            border: 1px solid #00509e;
        }
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #e6b800;
            font-size: 19px;
        }
        .top-bar {
            display: flex;
            justify-content: space-between;
            background: #002244;
            padding: 14px 25px;
            border-radius: 6px;
            margin-bottom: 25px;
            border: 2px solid #e6b800;
            align-items: center;
            flex-wrap: wrap;
            gap: 15px;
        }
        .badge-stat {
            background: #00509e;
            padding: 8px 16px;
            border-radius: 6px;
            font-weight: bold;
            border: 1px solid #e6b800;
            font-size: 18px;
        }
        @keyframes flashRed {
            0% { background-color: #00509e; }
            50% { background-color: #dc3545; }
            100% { background-color: #00509e; }
        }
        .flash-warning {
            animation: flashRed 0.5s infinite;
        }
        .event-banner {
            background-color: #5c1d1d;
            border: 2px dashed #ff4d4d;
            padding: 15px;
            border-radius: 6px;
            margin-bottom: 20px;
            text-align: center;
            font-weight: bold;
            color: #ffcccc;
            font-size: 20px;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>🚨 SIMULADOR PRL & FLOTAS AUTÓNOMAS - FORD ALMUSSAFES 🚨</h1>
    
    <div id="screen-hub">
        <div style="background-color: #002244; padding: 20px; border-radius: 8px; margin-bottom: 25px; border: 2px solid #e6b800;">
            <h3>📋 Registro de Equipos y Presupuesto de Planta</h3>
            <p style="text-align:center; font-size: 18px;">Se requiere un mínimo de 2 equipos en competición para iniciar el turno.</p>
            <label for="teamName">Nombre del equipo</label>
            <input type="text" id="teamName" placeholder="Ej. Equipo Turno Noche / Carrocerías">
            <div style="text-align: center;">
                <button onclick="addTeam()">Añadir Equipo</button>
                <button onclick="clearTeams()" style="background-color: #ff4d4d; color: #fff;">Reiniciar Competición</button>
            </div>
            <ul id="teamList" style="list-style:none; padding:0; margin-top: 20px;"></ul>
        </div>

        <h2>📚 Itinerario de Módulos Oficiales (Empieza por M0)</h2>
        <div id="modulesContainer"></div>

        <div style="text-align: center; margin-top: 35px; margin-bottom: 25px; background: #002244; padding: 25px; border-radius: 8px; border: 2px solid #e6b800;">
            <h3 style="color: #e6b800; margin-top: 0; font-size: 24px;">🏁 Examen Final de Consolidación</h3>
            <p style="font-size: 17px; color: #ccc; margin-bottom: 20px;">Pon a prueba a los equipos recorriendo los 10 módulos de forma consecutiva con corrección inmediata.</p>
            <button onclick="startShiftMode()" style="background-color: #28a745; color: #fff; font-size: 20px; padding: 18px 35px;">⚡ EVALUACIÓN FINAL - CAJA NEGRA COMPLETA (10 Retos M0-M9)</button>
        </div>
    </div>

    <!-- Pantalla de Pregunta -->
    <div id="screen-game" class="hidden">
        <div class="top-bar">
            <span id="gameModuleTitle" style="font-weight:bold; color:#e6b800; font-size:20px;"></span>
            <div>
                <span class="badge-stat" id="countdown">⏱ 40</span>
                <span class="badge-stat" id="questionCounter">Reto 1/3</span>
            </div>
            <button onclick="returnToHub()" style="padding: 8px 18px; margin:0; font-size: 16px;">⬅ Volver al Menú</button>
        </div>
        
        <div id="eventBannerContainer"></div>
        <h2 id="blockTitle" style="font-size: 25px; margin-bottom: 15px;"></h2>
        <div id="questionText" class="question-box"></div>
        <div id="optionsContainer"></div>
        
        <hr style="border-color: #00509e; margin: 35px 0;">
        <h3 style="color:#fff; font-size: 23px;">Panel de Decisión de los Equipos</h3>
        <div id="teamVotes"></div>
        <div style="text-align: center;"><button id="actionBtn" onclick="resolveTurn()" style="font-size: 20px; padding: 16px 32px;">Validar Respuesta ➔</button></div>
    </div>

    <!-- Pantalla de Feedback Inmediato por Reto con Clasificación en Directo -->
    <div id="screen-turn-feedback" class="hidden">
        <div class="top-bar">
            <span style="font-weight:bold; color:#e6b800; font-size:20px;">🔍 CORRECCIÓN INMEDIATA & CLASIFICACIÓN</span>
            <span class="badge-stat" id="feedbackProgressCounter">Reto 1/3</span>
        </div>
        
        <div id="turnFeedbackContainer"></div>
        
        <div style="text-align: center; margin-top: 35px;">
            <button id="turnNextBtn" onclick="proceedAfterTurn()" style="font-size: 20px; padding: 16px 32px; background-color: #28a745; color: #fff;">Siguiente Reto ➔</button>
        </div>
    </div>

    <!-- Pantalla de Clasificación Final -->
    <div id="screen-resolution" class="hidden">
        <h2 style="font-size: 28px; margin-bottom: 20px;">🏆 RESULTADO FINAL DEL BLOQUE</h2>
        <div style="background:#001a33; padding:25px; border-radius:8px; margin-bottom:25px; text-align:center; font-size:22px; border: 2px solid #e6b800;">
            <p style="margin:0; color:#28a745;">¡Bloque completado con éxito! Se han consolidado los presupuestos de planta y niveles de seguridad.</p>
        </div>
        
        <h2 style="font-size: 26px;">📊 CLASIFICACIÓN GENERAL DEFINITIVA</h2>
        <div id="liveRanking"></div>
        <div style="text-align: center; margin-top: 30px;"><button onclick="returnToHub()" style="font-size: 20px; padding: 16px 32px;">Volver al Menú Principal ➔</button></div>
    </div>
</div>

<script>
    const modulesData = [
        { 
            id: "M0", 
            title: "M0. Introducción y conceptos básicos", 
            pptx: "borrador_formación agv_v.2 _27_08_2026.pptx", 
            desc: "Argumentos de inversión, estabilidad operativa, trazabilidad y artículo 29 LPRL.", 
            bank: [
                { 
                    title: "Justificación de la inversión en automatización", 
                    text: "En una reunión se plantea automatizar un transporte interno que se realiza continuamente entre dos puntos de la planta desde hace años. ¿Cuál sería el argumento más sólido para justificar la inversión?", 
                    options: [
                        { text: "Reducir diferencias entre ejecuciones de una misma operación.", isCorrect: true, feedback: "La automatización aporta estabilidad y repetibilidad operativa frente a la variabilidad humana.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Permitir que los vehículos circulen a mayor velocidad media.", isCorrect: false, feedback: "Los límites de velocidad están regidos estrictamente por seguridad industrial.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Eliminar completamente los errores que puedan producirse.", isCorrect: false, feedback: "Ningún sistema elimina al 100% el margen de error o incidencias imprevistas.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Sustituir cualquier supervisión humana durante la operación.", isCorrect: false, feedback: "La supervisión técnica humana sigue siendo imprescindible para vigilar los procesos.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Consistencia operativa entre turnos", 
                    text: "Dos operarios realizan exactamente la misma tarea logística y obtienen resultados diferentes dependiendo del turno. ¿Por qué una empresa suele estudiar alternativas automatizadas?", 
                    options: [
                        { text: "Porque los equipos automáticos producen más unidades siempre.", isCorrect: false, feedback: "El objetivo principal es la repetibilidad y estabilidad, no la sobreproducción ciega.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Porque ayudan a mantener resultados más consistentes.", isCorrect: true, feedback: "La automatización minimiza la variabilidad entre turnos y ejecuciones estandarizando procesos.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Porque dejan de necesitar mantenimiento preventivo periódico.", isCorrect: false, feedback: "Los equipos automatizados exigen un mantenimiento preventivo riguroso.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Porque permiten eliminar todos los procedimientos existentes.", isCorrect: false, feedback: "Los procedimientos de trabajo y seguridad siguen siendo plenamente vigentes.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                {
                    title: "Trazabilidad y control operativo en flotas autónomas",
                    text: "¿Qué ventaja principal aporta la trazabilidad digital integrada en los sistemas de gestión de flotas AGV/AMR?",
                    options: [
                        { text: "Registrar de forma continua la posición, misiones e incidencias de cada vehículo en tiempo real.", isCorrect: true, feedback: "La trazabilidad digital aporta visibilidad completa de la operativa y el histórico de eventos.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Eximir a la planta de realizar controles físicos de inventario anual.", isCorrect: false, feedback: "Los inventarios físicos periódicos siguen formando parte del control logístico.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Sustituir por completo los registros documentales del departamento de calidad.", isCorrect: false, feedback: "Los sistemas de calidad operan de manera complementaria con los datos telemétricos.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Evitar el uso de redes inalámbricas corporativas para la transmisión de datos.", isCorrect: false, feedback: "La red Wi-Fi industrial es imprescindible para la comunicación con el servidor.", points: -10000, secPenalty: 8, type: "wrong" }
                    ]
                },
                {
                    title: "Escalabilidad de flujos y absorción de picos productivos",
                    text: "Una planta industrial experimenta incrementos puntuales en la cadencia de montaje de vehículos. ¿Cómo contribuye un sistema logístico automatizado a este escenario?",
                    options: [
                        { text: "Absorbiendo el incremento de misiones de transporte sin necesidad de alterar linealmente la plantilla de operarios manuales.", isCorrect: true, feedback: "La automatización permite escalar el suministro logístico manteniendo la estabilidad de los procesos.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Aumentando la velocidad máxima de circulación de los robots por encima de los límites de seguridad.", isCorrect: false, feedback: "La velocidad está limitada rígidamente por normativa y mapas de seguridad.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Modificando de forma autónoma el diseño físico de las líneas de montaje de carrocerías.", isCorrect: false, feedback: "El layout de línea es estático y no puede ser modificado por los vehículos logísticos.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Eliminando la necesidad de planificar las entregas de componentes a pie de línea.", isCorrect: false, feedback: "La planificación y secuenciación JIT siguen siendo críticas para el funcionamiento.", points: -10000, secPenalty: 8, type: "wrong" }
                    ]
                },
                { 
                    title: "Manipulación de sensores y artículo 29 LPRL", 
                    text: "AGV 3501 parado. Un operario observa que un sensor lateral genera paradas frecuentes. Durante varios días coloca siempre la misma caja delante para 'engañar' la detección porque así evita interrupciones. No ha ocurrido ningún incidente. ¿Cuál es la valoración más adecuada?", 
                    options: [
                        { text: "La medida puede aceptarse mientras no aparezcan daños ni reclamaciones.", isCorrect: false, feedback: "Anular protecciones activa riesgos graves de atropello o colisión.", points: -15000, secPenalty: 15, type: "wrong" },
                        { text: "El problema principal es que aumenta el tiempo de mantenimiento correctivo.", isCorrect: false, feedback: "El verdadero problema es la quiebra de la seguridad activa de las personas.", points: -12000, secPenalty: 10, type: "wrong" },
                        { text: "La actuación elimina una protección prevista por el sistema y modifica las condiciones seguras de uso.", isCorrect: true, feedback: "Anular dispositivos de seguridad vulnera el artículo 29 de la LPRL y expone a accidentes graves.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "La decisión podría ser válida si se informa al responsable al finalizar el turno.", isCorrect: false, feedback: "Ningún operario tiene autoridad para anular protecciones de seguridad de manera informal.", points: -15000, secPenalty: 15, type: "wrong" }
                    ] 
                }
            ]
        },
        { 
            id: "M1", 
            title: "1. Tipos de equipos y aplicaciones", 
            pptx: "borrador_formación agv_v.2 _27_08_2026.pptx", 
            desc: "AGC Mouse, Tugger Line, Unit Load y Forklift Line en plantas de Ford.", 
            bank: [
                { 
                    title: "Ventaja principal de tractora autónoma", 
                    text: "Una tractora autónoma realiza el suministro de materiales arrastrando varios carros en una sola misión. ¿Cuál es la principal ventaja de este sistema?", 
                    options: [
                        { text: "Permite mover varias cargas durante un único recorrido.", isCorrect: true, feedback: "Las tractoras optimizan el transporte al desplazar convoys completos de carros por misión.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Facilita reducir la longitud total de los pasillos.", isCorrect: false, feedback: "Los pasillos de la nave mantienen sus dimensiones estructurales constructivas.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Disminuye la necesidad de puntos de carga adicionales.", isCorrect: false, feedback: "Las estaciones de carga y baterías se dimensionan por el tamaño de la flota.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Elimina la necesidad de coordinar entregas posteriores.", isCorrect: false, feedback: "La secuenciación y coordinación JIT siguen siendo indispensables en montaje.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Identificación de vehículo de perfil bajo", 
                    text: "Observas un vehículo que se introduce por debajo de un carro, lo eleva ligeramente y lo transporta hasta otro destino. ¿De qué tipo de equipo se trata?", 
                    options: [
                        { text: "Vehículo de horquillas para almacenamiento en altura.", isCorrect: false, feedback: "Las carretillas de horquilla disponen de mástil frontal, no de plataforma baja.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Plataforma AGC utilizada para arrastre o elevación.", isCorrect: true, feedback: "Los AGV de perfil bajo tipo Mouse se deslizan bajo los carros para engancharlos y moverlos.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Tractora destinada al movimiento de convoyes completos.", isCorrect: false, feedback: "Las tractoras arrastran carros enganchados por enganche posterior.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Robot autónomo diseñado para operaciones de limpieza.", isCorrect: false, feedback: "La limpieza industrial se asigna a robots específicos tipo Kärcher.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Efecto inercial en remolcados (Tugger Train)", 
                    text: "Durante una maniobra un compañero solo observa la cabeza de una tractora y no los remolques posteriores. ¿Qué aspecto puede estar pasando por alto?", 
                    options: [
                        { text: "El comportamiento independiente de los últimos carros.", isCorrect: true, feedback: "Los remolcados amplían en curvas la trazada del tractor, exigiendo precaución lateral.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "La autonomía eléctrica disponible para la misión.", isCorrect: false, feedback: "La autonomía del tractor se monitoriza por telemetría central.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "La cobertura inalámbrica del circuito de trabajo.", isCorrect: false, feedback: "La cobertura Wi-Fi es una variable de infraestructura IT de planta.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "La comunicación entre PLC y gestor de flota.", isCorrect: false, feedback: "Es un parámetro del sistema de control centralizado.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Almacenamiento en altura por niveles", 
                    text: "Una zona necesita almacenar contenedores en diferentes niveles de estantería. ¿Qué solución encaja mejor con esa necesidad?", 
                    options: [
                        { text: "Plataforma Mouse para transporte horizontal de carros.", isCorrect: false, feedback: "Las plataformas Mouse operan a ras de suelo sin capacidad de apilamiento vertical.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Tractora diseñada para movimientos entre líneas.", isCorrect: false, feedback: "Las tractoras mueven carros horizontales en convoy, no apilan en alturas de racks.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "AGV de horquillas para manipulación en altura.", isCorrect: true, feedback: "Los AGVs Forklift con mástil están diseñados específicamente para estibar palés en altura.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Robot de limpieza para recorridos repetitivos internos.", isCorrect: false, feedback: "Los robots de limpieza no manipulan mercancías en estanterías.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Valoración de tractora para carro individual", 
                    text: "Un responsable propone utilizar una tractora para mover únicamente un carro individual. ¿Qué valoración harías?", 
                    options: [
                        { text: "Puede hacerse aunque quizá no aproveche sus capacidades.", isCorrect: true, feedback: "Es técnicamente posible, pero ineficiente al desaprovechar la alta capacidad de arrastre.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Es la solución más eficiente para cualquier operación.", isCorrect: false, feedback: "Para cargas unitarias individuales existen plataformas Mouse o Unit Load.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Permite reducir automáticamente todos los recorridos.", isCorrect: false, feedback: "La longitud de los recorridos depende del layout físico, no del vehículo.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Resulta obligatoria cuando existe tráfico compartido.", isCorrect: false, feedback: "Ninguna normativa obliga a sobredimensionar el equipo de transporte.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                }
            ]
        },
        { 
            id: "M2", 
            title: "2. Tecnologías de navegación y guiado. AGV vs AMR", 
            pptx: "borrador_formación agv_v.2 _27_08_2026.pptx", 
            desc: "Diferencias AGV vs AMR, SLAM, cinta magnética, QR, láser y capas de movimiento.", 
            bank: [
                { 
                    title: "Diferencia fundamental AGV vs AMR", 
                    text: "Durante una sesión técnica se discute la ampliación de la flota. Un compañero afirma que un AGV y un AMR hacen exactamente lo mismo porque ambos se mueven sin conductor. ¿Cuál es el matiz técnico real que los diferencia?", 
                    options: [
                        { text: "El AGV sigue estrictamente rutas fijas programadas y se detiene ante un obstáculo, mientras que el AMR calcula y recalcula su trayectoria de manera autónoma para sortear obstáculos.", isCorrect: true, feedback: "Los AGV operan sobre rutas definidas con gestión básica de parada, mientras los AMR adaptan su rumbo mediante SLAM.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "El AGV se desplaza únicamente por el exterior de las naves y el AMR exclusivamente en oficinas de dirección.", isCorrect: false, feedback: "Ambos tipos de vehículos operan en el interior de naves de producción y montaje.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "El AMR requiere la instalación obligatoria de cables eléctricos enterrados bajo el suelo de hormigón.", isCorrect: false, feedback: "El cable enterrado es una infraestructura de guiado para AGVs tradicionales.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "No existe ninguna diferencia tecnológica en el software de control; los nombres se usan de forma comercial indistinta.", isCorrect: false, feedback: "Sus arquitecturas de navegación, localización y gestión del entorno son totalmente distintas.", points: -12000, secPenalty: 10, type: "wrong" }
                    ] 
                },
                { 
                    title: "Tecnología SLAM", 
                    text: "En una zona de Almussafes donde se implantan AMRs, se explica que el sistema utiliza tecnología SLAM. ¿Qué labor realiza concretamente este sistema en el vehículo?", 
                    options: [
                        { text: "Mide la presión de los neumáticos mediante ultrasonidos para evitar pinchazos con virutas metálicas.", isCorrect: false, feedback: "La odometría mide el giro de rueda, pero SLAM se refiere a localización y cartografía.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Permite al robot crear y actualizar un mapa virtual (Digital Twin) de su entorno mediante LiDAR, localizándose y planificando rutas sin depender de guías físicas.", isCorrect: true, feedback: "El SLAM procesa datos para mapear y navegar de forma autónoma sin cintas o rieles.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Conecta el vehículo directamente con los satélites meteorológicos de la península para evitar zonas de lluvia.", isCorrect: false, feedback: "Los sistemas de navegación operan en interiores bajo techo sin conexión GPS.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Regula el consumo eléctrico de la batería para que dure exactamente 24 horas continuas.", isCorrect: false, feedback: "La gestión de batería corresponde al BMS, no al algoritmo SLAM de navegación.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Triangulación Láser con Balizas Reflectantes", 
                    text: "En la planta de Motores (VEP) se utiliza guiado por triangulación láser. ¿Cómo calcula el vehículo su posición exacta en todo momento dentro del circuito?", 
                    options: [
                        { text: "Mediante un cabezal láser giratorio a bordo que mide con precisión el ángulo y la distancia a múltiples bandas reflectantes fijadas en columnas y paredes.", isCorrect: true, feedback: "El cabezal óptico triangula su posición midiendo el eco láser devuelto por las balizas perimetrales fijas.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Siguiendo una zanja abierta en el suelo por la que pasa un cable eléctrico de alta tensión.", isCorrect: false, feedback: "Eso describe el guiado por cable enterrado, no la triangulación óptica láser.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Mediante una cámara cenital instalada en las cerchas del techo que fotografía al AGV desde arriba.", isCorrect: false, feedback: "La triangulación láser se realiza desde el propio vehículo hacia el entorno perimetral.", points: -12000, secPenalty: 10, type: "wrong" },
                        { text: "Adivinando las coordenadas mediante una brújula magnética analógica orientada al norte geográfico.", isCorrect: false, feedback: "Las brújulas sufren graves interferencias por las estructuras metálicas de las naves.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Las Cuatro Capas de Funcionamiento de un AGV", 
                    text: "La presentación esquemática resume el movimiento de un AGV en cuatro capas que trabajan juntas. ¿Cuál es el orden correcto de estos niveles según el flujo de control?", 
                    options: [
                        { text: "1. Movimiento -> 2. Navegación -> 3. Referencias -> 4. Sensores", isCorrect: false, feedback: "Inverso. El flujo real parte de percibir el entorno para traducirse en movimiento físico.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "1. Sensores (perciben el entorno) -> 2. Referencias (orientan) -> 3. Navegación (decide la ruta) -> 4. Movimiento (ejecuta la acción).", isCorrect: true, feedback: "Las cuatro capas integran percepción sensorial, anclaje de referencias, cálculo y actuación motriz.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "1. Chapa -> 2. Batería -> 3. Wi-Fi -> 4. Pantalla HMI", isCorrect: false, feedback: "Mezcla componentes físicos generales con conectividad.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "1. Planificación de ruta -> 2. Sensores -> 3. Movimiento -> 4. Referencias", isCorrect: false, feedback: "Orden incorrecto. La planificación requiere la información previa de sensores.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                }
            ]
        },
        { 
            id: "M3", 
            title: "3. Seguridad. UNE ISO 3691-4:2024", 
            pptx: "borrador_formación agv_v.2 _27_08_2026.pptx", 
            desc: "Escáneres de seguridad, mapas dinámicos, zonas operativas y gálibos.", 
            bank: [
                { 
                    title: "Reacción ante obstáculos menores (cartón)", 
                    text: "Vas caminando por la línea y ves un AGV parado delante de un cartón vacío caído en el suelo. Un compañero comenta: 'Mira qué exagerados son estos cacharros.' ¿Qué piensas?", 
                    options: [
                        { text: "El cartón es demasiado ligero para que un AGV tenga que reaccionar ante él.", isCorrect: false, feedback: "Los escáneres láser detectan cualquier volumen físico dentro de su zona activa.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Seguramente el escáner ha detectado algo dentro de su campo de seguridad.", isCorrect: true, feedback: "El escáner láser detecta cualquier elemento dentro de sus campos perimetrales activos.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Los AGV suelen detenerse cuando la batería baja del 50%.", isCorrect: false, feedback: "La baja batería genera alertas de recarga, no frenadas por obstáculos en la vía.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Los cartones activan automáticamente la parada de emergencia.", isCorrect: false, feedback: "Lo que se activa es la detección del campo láser por volumen, no el cartón en sí.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Reducción de velocidad en zonas concurridas", 
                    text: "Un AGV reduce mucho la velocidad al entrar en una zona donde suelen coincidir peatones y vehículos. ¿Qué explicación encaja mejor con lo visto en la formación?", 
                    options: [
                        { text: "El sistema ajusta la circulación cuando cambia el entorno alrededor.", isCorrect: true, feedback: "Los mapas adaptativos y zonas operativas configuran reducciones de velocidad automáticas.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "La velocidad baja porque se acerca a una estación de carga.", isCorrect: false, feedback: "Las estaciones de carga tienen protocolos específicos de aproximación final.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Todos los AGV circulan lentamente en cualquier circunstancia.", isCorrect: false, feedback: "Circulan a su velocidad nominal en viales libres y se reducen en áreas de riesgo.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "El vehículo está perdiendo conexión con el servidor central.", isCorrect: false, feedback: "La pérdida de red provoca paradas de seguridad fail-safe, no reducciones pautadas.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Comprobación tras activar seta de emergencia", 
                    text: "Durante una incidencia alguien pulsa una seta de emergencia. Cinco minutos después otro trabajador dice: 'Ya está, tiramos para delante.' ¿Qué falta antes de volver a arrancar?", 
                    options: [
                        { text: "Revisar que la causa de la parada realmente ha desaparecido.", isCorrect: true, feedback: "Exige comprobar presencialmente el despeje de la vía y realizar un rearme local verificado.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Comprobar el porcentaje de batería del vehículo.", isCorrect: false, feedback: "La seta es un dispositivo mecánico de seguridad, no afecta directamente a la batería.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Verificar la conexión WiFi de la zona.", isCorrect: false, feedback: "Las setas operan mediante circuitos hardwired de seguridad local (Safety PLCs).", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Consultar si el siguiente turno está informado.", isCorrect: false, feedback: "La prioridad inmediata es la verificación física de seguridad de la vía.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Deformación Dinámica de Campos Láser", 
                    text: "Un AGV industrial que transporta una carga ancha se dispone a trazar una curva pronunciada dentro de un pasillo limitado por estructuras fijas. Según la norma UNE ISO 3691-4:2024, ¿cómo debe comportarse el sistema de escáneres de seguridad?", 
                    options: [
                        { text: "Mantener un campo de protección estático y rectangular idéntico al de la marcha en línea recta.", isCorrect: false, feedback: "Un campo estático en curva dejaría sin protección el voladizo exterior.", points: -15000, secPenalty: 12, type: "wrong" },
                        { text: "Ajustar algorítmicamente de forma automática los límites de detección perimetral.", isCorrect: false, feedback: "La norma exige una adaptación geométrica certificada y no meros ajustes algorítmicos.", points: -15000, secPenalty: 12, type: "wrong" },
                        { text: "Deformar dinámicamente los campos de aviso y parada adaptándolos a la velocidad de giro y a la anchura máxima del vehículo más su carga.", isCorrect: true, feedback: "La norma exige que el mapa de seguridad se adapte en tiempo real al ángulo de giro y a la envolvente.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Configurar un perfil simétrico de frenado de emergencia constante para cualquier trayectoria.", isCorrect: false, feedback: "Un perfil simétrico constante ignora los puntos críticos generados por la inercia en curva.", points: -15000, secPenalty: 12, type: "wrong" }
                    ] 
                }
            ]
        },
        { 
            id: "M4", 
            title: "4. Arquitectura IT. Conectividad", 
            pptx: "borrador_formación agv_v.2 _27_08_2026.pptx", 
            desc: "Infocore, servidores SQL/App, puntos de acceso Wi-Fi, fibra POF y Transaction Manager.", 
            bank: [
                { 
                    title: "Desaparición de AGV en pantalla de sinóptico", 
                    text: "Un compañero comenta: 'El AGV no aparece en la pantalla. Seguro que está averiado.' ¿Qué te parece más razonable?", 
                    options: [
                        { text: "Si no aparece en el sistema probablemente esté fuera de servicio.", isCorrect: false, feedback: "La desaparición visual puede deberse a un corte temporal de Wi-Fi, no a fallo mecánico.", points: -15000, secPenalty: 12, type: "wrong" },
                        { text: "Puede existir un problema de comunicación sin que el vehículo haya perdido necesariamente todas sus funciones.", isCorrect: true, feedback: "Un fallo de red corta la telemetría, pero los autómatas locales siguen operativos.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "La desaparición en pantalla confirma un fallo absoluto de los sensores láser de abordo.", isCorrect: false, feedback: "Los sensores láser operan de forma local en el chasis, independientes de la red.", points: -12000, secPenalty: 10, type: "wrong" },
                        { text: "El vehículo debería dejar de circular automáticamente de inmediato por normativa.", isCorrect: false, feedback: "Disponen de autonomía de funcionamiento local temporal ante cortes de red.", points: -12000, secPenalty: 10, type: "wrong" }
                    ] 
                },
                { 
                    title: "Interpretación de AGV detenido en pista", 
                    text: "Ves un AGV parado. Un operario afirma: 'Seguro que es una avería.' Otro responde: 'Puede estar esperando una misión.' ¿Qué conclusión te parece mejor?", 
                    options: [
                        { text: "Un AGV parado siempre significa una incidencia.", isCorrect: false, feedback: "Los vehículos realizan paradas programadas de espera o recarga.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Sin más información no puede saberse la causa de la parada.", isCorrect: true, feedback: "Una detención puede deberse a espera de misión, tráfico, congestión de red o parada técnica.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Los AGV nunca esperan órdenes.", isCorrect: false, feedback: "Operan subordinados a las misiones enviadas por el gestor central.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Una parada superior a treinta segundos es una avería.", isCorrect: false, feedback: "Los tiempos muertos en retenciones de línea o cruces pueden superar ese tiempo.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Uso y Ventaja de la Fibra Óptica Plástica (POF)", 
                    text: "¿Por qué se emplea fibra óptica plástica (POF) en la conexión de periféricos fijos críticos (como puertas automáticas y pasarelas) en entornos de alta interferencia electromagnética?", 
                    options: [
                        { text: "Porque la fibra POF es un material elástico que permite estirarse físicamente cuando los AGVs chocan contra las puertas.", isCorrect: false, feedback: "Las fibras ópticas no están diseñadas para soportar impactos de vehículos.", points: -12000, secPenalty: 10, type: "wrong" },
                        { text: "Porque ofrece inmunidad absoluta frente al ruido electromagnético generado por equipos pesados de soldadura y motores de gran potencia.", isCorrect: true, feedback: "La transmisión por pulsos de luz en fibra POF es inmune a las perturbaciones eléctricas industriales.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Porque sustituye por completo a la necesidad de utilizar baterías eléctricas en los robots móviles.", isCorrect: false, feedback: "La fibra transporta datos ópticos, no energía eléctrica de potencia.", points: -15000, secPenalty: 12, type: "wrong" },
                        { text: "Porque permite conectar los sistemas de planta a internet mediante televisión por satélite.", isCorrect: false, feedback: "Se emplea para redes de campo locales y periféricos críticos industriales internos.", points: -12000, secPenalty: 10, type: "wrong" }
                    ] 
                }
            ]
        },
        { 
            id: "M5", 
            title: "5. Herramientas de seguimiento y análisis", 
            pptx: "borrador_formación agv_v.2 _27_08_2026.pptx", 
            desc: "Assets en FIS, integración con Teams, Dashboards de vsystems y KPIs de fiabilidad.", 
            bank: [
                { 
                    title: "Avisos en Teams sin impacto en producción", 
                    text: "En Teams aparecen varias incidencias relacionadas con el mismo circuito durante la semana. Ninguna ha provocado una parada importante. ¿Qué conclusión parece más prudente?", 
                    options: [
                        { text: "Las incidencias pueden merecer atención aunque todavía no hayan generado impactos relevantes.", isCorrect: true, feedback: "Los avisos repetitivos anticipan fallos mayores y permiten aplicar mantenimiento preventivo.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Si producción sigue funcionando, la situación probablemente es aceptable.", isCorrect: false, feedback: "Ignorar microincidencias suele derivar en paradas de mayor calado a futuro.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "El circuito presenta necesariamente un defecto técnico.", isCorrect: false, feedback: "Puede deberse a factores operativos de carga o entorno, no a defecto sistémico.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Las incidencias menores suelen resolverse por sí mismas.", isCorrect: false, feedback: "Las desviaciones industriales requieren análisis y contramedidas técnicas.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Contraste entre percepción y registros históricos", 
                    text: "Un compañero afirma: 'Ese AGV siempre da problemas.' Al consultar el histórico observas que durante los últimos dos meses no aparecen incidencias relevantes. ¿Qué conclusión es la más prudente?", 
                    options: [
                        { text: "Los registros disponibles no respaldan esa afirmación, aunque conviene entender en qué experiencias se basa.", isCorrect: true, feedback: "Se debe contrastar la percepción subjetiva con los datos telemétricos objetivos del sistema.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "El compañero recuerda incidencias antiguas.", isCorrect: false, feedback: "Suposición no demostrable de manera objetiva sin analizar los datos de campo.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "El AGV funciona perfectamente.", isCorrect: false, feedback: "Aseveración precipitada; el registro puede no recoger incidencias menores.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "La percepción del trabajador es más fiable que los registros.", isCorrect: false, feedback: "Los datos automatizados de FIS y vsystems aportan trazabilidad objetiva.", points: -12000, secPenalty: 10, type: "wrong" }
                    ] 
                },
                { 
                    title: "Estructura de Assets en el Sistema FIS", 
                    text: "En la herramienta FIS, ¿cómo se estructuran y qué representan los denominados Assets asociados a la flota de AGVs?", 
                    options: [
                        { text: "Son listados jerárquicos de eventos e incidentes donde existe un Asset específico por cada punto de carga/descarga o subcircuito, registrando duraciones, horas de inicio/fin e ID del AGV.", isCorrect: true, feedback: "El FIS organiza la trazabilidad operativa asignando identidades de Asset a los puntos críticos.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Son cuentas bancarias destinadas al pago de primas de seguros de los vehículos autónomos.", isCorrect: false, feedback: "No guardan relación con aspectos financieros o bancarios.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Son contraseñas encriptadas de acceso exclusivo para los directores de la compañía.", isCorrect: false, feedback: "Los Assets son registros técnicos de eventos de planta.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Son planos arquitectónicos en formato PDF de las oficinas centrales.", isCorrect: false, feedback: "Corresponden a elementos de monitorización de procesos logísticos.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Análisis de Pareto y Unidades Problemáticas (AGV 3501)", 
                    text: "Al examinar el histórico mensual de vsystems, se detecta que la unidad AGV 3501 acumula el doble de fallos que el resto de los 70 AGVs del circuito VEP. ¿Qué conclusión técnica se extrae?", 
                    options: [
                        { text: "El problema es intrínseco a esa unidad concreta (hardware de abordo, sensores o cableado) y requiere una inspección prioritaria en taller, descartando un fallo general de pista.", isCorrect: true, feedback: "Aislar datos por Asset permite discriminar averías de equipo frente a incidencias de pista.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Toda la infraestructura de la pista de VEP debe ser demolida y repavimentada por completo.", isCorrect: false, feedback: "Desproporcionado. El fallo se concentra en un vehículo específico, no en la pista.", points: -18000, secPenalty: 15, type: "wrong" },
                        { text: "Se debe reasignar el AGV 3501 a tareas administrativas de oficina para que no sufra desgaste mecánico.", isCorrect: false, feedback: "Inviable. Es un activo industrial de manutención de cargas.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "El indicador de vsystems presenta un error de cálculo y debe ser ignorado.", isCorrect: false, feedback: "Los datos de histórico son objetivos y sirven para guiar el mantenimiento preventivo.", points: -12000, secPenalty: 10, type: "wrong" }
                    ] 
                }
            ]
        },
        { 
            id: "M6", 
            title: "6. Áreas de mantenimiento", 
            pptx: "borrador_formación agv_v.2 _27_08_2026.pptx", 
            desc: "Talleres VEP y VO, Pit Stops, utillaje y mantenimiento preventivo de ruedas.", 
            bank: [
                { 
                    title: "Consignación y simplicidad de averías", 
                    text: "Un técnico necesita aplicar un procedimiento de consignación antes de intervenir en un AGV. Un responsable comenta: 'La avería es sencilla. Podemos ganar tiempo si simplificamos algunos pasos.' ¿Qué valoración te parece más razonable?", 
                    options: [
                        { text: "La complejidad de una avería no siempre coincide con el nivel real de riesgo asociado a la intervención.", isCorrect: true, feedback: "Un fallo simple en componentes eléctricos mantiene el riesgo de tensión, exigiendo rigor en el LOTO.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Los protocolos de consignación eléctrica pueden ajustarse o flexibilizarse según el juicio operativo del turno.", isCorrect: false, feedback: "Los procedimientos de consignación y LOTO son estrictos e inalterables.", points: -15000, secPenalty: 12, type: "wrong" },
                        { text: "Las intervenciones rápidas en taller eximen de colocar bloqueos físicos si hay visibilidad.", isCorrect: false, feedback: "La visibilidad no sustituye al bloqueo físico y etiquetado obligatorio.", points: -12000, secPenalty: 10, type: "wrong" },
                        { text: "La prioridad de la reparación debe primar sobre los pasos formales de seguridad.", isCorrect: false, feedback: "La seguridad de las personas se antepone siempre a los objetivos de producción.", points: -15000, secPenalty: 12, type: "wrong" }
                    ] 
                },
                { 
                    title: "Capacidades de los Talleres VEP y VO", 
                    text: "¿Qué instalaciones de soporte y mantenimiento se encuentran operativas en las áreas de VEP (Motores) y VO (Carrocerías)?", 
                    options: [
                        { text: "Talleres especializados con más de 70-80 AGVs asignados, circuitos de prueba, zonas de carga y útiles de volteo/mesa de trabajo.", isCorrect: true, feedback: "Los shops disponen de talleres equipados para soporte integral y pruebas de flota.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Un simple banco de carpintería manual y herramientas de cerrajería básica.", isCorrect: false, feedback: "Inadecuado. Las flotas autónomas exigen talleres dotados de tecnología avanzada.", points: -12000, secPenalty: 10, type: "wrong" },
                        { text: "Una pista exterior de karts recreativos para el descanso del personal.", isCorrect: false, feedback: "Las instalaciones son de estricta naturaleza técnico-productiva.", points: -15000, secPenalty: 12, type: "wrong" },
                        { text: "Un almacén exclusivo de ropa de trabajo y EPIs de repuesto.", isCorrect: false, feedback: "Su función principal es el mantenimiento correctivo y preventivo de vehículos.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Función del concepto Pit Stop en Planta", 
                    text: "¿Para qué sirve habilitar un área de 'Pit Stop' en los circuitos de Almussafes?", 
                    options: [
                        { text: "Para aparcar camiones de transporte externo durante sus descansos nocturnos.", isCorrect: false, feedback: "Los camiones operan en los muelles de expedición, no en los Pit Stops de AGVs.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Para realizar diagnósticos rápidos, reposiciones de emergencia y pequeñas asistencias locales sin necesidad de desplazar el AGV al taller central.", isCorrect: true, feedback: "El Pit Stop optimiza la disponibilidad minimizando tiempos muertos de desplazamiento.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Para realizar reuniones comerciales con proveedores de componentes mecánicos.", isCorrect: false, feedback: "Las áreas de Pit Stop están ubicadas en el interior de los viales productivos.", points: -12000, secPenalty: 10, type: "wrong" },
                        { text: "Para lavar con agua a presión la carrocería exterior de los robots.", isCorrect: false, feedback: "Los equipos electrónicos no deben lavarse con agua a presión directa.", points: -12000, secPenalty: 10, type: "wrong" }
                    ] 
                },
                { 
                    title: "Criterio preventivo en ruedas (100 horas)", 
                    text: "Se programa el control y reapriete obligatorio de la tornillería de ruedas a las 100 horas en AGVs de nueva incorporación. Esta medida responde a:", 
                    options: [
                        { text: "Neutralizar el fenómeno de asentamiento mecánico inicial y vibraciones que aflojan las sujeciones bajo carga dinámica.", isCorrect: true, feedback: "El mantenimiento preventivo en el periodo de rodaje previene averías en ruta.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Cumplir con un expediente burocrático de archivo sin implicaciones prácticas en la máquina.", isCorrect: false, feedback: "Su objetivo es eminentemente mecánico y de seguridad física.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Sustituir de forma preventiva las llantas de aluminio por desgaste de rodadura.", isCorrect: false, feedback: "Las 100 horas iniciales se centran en el par de apriete, no en el cambio de componentes.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Reconfigurar la conexión de red inalámbrica del vehículo desde los pernos de la rueda.", isCorrect: false, feedback: "Incongruencia técnica absoluta entre elementos mecánicos y de conectividad IT.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                }
            ]
        },
        { 
            id: "M7", 
            title: "7. Evacuación y emergencia", 
            pptx: "borrador_formación agv_v.2 _27_08_2026.pptx", 
            desc: "Proyecto Moisés, pasillos rojos, LST BCI y modos de emergencia.", 
            bank: [
                { 
                    title: "Reacción ante alarma general y AGVs fuera de posición", 
                    text: "Se activa una alarma general y observas varios AGV detenidos fuera de su posición habitual. ¿Qué interpretación parece más razonable?", 
                    options: [
                        { text: "El sistema está ejecutando una actuación prevista para situaciones de emergencia.", isCorrect: true, feedback: "Responde al comportamiento programado para liberar rutas de evacuación (Proyecto Moisés).", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Los AGV han perdido comunicación con el gestor de flota.", isCorrect: false, feedback: "Una parada generalizada coordinada obedece a protocolos de autoprotección, no a pérdida de red.", points: -12000, secPenalty: 10, type: "wrong" },
                        { text: "Existe una avería simultánea en varios vehículos distintos.", isCorrect: false, feedback: "Es altamente improbable un fallo masivo simultáneo independiente de la alarma.", points: -15000, secPenalty: 12, type: "wrong" },
                        { text: "Los equipos han agotado su batería al mismo tiempo.", isCorrect: false, feedback: "La gestión energética descentralizada evita descargas coincidentes masivas.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Proyecto Moisés y Despeje de Pasillos Rojos", 
                    text: "Se activa la alarma general de evacuación en planta y entra en juego el sistema central (Proyecto Moisés). ¿Cómo actúa la flota de AGVs ante una orden de repliegue?", 
                    options: [
                        { text: "Se mantienen detenidos donde estaban sin ejecutar el repliegue previsto por falta de señal.", isCorrect: false, feedback: "Los AGVs cuentan con rutas de escape automáticas programadas ante el plan de emergencia.", points: -15000, secPenalty: 12, type: "wrong" },
                        { text: "Los AGVs se desplazan de forma controlada hacia los apartaderos de seguridad designados, liberando por completo los pasillos rojos de evacuación.", isCorrect: true, feedback: "El protocolo Moisés despeja las rutas de escape peatonales y los viales para servicios de emergencia.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Inician un ciclo de retorno manual asistido esperando la intervención de los operarios de turno.", isCorrect: false, feedback: "El desalojo de viales durante una evacuación general está automatizado por el sistema.", points: -15000, secPenalty: 12, type: "wrong" },
                        { text: "Conmutan de forma autónoma a modo de transporte de mercancías prioritarias hacia el exterior.", isCorrect: false, feedback: "Priorizar material frente a la evacuación humana infringe los principios de PRL.", points: -20000, secPenalty: 20, type: "wrong" }
                    ] 
                },
                {
                    title: "Situaciones de Activación LST BCI",
                    text: "Según la LST de la Brigada Contra Incendios (BCI) en Ford Valencia, ¿en qué supuestos concretos se activa el modo de acceso de emergencia que obliga a despejar las rutas de AGVs?",
                    options: [
                        { text: "Ante cualquier aviso menor de mantenimiento preventivo registrado en el panel general de vsystems.", isCorrect: false, feedback: "Los avisos rutinarios de mantenimiento no disparan los protocolos de emergencia de la BCI.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Ante una emergencia confirmada que requiera el paso urgente de vehículos de auxilio (bomberos, ambulancia) o evacuación general.", isCorrect: true, feedback: "El protocolo se activa estrictamente ante emergencias reales confirmadas que exigen liberar viales.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Cada vez que un AGV experimenta una pérdida de guía puntual en un circuito secundario de carrocerías.", isCorrect: false, feedback: "Una pérdida de guía es una incidencia técnica resuelta por taller, no una emergencia de BCI.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Durante los cambios de turno productivo para reajustar los flujos de tráfico en pasillos rojos.", isCorrect: false, feedback: "Los cambios de turno operan bajo pautas logísticas ordinarias, no bajo planes de emergencia.", points: -10000, secPenalty: 8, type: "wrong" }
                    ]
                },
                { 
                    title: "Acceso de ambulancia con pasillos despejados", 
                    text: "Una ambulancia debe acceder a una nave y los pasillos aparecen completamente despejados. ¿Qué pensarías?", 
                    options: [
                        { text: "Se ha producido una actuación coordinada relacionada con emergencias.", isCorrect: true, feedback: "Indica que el sistema y el personal han despejado preventivamente los viales.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Los AGV están realizando automáticamente una operación de carga.", isCorrect: false, feedback: "Las operaciones de carga no guardan relación con viales de ambulancia despejados.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Existe una parada general de producción por mantenimiento.", isCorrect: false, feedback: "El mantenimiento programado no implica la intervención urgente de una ambulancia.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Los operarios han retirado manualmente todos los vehículos.", isCorrect: false, feedback: "El despeje se realiza mediante automatismos del sistema central de planta.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                }
            ]
        },
        { 
            id: "M8", 
            title: "8. Gestores de flota", 
            pptx: "borrador_formación agv_v.2 _27_08_2026.pptx", 
            desc: "Resolución de deadlocks, sinópticos de seguimiento (vsystems / MiR Fleet) y teleoperación segura.", 
            bank: [
                { 
                    title: "Interpretación de AGVs detenidos cara a cara en sinóptico", 
                    text: "En el sinóptico observas dos AGV detenidos frente a frente en un pasillo estrecho desde hace varios minutos. ¿Qué interpretación parece más razonable?", 
                    options: [
                        { text: "El gestor de flota está resolviendo una situación de prioridad o bloqueo (deadlock).", isCorrect: true, feedback: "El software analiza prioridades y reasigna rutas de bypass automáticamente ante deadlocks.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Ambos AGV se han quedado sin batería simultáneamente.", isCorrect: false, feedback: "Las descargas coincidentes exactas de dos unidades por batería son excepcionales.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Los dos vehículos han perdido la comunicación con planta.", isCorrect: false, feedback: "La pérdida de red activaría paradas individuales de seguridad fail-safe, no un cara a cara.", points: -12000, secPenalty: 10, type: "wrong" },
                        { text: "Los operarios han solicitado una parada manual de ambos.", isCorrect: false, feedback: "Las paradas manuales se gestionan mediante setas o mandos locales, no generan bloqueos simétricos.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Condiciones para Teleoperación Manual Asistida", 
                    text: "Un AGV queda fuera de ruta por obras y el operador debe teleoperarlo unos centímetros hacia atrás. ¿Qué condición de seguridad exige la ISO 3691-4?", 
                    options: [
                        { text: "Línea de visión directa (Line-of-Sight), velocidad reducida de seguridad (máx. 0.3 m/s) y dispositivo de hombre muerto activo.", isCorrect: true, feedback: "La intervención manual exige visión directa y hombre muerto para prevenir atropellos.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Conducirlo a ciegas desde la oficina con una webcam diferida.", isCorrect: false, feedback: "Manejar maquinaria pesada autónoma a ciegas desde remoto infringe la norma.", points: -18000, secPenalty: 15, type: "wrong" },
                        { text: "Arrastrarlo con una carretilla diésel a tirones sin soltar frenos.", isCorrect: false, feedback: "Arrastrar un AGV bloqueado destruye los motores y reductores.", points: -15000, secPenalty: 12, type: "wrong" },
                        { text: "Pulsar el acelerador al máximo sin mirar el entorno.", isCorrect: false, feedback: "Temeridad extrema en entornos de planta con personal.", points: -25000, secPenalty: 25, type: "wrong" }
                    ] 
                },
                { 
                    title: "Utilidad del sinóptico de seguimiento", 
                    text: "Un operario comenta: 'Si un AGV se mueve, no necesito mirar el sinóptico.' ¿Qué le responderías?", 
                    options: [
                        { text: "El sinóptico aporta información global de tráfico y misiones que no siempre se aprecia desde planta.", isCorrect: true, feedback: "Permite anticiparse a bloqueos, conocer estado de flotas y supervisar flujos completos.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "El sinóptico solo sirve para personal de mantenimiento avanzado.", isCorrect: false, feedback: "Su visualización es útil para operadores, mandos y técnicos de línea.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Los vehículos muestran siempre toda la información necesaria en sus pantallas locales.", isCorrect: false, feedback: "Las pantallas de abordo son reducidas frente a la vista sinóptica general del servidor.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "El gestor de flota únicamente registra averías de carácter grave.", isCorrect: false, feedback: "Registra microparadas, estados, misiones y alarmas de todo tipo.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Comprobación ante AGV detenido en circuito", 
                    text: "Un AGV lleva varios minutos sin avanzar, pero el circuito continúa funcionando. ¿Qué comprobarías primero en el gestor de flota?", 
                    options: [
                        { text: "Si tiene asignada una misión pendiente o está esperando prioridad en un cruce.", isCorrect: true, feedback: "Muchas detenciones se deben a esperas lógicas de tráfico asignadas por el sistema.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Si el vehículo necesita un cambio completo de batería.", isCorrect: false, feedback: "Las recargas se gestionan de forma automatizada por nivel de SoC.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Si el servidor principal se encuentra totalmente apagado.", isCorrect: false, feedback: "Si el servidor estuviera apagado, el circuito completo se detendría.", points: -12000, secPenalty: 10, type: "wrong" },
                        { text: "Si todos los AGV de la planta están detenidos simultáneamente.", isCorrect: false, feedback: "El enunciado indica que el circuito continúa funcionando.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                }
            ]
        },
        { 
            id: "M9", 
            title: "9. Casos prácticos", 
            pptx: "borrador_formación agv_v.2 _27_08_2026.pptx", 
            desc: "Casos críticos en Planta de Baterías, flotas de 180+ unidades (Valencia Site) y Kärcher Kira.", 
            bank: [
                { 
                    title: "Alarma térmica en Planta de Baterías", 
                    text: "Un AGV de Battery Plant registra una alarma térmica durante una misión de transporte. La carga llega correctamente al destino y la alarma desaparece pocos minutos después. ¿Cuál parece la interpretación más razonable?", 
                    options: [
                        { text: "Si la misión terminó correctamente, la alarma carece de relevancia.", isCorrect: false, feedback: "Las alarmas térmicas intermitentes en celdas de litio anticipan fallos latentes que exigen revisión.", points: -12000, secPenalty: 10, type: "wrong" },
                        { text: "Conviene registrar el evento porque puede aportar información útil si vuelve a repetirse.", isCorrect: true, feedback: "Las alertas transitorias en áreas de baterías deben registrarse para análisis predictivo de celdas.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "La alarma demuestra que el AGV necesita cambiar inmediatamente la batería.", isCorrect: false, feedback: "Precipitado. Un aviso aislado no justifica la sustitución sin un diagnóstico previo.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Las alarmas térmicas son normales durante operaciones prolongadas.", isCorrect: false, feedback: "Los sistemas de gestión térmica operan dentro de rangos estrictos; los avisos exigen atención.", points: -15000, secPenalty: 12, type: "wrong" }
                    ] 
                },
                { 
                    title: "Anomalía Térmica crítica en Planta de Baterías", 
                    text: "En la Planta de Baterías, un AGV transporta módulos energéticos y la telemetría avisa de un calentamiento anómalo crítico en una celda:", 
                    options: [
                        { text: "Aislar el vehículo inmediatamente, activar el protocolo de emergencia térmica y derivarlo a la zona segura de cuarentena exterior.", isCorrect: true, feedback: "Las anomalías térmicas graves en baterías de litio exigen aislamiento inmediato y cuarentena.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Continuar la ruta hasta el final del turno sin hacer caso a la alerta.", isCorrect: false, feedback: "Peligro de fuga térmica e incendio incontrolado. Inadmisible en plantas de baterías.", points: -25000, secPenalty: 25, type: "wrong" },
                        { text: "Apagar los ordenadores de la oficina técnica para desconectar el sistema.", isCorrect: false, feedback: "Apagar oficinas no soluciona el riesgo térmico físico en planta.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Lavar la batería con agua a presión en el puesto sin desenergizar.", isCorrect: false, feedback: "Riesgo de cortocircuito y explosión química. Inadecuado.", points: -20000, secPenalty: 20, type: "wrong" }
                    ] 
                },
                { 
                    title: "Comportamiento autónomo de robot de limpieza Kärcher", 
                    text: "Un robot de limpieza Kärcher Kira reduce velocidad y modifica ligeramente su recorrido al entrar en una zona con tránsito de personas. ¿Qué interpretación encaja mejor con la formación?", 
                    options: [
                        { text: "El comportamiento forma parte del funcionamiento previsto del equipo.", isCorrect: true, feedback: "Los robots de limpieza autónoma adaptan su trayectoria mediante evasión dinámica de obstáculos.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "La unidad ha perdido temporalmente la referencia de navegación.", isCorrect: false, feedback: "Modificar la velocidad y trazada ante personas es una respuesta de seguridad activa.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "El robot necesita asistencia manual para continuar trabajando.", isCorrect: false, feedback: "Operan de forma autónoma resolviendo pequeños desvíos por peatones.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "La batería entra automáticamente en modo ahorro energético.", isCorrect: false, feedback: "La gestión de velocidad por presencia peatonal responde a seguridad, no a ahorro.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                },
                { 
                    title: "Variedad tecnológica de flotas en Ford Valencia", 
                    text: "Durante una visita alguien comenta: 'Hay demasiados tipos de AGV distintos en esta planta.' ¿Qué explicación encaja mejor con lo visto en la formación?", 
                    options: [
                        { text: "Distintas operaciones exigen soluciones específicas de transporte (Mouse, Tugger, Forklift, AMRs).", isCorrect: true, feedback: "Cada proceso productivo requiere un tipo de vehículo especializado según su carga y operativa.", points: 5000, secPenalty: 0, type: "correct" },
                        { text: "Cada fabricante obliga a utilizar exclusivamente sus vehículos.", isCorrect: false, feedback: "Las compras responden a licitaciones técnicas y funcionales de planta.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "Todas las áreas deberían funcionar exactamente con el mismo modelo estandarizado.", isCorrect: false, feedback: "Inviable. Un AGV de plataforma baja no puede apilar en estanterías de altura VNA.", points: -10000, secPenalty: 8, type: "wrong" },
                        { text: "La variedad aparece únicamente por motivos económicos de presupuesto.", isCorrect: false, feedback: "Responde estrictamente a criterios de ingeniería logística y de proceso.", points: -10000, secPenalty: 8, type: "wrong" }
                    ] 
                }
            ]
        }
    ];

    let teams = [];
    let currentActiveModule = null;
    let currentQuestionIndex = 0;
    let activeQuestions = [];
    let completedModules = [];
    let timer;
    let timeLeft = 40;

    window.onload = function() {
        loadData();
        renderHub();
    };

    function loadData() {
        try {
            const saved = localStorage.getItem("kirleoAlmussafesData2026");
            if (saved) {
                const data = JSON.parse(saved);
                teams = data.teams || [];
                completedModules = data.completedModules || [];
            }
        } catch(e) {}
    }

    function saveData() {
        try {
            localStorage.setItem("kirleoAlmussafesData2026", JSON.stringify({
                teams: teams,
                completedModules: completedModules
            }));
        } catch(e) {}
    }

    function addTeam() {
        const input = document.getElementById("teamName");
        const name = input.value.trim();
        if (name.length < 3) { alert("Mínimo 3 caracteres para el nombre del equipo."); return; }
        if (teams.some(t => t.name.toLowerCase() === name.toLowerCase())) { alert("Este equipo ya está registrado."); return; }
        teams.push({ name: name, score: 35000, security: 100 });
        input.value = "";
        saveData();
        renderHub();
    }

    function clearTeams() {
        if(confirm("¿Seguro que deseas reiniciar todos los equipos, puntos y progresos?")) {
            teams = [];
            completedModules = [];
            localStorage.removeItem("kirleoAlmussafesData2026");
            document.getElementById("liveRanking").innerHTML = "";
            renderHub();
        }
    }

    function removeTeamByName(encodedName) {
        if (teams.length <= 2) {
            alert("Debe permanecer un mínimo de 2 equipos en la competición.");
            return;
        }
        const targetName = decodeURIComponent(encodedName);
        teams = teams.filter(t => t.name !== targetName);
        saveData();
        renderHub();
    }

    function shuffleArray(array) {
        const arr = [...array];
        for (let i = arr.length - 1; i > 0; i--) {
            const j = Math.floor(Math.random() * (i + 1));
            [arr[i], arr[j]] = [arr[j], arr[i]];
        }
        return arr;
    }

    function renderHub() {
        let listHTML = "";
        if(teams.length === 0) {
            listHTML = "<li style='color:#aaa;'>⚠️ No hay equipos registrados. Añade al menos 2 equipos para jugar.</li>";
        } else {
            const sortedTeams = [...teams].sort((a,b) => b.score - a.score);
            sortedTeams.forEach((t, i) => {
                let badge = t.score > 45000 ? "🟢 Experto" : (t.score >= 30000 ? "🔵 Competente" : (t.score >= 15000 ? "🟡 Refuerzo" : "🔴 Crítico"));
                let encodedName = encodeURIComponent(t.name);
                listHTML += `<li class="hub-team-row">
                    <span><strong>#${i+1} ${t.name}</strong> — 💰 ${t.score.toLocaleString("es-ES")} € | 🛡️ ${t.security}% (${badge})</span>
                    <button data-team="${encodedName}" onclick="removeTeamByName(this.dataset.team)" style="background:none; border:none; color:#ff4d4d; cursor:pointer; font-weight:bold; padding:0;">❌</button>
                </li>`;
            });
        }
        document.getElementById("teamList").innerHTML = listHTML;

        let modulesHTML = "";
        modulesData.forEach((mod, index) => {
            let isDone = completedModules.includes(mod.id);
            let prevDone = index === 0 || completedModules.includes(modulesData[index - 1].id);
            let statusBadge = isDone ? "✅ Completado" : (prevDone ? "🔓 Disponible" : "🔒 Bloqueado");
            let btnStyle = prevDone ? "background-color: #e6b800; color: #003366;" : "background-color: #555; color: #aaa; cursor: not-allowed;";

            modulesHTML += `
                <div class="module-card">
                    <div class="module-info">
                        <strong style="color: #e6b800;">${mod.title}</strong><br>
                        <span>${mod.desc}</span><br>
                        <span style="font-size: 14px; font-weight: bold;">Estado: ${statusBadge}</span>
                    </div>
                    <div class="module-actions">
                        <a href="${mod.pptx}" target="_blank" class="btn-pptx" title="Abrir presentación de teoría">📊 Ver Teoría (PPTX)</a>
                        <button style="${btnStyle}" onclick="${prevDone ? `startModule('${mod.id}')` : `alert('Completa el módulo anterior para desbloquear este.')`}">🎮 Jugar Simulador</button>
                    </div>
                </div>
            `;
        });
        document.getElementById("modulesContainer").innerHTML = modulesHTML;
    }

    const shiftEvents = [
        "🚑 **AVISO MÉDICO:** Ambulancia solicitando paso urgente en pasillo principal.",
        "⚡ **INCIDENCIA IT:** Microcorte detectado en clúster del servidor central de planta.",
        "📶 **CONECTIVIDAD:** Pico de alta latencia en red Wi-Fi de Montaje y Carrocerías.",
        "🔥 **PREVENCIÓN:** Conato detectado por sensor térmico en subcircuito crítico.",
        "🚧 **LOGÍSTICA:** Obra imprevista bloqueando trazada principal de AGVs.",
        "🔧 **MANTENIMIENTO:** Alerta de Asset por pérdida de guía repetida en TAG."
    ];

    function startShiftMode() {
        if(teams.length < 2) {
            alert("Por favor, registra al menos 2 equipos antes de arrancar el simulador.");
            return;
        }
        
        let seqQuestions = [];
        modulesData.forEach(m => {
            if(m.bank && m.bank.length > 0) {
                let randomQ = m.bank[Math.floor(Math.random() * m.bank.length)];
                seqQuestions.push(randomQ);
            }
        });
        
        currentActiveModule = { id: "SHIFT", title: "EVALUACIÓN FINAL - CAJA NEGRA COMPLETA (10 RETOS M0-M9)" };
        activeQuestions = seqQuestions;
        currentQuestionIndex = 0;

        document.getElementById("screen-hub").style.display = "none";
        document.getElementById("screen-game").style.display = "block";
        document.getElementById("gameModuleTitle").innerText = currentActiveModule.title;
        loadQuestion();
    }

    function startModule(modId) {
        if(teams.length < 2) {
            alert("Por favor, registra al menos 2 equipos antes de arrancar el simulador.");
            return;
        }
        currentActiveModule = modulesData.find(m => m.id === modId);
        if (!currentActiveModule || !currentActiveModule.bank || currentActiveModule.bank.length === 0) {
            alert("Este módulo no tiene preguntas disponibles.");
            return;
        }

        let limit = Math.min(3, currentActiveModule.bank.length);
        activeQuestions = shuffleArray(currentActiveModule.bank).slice(0, limit);
        currentQuestionIndex = 0;

        document.getElementById("screen-hub").style.display = "none";
        document.getElementById("screen-game").style.display = "block";
        document.getElementById("gameModuleTitle").innerText = currentActiveModule.title;
        loadQuestion();
    }

    function startTimer() {
        clearInterval(timer);
        timeLeft = 40;
        const countdownEl = document.getElementById("countdown");
        countdownEl.innerText = "⏱ " + timeLeft;
        countdownEl.classList.remove("flash-warning");

        timer = setInterval(() => {
            timeLeft--;
            countdownEl.innerText = "⏱ " + timeLeft;
            if(timeLeft <= 10) {
                countdownEl.classList.add("flash-warning");
            }
            if(timeLeft < 0) {
                clearInterval(timer);
                countdownEl.innerText = "⏱ 0 (Tiempo superado)";
            }
        }, 1000);
    }

    function loadQuestion() {
        const q = activeQuestions[currentQuestionIndex];
        document.getElementById("blockTitle").innerText = q.title;
        document.getElementById("questionText").innerText = q.text;
        document.getElementById("questionCounter").innerText = `Reto ${currentQuestionIndex + 1}/${activeQuestions.length}`;

        const randomEvt = shiftEvents[Math.floor(Math.random() * shiftEvents.length)];
        document.getElementById("eventBannerContainer").innerHTML = `<div class="event-banner">${randomEvt}</div>`;

        if (!q._renderedOptions) {
            q._renderedOptions = shuffleArray(q.options);
        }

        let optionsHTML = "";
        q._renderedOptions.forEach((opt, idx) => {
            let letter = String.fromCharCode(65 + idx);
            optionsHTML += `<div class='option'><strong>${letter})</strong> ${opt.text}</div>`;
        });
        document.getElementById("optionsContainer").innerHTML = optionsHTML;

        const teamVotesContainer = document.getElementById("teamVotes");
        teamVotesContainer.innerHTML = "";

        teams.forEach((t, i) => {
            const rowDiv = document.createElement("div");
            rowDiv.className = "vote-row";

            const span = document.createElement("span");
            const strong = document.createElement("strong");
            strong.textContent = t.name;
            span.appendChild(strong);
            rowDiv.appendChild(span);

            const select = document.createElement("select");
            select.id = `vote-${i}`;

            const defaultOpt = document.createElement("option");
            defaultOpt.value = "";
            defaultOpt.disabled = true;
            defaultOpt.selected = true;
            defaultOpt.textContent = "Decisión...";
            select.appendChild(defaultOpt);

            q._renderedOptions.forEach((opt, idx) => {
                let letter = String.fromCharCode(65 + idx);
                const optionEl = document.createElement("option");
                optionEl.value = letter;
                optionEl.textContent = letter;
                select.appendChild(optionEl);
            });

            rowDiv.appendChild(select);
            teamVotesContainer.appendChild(rowDiv);
        });

        const actionBtn = document.getElementById("actionBtn");
        if (currentQuestionIndex === activeQuestions.length - 1) {
            actionBtn.innerText = "💥 Validar Último Reto ➔";
        } else {
            actionBtn.innerText = "Validar Respuesta ➔";
        }

        startTimer();
    }

    function resolveTurn() {
        clearInterval(timer);
        for (let i = 0; i < teams.length; i++) {
            if (!document.getElementById(`vote-${i}`).value) { alert(`Falta la decisión del equipo: ${teams[i].name}`); return; }
        }

        const q = activeQuestions[currentQuestionIndex];
        const shuffled = q._renderedOptions;
        const correctOptObj = shuffled.find(o => o.isCorrect);
        const correctIdx = shuffled.indexOf(correctOptObj);
        const correctLetter = String.fromCharCode(65 + correctIdx);
        const keyIdea = correctOptObj.feedback || "Concepto clave consolidado en planta.";

        // Actualizar puntuaciones al momento
        teams.forEach((t, tIdx) => {
            const vote = document.getElementById(`vote-${tIdx}`).value;
            const voteIdx = vote.charCodeAt(0) - 65;
            const chosenOpt = shuffled[voteIdx];

            let totalEarned = chosenOpt.points;
            t.score = Math.max(0, t.score + totalEarned);
            if(chosenOpt.secPenalty) {
                t.security = Math.max(0, t.security - chosenOpt.secPenalty);
            }
        });

        // Construir HTML de corrección inmediata
        let turnHTML = `<div style="background:#001a33; padding:22px; border-radius:8px; border:2px solid #00509e; font-size:18px; margin-bottom: 20px;">
            <h3 style="color:#e6b800; margin-top:0; font-size:23px; margin-bottom: 12px;">Reto #${currentQuestionIndex + 1}: ${q.title}</h3>
            
            <p style="color:#28a745; margin-bottom: 10px; line-height: 1.4;">
                <strong>✅ Respuesta correcta (${correctLetter}):</strong><br>
                ${correctOptObj.text}
            </p>
            
            <p style="color:#e6b800; margin-bottom: 15px; line-height: 1.4;">
                <strong>📌 Idea clave:</strong><br>
                ${keyIdea}
            </p>
            
            <div style="background:#001224; padding: 14px; border-radius: 6px; border: 1px solid #004080;">
                <strong style="color: #ccc; font-size: 17px; display: block; margin-bottom: 6px;">Resultado en este reto:</strong>`;

        teams.forEach((t, tIdx) => {
            const vote = document.getElementById(`vote-${tIdx}`).value;
            const voteIdx = vote.charCodeAt(0) - 65;
            const chosenOpt = shuffled[voteIdx];
            const icon = chosenOpt.isCorrect ? '✅' : '❌';
            turnHTML += `<span style="display: inline-block; margin-right: 25px; margin-top: 4px; font-size: 18px;">${icon} <strong>${t.name}</strong></span>`;
        });

        turnHTML += `</div></div>`;

        // CONSTRUIR CLASIFICACIÓN PROVISIONAL EN DIRECTO (OPCIÓN 1 & 5)
        const sortedRanking = [...teams].sort((a, b) => b.score - a.score);
        turnHTML += `<div style="background:#00162e; padding: 18px; border-radius: 8px; border: 2px solid #e6b800;">
            <h4 style="color:#e6b800; margin:0 0 12px 0; font-size:20px; text-align:center;">🏅 CLASIFICACIÓN PROVISIONAL EN DIRECTO</h4>`;
        
        sortedRanking.forEach((st, sIdx) => {
            let medal = sIdx === 0 ? "🥇" : (sIdx === 1 ? "🥈" : (sIdx === 2 ? "🥉" : "🔹"));
            let width = Math.max(2, (st.score / 60000) * 100);
            let color = st.security < 70 ? "#dc3545" : (st.security < 90 ? "#ffc107" : "#28a745");
            turnHTML += `<div style="margin-bottom:12px; font-size:18px;">
                <div style="display:flex; justify-content:space-between; margin-bottom:4px;">
                    <span>${medal} <strong>#${sIdx+1} ${st.name}</strong></span>
                    <span style="color:#e6b800; font-weight:bold;">💰 ${st.score.toLocaleString("es-ES")} € | 🛡️ ${st.security}%</span>
                </div>
                <div class='ranking-bar'><div style='height:100%; width:${width}%; background-color:${color}; border-radius:12px;'></div></div>
            </div>`;
        });

        turnHTML += `</div>`;

        document.getElementById("turnFeedbackContainer").innerHTML = turnHTML;
        document.getElementById("feedbackProgressCounter").innerText = `Reto ${currentQuestionIndex + 1}/${activeQuestions.length}`;

        currentQuestionIndex++;

        const nextBtn = document.getElementById("turnNextBtn");
        if (currentQuestionIndex >= activeQuestions.length) {
            nextBtn.innerText = "🏆 Ver Clasificación Final ➔";
        } else {
            nextBtn.innerText = "Siguiente Reto ➔";
        }

        document.getElementById("screen-game").style.display = "none";
        document.getElementById("screen-turn-feedback").style.display = "block";
    }

    function proceedAfterTurn() {
        if (currentQuestionIndex >= activeQuestions.length) {
            document.getElementById("screen-turn-feedback").style.display = "none";
            document.getElementById("screen-resolution").style.display = "block";
            renderRanking();
            saveData();

            if(currentActiveModule && currentActiveModule.id !== "SHIFT" && !completedModules.includes(currentActiveModule.id)) {
                completedModules.push(currentActiveModule.id);
                saveData();
            }
        } else {
            document.getElementById("screen-turn-feedback").style.display = "none";
            document.getElementById("screen-game").style.display = "block";
            loadQuestion();
        }
    }

    function returnToHub() {
        clearInterval(timer);
        modulesData.forEach(m => m.bank.forEach(q => delete q._renderedOptions));
        document.getElementById("screen-game").style.display = "none";
        document.getElementById("screen-turn-feedback").style.display = "none";
        document.getElementById("screen-resolution").style.display = "none";
        document.getElementById("screen-hub").style.display = "block";
        renderHub();
    }

    function renderRanking() {
        const ranking = [...teams].sort((a,b) => b.score - a.score);
        let maxScore = Math.max(...ranking.map(t => t.score), 45000);
        let html = "";
        ranking.forEach(t => {
            let width = Math.max(2, (t.score / maxScore) * 100);
            let color = t.security < 70 ? "#dc3545" : (t.security < 90 ? "#ffc107" : "#28a745");
            html += `<div style='margin-bottom:18px; font-size:20px;'><strong>${t.name}:</strong> 💰 ${t.score.toLocaleString("es-ES")} € Presupuesto | 🛡️ Seguridad: ${t.security}%<div class='ranking-bar'><div style='height:100%; width:${width}%; background-color:${color}; border-radius:12px;'></div></div></div>`;
        });
        document.getElementById("liveRanking").innerHTML = html;
    }
</script>

</body>
</html>
