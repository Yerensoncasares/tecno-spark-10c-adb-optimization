# ⚡ Guía de Optimización y Debloat ADB para Tecno Spark 10C (Unisoc T606)
**Un proyecto de Systemic Flow**

<div align="center">

🌐 **Languages / Idiomas:**

[🇺🇸 English](README.md) | [🇪🇸 Español](README_ES.md)

</div>

![Android](https://img.shields.io/badge/Android-12%2B-34A853?style=for-the-badge&logo=android&logoColor=white)
![ADB](https://img.shields.io/badge/ADB-Debloat%20%26%20Tuning-000000?style=for-the-badge&logo=android&logoColor=white)
![Chipset](https://img.shields.io/badge/Unisoc-T606-FF6600?style=for-the-badge)
![HiOS](https://img.shields.io/badge/HiOS-Optimized-6C5CE7?style=for-the-badge)
![Licencia](https://img.shields.io/badge/Licencia-MIT-green?style=for-the-badge)

Esta guía proporciona un método completo, **100% seguro y sin necesidad de Root**, para optimizar el rendimiento del **Tecno Spark 10C (Unisoc T606)** bajo la capa HiOS. Permite recuperar hasta **2.1 GB de RAM libre en reposo**, reducir la latencia táctil y eliminar la telemetría de fondo junto con el bloatware de fábrica.

---

## 📌 Aspectos Destacados
* **Mejora de Rendimiento:** Recuperación masiva de memoria RAM (~2.1 GB libres en reposo / ~1.5 GB bajo carga pesada).
* **Diseñado para el Chipset:** Ajustado específicamente para la arquitectura del procesador Unisoc T606.
* **Seguro y Estable:** Mantiene completamente funcionales Tecno ID, la sincronización en la nube y el asistente virtual Ella.

---

## 📁 1. Lista Maestra de Bloatware Eliminado

Los siguientes paquetes se desinstalan de forma segura a través de consola ADB:

### 🚫 Publicidad, Tiendas y Telemetría (Transsion / HiOS)
* `com.transsnet.store` (PalmStore - Tienda secundaria)
* `net.bat.store` (AHA Games - Catálogo de juegos)
* `com.talpa.hibrowser` (Navegador nativo de fábrica)
* `com.talpa.hiservice` (Servicios secundarios de marca)
* `com.transsion.statisticalsales` (Rastreador de ventas / Telemetría)
* `com.transsion.chromecustomization` (Personalizaciones de operador)

### 📦 Aplicaciones Basura y Diagnósticos del Sistema
* `com.transsion.tecnospot` (Foro comunitario Tecno Spot)
* `com.transsion.carlcare` (Soporte técnico Carlcare)
* `com.transsion.fmradio` (Radio FM analógica)
* `com.transsion.childmode` (Modo niños)
* `com.transsion.hiparty` (App de música en grupo Hi Party)
* `com.transsion.letswitch` (Herramienta de migración de datos)
* `com.idea.questionnaire` (Encuestas de opinión del sistema)
* `com.transsion.trancare` (Servicio de diagnóstico en segundo plano)
* `com.transsion.repaircard` (Tarjeta de garantía virtual)
* `com.transsion.beez` (Componente innecesario de HiOS)
* `com.transsion.tabe` (Componente innecesario de HiOS)
* `com.transsion.teop` (Componente innecesario de HiOS)

### 👥 Servicios Ocultos de Facebook (Rastreadores)
* `com.facebook.services` (Servicios de fondo de Facebook)
* `com.facebook.system` (Instalador oculto de Facebook)
* `com.facebook.appmanager` (Administrador de aplicaciones de Facebook)

### 🤖 Herramientas Secundarias de Google
* `com.google.android.apps.youtube.music` (YouTube Music)
* `com.google.android.projection.gearhead` (Android Auto)
* `com.google.android.apps.wellbeing` (Bienestar Digital)
* `com.google.android.feedback` (Envío constante de reportes de error)

---

## 🛠️ 2. Comandos ADB de Ejecución Directa

Ejecuta estos bloques secuencialmente en tu terminal con la Depuración USB activada en el teléfono:

### Paso A: Eliminación de Bloatware
```bash
adb shell pm uninstall -k --user 0 com.transsnet.store
adb shell pm uninstall -k --user 0 net.bat.store
adb shell pm uninstall -k --user 0 com.talpa.hibrowser
adb shell pm uninstall -k --user 0 com.talpa.hiservice
adb shell pm uninstall -k --user 0 com.transsion.statisticalsales
adb shell pm uninstall -k --user 0 com.transsion.chromecustomization
adb shell pm uninstall -k --user 0 com.transsion.tecnospot
adb shell pm uninstall -k --user 0 com.transsion.carlcare
adb shell pm uninstall -k --user 0 com.transsion.fmradio
adb shell pm uninstall -k --user 0 com.transsion.childmode
adb shell pm uninstall -k --user 0 com.transsion.hiparty
adb shell pm uninstall -k --user 0 com.transsion.letswitch
adb shell pm uninstall -k --user 0 com.idea.questionnaire
adb shell pm uninstall -k --user 0 com.transsion.trancare
adb shell pm uninstall -k --user 0 com.transsion.repaircard
adb shell pm uninstall -k --user 0 com.transsion.beez
adb shell pm uninstall -k --user 0 com.transsion.tabe
adb shell pm uninstall -k --user 0 com.transsion.teop
adb shell pm uninstall -k --user 0 com.facebook.services
adb shell pm uninstall -k --user 0 com.facebook.system
adb shell pm uninstall -k --user 0 com.facebook.appmanager
adb shell pm uninstall -k --user 0 com.google.android.apps.youtube.music
adb shell pm uninstall -k --user 0 com.google.android.projection.gearhead
adb shell pm uninstall -k --user 0 com.google.android.apps.wellbeing
adb shell pm uninstall -k --user 0 com.google.android.feedback
```

### Paso B: Ajustes de Rendimiento y Respuesta Táctil
```bash
adb shell settings put global hardware_accelerated_rendering true
adb shell settings put system touch_pump_rate 1
adb shell settings put secure long_press_timeout 200
adb shell settings put global app_standby_enabled 0
```

### Paso C: Optimización ART (Opciones Avanzadas de Compilación)

* **Recompilación total del sistema (Ideal para la primera configuración):**
```bash
  adb shell cmd package compile -m speed -a
```

* **Compilar un solo paquete específico (Para apps nuevas o individuales sin re-compilar todo):**
```bash
  adb shell cmd package compile -m speed <nombre_del_paquete>
```

* **Revertir/Descompilar el perfil de una aplicación específica:**
```bash
  adb shell cmd package compile --reset <nombre_del_paquete>
```

* **Revertir/Descompilar todos los paquetes del sistema:**
```bash
  adb shell cmd package compile --reset -a
```

---

## 🔒 3. Lista Blanca (Componentes Protegidos)

Para garantizar la estabilidad del sistema HiOS y prevenir reinicios en bucle (*bootloops*), **NO** desinstales los siguientes paquetes:

* `tech.palm.id` (Tecno ID / Sincronización de cuenta)
* `com.transsion.notebook` (Aplicación de Notas del sistema)
* `com.transsion.hilauncher` (Lanzador de interfaz de HiOS)
* `com.transsion.kolun.assistant` (Asistente de voz Ella)
* `com.google.android.apps.photos` (Google Fotos)

---

## 📜 Licencia
Publicado bajo la licencia **MIT** por **Systemic Flow**.
