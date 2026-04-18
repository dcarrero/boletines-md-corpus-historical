# boletines-md-corpus-historical

Archivo **histórico** de los boletines oficiales españoles anteriores a 2019, descargados, normalizados y publicados como Markdown plano con frontmatter YAML estructurado.

> **Estado:** backfill histórico en progreso. Primera fuente: **BOE** (Boletín Oficial del Estado). La API de datos abiertos del BOE ofrece XML estructurado hasta 2009; anteriores (pre-2009) solo están en PDF y quedan fuera de scope hasta que haya OCR.

Este repositorio es el **complemento histórico** de [`boletines-md-corpus`](https://github.com/dcarrero/boletines-md-corpus), que contiene el corpus desde **2019 hasta hoy** y se actualiza diariamente. Aquí se publican los años 2018 hacia atrás, en bloques, sin actualización continua.

---

## Qué hay aquí

Cada disposición publicada en un boletín oficial es un único fichero `.md` con metadatos completos en el frontmatter y el cuerpo normalizado a Markdown plano.

```
boletines-md-corpus-historical/
├── README.md
├── SPEC.md                    ← especificación completa del formato
└── boe/                       ← prefijo por fuente
    └── 2018/
        └── 12/
            └── 31/
                ├── _sumario.md       ← índice del día
                ├── BOE-A-2018-17989.md
                └── ...
```

---

## Formato y especificación

El formato es **idéntico** al del corpus principal. Consulta [`SPEC.md`](SPEC.md) para la especificación completa (frontmatter, jerarquía de encabezados, mapeo XML→Markdown, reglas de normalización).

---

## Cómo usar el corpus

### Clonar y leer

```bash
git clone https://github.com/dcarrero/boletines-md-corpus-historical.git
cd boletines-md-corpus-historical
ls boe/2018/01/02/
```

### Búsqueda con ripgrep

```bash
rg 'rango: "ley orgánica"' boe/
rg -l "transición energética" boe/
```

### Combinar con el corpus principal

Para análisis que cruce pre-2019 y post-2019, clona ambos repos como hermanos:

```bash
git clone https://github.com/dcarrero/boletines-md-corpus-historical.git
git clone https://github.com/dcarrero/boletines-md-corpus.git
```

---

## Licencia y atribución

- **El contenido** de los boletines oficiales es de **dominio público** en España (art. 13 de la Ley de Propiedad Intelectual).
- **El formato, la normalización y la organización** del corpus se publican bajo licencia **MIT**.
- **Para citas oficiales**, consulta siempre la URL `url_html` o `url_pdf` del frontmatter del documento. Este corpus es una herramienta de acceso, no una fuente oficial.

---

## Cómo se genera

El código que descarga el BOE y normaliza el XML a Markdown vive en un repo privado separado. Este repositorio contiene únicamente los datos resultantes del proceso. Si encuentras un error de normalización o un campo de frontmatter incorrecto, abre un issue aquí indicando el `identificador` del documento afectado.
