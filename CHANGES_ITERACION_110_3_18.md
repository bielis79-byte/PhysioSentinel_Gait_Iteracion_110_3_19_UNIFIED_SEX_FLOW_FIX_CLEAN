# PhysioSentinel Gait · V110.3.18

## Legacy NPZ Migration + Pose-Sequence Integrity

- Mantiene congelados SKEL24, Unified Coordinate Frame, Frame 1, sexo unificado, B2/cache, solver temporal V110.3.17 y generación `skin_verts`.
- El cargador directo de NPZ ya no reproduce automáticamente nada al seleccionar un archivo.
- Tras cargar un NPZ aparecen dos rutas explícitas:
  1. **Reproducir NPZ existente**: no recalcula nada.
  2. **Recalcular marcha con motor V110.3.18**: ignora poses/malla del NPZ y usa la secuencia V104/V107 actual de la sesión para ejecutar de nuevo Frame 1 → retargeting temporal → auditorías → malla.
- Los NPZ sin `poses[frame,46]`, sin sexo SKEL o de una versión antigua se etiquetan como **legado**.
- Se aclara que un NPZ antiguo por sí solo no contiene los landmarks V104/V107 necesarios para corregir una marcha congelada; el recálculo usa los 75 frames activos de la sesión.
- En recálculo, `Sexo` de la ficha sigue siendo la única fuente de verdad (`Mujer→female`, `Hombre→male`).
- Se limpian secuencia/malla previas al iniciar la migración para impedir que un resultado legado contamine el nuevo cálculo.
- El NPZ nuevo conserva `poses`, `skel_gender`, versión fuente y metadatos de migración.
