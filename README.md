# � Dashboard de Usuarios - GoRest API

Un dashboard moderno para visualizar usuarios obtenidos desde la API de GoRest, desarrollado con **Vue 3**, **TypeScript**, **Tailwind CSS** y **Axios**.

## ✨ Características

- 🎨 **Diseño Responsive**: Grid adaptable con Tailwind CSS
- ⚡ **Vue 3**: Composition API con `<script setup>`
- 🔷 **TypeScript**: Tipado estático completo
- 🎯 **Tailwind CSS**: Utility-first CSS framework
- 📡 **Axios**: Cliente HTTP para consumir APIs
- 🖼️ **Imágenes Dinámicas**: Paisajes asignados a cada usuario
- 📱 **Grid Responsive**: 1-4 columnas según el dispositivo
- 🔄 **Estados de Carga**: Loading y manejo de errores

## 🏗️ Estructura del Proyecto

```
src/
├── components/
│   └── UserCard.vue      # Componente individual de usuario
├── App.vue               # Componente principal con grid
├── main.ts              # Punto de entrada
└── style.css            # Estilos Tailwind
```

## 🛠️ Tecnologías Utilizadas

- **Vue.js 3.5.21** - Framework con Composition API
- **TypeScript** - Lenguaje tipado
- **Tailwind CSS 4.1.13** - Framework de estilos
- **Axios 1.7.7** - Cliente HTTP
- **Vite 7.1.6** - Build tool y dev server

## 📡 API y Recursos

