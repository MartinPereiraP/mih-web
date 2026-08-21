# Changelog
Todos los cambios notables de este proyecto se documentarán en este archivo.
El formato está basado en [Keep a Changelog](https://keepachangelog.com/es-ES/1.0.0/).

## [Sin liberar]
### Añadido
- **Cobertura Aduanera:** Se incorporaron los puertos y pasos fronterizos de Arica (Chacalluta), Talcahuano, San Vicente, Lirquén, Coronel y Cardenal Samoré en el footer de la plataforma.
- **Grilla Fotográfica Multimodal:** Nueva galería tipo *Masonry* en la sección Operaciones, con imágenes exclusivas para los tráficos Marítimo, Terrestre y Aéreo.

### Cambiado
- **Identidad SEO y Copywriting:** Se calibró la redacción del sitio para reflejar con exactitud el rol de "Gestión Documental y Operaciones Portuarias", delimitando la responsabilidad frente a servicios logísticos físicos puros.
- **Redirección de Plataforma:** Los botones de "Plataforma Clientes" ahora redirigen correctamente hacia el sistema operativo externo `https://mihsystem.cl`.
- **Terminología Técnica:** Se estandarizó el concepto de transporte a "Tráfico" (Marítimo, Terrestre, Aéreo) alineándose al Anexo 51 de la Ordenanza de Aduanas.
- **Mensaje IT:** El copy de Infraestructura Tecnológica fue refactorizado a un formato minimalista centrado en integraciones B2B vía API RESTful y EDI.

### Eliminado
- **Bloat Visual:** Se eliminaron banners intermedios redundantes y el efecto de desenfoque (`backdrop-blur`) que afectaba la nitidez fotográfica en los fondos fijos.



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

