# V110.3.16 · guía de validación

Objetivo: corregir específicamente la congelación temporal de miembros inferiores observada en los NPZ V110.3.14/15.

## Criterio de éxito
Tras procesar 75 frames deben aparecer rangos XY > 0.004 para RKnee, RAnkle, LKnee y LAnkle siempre que esos landmarks se muevan > 0.01 en V104/V107.

La aplicación compara el rango objetivo con el rango SKEL. Si detecta target móvil + SKEL congelado, detiene la generación de skin_verts y muestra FAIL.

El visor, SKEL24 y el retargeting del Frame 1 no se modifican.
