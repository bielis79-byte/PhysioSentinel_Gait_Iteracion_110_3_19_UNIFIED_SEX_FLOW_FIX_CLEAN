# V110.3.18 · Legacy NPZ Migration

## Objetivo
Evitar el bloqueo de UX observado en V110.3.17: al cargar un NPZ antiguo se entraba directamente al reproductor y el usuario no podía volver al pipeline temporal corregido sin retirar manualmente el archivo.

## Flujo
Al seleccionar un `.NPZ`:

- **Reproducir NPZ existente**: visor directo del archivo, sin fitting.
- **Recalcular marcha con motor V110.3.18**: mantiene el archivo como referencia de trazabilidad, pero no reutiliza sus `vertices/joints` como fuente cinemática. El motor usa los frames V104/V107 ya cargados en la sesión y reconstruye una marcha nueva.

## NPZ legado
Se considera legado cuando falta alguno de estos elementos:
- `poses[frame,46]`,
- `skel_gender`,
- versión compatible del motor temporal actual.

Un NPZ legado puede reproducirse, pero no puede reconstruir por sí solo la cinemática objetivo que no contiene.

## Seguridad de estado
Al activar recálculo se eliminan de `session_state` la secuencia y malla SKEL previas de V110.3.18. El nuevo NPZ sólo se genera desde el resultado recalculado.
