\# Infografía Interactiva: Dinámica y Táctica del Balonmano

Recurso educativo interactivo tipo PWA (Progressive Web App) diseñado para adultos de 30 a 50 años, que explora los fundamentos tácticos, reglas y dinámicas del balonmano mediante una experiencia visual premium, no lineal y de profundidad progresiva.

\---

\#\# Arquitectura y Enfoque de Construcción

La aplicación está contenida en un \*\*único archivo HTML\*\* (\`index.html\`), cumpliendo con el requisito de distribución sencilla y ejecución sin dependencias locales. A pesar de ser un solo archivo, el código mantiene una \*\*separación lógica estricta\*\* entre Datos, Presentación y Comportamiento.

\#\#\# 1\. Filosofía Data-Driven  
Todo el contenido textual y configuraciones visuales están aislados en el objeto \`DATA\` dentro de JavaScript. Esto permite:  
\- Modificar contenido (reglas, preguntas, posiciones) sin tocar la estructura del DOM.  
\- Escalar la aplicación fácilmente añadiendo nuevos módulos al objeto.  
\- Simular la carga desde una API o JSON externo.

\#\#\# 2\. Renderizado Dinámico (Vanilla JS)  
El HTML estático es mínimo (solo contenedores estructurales). El DOM se construye dinámicamente mediante funciones de renderizado (\`renderBento()\`, \`renderPosiciones()\`, \`renderQuiz()\`, etc.) que iteran sobre el objeto \`DATA\`. Esto garantiza que el contenido siempre esté sincronizado con la fuente de datos.

\#\#\# 3\. Sistema de Diseño (CSS Variables)  
El tema visual se controla mediante variables CSS (\`--bg\`, \`--accent\`, \`--card\`, etc.) en el pseudo-clase \`:root\`, permitiendo:  
\- \*\*Dark Mode Sofisticado\*\* por defecto.  
\- \*\*Modo Alto Contraste\*\* alternando el atributo \`data-theme="high-contrast"\` en el \`\<html\>\`.

\---

\#\# Stack Tecnológico

| Tecnología | Uso en la Aplicación |  
| :--- | :--- |  
| \*\*HTML5\*\* | Estructura semántica (\`\<main\>\`, \`\<section\>\`, \`\<nav\>\`), accesibilidad nativa y contenedores. |  
| \*\*CSS3\*\* | Custom Properties para temas, Grid/Flexbox para layouts (Bento UI), Glassmorphism, animaciones de entrada y transiciones. |  
| \*\*Bootstrap 5\*\* | Sistema de grillas responsivo (\`col-md-6\`, \`col-lg-4\`), sistema de navegación (Navbar), y utilidades de espaciado/display. |  
| \*\*JavaScript Vanilla\*\* | Lógica de negocio, manipulación del DOM, gestión de estado (Quiz), IntersectionObserver (animaciones), lógica PWA. |  
| \*\*Font Awesome 6\*\* | Iconografía lineal y táctica para tarjetas, métricas y botones. |  
| \*\*Google Fonts\*\* | Tipografías \`Outfit\` (display/títulos) y \`Source Sans 3\` (body/texto). |

\---

\#\# Estructura de Módulos (Secciones)

La aplicación se divide en los siguientes módulos funcionales, accesibles desde el Bento Grid y el mapa conceptual SVG:

1\. \*\*Hero Principal\*\*: Presentación con métricas clave y mapa mental SVG interactivo. Los nodos del mapa disparan \`scrollTo()\` hacia las secciones.  
2\. \*\*Bento Hub\*\*: Grilla CSS tipo dashboard con tarjetas modulares. Usa \`grid-template-columns: repeat(4, 1fr)\` con clases \`.wide\` y \`.tall\` para romper la monotonía.  
3\. \*\*Reglas Básicas\*\*: Tarjetas generadas dinámicamente explicando fundamentos reglamentarios (pasos, tiempo, sanciones).  
4\. \*\*La Cancha\*\*: Dibujo técnico en SVG inline (\`viewBox="0 0 440 240"\`). Incluye líneas de 6m, 7m y 9m. Las áreas poseen la clase \`.zone-hover\` que detecta eventos \`mouseenter/mousemove\` en JS para mostrar un tooltip contextual.  
5\. \*\*Posiciones\*\*: Grid responsivo con 7 tarjetas detalladas (Portero, Extremos, Laterales, Central, Pivote), incluyendo atributos y funciones tácticas.  
6\. \*\*Técnicas de Lanzamiento\*\*: Acordeones custom (sin depender de Bootstrap JS para lógica de estado) que detallan Suspensión, Apoyo y Cadera (cuándo, ventaja, lectura).  
7\. \*\*El Portero\*\*: Sección destacada con borde y fondo de gradiente especial, enfocada en su rol dual (defensa y contraataque).  
8\. \*\*Jugadas Tácticas\*\*: Tarjetas con borde lateral de color según tipo (Ofensiva/Mixta), explicando cruce, bloqueo, circulación, etc.  
9\. \*\*Autoevaluación\*\*: Motor de quiz propio. Gestiona estado (\`current\`, \`score\`, \`answered\`), valida respuestas, inyecta feedback DOM y calcula resultado final.  
10\. \*\*Footer/Takeaway\*\*: Síntesis visual de las 4 ideas clave del recurso.

\---

\#\# Características de Interacción y UI/UX

\- \*\*Scroll Reveal\*\*: Los elementos con clase \`.fade-up\` se observan mediante \`IntersectionObserver\` y reciben la clase \`.visible\` al entrar al viewport.  
\- \*\*Tooltips en Cancha\*\*: Posicionamiento absoluto relativo al contenedor, calculado con \`getBoundingClientRect()\` y coordenadas del ratón.  
\- \*\*Microinteracciones\*\*: Efectos \`:hover\` en tarjetas con \`translateY(-4px)\` y sombras de resplandor (\`box-shadow\` con colores acento).  
\- \*\*Navegación Activa\*\*: Otro \`IntersectionObserver\` marca el enlace activo en el navbar según la sección visible.

\---

\#\# Accesibilidad (a11y)

El código integra prácticas de accesibilidad robustas:

\- \*\*Skip Link\*\*: Enlace para saltar al contenido principal visible solo al navegar con Tab.  
\- \*\*Atributos ARIA\*\*: \`aria-label\`, \`aria-expanded\`, \`aria-controls\`, \`aria-live="polite"\` en el toast.  
\- \*\*Foco Visible\*\*: Regla \`:focus-visible\` con outline personalizado usando el color acento.  
\- \*\*Semántica\*\*: Uso correcto de landmarks (\`\<nav\>\`, \`\<main\>\`, \`\<footer\>\`) y roles implícitos.  
\- \*\*Movimiento Reducido\*\*: Media query \`@media (prefers-reduced-motion: reduce)\` que anula animaciones y transiciones.  
\- \*\*Alto Contraste\*\*: Sistema de temas toggleable que intensifica colores y bordes.

\---

\#\# Implementación PWA

La aplicación es instalable gracias a la lógica embebida:

1\. \*\*Manifest\*\*: Se genera dinámicamente como un objeto JSON, se convierte a \`Blob\` y se inyecta como URL en la etiqueta \`\<link rel="manifest"\>\`. El ícono es un SVG encodeado en Data URI.  
2\. \*\*Service Worker\*\*: El código del SW está contenido en un string template. Se intenta registrar como un Blob URL (nota: por restricciones de seguridad de los navegadores, el SW en producción debe servirse como archivo físico \`.js\`, pero la lógica estructural queda embebida y lista para extracción).

\---

\#\# Cómo Ejecutar y Desplegar

\#\#\# Ejecución Local  
Al ser un archivo único, basta con abrir el archivo \`index.html\` en cualquier navegador moderno.  
\`\`\`bash  
\# Navegación directa  
start index.html  \# Windows  
open index.html   \# macOS  
\`\`\`

\#\#\# Servidor Local (Recomendado para PWA)  
Para que el Service Worker y el Manifest funcionen correctamente, la app debe servirse bajo un protocolo seguro o localhost:  
\`\`\`bash  
\# Usando Python  
python3 \-m http.server 8000

\# Usando Node.js (npx)  
npx serve .  
\`\`\`  
Luego acceder a \`http://localhost:8000\`.

\#\#\# Despliegue en Producción  
Sube el archivo \`index.html\` a cualquier hosting estático (Netlify, Vercel, GitHub Pages, AWS S3). Para máxima compatibilidad PWA, extrae el código del Service Worker a un archivo \`sw.js\` en el mismo directorio raíz y actualiza la ruta en el registro del \`navigator.serviceWorker.register()\`.  
