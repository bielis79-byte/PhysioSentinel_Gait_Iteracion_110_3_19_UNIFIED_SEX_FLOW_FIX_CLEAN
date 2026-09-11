# PhysioSentinel Gait V110.3.11

## Depth-Safe Anatomical Gate + Consistent Validation

V110.3.11 corrige exclusivamente la lógica de validación del Frame 1 y de la secuencia temporal. El retargeting anatómico SKEL24 validado en V110.3.9/V110.3.10 no se reabre.

### Monocular frontal/posterior

La profundidad Z es inferida. Por ello la puerta anatómica usa:

- RMSE XY < 0.38
- ausencia de violaciones duras de límites articulares
- SKEL24 sanity OK
- Unified Coordinate Frame OK

El RMSE Z y los errores angulares dependientes de profundidad se conservan como información de incertidumbre, pero no bloquean la propagación por sí solos.

### Biplanar o 3D calibrado

Se mantiene validación estricta sobre XY, Z y auditoría ósea.

### Coherencia de interfaz

Una sola variable `frame1_gate` controla el mensaje PASS/FAIL, el botón de 75 frames y la información inferior. No puede existir simultáneamente “puerta no superada” y “frame validado”.

### Backblaze

Se mantiene la caché runtime estable `/tmp/physiosentinel_skel_b2_cache_v1_1` y el fallback manual.
