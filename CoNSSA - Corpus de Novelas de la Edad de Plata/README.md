# CoNSSA — Corpus de Novelas de la Edad de Plata

Colección de **217 novelas españolas** (1880–1939) en texto plano, organizadas por década, extraídas y reordenadas a partir del repositorio original:

🔗 https://github.com/cligs/conssa

Corpus diseñado y compilado por **José Calvo Tello** (Universidad de Würzburg), como parte de su tesis doctoral en el grupo de investigación *Computational Literary Genre Stylistics* (CLiGS), dirigido por Christof Schöch.

## Qué contiene esta carpeta

- **`Textos por decada/`** — las 217 novelas en `.txt`, repartidas en subcarpetas por década (1880s–1930s). Cada archivo lleva un nombre legible: `Autor - Título (Año) [idno].txt`, y comienza con una pequeña cabecera bibliográfica (autor, año, género, subgénero, identificador del corpus).
- **`Índice.md`** — tabla completa de las 217 novelas, agrupadas por década, con autor, título, año y (sub)género.
- **`Índice general.csv`** — el mismo índice en formato tabular, útil para abrir en una hoja de cálculo o importar a una base de datos.

## Nota sobre el corpus completo

El repositorio original contiene **358 novelas** en total, pero solo 217 (61%) pueden publicarse actualmente en texto plano por restricciones de derechos de autor sobre las ediciones digitalizadas; esas 217 son justamente las que aquí se incluyen. El repositorio original ofrece además, para quien lo necesite:

- Los archivos en **XML-TEI** (anotación lingüística completa: morfológica, sintáctica, semántica y de discurso directo) en `master/annotated/` y `master/master/`.
- **Metadatos extendidos** por novela (autor, género, ambientación, personajes, etc.) en `metadata/metadata.tsv`.
- **Tablas de frecuencias léxicas y semánticas** en `extracted-features/`.

Estos materiales no se incluyeron aquí para mantener la colección centrada en los textos legibles; si te interesan, dímelo y te los preparo también.

## Licencia y cita

- **Los textos en sí son de dominio público** (Public Domain Mark).
- La marcación XML-TEI y los metadatos del repositorio original están bajo licencia **CC-BY 4.0**.

Cita sugerida del corpus:

> Calvo Tello, José. *Corpus of Novels of the Spanish Silver Age (CoNSSA)*. University of Würzburg, 2021. https://github.com/cligs/conssa
