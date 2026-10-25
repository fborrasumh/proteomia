# ProteomIA

El laboratorio de proteómica en tu navegador: del gel 2D al biomarcador. Aplicación web de un solo fichero.

**Usar la app:** https://fborrasumh.github.io/proteomia/

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23646272.svg)](https://doi.org/10.5281/zenodo.23646272)

**Idiomas:** español (por defecto), inglés, portugués; selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL).

## Qué hace

Un laboratorio de Proteómica en el navegador que sigue el temario, las prácticas y el formato de examen de la guía docente 2026-2027 de Proteómica (asignatura 1410, Grado en Biotecnología, UMH). Todo funciona sin clave de IA salvo donde se indica.

- **Gel 2D y DIGE (U2).** 28 proteínas reales de *E. coli* K-12 en tres experimentos (choque térmico, inducción con IPTG, fase exponencial frente a estacionaria). El código calcula pI y masa de la secuencia madura; se elige tira IPG (pH 3-10, 4-7, 6-11) y porcentaje de acrilamida, se marcan los spots que cambian y se comprueba con una t de Welch sobre 3 réplicas (|cambio| ≥ 1,5 y p < 0,05). En DIGE la variación entre réplicas es menor, como con el patrón interno Cy2. Cualquier spot se puede «recortar» e identificar.
- **Espectrometría de masas (U2).** Fórmula, masa monoisotópica y media y distribución isotópica calculadas a partir de la composición elemental; perfil del espectro según la resolución (R = m/Δm) y la carga. Tabla y espectro de iones b/y. Retos de secuenciación de novo distintos por estudiante (se acepta cualquier secuencia que explique todos los iones y la masa del precursor). Deconvolución de la envolvente ESI de proteínas intactas pulsando dos picos.
- **Identificación (U2).** Digestión in silico al estilo PeptideMass de ExPASy (tripsina, Lys-C, Glu-C, Asp-N, quimotripsina, CNBr; escisiones fallidas, carbamidometilación, oxidación de Met). Huella peptídica (PMF) y búsqueda MS/MS contra 82 secuencias reales de UniProtKB/Swiss-Prot (E. coli, proteínas humanas de interés clínico, estándares y contaminantes del repositorio cRAP), con espectros simulados que incluyen error de masa, autólisis de la tripsina, queratinas y ruido. Puntuación probabilística −10·log10(P) con umbral de significación corregido por el número de comparaciones.
- **PTM e interactoma (U3-U4).** Detective de modificaciones por diferencia de masa (20 modificaciones, masas calculadas desde su composición; muestra la ambigüedad acetil/trimetil y fosfo/sulfato según la tolerancia). Reto de localización del sitio de fosforilación con iones b/y. Visor de pares SILAC. Siete escenarios para elegir técnica de interacción (doble híbrido, coinmunoprecipitación, TAP-MS, GST, FRET, phage display, split-ubiquitina). Análisis de una purificación por afinidad con espectrometría (AP-MS) simulada: filtros frente al control, red de interacciones con grado, intermediación y agrupamiento.
- **Metabolómica y clínica (U5-U6).** Metaboloma LC-MS simulado en tres estudios (tumor frente a sano, diabetes tipo 2, enfermedad renal): PCA con escalado a elegir, gráfico de volcán con corrección de Benjamini-Hochberg y anotación por m/z exacta con aductos (el caso leucina/isoleucina). Calculadora de masas desde la fórmula. Curvas ROC de biomarcadores (troponina I, NGAL, PSA) con AUC, punto de Youden y valores predictivos según la prevalencia. Rango dinámico de las proteínas del plasma.
- **Laboratorio de problemas.** Diez tipos (Bradford y carga de la tira, m/z y carga, deconvolución ESI, exactitud y resolución, DIGE, fosfopéptidos, SILAC, FRET, aductos de metabolitos, prueba diagnóstica) con datos distintos por estudiante a partir de su código. La solución la calcula el código y, si la respuesta es incorrecta, se recalcula con los errores típicos declarados para explicar el fallo.
- **Simulacro de examen.** 39 preguntas tipo test y 7 preguntas cortas repartidas por las seis unidades. El test lo corrige el código con la clave; **no pone nota ni aplica la penalización del examen real**. Las preguntas cortas tienen revisión de conceptos sin IA o feedback detallado con IA.
- **Casos (U1-U6).** Seis problemas abiertos con pistas graduadas y un tutor socrático.
- **Tarjetas, Mis apuntes y Progreso.** 28 tarjetas con repetición espaciada; preguntas a los apuntes propios y tarjetas generadas a partir de ellos (con IA, cita comprobada); aciertos recientes por unidad y exportación a Word, CSV y JSON.

