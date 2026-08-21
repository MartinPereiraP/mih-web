# Changelog
Todos los cambios notables de este proyecto se documentarán en este archivo.
El formato está basado en [Keep a Changelog](https://keepachangelog.com/es-ES/1.0.0/).

## [Sin liberar]

### Añadido
- **Legal:** Se incorporó el archivo de Licencia Comercial (2016-2026), reafirmando el software como propietario para MIH SpA.
- **SEO/Metadatos:** Implementación de metadatos dinámicos `<Head>` para *Inertia* y generación de esquema *JSON-LD* (LogisticsService) enfocado al posicionamiento orgánico en Chile.

### Cambiado
- **UI (Rediseño):** Evolución visual de la Landing Page desde un minimalismo plano hacia un estándar corporativo de alta gama (*Apple-Style*).
  - Integración de efecto *Glassmorphism* profundo (`backdrop-blur-2xl`) en cabeceras y tarjetas.
  - Implementación de un fondo limpio iluminado con *Ambient Glow* ultra-suave.
  - Acentos tecnológicos preservados: tipografía monoespaciada para insignias, botones técnicos de línea punteada y micro-textura de cuadrícula oculta tras los cristales operativos.
- **Config:** Ajuste del `APP_NAME` predeterminado a "MIH" en el archivo de entorno de ejemplo.
- **UI:** Simplificación de la cabecera principal removiendo el subtítulo del logotipo en la Landing Page.

### Solucionado
- **Vue Compiler:** Resolución de *side-effects* en SSR mediante el reemplazo de tags de script regulares por `<component is="script">` para inyección segura de SEO estructurado.
- **Assets:** Generación y estandarización nativa del ícono de plataforma (`favicon.ico`) a partir del vector SVG oficial de MIH.

