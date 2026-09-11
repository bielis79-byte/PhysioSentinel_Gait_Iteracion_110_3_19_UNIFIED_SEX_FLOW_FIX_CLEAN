# PhysioSentinel Gait · V110.3.10

## Base congelada
V110.3.9 queda congelada como la primera versión SKEL anatómicamente válida. No se modifica el mapa oficial SKEL24, el Unified Coordinate Frame, el FK Ground Truth ni la caché privada Backblaze B2 que permitieron recuperar una anatomía coherente.

## Cambios de V110.3.10
- Corrige la propiedad q→cadena en el Hierarchical IK: los q lumbares/torácicos q17–q22 pertenecen a `tronco` aunque su desplazamiento FK se propague a ambos brazos.
- Mantiene el grafo empírico q→joints como auditoría, separado de la propiedad biomecánica oficial del q.
- Reordena el IK monótono para proteger el tronco y las extremidades antes del ajuste de cabeza.
- Añade `Peripheral Landmark Anatomical Refinement` con commit/rollback para rodilla+tobillo y codo+muñeca de cada lado.
- Una etapa periférica sólo se acepta si reduce el error XY local sin empeorar el RMSE XY global ni el núcleo pelvis/caderas/cuello/hombros/cabeza.
- Añade auditoría por landmark con error X, Y, Z firmado, RMSE XY, |Z| y error 3D, ordenada por peor landmark.
- Corrige la auditoría de vectores óseos para usar los nombres reales SKEL24 (`femur_r`, `tibia_r`, `talus_r`, `humerus_r`, `ulna_r`, `hand_r`, etc.).
- Aísla session_state y nombres de exportación a V110.3.10 para impedir contaminación por secuencias/mallas de iteraciones anteriores.
- Mantiene la caché runtime B2 estable `/tmp/physiosentinel_skel_b2_cache_v1_1`.