## Cómo se usa la IA

Con la propia clave de OpenAI, Google Gemini o Anthropic Claude. La clave se guarda solo en el navegador. No hace falta servidor. La IA solo se usa en el feedback de las preguntas cortas, el tutor de los casos y los apuntes; no calcula nada ni pone notas.

## Privacidad

Todo se procesa y se guarda en el navegador (IndexedDB): progreso, respuestas, apuntes y la clave de IA. La base de datos de secuencias va dentro del propio fichero, y todos los cálculos (masas, espectros, búsquedas, geles, estadística y laboratorio) los hace el código sin red.

Solo salen datos hacia el proveedor de IA si se usan las funciones con IA: las respuestas cortas, los mensajes al tutor o los apuntes, con correos, documentos de identidad y teléfonos enmascarados y tras un aviso previo con una muestra de lo que sale. El JSON exportado no contiene la clave de API.

## Límites

- El contenido (test, preguntas cortas, tarjetas, casos) es material de repaso elaborado a partir del temario de la guía docente: puede contener errores u omisiones. Mandan el profesorado, la guía docente y los guiones de prácticas.
- El gel 2D, los espectros de ejemplo, la red AP-MS, el metaboloma y los biomarcadores son **simulaciones didácticas**: las abundancias y los cambios tienen el sentido biológico esperado, pero no son medidas reales.
- La base de datos tiene 82 secuencias completas (con péptido señal cuando lo tienen): no sustituye a una búsqueda en Swiss-Prot o UniProt completos.
- La puntuación de las búsquedas se inspira en la lógica de MOWSE y Mascot, **pero no es Mascot**: sus valores no son comparables. Supone que las masas de los péptidos se concentran en una banda de unos 0,15 Da por unidad de masa nominal; en espectros simulados identifica la proteína correcta en 228 de 234 casos con 2 falsos positivos significativos.
- El pI usa los pKa de EMBOSS; otras herramientas pueden dar valores algo distintos. La lista de metabolitos para anotar es corta (35).
- El simulacro no pone nota ni reproduce la penalización del examen real. Si la IA cuela una calificación, el código la elimina. El feedback de la IA solo se muestra cuando su cita literal aparece de verdad en la respuesta del estudiante.
- El tutor de los casos no recibe la solución y el código filtra sus frases, pero el filtro es una lista de términos: puede dejar pasar una formulación inesperada.

Probado con IA simulada de los tres proveedores (incluida una IA que inventa citas, cuela una nota y chiva la solución), en español, inglés y portugués, en escritorio y móvil. Las masas se contrastaron con Unimod y con los picos de autólisis de la tripsina (842,51; 1045,56; 2211,10). No se ha probado con una clave de API real.

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche) y Vicente Micol Molina (Universidad Miguel Hernández de Elche).

Sigue el temario, las prácticas y el formato de evaluación de la guía docente 2026-2027 de Proteómica (asignatura 1410, Grado en Biotecnología, UMH), cuyo responsable es Vicente Micol Molina.

ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573) · Vicente Micol Molina [0000-0001-8089-0696](https://orcid.org/0000-0001-8089-0696)

## Cómo citar

Borrás Rocher, F. y Micol Molina, V. (2026). *ProteomIA* (v1.0.0) [Software]. DOI: [10.5281/zenodo.23646272](https://doi.org/10.5281/zenodo.23646272)

## Licencia

MIT. Véase [LICENSE](LICENSE). Las secuencias proceden de UniProtKB/Swiss-Prot (CC BY 4.0) a través del repositorio cRAP (The GPM) y del repositorio FoldDock.
