# KoLand OS · Universal OTA Updates (`Obsidian Liquid Glass`)

![Versión](https://img.shields.io/badge/KoLand_OS-v3.6.0-10b981?style=for-the-badge)
![Codename](https://img.shields.io/badge/Edici%C3%B3n-Obsidian_Overdrive-18181b?style=for-the-badge)
![Arquitectura](https://img.shields.io/badge/Universal-x86--64--v2-3b82f6?style=for-the-badge)
![Consumo](https://img.shields.io/badge/OTA_Reposo-0.0_MB_RAM-f59e0b?style=for-the-badge)

Servidor oficial de actualizaciones OTA firmadas (SHA-256) para el entorno de escritorio **EndHa Win + Koland Universal (`x86-64-v2` · AMD / Intel / NVIDIA)**.

---

## Última versión publicada

| Campo | Valor |
| --- | --- |
| **Versión actual** | `v3.6.0` (*Obsidian Overdrive*) |
| **Fecha de lanzamiento** | `2026-11-23` |
| **Canal** | `Stable · Universal x86_64` |
| **Tamaño del paquete** | `9.1MB` |
| **Firma SHA-256** | `93f2a94bd7ff54b59dd831fd7a6ca6595a2e31b97f1334c262d5b839a4aa1523` |
| **Release en GitHub** | [`v3.6.0`](https://github.com/eroicoyt778-ops/koland-updates/releases/tag/v3.6.0) |
| **Manifiesto OTA** | [`manifest.json`](https://github.com/eroicoyt778-ops/koland-updates/releases/download/v3.6.0/manifest.json) · [`main/manifest.json`](https://raw.githubusercontent.com/eroicoyt778-ops/koland-updates/main/manifest.json) |
| **Paquete Universal** | [`endha-koland-universal.tar.zst`](https://github.com/eroicoyt778-ops/koland-updates/releases/latest/download/endha-koland-universal.tar.zst) |

---

## Novedades destacadas

- Nuevo apartado Color de iconos y barra en Personalizar (Pure Floating Liquid Glass): color global con paleta/Hex/rápidos, modo Multicolor, sincronizar Del cristal, personalización individual por icono (Wi-Fi, Bluetooth, Audio, Brillo, Batería, Notificaciones y Escritorios/Dock) y alcances opcionales para Texto/reloj, Logo EndHa y Paneles/Ajustes (0% CPU extra)
- Pantalla de bloqueo y SDDM 100% parcheados (modo Sólido Mate opaco de alto contraste, layout anti-colisión y sincronización atómica), botón para desactivar animaciones del escritorio en Personalizar, fix del rebote inicial en Wi-Fi/Bluetooth y shell sin polling (eventos D-Bus, SystemClock y toasts en GPU)
- Motor OTA en tiempo real (aviso flotante Liquid Glass + píldora en barra + HEAD ~200 B sin bucles), nuevo Centro de Ajustes modular Pure Floating Liquid Glass v10 y corrección de zonas táctiles en Menú EndHa y Batería
- Nuevo apartado Pantalla de Bloqueo en Apariencia: personalización completa de SDDM (fondo independiente o sincronizado, reloj 12h/24h, color Hex y subtítulo) + botón Bloquear SDDM Eco 0% consumo
- Detector real de reproducción de video y audio (PipeWire, ALSA PCM, MPRIS y Pantalla Completa) para evitar que Modo Reposo se active viendo videos

---

## Motor OTA en tiempo real (`0.0 MB RAM` en reposo)

- **Detección en 2 etapas sin bucles pesados:** consulta un `HEAD /releases/latest` (`cache-control: no-cache`, ~200 bytes, ~18 ms de CPU en Bash puro, sin rate-limit) y solo descarga `manifest.json` si hay una versión más nueva.
- **Disparadores por eventos:** comprueba automáticamente al encender el PC (con reintento automático si el Wi-Fi conecta después), al reconectar red, al despertar de suspensión/reposo y cada 3–5 min (pausado automáticamente en Pantalla Completa).
- **Aviso nativo Liquid Glass v10:** tarjeta flotante persistente con botones **Actualizar ahora**, **Novedades** y **Más tarde**, más píldora indicadora en la barra inferior y punto de aviso en Menú EndHa / Ajustes.
- **Actualización segura:** verifica integridad **SHA-256** y preserva las configuraciones locales de hardware y monitores (`env.lua`, `animations.lua`, `decoration.lua`, `koland-vars.lua`, `koland.lua`).

---

## Historial de versiones

<!-- HISTORY_START -->
| Versión | Fecha | Cambios principales |
| --- | --- | --- |
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
