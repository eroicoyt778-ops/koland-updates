# KoLand OS · Universal OTA Updates (`Obsidian Liquid Glass`)

![Versión](https://img.shields.io/badge/KoLand_OS-v3.7.4-10b981?style=for-the-badge)
![Codename](https://img.shields.io/badge/Edici%C3%B3n-Obsidian_Overdrive-18181b?style=for-the-badge)
![Arquitectura](https://img.shields.io/badge/Universal-x86--64--v2-3b82f6?style=for-the-badge)
![Consumo](https://img.shields.io/badge/OTA_Reposo-0.0_MB_RAM-f59e0b?style=for-the-badge)

Servidor oficial de actualizaciones OTA firmadas (SHA-256) para el entorno de escritorio **EndHa Win + Koland Universal (`x86-64-v2` · AMD / Intel / NVIDIA)**.

---

## Última versión publicada

| Campo | Valor |
| --- | --- |
| **Versión actual** | `v3.7.4` (*Obsidian Overdrive*) |
| **Fecha de lanzamiento** | `2026-11-24` |
| **Canal** | `Stable · Universal x86_64` |
| **Tamaño del paquete** | `9.7MB` |
| **Firma SHA-256** | `c1a626571a2c12dd2f772932540370dc0e6ab2774e85e400f2e537847d8e6a21` |
| **Release en GitHub** | [`v3.7.4`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.7.4) |
| **Manifiesto OTA** | [`manifest.json`](https://github.com/eroicoyt778-ops/koland-updates/releases/download/v3.7.4/manifest.json) · [`main/manifest.json`](https://raw.githubusercontent.com/eroicoyt778-ops/koland-updates/main/manifest.json) |
| **Paquete Universal** | [`endha-koland-universal.tar.zst`](https://github.com/eroicoyt778-ops/koland-updates/releases/latest/download/endha-koland-universal.tar.zst) |

---

## Novedades destacadas

- Controlador Universal de Ventilador v2.0 + Perfiles Térmicos v5.0: soporte nativo en C para ThinkPad Classic y Edge E431 (/proc/acpi/ibm/fan + thinkpad_hwmon PWM + auto fan_control=1 en caliente), IdeaPad/Legion, ASUS EC y hwmon PWM universal; instalación automática de koland-fan-control.service en el Paquete Universal y OTA; selector clicable Auto/Medio/Máximo en el icono de ventilador y corrección del salto de perfil Turbo/Normal a Ahorro en CPUs sin ACPI platform_profile
- Fix definitivo de Batería Fijada sobre Pantalla Completa + Paquete Universal: mantiene Batería fija en capa Overlay (F11/juegos) con telemetría y Liquid Glass v11 en vivo incluso en laptops de 1 monitor, corrige el congelamiento en instalaciones universales migrando harich-wall.service a QSG_RENDER_LOOP=basic + sin mesa_glthread + new_render_scheduling=false + direct_scanout=0 dinámico mientras está fijado, añade desfijado/cierre en 1 clic dentro de juegos + botón ✕ + atajo SUPER+B y unifica prlimit/renice root en endha-repose
- Fix crítico del panel de Batería en juegos (PCs de 1 monitor): auto-desfijado/cierre limpio al entrar en Pantalla Completa, telemetría en vivo sin congelarse, botón cerrar directo en modo Fijado, commit inmediato de capa Wayland y soporte de desactivación manual de Gaming Overdrive
- Universal Gaming Overdrive v2.0: controlador HW v4 con game-off real (corrige GPU clavada en high) y presupuesto térmico PPT inteligente en APUs + soporte NVIDIA, partición física SMT-aware + 3D V-Cache + árbol Proton/Wine de 8 niveles, PipeWire RT libre de xruns, Escudo Direct Scanout 0 ms (Game DND), Wi-Fi 0-Jitter y detección automática en ventana
- Motor óptico Apple iOS 26 Liquid Glass v11 en tiempo real (120 Hz Ley de Snell 3D + espejo Schlick + doble textura + 0 FBOs QML) y Optimización Central v3.7 (-52% RAM a ~80 MB, demonios C nativos, galería GPU 0-FBO con caché vipsthumbnail, migración total a PanelWindow y 0% shaders en juegos Fullscreen)

---

## Motor OTA en tiempo real (`0.0 MB RAM` en reposo)

- **Detección en 2 etapas sin bucles pesados:** consulta un `HEAD /releases/latest` (`cache-control: no-cache`, ~200 bytes, ~18 ms de CPU en Bash puro, sin rate-limit) y solo descarga `manifest.json` si hay una versión más nueva.
- **Disparadores por eventos:** comprueba automáticamente al encender el PC (con reintento automático si el Wi-Fi conecta después), al reconectar red, al despertar de suspensión/reposo y cada 3–5 min (pausado automáticamente en Pantalla Completa).
- **Motor Óptico Apple iOS 26 Liquid Glass v11 (`120 Hz`):** refracción física 3D por Ley de Snell sobre textura en vivo `1:1`, reflexión especular de espejo de Schlick en el labio curvo, dispersión cromática y **0 FBOs extra** en Quickshell (`~80 MB RAM`).
- **Aviso nativo Liquid Glass v11:** tarjeta flotante persistente con botones **Actualizar ahora**, **Novedades** y **Más tarde**, más píldora indicadora en la barra inferior y punto de aviso en Menú EndHa / Ajustes.
- **Actualización segura:** verifica integridad **SHA-256** y preserva las configuraciones locales de hardware y monitores (`env.lua`, `animations.lua`, `decoration.lua`, `koland-vars.lua`, `koland.lua`, `koland-user.lua`, `koland-displays.lua`).

---

## Historial de versiones

<!-- HISTORY_START -->
| Versión | Fecha | Cambios principales |
| --- | --- | --- |
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

## Cómo actualizar

- **Desde el escritorio:** haz clic en **Actualizar ahora** en el aviso flotante o abre **Configuración → KoLand Update**.
- **Desde terminal:**
  ```bash
  ~/.config/koland/bar/endha-updater.sh install
  ```
