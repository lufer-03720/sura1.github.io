<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Arquitectura de Marca Interactiva - SURA</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Barlow:wght@500&display=swap" rel="stylesheet">
    <!-- Chosen Palette: SURA Corporate Harmony -->
    <!-- Application Structure Plan: He diseñado una aplicación de una sola página centrada en un diagrama visual. La estructura se basa en secciones temáticas (Marca Única, Beneficios, Coherencia, Mensaje Clave) controladas por una navegación principal. Este enfoque convierte un documento de texto estático en una experiencia de exploración. El diagrama actúa como ancla visual constante, reforzando el concepto de unificación, mientras que el contenido textual se presenta en fragmentos digeribles al hacer clic, mejorando la comprensión y el engagement del usuario. Se prioriza la claridad y la interacción sobre una simple lectura lineal. -->
    <!-- Visualization & Content Choices: Report Info: Estructura de marca paraguas de SURA. -> Goal: Organizar y mostrar la relación jerárquica. -> Viz/Presentation Method: Diagrama conceptual creado con HTML/CSS (divs y bordes) para representar la marca central y sus unidades. -> Interaction: Botones de navegación actualizan un panel de contenido adyacente, mostrando texto detallado para cada sección temática (Beneficios, Coherencia, etc.). -> Justification: El diagrama ofrece una comprensión visual inmediata del concepto "marca paraguas". La actualización de contenido por secciones evita la sobrecarga de información y crea un flujo de exploración controlado por el usuario. Se usan íconos (Unicode) para reforzar visualmente los puntos clave en la sección de beneficios. -> Library/Method: Vanilla JavaScript para la interactividad de los tabs, Tailwind CSS para el layout y el diagrama. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Barlow', sans-serif;
            background-color: #f8fafc; 
        }
        .sura-blue { color: #0033A0; }
        .sura-accent { color: #00A7D0; }
        .bg-sura-blue { background-color: #0033A0; }
        .bg-sura-accent { background-color: #00A7D0; }
        .border-sura-blue { border-color: #0033A0; }
        .nav-button {
            transition: all 0.3s ease;
        }
        .nav-button.active {
            background-color: #0033A0;
            color: white;
            transform: translateY(-2px);
            box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
        }
        .content-panel {
            min-height: 380px;
        }
        .line {
            background-color: #cbd5e1;
            position: absolute;
            transform-origin: left center;
        }
        .brand-circle {
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 9999px;
            font-weight: 500;
            text-align: center;
        }
    </style>
</head>
<body class="text-gray-700">

    <div class="container mx-auto px-4 sm:px-6 lg:px-8 py-12">

        <header class="text-center mb-12">
            <h1 class="text-4xl md:text-5xl font-bold sura-blue mb-2">Arquitectura de Marca SURA</h1>
            <p class="text-lg md:text-xl text-gray-600">Una estrategia unificada para una experiencia coherente.</p>
            <p class="mt-4 max-w-3xl mx-auto">Esta es una exploración interactiva de cómo SURA estructura su marca. El modelo de "marca paraguas" no solo organiza internamente la empresa, sino que construye una experiencia clara y sólida para el cliente. Usa la navegación para descubrir los pilares de esta estrategia.</p>
        </header>

        <main class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
            
            <div class="flex items-center justify-center p-8">
                <div class="relative w-[350px] h-[350px] sm:w-[400px] sm:h-[400px]">
                    <div class="brand-circle bg-sura-blue text-white w-32 h-32 sm:w-40 sm:h-40 absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 text-3xl">SURA</div>
                    
                    <div class="brand-circle bg-white border-2 border-sura-accent w-24 h-24 sm:w-28 sm:h-28 absolute text-sura-blue p-2" style="top: 12%; left: 12%;">Seguros</div>
                    
                    <div class="brand-circle bg-white border-2 border-sura-accent w-24 h-24 sm:w-28 sm:h-28 absolute text-sura-blue p-2" style="bottom: 12%; left: 12%;">Salud</div>

                    <div class="brand-circle bg-white border-2 border-sura-accent w-24 h-24 sm:w-28 sm:h-28 absolute text-sura-blue p-2" style="top: 12%; right: 12%;">ARL</div>

                    <div class="brand-circle bg-white border-2 border-sura-accent w-24 h-24 sm:w-28 sm:h-28 absolute text-sura-blue p-2" style="bottom: 12%; right: 12%;">Pensiones</div>
                </div>
            </div>

            <div class="flex flex-col">
                <nav class="flex flex-wrap gap-2 sm:gap-4 mb-6 justify-center lg:justify-start">
                    <button class="nav-button active text-sm sm:text-base px-4 py-2 rounded-lg bg-white border border-gray-200 shadow-sm" data-target="unica">Marca Única</button>
                    <button class="nav-button text-sm sm:text-base px-4 py-2 rounded-lg bg-white border border-gray-200 shadow-sm" data-target="beneficios">Beneficios al Cliente</button>
                    <button class="nav-button text-sm sm:text-base px-4 py-2 rounded-lg bg-white border border-gray-200 shadow-sm" data-target="coherencia">Coherencia</button>
                    <button class="nav-button text-sm sm:text-base px-4 py-2 rounded-lg bg-white border border-gray-200 shadow-sm" data-target="mensaje">Mensaje Clave</button>
                </nav>

                <div id="content-container" class="bg-white p-6 sm:p-8 rounded-xl shadow-lg border border-gray-100 content-panel">
                    
                    <div id="unica" class="content-section">
                        <h2 class="text-2xl font-bold sura-blue mb-4">Una Marca Paraguas</h2>
                        <p class="mb-4">SURA trabaja bajo una marca paraguas, lo que significa que todas sus unidades de negocio —Seguros, ARL, Salud y Pensiones— están unificadas bajo una misma identidad corporativa.</p>
                        <p>Este enfoque centralizado evita la dispersión de esfuerzos y garantiza que, sin importar el servicio al que acceda el cliente, siempre encuentre el respaldo de una organización sólida y coherente.</p>
                    </div>

                    <div id="beneficios" class="content-section hidden">
                        <h2 class="text-2xl font-bold sura-blue mb-4">Ventajas Claras para el Cliente</h2>
                        <p class="mb-6">Esta estrategia se traduce en beneficios directos que construyen una relación de confianza a largo plazo:</p>
                        <ul class="space-y-4">
                            <li class="flex items-start">
                                <span class="text-2xl mr-4 sura-accent">✓</span>
                                <div>
                                    <h3 class="font-bold">Confianza y Solidez</h3>
                                    <p class="text-gray-600">El cliente sabe que detrás de cada producto está la misma empresa con una sólida trayectoria y respaldo.</p>
                                </div>
                            </li>
                            <li class="flex items-start">
                                <span class="text-2xl mr-4 sura-accent">✓</span>
                                <div>
                                    <h3 class="font-bold">Claridad en la Oferta</h3>
                                    <p class="text-gray-600">No tiene que navegar entre marcas distintas, sino que identifica todo lo que necesita bajo un solo nombre.</p>
                                </div>
                            </li>
                            <li class="flex items-start">
                                <span class="text-2xl mr-4 sura-accent">✓</span>
                                <div>
                                    <h3 class="font-bold">Respaldo Integral</h3>
                                    <p class="text-gray-600">Se refuerza la percepción de que SURA es un aliado capaz de responder en diferentes momentos de la vida.</p>
                                </div>
                            </li>
                        </ul>
                    </div>

                    <div id="coherencia" class="content-section hidden">
                        <h2 class="text-2xl font-bold sura-blue mb-4">Coherencia Visual y Verbal</h2>
                        <p class="mb-4">La arquitectura de marca se refleja en una consistencia total en la comunicación y la identidad visual de la compañía.</p>
                         <ul class="list-disc list-inside space-y-2">
                            <li>Se usan nombres claros y uniformes: Seguros SURA, ARL SURA, Salud SURA.</li>
                            <li>Se mantiene una identidad gráfica común (tipografía, colores, estilo visual).</li>
                            <li>Se utiliza un tono de comunicación coherente, lo que refuerza la unidad y transmite orden.</li>
                        </ul>
                        <p class="mt-4">Esto asegura que, al interactuar con cualquiera de las líneas de negocio, el cliente siempre perciba la misma esencia de SURA.</p>
                    </div>

                    <div id="mensaje" class="content-section hidden">
                        <h2 class="text-2xl font-bold sura-blue mb-4">Simplificando la Elección</h2>
                        <p class="mb-4">La arquitectura de marca de SURA simplifica la elección del cliente y fortalece la percepción de integralidad.</p>
                        <p>En lugar de enfrentar un panorama fragmentado con marcas dispersas, los usuarios reconocen que todo proviene de un solo lugar confiable. Así, la estrategia no solo organiza la empresa, sino que construye una experiencia clara, cercana y consistente para el cliente.</p>
                    </div>
                </div>
            </div>
        </main>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const buttons = document.querySelectorAll('.nav-button');
            const contentSections = document.querySelectorAll('.content-section');

            buttons.forEach(button => {
                button.addEventListener('click', () => {
                    const targetId = button.dataset.target;

                    buttons.forEach(btn => btn.classList.remove('active'));
                    button.classList.add('active');

                    contentSections.forEach(section => {
                        if (section.id === targetId) {
                            section.classList.remove('hidden');
                        } else {
                            section.classList.add('hidden');
                        }
                    });
                });
            });
        });
    </script>
</body>
</html>

