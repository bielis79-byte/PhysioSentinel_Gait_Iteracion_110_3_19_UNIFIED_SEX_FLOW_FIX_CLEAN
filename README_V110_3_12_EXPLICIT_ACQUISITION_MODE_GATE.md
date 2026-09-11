# V110.3.12 · Explicit Acquisition-Mode Gate

La modalidad de adquisición seleccionada en la interfaz es la fuente de verdad de la validación SKEL.

| Entrada | Modo SKEL | Papel de Z |
|---|---|---|
| Nivel 1 · frontal/posterior monocular | `monocular_depth_safe` | Inferida; informativa, no bloqueante |
| Nivel 2 · frontal + lateral sin triangulación métrica | `biplanar_estimated` | Estimada/no métrica; informativa, no bloqueante |
| Nivel 3 + triangulación V56 válida | `3d_strict` | Observada/calibrada; bloqueante |

Esto evita que un frontal monocular con buen RMSE XY sea rechazado únicamente por la incertidumbre de profundidad. El retargeting SKEL24 validado en V110.3.9/V110.3.10 no se modifica.
