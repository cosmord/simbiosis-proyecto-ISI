
# L3 Instrucciones de trabajo

| Versión | Fecha | Estado |
| :--- | :--- | :--- |
| 3.2 | 29/09/2026 | Vigente |

El producto de L3 es el repositorio individual y la URL del commit final que se entrega en Moovi.

---

## 1. Crear y reconocer el repositorio

1. Abrid el repositorio plantilla: [https://github.com/kikebar/simbiosis-proyecto-isi-plantilla](https://github.com/kikebar/simbiosis-proyecto-isi-plantilla)
2. Seleccionad **Use this template** y después **Create a new repository**.
3. Elegid un nombre sin datos personales y dejad el repositorio como público.
4. Comprobad que aparecen las carpetas y archivos de la plantilla.
5. No utilicéis un *fork*, ramas ni solicitudes de incorporación de cambios (*pull requests*).

### Documentos de referencia en L3

| Documento | Para qué sirve en L3 |
| :--- | :--- |
| **Actas de captura UR-01 y UR-05** | Conservan la información obtenida. No se editan. |
| **Documento de Visión y Alcance** | Presenta el contexto, el alcance, las restricciones y las obligaciones conocidas. |
| **Acta de captura de requisitos generales** | Aporta decisiones confirmadas sobre el dominio, perfiles y experiencia de uso (información extraída de la entrevista realizada en la sesión A03). |
| **Acta de acuerdos técnicos y operativos** | Aporta condiciones de calidad, interfaces y restricciones técnicas. |
| **SRS y catálogo** | Contienen el glosario y el apartado donde se añadirán los NFR. |
| **Guía rápida** | Explica cómo redactar requisitos y distinguirlos de las reglas de negocio. |

> [!IMPORTANT]
> En L3 **no se revisan ni se amplían los UR ni los FR**. Solo se añaden los NFR y el glosario acordados.

---

## 2. Definir requisitos no funcionales (NFR)

Consultad el Documento de Visión y Alcance, el acta de captura de requisitos generales y el acta de acuerdos técnicos y operativos. Usad la guía rápida para revisar la redacción.

Un NFR expresa una condición que debe cumplir la plataforma. Debe poder comprobarse con una medida, una condición concreta, un estándar o un método de prueba. No escribáis solo «rápido», «seguro» o «fácil de usar».

### Tipos de NFR

| Tipo | Qué buscar |
| :--- | :--- |
| **NFR de calidad (NFR-Q)** | Atributos de calidad, como disponibilidad, integridad, recuperación, rendimiento, capacidad, autonomía, accesibilidad... |
| **Restricciones de diseño e implementación (NFR-R)** | Por ejemplo: plataforma web, despliegue y tecnología web. |
| **Requisitos de interfaz (NFR-I)** | Por ejemplo: idioma de la interfaz y autenticación con Google. |

### Preguntas para localizar NFR

Usad estas preguntas para buscar condiciones confirmadas en el Documento de Visión y Alcance, el acta de A3 y el acta de acuerdos técnicos y operativos.

| Aspecto | Pregunta |
| :--- | :--- |
| **Rendimiento** | ¿Qué tiempos de respuesta o capacidad debe tener el sistema? |
| **Seguridad** | ¿Qué debe exigir sobre autenticación, cifrado y protección frente a accesos no autorizados? |
| **Disponibilidad y fiabilidad** | ¿Cuándo debe estar disponible el sistema? ¿Qué debe ocurrir si falla? |
| **Usabilidad y accesibilidad** | ¿Qué condiciones de accesibilidad o facilidad de uso deben poder comprobarse? |
| **Compatibilidad y portabilidad** | ¿Qué navegadores, dispositivos o idiomas debe admitir el sistema? |
| **Obligaciones legales y normativas** | ¿Qué exige la ley, por ejemplo sobre protección de datos, consentimiento o conservación de información? |

### Cómo trabajar

1. Buscad una condición confirmada en las tres fuentes indicadas antes.
2. Redactad un NFR por cada condición que podáis justificar.
3. Comprobad en el cuaderno de revisión de requisitos (NotebookLM) si es correcto.
4. Anotad: identificador, tipo, texto, ámbito, fuente y método de comprobación (cuando la fuente permita definirla).
5. Indicad **G** si afecta a toda la plataforma y **L** si se aplica a un UR, FR, funcionalidad o rol de usuario concreto.
6. Si falta una decisión, anotad la pregunta en la sección de *decisiones pendientes* de la SRS.

### Reglas de negocio
Las reglas de negocio **no** se incorporan como NFR. Por ejemplo, la aprobación de recetas, la aprobación de cuentas o el acceso de un cuidador mientras existe una asociación vigente son políticas del negocio. Si una regla exige una función del sistema, esa función es un FR derivado.

### Incorporación y commit
Editad el apartado «5. Requisitos no funcionales» de `docs/requisitos/catalogo-requisitos.md`. Guardad el cambio en el repositorio con un mensaje claro, por ejemplo: `L3: añade requisitos no funcionales`.

---

## 3. Elaborar el glosario del dominio

Buscad términos en el Documento de Visión y Alcance y en el acta de captura de requisitos generales. El glosario forma parte de la SRS y **no es un diccionario general de informática**.

Criterios para incluir un término:
1. El término es propio del dominio de Proyecto Simbiosis.
2. Aparece en un UR, un FR o un documento del caso.
3. Puede entenderse de más de una manera si no se define.

Para cada entrada escribid el término, su definición dentro del proyecto y la fuente. No se fija una cantidad de entradas.

**Incorporación:**
Editad la sección «9. Glosario» de `docs/requisitos/srs.md`. Guardad el cambio con un mensaje claro, por ejemplo: `L3: añade el glosario del dominio`.


> Las decisiones se pueden tomar en equipo. Después, cada estudiante incorpora el mismo resultado a su repositorio individual.

---

## 4. Comprobar y entregar

### Antes de entregar
- [ ] El repositorio es público y no contiene datos personales.
- [ ] El apartado de NFR contiene solo requisitos justificados por las fuentes.
- [ ] Cada NFR tiene tipo, fuente y ámbito **G** o **L**.
- [ ] El glosario contiene términos del dominio, definiciones del proyecto y fuentes.
- [ ] Los UR y FR canónicos **no se han modificado**.
- [ ] Los cambios están registrados con commits de mensajes claros.

### Entrega en Moovi
1. Abrid el historial de commits de vuestro repositorio.
2. Seleccionad el commit final, que debe incluir los NFR y el glosario.
3. Copiad la **URL permanente** de ese commit (no solo la URL general del repositorio).
4. Entregad esa URL y la declaración de uso de IA en Moovi.

> [!WARNING]
> **No hay que entregar ningún archivo** adjunto, solo la URL del commit.

### Si falla un servicio
- Si **GitHub** no está disponible, conservad el contenido acordado y actualizad el repositorio cuando se restablezca.
- Si **Moovi** no está disponible, conservad la URL del commit y entregadla cuando el servicio vuelva a funcionar.

