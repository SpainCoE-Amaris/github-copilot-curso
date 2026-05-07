# 🖥️ GitHub Copilot CLI - Trabajando desde la Terminal

**Duración estimada:** 30 minutos  
**Audiencia:** Desarrolladores principiantes  
**Fecha:** Mayo 2026

> **⚡ Nota Importante**: En esta clase usaremos **GitHub Copilot CLI** desde una terminal externa (PowerShell, CMD o Git Bash), no desde VS Code. Aprenderás a obtener ayuda de Copilot directamente en la línea de comandos.

---

## 📋 Tabla de Contenidos

1. [Introducción - ¿Qué es GitHub Copilot CLI?](#1-introducción---qué-es-github-copilot-cli)
2. [Instalación y Configuración](#2-instalación-y-configuración)
3. [Configuración del Proyecto agents-poc](#3-configuración-del-proyecto-agents-poc)
4. [Comandos Básicos de Copilot CLI](#4-comandos-básicos-de-copilot-cli)
5. [Ejercicio Práctico: Agregar Botón "Me Gusta"](#5-ejercicio-práctico-agregar-botón-me-gusta)
6. [Flujo de Trabajo: Terminal → Editor](#6-flujo-de-trabajo-terminal--editor)
7. [Comparativa: CLI vs IDE](#7-comparativa-cli-vs-ide)
8. [Mejores Prácticas y Tips](#8-mejores-prácticas-y-tips)
9. [Troubleshooting](#9-troubleshooting)
10. [Recursos Adicionales](#10-recursos-adicionales)

---

## 1. Introducción - ¿Qué es GitHub Copilot CLI?

**⏱️ ~3-5 minutos**

### ¿Qué es una CLI?

**CLI** significa **Command Line Interface** (Interfaz de Línea de Comandos). Es una forma de interactuar con tu computadora mediante **comandos de texto** en lugar de usar una interfaz gráfica con ventanas y botones.

**Ejemplos de CLI:**
- **PowerShell** (Windows)
- **CMD** (Windows)
- **Git Bash** (Windows/Mac/Linux)
- **Terminal** (Mac/Linux)

**¿Por qué usar una CLI?**
- ✅ **Más rápido**: Ejecutar comandos es más rápido que navegar por menús
- ✅ **Automatizable**: Puedes crear scripts para tareas repetitivas
- ✅ **Poderoso**: Acceso a funcionalidades avanzadas del sistema
- ✅ **Universal**: Funciona igual en diferentes computadoras

**Ejemplo de comando en CLI:**
```powershell
# En lugar de hacer click derecho → Nueva carpeta
mkdir mi-proyecto

# En lugar de abrir un archivo con doble click
code archivo.txt
```

### ¿Qué es GitHub Copilot CLI?

GitHub Copilot CLI es una **extensión de GitHub CLI** que te permite obtener sugerencias y explicaciones de comandos directamente desde tu terminal, sin necesidad de abrir un IDE.

Es como tener a Copilot **dentro de la terminal**, ayudándote a encontrar y entender comandos del sistema operativo, Git, npm, y más.

### Diferencias Clave

| Característica | GitHub Copilot (VS Code) | GitHub Copilot CLI |
|----------------|--------------------------|-------------------|
| **Entorno** | Dentro del editor VS Code | Cualquier terminal (PowerShell, CMD, Bash) |
| **Uso principal** | Escribir y entender código | Obtener comandos del sistema y explicaciones |
| **Integración** | Editor de código | Línea de comandos |
| **Ideal para** | Desarrollo de aplicaciones | DevOps, scripting, navegación de proyectos |

### ¿Cuándo usar CLI vs IDE?

**Usa Copilot CLI cuando:**
- ✅ Necesitas un comando del sistema operativo
- ✅ Estás trabajando directamente en la terminal
- ✅ Quieres explorar un proyecto desde la línea de comandos
- ✅ Necesitas explicar la salida de un comando

**Usa Copilot en VS Code cuando:**
- ✅ Estás escribiendo código en un archivo
- ✅ Necesitas autocompletado inteligente mientras escribes
- ✅ Quieres generar funciones o clases completas
- ✅ Necesitas refactorizar código existente

---

## 2. Instalación y Configuración

**⏱️ ~5 minutos**

> **📌 Importante**: Existen **dos formas** de usar Copilot CLI. Verifica cuál tienes instalada.

### Opción A: Copilot CLI Standalone (Instalación Directa)

#### Paso 1: Verificar si ya lo tienes instalado

```powershell
copilot --version
```

**Salida esperada:**
```
copilot version 1.0.0
```

#### Paso 2: Si no está instalado

**Instalación recomendada con npm:**

```powershell
npm install -g @githubnext/github-copilot-cli
```

> 💡 **Requisito**: Necesitas tener **Node.js y npm** instalados. Descárgalos desde https://nodejs.org/

**Alternativa**: También puedes descargar desde https://githubnext.com/projects/copilot-cli y seguir las instrucciones específicas de tu sistema operativo.

#### Paso 3: Autenticación

```powershell
copilot auth
```

Sigue las instrucciones para autenticarte con GitHub.

#### Comandos principales (Standalone):

```powershell
copilot suggest "tu pregunta"   # Sugiere comandos
copilot explain "comando"       # Explica comandos
```

---

### Opción B: Copilot CLI vía GitHub CLI (gh)

#### Paso 1: Verificar GitHub CLI

```powershell
gh --version
```

**Salida esperada:**
```
gh version 2.40.0 (2024-01-15)
```

**Si no lo tienes instalado:**

1. Ve a la página oficial: **https://cli.github.com/**
2. En la página verás opciones para instalar usando diferentes gestores de paquetes (Winget, Chocolatey, Scoop, etc.)
3. **Para esta clase recomendamos usar npm** (si ya tienes Node.js instalado):

```powershell
npm install -g gh
```

4. Verifica la instalación:
```powershell
gh --version
```

> 💡 **Nota**: También puedes descargar el instalador `.msi` directamente desde la página si no tienes npm.

#### Paso 2: Autenticación en GitHub

```powershell
gh auth login
```

#### Paso 3: Instalar la extensión de Copilot

```powershell
gh extension install github/gh-copilot
```

**Salida esperada:**
```
✓ Installed extension github/gh-copilot
```

#### Paso 4: Verificar la instalación

```powershell
gh copilot --version
```

#### Comandos principales (vía gh):

```powershell
gh copilot suggest "tu pregunta"   # Sugiere comandos
gh copilot explain "comando"       # Explica comandos
```

---

### ¿Cuál usar?

| Método | Comando | Ventajas |
|--------|---------|----------|
| **Standalone** | `copilot suggest` | Más corto, instalación simple vía npm |
| **vía gh** | `gh copilot suggest` | Integrado con GitHub CLI, actualizaciones automáticas |

> 💡 **Nota**: En el resto de este documento usaremos **ambos formatos**. Usa el que tengas instalado.
>
> - Si tienes standalone: `copilot suggest "..."` 
> - Si tienes vía gh: `gh copilot suggest "..."`

---

## 3. Configuración del Proyecto agents-poc

**⏱️ ~5-7 minutos**

### 3.1 Clonar el Repositorio

Vamos a trabajar con un proyecto real: un dashboard de gestión de backlog desarrollado en **Vue 3** (frontend) y **C# .NET** (backend).

```powershell
git clone https://github.com/SpainCoE-Amaris/agents-poc.git
cd agents-poc
```

**Estructura del proyecto:**
- `web/` - Frontend Vue 3 + TypeScript
- `src/` - Backend C# .NET con Clean Architecture

### 3.2 Explorar el Proyecto con Copilot CLI

#### Ejercicio 1: Entender la estructura del proyecto

Primero, lista el contenido del directorio:

```powershell
dir
# En Linux/Mac: ls -la
```

Ahora usa Copilot para entender qué tipo de proyecto es:

```powershell
# Opción A (Standalone):
copilot suggest "cómo identificar la estructura de un proyecto con frontend Vue y backend C#"

# Opción B (vía gh):
gh copilot suggest "cómo identificar la estructura de un proyecto con frontend Vue y backend C#"
```

**Salida esperada (ejemplo):**
```
Suggestion:

# Para identificar la estructura:
# 1. Buscar package.json (indica proyecto Node/Vue)
Get-ChildItem -Recurse -Filter "package.json"

# 2. Buscar archivos .csproj (indica proyecto C#)
Get-ChildItem -Recurse -Filter "*.csproj"

# 3. Ver la estructura de carpetas
tree /F

# Resultado esperado:
# - web/ (carpeta con frontend Vue 3)
# - src/ (carpeta con backend C# .NET)
```

#### Ejercicio 2: Inicializar el proyecto

Pregunta a Copilot cómo inicializar un proyecto Vue:

```powershell
# Con el comando que tengas instalado:
copilot suggest "cómo instalar dependencias e iniciar un proyecto Vue 3 con Vite"
# O: gh copilot suggest "cómo instalar dependencias e iniciar un proyecto Vue 3 con Vite"
```

**Salida esperada (ejemplo):**
```
Suggestion:

# Navegar a la carpeta del frontend
cd web

# Instalar dependencias
npm install

# Iniciar el servidor de desarrollo
npm run dev
```

Ejecuta los comandos sugeridos para iniciar el frontend (estará disponible en http://localhost:3000).

### 3.3 Preguntas Exploratorias

Usa Copilot para descubrir más sobre el proyecto:

**Pregunta 1: ¿De qué se trata este proyecto?**

```powershell
copilot suggest "cómo leer el archivo README de un proyecto para entender de qué se trata"
```

**Pregunta 2: ¿Qué tecnologías usa?**

```powershell
copilot explain "package.json contiene las dependencias de un proyecto. ¿Cómo puedo ver las principales tecnologías?"
```

**Pregunta 3: ¿Cómo se estructura un proyecto Vue 3?**

```powershell
copilot suggest "mostrar la estructura de carpetas de un proyecto Vue 3 con Vite"
```

> 💡 Si usas GitHub CLI, agrega `gh` antes: `gh copilot suggest "..."`

---

## 4. Comandos Básicos de Copilot CLI

**⏱️ ~8-10 minutos**

> 💡 **Recordatorio**: Usa `copilot` o `gh copilot` según tu instalación.

### 4.1 Comando: `suggest`

Este comando te sugiere comandos del sistema para realizar una tarea.

#### Ejemplo 1: Entender de qué se trata el proyecto

```powershell
copilot suggest "cómo leer y entender el README de un proyecto para saber de qué se trata"
# O: gh copilot suggest "cómo leer y entender el README de un proyecto para saber de qué se trata"
```

**Salida esperada:**
```
Suggestion:

# Leer el archivo README principal
Get-Content README.md

# O en Linux/Mac:
cat README.md

# Para ver el README con formato en la terminal:
npm install -g mdcat
mdcat README.md

# Buscar archivos README en subcarpetas:
Get-ChildItem -Recurse -Filter "README.md"
```

**Ahora prueba con explain:**
```powershell
copilot explain "Este es un proyecto de backlog management con Vue 3 y C#. ¿Qué tipo de aplicación es?"
```

#### Ejemplo 2: Ejecutar la aplicación completa (Frontend + Backend)

```powershell
copilot suggest "cómo ejecutar un frontend Vue y un backend C# simultáneamente en Windows"
```

**Salida esperada:**
```
Suggestion:

# Opción 1: Usando dos terminales
# Terminal 1 - Frontend:
cd web && npm run dev

# Terminal 2 - Backend:
cd src\AgentsPoc.Api && dotnet run

# Opción 2: En una sola terminal con Start-Process
Start-Process powershell -ArgumentList "-NoExit", "-Command", "cd web; npm run dev"
Start-Process powershell -ArgumentList "-NoExit", "-Command", "cd src\AgentsPoc.Api; dotnet run"

# Opción 3: Crear un script de inicio
# Guardar en start-app.ps1:
# Start-Process -NoNewWindow powershell -ArgumentList "cd web; npm run dev"
# Start-Process -NoNewWindow powershell -ArgumentList "cd src\AgentsPoc.Api; dotnet run"
```

**🎯 Ejercicio práctico:**
1. Ejecuta el comando sugerido para levantar ambas aplicaciones
2. Verifica que el frontend esté en http://localhost:3000
3. Verifica que el backend responda en http://localhost:5167/health

---

## 5. Ejercicio Práctico: Agregar Botón "Me Gusta"

**⏱️ ~10-12 minutos**

Ahora vamos a usar Copilot CLI para agregar una nueva funcionalidad al proyecto: un botón de "me gusta" en las tarjetas de backlog del dashboard (componente `KanbanCard`).

### Paso 0: Crear rama y planificar con Copilot

**Primero, crea una rama para tu trabajo:**

```powershell
copilot suggest "cómo crear una rama de git para agregar un botón de me gusta"
```

**Salida esperada:**
```
Suggestion:

# Crear y cambiar a una nueva rama
git checkout -b feature/like-button

# Verificar en qué rama estás:
git branch

# Ver el estado actual:
git status
```

**Ejecuta el comando:**
```powershell
git checkout -b feature/like-button
```

**Ahora, planifica la implementación usando Copilot:**

```powershell
copilot suggest "/*plan: agregar un botón de me gusta a un componente Vue 3. ¿Qué pasos debo seguir?"
```

**Salida esperada:**
```
Suggestion:

Plan para agregar botón de "me gusta" en Vue 3:

1. 🔍 Encontrar el componente objetivo (KanbanCard.vue)
   - Buscar archivos .vue que contengan "Card"
   
2. 📝 Añadir estado reactivo en <script setup>
   - Importar ref desde vue
   - Crear ref para isLiked (estado booleano)
   
3. ⚙️ Implementar lógica del botón
   - Crear función handleLike para alternar estado
   - Cambiar entre liked y no liked
   
4. 🎨 Agregar botón en <template>
   - Usar @click para manejar eventos
   - Usar :class para estilos condicionales
   - Mostrar emoji según estado (❤️ o 🤍)
   
5. 💄 Aplicar estilos en <style scoped>
   - Estilo base del botón
   - Estilo para estado "liked"
   - Transiciones suaves
   
6. ✅ Probar y verificar
   - Guardar cambios
   - HMR recarga automáticamente
   - Verificar funcionalidad en navegador
   
7. 📦 Guardar cambios en Git
   - git add [archivo]
   - git commit con mensaje descriptivo
   - git push (opcional)
```

> 💡 **Tip**: El prefijo `/*plan:` ayuda a Copilot a entender que quieres una planificación paso a paso.

### Paso 1: Encontrar el Componente de Tarjeta

**Objetivo**: Localizar el archivo que contiene el componente de tarjeta de tarea.

```powershell
copilot suggest "cómo buscar archivos que contengan 'Card' en un proyecto Vue"
```

**Salida esperada:**
```
Suggestion:

# Buscar archivos con 'Card' en el nombre (archivos .vue)
Get-ChildItem -Recurse -Filter "*Card*.vue"

# O buscar contenido dentro de archivos
Select-String -Path ".\web\src\**\*.vue" -Pattern "Card" -List

# En Linux/Mac:
find ./web -name "*Card*.vue"
```

Ejecuta el comando y anota la ruta del archivo encontrado.

**Ejemplo de resultado:**
```
.\web\src\features\backlog\components\KanbanCard.vue
```

### Paso 2: Entender el Componente Actual

Lee el contenido del archivo:

```powershell
# En PowerShell
Get-Content .\web\src\features\backlog\components\KanbanCard.vue

# En CMD
type .\web\src\features\backlog\components\KanbanCard.vue

# En Linux/Mac
cat ./web/src/features/backlog/components/KanbanCard.vue
```

Ahora usa Copilot para entender qué hace este componente:

```powershell
copilot explain "Tengo un componente Vue 3 KanbanCard que muestra información de tareas en un tablero. ¿Qué elementos típicamente tiene?"
```

**Salida esperada:**
```
A KanbanCard component in Vue 3 typically contains:

1. Props for data (title, description, status, priority, category)
2. Visual elements (card container, header, body, category badge)
3. Interactive elements (buttons, icons)
4. Event emitters (for edit, delete actions)
5. Styling (scoped CSS styles)

Common structure:
<template>
  <div class="kanban-card">
    <h3>{{ title }}</h3>
    <p>{{ description }}</p>
    <div class="card-meta">
      <span>Priority: {{ priority }}</span>
      <CategoryBadge :category="category" />
    </div>
  </div>
</template>
```

### Paso 3: Solicitar Implementación del Botón de Like

**Opción A: Pedir código específico**

```powershell
copilot suggest "cómo agregar un botón de me gusta en un componente Vue 3 usando Composition API"
```

**Salida esperada:**
```
Suggestion:

<script setup lang="ts">
import { ref } from 'vue'

const isLiked = ref(false)

function handleLike() {
  isLiked.value = !isLiked.value
}
</script>

<template>
  <div class="kanban-card">
    <!-- Contenido existente de la tarjeta -->
    
    <button 
      @click="handleLike"
      :class="{ liked: isLiked }"
      class="like-button"
    >
      {{ isLiked ? '❤️' : '🤍' }}
    </button>
  </div>
</template>

<style scoped>
.like-button {
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.2s;
}

.like-button.liked {
  background: #ff6b6b;
  color: white;
}
</style>
```

---

**Opción B: Usar modo agente con prompt completo**

> 🤖 **Nuevo**: Si tienes acceso a Copilot con modo agente, puedes dar un prompt completo para que implemente todo:

```powershell
copilot suggest "@workspace Implementa un botón de me gusta con las siguientes especificaciones:
- Archivo: web/src/features/backlog/components/KanbanCard.vue
- Usar Vue 3 Composition API con TypeScript
- Estado reactivo: isLiked (booleano)
- Al hacer click: alternar isLiked
- UI: emoji corazón (❤️ liked, 🤍 no liked)
- Estilos: botón redondeado, transición suave, fondo rojo cuando liked
- Ubicación: al final de la tarjeta, debajo de la descripción"
```

**Con este prompt, el agente:**
1. Encontrará el archivo automáticamente
2. Leerá el contenido actual
3. Generará el código completo integrado
4. Te mostrará los cambios sugeridos

> 📝 **Nota**: La funcionalidad de agente puede variar según tu versión de Copilot CLI.

### Paso 4: Implementar los Cambios

**Flujo de trabajo:**

1. **Copiar la sugerencia** de Copilot CLI desde la terminal
2. **Abrir el archivo** en tu editor favorito (VS Code, Notepad++, etc.)
   ```powershell
   code .\web\src\features\backlog\components\KanbanCard.vue
   ```
3. **Integrar el código** sugerido en el componente existente
4. **Guardar el archivo**

> 📝 **Nota para el instructor**: En este punto, se hará una **review en vivo** con los estudiantes para analizar:
> - ¿Dónde colocar las referencias reactivas (ref) en el `<script setup>`?
> - ¿Dónde agregar el botón en el `<template>`?
> - ¿Cómo integrarlo con el diseño existente en `<style scoped>`?

### Paso 5: Verificar los Cambios

Pregunta a Copilot cómo recargar la aplicación:

```powershell
copilot suggest "cómo recargar una aplicación Vue con Vite que ya está corriendo en modo desarrollo"
```

**Salida esperada:**
```
Suggestion:

# Vite con npm run dev tiene Hot Module Replacement (HMR) automático.
# Los cambios se reflejan instantáneamente sin recargar la página.
# Si no recarga, puedes:

# 1. Presionar Ctrl+C para detener el servidor y volver a iniciarlo:
npm run dev

# 2. O simplemente recargar el navegador:
# Presiona F5 o Ctrl+R en el navegador
# La app estará en http://localhost:3000
```

### Paso 6: Guardar los Cambios con Git

**Ahora que has implementado la funcionalidad, guárdala en Git:**

```powershell
copilot suggest "cómo hacer commit de mis cambios en git con un mensaje descriptivo siguiendo conventional commits"
```

**Salida esperada:**
```
Suggestion:

# 1. Ver los archivos modificados
git status

# 2. Agregar los archivos al staging
git add web/src/features/backlog/components/KanbanCard.vue

# 3. Hacer commit con mensaje descriptivo (Conventional Commits)
git commit -m "feat(backlog): agregar botón de me gusta con contador en KanbanCard

- Agregado estado reactivo para likes e isLiked
- Implementada función handleLike para alternar estado
- Añadido botón con estilos condicionales
- Usado emojis para indicar estado visualmente"

# 4. (Opcional) Ver el historial
git log --oneline -5

# 5. (Opcional) Subir cambios al repositorio remoto
git push origin feature/like-button
```

**Ejecuta los comandos paso a paso:**

```powershell
# Verificar cambios
git status

# Agregar archivo modificado
git add web/src/features/backlog/components/KanbanCard.vue

# Hacer commit
git commit -m "feat(backlog): agregar botón de me gusta en KanbanCard"

# Ver confirmación
git log --oneline -1
```

> 🎯 **Convenciones de commits**:
> - `feat`: Nueva funcionalidad
> - `fix`: Corrección de bug
> - `docs`: Cambios en documentación
> - `style`: Cambios de formato (no afectan código)
> - `refactor`: Refactorización de código
> - `test`: Añadir o modificar tests

---

## 6. Flujo de Trabajo: Terminal → Editor

**⏱️ ~2 minutos**

### Flujo Recomendado

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  1. Terminal (Copilot CLI - Planificación)                 │
│     ↓                                                       │
│     copilot suggest "/*plan: cómo hacer X"                  │
│     ↓                                                       │
│     [Obtener plan paso a paso]                              │
│                                                             │
│  2. Terminal (Copilot CLI - Sugerencias)                    │
│     ↓                                                       │
│     copilot suggest "cómo hacer X"                          │
│     ↓                                                       │
│     [Obtener sugerencia de código/comando]                  │
│                                                             │
│  3. Evaluar y Copiar                                        │
│     ↓                                                       │
│     Revisar la sugerencia                                   │
│     Copiar el código/comando útil                           │
│                                                             │
│  4. Editor (VS Code, etc.)                                  │
│     ↓                                                       │
│     Abrir archivo correspondiente                           │
│     Integrar el código                                      │
│     Adaptar según necesidad                                 │
│                                                             │
│  5. Terminal (Ejecutar)                                     │
│     ↓                                                       │
│     Probar la aplicación                                    │
│     Verificar que funciona                                  │
│                                                             │
│  6. Terminal (Git)                                          │
│     ↓                                                       │
│     git add, commit, push                                   │
│     (usar copilot para comandos git)                        │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Ejemplo Práctico

```powershell
# 1. Planificar con Copilot
copilot suggest "/*plan: agregar validación de email en Vue 3"

# 2. Obtener sugerencia específica
copilot suggest "agregar validación de email en Vue 3"

# 3. Copiar código sugerido

# 4. Abrir editor desde terminal
code .\src\components\LoginForm.vue

# 5. (Editar en el editor)

# 6. Volver a terminal para probar
npm run dev

# 7. Guardar cambios
git add .
git commit -m "feat: agregar validación de email"
```

---

## 7. Comparativa: CLI vs IDE

**⏱️ ~3 minutos**

### Tabla Comparativa Completa

| Tarea | Con Copilot CLI | Con Copilot en VS Code |
|-------|----------------|----------------------|
| **Buscar archivos** | `copilot suggest "buscar archivos .vue"` → Ejecutar comando sugerido | Usar búsqueda integrada (Ctrl+P) |
| **Entender código** | `copilot explain "[código]"` en terminal | Seleccionar código → Click derecho → "Copilot: Explain" |
| **Generar código** | `copilot suggest "código para X"` → Copiar → Pegar en editor | Escribir comentario → Copilot genera inline |
| **Comandos Git** | `copilot suggest "comando git para X"` | Usar extensión GitLens o terminal integrada |
| **Instalar dependencias** | `copilot suggest "instalar Vue 3"` | Terminal integrada + Copilot |
| **Refactorizar** | Obtener sugerencia → Aplicar manualmente | Seleccionar → "Copilot: Refactor" |

### Ventajas de Copilot CLI

✅ **Independiente del editor**: Funciona en cualquier terminal  
✅ **Ideal para scripting**: Genera comandos del sistema operativo  
✅ **DevOps friendly**: Perfecto para automatización  
✅ **Ligero**: No requiere abrir IDE completo  
✅ **Exploratorio**: Excelente para entender proyectos nuevos

### Ventajas de Copilot en VS Code

✅ **Integración directa**: Sugerencias mientras escribes  
✅ **Contexto completo**: Conoce todo tu archivo  
✅ **Autocompletado**: Completa código automáticamente  
✅ **Refactoring**: Herramientas visuales integradas  
✅ **Debugging**: Combinado con depurador de VS Code

### Mejor Práctica: Combinar Ambos

**Flujo híbrido recomendado:**

1. **Exploración inicial** → Copilot CLI
   ```powershell
   copilot suggest "estructura típica de proyecto Vue 3 con Vite"
   ```

2. **Setup del proyecto** → Copilot CLI
   ```powershell
   copilot suggest "instalar dependencias npm"
   ```

3. **Desarrollo activo** → Copilot en VS Code
   - Escribir código con autocompletado
   - Generar funciones completas

4. **Scripts y automatización** → Copilot CLI
   ```powershell
   copilot suggest "script para hacer build y deploy"
   ```

5. **Git y control de versiones** → Copilot CLI
   ```powershell
   copilot suggest "comandos git para feature branch"
   ```

---

## 8. Mejores Prácticas y Tips

**⏱️ ~2-3 minutos**

### 📝 Tips para Mejores Prompts

#### ✅ Sé Específico

**❌ Malo:**
```powershell
copilot suggest "react"
```

**✅ Bueno:**
```powershell
copilot suggest "crear un componente Vue 3 con Composition API para manejar un formulario de login"
```

#### ✅ Incluye Contexto

**❌ Malo:**
```powershell
copilot suggest "ejecutar el proyecto"
```

**✅ Bueno:**
```powershell
copilot suggest "ejecutar un proyecto Vue 3 con Vite en modo desarrollo"
```

#### ✅ Especifica el Sistema Operativo

**❌ Malo:**
```powershell
copilot suggest "ver puertos abiertos"
```

**✅ Bueno:**
```powershell
copilot suggest "ver puertos abiertos en Windows usando PowerShell"
```

#### ✅ Usa prefijos para contexto específico

**💡 Tip avanzado**: Usa prefijos especiales para obtener resultados más específicos:

```powershell
# Para planificación paso a paso
copilot suggest "/*plan: agregar autenticación a mi app Vue 3"

# Para trabajar con el workspace actual
copilot suggest "@workspace: cómo está estructurado este proyecto"

# Para explicaciones detalladas
copilot explain "/*detailed: qué hace este componente y cómo mejorarlo"
```

### 🎯 Cuándo Usar Cada Comando

| Comando | Úsalo cuando... |
|---------|----------------|
| `copilot suggest` | Necesites saber **cómo hacer** algo (comandos, código) |
| `copilot explain` | Necesites saber **qué hace** algo (entender comandos/código) |

### 🚀 Atajos y Productividad

```powershell
# Crear alias en PowerShell para comandos frecuentes (si usas gh copilot)
Set-Alias gcs "gh copilot suggest"
Set-Alias gce "gh copilot explain"

# O para copilot standalone:
Set-Alias cs "copilot suggest"
Set-Alias ce "copilot explain"

# Ahora puedes usar:
cs "instalar React"
ce "npm install --save-dev"
```

### ⚠️ Limitaciones del CLI

- **No reemplaza el conocimiento**: Siempre revisa y entiende las sugerencias
- **Verifica antes de ejecutar**: Especialmente comandos que modifican archivos
- **Contexto limitado**: No ve todo tu proyecto como lo hace VS Code
- **No ejecuta automáticamente**: Tú decides qué comandos ejecutar

---

## 9. Troubleshooting

**⏱️ ~2 minutos**

### Problemas Comunes

<details>
<summary><strong>❌ Error: "gh: command not found" o "copilot: command not found"</strong></summary>

**Solución para gh:**
1. Ve a https://cli.github.com/
2. **Opción recomendada**: Instala con npm (si tienes Node.js):
   ```powershell
   npm install -g gh
   ```
3. **Alternativa**: Descarga el instalador `.msi` desde la página web y selecciona tu gestor de paquetes preferido (Winget, Chocolatey, etc.)
4. Reinicia tu terminal
5. Verifica: `gh --version`
6. Instala extensión: `gh extension install github/gh-copilot`

**Solución para copilot standalone:**
```powershell
npm install -g @githubnext/github-copilot-cli
```
> **Requisito**: Necesitas Node.js y npm instalados desde https://nodejs.org/

O descarga desde: https://githubnext.com/projects/copilot-cli
</details>

<details>
<summary><strong>❌ Tengo "copilot" pero no "gh copilot" (o viceversa)</strong></summary>

**Solución:**
Ambas opciones funcionan igual. Usa la que tengas instalada:
- Si tienes `copilot --version` ✅ → Usa `copilot suggest` y `copilot explain`
- Si tienes `gh copilot --version` ✅ → Usa `gh copilot suggest` y `gh copilot explain`

No necesitas ambas, solo una.
</details>

<details>
<summary><strong>❌ Error: "authentication required"</strong></summary>

**Solución:**
```powershell
gh auth login
```
Sigue las instrucciones para autenticarte con GitHub.
</details>

<details>
<summary><strong>❌ Copilot no responde o responde en inglés</strong></summary>

**Solución:**
- Las sugerencias pueden venir en inglés o español dependiendo del prompt
- Sé explícito en tu idioma preferido:
```powershell
copilot suggest "en español: cómo instalar React"
```
</details>

<details>
<summary><strong>❌ La sugerencia no es lo que esperaba</strong></summary>

**Solución:**
- Reformula tu pregunta con más contexto
- Sé más específico sobre tu sistema operativo y tecnología
- Usa `copilot --help` para ver opciones adicionales
</details>

### Comandos Útiles de Diagnóstico

```powershell
# Verificar instalación (prueba ambos)
copilot --version
gh copilot --version

# Si usas gh, ver extensiones instaladas:
gh extension list

# Actualizar Copilot CLI
# Para standalone:
npm update -g @githubnext/github-copilot-cli

# Para gh:
gh extension upgrade gh-copilot

# Ver ayuda
copilot --help
copilot suggest --help
copilot explain --help
```

---

## 10. Recursos Adicionales

**⏱️ ~1-2 minutos**

### 📚 Documentación Oficial

- **GitHub Copilot CLI**: https://docs.github.com/en/copilot/github-copilot-in-the-cli
- **GitHub CLI**: https://cli.github.com/manual/
- **GitHub Copilot**: https://github.com/features/copilot

### 🎓 Microsoft Learn

- [Introducción a GitHub Copilot](https://learn.microsoft.com/es-es/training/modules/introduction-to-github-copilot/)
- [GitHub Copilot Fundamentals](https://learn.microsoft.com/en-us/training/paths/copilot/)

### 🔧 Herramientas Relacionadas

- **Node.js y npm**: https://nodejs.org/ (requerido para instalación con npm)
- **Visual Studio Code**: https://code.visualstudio.com/
- **GitHub CLI**: https://cli.github.com/ (en la web puedes elegir tu gestor de paquetes preferido)
- **GitHub Desktop**: https://desktop.github.com/
- **Git**: https://git-scm.com/

### 📖 Comandos de Referencia Rápida

```powershell
# Instalación (Opción A - Standalone con npm)
npm install -g @githubnext/github-copilot-cli
copilot auth

# Instalación (Opción B - vía gh)
# Primero instalar gh CLI:
npm install -g gh
# O descargar desde https://cli.github.com/ y elegir tu gestor de paquetes
# Luego instalar extensión:
gh extension install github/gh-copilot

# Uso (usa el que tengas instalado)
copilot suggest "tu pregunta aquí"
copilot explain "comando o código a explicar"

# O con gh:
gh copilot suggest "tu pregunta aquí"
gh copilot explain "comando o código a explicar"

# Ayuda
copilot --help

# Actualizar
npm update -g @githubnext/github-copilot-cli  # standalone
gh extension upgrade gh-copilot                 # vía gh
```

### 🚀 Próximos Pasos

1. **Asegúrate de tener Node.js instalado**: Verifica con `node --version` y `npm --version` (necesario para instalaciones con npm)
2. **Practica el flujo completo**: Git branch → `/*plan:` → implementación → commit
3. **Explora el proyecto agents-poc**: Agrega más funcionalidades usando CLI
   - Prueba agregar un contador de likes (ejercicio bonus)
   - Implementa persistencia del estado en localStorage
   - Agrega animaciones a las tarjetas
4. **Combina CLI + IDE**: Alterna entre terminal y VS Code según la tarea
5. **Experimenta con prefijos**: Prueba `/*plan:`, `@workspace`, `/*detailed`
6. **Crea scripts**: Usa Copilot para automatizar tareas repetitivas
7. **Comparte conocimiento**: Enseña a tu equipo estos comandos

---

## 🎯 Ejercicios Bonus (Opcionales)

### Ejercicio 1: Agregar Estilos al Botón

**Paso 1 - Planificar:**
```powershell
copilot suggest "/*plan: mejorar estilos del botón de me gusta con animaciones y gradientes"
```

**Paso 2 - Implementar:**
```powershell
copilot suggest "cómo agregar estilos CSS scoped a un botón de me gusta en Vue 3 con estado activo/inactivo, gradientes y animación de pulso"
```

### Ejercicio 2: Persistir el Estado del Like

**Paso 1 - Planificar:**
```powershell
copilot suggest "/*plan: guardar el estado del me gusta en localStorage para que persista al recargar"
```

**Paso 2 - Implementar:**
```powershell
copilot suggest "cómo guardar el estado booleano de isLiked en localStorage en Vue 3 usando watchEffect y recuperarlo al montar el componente"
```

### Ejercicio 3: Animación al Dar Like

**Paso 1 - Planificar:**
```powershell
copilot suggest "/*plan: agregar animación de corazón cuando el usuario da like"
```

**Paso 2 - Implementar:**
```powershell
copilot suggest "cómo agregar una animación CSS de escala y rebote cuando se hace click en un botón en Vue 3"
```

---

## 💡 Ejercicio Challenge: Feature Completo

**Desafío final**: Usa solo Copilot CLI para implementar una feature completa desde cero.

**Feature**: Contador de "Me Gusta" en las tarjetas

```powershell
# 1. Planificar
copilot suggest "/*plan: agregar contador de me gusta a las tarjetas del backlog mostrando el número total de likes"

# 2. Crear rama
git checkout -b feature/comments-system

# 3. Encontrar archivos
copilot suggest "cómo encontrar el componente KanbanCard en el proyecto agents-poc"

# 4. Implementar (usar el plan del paso 1)
# ... seguir el plan paso a paso con copilot suggest

# 5. Commit
git commit -m "feat(backlog): agregar contador de me gusta a tarjetas"
```

---

## 📝 Resumen de la Clase

En esta clase aprendiste:

✅ Qué es GitHub Copilot CLI y cómo se diferencia de Copilot en VS Code  
✅ Cómo instalar y configurar `copilot` o `gh copilot`  
✅ Los dos comandos principales: `suggest` y `explain`  
✅ Cómo explorar un proyecto real (agents-poc) desde la terminal  
✅ Usar Copilot para entender proyectos y ejecutar aplicaciones  
✅ Planificar implementaciones con `/*plan:`  
✅ El flujo de trabajo: Terminal → Editor → Terminal  
✅ Cuándo usar CLI vs IDE  
✅ Mejores prácticas: prompts específicos, prefijos especiales  
✅ Workflow completo: rama Git → planificación → implementación → commit  

---

## 💬 Feedback

¿Encontraste útil esta clase? ¿Tienes sugerencias de mejora?  
Comparte tu feedback en: [Issues del repositorio]

---

**Creado con ❤️ usando GitHub Copilot**  
**Última actualización:** Mayo 2026