- **API**: [GoRest](https://gorest.co.in/public/v2/users)
- **Imágenes de Paisajes**:
  - Finlandia e Islandia (Mikko Lagerstedt)
  - Fotografía urbana de Barcelona
  - Paisaje con barco (Nikon)
  - Paisaje natural (Ecología Hoy)

## 🚀 Instalación y Uso

### Prerrequisitos
- Node.js (versión 18 o superior)
- npm o yarn

### Instalación
```bash
# Instalar dependencias
npm install

# Servidor de desarrollo
npm run dev

# Build para producción
npm run build
```

## 📱 Grid Responsive

El layout utiliza CSS Grid de Tailwind con diferentes columnas según el dispositivo:

```html
<!-- Configuración responsive -->
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
```

- **📱 Mobile** (< 768px): 1 columna
- **📟 Tablet** (768px - 1024px): 2 columnas  
- **💻 Desktop** (1024px - 1280px): 3 columnas
- **🖥️ Large** (> 1280px): 4 columnas

## 🎨 Componente UserCard

Cada tarjeta de usuario incluye:

- ✅ **Imagen de paisaje** asignada por ID
- ✅ **Badge de estado** (active/inactive)
- ✅ **Información del usuario** (nombre, email, género)
- ✅ **Iconos de género** (👨/👩)
- ✅ **Botón de acción**
- ✅ **Efectos hover** y transiciones

## 🔧 Funcionalidades Implementadas

### 📊 Dashboard Principal (App.vue)
```typescript
// Composición API con script setup
<script setup lang="ts">
import { ref, onMounted } from 'vue';
import axios from 'axios';

// Estado reactivo tipado
const users = ref<User[]>([]);
const loading = ref(false);

// Función async/await para obtener datos
const fetchUsers = async (): Promise<void> => {
  try {
    const response = await axios.get<User[]>('https://gorest.co.in/public/v2/users');
    users.value = response.data;
  } catch (error) {
    // Manejo de errores
  }
};
</script>
```

### 🃏 Tarjeta de Usuario (UserCard.vue)
```typescript
// Props tipadas con TypeScript
defineProps<{
  user: User;
}>();

// Función para asignar imagen por ID
const getImageForUser = (userId: number): string => {
  return landscapeImages[userId % landscapeImages.length];
};
```

## 🎯 Seguimiento de Especificaciones

### ✅ Vite + Vue 3 + Tailwind
- Configuración según [documentación oficial](https://tailwindcss.com/docs/guides/vite)
- Vue 3 con Composition API

### ✅ API GoRest
- Consumo de https://gorest.co.in/public/v2/users
- Tipado TypeScript para respuestas

### ✅ Imágenes de Paisajes
- 4 URLs de paisajes proporcionadas
- Asignación automática por ID de usuario

### ✅ Composition API
- `<script setup>` en todos los componentes
- Hooks reactivos (ref, onMounted)

### ✅ Axios
- Instalación y configuración
- Manejo de errores y estados de carga

### ✅ Componente UserCard
- Tarjeta individual y reutilizable
- Props tipadas con TypeScript

### ✅ Grid Responsive
- `grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4`
- Gap consistente con `gap-6`

## 🎨 Características Visuales

- **Sombras dinámicas**: `shadow-lg` → `shadow-xl` en hover
- **Transiciones suaves**: `transition-all duration-300`
- **Efectos de imagen**: Zoom en hover con `hover:scale-105`
- **Estados visuales**: Loading spinner y manejo de errores
- **Badges coloridos**: Verde para activo, rojo para inactivo

## 🚀 Deploy

```bash
# Build optimizado
npm run build

# Preview del build
npm run preview
```

Los archivos se generan en `/dist` listos para deploy.

## 📄 Licencia

Proyecto desarrollado siguiendo las especificaciones exactas proporcionadas.

---

Desarrollado con Vue 3 + TypeScript + Tailwind CSS 🚀

## ✨ Características

- 🎨 **Diseño Responsive**: Adaptable a todos los dispositivos
- ⚡ **Vue.js 3**: Framework progresivo con Composition API
- 🔷 **TypeScript**: Tipado estático para mayor robustez
- 🎯 **Tailwind CSS**: Utility-first CSS framework
- 📝 **ESLint + Prettier**: Linting y formateo automático
- 🧩 **Componentes Modulares**: Arquitectura escalable
- 🔄 **Async/Await**: Manejo moderno de promesas
- 📚 **JSDoc**: Documentación completa del código

## 🏗️ Estructura del Proyecto

```
src/
├── components/           # Componentes reutilizables
│   ├── AppHeader.vue    # Navegación principal
│   ├── HeroSection.vue  # Sección hero
│   ├── FeaturesSection.vue # Servicios/características
│   ├── ContactSection.vue  # Formulario de contacto
│   └── AppFooter.vue    # Pie de página
├── composables/         # Lógica reutilizable
│   └── useContactForm.ts # Hook para formulario
├── App.vue             # Componente principal
├── main.ts             # Punto de entrada
└── style.css           # Estilos globales Tailwind
```

## 🛠️ Tecnologías Utilizadas

- **Vue.js 3.5.21** - Framework principal
- **TypeScript** - Lenguaje de programación
- **Tailwind CSS 4.1.13** - Framework de estilos
- **Vite 7.1.6** - Build tool y dev server
- **ESLint 9.35.0** - Linter para calidad de código
- **Prettier 3.6.2** - Formateador de código

## 🚀 Instalación y Desarrollo

### Prerrequisitos
- Node.js (versión 18 o superior)
- npm o yarn

### Instalación
```bash
# Clonar el repositorio
git clone <repository-url>
cd vuetailwind

# Instalar dependencias
npm install
```

### Comandos Disponibles

```bash
# Servidor de desarrollo
npm run dev

# Build para producción
npm run build

# Preview del build
npm run preview

# Linting (con auto-fix)
npm run lint

# Formateo de código
npm run format
```

## 📋 Funcionalidades Implementadas

### 🔝 Header/Navegación
- Menú responsive con hamburger para móviles
- Navegación suave entre secciones
- CTA (Call to Action) prominente

### 🎯 Hero Section
- Diseño atractivo con gradientes
- Botones interactivos con estados de carga
- Estadísticas destacadas
- Animaciones CSS

### ⭐ Features Section
- Grid responsive de servicios
- Iconos y colores diferenciados
- Animaciones de aparición gradual
- CTA secundario

### 📧 Contact Section
- Formulario con validación completa
- Manejo de estados (carga, éxito, error)
- Información de contacto adicional
- UI/UX optimizada

### 📄 Footer
- Enlaces organizados por categorías
- Redes sociales
- Newsletter subscription
- Copyright y enlaces legales

## 🎨 Seguimiento del Manifiesto

### ✅ Formateo de Código
- **Prettier** configurado para estilo consistente
- Configuración en `.prettierrc.json`

### ✅ Linting y Validación
- **ESLint** con configuración ESLint 9
- Validación automática antes de commits
- Configuración en `eslint.config.js`

### ✅ Manejo de Promesas
- **Async/Await** en lugar de `.then()`
- Manejo adecuado de errores con try/catch

### ✅ Uso de TypeScript
- Interfaces y tipos claramente definidos
- Evita el uso de `any`
- Tipado estricto en toda la aplicación

### ✅ Estructura y Estilo
- **Componentes modulares** con una sola responsabilidad
- **Nombres descriptivos** y coherentes
- **PascalCase** para componentes
- **kebab-case** para archivos

### ✅ Documentación
- **JSDoc** para funciones complejas
- Comentarios claros y concisos
- README completo

## 🧪 Ejemplos de Uso

### Composable personalizado
```typescript
// En cualquier componente
import { useContactForm } from '@/composables/useContactForm';

const {
  formData,
  errors,
  isSubmitting,
  handleSubmit
} = useContactForm();
```

### Validación de formularios
```typescript
// Validación automática con tipado
interface ContactForm {
  name: string;
  email: string;
  company: string;
  message: string;
}
```

## 🔧 Configuraciones

### ESLint (eslint.config.js)
```javascript
// Configuración plana ESLint 9
export default [
  js.configs.recommended,
  ...pluginVue.configs['flat/essential'],
  // ... configuración personalizada
];
```

### Tailwind (tailwind.config.js)
```javascript
export default {
  content: ["./index.html", "./src/**/*.{vue,js,ts,jsx,tsx}"],
  theme: { extend: {} },
  plugins: [],
};
```

## 📱 Responsive Design

La aplicación está optimizada para todos los dispositivos:

- **📱 Mobile**: 320px - 768px
- **📟 Tablet**: 768px - 1024px  
- **💻 Desktop**: 1024px+

## 🚀 Deploy

```bash
# Build para producción
npm run build

# Los archivos estáticos se generan en /dist
```

## 🤝 Contribuciones

Este proyecto sigue las mejores prácticas establecidas en el manifiesto:

1. Usar **Prettier** para formateo
2. Pasar **ESLint** antes de commit
3. Preferir **async/await**
4. Usar **TypeScript** siempre que sea posible
5. Componentes **modulares** y **reutilizables**
6. **Documentar** el código apropiadamente

## 📄 Licencia

Este proyecto está bajo la Licencia MIT.

---

Desarrollado con ❤️ siguiendo el manifiesto de mejores prácticas para Vue.js
