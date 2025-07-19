# Proyecto: Auditoría Forense – Práctica MF0488_3

---

## Descripción general

Este proyecto documenta la práctica evaluable E3 del módulo MF0488_3 (Seguridad Informática) del certificado IFCT0109. Consiste en la resolución de tres casos prácticos relacionados con auditoría forense y respuesta ante incidentes: (1) gestión legal de incidentes y restauración de sistemas, (2) clasificación y análisis de evidencias digitales, y (3) análisis forense de una imagen de disco con Autopsy. El propósito es que el alumno aplique técnicas de seguridad y herramientas forenses para investigar incidentes, cumpliendo con la legislación aplicable. En este repositorio se incluyen el informe técnico detallado y los recursos utilizados para cada caso.

---

## Estructura del repositorio

```
.
├── informe_tecnico.md    # Informe técnico completo de la práctica
├── README.md             # Descripción del proyecto y documentación general
└── evidencias/           # Carpeta con archivos de evidencias y ejemplos (si procede)
    ├── imagen_forense.dd # Imagen de disco utilizada en el Caso 3
    └── ...               # Otros archivos relacionados con los casos
```

* informe_tecnico.md:  Documento principal con portada, contenidos, desarrollo de los casos prácticos, conclusiones y anexos.

* README.md: Este archivo, con información del proyecto, estructura del repositorio, herramientas y créditos.

* evidencias/ (opcional): Carpeta para almacenar archivos auxiliares, como la imagen forense (.dd) del Caso 3 u otros datos utilizados.

---

## Herramientas utilizadas

* Autopsy (The Sleuth Kit): Plataforma gráfica de análisis forense digital para examinar sistemas de archivos, metadatos y contenidos.

* The Sleuth Kit (CLI): Conjunto de utilidades de línea de comandos para análisis forense de discos (incluye herramientas como fls, icat, istat).

* PhotoRec: Herramienta de recuperación de archivos eliminados por contenido, incluida con The Sleuth Kit.

* Wireshark: Analizador de tráfico de red para examinar archivos de captura .pcap (Caso 2).

* Visualizadores de logs: (p. ej. Splunk, ELK o visores nativos del sistema) para analizar archivos de registro del sistema operativo.

Otras herramientas: Dependiendo del caso, también se podrían usar herramientas de copia forense (dd, FTK Imager) y análisis de procesos o memoria si fuese necesario. Todas las herramientas mencionadas son de uso estándar en entornos de ciberseguridad.

---

## Instrucciones generales

- Lectura del informe: Abra informe_tecnico.md en un editor o visor de Markdown para revisar el desarrollo de los casos y las soluciones propuestas.

- Reproducción del Caso 3: Para replicar el análisis forense, cree un nuevo caso en Autopsy e importe la imagen de disco (imagen_forense.dd) proporcionada en la carpeta evidencias/. Active los módulos recomendados (Recent Activity, Hash Lookup, File Type Identification, etc.) y ejecute el ingest. Utilice las vistas de texto y metadata en Autopsy para buscar las palabras clave especificadas (“cat”) y verificar el hallazgo de la frase secreta.

- Casos teóricos (1 y 2): No requieren ejecución de software específico. Para el Caso 1, revise la legislación mencionada y detalle el plan de actuación. Para el Caso 2, clasifique las evidencias de acuerdo con la volatilidad y describa los pasos de análisis forense (referenciando las herramientas sugeridas).

En general, se recomienda documentar cada acción tomada, manteniendo la cadena de custodia de las evidencias digitales y siguiendo buenas prácticas forenses descritas en el informe.

---

## Créditos

* Deborah Loisel Santana

* Módulo: IFCT0109 – Seguridad Informática (MF0488_3)
