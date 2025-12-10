<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tienda de Electrodomésticos</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&family=Roboto&display=swap" rel="stylesheet">
<style>
/* Reset básico */
* { margin: 0; padding: 0; box-sizing: border-box; }

/* Fondo y texto general */
body {
    font-family: 'Roboto', Arial, sans-serif;
    background: #203a43; /* fondo oscuro sólido para contraste */
    color: #f0f0f0; /* texto general claro */
}

/* Header */
header {
    background-color: #111;
    color: #00ffff;
    text-align: center;
    padding: 2rem;
    font-family: 'Orbitron', sans-serif;
    box-shadow: 0 4px 10px rgba(0, 255, 255, 0.2);
}

/* Navegación */
nav { text-align: center; margin: 1rem 0; }
nav a {
    color: #00ffff;
    margin: 0 1rem;
    text-decoration: none;
    font-weight: bold;
    cursor: pointer;
}
nav a:hover { text-decoration: underline; }

/* Main */
main { padding: 2rem; max-width: 900px; margin: auto; }
section { display: none; }
section.active { display: block; }

/* Imágenes */
img { max-width: 100%; margin: 1rem 0; border-radius: 10px; }

/* Preformato para JSON */
pre {
    background: #e0e0e0; /* fondo claro para contrastar */
    padding: 1rem;
    border-radius: 10px;
    overflow-x: auto;
    color: #000000; /* texto negro */
}

/* Contacto */
p.contacto { margin: 0.5rem 0; }
</style>
</head>
<body>
<header>
    <h1>Mi Tienda de Electrodomésticos</h1>
</header>

<nav>
    <a onclick="mostrarSeccion('inicio')">Inicio</a>
    <a onclick="mostrarSeccion('resultados')">Resultados</a>
    <a onclick="mostrarSeccion('informacion')">Información</a>
</nav>

<main>
    <!-- Sección Inicio -->
    <section id="inicio" class="active">
        <h2>Bienvenido a nuestra tienda</h2>
        <p>Somos una tienda especializada en electrodomésticos modernos y confiables para tu hogar.</p>
        <p>Ofrecemos productos de alta calidad, desde neveras y lavadoras hasta pequeños electrodomésticos, todos con garantía y excelente servicio al cliente.</p>
        <p>Nuestra misión es hacer tu vida más fácil con productos que combinan tecnología, eficiencia y diseño.</p>
        <img src="https://img.freepik.com/fotos-premium/electrodomesticos-cocina-licuadora-tostadora-cafetera-picadora-carne-horno-microondas-hervidor-3d_505080-344.jpg?semt=ais_hybrid&w=740&q=80" alt="Electrodomésticos en cocina">
    </section>

    <!-- Sección Resultados -->
    <section id="resultados">
        <p>En esta sección se muestran los resultados de nuestra base de datos de ventas. Aquí encontrarás información general sobre el desempeño de los productos y tiendas, incluyendo totales, promedios, máximos y mínimos. Los datos pueden incluir ventas por tienda, promedios por producto y rangos de ventas, presentados en formato JSON para su consulta.</p>
        <pre id="jsonbin">Cargando datos...</pre>
    </section>

    <!-- Sección Información -->
    <section id="informacion">
        <h2>Contacto</h2>
        <p class="contacto"><strong>Correo personal:</strong> sgt116sandoval@gmail.com</p>
        <p class="contacto"><strong>Celular:</strong> 3006888066</p>
        <p class="contacto"><strong>Correo institucional:</strong> santiagossandoval@unibarranquilla.edu.co</p>
    </section>
</main>

<script>
// Función para mostrar secciones
function mostrarSeccion(id) {
    document.querySelectorAll('section').forEach(sec => sec.classList.remove('active'));
    document.getElementById(id).classList.add('active');
}

// Cargar la última versión del JSONBin
const apiUrl = "https://api.jsonbin.io/v3/b/69398d3eae596e708f906838/latest";
fetch(apiUrl, {
    method: "GET",
    headers: {
        "X-Master-Key": "$2a$10$J3Whmspgd/Bg6SUFg9WTVeV7bLY8jZJiubqOURZpz7mJ3KjQ6asXq"
    }
})
.then(response => response.json())
.then(data => {
    const jsonElement = document.getElementById("jsonbin");
    jsonElement.textContent = JSON.stringify(data.record, null, 4);
})
.catch(err => {
    console.error("Error cargando los resultados:", err);
    document.getElementById("jsonbin").textContent = "No se pudieron cargar los datos.";
});
</script>
</body>
</html>
