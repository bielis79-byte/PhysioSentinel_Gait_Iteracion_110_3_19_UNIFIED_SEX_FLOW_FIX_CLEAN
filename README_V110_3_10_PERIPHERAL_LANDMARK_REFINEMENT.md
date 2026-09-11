# V110.3.10 · Peripheral Landmark Anatomical Refinement

V110.3.9 es la referencia congelada y no se reabre. V110.3.10 trabaja únicamente sobre residuos periféricos una vez que el mapa SKEL24 y la anatomía global ya son válidos.

Pipeline:

`V104/V107 → Official SKEL24 (congelado) → Unified Frame (congelado) → FK Ground Truth → q ownership oficial → Monotonic Hierarchical IK → CMA-ES residual → gradient refine → Peripheral Landmark Refinement con rollback → auditoría XY/Z/3D → puerta anatómica → 75 frames`

El refinamiento periférico no puede recolocar globalmente el cuerpo. Cada bloque sólo modifica su cadena y se revierte si empeora el error global o el núcleo corporal.

La tabla de errores por landmark permite separar dos fuentes residuales diferentes: error observable XY y profundidad Z inferida en monocular. Esto evita volver a modificar el retargeting global por un problema concentrado en tobillos, muñecas u otra correspondencia distal.
