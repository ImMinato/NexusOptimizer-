<div align="center">

# ⚡ NexusOptimizer

### Suite de diagnóstico, mantenimiento y optimización de rendimiento para Windows

[![Estado](https://img.shields.io/badge/estado-en%20desarrollo-yellow?style=for-the-badge)]()
[![Plataforma](https://img.shields.io/badge/plataforma-Windows%2010%2F11-0078D6?style=for-the-badge&logo=windows&logoColor=white)]()
[![Lenguaje](https://img.shields.io/badge/C%23-.NET%208-512BD4?style=for-the-badge&logo=csharp&logoColor=white)]()
[![Licencia](https://img.shields.io/badge/licencia-propietaria-red?style=for-the-badge)]()

🔗 **Sitio del proyecto:** 

</div>

<br>

> [!WARNING]
> **Software propietario — codigo privado.** El código fuente, la arquitectura y la lógica de optimización aquí documentada son de uso exclusivo del autor/equipo y **no** se distribuyen bajo licencia de código abierto. Ver sección [Licencia](#-licencia).

<br>

## 📑 Tabla de contenidos

- [¿Qué es NexusOptimizer?](#-qué-es-nexusoptimizer)
- [Por qué existe este proyecto](#-por-qué-existe-este-proyecto)
- [Principios de diseño](#-principios-de-diseño)
- [Funcionalidades principales](#-funcionalidades-principales)
- [Perfiles de optimización](#-perfiles-de-optimización)
- [Arquitectura](#-arquitectura)
- [Stack tecnológico](#-stack-tecnológico)
- [Métricas del proyecto](#-métricas-del-proyecto)
- [Validación y pruebas](#-validación-y-pruebas)
- [Capturas de pantalla](#-capturas-de-pantalla)
- [Preguntas frecuentes](#-preguntas-frecuentes)
- [Roadmap](#-roadmap)
- [Estado del proyecto](#-estado-del-proyecto)
- [Licencia](#-licencia)

<br>

## 🧭 ¿Qué es NexusOptimizer?

**NexusOptimizer** es una aplicación de escritorio para Windows que centraliza el diagnóstico, mantenimiento y optimización de rendimiento de un equipo en una sola herramienta, con interfaz gráfica, perfiles de uso predefinidos y mecanismos de seguridad para revertir cualquier cambio aplicado.

El sistema está organizado en **más de 25 módulos independientes**, agrupados en seis áreas funcionales:

<table>
<tr>
<td align="center">⚡<br><b>Hardware y energía</b></td>
<td align="center">💾<br><b>Disco y almacenamiento</b></td>
<td align="center">🌐<br><b>Red y privacidad</b></td>
</tr>
<tr>
<td align="center">🛠️<br><b>Sistema y mantenimiento</b></td>
<td align="center">📊<br><b>Diagnóstico y benchmarking</b></td>
<td align="center">🧩<br><b>Infraestructura de soporte</b></td>
</tr>
</table>

El proyecto es la evolución de una herramienta de línea de comandos previa, cuya lógica de optimización —ya validada empíricamente en uso real— fue migrada, ampliada y verificada por trazabilidad sobre una arquitectura de software completamente nueva.

<br>

## 💡 Por qué existe este proyecto

Windows, por su naturaleza de sistema operativo de propósito general, prioriza la compatibilidad y la facilidad de uso por sobre el rendimiento máximo en escenarios específicos (juegos, multimedia, uso intensivo de red). Las herramientas comerciales existentes suelen ser de código cerrado, requerir licencias pagas, o aplicar cambios que el usuario no comprende ni puede revertir con seguridad.

NexusOptimizer nace para resolver eso desde una idea simple: **el usuario debería poder optimizar su equipo sin perder el control sobre lo que está cambiando, y sin temor a romper algo que no pueda deshacer.**

<br>

## 🎯 Principios de diseño

| Principio | Qué significa en la práctica |
|---|---|
| 🔄 **Reversible** | Se generan puntos de restauración del sistema y copias de seguridad del registro antes de aplicar cualquier cambio significativo |
| 🔍 **Transparente** | Cada acción es comprensible para el usuario final; no hay cambios "ocultos" de cara a la interfaz |
| 🎮 **Orientado a perfiles de uso** | En lugar de exponer decenas de ajustes sueltos, se agrupan optimizaciones según un objetivo concreto |
| 🧱 **Sin dependencias externas en el núcleo** | Toda la interacción con Windows usa APIs estándar de .NET o utilidades nativas del sistema operativo |
| 🧩 **Modular** | Cada función (disco, red, energía, audio...) es una unidad de código independiente, testeable por separado |

<br>

## 🚀 Funcionalidades principales

<details open>
<summary><b>⚡ Energía y hardware</b></summary>
<br>

- Gestión de planes de energía de Windows, incluido el plan oculto **"Máximo rendimiento"** (Ultimate Performance)
- Monitoreo de temperatura de CPU/GPU con mecanismo de respaldo en cascada
- Control de aceleración del mouse para correspondencia 1:1 entre movimiento físico y en pantalla
- Tweaks de registro específicos según el fabricante de GPU detectado (NVIDIA / AMD / Intel)

</details>

<details>
<summary><b>💾 Disco y almacenamiento</b></summary>
<br>

- Limpieza de archivos temporales del usuario y del sistema
- Vaciado de caché de Windows Update y papelera de reciclaje
- Habilitación de TRIM para unidades SSD y lectura de salud de disco vía WMI
- Optimización del archivo de paginación según RAM instalada
- Exportación de históricos de benchmark a CSV (UTF-8 con BOM)

</details>

<details>
<summary><b>🌐 Red y privacidad</b></summary>
<br>

- Reducción de telemetría y deshabilitación de tareas programadas de diagnóstico
- Configuración de DNS con perfiles predefinidos (Cloudflare, Google, Quad9, OpenDNS)
- Bloqueo de dominios de publicidad y rastreo vía archivo hosts (lista propia + lista extendida de la comunidad)
- Test de velocidad de conexión integrado, sin depender de apps de terceros

</details>

<details>
<summary><b>🛠️ Sistema y mantenimiento</b></summary>
<br>

- Control de efectos visuales (animaciones, transparencia, sombras)
- Reducción de latencia de audio mediante el servicio MMCSS
- Optimizaciones de red heredadas (algoritmo de Nagle) para escenarios sensibles a latencia

</details>

<details>
<summary><b>📊 Diagnóstico y reportes</b></summary>
<br>

- Motor de benchmark con historial persistente (hasta 50 sesiones)
- **Health Score**: puntaje de salud del sistema sobre 8 factores reales, con consejos de mejora
- Generación de reportes legibles a partir de los resultados de benchmark

</details>

<details>
<summary><b>🧩 Infraestructura de soporte</b></summary>
<br>

- Logging estructurado con rotación automática y clasificación por severidad
- Configuración persistente en JSON, con carga diferida
- Notificaciones visuales no bloqueantes (tipo "toast")
- Verificación automática de actualizaciones disponibles

</details>

> 📌 El detalle de implementación (claves de registro exactas, comandos de sistema y algoritmos específicos) vive únicamente en el código fuente y no se documenta públicamente, por tratarse de propiedad intelectual del proyecto.

<br>

## 🎮 Perfiles de optimización

En lugar de pedirle al usuario que configure módulo por módulo, NexusOptimizer agrupa optimizaciones en **perfiles** orientados a un objetivo de uso real:

| Perfil | Pensado para | Combina |
|---|---|---|
| 🎮 **Gaming** | Máximo rendimiento en juegos | Plan Ultimate Performance, mouse sin aceleración, efectos visuales al mínimo, audio optimizado, telemetría deshabilitada, red optimizada, tweaks de GPU — **8 módulos en una sola acción** |
| 💼 **Work** | Estabilidad y privacidad | Plan equilibrado, valores de mouse/visuales por defecto, todos los tweaks de privacidad, DNS de buena reputación |
| ⚖️ **Balanced** | Uso cotidiano | Plan de alto rendimiento, mouse sin aceleración, transparencia desactivada, audio y red optimizados, privacidad básica |
| 🔋 **Power Save** | Minimizar consumo energético | Plan de ahorro, animaciones y apps en segundo plano desactivadas, hibernación deshabilitada |

<br>

## 🏗️ Arquitectura

NexusOptimizer sigue una **arquitectura en capas**, con responsabilidades claramente separadas y comunicación únicamente entre capas adyacentes:

```
┌──────────────────────────────────────────────────────────┐
│  🖥️  CAPA DE PRESENTACIÓN (WPF / XAML)                    │
│      Ventanas · navegación · interacción con el usuario   │
└───────────────────────────┬────────────────────────────────┘
                            │
┌───────────────────────────▼────────────────────────────────┐
│  🧠  CAPA DE LÓGICA                                         │
│      27+ módulos de optimización y diagnóstico              │
└───────────────────────────┬────────────────────────────────┘
                            │
┌───────────────────────────▼────────────────────────────────┐
│  🔧  SERVICIOS TRANSVERSALES                                 │
│      Logging · configuración · notificaciones · restauración│
└───────────────────────────┬────────────────────────────────┘
                            │
┌───────────────────────────▼────────────────────────────────┐
│  ⚙️  CAPA DE SISTEMA                                          │
│      Registro de Windows · WMI · Performance Counters · P/Invoke │
└──────────────────────────────────────────────────────────────┘
```

Esta separación permite que cada módulo se desarrolle, prueba y mantenga de forma independiente, sin acoplar la lógica de negocio a la interfaz ni al acceso directo al sistema operativo. Los módulos de la capa de lógica son clases estáticas sin estado compartido entre sí, lo que permite invocarlos desde cualquier parte de la interfaz sin gestionar ciclos de vida de objetos.

<br>

## 🧰 Stack tecnológico

<div align="center">

| Componente | Tecnología |
|---|---|
| **Lenguaje** | C# (.NET 8) |
| **Interfaz** | WPF, con XAML para vistas declarativas |
| **Acceso a sistema** | `Microsoft.Win32.Registry` · WMI (`System.Management`) · `PerformanceCounter` |
| **Interoperabilidad nativa** | P/Invoke sobre `user32.dll`, `kernel32.dll`, `Shell32.dll` |
| **Persistencia** | JSON vía `System.Text.Json` |
| **Bandeja del sistema** | `System.Windows.Forms.NotifyIcon` |
| **Red** | `System.Net.Http.HttpClient` |
| **Control de versiones** | Git |

</div>

> **Decisión de diseño deliberada:** sin librerías externas en el núcleo del sistema. Toda la lógica central depende únicamente del framework .NET y de utilidades incluidas en Windows, lo que reduce la superficie de dependencias y da control total sobre el comportamiento exacto de cada optimización.

<br>

## 📈 Métricas del proyecto

<div align="center">

| 📏 Métrica | 🔢 Valor |
|---|---|
| Líneas de código | **~11.000** |
| Archivos fuente | **~35** |
| Módulos de lógica de negocio | **27** |
| Ventanas / componentes de interfaz | **7** |
| Pestañas de funcionalidad | **16** |
| Perfiles de optimización | **4** |
| Consejos de mantenimiento documentados | **38**, en 7 categorías |
| Factores evaluados en el Health Score | **8** |
| Sesiones de historial conservadas | hasta **50** |
| Tareas de telemetría gestionables | **12** |
| Servidores DNS predefinidos | **4** + automático |

</div>

<br>

## ✅ Validación y pruebas

El sistema fue probado de forma exhaustiva sobre **hardware real** (no virtualizado), priorizando esto dado que buena parte de la lógica depende de sensores y controladores que no siempre son representativos en entornos virtuales.

Como parte del control de calidad, se realizó además una **verificación de trazabilidad**: se confirmó coincidencia exacta entre los valores aplicados por NexusOptimizer y los validados empíricamente en la versión anterior del proyecto, asegurando que la migración a la nueva arquitectura no alteró ningún comportamiento ya probado en producción.

```
✔ Detección automática de CPU y GPU
✔ Identificación de fabricante de GPU para tweaks específicos
✔ Cálculo de espacio libre en disco y detección de tipo de unidad
✔ Monitoreo en tiempo real de CPU y RAM
✔ Respaldo en cascada del módulo de temperatura
✔ Coincidencia exacta de parámetros críticos vs. versión anterior
```

<br>


</div>

<br>

## ❓ Preguntas frecuentes

<details>
<summary><b>¿Es de código abierto?</b></summary>
<br>
No. Es un proyecto propietario en etapa de desarrollo, con planes de comercialización futura. El codigo es privado.
</details>

<details>
<summary><b>¿Funciona en Windows 11?</b></summary>
<br>
El desarrollo y las pruebas se realizaron sobre Windows 10. La compatibilidad con Windows 11 está prevista pero pendiente de validación formal.
</details>

<details>
<summary><b>¿Los cambios que aplica se pueden revertir?</b></summary>
<br>
Sí. Antes de aplicar cambios significativos (como un perfil completo) se generan puntos de restauración del sistema y copias de seguridad del registro.
</details>

<details>
<summary><b>¿Cuándo estará disponible para descargar?</b></summary>
<br>
Todavía no hay fecha de lanzamiento público. El roadmap incluye empaquetarlo como instalador distribuible como paso previo a su evaluación por usuarios externos.
</details>

<br>

## 🗺️ Roadmap

- [ ] Suite de pruebas automatizadas (actualmente las pruebas son manuales)
- [ ] Ampliación del catálogo de tweaks específicos por modelo de GPU
- [ ] Empaquetado como instalador distribuible
- [ ] Validación formal en Windows 11
- [ ] Página de producto y distribución pública (en construcción — ver enlace al inicio de este documento)

<br>

## 🚧 Estado del proyecto

En desarrollo activo. Actualmente de uso interno / evaluación. El modelo de distribución y licenciamiento comercial se definirá en una etapa posterior.

<div align="center">

`Concepto` → `Script CLI` → `Reescritura como app de escritorio` → **`Estado actual`** → `Empaquetado` → `Lanzamiento`

</div>

<br>

## 🔒 Licencia

**Todos los derechos reservados.**

Este software es propiedad de su(s) autor(es) y se encuentra en una etapa previa a su comercialización. Queda prohibida su copia, modificación, distribución, ingeniería inversa o uso, total o parcial, sin autorización expresa y por escrito del titular.

Este se mantiene con fines de desarrollo y control de versiones. El acceso al código no implica la concesión de ninguna licencia de uso.

<br>

<div align="center">

<sub>© 2026 NexusOptimizer. Todos los derechos reservados.</sub>

</div>
