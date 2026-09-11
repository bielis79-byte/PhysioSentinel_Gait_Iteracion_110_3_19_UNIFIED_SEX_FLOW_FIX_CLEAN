# V110.3.13 · SKEL Animated Anatomical Mesh

- V110.3.9 permanece congelada como primera versión SKEL anatómicamente válida.
- V110.3.12 permanece congelada como puerta explícita por modalidad de adquisición.
- El botón principal ejecuta en un único flujo la propagación temporal SKEL y, si se resuelve al menos el 90% de la secuencia, genera automáticamente `skin_verts(t)` para todos los frames válidos.
- La malla no se vuelve a optimizar: cada frame usa exclusivamente la pose `q(t)`, escala, axis_map y transformación global ya validadas.
- Topología fija `skin_f`, betas constantes y 6890 vértices por frame.
- Visor animado 3D con Play/Pausa, 0.5x/1x/2x, slider y cámara orbitable.
- Conectividad de joints del visor actualizada al orden oficial SKEL24.
- Nueva auditoría de integridad de malla: finitud, índices de caras, estabilidad de bounding box y saltos de vértices frame-a-frame.
- Exportación científica NPZ de vertices, faces, joints, frame_ids, escala, betas y axis_map.
- Backblaze B2 Cache estable se mantiene sin cambios.
