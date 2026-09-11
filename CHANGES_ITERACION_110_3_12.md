# PhysioSentinel Gait · V110.3.12

## Explicit Acquisition-Mode Gate

V110.3.12 corrige la falsa clasificación de registros monoculares frontal/posterior como `3D estricta`.

- La puerta anatómica ya **no infiere** la modalidad desde `depth_weight` ni desde la existencia de coordenadas XYZ.
- `Nivel 1` se transmite explícitamente a SKEL como `monocular_depth_safe`.
- `Nivel 2` se transmite como `biplanar_estimated`.
- `Nivel 3` solo se considera `3d_strict` cuando existe triangulación V56 válida; si no, usa `biplanar_estimated`.
- Monocular y biplanar estimado: RMSE XY + límites/coherencia bloquean; Z es informativa/no métrica y no provoca FAIL por sí sola.
- 3D calibrado: RMSE XY, RMSE Z y auditoría ósea son estrictos.
- La misma modalidad explícita gobierna Frame 1, frames 2→75, mensajes, botón de propagación y exportaciones.
- V110.3.9 permanece congelada como primera baseline SKEL anatómicamente válida.
- Se conserva el cache estable de Backblaze B2.
