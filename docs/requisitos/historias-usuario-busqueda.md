# Historias de usuario de búsqueda

| Campo | Valor |
| --- | --- |
| Proyecto | Proyecto Simbiosis |
| Fecha | 28/10/2026 |
| Versión | 1.0 |
| Estado | Borrador |

## Fuentes comunes

- [Acta de UC-21 Buscar recetas](../captura/acta-acuerdos-uc-21-buscar-recetas.md), v1.1, Vigente.
- [Catálogo de requisitos](catalogo-requisitos.md), UR-08 y FR pertinentes.
- [Modelo de casos de uso](../modelos/modelo-casos-de-uso.md), UC-21.

## Épica de búsqueda

Como persona usuaria registrada, quiero buscar recetas mediante texto, ingredientes deseados e ingredientes a excluir, para encontrar platos que se ajusten a mis gustos y restricciones dietéticas.

**Estado:** descompuesta en US-01, US-02 y US-03. Conserva la necesidad conjunta.

## Justificación de la división

Dividir la épica permite abordar la búsqueda textual y la filtración por ingredientes como capacidades independientes que aportan valor por sí solas. Además, separar la inclusión de la exclusión de ingredientes facilita gestionar los conflictos entre ambos criterios y mantener un alcance manejable para cada iteración.

## US-01

**Título:** Búsqueda por texto

Como persona usuaria registrada, quiero buscar recetas introduciendo una palabra o frase, para localizar platos específicos o relacionados con un tema de mi interés.

**Fuentes:** UR-08; UC-21; FR-085; acta, apartados "Criterios de búsqueda" y "Búsqueda sin resultados".

### Criterios de aceptación

- **CA-01.** Dado que existen recetas publicadas con la palabra "vegano" en el título, cuando busco la palabra "vegano", entonces el sistema muestra las recetas que la contienen ignorando mayúsculas y tildes.
- **CA-02.** Dado que existe una receta con la descripción "salsa de tomate casera", cuando busco la frase "salsa de tomate", entonces el sistema muestra la receta si coinciden las palabras en el mismo orden.
- **CA-03.** Dado que no hay recetas que contengan la palabra "espagueti", cuando busco espageti", entonces el sistema indica que no hay resultados y propone la corrección ortográfica "espagueti".

## US-02

**Título:** Busqueda por ingredientes incluidos

Como persona usuaria registrada, quiero buscar recetas seleccionando los ingredientes que deben contener, para aprovechar los productos que tengo disponibles o asegurar que el plato contenga mis alimentos favoritos.

**Fuentes:** UR-08; UC-21; FR-086; acta, apartado "Criterios de búsqueda".

### Criterios de aceptación

- **CA-01.** Dado que selecciono "pollo" y "limón" como ingredientes a incluir, cuando ejecuto la búsqueda, entonces el sistema muestra solo las recetas que contienen ambos ingredientes simultáneamente. 
- **CA-02.** Dado que he seleccionado "tomate" como ingrediente a incluir, cuando retiro "tomate" y añado "queso" antes de buscar, entonces el sistema ejecuta la búsqueda considerando únicamente "queso".
- **CA-03.** Dado que no he introducido texto ni seleccionado ningún ingrediente, cuando intento ejecutar la búsqueda, entonces el sistema solicita un criterio y conserva la pantalla sin ejecutar la consulta.

## US-03

**Título:** Exclusión de ingredientes y filtros combinados.

Como persona usuaria registrada, quiero excluir ingredientes de los resultados y combinar este filtro con otros criterios, para evitar alimentos que me desagradan o a los que tengo alergia, afinando los resultados obtenidos.

**Fuentes:** UR-08; UC-21; FR-087; acta, apartado "Criterios de búsqueda.

### Criterios de aceptación

- **CA-01.** Dado que selecciono "cilantro" como ingrediente a excluir, cuando ejecuto la búsqueda, entonces el sistema no muestra ninguna receta que contenga "cilantro" en sus resultados.
- **CA-02.** Dado que selecciono "nueces " tanto para incluir como para excluir, cuando intento buscar, entonces el sistema señala el conflicto y no ejecuta la búsqueda hasta que lo corrija.
- **CA-03.** Dado que busco el texto "ensalada", incluyo "tomate" y excluyo "cebolla", cuando ejecuto la búsqueda, entonces el sistema muestra solo recetas que cumplen los tres criterios simultáneamente.

## Revisión INVEST

La revisión de INVEST : A continuación se presenta la revisión de las **Historias de Usuario (US)** y sus correspondientes **Criterios de Aceptación (CA)**, aplicando la plantilla estructural, los criterios **INVEST**, la estructura **Dado-Cuando-Entonces**, los defectos frecuentes de redacción y la trazabilidad con los acuerdos de las actas del proyecto:

