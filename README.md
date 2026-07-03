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

El `.exe` para Windows se compila automáticamente en cada cambio, vía GitHub Actions. Lo encontrás en la pestaña **[Actions](../../actions)** de este repo → entrá al build más reciente con ✅ → sección **Artifacts** → `VR-Calibrador-windows`.

### ⚠️ Sobre el aviso de Windows ("Smart App Control" / SmartScreen)

Este proyecto es gratuito y de código abierto — no tiene certificado de firma digital pagado, así que Windows puede mostrar un aviso de "aplicación no reconocida" al abrirlo por primera vez. Esto **no significa que el ejecutable sea inseguro**: significa que Microsoft no cobró por verificarlo. Todo el código está acá mismo, a la vista, para que lo audites si querés.

Si te aparece el bloqueo:
- **SmartScreen clásico**: click en "Más información" → "Ejecutar de todas formas".
- **Smart App Control** (Windows 11, más estricto): hay que desactivarlo desde *Configuración → Privacidad y seguridad → Seguridad de Windows → Control de aplicaciones y del explorador*. Ojo: en algunos casos esta desactivación no se puede revertir sin reinstalar Windows, así que hacelo solo si estás de acuerdo con el trade-off.

Estamos gestionando una firma digital gratuita para proyectos open source (vía SignPath) para eliminar este aviso a futuro.

## Compilar manualmente

Si preferís compilarlo vos mismo en lugar de bajar el artifact de Actions:

```bash
pip install pyinstaller
pyinstaller --onefile --windowed --name "VR-Calibrador" "Calibrador_VR-Simulacion.py"
```

El ejecutable queda en `dist/VR-Calibrador.exe`.

## Licencia

MIT — ver [LICENSE](LICENSE).
