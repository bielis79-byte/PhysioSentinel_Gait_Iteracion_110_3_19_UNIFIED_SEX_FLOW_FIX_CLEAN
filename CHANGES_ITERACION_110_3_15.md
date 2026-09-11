# PhysioSentinel Gait · V110.3.15

## Lower-Limb Temporal Retargeting + Pelvis-Centered Playback + Unified Sex + B2 Fix

V110.3.9 permanece congelada como primera versión SKEL anatómicamente válida. V110.3.15 no reabre SKEL24, Unified Coordinate Frame ni la correspondencia anatómica ya validada.

### 1. Retargeting temporal específico de miembros inferiores
- Se detectó en el NPZ V110.3.14 que pelvis, femur/tibia/talus/calcn/toes de ambos lados tenían rango temporal exactamente 0 mientras tronco y brazos sí variaban.
- Frames 2→75 mantienen la optimización temporal general y añaden una fase de rescate exclusiva de q de cadera/rodilla (q3–q6 y q10–q13).
- El prior hacia el frame anterior es deliberadamente suave en esta fase para no inmovilizar apoyo/oscilación.
- Commit/rollback monótono: la fase inferior sólo se acepta si mejora el error de landmarks de pierna.
- Nueva auditoría temporal: RKnee/RAnkle/LKnee/LAnkle deben mostrar rango temporal real. Si la cadena inferior queda congelada, la app lo marca como inválido.

### 2. Playback centrado en pelvis
- El visor resta la pelvis frame a frame únicamente en la copia visual de vertices/joints.
- El NPZ científico no se modifica.
- Rangos de cámara simétricos alrededor de 0 para evitar que el cuerpo aparezca descentrado.

### 3. Sexo único desde la ficha general
- Se elimina el selector SKEL independiente.
- Sexo=Mujer -> female -> skel_female.pkl.
- Sexo=Hombre -> male -> skel_male.pkl.
- Si no se ha seleccionado Mujer/Hombre, SKEL no elige silenciosamente un modelo por defecto.
- Los nuevos NPZ guardan `skel_gender`.

### 4. Direct SKEL March Loader
- Nuevo cargador de NPZ ya calculado.
- Salta directamente al reproductor sin repetir Frame 1, IK, propagación 75F ni skin_verts.
- Comprueba sexo cuando el NPZ ya contiene `skel_gender`.

### 5. Backblaze B2
- CACHE HIT sigue siendo prioritario.
- La ruta S3 usa ahora `GetObject` firmado directo en vez de `download_fileobj`/TransferManager.
- Se evita el `HeadObject` previo que estaba devolviendo 403 con la Application Key read-only del despliegue.
- Native API y carga manual continúan como fallback.
