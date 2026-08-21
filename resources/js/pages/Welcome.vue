<script setup lang="ts">
import { Head } from '@inertiajs/vue3';
import { ref, onMounted } from 'vue';

const isDark = ref(false);
const activeModal = ref<'none' | 'privacy' | 'terms'>('none');
const showCookieBanner = ref(false);

const acceptCookies = () => {
    localStorage.setItem('cookies_accepted', 'true');
    showCookieBanner.value = false;
};

const toggleDark = () => {
    isDark.value = !isDark.value;
    document.documentElement.classList.toggle('dark', isDark.value);
    localStorage.setItem('theme', isDark.value ? 'dark' : 'light');
};

onMounted(() => {
    const savedTheme = localStorage.getItem('theme');
    if (savedTheme === 'dark') {
        isDark.value = true;
        document.documentElement.classList.add('dark');
    } else if (savedTheme === 'light') {
        isDark.value = false;
        document.documentElement.classList.remove('dark');
    } else {
        isDark.value = document.documentElement.classList.contains('dark');
    }
    
    if (!localStorage.getItem('cookies_accepted')) {
        setTimeout(() => { showCookieBanner.value = true; }, 1500);
    }
});
</script>

<template>
    <Head>
        <title>Agencia de Embarques MIH | Comercio Exterior & Operaciones Portuarias</title>
        <meta name="description" content="Agencia de Embarques MIH SpA. Coordinación física y documental con precisión exacta. Operaciones aduaneras, portuarias y logísticas en Valparaíso y todo Chile." />
        <meta name="keywords" content="agencia de embarques, comercio exterior, operaciones portuarias, aduanas, logística, Valparaíso, Chile, MIH, Agentes de Aduana, SAG" />
        
        <!-- Open Graph / Redes Sociales -->
        <meta property="og:type" content="website" />
        <meta property="og:url" content="https://mih.cl/" />
        <meta property="og:title" content="Agencia de Embarques MIH | Operaciones Portuarias" />
        <meta property="og:description" content="Supervisamos el flujo crítico documental y de terreno en los principales terminales de Chile, mitigando sobreestadías y garantizando trazabilidad total." />
        <meta property="og:image" content="https://mih.cl/img/logo-black.svg" />

        <!-- Twitter Cards -->
        <meta name="twitter:card" content="summary_large_image" />
        <meta name="twitter:title" content="Agencia de Embarques MIH | Logística y Aduanas" />
        <meta name="twitter:description" content="Coordinación física y documental con precisión exacta para el comercio exterior en Chile." />
        <meta name="twitter:image" content="https://mih.cl/img/logo-black.svg" />

        <!-- Datos Estructurados JSON-LD (SEO Local Business) -->
        <script type="application/ld+json">
        {
          "@context": "https://schema.org",
          "@type": "LogisticsService",
          "name": "Agencia de Embarques MIH SpA",
          "image": "https://mih.cl/img/logo-black.svg",
          "url": "https://mih.cl",
          "telephone": "+56 32 342 3242",
          "email": "contacto@mih.cl",
          "address": {
            "@type": "PostalAddress",
            "streetAddress": "Almirante Señoret 70",
            "addressLocality": "Valparaíso",
            "addressCountry": "CL"
          },
          "description": "Servicios de coordinación logística, aduanera y operaciones portuarias en Chile."
        }
        </script>
    </Head>

    <div class="min-h-screen bg-slate-100 text-slate-900 dark:bg-slate-900 dark:text-slate-50 font-sans antialiased selection:bg-[#f59d02] selection:text-slate-900 transition-colors duration-300"
         style="background-image: radial-gradient(var(--tw-gradient-stops)); --tw-gradient-from: #cbd5e1 1px; --tw-gradient-to: transparent 1px; background-size: 32px 32px;"
         :class="{'[--tw-gradient-from:#334155]': isDark, '[--tw-gradient-from:#cbd5e1]': !isDark}">
         
        <header class="sticky top-0 z-50 border-b border-slate-300 dark:border-slate-700 bg-white/95 dark:bg-slate-900/95 backdrop-blur-md transition-colors duration-300">
            <div class="mx-auto flex max-w-7xl items-center justify-between px-6 py-4 sm:px-8">
                <div class="flex items-center gap-3">
                    <img src="/img/logo-black.svg" alt="MIH" class="h-11 w-auto object-contain block dark:hidden">
                    <img src="/img/logo-white.svg" alt="MIH" class="h-11 w-auto object-contain hidden dark:block">
                </div>

                <nav class="hidden md:flex items-center gap-8">
                    <a href="#operaciones" class="text-sm font-semibold text-slate-600 dark:text-slate-300 transition-colors hover:text-[#f59d02] dark:hover:text-[#f59d02]">Operaciones</a>
                    <a href="#servicios" class="text-sm font-semibold text-slate-600 dark:text-slate-300 transition-colors hover:text-[#f59d02] dark:hover:text-[#f59d02]">Servicios</a>
                    <a href="#contacto" class="text-sm font-semibold text-slate-600 dark:text-slate-300 transition-colors hover:text-[#f59d02] dark:hover:text-[#f59d02]">Contacto</a>

                    <button @click="toggleDark" class="rounded-lg p-2 border-2 border-slate-300 dark:border-slate-700 text-[#f59d02] hover:bg-[#f59d02]/10 transition-colors cursor-pointer flex items-center justify-center" title="Cambiar modo visual" type="button">
                        <svg v-if="!isDark" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z" />
                        </svg>
                        <svg v-else class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364-6.364l-.707.707M6.343 17.657l-.707.707m2.828 0l.707-.707m12.022-12.022l.707-.707M12 7a5 5 0 100 10 5 5 0 000-10z" />
                        </svg>
                    </button>

                    <a href="/login" class="inline-flex items-center justify-center rounded-lg bg-[#f59d02] px-6 py-2.5 text-sm font-bold text-slate-950 shadow-md shadow-[#f59d02]/30 transition-all hover:bg-[#d98502] hover:scale-[1.02]">
                        Plataforma Clientes
                    </a>
                </nav>
            </div>
        </header>

        <main>
        <section class="relative bg-white dark:bg-slate-950 pt-24 pb-24 lg:pt-36 lg:pb-36 overflow-hidden border-b border-slate-300 dark:border-slate-700 transition-colors duration-300">
            <div class="absolute inset-0 bg-[radial-gradient(ellipse_at_top_right,rgba(245,157,2,0.08),transparent_50%)]"></div>

            <div class="mx-auto max-w-7xl px-6 sm:px-8 grid grid-cols-1 gap-12 lg:grid-cols-12 lg:gap-8 items-center relative z-10">
                <div class="lg:col-span-7 space-y-6 text-center lg:text-left">
                    <div class="inline-flex items-center gap-2 rounded-full border-2 border-slate-300 dark:border-slate-700 bg-white/80 dark:bg-slate-900/80 px-4 py-1 text-xs font-bold text-[#f59d02]">
                        <span class="flex h-2.5 w-2.5 rounded-full bg-emerald-500 animate-pulse"></span>
                        Soporte Operativo Activo · Nodos Portuarios
                    </div>
                    <h1 class="text-4xl font-extrabold tracking-tight sm:text-5xl xl:text-6xl leading-[1.15]">
                        Coordinación física y documental con <span class="text-[#f59d02] underline decoration-wavy decoration-2">precisión exacta</span>
                    </h1>
                    <p class="text-base sm:text-lg text-slate-600 dark:text-slate-300 max-w-xl mx-auto lg:mx-0 font-medium leading-relaxed tracking-wide">
                        No dejamos su carga al azar. Supervisamos el flujo crítico documental y de terreno en los principales terminales de Chile, mitigando sobreestadías y garantizando trazabilidad total.
                    </p>
                    <div class="flex flex-col sm:flex-row gap-4 justify-center lg:justify-start pt-4">
                        <a href="#contacto" class="rounded-lg bg-[#f59d02] px-7 py-4 text-center text-sm font-bold text-slate-950 shadow-lg shadow-[#f59d02]/30 transition-all hover:bg-[#d98502]">
                            Asignar Nuevo Embarque
                        </a>
                        <a href="#servicios" class="rounded-lg border-2 border-slate-300 dark:border-slate-700 bg-white/40 dark:bg-slate-900/40 px-7 py-4 text-center text-sm font-bold transition-all hover:bg-slate-200 dark:hover:bg-slate-800">
                            Ver Portafolio de Servicios
                        </a>
                    </div>
                </div>

                <div class="lg:col-span-5 w-full max-w-md mx-auto lg:max-w-none">
                    <div class="relative rounded-2xl border-2 border-slate-300 dark:border-slate-700 bg-white dark:bg-slate-800 p-6 shadow-2xl transition-colors duration-300">
                        <div class="flex items-center justify-between border-b border-slate-300 dark:border-slate-700 pb-4 mb-4">
                            <div class="flex items-center gap-2">
                                <div class="h-3 w-3 rounded-full bg-[#f59d02]"></div>
                                <div class="h-3 w-3 rounded-full bg-slate-400"></div>
                                <div class="h-3 w-3 rounded-full bg-slate-500"></div>
                            </div>
                            <span class="text-xs font-bold font-mono text-slate-600 dark:text-slate-300">MIH_OPERATIONS_DESK</span>
                        </div>

                        <div class="space-y-4">
                            <p class="text-xs font-bold uppercase tracking-widest text-[#f59d02]">Monitoreo de Servicios</p>

                            <div class="rounded-lg border-2 border-slate-300 dark:border-slate-700 bg-slate-100 dark:bg-slate-950/50 p-4 flex items-center justify-between">
                                <div>
                                    <p class="text-xs font-bold font-mono">Tramitación Documental</p>
                                    <p class="text-[11px] font-medium text-slate-600 dark:text-slate-300 mt-0.5">Revisión de Carpetas / Visaciones</p>
                                </div>
                                <span class="rounded bg-[#f59d02]/10 px-2 py-1 text-[10px] font-bold text-[#f59d02] border border-[#f59d02]/30">Línea Operativa</span>
                            </div>

                            <div class="rounded-lg border-2 border-slate-300 dark:border-slate-700 bg-slate-100 dark:bg-slate-950/50 p-4 flex items-center justify-between">
                                <div>
                                    <p class="text-xs font-bold font-mono">Inspección Física en Zona Primaria</p>
                                    <p class="text-[11px] font-medium text-slate-600 dark:text-slate-300 mt-0.5">Coordinación de Aforos y Sellos</p>
                                </div>
                                <span class="rounded bg-[#f59d02]/10 px-2 py-1 text-[10px] font-bold text-[#f59d02] border border-[#f59d02]/30">En Terreno</span>
                            </div>

                            <div class="pt-2">
                                <a href="/login" class="flex w-full items-center justify-center gap-2 rounded-lg border-2 border-dashed border-slate-300 dark:border-slate-700 py-3.5 text-xs font-bold text-slate-600 dark:text-slate-300 hover:text-[#f59d02] dark:hover:text-[#f59d02] hover:border-[#f59d02]/60 dark:hover:border-[#f59d02]/60 transition-colors">
                                    <svg class="h-4 w-4 text-[#f59d02]" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z" />
                                    </svg>
                                    Ingresar al Sistema Corporativo
                                </a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="operaciones" class="py-28 lg:py-40 border-b border-slate-300 dark:border-slate-700 transition-colors duration-300">
            <div class="mx-auto max-w-7xl px-6 sm:px-8">
                <div class="grid grid-cols-1 gap-14 lg:grid-cols-2 items-center">
                    <div class="relative group">
                        <div class="absolute -inset-2 rounded-xl bg-gradient-to-r from-[#f59d02] to-amber-600 opacity-20 blur-lg group-hover:opacity-30 transition-opacity"></div>
                        <div class="relative overflow-hidden rounded-xl border-2 border-slate-300 dark:border-slate-700 bg-white dark:bg-slate-800 shadow-2xl">
                            <img src="/img/operaciones.jpg" alt="Supervisión en Puerto" class="w-full object-cover aspect-[16/10] opacity-95 transition-all duration-500 group-hover:scale-[1.01]">
                            <div class="absolute inset-0 bg-gradient-to-t from-white/90 via-transparent to-transparent dark:from-slate-950/90"></div>
                            <div class="absolute bottom-6 left-6 right-6">
                                <span class="text-[10px] font-bold uppercase tracking-widest text-slate-950 bg-[#f59d02] px-2.5 py-1 rounded">Control de Cadena Logística</span>
                                <h4 class="text-lg font-bold mt-2">Presencia directa en los terminales del país</h4>
                            </div>
                        </div>
                    </div>

                    <div class="space-y-6">
                        <h2 class="text-3xl font-bold tracking-tight sm:text-4xl leading-tight">
                            Un puente sólido entre la <span class="text-[#f59d02]">documentación</span> y el puerto
                        </h2>
                        <p class="text-slate-600 dark:text-slate-300 font-medium text-sm sm:text-base leading-relaxed tracking-wide">
                            Heredamos la claridad informativa de nuestra plataforma tradicional. Separamos los procesos críticos para que tanto exportadores como importadores identifiquen el estado real de sus operaciones en aduana y zona primaria.
                        </p>

                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-6 pt-2">
                            <div class="border-l-4 border-[#f59d02] pl-4">
                                <h4 class="text-sm font-bold uppercase tracking-wider">Respaldo Digital</h4>
                                <p class="text-xs font-semibold text-slate-600 dark:text-slate-300 mt-1">Repositorio centralizado de carpetas de despacho escaneadas.</p>
                            </div>
                            <div class="border-l-4 border-[#f59d02] pl-4">
                                <h4 class="text-sm font-bold uppercase tracking-wider">Mitigación de Riesgos</h4>
                                <p class="text-xs font-semibold text-slate-600 dark:text-slate-300 mt-1">Evitamos multas por mala clasificación o retrasos aduaneros.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section class="relative h-[50vh] bg-cover bg-center bg-no-repeat bg-fixed border-y-2 border-slate-300 dark:border-slate-700" style="background-image: url('/img/hero-bg.jpg');">
            <div class="absolute inset-0 bg-slate-100/50 dark:bg-slate-950/75 backdrop-blur-[2px]"></div>
            <div class="absolute inset-0 flex items-center justify-center text-center px-4">
                <div class="max-w-2xl border-2 border-[#f59d02] bg-white/95 dark:bg-slate-950/90 backdrop-blur-md p-8 rounded-xl shadow-2xl">
                    <p class="text-xs font-bold uppercase tracking-widest text-[#f59d02] mb-2">Infraestructura Tecnológica</p>
                    <h3 class="text-xl sm:text-2xl font-bold">Seguridad y control operativo en zona primaria</h3>
                </div>
            </div>
        </section>

        <section id="servicios" class="py-36 lg:py-48 border-b border-slate-300 dark:border-slate-700 transition-colors duration-300">
            <div class="mx-auto max-w-7xl px-6 sm:px-8">
                <div class="text-center space-y-4 max-w-2xl mx-auto">
                    <span class="text-xs font-bold uppercase tracking-widest text-[#f59d02]">Estructura de Servicios</span>
                    <h2 class="text-3xl font-bold tracking-tight sm:text-4xl">Nuestras Líneas de Acción</h2>
                    <p class="text-sm font-medium text-slate-600 dark:text-slate-300">
                        Soluciones integrales diseñadas con estricto apego a las normativas de aduana y logística portuaria chilena.
                    </p>
                </div>

                <div class="mt-16 grid grid-cols-1 gap-8 md:grid-cols-3">
                    <div class="bg-white dark:bg-slate-800 border-2 border-slate-300 dark:border-slate-700 rounded-xl p-6 hover:border-[#f59d02] transition-all group shadow-md">
                        <div class="h-11 w-11 rounded-lg bg-[#f59d02]/10 flex items-center justify-center text-[#f59d02] group-hover:bg-[#f59d02] group-hover:text-slate-950 transition-colors">
                            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
                            </svg>
                        </div>
                        <h3 class="text-lg font-bold mt-5">Gestión Documental Completa</h3>
                        <p class="text-xs font-medium text-slate-600 dark:text-slate-300 mt-2 leading-relaxed">
                            Confección, revisión y tramitación experta de la documentación necesaria ante el Servicio Nacional de Aduanas y entidades portuarias.
                        </p>
                    </div>

                    <div class="bg-white dark:bg-slate-800 border-2 border-slate-300 dark:border-slate-700 rounded-xl p-6 hover:border-[#f59d02] transition-all group shadow-md">
                        <div class="h-11 w-11 rounded-lg bg-[#f59d02]/10 flex items-center justify-center text-[#f59d02] group-hover:bg-[#f59d02] group-hover:text-slate-950 transition-colors">
                            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10" />
                            </svg>
                        </div>
                        <h3 class="text-lg font-bold mt-5">Coordinación en Zona Primaria</h3>
                        <p class="text-xs font-medium text-slate-600 dark:text-slate-300 mt-2 leading-relaxed">
                            Presencia directa en los patios de acopio. Supervisamos aforos, revisiones del SAG/Sernapesca y velamos por la integridad física de los sellos.
                        </p>
                    </div>

                    <div class="bg-white dark:bg-slate-800 border-2 border-slate-300 dark:border-slate-700 rounded-xl p-6 hover:border-[#f59d02] transition-all group shadow-md">
                        <div class="h-11 w-11 rounded-lg bg-[#f59d02]/10 flex items-center justify-center text-[#f59d02] group-hover:bg-[#f59d02] group-hover:text-slate-950 transition-colors">
                            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M11 3.055A9.003 9.003 0 1020.945 13H11V3.055z" />
                            </svg>
                        </div>
                        <h3 class="text-lg font-bold mt-5">Reportería & Información</h3>
                        <p class="text-xs font-medium text-slate-600 dark:text-slate-300 mt-2 leading-relaxed">
                            Creación de reportes diarios consolidados del estado de sus despachos para mantener informada a toda su cadena de distribución.
                        </p>
                    </div>
                </div>
            </div>
        </section>

        <section id="contacto" class="py-36 lg:py-48 transition-colors duration-300">
            <div class="mx-auto max-w-7xl px-6 sm:px-8 grid grid-cols-1 gap-12 lg:grid-cols-2 items-start">
                <div class="space-y-6">
                    <span class="text-xs font-bold uppercase tracking-widest text-[#f59d02]">Contacto Corporativo</span>
                    <h2 class="text-3xl font-bold tracking-tight sm:text-4xl">Comience a operar con nosotros</h2>
                    <p class="text-sm font-medium text-slate-600 dark:text-slate-300 leading-relaxed tracking-wide">
                        Nuestras oficinas centrales están ubicadas estratégicamente en el centro financiero e histórico de Valparaíso, facilitando las gestiones directas ante las direcciones nacionales de control aduanero y portuario.
                    </p>

                    <div class="space-y-4 pt-2 text-xs font-bold text-slate-600 dark:text-slate-300 font-mono">
                        <div class="flex items-center gap-3">
                            <svg class="h-5 w-5 text-[#f59d02]" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                            </svg>
                            <span>Almirante Señoret 70, Oficina 51, Valparaíso - Chile.</span>
                        </div>
                        <div class="flex items-center gap-3">
                            <svg class="h-5 w-5 text-[#f59d02]" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.94.725l.548 2.2a1 1 0 01-.321.988l-1.305.98a10.582 10.582 0 004.872 4.872l.98-1.305a1 1 0 01.988-.321l2.2.548a1 1 0 01.725.94V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
                            </svg>
                            <span>Fono Operaciones: 032-3423242</span>
                        </div>
                    </div>
                </div>

                <div class="rounded-xl border-2 border-slate-300 dark:border-slate-700 bg-white dark:bg-slate-800 p-8 shadow-xl transition-colors duration-300 flex flex-col justify-center gap-6 text-center sm:text-left h-full">
                    <p class="text-sm font-bold text-slate-600 dark:text-slate-300 mb-2">Comuníquese directamente con Operaciones:</p>
                    
                    <a href="mailto:contacto@mih.cl" class="flex items-center justify-center sm:justify-start gap-4 rounded-lg bg-slate-100 dark:bg-slate-900 px-6 py-4 transition-all hover:bg-slate-200 dark:hover:bg-slate-950 hover:scale-[1.02] border border-slate-300 dark:border-slate-700">
                        <div class="h-10 w-10 rounded-full bg-[#f59d02]/10 flex items-center justify-center text-[#f59d02] shrink-0">
                            <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                            </svg>
                        </div>
                        <div>
                            <span class="block text-[10px] font-bold uppercase tracking-widest text-slate-500">Correo Corporativo</span>
                            <span class="block text-sm font-bold text-slate-900 dark:text-white mt-0.5">contacto@mih.cl</span>
                        </div>
                    </a>

                    <a href="tel:+56323423242" class="flex items-center justify-center sm:justify-start gap-4 rounded-lg bg-slate-100 dark:bg-slate-900 px-6 py-4 transition-all hover:bg-slate-200 dark:hover:bg-slate-950 hover:scale-[1.02] border border-slate-300 dark:border-slate-700">
                        <div class="h-10 w-10 rounded-full bg-[#f59d02]/10 flex items-center justify-center text-[#f59d02] shrink-0">
                            <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.94.725l.548 2.2a1 1 0 01-.321.988l-1.305.98a10.582 10.582 0 004.872 4.872l.98-1.305a1 1 0 01.988-.321l2.2.548a1 1 0 01.725.94V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
                            </svg>
                        </div>
                        <div>
                            <span class="block text-[10px] font-bold uppercase tracking-widest text-slate-500">Fono Operaciones Central</span>
                            <span class="block text-sm font-bold text-slate-900 dark:text-white mt-0.5">+56 32 342 3242</span>
                        </div>
                    </a>
                </div>

            </div>
        </section>
        </main>

                <footer class="bg-white dark:bg-slate-950/60 py-12 text-xs border-t-2 border-slate-300 dark:border-slate-700 transition-colors duration-300">
            <div class="mx-auto max-w-7xl px-6 sm:px-8 flex flex-col sm:flex-row items-center justify-between gap-6">
                <div class="flex items-center gap-3">
                    <span class="font-bold tracking-tight">MIH</span>
                    <span class="text-slate-600 dark:text-slate-300 font-medium">| Agencia de Embarques MIH SpA</span>
                </div>
                
                <!-- NUEVO: Enlaces Legales (Ley 21.719) -->
                <div class="flex flex-col sm:flex-row items-center gap-4 text-center sm:text-right">
                    <div class="flex items-center gap-4 text-slate-500 dark:text-slate-400 font-medium">
                        <button type="button" @click="activeModal = 'terms'" class="hover:text-[#f59d02] transition-colors cursor-pointer">Términos de Servicio</button>
                        <span>&bull;</span>
                        <button type="button" @click="activeModal = 'privacy'" class="hover:text-[#f59d02] transition-colors cursor-pointer">Política de Privacidad (Ley 21.719)</button>
                    </div>
                    <p class="font-bold text-slate-600 dark:text-slate-300">&copy; {{ new Date().getFullYear() }} Agencia de Embarques MIH.</p>
                </div>
            </div>
        </footer>



        <!-- Cookie Banner (Ley 21.719 / RGPD) -->
        <transition 
            enter-active-class="transition duration-500 ease-out transform"
            enter-from-class="translate-y-full opacity-0"
            enter-to-class="translate-y-0 opacity-100"
            leave-active-class="transition duration-300 ease-in transform"
            leave-from-class="translate-y-0 opacity-100"
            leave-to-class="translate-y-full opacity-0">
            
            <div v-if="showCookieBanner" class="fixed bottom-0 left-0 right-0 z-[90] p-4 sm:p-6 sm:bottom-4 sm:left-4 sm:right-auto sm:max-w-sm w-full">
                <div class="bg-slate-900 dark:bg-slate-800 rounded-2xl shadow-2xl border border-slate-700 p-5 relative overflow-hidden">
                    <div class="absolute -top-10 -right-10 w-24 h-24 bg-[#f59d02]/10 rounded-full blur-2xl"></div>
                    
                    <div class="flex items-start gap-4">
                        <div class="text-[#f59d02] shrink-0 mt-0.5">
                            <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M12 11c0 3.517-1.009 6.799-2.753 9.571m-3.44-2.04l.054-.09A13.916 13.916 0 008 11a4 4 0 118 0c0 1.017-.07 2.019-.203 3m-2.118 6.844A21.88 21.88 0 0015.171 17m3.839 1.132c.645-2.266.99-4.659.99-7.132A8 8 0 008 4.07M3 15.364c.64-1.319 1-2.8 1-4.364 0-1.457.39-2.823 1.07-4" />
                            </svg>
                        </div>
                        <div>
                            <h3 class="text-white font-bold text-[13px] mb-1">Control de Privacidad</h3>
                            <p class="text-slate-400 text-[11px] leading-relaxed">
                                Utilizamos cookies técnicas para asegurar el funcionamiento del sitio y analíticas para mejorar su experiencia, acorde a la Ley 21.719. Al continuar, usted acepta nuestras políticas.
                            </p>
                        </div>
                    </div>
                    <div class="mt-4 flex items-center justify-end gap-3 border-t border-slate-700/50 pt-4">
                        <button type="button" @click="showCookieBanner = false" class="text-[11px] font-bold text-slate-400 hover:text-white transition-colors px-2 py-2">
                            Solo Esenciales
                        </button>
                        <button type="button" @click="acceptCookies" class="rounded-lg bg-[#f59d02] px-4 py-2 text-[11px] font-bold text-slate-950 shadow-md transition-all hover:bg-[#d98502]">
                            Aceptar Cookies
                        </button>
                    </div>
                </div>
            </div>
        </transition>

        <!-- Modal Legal -->
        <transition name="modal">
            <div v-if="activeModal !== 'none'" class="fixed inset-0 z-[100] flex items-center justify-center p-4 sm:p-6" aria-labelledby="modal-title" role="dialog" aria-modal="true">
            <!-- Fondo Oscuro -->
            <div class="fixed inset-0 bg-slate-900/70 backdrop-blur-sm transition-opacity" @click="activeModal = 'none'"></div>

            <!-- Contenedor del Modal -->
            <div class="modal-content relative w-full max-w-2xl overflow-hidden rounded-2xl bg-white dark:bg-slate-900 shadow-2xl border border-slate-200 dark:border-slate-800 flex flex-col max-h-[85vh]">
                
                <!-- Cabecera -->
                <div class="flex items-center justify-between border-b border-slate-200 dark:border-slate-800 px-6 py-4 bg-slate-50 dark:bg-slate-900/50">
                    <h3 class="text-lg font-bold text-slate-900 dark:text-white flex items-center gap-2" id="modal-title">
                        <svg v-if="activeModal === 'privacy'" class="w-5 h-5 text-[#f59d02]" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z" />
                        </svg>
                        <svg v-else class="w-5 h-5 text-[#f59d02]" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
                        </svg>
                        {{ activeModal === 'privacy' ? 'Política de Privacidad' : 'Términos de Servicio' }}
                    </h3>
                    <button type="button" @click="activeModal = 'none'" class="rounded-lg p-1.5 text-slate-400 hover:bg-slate-200 hover:text-slate-600 dark:hover:bg-slate-800 dark:hover:text-slate-300 transition-colors">
                        <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                        </svg>
                    </button>
                </div>

                <!-- Contenido con scroll dinámico -->
                <div class="overflow-y-auto p-6 text-sm text-slate-600 dark:text-slate-300 space-y-4">
                    <template v-if="activeModal === 'privacy'">
                        <p><strong>1. Responsable del Tratamiento:</strong> Agencia de Embarques MIH SpA, con domicilio en Almirante Señoret 70, Valparaíso.</p>
                        <p><strong>2. Finalidad:</strong> La información recopilada mediante nuestros canales corporativos es utilizada exclusivamente para coordinar y ejecutar servicios aduaneros, portuarios y logísticos solicitados por nuestros clientes.</p>
                        <p><strong>3. Base Legal:</strong> El tratamiento se rige por la Ley N° 19.628 sobre Protección de la Vida Privada (actualizada por la Ley 21.719). Sus datos no serán cedidos a terceros, salvo requerimientos legales o aduaneros dictaminados por el Estado de Chile.</p>
                        <p><strong>4. Derechos ARCO:</strong> Usted puede ejercer sus derechos de Acceso, Rectificación, Cancelación u Oposición enviando un correo a <a href="mailto:contacto@mih.cl" class="text-[#f59d02] font-semibold hover:underline">contacto@mih.cl</a>.</p>
                        <p><strong>5. Conservación:</strong> Los datos se almacenan en servidores seguros bajo altos estándares de la industria, durante el tiempo necesario para la prestación del servicio logístico y documental.</p>
                    </template>
                    <template v-else>
                        <p><strong>1. Alcance de los Servicios:</strong> Agencia de Embarques MIH actúa como coordinador logístico y documental en la tramitación de despachos de exportación e importación ante el Servicio Nacional de Aduanas.</p>
                        <p><strong>2. Responsabilidad Operativa:</strong> MIH asume la coordinación diligente de aforos y tramitaciones, pero no se hace responsable por retrasos, multas o bloqueos dictaminados de forma unilateral por SAG, Sernapesca, Aduana u otras autoridades fiscales/marítimas.</p>
                        <p><strong>3. Confidencialidad:</strong> Toda información comercial de sus despachos será tratada con estricta reserva por nuestro personal de oficina y terreno.</p>
                        <p><strong>4. Ajustes Tarifarios:</strong> Cualquier tarifa proyectada puede sufrir variaciones si las condiciones de la carga (pesos, dimensiones, sobreestadías) difieren de lo declarado inicialmente en la matriz documental.</p>
                        <p><strong>5. Jurisdicción:</strong> Cualquier controversia derivada de la prestación de los servicios será sometida a la jurisdicción de los Tribunales Ordinarios de Valparaíso, Chile.</p>
                    </template>
                </div>

                <!-- Pie del modal -->
                <div class="border-t border-slate-200 dark:border-slate-800 bg-slate-50 dark:bg-slate-900/50 px-6 py-4 flex justify-end">
                    <button type="button" @click="activeModal = 'none'" class="rounded-lg bg-[#f59d02] px-6 py-2 text-sm font-bold text-slate-950 shadow-md transition-all hover:bg-[#d98502]">
                        Entendido
                    </button>
                </div>
            </div>
        </div>
        </transition>

    </div>
</template>

<style>
html { scroll-behavior: smooth; }

/* Animaciones del Modal Legal */
.modal-enter-active,
.modal-leave-active {
    transition: opacity 0.3s ease;
}
.modal-enter-active .modal-content {
    transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
}
.modal-leave-active .modal-content {
    transition: all 0.2s ease-in;
}
.modal-enter-from,
.modal-leave-to {
    opacity: 0;
}
.modal-enter-from .modal-content {
    opacity: 0;
    transform: translateY(20px) scale(0.95);
}
.modal-leave-to .modal-content {
    opacity: 0;
    transform: translateY(10px) scale(0.98);
}
</style>
