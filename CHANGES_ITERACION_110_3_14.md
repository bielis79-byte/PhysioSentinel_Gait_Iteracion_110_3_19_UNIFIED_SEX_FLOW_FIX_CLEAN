# PhysioSentinel Gait · V110.3.14

## Robust B2 Private Loader + Persistent Runtime Cache + Fixed SKEL Mesh Playback

- Congela íntegramente el retargeting SKEL24, q(t) y generación `skin_verts(t)` de V110.3.13.
- Corrige el Auto-Loader privado de Backblaze B2:
  - primero busca un ZIP SKEL válido en `/tmp/physiosentinel_skel_b2_cache_v1_1`;
  - autentica con `b2_authorize_account`;
  - intenta descarga por API S3-compatible usando `s3ApiUrl`;
  - conserva descarga Native API como fallback;
  - muestra `CACHE HIT`, `B2 AUTH OK`, `B2 DOWNLOAD OK` o `MANUAL FALLBACK`.
- Una carga manual válida se copia a la misma caché runtime y se reutiliza en reruns posteriores de la misma instancia.
- Un error 401/403 de B2 no elimina una caché válida existente.
- Sustituye el reproductor `fig.frames` de V110.3.13 por un reproductor HTML/JavaScript explícito:
  - actualiza directamente `x/y/z` de la `Mesh3d` y de los joints;
  - Play 0.5× / 1× / 2× / Pausa;
  - slider por frame;
  - contador visible de frame;
  - no modifica el NPZ científico ni recalcula la marcha.

V110.3.9 permanece congelada como primera versión SKEL anatómicamente válida.
V110.3.13 permanece congelada como base de la malla anatómica animada.
