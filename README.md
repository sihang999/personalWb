# Portafolio

A simple and easy Portafolio, referenced from Javier Castillo

## ✨ Características

- 🌍 **Soporte Bilingüe** - Inglés y Español con cambio de idioma fluido
- 🌙 **Modo Oscuro** - Toggle de tema claro/oscuro con persistencia en localStorage
- 📱 **Totalmente Responsivo** - Diseño mobile-first con menú hamburguesa para navegación móvil
- ⚡ **Alto Rendimiento** - Construido con Astro para generación de sitios estáticos optimizada
- 🎨 **Diseño Moderno** - Tailwind CSS con animaciones personalizadas y efectos de gradiente
- 🌈 **Animaciones Arcoíris** - Efectos de borde animado en elementos interactivos
- ♿ **Accesible** - HTML semántico y etiquetas ARIA para mejor accesibilidad
- 📊 **Línea de Tiempo Laboral** - Experiencia profesional con descripciones multilingües
- 🔗 **Integración Social** - Enlaces a GitHub, LinkedIn, Email y Teléfono (SMS)

## 🏗️ Estructura del Proyecto

portfolio/
├── src/
│   ├── components/
│   │   ├── Header.astro      # Navegación con toggles de idioma/tema
│   │   ├── Footer.astro      # Pie de página con tech stack
│   ├── layouts/
│   │   └── Layout.astro      # Layout base con scripts globales
│   ├── pages/
│   │   ├── index.astro       # Página de inicio con perfil
│   │   ├── work.astro        # Línea de tiempo de experiencia laboral
│   │   ├── projects.astro    # Vitrina de proyectos
│   │   └── contact.astro     # Información de contacto
│   ├── assets/
│   │   ├── photo.jpeg        # Foto de perfil
│   │   ├── Astro_dark.svg    # Logo de Astro
│   │   ├── Astro_light.svg   # Logo de Astro (claro)
│   │   └── tailwindcss.svg   # Logo de Tailwind CSS
│   └── styles/
│       └── global.css        # Animaciones y utilidades personalizadas
├── public/
│   └── favicon.svg           # Favicon del sitio
├── astro.config.mjs          # Configuración de Astro
├── tailwind.config.mjs       # Configuración de Tailwind CSS
├── tsconfig.json             # Configuración de TypeScript
└── package.json              # Dependencias del proyecto

## 🎨 Personalización

### Actualizar Información Personal

Edita los siguientes archivos para personalizar tu portafolio:

- `src/pages/index.astro` - Perfil, sobre mí y tech stack
- `src/pages/work.astro` - Entradas de experiencia laboral
- `src/pages/contact.astro` - Información de contacto y enlaces sociales
- `src/components/Header.astro` - Estructura de navegación

### Modificar Colores

Edita `tailwind.config.mjs` para personalizar el esquema de colores. El portafolio utiliza:
- Fondo: white/gray-950
- Texto: gray-900/white (consciente del dark mode)
- Acentos: gradientes arcoíris en animaciones

### Actualizar Visualización de Tech Stack

El ticker de tecnologías en la página de inicio se puede editar en `src/pages/index.astro`. Modifica el array de tecnologías con las tuyas propias.