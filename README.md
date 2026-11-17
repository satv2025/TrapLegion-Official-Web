# TrapLegion — Web premium 2026

Sitio público conectado a Supabase. Diseño editorial de sello discográfico, en paleta marfil, verde bosque y dorado suave. Identidad de marca **TrapLegion**, sin separar el nombre.

## Rutas
- `/` página principal
- `/artistas` catálogo de artistas
- `/artist=oficialskb` URL pública oficial: nombre sin espacios, guiones, tildes ni símbolos
- `/artist=matiasponce`, `/artist=eldevon`, `/artist=kaliflow`
- `/artist=andrescalamaro` si se crea un perfil llamado «Andrés Calamaro»
- `/artist?a=Matias%20Ponce` ruta interna equivalente, que también acepta slug compacto
- Los UUID se usan únicamente en Supabase; el nombre completo se muestra en la página
- `/lanzamientos` discografía y tracklists
- `/historia`, `/novedades`, `/novedad=slug`

## Instalación
1. Si no tenés la base: ejecutá `TrapLegion_SUPABASE_COMPLETO.sql` en Supabase SQL Editor. Si tenés la versión anterior, ejecutá `TrapLegion_MIGRACION_URLS_Y_OFICIALSKB.sql` para corregir las URL de artistas y el texto biográfico. Si no aplicaste la revisión premium anterior, ejecutá además `TrapLegion_ACTUALIZACION_EXISTENTE.sql` para limpiar referencias a imágenes antiguas sin borrar tus archivos.
2. Configurá URL y clave **anon/publishable** en `assets/js/config.js`. No coloques nunca claves `service_role`.
3. Desplegá la carpeta en Vercel, manteniendo `vercel.json` y la estructura de archivos.
4. Subí por separado el panel de administración actualizado.

## Carátulas oficiales
Al cargar un lanzamiento, se usa primero la imagen real especificada por vos en Supabase `cover_url` (cuando no es uno de los SVG editoriales de la versión anterior). Si no tiene imagen, intenta recuperar la carátula oficial del `spotify_url` mediante la API pública oEmbed de Spotify. Si no hay enlace de Spotify o el servicio no permite resolverlo desde el navegador, intenta obtener el arte de Apple Music a partir del campo `apple_music_url` (iTunes Lookup). Si los servicios fallan, muestra un bloque tipográfico neutral **sin fingir ser la portada oficial**.

Para `Kali Flow` la imagen del perfil está enlazada al thumbnail público del artista en Spotify, no descargada. Las ilustraciones ficticias de portadas y artistas fueron retiradas de la UI. Las imágenes externas dependen de la disponibilidad y políticas de sus respectivos proveedores. Usá enlaces reales en el panel; no se inventaron IDs ni URLs de discos de Spotify.

### Nota Spotify
Cuando Spotify sea la fuente de la portada, el sitio agrega un enlace de atribución a la ficha del lanzamiento. Las carátulas se muestran enteras sin recortes, siguiendo la guía de Spotify.

## Estilo
Solo `Barlow Condensed`; declarada en `*` con `!important`. Sin shorthand `font:` ni tipografías alternativas. Se mantienen dropdowns custom y sin contorno visual en foco, como pediste.

## Importante
El sitio muestra datos reales de tu catálogo ingresados en Supabase; el panel permite administrarlos. Para ver los datos conectá tu proyecto. No hay sedes ni lanzamientos inventados.


Esta versión incorpora las imágenes originales aportadas por el creador, la biografía completa y SQL complementario incluido en el paquete de entrega.
