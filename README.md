# MIH Web - Agencia de Embarques SpA

Proyecto principal para la *Landing Page* y plataforma pública de **Agencia de Embarques MIH SpA**.

## 🛠️ Arquitectura
*   **Framework Backend:** Laravel 11.x
*   **Framework Frontend:** Vue 3 (Composition API) + Vite
*   **Estilos:** Tailwind CSS
*   **Cumplimiento Legal:** Integración nativa con la **Ley 21.719** de Protección de Datos (Consentimiento de Cookies y Modal de Privacidad).

## 🚀 Instalación Local

```bash
# Instalar dependencias PHP
composer install

# Instalar dependencias Node
npm install

# Copiar variables de entorno
cp .env.example .env

# Generar llave de la app
php artisan key:generate

# Levantar entorno de desarrollo
npm run dev
php artisan serve
```

## 🤖 Agentes y Automatización
Este repositorio está vinculado a los flujos asistidos de **Google Antigravity**. 
Para registrar cambios de manera estructurada, utiliza el comando `/git_smart_commit` desde la consola del agente.
