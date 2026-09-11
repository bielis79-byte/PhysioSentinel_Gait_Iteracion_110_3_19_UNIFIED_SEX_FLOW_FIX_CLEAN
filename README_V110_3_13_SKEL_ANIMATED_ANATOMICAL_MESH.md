# V110.3.13 · SKEL Animated Anatomical Mesh

Objetivo: hacer caminar la malla corporal real de SKEL sobre la secuencia temporal ya validada por V110.3.12, sin introducir un nuevo optimizador.

Pipeline:

`V104/V107 → SKEL24 fit Frame 1 → puerta por modalidad → q(t) 1..75 → SKEL.forward(q(t)) → skin_verts(t) → skin_f fija → malla anatómica animada`

Principios de seguridad geométrica:

1. No se modifica el retargeting anatómico congelado de V110.3.9/V110.3.12.
2. La identidad corporal usa las mismas betas que el fitting (neutras en esta rama).
3. Escala, axis_map, rotación y traslación son las de la secuencia temporal activa.
4. La topología de piel es constante durante todos los frames.
5. Una auditoría independiente detecta NaN/Inf, caras inválidas o explosiones geométricas.
6. La malla se genera automáticamente después de la propagación temporal cuando hay cobertura suficiente; puede regenerarse sin repetir el fitting.
