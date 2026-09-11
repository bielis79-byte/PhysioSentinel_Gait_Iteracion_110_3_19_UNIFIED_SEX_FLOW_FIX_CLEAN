# V110.3.14 · Robust B2 Private Loader + Persistent Runtime Cache + Fixed SKEL Mesh Playback

Esta versión es deliberadamente de infraestructura/presentación. No cambia el retargeting, la calibración SKEL24, la propagación temporal ni los `skin_verts` de V110.3.13.

## Carga privada SKEL

Orden de resolución:

1. `CACHE HIT` en `/tmp/physiosentinel_skel_b2_cache_v1_1`.
2. `B2 AUTH OK` mediante `B2_KEY_ID` y `B2_APPLICATION_KEY`.
3. Descarga privada por S3-compatible API usando el `s3ApiUrl` que devuelve Backblaze.
4. Fallback Native API por nombre de archivo.
5. `MANUAL FALLBACK` si B2 no está disponible.

La carga manual alimenta también la caché runtime para que el mismo contenedor no vuelva a pedir el ZIP en cada rerun.

## Reproductor de la malla

El reproductor ya no depende de `Plotly fig.frames`. Los 75 frames de vértices se mantienen en memoria del navegador y `requestAnimationFrame` actualiza directamente la geometría visible. El contador de frame permite verificar que la secuencia avanza realmente.
