# V110.3.17 · Pose-Sequence Integrity Fix

## Objetivo
Corregir el fallo residual observado en V110.3.16: los 75 frames y la malla se generaban, pero q de miembros inferiores permanecían constantes y la marcha SKEL no movía las piernas.

## Cambios
- El solver temporal inferior deja de asumir que la marcha está contenida en XY.
- Se calcula un perfil temporal V104/V107 de RHip/RKnee/RAnkle/LHip/LKnee/LAnkle con rango XYZ por eje.
- En modo biplanar estimado, los ejes con movimiento real reciben mayor peso; Z ya no queda ignorada cuando contiene la excursión sagital.
- q3–q7 y q10–q14 se resuelven por DLS/Gauss-Newton ponderado XYZ y se escriben en la misma `pose` persistida en `frames[].pose`.
- `ankle_angle_r` (q7) y `ankle_angle_l` (q14) pasan a formar parte de las cadenas inferiores activas y reciben límites conservadores.
- Nueva auditoría `pose_sequence_integrity`: mide rango temporal de cada q inferior y falla si el objetivo se mueve pero una pierna queda constante.
- La `Temporal Motion Gate` usa movimiento ponderado XYZ, no sólo XY.
- El NPZ exporta opcionalmente `poses[frame,46]`, además de vértices/joints, para poder verificar la persistencia de q(t) sin repetir el fitting.
- La malla continúa bloqueada cuando falla la integridad temporal.

## Congelado
No se modifica SKEL24, Unified Coordinate Frame, Frame 1, sexo unificado, generación skin_verts, visor ni retargeting anatómico validado.
