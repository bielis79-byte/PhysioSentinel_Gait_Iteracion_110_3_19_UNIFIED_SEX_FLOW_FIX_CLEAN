# V110.3.11 · Depth-Safe Anatomical Gate + Consistent Validation

Base congelada: V110.3.9 permanece identificada como primera versión SKEL anatómicamente válida; V110.3.10 se conserva como base de refinamiento periférico.

Cambios de V110.3.11:

- Una única puerta `frame1_gate` gobierna mensaje, botón de propagación y estado de validación. Se elimina la contradicción entre “NO superada” y “frame validado”.
- En frontal/posterior monocular (`depth_weight <= 0.25`) la validación es **Depth-Safe**: RMSE XY < 0.38 + límites articulares + sanity SKEL24 + Unified Coordinate Frame. La Z inferida se informa pero no provoca FAIL por sí sola.
- En biplanar/3D calibrado la puerta sigue siendo estricta: XY + Z + auditoría ósea.
- Se conserva `depth_weight` del frame V104/V107 al construir el DataFrame objetivo del frame semilla; antes podía perderse y convertir incorrectamente un caso monocular en validación 3D estricta.
- La propagación temporal calcula ahora RMSE XY y RMSE Z por frame y usa la misma lógica de validación coherente con la modalidad.
- La auditoría temporal exporta `depth_safe_validation`, modo, razones, RMSE XY y RMSE Z.
- No se modifica el mapa SKEL24, FK Ground Truth, Unified Coordinate Frame, IK, CMA-ES ni refinamiento periférico de V110.3.10.
- Se mantiene la caché estable de Backblaze B2.
