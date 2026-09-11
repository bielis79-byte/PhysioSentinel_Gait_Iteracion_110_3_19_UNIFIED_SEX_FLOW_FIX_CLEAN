# PhysioSentinel Gait V110.3.17

## Pose-Sequence Integrity Fix

Esta versión se centra exclusivamente en garantizar que la pose inferior calculada para cada frame se conserve en la secuencia temporal que luego alimenta SKEL.forward() y la malla.

### Criterio de éxito
Antes de generar la malla, la app debe comprobar que:
- q de pierna derecha presentan rango temporal no nulo cuando el target inferior derecho se mueve;
- q de pierna izquierda presentan rango temporal no nulo cuando el target inferior izquierdo se mueve;
- tibia/talus SKEL reproducen movimiento temporal compatible con el target V104/V107.

Si cualquiera de estas condiciones falla, la malla no se genera y la ejecución se marca como FAIL temporal.

### Importante
En biplanar estimado el solver detecta qué eje XYZ contiene realmente el movimiento. V110.3.16 utilizaba sólo XY y podía congelar las piernas si la excursión sagital estaba codificada principalmente en Z.
