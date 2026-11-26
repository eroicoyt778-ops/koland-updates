# KoLand OS · Universal OTA Updates (`Obsidian Native Rust`)

![Versión](https://img.shields.io/badge/KoLand_OS-v4.0.0-10b981?style=for-the-badge)
![Codename](https://img.shields.io/badge/Edici%C3%B3n-Obsidian_Native_Rust-18181b?style=for-the-badge)
![Arquitectura](https://img.shields.io/badge/Universal-x86--64-3b82f6?style=for-the-badge)
![Shell RAM](https://img.shields.io/badge/Shell_Rust-~20_MB_PSS-f59e0b?style=for-the-badge)

Servidor oficial de actualizaciones OTA firmadas (SHA-256) e instalador universal para **EndHa Win + KoLand OS (`x86-64` · AMD / Intel / NVIDIA · Laptops y Escritorio)**.

---

## Última versión publicada

| Campo | Valor |
| --- | --- |
| **Versión actual** | `v4.0.0` (*Obsidian Native Rust*) |
| **Fecha de lanzamiento** | `2026-11-26` |
| **Canal** | `Stable · Universal x86_64` |
| **Tamaño del paquete** | `13MB` |
| **Firma SHA-256** | `4c558c038ce358201e1428a629c24e1a6b863e1037fea78b7cc56f1e85863e71` |
| **Release en GitHub** | [`v4.0.0`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v4.0.0) |
| **Manifiesto OTA** | [`manifest.json`](https://github.com/eroicoyt778-ops/koland-updates/releases/download/v4.0.0/manifest.json) · [`main/manifest.json`](https://raw.githubusercontent.com/eroicoyt778-ops/koland-updates/main/manifest.json) |
| **Paquete Universal** | [`endha-koland-universal.tar.zst`](https://github.com/eroicoyt778-ops/koland-updates/releases/latest/download/endha-koland-universal.tar.zst) |

---

## Novedades destacadas

- KoLand 4.0 · Shell 100% Nativo en Rust (endha-shell ~20 MB PSS · 0% CPU · Quickshell retirado): nueva Barra de tareas adaptable (4 bordes: Abajo/Arriba/Izquierda/Derecha + modo Compacto en Ajustes → Personalizar), Polkit nativo sd-bus, Bloqueo ext-session-lock-v1 + PAM, Wallpaper multi-monitor sin SHM residente, SDDM Obsidian Wayland 0-RAM (weston kiosk adaptativo para AMD/Intel/NVIDIA), migración automática sin procesos duplicados y soporte universal x86-64
- Motor Core Nativo en Rust v1.0 (endha-core + endha-repose v6.0 · 858 KB · x86-64 universal): reescritura completa en Rust sin dependencias de Telemetría (3.5x), Audio/Modo Múltiple (8.1x · 0 python3), Detector Reposo (2.1x · 0 jq), Gaming Overdrive con syscalls Linux directas (13.2x), Pantalla/Nocturno/SDDM/Importador de Fondos, OTA con SHA-256 nativo (6.7x) y controlador root endha-repose v6.0 (<2 ms con flock/prlimit64 nativos)
- Controlador Universal de Ventilador v2.0 + Perfiles Térmicos v5.0: soporte nativo en C para ThinkPad Classic y Edge E431 (/proc/acpi/ibm/fan + thinkpad_hwmon PWM + auto fan_control=1 en caliente), IdeaPad/Legion, ASUS EC y hwmon PWM universal; instalación automática de koland-fan-control.service en el Paquete Universal y OTA; selector clicable Auto/Medio/Máximo en el icono de ventilador y corrección del salto de perfil Turbo/Normal a Ahorro en CPUs sin ACPI platform_profile
- Fix definitivo de Batería Fijada sobre Pantalla Completa + Paquete Universal: mantiene Batería fija en capa Overlay (F11/juegos) con telemetría y Liquid Glass v11 en vivo incluso en laptops de 1 monitor, corrige el congelamiento en instalaciones universales migrando harich-wall.service a QSG_RENDER_LOOP=basic + sin mesa_glthread + new_render_scheduling=false + direct_scanout=0 dinámico mientras está fijado, añade desfijado/cierre en 1 clic dentro de juegos + botón ✕ + atajo SUPER+B y unifica prlimit/renice root en endha-repose
- Fix crítico del panel de Batería en juegos (PCs de 1 monitor): auto-desfijado/cierre limpio al entrar en Pantalla Completa, telemetría en vivo sin congelarse, botón cerrar directo en modo Fijado, commit inmediato de capa Wayland y soporte de desactivación manual de Gaming Overdrive

---

## Arquitectura KoLand 4 (`~20 MB PSS` · `0.00% CPU` en reposo)

- **Shell 100% Nativo en Rust (`endha-shell` · Quickshell retirado):** barra de tareas multi-monitor, Dock con vista previa Wayland en vivo, Launcher, Notificaciones D-Bus, Ajustes completos de 5 pestañas, Polkit nativo (`sd-bus`), Pantalla de Bloqueo (`ext-session-lock-v1` + PAM), Wallpaper multi-monitor sin SHM residente y Modo Reposar, todo en un solo binario `x86-64` sin dependencias de Qt/QML.
- **Barra de tareas adaptable (4 bordes + modo compacto):** configura desde **Ajustes → Personalizar** tamaño **Compacto** o **Estándar** y posición **Abajo, Arriba, Izquierda o Derecha**; todos los paneles, menús, previews y toasts se adaptan automáticamente.
- **SDDM Obsidian Liquid Glass en Wayland 0-RAM (`weston --shell=kiosk`):** el gestor de inicio se cierra por completo al entrar al escritorio (**0 MB de Xorg/greeter en memoria**), con detección automática de teclado y validación segura para GPUs AMD, Intel y NVIDIA.
- **Migración automática sin duplicados:** retira y desactiva automáticamente servicios antiguos (`harich-wall.service`, `qs`, `polkit-gnome`, QML obsoletos), enmascara `at-spi-dbus-bus.service` y preserva tus configuraciones personales de monitores y hardware.

---

## Historial de versiones

<!-- HISTORY_START -->
| Versión | Fecha | Cambios principales |
| --- | --- | --- |
| [`v4.0.0`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v4.0.0) | `2026-11-26` | KoLand 4.0 · Shell 100% Nativo en Rust (endha-shell ~20 MB PSS · 0% CPU · Quickshell retirado): nueva Barra de tareas adaptable (4 bordes: Abajo/Arriba/Izquierda/Derecha + modo Compacto en Ajustes → Personalizar), Polkit nativo sd-bus, Bloqueo ext-session-lock-v1 + PAM, Wallpaper multi-monitor sin SHM residente, SDDM Obsidian Wayland 0-RAM (weston kiosk adaptativo para AMD/Intel/NVIDIA), migración automática sin procesos duplicados y soporte universal x86-64 |
| [`v3.8.0`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.8.0) | `2026-11-25` | Motor Core Nativo en Rust v1.0 (endha-core + endha-repose v6.0 · 858 KB · x86-64 universal): reescritura completa en Rust sin dependencias de Telemetría (3.5x), Audio/Modo Múltiple (8.1x · 0 python3), Detector Reposo (2.1x · 0 jq), Gaming Overdrive con syscalls Linux directas (13.2x), Pantalla/Nocturno/SDDM/Importador de Fondos, OTA con SHA-256 nativo (6.7x) y controlador root endha-repose v6.0 (<2 ms con flock/prlimit64 nativos) |
| [`v3.7.4`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.7.4) | `2026-11-24` | Controlador Universal de Ventilador v2.0 + Perfiles Térmicos v5.0: soporte nativo en C para ThinkPad Classic y Edge E431 (/proc/acpi/ibm/fan + thinkpad_hwmon PWM + auto fan_control=1 en caliente), IdeaPad/Legion, ASUS EC y hwmon PWM universal; instalación automática de koland-fan-control.service en el Paquete Universal y OTA; selector clicable Auto/Medio/Máximo en el icono de ventilador y corrección del salto de perfil Turbo/Normal a Ahorro en CPUs sin ACPI platform_profile |
| [`v3.7.3`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.7.3) | `2026-11-24` | Fix definitivo de Batería Fijada sobre Pantalla Completa + Paquete Universal: mantiene Batería fija en capa Overlay (F11/juegos) con telemetría y Liquid Glass v11 en vivo incluso en laptops de 1 monitor, corrige el congelamiento en instalaciones universales migrando harich-wall.service a QSG_RENDER_LOOP=basic + sin mesa_glthread + new_render_scheduling=false + direct_scanout=0 dinámico mientras está fijado, añade desfijado/cierre en 1 clic dentro de juegos + botón ✕ + atajo SUPER+B y unifica prlimit/renice root en endha-repose |
| [`v3.7.2`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.7.2) | `2026-11-24` | Fix crítico del panel de Batería en juegos (PCs de 1 monitor): auto-desfijado/cierre limpio al entrar en Pantalla Completa, telemetría en vivo sin congelarse, botón cerrar directo en modo Fijado, commit inmediato de capa Wayland y soporte de desactivación manual de Gaming Overdrive |
| [`v3.7.1`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.7.1) | `2026-11-24` | Universal Gaming Overdrive v2.0: controlador HW v4 con game-off real (corrige GPU clavada en high) y presupuesto térmico PPT inteligente en APUs + soporte NVIDIA, partición física SMT-aware + 3D V-Cache + árbol Proton/Wine de 8 niveles, PipeWire RT libre de xruns, Escudo Direct Scanout 0 ms (Game DND), Wi-Fi 0-Jitter y detección automática en ventana |
| [`v3.7.0`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.7.0) | `2026-11-24` | Motor óptico Apple iOS 26 Liquid Glass v11 en tiempo real (120 Hz Ley de Snell 3D + espejo Schlick + doble textura + 0 FBOs QML) y Optimización Central v3.7 (-52% RAM a ~80 MB, demonios C nativos, galería GPU 0-FBO con caché vipsthumbnail, migración total a PanelWindow y 0% shaders en juegos Fullscreen) |
| [`v3.6.3`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.6.3) | `2026-11-23` | Modo Reposar v3.1 Zero-Freeze (0 bucles · 100% eventos MPRIS/PipeWire/Hyprland) + Agente Polkit nativo Obsidian Liquid Glass (-57 MB RAM al reemplazar polkit-gnome): cronómetro hardware exacto sin desfasarse tras videos/juegos, despertar triple-redundante en todos los monitores, controlador HW v3.0 con busctl (<25 ms CPU unlock, ASPM seguro sin congelar NVMe/Wi-Fi/GPU) y aviso automático post-instalación para actualizar el controlador en Energía y Reposo → Actualizar v3 |
| [`v3.6.2`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.6.2) | `2026-11-23` | Panel de Sonido v2.0 (Pure Floating Liquid Glass): migración a PanelWindow con altura fija y máscara exacta (cero temblores/recortes al abrir desplegables), fix crítico de Modo Múltiple (ya no explota a 150% y restaura salida/puerto/volumen exactos al desactivar), sliders nativos PipeWire 0 ms sin rebote ni NaN%, auto-desmuteo al subir volumen, iconos Nerd Font alineados sin colisión en Boost 150%, sincronización de color personalizado y soporte IPC audio |
| [`v3.6.1`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.6.1) | `2026-11-23` | Modo Reposar v2.0: auto-rearmado instantáneo de IdleMonitor (soluciona que no se activara solo), cola secuencial atómica de hardware sin race conditions, restauración exacta de perfil y CPU Boost completo al despertar, detector multimedia real sin falsos positivos (video/audio/llamadas/inhibidores), soporte PrepareForSleep, brillo en reposo configurable (2-15%), DPMS opcional y diagnóstico en vivo en Energía y Reposo |
| [`v3.6.0`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.6.0) | `2026-11-23` | Nuevo apartado Color de iconos y barra en Personalizar (Pure Floating Liquid Glass): color global con paleta/Hex/rápidos, modo Multicolor, sincronizar Del cristal, personalización individual por icono (Wi-Fi, Bluetooth, Audio, Brillo, Batería, Notificaciones y Escritorios/Dock) y alcances opcionales para Texto/reloj, Logo EndHa y Paneles/Ajustes (0% CPU extra) |
| [`v3.5.1`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.5.1) | `2026-11-23` | Pantalla de bloqueo y SDDM 100% parcheados (modo Sólido Mate opaco de alto contraste, layout anti-colisión y sincronización atómica), botón para desactivar animaciones del escritorio en Personalizar, fix del rebote inicial en Wi-Fi/Bluetooth y shell sin polling (eventos D-Bus, SystemClock y toasts en GPU) |
| [`v3.5.0`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.5.0) | `2026-11-23` | Motor OTA en tiempo real (aviso flotante Liquid Glass + píldora en barra + HEAD ~200 B sin bucles), nuevo Centro de Ajustes modular Pure Floating Liquid Glass v10 y corrección de zonas táctiles en Menú EndHa y Batería |
| [`v3.4.0`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.4.0) | `2026-11-22` | Nuevo apartado Pantalla de Bloqueo en Apariencia: personalización completa de SDDM (fondo independiente o sincronizado, reloj 12h/24h, color Hex y subtítulo) + botón Bloquear SDDM Eco 0% consumo |
| [`v3.3.1`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.3.1) | `2026-11-22` | Detector real de reproducción de video y audio (PipeWire, ALSA PCM, MPRIS y Pantalla Completa) para evitar que Modo Reposo se active viendo videos |
| [`v3.3.0`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.3.0) | `2026-11-22` | Panel de Sonido con selector de Salida/Micrófono y Modo Múltiple, Pantalla estilo Apple Displays con desplegables, Color Hex (#75343f) + Bordes y 0% uso GPU en Modo Reposo |
| [`v3.2.0`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.2.0) | `2026-11-22` | Lanzamiento base Universal OTA (`Obsidian Overdrive`) con Motor Fullscreen Overdrive por monitor y centro KoLand Update |
<!-- HISTORY_END -->

---

## Cómo instalar o actualizar

- **Desde el escritorio (OTA):** haz clic en **Actualizar ahora** en el aviso flotante o abre **Configuración → KoLand Update**.
- **Desde terminal (OTA):**
  ```bash
  ~/.config/koland/bar/endha-core updater install
  ```
- **Instalación universal limpia (`endha-koland-universal.tar.zst`):**
  ```bash
  tar --zstd -xf endha-koland-universal.tar.zst && ./install.sh
  ```
