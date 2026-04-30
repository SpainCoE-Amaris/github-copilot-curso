# 🚀 Fundamentos de GitHub Copilot

**Duración estimada:** 30 minutos  
**Audiencia:** Desarrolladores  
**Fecha:** Abril 2026

---

## 📋 Tabla de Contenidos

1. [Introducción a GitHub Copilot](#1-introducción-a-github-copilot)
2. [IA en el Ciclo de Vida del Desarrollo (SDLC)](#2-ia-en-el-ciclo-de-vida-del-desarrollo-sdlc)
3. [Instalación y Configuración](#3-instalación-y-configuración)
4. [Funcionalidades con Ejemplos de Código](#4-funcionalidades-con-ejemplos-de-código)
5. [Comandos Principales](#5-comandos-principales)
6. [Licencias y Planes](#6-licencias-y-planes)
7. [Preguntas Frecuentes](#7-preguntas-frecuentes)
8. [Recursos Adicionales](#8-recursos-adicionales)

---

## 1. Introducción a GitHub Copilot

**⏱️ ~3 minutos**

### ¿Qué es GitHub Copilot?

GitHub Copilot es un **asistente de programación impulsado por IA** desarrollado por GitHub y OpenAI. Utiliza modelos de lenguaje avanzados para ayudar a los desarrolladores a escribir código más rápido y con mayor calidad.

### Características principales:

- 🔄 **Autocompletado inteligente**: Sugiere líneas o bloques completos de código
- 💬 **Chat integrado**: Permite hacer preguntas sobre código en lenguaje natural
- 📝 **Generación desde comentarios**: Transforma descripciones en código funcional
- 🔍 **Explicación de código**: Ayuda a entender código existente o heredado
- 🧪 **Generación de pruebas**: Crea tests unitarios automáticamente

> 📚 **Microsoft Learn**: [Introducción a GitHub Copilot](https://learn.microsoft.com/es-es/training/modules/introduction-to-github-copilot/)

---

## 2. IA en el Ciclo de Vida del Desarrollo (SDLC)

**⏱️ ~5 minutos**

GitHub Copilot no solo ayuda a escribir código, sino que mejora **todas las fases del ciclo de vida del desarrollo de software**.

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│    ┌──────────────┐     ┌──────────────┐     ┌──────────────┐  │
│    │   Análisis   │────▶│    Diseño    │────▶│   Pruebas    │  │
│    │  Requisitos  │     │  Desarrollo  │     │      QA      │  │
│    └──────────────┘     └──────────────┘     └──────────────┘  │
│           │                                         │          │
│           │                                         ▼          │
│           │              ┌──────────────┐     ┌──────────────┐ │
│           └─────────────▶│   Soporte    │◀────│Implementación│ │
│                          │Mantenimiento │     │    Deploy    │ │
│                          └──────────────┘     └──────────────┘ │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 2.1 Análisis de Requisitos

Copilot ayuda a traducir requisitos en estructuras de código:

| Capacidad | Descripción |
|-----------|-------------|
| **Creación rápida de prototipos** | Genera fragmentos de código basados en descripciones de alto nivel |
| **Implementación de casos de usuario** | Transforma casos de usuario en definiciones de clase o función |
| **Diseño de API** | Sugiere estructuras de API basadas en funcionalidad descrita |

### 2.2 Diseño y Desarrollo

Aquí es donde Copilot **realmente brilla**:

- ✅ **Generación de código reutilizable**: Crea estructuras repetitivas automáticamente
- ✅ **Implementación de patrones de diseño**: Sugiere patrones adecuados según el contexto
- ✅ **Optimización de código**: Ofrece alternativas más eficientes
- ✅ **Traducción entre lenguajes**: Ayuda a convertir código entre diferentes lenguajes

### 2.3 Pruebas y Control de Calidad

| Función | Beneficio |
|---------|-----------|
| Creación de pruebas unitarias | Genera casos de prueba basados en firmas de función |
| Generación de datos de prueba | Crea datasets realistas para testing |
| Identificación de casos límite | Sugiere escenarios de prueba para edge cases |
| Arquitectura de test suites | Diseña frameworks completos de pruebas |

### 2.4 Implementación (Deploy)

- 📄 Generación de archivos de configuración (YAML, JSON, etc.)
- 📜 Scripts de implementación para diferentes entornos
- 📖 Actualización de documentación de deployment

### 2.5 Soporte y Mantenimiento

- 🐛 **Corrección de errores**: Propone fixes basados en mensajes de error
- 🔧 **Refactorización**: Sugiere mejoras al código existente
- 📚 **Documentación**: Mantiene comentarios sincronizados con cambios
- 🏛️ **Código heredado**: Explica y moderniza código legacy

> 📚 **Microsoft Learn**: [IA en el Ciclo de Vida de Desarrollo del Software](https://learn.microsoft.com/es-es/training/modules/developer-use-cases-for-ai-with-github-copilot/4-ai-software-development-lifecycle)

---

## 3. Instalación y Configuración

**⏱️ ~3 minutos**

### Requisitos Previos

- ✅ Cuenta de GitHub
- ✅ Suscripción activa de GitHub Copilot
- ✅ Visual Studio Code (recomendado) u otro IDE compatible

### Instalación en VS Code

1. **Abrir VS Code**
2. **Ir a Extensiones** (`Ctrl+Shift+X`)
3. **Buscar** "GitHub Copilot"
4. **Instalar** la extensión oficial de GitHub
5. **Autenticarse** con tu cuenta de GitHub cuando se solicite

```
┌──────────────────────────────────────────┐
│  Extensions: Marketplace                 │
│  ┌────────────────────────────────────┐  │
│  │ 🔍 GitHub Copilot                  │  │
│  └────────────────────────────────────┘  │
│                                          │
│  ┌────────────────────────────────────┐  │
│  │ 🤖 GitHub Copilot                  │  │
│  │    ★★★★★ (10M+ downloads)          │  │
│  │    [Install]                       │  │
│  └────────────────────────────────────┘  │
│                                          │
│  ┌────────────────────────────────────┐  │
│  │ 💬 GitHub Copilot Chat             │  │
│  │    ★★★★★ (5M+ downloads)           │  │
│  │    [Install]                       │  │
│  └────────────────────────────────────┘  │
└──────────────────────────────────────────┘
```

### Verificar la Instalación

- Deberías ver el **ícono de Copilot** en la barra de estado inferior
- El ícono cambia según el estado:
  - 🟢 Activo y funcionando
  - 🟡 Procesando
  - 🔴 Error o deshabilitado

> 📚 **Microsoft Learn**: [Configurar GitHub Copilot en tu IDE](https://learn.microsoft.com/es-es/training/modules/introduction-to-github-copilot/3-exercise-configure-github-copilot)

---

## 4. Funcionalidades con Ejemplos de Código

**⏱️ ~10 minutos**

### 4.1 Autocompletado Inline (Ghost Text)

Copilot sugiere código en texto gris mientras escribes. Presiona `Tab` para aceptar.

**Ejemplo: Función para validar email**

```javascript
// Escribe esto y espera la sugerencia:
function validateEmail(email) {
    // Copilot sugerirá algo como:
    const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return regex.test(email);
}
```

#### 🎯 Ejercicio 1: Autocompletado

1. Crea un archivo `ejercicio1.js`
2. Escribe: `function calcularIVA(precio) {`
3. Presiona `Enter` y espera la sugerencia
4. Presiona `Tab` para aceptar o `Esc` para rechazar

---

### 4.2 Comentarios → Código

Escribe un comentario descriptivo y Copilot generará el código correspondiente.

**Ejemplo: Generar función desde comentario**

```python
# Función que recibe una lista de números y retorna 
# la suma de los números pares

def suma_pares(numeros):
    return sum(n for n in numeros if n % 2 == 0)
```

#### 🎯 Ejercicio 2: Comentario a Código

1. Crea un archivo `ejercicio2.py`
2. Escribe este comentario:
   ```python
   # Función que recibe un texto y cuenta cuántas vocales tiene
   ```
3. Presiona `Enter` y observa la sugerencia
4. Acepta con `Tab`

---

### 4.3 Chat Integrado

Usa el panel de chat para hacer preguntas sobre código, pedir explicaciones o generar código complejo.

**Acceso al Chat:**
- `Ctrl+Alt+I` - Abrir Chat de Copilot
- `Ctrl+I` - Chat inline (en el editor)

**Ejemplo de conversación:**

```
👤 Tú: Explica qué hace este código:

function debounce(func, wait) {
    let timeout;
    return function(...args) {
        clearTimeout(timeout);
        timeout = setTimeout(() => func.apply(this, args), wait);
    };
}

🤖 Copilot: Esta función implementa el patrón "debounce", que limita 
la frecuencia con la que se ejecuta una función. Es útil para eventos 
que se disparan muchas veces (como scroll o resize)...
```

#### 🎯 Ejercicio 3: Usar /explain

1. Selecciona cualquier bloque de código en tu proyecto
2. Presiona `Ctrl+I` para abrir chat inline
3. Escribe `/explain`
4. Lee la explicación generada por Copilot

---

## 5. Comandos Principales

**⏱️ ~5 minutos**

### Atajos de Teclado Esenciales

| Atajo | Acción |
|-------|--------|
| `Tab` | Aceptar sugerencia completa |
| `Esc` | Rechazar sugerencia |
| `Ctrl+Enter` | Ver sugerencias alternativas (panel) |
| `Alt+]` | Siguiente sugerencia |
| `Alt+[` | Sugerencia anterior |
| `Ctrl+Alt+I` | Abrir Chat de Copilot |
| `Ctrl+I` | Chat inline en el editor |

### Comandos Slash (Chat)

Usa estos comandos en el chat para acciones específicas:

| Comando | Descripción | Ejemplo de uso |
|---------|-------------|----------------|
| `/explain` | Explica el código seleccionado | Selecciona código → `/explain` |
| `/fix` | Sugiere correcciones para errores | Selecciona código con bug → `/fix` |
| `/tests` | Genera pruebas unitarias | Selecciona función → `/tests` |
| `/doc` | Genera documentación | Selecciona función → `/doc` |
| `/optimize` | Sugiere optimizaciones | Selecciona código → `/optimize` |
| `/new` | Crea nuevo archivo/proyecto | `/new crear API REST en Node.js` |

### Ejemplo Práctico de Comandos

```javascript
// Selecciona esta función y usa /tests en el chat:
function fibonacci(n) {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

// Copilot generará algo como:
describe('fibonacci', () => {
    test('returns 0 for n=0', () => {
        expect(fibonacci(0)).toBe(0);
    });
    test('returns 1 for n=1', () => {
        expect(fibonacci(1)).toBe(1);
    });
    test('returns 5 for n=5', () => {
        expect(fibonacci(5)).toBe(5);
    });
});
```

> 📚 **Microsoft Learn**: [Uso de GitHub Copilot con JavaScript](https://learn.microsoft.com/es-es/training/modules/introduction-to-github-copilot/4-exercise-generate-code-with-github-copilot)

---

### Uso de /plan para Estructurar Tareas

El comando `/plan` es especialmente potente cuando necesitas **planificar una tarea antes de implementarla**. En lugar de pedir código directamente, le pides a Copilot que te proponga un plan estructurado: pasos secuenciales, dependencias, archivos necesarios y validación final.

#### ¿Por qué usar `/plan`?

- ✅ **Evita código incompleto**: al revisar el plan, identificas huecos de alcance antes de gastar tiempo.
- ✅ **Aclara dependencias**: ves qué debe hacerse primero y en qué orden.
- ✅ **Ahorra retrabajos**: validando el plan, reduces cambios de dirección de último minuto.
- ✅ **Facilita la ejecución**: el plan se convierte en una checklist que puedes seguir paso a paso.

#### Ejemplo: Generar un Login React Mockeado

Aquí está el flujo completo. Copia este prompt en el chat de Copilot y úsalo con `/plan`:

```
/plan

Crear un login simple en React con usuario y contraseña. 
- Autenticación mockeada (credenciales fijas: usuario "demo", contraseña "demo123").
- Formulario con dos campos de entrada, botón de envío y mensajes de error/éxito.
- Manejo de estados: campos vacíos, autenticando, credenciales inválidas y login exitoso.
- Ubicación: carpeta "plan-ejemplo" dentro del proyecto.
- Sin backend real, sin base de datos, sin routing ni persistencia.
- Tiempo estimado: 2 minutos de desarrollo con Copilot.
```

#### Pasos para Ejecutar el Ejercicio

1. **Abre el Chat de Copilot**  
   Presiona `Ctrl+Alt+I` (o usa el ícono de chat en VS Code).

2. **Copia el Prompt**  
   Toma el prompt del ejemplo anterior y pégalo en el chat.

3. **Usa el Comando `/plan`**  
   Antes del prompt, incluye `/plan` para indicarle a Copilot que genere un plan, no código directo.

4. **Revisa el Plan Propuesto**  
   Copilot te mostrará un plan con: steps, dependencias, archivos relevantes, verification steps y decisions.

5. **Valida el Alcance**  
   Lee el plan y confirma que cubre lo que necesitas y excluye lo que no quieres. Si falta algo, iterá el prompt.

6. **Pide la Implementación**  
   Una vez validado el plan, di en el chat: `Implementa el plan propuesto` o `Genera el código basado en el plan anterior`. Copilot usará ese plan como referencia.

#### Cómo Escribir Buenos Prompts para `/plan`

Para que un plan sea útil, tu prompt debe incluir:

| Aspecto | Ejemplos |
|--------|----------|
| **Objetivo claro** | "Crear un login", "Construir un dashboard", "Escribir un script que procese CSV" |
| **Stack/Tecnología** | "React + JavaScript", "Python + Flask", "Node.js + Express" |
| **Alcance (qué incluir)** | "Autenticación, formulario, mensajes de error" |
| **Restricciones (qué excluir)** | "Sin backend real, sin persistencia, sin routing" |
| **Complejidad esperada** | "2 minutos", "1 hora", "pequeño" |
| **Ubicación o contexto** | "En una carpeta llamada 'plan-ejemplo'" |

**Ejemplo malo:**
```
Plan para un login
```

**Ejemplo bueno:**
```
/plan

Crear un login en React con usuario y contraseña.
Stack: React + JavaScript (sin TypeScript).
Incluir: formulario, validación, autenticación mockeada.
Excluir: backend, base de datos, routing, persistencia.
Carpeta: "plan-ejemplo".
Duración: 2 minutos.
```

#### Siguiente Paso

Una vez que Copilot proponga el plan y lo hayas validado, el flujo es:

> **"El plan me dice qué hacer paso a paso. Ahora pido la implementación: `Implementa este plan paso a paso`."**

De esa forma, el código que genere Copilot estará alineado con lo que acordaste en el plan, reduciendo sorpresas y ajustes innecesarios.

---

## 6. Licencias y Planes

**⏱️ ~2 minutos**

### Comparativa de Planes

| Característica | Individual | Business | Enterprise |
|----------------|:----------:|:--------:|:----------:|
| **Precio/mes** | $10 USD | $19 USD/usuario | $39 USD/usuario |
| Autocompletado de código | ✅ | ✅ | ✅ |
| Chat de Copilot | ✅ | ✅ | ✅ |
| CLI de Copilot | ✅ | ✅ | ✅ |
| Copilot en móvil | ✅ | ✅ | ✅ |
| Gestión de políticas | ❌ | ✅ | ✅ |
| Exclusión de archivos | ❌ | ✅ | ✅ |
| Logs de auditoría | ❌ | ✅ | ✅ |
| Base de conocimiento personalizada | ❌ | ❌ | ✅ |
| Copilot en pull requests | ❌ | ❌ | ✅ |
| Fine-tuning de modelos | ❌ | ❌ | ✅ |

### Consideraciones de Privacidad

- **Individual**: El código se puede usar para mejorar el modelo (opt-out disponible)
- **Business/Enterprise**: El código **NO** se usa para entrenar modelos
- Todos los planes cumplen con SOC 2 Type 2

> 📚 **Más información**: [Planes de GitHub Copilot](https://github.com/features/copilot)

---

## 7. Preguntas Frecuentes

**⏱️ ~2 minutos**

### ❓ ¿Copilot funciona sin conexión a internet?

**No.** GitHub Copilot requiere conexión a internet para comunicarse con los servidores de IA.

### ❓ ¿Qué lenguajes soporta?

Copilot soporta prácticamente **todos los lenguajes de programación**, con mejor rendimiento en:
- JavaScript/TypeScript
- Python
- Java
- C#
- Go
- Ruby
- PHP

### ❓ ¿El código generado es seguro?

Copilot puede sugerir código con vulnerabilidades. Siempre **revisa las sugerencias** antes de aceptarlas. La versión Business/Enterprise incluye filtros de seguridad adicionales.

### ❓ ¿Quién es dueño del código generado?

**Tú.** GitHub no reclama derechos sobre el código que generas con Copilot.

### ❓ ¿Copilot puede ver todo mi código?

Copilot envía **contexto limitado** (archivo actual y archivos abiertos relacionados) para generar sugerencias. No tiene acceso a todo tu repositorio simultáneamente.

---

## 8. Recursos Adicionales

### Microsoft Learn - Ruta de Aprendizaje Completa

| Módulo | Descripción | Link |
|--------|-------------|------|
| Introducción | Conceptos básicos de GitHub Copilot | [Ver módulo](https://learn.microsoft.com/es-es/training/modules/introduction-to-github-copilot/) |
| Casos de uso | Casos de uso para desarrolladores | [Ver módulo](https://learn.microsoft.com/es-es/training/modules/developer-use-cases-for-ai-with-github-copilot/) |
| SDLC con IA | IA en el ciclo de desarrollo | [Ver módulo](https://learn.microsoft.com/es-es/training/modules/developer-use-cases-for-ai-with-github-copilot/4-ai-software-development-lifecycle) |
| Ejercicios prácticos | Laboratorios hands-on | [Ver módulo](https://learn.microsoft.com/es-es/training/modules/introduction-to-github-copilot/4-exercise-generate-code-with-github-copilot) |

### Documentación Oficial

- 📖 [Documentación de GitHub Copilot](https://docs.github.com/es/copilot)
- 🎓 [GitHub Copilot Learning Path](https://learn.microsoft.com/es-es/training/paths/copilot/)
- 💡 [Mejores prácticas](https://docs.github.com/es/copilot/using-github-copilot/best-practices-for-using-github-copilot)

---

## ✅ Resumen de la Sesión

| Tema | Puntos Clave |
|------|--------------|
| **SDLC** | Copilot mejora las 5 fases del desarrollo |
| **Instalación** | Extensión en VS Code + autenticación GitHub |
| **Autocompletado** | `Tab` acepta, `Esc` rechaza, `Ctrl+Enter` alternativas |
| **Chat** | `/explain`, `/fix`, `/tests`, `/doc` |
| **Licencias** | Individual ($10), Business ($19), Enterprise ($39) |

---

**¿Preguntas?** 🙋‍♂️

---

*Material creado para capacitación interna - Abril 2026*
