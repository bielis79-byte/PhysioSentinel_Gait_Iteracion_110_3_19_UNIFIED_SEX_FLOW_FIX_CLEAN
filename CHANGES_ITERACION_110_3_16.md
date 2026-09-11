# PhysioSentinel Gait · V110.3.16

## Hard-Wired Lower-Limb Temporal Update + Temporal Motion Gate

- V110.3.9 permanece congelada como primera versión SKEL anatómicamente válida.
- No modifica SKEL24, Unified Coordinate Frame, Frame 1, sexo unificado, B2/cache ni la construcción de skin_verts.
- Sustituye el rescate temporal de piernas V110.3.15 por un solver Gauss-Newton amortiguado en XY para q3-q7 y q10-q14.
- La pose resultante se escribe directamente en la misma pose temporal que se persiste y alimenta la malla.
- Añade comparación entre movimiento objetivo V104/V107 y movimiento SKEL de RKnee/RAnkle/LKnee/LAnkle.
- Si el target se mueve y una pierna queda congelada, TEMPORAL MOTION GATE = FAIL y no se genera una falsa malla de marcha.
