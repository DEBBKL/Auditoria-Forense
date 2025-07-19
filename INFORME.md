# Proyecto: Auditoría Forense – Práctica MF0488\_3

---

## Índice

* [Descripción general](#descripción-general)
* [Estructura del repositorio](#estructura-del-repositorio)
* [Herramientas utilizadas](#herramientas-utilizadas)
* [Instrucciones generales](#instrucciones-generales)
* [Créditos](#créditos)

---

## Descripción general

Este proyecto documenta la práctica evaluable E3 del módulo MF0488\_3 (Seguridad Informática) del certificado IFCT0109. Consiste en la resolución de tres casos prácticos relacionados con auditoría forense y respuesta ante incidentes:

1. Gestión legal de incidentes y restauración de sistemas.
2. Clasificación y análisis de evidencias digitales.
3. Análisis forense de una imagen de disco con Autopsy.

El propósito es que el alumno aplique técnicas de seguridad y herramientas forenses para investigar incidentes, cumpliendo con la legislación aplicable.

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

---

## Herramientas utilizadas

* **Autopsy (The Sleuth Kit):** Plataforma gráfica para el análisis forense digital, utilizada para la inspección de imágenes de disco, extracción de metadatos, búsquedas por palabras clave y recuperación de archivos.
* **The Sleuth Kit (CLI):** Herramientas de línea de comandos para examinar estructuras de sistemas de archivos.
* **PhotoRec:** Para la recuperación de archivos eliminados mediante técnicas de carving.
* **Wireshark:** Inspección de tráfico de red para analizar conexiones y posibles actividades sospechosas.
* **Event Viewer / syslog / Splunk / ELK Stack:** Visualización de registros del sistema operativo.
* **FTK Imager, `dd`, NetworkMiner:** Utilidades para copias forenses, adquisición de evidencias y análisis de red.

---

## Instrucciones generales

---

### Caso práctico 1: Gestión legal y restauración de sistemas

**Escenario:** Una empresa ha sufrido una intrusión en su sistema de red con acceso no autorizado a la base de datos de clientes.

---

#### a. Obligaciones legales ante incidentes de seguridad

Ante este tipo de incidentes, la legislación vigente en España y la Unión Europea obliga a las organizaciones a actuar de forma diligente. Entre las normativas más relevantes se encuentran:

* **RGPD (Reglamento General de Protección de Datos - UE 2016/679):** Artículo 33 obliga a notificar cualquier violación de la seguridad de los datos personales a la AEPD en un plazo no superior a 72 horas desde su detección.
* **LOPDGDD (Ley Orgánica 3/2018):** Desarrolla el RGPD y refuerza la obligación de informar a los afectados si existe un riesgo alto para sus derechos y libertades.
* **LSSI-CE (Ley 34/2002):** Para empresas proveedoras de servicios, se exige comunicar de inmediato cualquier vulneración grave de la seguridad.
* **RDL 12/2018 y RD 43/2021 (Directiva NIS):** Establecen medidas para sectores esenciales e infraestructuras críticas, incluyendo la obligación de notificar incidentes al CCN-CERT o INCIBE-CERT.

---

#### b. Proceso de restauración del sistema comprometido

Una vez identificada la intrusión, se deben aplicar las fases del plan de respuesta ante incidentes:

1. **Identificación y análisis:** Se confirma la intrusión mediante registros, alertas y monitorización de sistemas.
2. **Contención:** Se aísla el sistema afectado de la red para evitar la propagación de daños.
3. **Erradicación:** Se eliminan los vectores de ataque (malware, cuentas sospechosas, servicios inseguros).
4. **Recuperación:** Se restauran los servicios desde copias de seguridad verificadas, se aplican parches y se refuerzan las configuraciones de seguridad.
5. **Mejoras preventivas:** Se implantan medidas adicionales como firewalls avanzados, autenticación multifactor (MFA), segmentación de red y políticas de acceso más restrictivas.
6. **Documentación y lecciones aprendidas:** Se recopila toda la información sobre el incidente y se actualizan los planes de contingencia y respuesta para futuros casos.

---

### Caso práctico 2: Clasificación de evidencias digitales y análisis forense

#### Clasificación de evidencias según orden de preservación

La evidencia digital debe recogerse en orden inverso a su volatilidad. Este principio garantiza que los datos más efímeros se conserven antes de que desaparezcan:

1. **Captura de paquetes de red:** Son extremadamente volátiles. Deben guardarse en tiempo real. Herramientas: *Wireshark, tcpdump, NetworkMiner*.
2. **Archivos de registro (logs):** Se deben copiar antes de que se sobrescriban. Herramientas: *Event Viewer (Windows), syslog, Splunk*.
3. **Ficheros temporales del sistema:** Pueden contener fragmentos útiles. Herramientas: *Autopsy, FTK Imager*.
4. **Hardware con datos sensibles:** Aunque menos volátil, debe copiarse mediante imágenes forenses con write-blockers. Herramientas: *FTK Imager, Guymager, dd*.

---

#### Pasos para realizar un análisis forense completo

1. **Adquisición:** Creación de una copia exacta (bit a bit) de las evidencias utilizando herramientas forenses.
2. **Preservación:** Asegurar la integridad de las copias con funciones hash (MD5, SHA-1) y mantener una cadena de custodia documentada.
3. **Análisis:** Examen detallado con herramientas especializadas según el tipo de evidencia (textos, imágenes, logs, red, etc.).
4. **Documentación:** Generación de un informe técnico detallado con cronología de acciones, hallazgos y conclusiones.

---

### Caso práctico 3: Análisis de imagen forense con Autopsy

Este ejercicio práctico tiene como objetivo aplicar técnicas forenses reales sobre una imagen de disco (.dd) para simular un caso de investigación digital. El contexto está relacionado con un caso ficticio vinculado al tráfico de drogas, en el cual se sospecha que existen archivos ocultos y pruebas clave que podrían incriminar a una persona o grupo. Se utilizará la herramienta **Autopsy** como entorno de análisis forense debido a su robustez, interfaz amigable y compatibilidad con los módulos de ingestión del kit forense **The Sleuth Kit**.

El análisis se centrará en tres aspectos fundamentales:

1. **Identificación de actividad reciente del usuario y posibles trazas de comportamiento sospechoso.**
2. **Detección de archivos ocultos, modificados o eliminados, incluyendo imágenes con metadatos relevantes.**
3. **Búsqueda de evidencias textuales mediante palabras clave previamente configuradas para encontrar patrones asociados al caso.**

Cada acción realizada está orientada a preservar la integridad de la evidencia, extraer información significativa y documentar todos los pasos del análisis con capturas de pantalla que validan el procedimiento forense. Las capturas (hasta 15) ilustran visualmente la actividad durante el análisis, proporcionando contexto y respaldo gráfico a cada hallazgo.

---

#### Proceso de análisis paso a paso con Autopsy

A continuación, se describe detalladamente el procedimiento llevado a cabo en Autopsy durante el análisis de la imagen forense:

---

1. **Creación del caso en Autopsy:** Se inició la herramienta Autopsy y se seleccionó la opción de crear un nuevo caso. Se introdujo el nombre del caso, la ubicación donde se almacenarían los datos y una breve descripción del análisis.

---

2. **Adición de la imagen forense:** Se agregó la imagen `.dd` proporcionada mediante la opción "Add Data Source". Se especificó el tipo de fuente (imagen de disco) y se seleccionó el archivo desde el sistema de archivos.

---

3. **Configuración de módulos de ingestión:** Autopsy permite seleccionar módulos que se ejecutan automáticamente durante la carga de la imagen. Se activaron los siguientes:

   * Recent Activity
   * Hash Lookup
   * File Type Identification
   * Extension Mismatch Detector
   * Embedded File Extractor
   * Picture Analyzer
   * Keyword Search
   * Email Parser
   * Interesting Files Identifier
   * PhotoRec Carver

4. **Ejecución del análisis:** Tras confirmar la configuración, Autopsy comenzó a procesar la imagen. El sistema identificó automáticamente particiones y sistemas de archivos válidos y generó una estructura de carpetas para navegar por los archivos recuperados.

---

5. **Exploración de archivos multimedia:** Se accedió a la categoría "Images" dentro de la vista de resultados. Aquí se identificaron 11 imágenes activas. Se inspeccionaron metadatos EXIF como fechas, dispositivos de captura y coordenadas GPS.

---

6. **Recuperación de archivos eliminados:** Desde la sección "Deleted Files" se encontraron 6 archivos que habían sido borrados. Se usó PhotoRec Carver para intentar restaurarlos completamente.

---

7. **Análisis de palabras clave:** Se utilizó el módulo "Keyword Search" con la palabra clave `cat` en modo substring. Esto permitió encontrar coincidencias parciales en archivos de texto, incluyendo la frase secreta. Se analizaron los resultados desde diferentes pestañas:

   * **Hex:** Se examinó la codificación binaria de los archivos.
   * **Strings:** Extrajo cadenas de texto legibles.
   * **Extracted Text:** Muestra texto extraído automáticamente de archivos de documentos o imágenes.
   * **Application:** Mostró los archivos abiertos con sus aplicaciones asociadas.
   * **Metadata:** Permitió ver atributos avanzados como autores, fechas, permisos, etc.

---

8. **Validación del hallazgo clave:** Una de las imágenes contenía texto plano con la frase "Let’s go get some coffee", que fue identificada como la evidencia principal. Esta fue exportada y preservada como parte del informe final.

---

9. **Exportación de evidencias:** Los archivos relevantes fueron exportados utilizando la herramienta integrada de Autopsy, asegurando mantener la integridad mediante el uso de hashes y registros automáticos del sistema.

---

10. **Documentación de todo el proceso:** Durante cada fase se tomaron capturas de pantalla (hasta 15 en total), que servirán para validar visualmente el flujo de trabajo y proporcionar evidencias del análisis realizado para una posterior auditoría o presentación judicial.

Este proceso evidencia la utilidad de Autopsy en entornos reales de investigación, destacando su capacidad para extraer, relacionar y visualizar datos de forma eficiente y profesional.

Se proporcionó una imagen forense de tipo `.dd` para su estudio en la herramienta **Autopsy**. Se crearon módulos de ingestión y se configuraron para extraer información relevante:

* **Recent Activity:** Extrajo el historial reciente de navegación, archivos abiertos y últimos accesos.
* **Hash Lookup:** Verificó los hashes de los archivos frente a bases de datos para identificar posibles amenazas.
* **File Type Identification / Extension Mismatch:** Detectó incoherencias entre el tipo real de archivo y su extensión declarada.
* **Embedded File Extractor:** Extrajo archivos comprimidos o embebidos.
* **Picture Analyser:** Examinó imágenes en busca de metadatos (EXIF, fechas, ubicación).
* **Keyword Search:** Se configuró la búsqueda de la palabra clave “cat” con coincidencia parcial (*Substring Match*).
* **Email Parser y Interesting Files:** Identificaron correos electrónicos y archivos sospechosos.
* **PhotoRec Carver:** Permitió recuperar archivos eliminados.

---

#### Resultados del análisis

* Se identificaron **11 imágenes activas** y **6 archivos eliminados**. Se centró la inspección en imágenes.
* Se analizaron los resultados desde las pestañas: *Hex*, *Strings*, *Extracted Text*, *Application* y *Metadata*.
* Durante la búsqueda por palabra clave, se detectó en texto plano la frase secreta:

**“Let’s go get some coffee”**

Este hallazgo demuestra la eficacia del análisis basado en palabras clave y metadatos para localizar evidencia crucial en investigaciones forenses.

---

## Créditos

* **Alumno:** Deborah Loisel Santana
* **Módulo:** IFCT0109 – Seguridad Informática (MF0488\_3)
