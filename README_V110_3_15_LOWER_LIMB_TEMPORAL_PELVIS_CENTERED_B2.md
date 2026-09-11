# V110.3.15 · guía de validación

## Prueba nueva desde vídeo
1. Seleccionar Sexo en Datos del paciente: Mujer u Hombre.
2. Confirmar que el panel indica `Modelo SKEL: female/male · determinado automáticamente`.
3. Confirmar CACHE HIT o B2 DOWNLOAD OK; carga manual sólo si ambos fallan.
4. Validar Frame 1.
5. Procesar 75 frames + malla.
6. Revisar la nueva auditoría de miembros inferiores: RKnee, RAnkle, LKnee y LAnkle no deben mostrar rango ~0.
7. Reproducir malla: debe estar centrada en pelvis y las piernas deben seguir la marcha.

## Prueba rápida sin recalcular
Usar `Abrir marcha SKEL ya calculada (.NPZ)` al principio del módulo. Un NPZ V110.3.13/14 puede reproducirse directamente. Los NPZ V110.3.15 añaden `skel_gender` para control de coherencia con la ficha.

## Invariantes congelados
No se modifican SKEL24, Unified Coordinate Frame ni la topología/skin_verts del modelo. El centrado de pelvis es sólo de visualización.
