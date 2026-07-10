# Calibrador VR-Simulación

Calibrador para pedaleras de sim racing (throttle, brake, clutch) sobre HID/Arduino. Permite ajustar mín/máx, deadzone, curva de respuesta e inversión de eje por pedal, con vista previa en vivo.

## Funcionalidades

- Detección automática del dispositivo/joystick conectado.
- Panel independiente por pedal (acelerador, freno, embrague), con auto-detección de cuántos ejes tiene el volante/pedalera.
- Captura de MIN/MAX con un click, directo desde el pedal físico.
- Deadzone configurable en el extremo inferior y superior de cada eje.
- 5 curvas de respuesta: Lineal, Exponencial, Logarítmica, S-Curve y Personalizada (con puntos de control arrastrables).
- Checkbox de **inversión de eje**, para pedaleras que reportan la medición al revés.
- Perfiles de calibración guardables/cargables en `.json`.

## Requisitos (para correr desde el código fuente)

- Python 3.11+
- Dependencias en `requirements.txt`:

```bash
pip install -r requirements.txt
python "Calibrador_VR-Simulacion.py"
```

## Descargar el ejecutable

La forma recomendada es la pestaña **[Releases](../../releases)**: ahí vas a encontrar siempre la última versión estable, ya compilada, lista para descargar y ejecutar (`VR-Calibrador.exe`).

Alternativamente, cada cambio en `main` también genera un build de verificación en **[Actions](../../actions)** → build más reciente con ✅ → sección **Artifacts** → `VR-Calibrador-windows` (útil para probar cambios antes de que salgan en una Release oficial).

### ⚠️ Sobre el aviso de Windows ("Smart App Control" / SmartScreen)

Este proyecto es gratuito y de código abierto — no tiene certificado de firma digital pagado, así que Windows puede mostrar un aviso de "aplicación no reconocida" al abrirlo por primera vez. Esto **no significa que el ejecutable sea inseguro**: significa que Microsoft no cobró por verificarlo. Todo el código está acá mismo, a la vista, para que lo audites si querés.

Si te aparece el bloqueo:
- **SmartScreen clásico**: click en "Más información" → "Ejecutar de todas formas".
- **Smart App Control** (Windows 11, más estricto): hay que desactivarlo desde *Configuración → Privacidad y seguridad → Seguridad de Windows → Control de aplicaciones y del explorador*. Ojo: en algunos casos esta desactivación no se puede revertir sin reinstalar Windows, así que hacelo solo si estás de acuerdo con el trade-off.

Estamos gestionando una firma digital gratuita para proyectos open source (vía SignPath) para eliminar este aviso a futuro.

## Compilar manualmente

El build "oficial" de este proyecto usa **PyInstaller** con el ícono de marca embebido. Desde la carpeta del repo, con Python en PATH:

```bash
pip install pyinstaller
pyinstaller --onefile --windowed --icon=logosolovr.ico --name=VR-Calibrador --collect-all customtkinter "Calibrador_VR-Simulacion.py"
```

El `.ico` (`logosolovr.ico`) ya está en la raíz del repo. El ejecutable resultante queda en la carpeta `dist/`, con el ícono de la marca aplicado tanto en el archivo como en la ventana en tiempo de ejecución.

> El workflow automático de GitHub Actions (`.github/workflows/build.yml`) usa exactamente este mismo comando, así que el `.exe` que bajás de la pestaña Actions es idéntico al que se distribuye a clientes (mismo ícono, mismo build).

## Licencia

MIT — ver [LICENSE](LICENSE).
