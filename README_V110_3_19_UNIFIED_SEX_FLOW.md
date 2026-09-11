# V110.3.19 · Unified Sex Flow Fix

Corrección focal sobre V110.3.18.

- `Sexo` de **Datos del paciente / registro** es la única fuente de verdad.
- Mujer → `female` → `skel_female.pkl`.
- Hombre → `male` → `skel_male.pkl`.
- El valor visible se sincroniza con `patient_sex` antes de entrar al flujo SKEL.
- No existe selector SKEL independiente ni fallback silencioso a masculino.
- Se mantienen sin cambios el mapa SKEL24 validado, retargeting, propagación temporal, malla, migración NPZ y caché/B2 de V110.3.18.
