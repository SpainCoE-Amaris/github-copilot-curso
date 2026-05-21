# AMARA

## Objetivos tecnicos de la sesion (30-40 min)

Al finalizar esta sesion podras:
- Comprender por que una empresa mantiene un repositorio interno de plugins.
- Configurar de forma basica un plugin del repositorio AMARA.
- Crear una API corta en .NET con ayuda de Copilot.

Repositorio de referencia:
https://github.com/SpainCoE-Amaris/AMARA

## Por que es importante un repositorio interno de plugins

En una empresa, no basta con que algo funcione: tambien debe ser seguro, trazable y gobernable.

### Beneficios principales

1. Seguridad
- Se evita instalar plugins no revisados desde fuentes externas.
- Los plugins pasan por validaciones internas antes de usarse.
- Se reduce el riesgo de fuga de datos o ejecucion de codigo malicioso.

2. Control y cumplimiento
- La empresa define que plugins estan permitidos.
- Se mantiene versionado y control de cambios.
- Ayuda a cumplir politicas internas y requisitos legales/auditoria.

3. Estandarizacion tecnica
- Todos los equipos usan herramientas validadas.
- Menos diferencias entre proyectos y menos errores por configuraciones distintas.
- Onboarding mas rapido para nuevos integrantes.

4. Productividad con calidad
- Se reutilizan soluciones internas ya probadas.
- Menos tiempo buscando herramientas, mas tiempo construyendo producto.

## Gobernanza recomendada del repositorio interno

1. Ownership claro por plugin
- Cada plugin debe tener un owner tecnico y un owner de seguridad.
- Definir SLA de mantenimiento: fixes, actualizaciones y respuesta a vulnerabilidades.

2. Politica de versionado
- Usar versionado semantico (MAJOR.MINOR.PATCH).
- Bloquear cambios breaking sin plan de migracion.
- Mantener changelog con impacto tecnico y de seguridad.

3. Control de aprobaciones
- Pull requests con al menos 2 aprobaciones (tecnica y seguridad).
- Validaciones obligatorias en CI: lint, tests, analisis de dependencias y escaneo de secretos.
- No permitir merge directo a rama principal.

4. Trazabilidad y auditoria
- Registrar quien publico, que cambio y en que version.
- Asociar cada cambio a ticket/incidente/requerimiento.
- Retener historico para auditorias internas y cumplimiento.

## Agenda

1. 0-10 min: Que es AMARA y por que existe dentro de la empresa.
2. 10-25 min: Configuracion rapida de un plugin.
4. 35-40 min: Implementacion guiada de una API corta en .NET.

## Copilot con agentes (enfoque operativo)

Un agente en Copilot permite ejecutar flujos mas completos: explorar codigo, proponer cambios y validar resultados con menos intervencion manual.

Prompt recomendado para desarrolladores:
"Actua como desarrollador senior. Explica en pasos cortos lo que haras, implementa cambios minimos y valida con build/test."


## Implementacion guiada: API .NET corta

### 1) Crear proyecto base

```bash
dotnet new webapi -n DemoApiCopilot
cd DemoApiCopilot
```

### 2) Pedir endpoints basicos a Copilot

Usa este prompt en el chat:
"Crea en Minimal API dos endpoints: GET /health y GET /saludo?nombre=Andres, devolviendo JSON y codigos HTTP correctos."

### 3) Ejecutar y validar

```bash
dotnet run
```

Validacion rapida:

```bash
curl http://localhost:5000/health
curl "http://localhost:5000/saludo?nombre=Andres"
```

## Buenas practicas de seguridad para desarrolladores

- Nunca subas secretos o tokens al repositorio.
- Usa solo plugins aprobados por la empresa.
- Revisa permisos solicitados por cada plugin.
- Mantente en versiones estables/recomendadas por el equipo interno.
- Si algo no esta documentado, pregunta antes de instalar.

## Resumen final

AMARA no solo mejora productividad. Tambien protege a la organizacion porque centraliza y controla que herramientas se usan, como se actualizan y bajo que politicas de seguridad. Aprender este flujo te prepara para trabajar en entornos corporativos reales.