| ID | Clasificación | Justificación breve |
| --- | --- | --- |
| **US-01** | **Correcto** | Cumple la plantilla «Como [rol], quiero [capacidad], para [finalidad]» con sus tres elementos presentes y delimitados. Satisface todos los criterios INVEST (Independiente, Negociable, Valiosa, Estimable, Pequeña y Testable), no incurre en defectos frecuentes y es trazable con las actas de acuerdos del proyecto sobre la búsqueda de recetas. |
| **CA-01 (US-01)** | **Correcto** | Cumple la estructura Dado-Cuando-Entonces, es atómico, verificable y está formulado en términos observables de comportamiento. Es independiente de la interfaz de usuario y de detalles de implementación, y cubre el caso nominal de búsqueda con insensibilidad a mayúsculas y tildes. |
| **CA-02 (US-01)** | **Correcto** | Sigue la estructura Dado-Cuando-Entonces, es atómico, objetivamente verificable e independiente de la interfaz de usuario, evaluando de forma precisa la coincidencia de frase exacta. |
| **CA-03 (US-01)** | **Incorrecto** | Incumple el criterio de trazabilidad con las actas de acuerdos al incorporar una función de propuesta automática de corrección ortográfica que no figura como acuerdo confirmado en la documentación fuente del proyecto. |
| **US-02** | **Correcto** | Respeta la plantilla obligatoria («Como [rol], quiero [capacidad], para [finalidad]»), cumple cada uno de los criterios INVEST, no presenta defectos de diseño ni términos de implementación y posee trazabilidad con los acuerdos de las actas. |
| **CA-01 (US-02)** | **Correcto** | Presenta la estructura Dado-Cuando-Entonces, define un comportamiento atómico, observable y verificable para la inclusión conjunta de ingredientes, sin acoplamiento con la interfaz de usuario. |
| **CA-02 (US-02)** | **Correcto** | Formulado según el patrón Dado-Cuando-Entonces, es atómico, verificable y neutro respecto a la interfaz, comprobando la actualización de criterios antes de ejecutar la búsqueda. |
| **CA-03 (US-02)** | **Correcto en lo esencial, pero necesita ajuste** | Aunque aplica la estructura Dado-Cuando-Entonces y evalúa la validación de búsqueda vacía, incumple el principio de independencia de la interfaz de usuario al incluir una referencia directa a un elemento visual («conserva la pantalla»). |
| **US-03** | **Correcto en lo esencial, pero necesita ajuste** | Sigue la plantilla básica, pero incumple la dimensión «Pequeña» (singularidad) de los criterios INVEST al mezclar dos capacidades distintas en la cláusula de acción (la exclusión de ingredientes y la combinación con otros filtros de búsqueda). |
| **CA-01 (US-03)** | **Correcto** | Cumple la estructura Dado-Cuando-Entonces, resulta atómico, verificable y libre de dependencias de la interfaz de usuario, cubriendo el escenario nominal de exclusión de ingredientes. |
| **CA-02 (US-03)** | **Correcto** | Formulado mediante Dado-Cuando-Entonces, es atómico, verificable e independiente de decisiones de diseño, cubriendo la detección de conflictos entre criterios de inclusión y exclusión. |
| **CA-03 (US-03)** | **Correcto** | Sigue la estructura Dado-Cuando-Entonces, es atómico, verificable e independiente de la interfaz, evaluando de forma completa la combinación simultánea de texto, inclusión y exclusión. |

🔍 ¿Deseas proporcionar los requisitos de interfaz o las reglas de negocio vinculadas a este módulo para proceder con su revisión?

| Criterio | Pregunta de revisión | Aplicado | Cumple | Justificación |
| --- | --- | --- | --- | --- |
| Independiente | ¿Puede implementarse cada historia y ofrecer un resultado útil sin implementar antes las otras historias del conjunto? Puede compartir infraestructura con ellas. | [Sí/No] | [Sí/No/Pendiente] | [Historias y motivo] |
| Negociable | ¿Cada historia explica qué necesita la persona y deja margen para discutir los detalles de la solución, respetando los acuerdos confirmados? | [Sí/No] | [Sí/No/Pendiente] | [Historias y motivo] |
| Valiosa | ¿La parte «para…» de cada historia explica el beneficio que obtiene la persona al usar esa capacidad? | [Sí/No] | [Sí/No/Pendiente] | [Historias y motivo] |
| Estimable | ¿Están claros el alcance y los datos necesarios para estimar el trabajo de cada historia? | [Sí/No] | [Sí/No/Pendiente] | [Historias y motivo] |
| Pequeña | ¿Se centra cada historia en una única capacidad de alcance manejable? | [Sí/No] | [Sí/No/Pendiente] | [Historias y motivo] |
| Comprobable | ¿Los criterios de aceptación de cada historia describen acciones y resultados observables que permiten distinguir un comportamiento correcto de uno incorrecto? | [Sí/No] | [Sí/No/Pendiente] | [Historias y motivo] |

## Dudas pendientes