# Ejemplos de descripciones detalladas de casos de uso

# Ejemplos de descripciones detalladas de casos de uso

Este documento presenta ejemplos de cómo transformar los acuerdos con un cliente en requisitos y en una descripción detallada de un caso de uso. Cada ejemplo incluye el contexto, un acta de acuerdos, los requisitos derivados y la descripción del caso de uso.

Los ejemplos son ficticios y pertenecen a aplicaciones independientes. Por ello, la numeración de los requisitos y de los casos de uso comienza de nuevo en cada ejemplo: **UR-01**, **FR-001** y **UC-01**.

## Ejemplo 1. Industria química: registrar la recepción de un lote

### 1. Contexto de la aplicación

Una empresa de fabricación de productos químicos utiliza una aplicación para registrar las materias primas que recibe de sus proveedores. Antes de que un lote pueda utilizarse en producción, el departamento de calidad debe evaluarlo.

El ejemplo se centra en el registro de la recepción: identificar el pedido, introducir los datos del lote y aportar el certificado de análisis del proveedor. La evaluación de calidad se realiza posteriormente y queda fuera de este caso de uso.

### 2. Acta de acuerdos con el cliente

| Campo | Valor |
| --- | --- |
| Naturaleza | Acta ficticia elaborada para este ejemplo docente. |
| Funcionalidad | Registro de la recepción de un lote de materia prima. |
| Requisito de usuario | UR-01 · El responsable de recepción podrá registrar la llegada de un lote de materia prima, vinculándolo con el pedido y aportando la documentación necesaria para su posterior evaluación de calidad. |
| Finalidad | Concretar los datos, las comprobaciones y el resultado del registro de una recepción. |

#### 2.1. Participantes

| Rol | Participación |
| --- | --- |
| Responsable de recepción | Necesidades de identificación del pedido y registro del lote recibido. |
| Representante del departamento de calidad | Información y documentación necesarias para evaluar posteriormente el lote. |
| Analista | Registro y organización de los acuerdos. |

#### 2.2. Alcance acordado

- Cada operación de registro se refiere a un único lote recibido y a un único pedido.
- Para este ejemplo, cada pedido corresponde a una materia prima e indica el proveedor, la cantidad prevista y la unidad de medida.
- Los pedidos ya están registrados en la aplicación. El registro de una recepción no permite crear un pedido nuevo.
- La persona que registra la recepción debe haber iniciado sesión y disponer de autorización para realizar esta operación.

#### 2.3. Acuerdos confirmados

**Identificación del pedido**

- El responsable de recepción indicará el identificador del pedido al que corresponde el lote.
- La aplicación mostrará el proveedor, la materia prima, la cantidad prevista y la unidad de medida del pedido localizado.
- Si el pedido no existe, la aplicación lo notificará y permitirá introducir otro identificador. No se podrá registrar una recepción sin asociarla a un pedido existente.

**Datos y documentación del lote**

- El responsable de recepción introducirá el código de lote asignado por el proveedor y la cantidad realmente recibida.
- La cantidad se expresará en la unidad indicada en el pedido; esta operación no incluye conversiones de unidades.
- El responsable de recepción adjuntará el certificado de análisis del proveedor en formato PDF.
- El código de lote no podrá estar vacío y la cantidad recibida deberá ser mayor que cero.
- El certificado será obligatorio. La aplicación comprobará que se ha adjuntado un archivo PDF; la valoración de su contenido corresponderá al departamento de calidad.
- Si falta un dato obligatorio o no cumple estas condiciones, la aplicación indicará el problema y permitirá corregirlo antes de continuar.

**Comprobación de duplicidades y cantidades**

- La combinación de proveedor y código de lote identificará de forma única un lote registrado.
- Si ya existe un lote con esa combinación, la aplicación informará de la duplicidad, mostrará el identificador del registro existente y finalizará la operación sin crear otro registro.
- La aplicación comparará la cantidad recibida con la cantidad prevista en el pedido.
- Si las cantidades son diferentes, la aplicación mostrará ambas y solicitará una confirmación expresa de la cantidad recibida.
- El responsable de recepción podrá confirmar que la cantidad introducida es correcta o volver a los datos del lote para corregirla.
- Cuando se confirme una cantidad diferente, el registro de la recepción dejará constancia de la discrepancia con el pedido. La discrepancia no impedirá registrar la recepción.

**Confirmación y resultado del registro**

- Antes de guardar, la aplicación mostrará un resumen con el pedido, el proveedor, la materia prima, el código de lote, la cantidad recibida, la unidad y el certificado adjunto. Si existe una discrepancia de cantidad confirmada, también la mostrará.
- El responsable de recepción deberá confirmar el registro a partir de ese resumen.
- Tras la confirmación, la aplicación guardará la recepción, le asignará un identificador único y dejará el lote en el estado «Pendiente de evaluación de calidad».
- La aplicación mostrará un mensaje de registro correcto con el identificador de la recepción y el estado del lote.
- El responsable de recepción podrá cancelar antes de confirmar el registro. En ese caso, no se guardará una nueva recepción.
- Si se produce un error al guardar, la aplicación indicará que el registro no se ha completado y sugerirá intentarlo más tarde. La operación no dejará una recepción guardada parcialmente.

#### 2.4. Límites del alcance

| Asunto | Acuerdo |
| --- | --- |
| Creación y modificación de pedidos | Se realiza mediante otras funcionalidades. |
| Evaluación del certificado y del lote | Corresponde a una actividad posterior del departamento de calidad. |
| Autorización para utilizar el lote en producción | No se obtiene al registrar la recepción. |
| Recepciones posteriores del mismo lote | Quedan fuera del ejemplo; una combinación de proveedor y código de lote solo puede registrarse una vez. |
| Conversión de unidades | Queda fuera del ejemplo; se utiliza la unidad del pedido. |

### 3. Requisitos derivados y relación con el caso de uso

#### 3.1. Requisito de usuario

| ID | Requisito de usuario |
| --- | --- |
| UR-01 | El responsable de recepción podrá registrar la llegada de un lote de materia prima, vinculándolo con el pedido y aportando la documentación necesaria para su posterior evaluación de calidad. |

#### 3.2. Requisitos funcionales

Todos los requisitos funcionales de esta tabla se derivan de los acuerdos del acta y están asociados a **UR-01**.

| ID | Requisito funcional |
| --- | --- |
| FR-001 | El sistema debe permitir localizar un pedido por su identificador y mostrar su proveedor, materia prima, cantidad prevista y unidad de medida, o informar de que no existe un pedido con ese identificador. |
| FR-002 | El sistema debe permitir introducir el código de lote del proveedor y la cantidad recibida, expresada en la unidad del pedido. |
| FR-003 | El sistema debe permitir adjuntar el certificado de análisis del proveedor en formato PDF. |
| FR-004 | El sistema debe comprobar que el código de lote no esté vacío, que la cantidad recibida sea mayor que cero y que se haya adjuntado un certificado en formato PDF, e indicar los datos que deban corregirse. |
| FR-005 | El sistema debe impedir el registro de un lote cuando ya exista otro con el mismo proveedor y código de lote, e informar del identificador del registro existente. |
| FR-006 | El sistema debe comparar la cantidad recibida con la cantidad prevista en el pedido. |
| FR-007 | El sistema debe solicitar una confirmación expresa cuando la cantidad recibida difiera de la prevista, permitiendo confirmar la cantidad introducida o volver a corregirla. |
| FR-008 | El sistema debe mostrar un resumen de la recepción y solicitar la confirmación del responsable de recepción antes de guardar el registro. |
| FR-009 | El sistema debe guardar la recepción confirmada con su pedido, proveedor, materia prima, código de lote, cantidad recibida, unidad, certificado y estado «Pendiente de evaluación de calidad», dejando constancia de la discrepancia de cantidad cuando corresponda. |
| FR-010 | El sistema debe asignar un identificador único a cada recepción registrada. |
| FR-011 | El sistema debe mostrar una confirmación del registro correcto que incluya el identificador de la recepción y el estado del lote. |
| FR-012 | El sistema debe permitir cancelar la operación antes de confirmar el registro, sin guardar una nueva recepción. |
| FR-013 | El sistema debe notificar que el registro no se ha completado cuando se produzca un error al guardar, sugerir un nuevo intento posterior y evitar que quede una recepción guardada parcialmente. |

#### 3.3. Relación entre el caso de uso y los requisitos

| ID | Caso de uso | UR asociados | FR asociados |
| --- | --- | --- | --- |
| UC-01 | Registrar la recepción de un lote | UR-01 | FR-001, FR-002, FR-003, FR-004, FR-005, FR-006, FR-007, FR-008, FR-009, FR-010, FR-011, FR-012, FR-013 |

### 4. Descripción detallada de UC-01 · Registrar la recepción de un lote

#### Actor principal

Responsable de recepción.

#### Actores de apoyo

Ninguno. El proveedor y el departamento de calidad no interactúan con el sistema durante este caso de uso. El responsable de recepción aporta el certificado del proveedor y el departamento de calidad evaluará el lote posteriormente.

#### Precondiciones

- El responsable de recepción ha iniciado sesión en la aplicación.
- El responsable de recepción tiene autorización para registrar recepciones.

La existencia del pedido, la validez de los datos y la ausencia de duplicidades se comprueban durante el caso de uso.

#### Postcondiciones

**Tras completar el caso de uso con éxito:**

- La recepción queda registrada y asociada al pedido y al lote identificados.
- Se conservan el proveedor, la materia prima, el código de lote, la cantidad recibida, la unidad y el certificado adjunto.
- La recepción dispone de un identificador único.
- El lote queda en el estado «Pendiente de evaluación de calidad».
- Si la cantidad recibida difiere de la prevista y el responsable ha confirmado esa cantidad, la discrepancia queda reflejada en el registro.
- El responsable de recepción recibe una confirmación en pantalla con el identificador de la recepción y el estado del lote.

**Si el caso de uso termina sin éxito o se cancela:**

- No se crea una nueva recepción ni queda un registro parcial de ella.
- Si se ha detectado una duplicidad, el registro existente se mantiene sin cambios y se informa de su identificador.

#### Escenario principal de éxito

1. El responsable de recepción inicia el registro de una recepción e indica el identificador del pedido.
2. El sistema localiza el pedido y muestra el proveedor, la materia prima, la cantidad prevista y la unidad de medida.
3. El responsable de recepción introduce el código de lote del proveedor, la cantidad recibida en la unidad del pedido y adjunta el certificado de análisis en formato PDF.
4. El sistema comprueba que el código de lote no esté vacío, que la cantidad sea mayor que cero y que se haya adjuntado un certificado en formato PDF.
5. El sistema comprueba que no exista un lote registrado con el mismo proveedor y código de lote.
6. El sistema compara la cantidad recibida con la prevista en el pedido y comprueba que coinciden.
7. El sistema muestra el resumen de la recepción y solicita la confirmación del registro.
8. El responsable de recepción confirma el registro.
9. El sistema guarda la recepción con los datos y el certificado aportados, le asigna un identificador único y deja el lote en el estado «Pendiente de evaluación de calidad».
10. El sistema muestra un mensaje de registro correcto con el identificador de la recepción y el estado del lote.

#### Extensiones

**2.a. El pedido indicado no existe:**

1. El sistema informa al responsable de recepción de que no existe un pedido con ese identificador.
2. El flujo de eventos vuelve al paso 1 para introducir otro identificador.

**4.a. Falta un dato obligatorio o alguno de los datos no es válido:**

1. El sistema indica los problemas detectados: código de lote vacío, cantidad no válida, ausencia del certificado o archivo adjunto que no es un PDF.
2. El flujo de eventos vuelve al paso 3 para corregir los datos o el archivo adjunto.

**5.a. Ya existe un lote registrado con el mismo proveedor y código de lote:**

1. El sistema informa de que el lote ya está registrado y muestra el identificador del registro existente.
2. El caso de uso finaliza sin crear una nueva recepción.

**6.a. La cantidad recibida difiere de la prevista en el pedido:**

1. El sistema muestra ambas cantidades y solicita confirmar expresamente la cantidad recibida o corregirla.
2. El responsable de recepción confirma que la cantidad introducida es correcta.
3. El sistema incorpora la discrepancia al resumen que se mostrará y al registro que se guardará si se confirma la recepción.
4. El flujo de eventos continúa en el paso 7.

**6.a.2.a. El responsable de recepción elige corregir la cantidad:**

1. El flujo de eventos vuelve al paso 3.

**\*.a. En cualquier momento antes de confirmar el registro, el responsable de recepción cancela la operación:**

1. El sistema descarta los datos de la operación sin guardar una nueva recepción.
2. El caso de uso finaliza.

**9.a. Se produce un error al guardar la recepción:**

1. El sistema garantiza que no quede una recepción guardada parcialmente.
2. El sistema informa de que el registro no se ha completado debido a un error técnico y sugiere intentarlo de nuevo más tarde.
3. El caso de uso finaliza.

### 5. Observaciones para interpretar el ejemplo

- **Los participantes del acta no son necesariamente actores del caso de uso.** El representante de calidad aporta necesidades durante la captura, pero no interviene en el registro de la recepción.
- **Una precondición se da por cumplida al comenzar.** El pedido existe o los datos son válidos no se establecen como precondiciones, porque el sistema los comprueba durante el flujo y se describen extensiones para los resultados negativos.
- **Una extensión puede volver al escenario principal.** Confirmar una cantidad distinta permite continuar y completar el registro; esa extensión no representa un fracaso del caso de uso.
- **Las extensiones señalan dónde cambia el flujo.** La etiqueta «6.a.2.a» se refiere al paso 2 de la extensión 6.a; el asterisco de «*.a» indica una situación que puede producirse en cualquier paso anterior a la confirmación.
- **La descripción mantiene el objetivo acordado.** El resultado es una recepción registrada y un lote pendiente de evaluación; la autorización para producción pertenece a otra funcionalidad.

### 

## Ejemplo 2. Administración pública: presentar una solicitud de rodaje

### 1. Contexto de la aplicación

Un ayuntamiento dispone de una aplicación para solicitar el uso de espacios municipales en rodajes. La persona solicitante selecciona un espacio, indica cuándo y para qué desea utilizarlo y aporta la documentación requerida.

El ejemplo se centra en presentar la solicitud y obtener un justificante. El personal municipal la revisará posteriormente y decidirá si autoriza el rodaje. Los acuerdos que siguen definen el funcionamiento de esta aplicación ficticia.

### 2. Acta de acuerdos con el cliente

| Campo | Valor |
| --- | --- |
| Naturaleza | Acta ficticia elaborada para este ejemplo docente. |
| Funcionalidad | Presentación de una solicitud de rodaje en un espacio municipal. |
| Requisito de usuario | UR-01 · La persona solicitante podrá presentar una solicitud para realizar un rodaje en un espacio municipal y obtener un justificante de presentación. |
| Finalidad | Concretar la información requerida, las comprobaciones previas y el resultado de la presentación. |

#### 2.1. Participantes

| Rol | Participación |
| --- | --- |
| Representante de las personas solicitantes | Necesidades de presentación y obtención de un justificante. |
| Responsable municipal de gestión de espacios | Condiciones para solicitar espacios y datos necesarios para la revisión posterior. |
| Analista | Registro y organización de los acuerdos. |

#### 2.2. Alcance acordado

- Cada solicitud se referirá a un único espacio municipal y a una franja horaria dentro de un único día.
- La persona solicitante debe disponer de una cuenta, haber iniciado sesión y tener su nombre e identificador personal registrados en su perfil. Esos datos identificarán a quien presenta la solicitud.
- Los espacios que pueden solicitarse estarán incluidos en un catálogo mantenido por el ayuntamiento.
- La aplicación utilizará su calendario de espacios para comprobar si la franja solicitada coincide con un periodo bloqueado o con una ocupación ya autorizada.
- Una solicitud pendiente de revisión no reservará el espacio. La disponibilidad comprobada al presentar la solicitud no garantiza que el rodaje vaya a autorizarse.

#### 2.3. Acuerdos confirmados

**Información de la solicitud**

- La aplicación mostrará los datos identificativos de la persona solicitante, el catálogo de espacios y la documentación que debe aportar.
- La persona solicitante elegirá un espacio e indicará la fecha, la hora de inicio, la hora de fin y una descripción del rodaje.
- Todos esos datos serán obligatorios. La fecha deberá ser posterior al día de presentación y la hora de fin deberá ser posterior a la de inicio.
- Para este ejemplo se exigirán dos documentos en PDF: una memoria del rodaje y un plano de la zona que se pretende ocupar.
- La aplicación comprobará la presencia y el formato de los documentos. Su contenido será revisado posteriormente por el personal municipal.
- Si los datos o los documentos no cumplen estas condiciones, la aplicación indicará los problemas y permitirá corregirlos antes de continuar.

**Disponibilidad del espacio y solicitudes duplicadas**

- La aplicación comprobará que la franja solicitada no se solape con un periodo bloqueado ni con una ocupación autorizada del espacio.
- Si el espacio no está disponible, la aplicación informará del conflicto y permitirá modificar el espacio, la fecha o el horario.
- Se considerará duplicada una solicitud de la misma persona para el mismo espacio, fecha y horas de inicio y fin, cuando ya exista otra en estado «Pendiente de revisión» o «Autorizada».
- Si se detecta una solicitud duplicada, la aplicación informará de ello, mostrará el identificador de la solicitud existente y finalizará la operación sin presentar otra solicitud.

**Confirmación y presentación**

- Antes de presentar la solicitud, la aplicación mostrará un resumen con la identidad de la persona solicitante, el espacio, la fecha, el horario, la descripción y los nombres de los documentos adjuntos.
- El resumen recordará que la presentación no equivale a una autorización ni reserva el espacio.
- La persona solicitante podrá volver a corregir la información o confirmar la presentación.
- Tras la confirmación, la aplicación guardará la solicitud y los documentos, asignará un identificador único y registrará la fecha y hora de presentación.
- La solicitud quedará en el estado «Pendiente de revisión».
- La persona solicitante podrá cancelar en cualquier momento anterior a la confirmación. No se conservará una solicitud nueva ni un borrador de la operación cancelada.
- Si se produce un error al guardar, la aplicación indicará que la solicitud no se ha presentado y sugerirá intentarlo más tarde. No quedará una solicitud guardada parcialmente.

**Justificante y confirmación del resultado**

- Una vez registrada la solicitud, la aplicación generará un justificante en PDF con el identificador, la fecha y hora de presentación, la identidad de la persona solicitante, el espacio, la fecha y horario solicitados y los nombres de los documentos aportados.
- La aplicación mostrará un mensaje de presentación correcta con el identificador y el estado de la solicitud, y ofrecerá descargar el justificante.
- La persona solicitante podrá solicitar la descarga y la aplicación le proporcionará el archivo PDF.
- La persona solicitante también podrá finalizar sin descargarlo en ese momento. El justificante generado quedará disponible para obtenerlo posteriormente mediante la consulta de solicitudes.
- Si falla la generación del justificante, la solicitud seguirá presentada. La aplicación mostrará su identificador, fecha y hora de presentación y estado, e informará de que el justificante no está disponible en ese momento.
- En ese caso, indicará que se podrá obtener el justificante más tarde mediante la funcionalidad de consulta de solicitudes. La persona no deberá repetir la presentación para obtenerlo.

#### 2.4. Límites del alcance

| Asunto | Acuerdo |
| --- | --- |
| Registro de cuentas y modificación del perfil | Se realiza mediante otras funcionalidades. |
| Solicitudes para varios espacios o varios días | Quedan fuera del ejemplo. |
| Evaluación del contenido de los documentos | Se realiza durante la revisión municipal posterior. |
| Autorización del rodaje y reserva del espacio | Corresponden a la resolución posterior de la solicitud. |
| Consulta de solicitudes y obtención posterior de justificantes | Constituyen otra funcionalidad, que permite obtener el justificante si no se descargó o no pudo generarse durante la presentación. |
| Conservación de borradores | Queda fuera del ejemplo. |

### 3. Requisitos derivados y relación con el caso de uso

#### 3.1. Requisito de usuario

| ID | Requisito de usuario |
| --- | --- |
| UR-01 | La persona solicitante podrá presentar una solicitud para realizar un rodaje en un espacio municipal y obtener un justificante de presentación. |

#### 3.2. Requisitos funcionales

Todos los requisitos funcionales de esta tabla se derivan de los acuerdos del acta y están asociados a **UR-01**.

| ID | Requisito funcional |
| --- | --- |
| FR-001 | El sistema debe mostrar la identidad de la persona solicitante, el catálogo de espacios municipales y la documentación requerida para presentar una solicitud de rodaje. |
| FR-002 | El sistema debe permitir seleccionar un espacio e introducir la fecha, las horas de inicio y fin y la descripción del rodaje. |
| FR-003 | El sistema debe permitir adjuntar una memoria del rodaje y un plano de la zona que se pretende ocupar, ambos en formato PDF. |
| FR-004 | El sistema debe comprobar que se hayan aportado todos los datos y documentos obligatorios, que la fecha sea posterior al día de presentación, que la hora de fin sea posterior a la de inicio y que los documentos estén en formato PDF, e indicar los problemas que deban corregirse. |
| FR-005 | El sistema debe comprobar en el calendario del espacio que la franja solicitada no se solape con un periodo bloqueado ni con una ocupación autorizada, e informar del conflicto cuando exista. |
| FR-006 | El sistema debe impedir la presentación de una solicitud cuando ya exista otra de la misma persona para el mismo espacio, fecha y horas de inicio y fin en estado «Pendiente de revisión» o «Autorizada», e informar del identificador de la solicitud existente. |
| FR-007 | El sistema debe mostrar un resumen de la solicitud, advertir de que su presentación no equivale a una autorización ni reserva el espacio y permitir corregir la información o confirmar la presentación. |
| FR-008 | El sistema debe guardar la solicitud confirmada y sus documentos, asociándolos a la persona solicitante y dejando la solicitud en el estado «Pendiente de revisión». |
| FR-009 | El sistema debe asignar un identificador único a la solicitud y registrar la fecha y hora de su presentación. |
| FR-010 | El sistema debe generar un justificante de presentación en PDF con el identificador, la fecha y hora de presentación, la identidad de la persona solicitante, el espacio, la fecha y horario solicitados y los nombres de los documentos aportados. |
| FR-011 | El sistema debe mostrar una confirmación de presentación correcta con el identificador y el estado de la solicitud, y permitir descargar el justificante generado o finalizar sin descargarlo en ese momento. |
| FR-012 | El sistema debe permitir cancelar antes de confirmar la presentación, sin conservar una solicitud nueva ni un borrador de la operación. |
| FR-013 | El sistema debe notificar que la solicitud no se ha presentado cuando se produzca un error al guardar, sugerir un nuevo intento posterior y evitar que quede una solicitud guardada parcialmente. |
| FR-014 | El sistema debe conservar la solicitud presentada si falla la generación del justificante, mostrar su identificador, fecha y hora de presentación y estado, e informar de que el justificante podrá obtenerse posteriormente mediante la consulta de solicitudes. |

#### 3.3. Relación entre el caso de uso y los requisitos

| ID | Caso de uso | UR asociados | FR asociados |
| --- | --- | --- | --- |
| UC-01 | Presentar una solicitud de rodaje | UR-01 | FR-001, FR-002, FR-003, FR-004, FR-005, FR-006, FR-007, FR-008, FR-009, FR-010, FR-011, FR-012, FR-013, FR-014 |

### 4. Descripción detallada de UC-01 · Presentar una solicitud de rodaje

#### Actor principal

Persona solicitante.

#### Actores de apoyo

Ninguno. El catálogo, el calendario y el registro de solicitudes forman parte del sistema descrito. El personal municipal revisará la solicitud después de su presentación y no interviene durante este caso de uso.

#### Precondiciones

- La persona solicitante dispone de una cuenta y ha iniciado sesión.
- Su perfil contiene el nombre y el identificador personal necesarios para identificarla en la solicitud.

La validez de la información aportada, la disponibilidad del espacio y la ausencia de duplicidades se comprueban durante el caso de uso.

#### Postcondiciones

**Tras completar el escenario principal con éxito:**

- La solicitud y sus documentos quedan registrados y asociados a la persona solicitante.
- La solicitud dispone de un identificador único y de una fecha y hora de presentación.
- Su estado es «Pendiente de revisión».
- El justificante en PDF queda generado y se proporciona a la persona solicitante mediante la descarga.
- Se muestra una confirmación de presentación correcta.
- El espacio no queda reservado y el rodaje no queda autorizado por el hecho de presentar la solicitud.

**En las situaciones alternativas y de excepción:**

- Si se cancela antes de confirmar o se produce un error al guardar, no se crea una nueva solicitud ni queda un registro parcial o un borrador de ella.
- Si se detecta una duplicidad, la solicitud existente se mantiene sin cambios y se informa de su identificador.
- Si falla la generación del justificante después del registro, la solicitud permanece presentada y en estado «Pendiente de revisión», con su identificador, documentos y fecha y hora de presentación. Se informa a la persona solicitante de cómo obtener el justificante posteriormente.
- Si la persona solicitante finaliza sin descargar el justificante generado, la solicitud permanece presentada y el justificante queda disponible mediante la consulta de solicitudes.

#### Escenario principal de éxito

1. La persona solicitante inicia la presentación de una solicitud de rodaje.
2. El sistema muestra su identidad, los espacios que pueden solicitarse, los datos que debe completar y los dos documentos PDF requeridos.
3. La persona solicitante selecciona un espacio, introduce la fecha, las horas de inicio y fin y la descripción del rodaje, y adjunta la memoria y el plano.
4. El sistema comprueba que los datos y documentos obligatorios estén completos, que la fecha sea posterior al día de presentación, que la hora de fin sea posterior a la de inicio y que los documentos estén en formato PDF.
5. El sistema comprueba que no exista una solicitud duplicada de la misma persona para ese espacio, fecha y horario en estado «Pendiente de revisión» o «Autorizada».
6. El sistema comprueba que la franja solicitada no se solape con un periodo bloqueado ni con una ocupación autorizada del espacio.
7. El sistema muestra el resumen de la solicitud, recuerda que la presentación no autoriza el rodaje ni reserva el espacio y solicita confirmar la presentación.
8. La persona solicitante confirma la presentación.
9. El sistema guarda la solicitud y sus documentos, asigna un identificador único, registra la fecha y hora de presentación y establece el estado «Pendiente de revisión».
10. El sistema genera el justificante de presentación en PDF con los datos acordados en el acta.
11. El sistema muestra una confirmación de presentación correcta con el identificador y el estado de la solicitud y ofrece descargar el justificante.
12. La persona solicitante solicita la descarga del justificante.
13. El sistema proporciona el archivo PDF a la persona solicitante.

#### Extensiones

**4.a. Falta información obligatoria o alguno de los datos o documentos no cumple las condiciones:**

1. El sistema indica los problemas detectados: campos vacíos, fecha u horario no válidos, ausencia de un documento obligatorio o archivo que no es un PDF.
2. El flujo de eventos vuelve al paso 3 para corregir la solicitud.

**5.a. Ya existe una solicitud duplicada:**

1. El sistema informa de la duplicidad y muestra el identificador de la solicitud existente.
2. El caso de uso finaliza sin presentar una nueva solicitud.

**6.a. El espacio no está disponible en la franja solicitada:**

1. El sistema informa de que el horario solicitado coincide con un periodo bloqueado o con una ocupación autorizada.
2. El flujo de eventos vuelve al paso 3 para modificar el espacio, la fecha o el horario.

**7.a. La persona solicitante elige corregir la información del resumen:**

1. El flujo de eventos vuelve al paso 3.

**\*.a. En cualquier momento antes de confirmar la presentación, la persona solicitante cancela la operación:**

1. El sistema descarta los datos de la operación sin conservar una solicitud nueva ni un borrador.
2. El caso de uso finaliza.

**9.a. Se produce un error al guardar la solicitud:**

1. El sistema garantiza que no quede una solicitud guardada parcialmente.
2. El sistema informa de que la solicitud no se ha presentado debido a un error técnico y sugiere intentarlo de nuevo más tarde.
3. El caso de uso finaliza.

**10.a. Se produce un error al generar el justificante:**

1. El sistema conserva la solicitud ya presentada y sus documentos.
2. El sistema informa de que la presentación se ha completado, muestra el identificador, la fecha y hora de presentación y el estado «Pendiente de revisión», e indica que el justificante no está disponible en ese momento.
3. El sistema indica que el justificante podrá obtenerse posteriormente desde la consulta de solicitudes, sin repetir la presentación.
4. El caso de uso finaliza con la solicitud presentada y el justificante pendiente de obtención.

**11.a. La persona solicitante decide finalizar sin descargar el justificante en ese momento:**

1. El sistema mantiene la solicitud presentada y el justificante generado, que queda disponible mediante la consulta de solicitudes.
2. El caso de uso finaliza.

### 5. Observaciones para interpretar el ejemplo

- **El resultado se expresa desde el objetivo de la persona solicitante.** Se presenta una solicitud y se obtiene un justificante; la resolución municipal posterior pertenece a otro caso de uso.
- **Las comprobaciones automáticas tienen un alcance concreto.** El sistema comprueba campos, fechas, formatos y conflictos de calendario; la revisión del contenido de los documentos corresponde al personal municipal.
- **Volver a corregir implica repetir las comprobaciones.** Las extensiones que vuelven al paso 3 pasan de nuevo por la validación, la disponibilidad y la detección de duplicidades.
- **Un error posterior al registro no elimina necesariamente lo ya conseguido.** En la extensión 10.a, la solicitud sigue presentada aunque el justificante no pueda generarse. Por eso sus postcondiciones son distintas de las del error al guardar del paso 9.
- **Un componente interno no se convierte en actor de apoyo.** El calendario pertenece a la aplicación en este ejemplo; no se ha definido un servicio externo que intervenga en el caso de uso.

### 

## Ejemplo 3. Ámbito policial: registrar la transferencia de una evidencia

### 1. Contexto de la aplicación

Una unidad policial utiliza una aplicación para registrar quién tiene la custodia de cada evidencia y conservar el historial de sus transferencias. Cada evidencia está identificada mediante un código que también figura en su etiqueta física.

El ejemplo se centra en registrar una transferencia entre dos personas. Se denomina **custodio de origen** a quien inicia la operación y **custodio destinatario** a quien debe comprobar la evidencia y aceptar la transferencia. Los acuerdos siguientes definen el funcionamiento de esta aplicación ficticia.

### 2. Acta de acuerdos con el cliente

| Campo | Valor |
| --- | --- |
| Naturaleza | Acta ficticia elaborada para este ejemplo docente. |
| Funcionalidad | Registro de la transferencia de la custodia de una evidencia entre dos personas. |
| Requisito de usuario | UR-01 · La persona responsable de la custodia podrá transferir una evidencia a otra persona autorizada, dejando constancia de la entrega y de su aceptación. |
| Finalidad | Concretar la identificación de la evidencia, la intervención de ambas personas y las condiciones para actualizar la custodia registrada. |

#### 2.1. Participantes

| Rol | Participación |
| --- | --- |
| Representante de los custodios de origen | Necesidades de identificación de evidencias e inicio de transferencias. |
| Representante de los custodios destinatarios | Comprobaciones previas y aceptación o rechazo de una transferencia. |
| Responsable de gestión de evidencias | Información que debe conservarse en el historial y condiciones para cambiar la custodia registrada. |
| Analista | Registro y organización de los acuerdos. |

#### 2.2. Alcance acordado

- Cada operación se referirá a una única evidencia y a un único custodio destinatario.
- Las evidencias y las cuentas de las personas ya estarán registradas en la aplicación.
- Ambas personas participarán durante la misma operación, con sus propias sesiones iniciadas. El ejemplo no incluye propuestas pendientes de respuesta durante varios días.
- El custodio de origen deberá tener autorización para iniciar transferencias. Además, la aplicación comprobará que figure como custodio actual de la evidencia concreta.
- El registro de la transferencia requerirá la aceptación del custodio destinatario desde su propia sesión. El custodio de origen no podrá aceptar en su nombre.
- La operación describe el registro informático de la transferencia. Los procedimientos de manipulación, transporte y conservación física de las evidencias quedan fuera de su alcance.

#### 2.3. Acuerdos confirmados

**Identificación de la evidencia y de su custodio actual**

- El custodio de origen indicará el código de la evidencia que desea transferir.
- La aplicación mostrará su código, descripción, expediente asociado y custodio actual.
- Si no existe una evidencia con ese código, la aplicación lo notificará y permitirá introducir otro.
- La aplicación comprobará que quien inicia la operación figure como custodio actual de esa evidencia.
- Si no figura como custodio actual, la aplicación informará de ello y finalizará la operación sin registrar una transferencia.

**Destinatario y motivo**

- El custodio de origen indicará el identificador de la persona destinataria y el motivo de la transferencia.
- La persona destinataria deberá disponer de una cuenta activa, tener autorización para recibir evidencias y ser distinta del custodio de origen.
- El motivo será obligatorio y no podrá estar vacío.
- Si el identificador no corresponde a una persona que cumpla esas condiciones o falta el motivo, la aplicación indicará el problema y permitirá corregirlo.
- La aplicación mostrará al custodio de origen un resumen con la evidencia, las identidades de origen y destino y el motivo.
- El custodio de origen podrá corregir el destinatario o el motivo antes de confirmar la propuesta.

**Comprobación y aceptación por el destinatario**

- Tras la confirmación del custodio de origen, la aplicación mostrará la propuesta al custodio destinatario en su propia sesión.
- La propuesta incluirá el código y descripción de la evidencia, el expediente asociado, la identidad del custodio de origen y el motivo de la transferencia.
- El custodio destinatario comprobará la etiqueta física de la evidencia e introducirá en la aplicación el código que figura en ella.
- La aplicación comparará el código introducido con el de la evidencia seleccionada para la transferencia.
- Si no coinciden, la aplicación informará de la discrepancia a ambas personas y finalizará la operación sin registrar la transferencia ni cambiar la custodia. La aclaración de la discrepancia se realizará fuera de esta operación.
- Si los códigos coinciden, la aplicación solicitará al custodio destinatario que acepte o rechace la transferencia.
- Si el destinatario rechaza, la aplicación informará a ambas personas y finalizará la operación sin registrar la transferencia ni cambiar la custodia.

**Registro y resultado de la transferencia**

- La confirmación del custodio de origen solo permitirá continuar con la propuesta. La transferencia se registrará únicamente tras la aceptación del custodio destinatario.
- Al registrar la transferencia, la aplicación asignará un identificador único y añadirá al historial de la evidencia su código, las identidades de ambos custodios, el motivo y la fecha y hora de registro de la aceptación.
- La aplicación conservará los registros anteriores del historial sin modificarlos.
- En la misma operación de guardado, la aplicación actualizará el custodio actual de la evidencia, que pasará a ser el destinatario.
- La aplicación mostrará a ambas personas una confirmación con el identificador de la transferencia, el código de la evidencia y la identidad del nuevo custodio.
- El custodio de origen podrá cancelar en cualquier momento anterior a la confirmación de la propuesta. En ese caso, no se registrará una transferencia ni cambiará la custodia.
- Si se produce un error al guardar, no se añadirá una transferencia al historial ni se cambiará el custodio registrado. La aplicación informará a ambas personas de que el registro no se ha completado y sugerirá intentarlo más tarde.
- Una operación rechazada, cancelada o interrumpida por una discrepancia no dejará una propuesta pendiente ni una transferencia en el historial.

#### 2.4. Límites del alcance

| Asunto | Acuerdo |
| --- | --- |
| Alta de evidencias y gestión de cuentas y autorizaciones | Se realiza mediante otras funcionalidades. |
| Transferencias de varias evidencias a la vez | Quedan fuera del ejemplo. |
| Manipulación, transporte y conservación física | Se rigen por procedimientos externos a esta operación informática. |
| Aclaración de discrepancias en la identificación | Se realiza fuera de este caso de uso; la operación afectada finaliza sin cambiar la custodia registrada. |
| Propuestas pendientes de aceptación posterior | Quedan fuera del ejemplo; ambas personas intervienen durante la misma operación. |
| Historial de operaciones fallidas o rechazadas | Queda fuera del ejemplo; el historial descrito conserva las transferencias completadas. |

### 3. Requisitos derivados y relación con el caso de uso

#### 3.1. Requisito de usuario

| ID | Requisito de usuario |
| --- | --- |
| UR-01 | La persona responsable de la custodia podrá transferir una evidencia a otra persona autorizada, dejando constancia de la entrega y de su aceptación. |

#### 3.2. Requisitos funcionales

Todos los requisitos funcionales de esta tabla se derivan de los acuerdos del acta y están asociados a **UR-01**.

| ID | Requisito funcional |
| --- | --- |
| FR-001 | El sistema debe permitir localizar una evidencia por su código y mostrar su descripción, expediente asociado y custodio actual, o informar de que no existe una evidencia con ese código. |
| FR-002 | El sistema debe comprobar que quien inicia la transferencia figure como custodio actual de la evidencia e informar y finalizar la operación cuando no se cumpla esa condición. |
| FR-003 | El sistema debe permitir introducir el identificador de la persona destinataria y el motivo de la transferencia. |
| FR-004 | El sistema debe comprobar que el destinatario tenga una cuenta activa y autorización para recibir evidencias, que sea distinto del custodio de origen y que el motivo no esté vacío, e indicar los problemas que deban corregirse. |
| FR-005 | El sistema debe mostrar al custodio de origen un resumen de la evidencia, las identidades de origen y destino y el motivo, permitiendo corregir el destinatario o el motivo o confirmar la propuesta. |
| FR-006 | El sistema debe mostrar la propuesta confirmada al custodio destinatario en su propia sesión y solicitar que introduzca el código de la etiqueta física de la evidencia. |
| FR-007 | El sistema debe comparar el código introducido por el destinatario con el de la evidencia seleccionada y, si no coinciden, informar a ambos custodios y finalizar sin registrar la transferencia ni cambiar la custodia. |
| FR-008 | El sistema debe permitir que el custodio destinatario acepte o rechace la transferencia cuando los códigos coincidan y, si la rechaza, informar a ambos custodios y finalizar sin registrar la transferencia ni cambiar la custodia. |
| FR-009 | El sistema debe añadir al historial, tras la aceptación del destinatario, una transferencia con el código de la evidencia, las identidades de ambos custodios, el motivo y la fecha y hora de registro de la aceptación, conservando los registros anteriores sin modificarlos. |
| FR-010 | El sistema debe actualizar el custodio actual de la evidencia al registrar la transferencia aceptada, de modo que pase a ser el custodio destinatario. |
| FR-011 | El sistema debe asignar un identificador único a cada transferencia registrada. |
| FR-012 | El sistema debe mostrar a ambos custodios una confirmación con el identificador de la transferencia, el código de la evidencia y la identidad del nuevo custodio. |
| FR-013 | El sistema debe permitir al custodio de origen cancelar antes de confirmar la propuesta, sin registrar una transferencia ni cambiar la custodia. |
| FR-014 | El sistema debe evitar que se añada una transferencia o cambie la custodia registrada si se produce un error al guardar, e informar a ambos custodios de que el registro no se ha completado y de que pueden intentarlo más tarde. |

#### 3.3. Relación entre el caso de uso y los requisitos

| ID | Caso de uso | UR asociados | FR asociados |
| --- | --- | --- | --- |
| UC-01 | Registrar la transferencia de una evidencia | UR-01 | FR-001, FR-002, FR-003, FR-004, FR-005, FR-006, FR-007, FR-008, FR-009, FR-010, FR-011, FR-012, FR-013, FR-014 |

### 4. Descripción detallada de UC-01 · Registrar la transferencia de una evidencia

#### Actor principal

Custodio de origen: persona que inicia el registro de la transferencia.

#### Actores de apoyo

Custodio destinatario: persona que comprueba la identificación de la evidencia y acepta o rechaza la transferencia desde su propia sesión.

#### Precondiciones

- El custodio de origen ha iniciado sesión y tiene autorización para iniciar transferencias.
- El custodio destinatario dispone de una sesión iniciada para intervenir durante la misma operación.

La existencia de la evidencia, la relación entre el custodio de origen y la evidencia, las condiciones del destinatario seleccionado y la coincidencia del código de la etiqueta se comprueban durante el caso de uso.

#### Postcondiciones

**Tras completar el caso de uso con éxito:**

- La transferencia queda registrada con un identificador único.
- El historial de la evidencia incluye el código de la evidencia, las identidades de ambos custodios, el motivo y la fecha y hora de registro de la aceptación del destinatario.
- Los registros anteriores del historial se conservan sin cambios.
- El custodio actual registrado para la evidencia pasa a ser el custodio destinatario.
- Ambos custodios reciben una confirmación en pantalla con el identificador de la transferencia, el código de la evidencia y la identidad del nuevo custodio.

**Si el caso de uso finaliza sin completar la transferencia:**

- No se añade una transferencia al historial ni cambia el custodio registrado para la evidencia.
- No queda una propuesta pendiente de aceptación.
- Si existe una discrepancia en el código, un rechazo o un error al guardar, ambos custodios reciben la información correspondiente.

#### Escenario principal de éxito

1. El custodio de origen inicia el registro de una transferencia e introduce el código de la evidencia.
2. El sistema localiza la evidencia y muestra su código, descripción, expediente asociado y custodio actual.
3. El sistema comprueba que el custodio de origen figure como custodio actual de esa evidencia.
4. El custodio de origen introduce el identificador de la persona destinataria y el motivo de la transferencia.
5. El sistema comprueba que el destinatario tenga una cuenta activa y autorización para recibir evidencias, que sea distinto del custodio de origen y que el motivo no esté vacío.
6. El sistema muestra al custodio de origen el resumen de la transferencia y solicita confirmar la propuesta.
7. El custodio de origen confirma la propuesta.
8. El sistema muestra la propuesta al custodio destinatario en su propia sesión y solicita el código de la etiqueta física de la evidencia.
9. El custodio destinatario comprueba la etiqueta física de la evidencia e introduce el código que figura en ella.
10. El sistema comprueba que el código coincida con el de la evidencia seleccionada y solicita aceptar o rechazar la transferencia.
11. El custodio destinatario acepta la transferencia.
12. El sistema registra la transferencia con un identificador único, añade al historial los datos acordados y actualiza el custodio actual de la evidencia, que pasa a ser el destinatario.
13. El sistema muestra a ambos custodios una confirmación con el identificador de la transferencia, el código de la evidencia y la identidad del nuevo custodio.

#### Extensiones

**2.a. No existe una evidencia con el código indicado:**

1. El sistema informa al custodio de origen de que no existe una evidencia con ese código.
2. El flujo de eventos vuelve al paso 1 para introducir otro código.

**3.a. El custodio de origen no figura como custodio actual de la evidencia:**

1. El sistema informa de que quien inicia la operación no tiene la custodia registrada de esa evidencia.
2. El caso de uso finaliza sin registrar una transferencia.

**5.a. El destinatario no cumple las condiciones o el motivo está vacío:**

1. El sistema indica los problemas detectados: identificador inexistente, cuenta inactiva, ausencia de autorización para recibir evidencias, destinatario igual al custodio de origen o motivo vacío.
2. El flujo de eventos vuelve al paso 4 para corregir el destinatario o el motivo.

**6.a. El custodio de origen elige corregir el destinatario o el motivo:**

1. El flujo de eventos vuelve al paso 4.

**\*.a. En cualquier momento antes de confirmar la propuesta, el custodio de origen cancela la operación:**

1. El sistema descarta los datos de la operación sin registrar una transferencia ni cambiar la custodia.
2. El caso de uso finaliza.

**10.a. El código introducido por el destinatario no coincide con el de la evidencia seleccionada:**

1. El sistema informa a ambos custodios de la discrepancia entre los códigos.
2. El caso de uso finaliza sin registrar la transferencia ni cambiar la custodia.

**11.a. El custodio destinatario rechaza la transferencia:**

1. El sistema informa a ambos custodios de que la transferencia ha sido rechazada.
2. El caso de uso finaliza sin registrar la transferencia ni cambiar la custodia.

**12.a. Se produce un error al guardar la transferencia:**

1. El sistema mantiene el historial y el custodio registrado sin cambios, evitando que quede una transferencia guardada parcialmente.
2. El sistema informa a ambos custodios de que la transferencia no ha podido registrarse debido a un error técnico y sugiere intentarlo de nuevo más tarde.
3. El caso de uso finaliza sin dejar una propuesta pendiente de aceptación.

### 5. Observaciones para interpretar el ejemplo

- **Un caso de uso puede requerir la intervención de varias personas.** El custodio de origen lo inicia y el custodio destinatario aporta una comprobación y una decisión necesarias para completar el objetivo.
- **El actor de apoyo también puede ser una persona.** No se limita a servicios o sistemas externos; aquí el destinatario interactúa directamente con la aplicación.
- **Las dos confirmaciones tienen efectos distintos.** La confirmación del origen permite mostrar la propuesta; la aceptación del destinatario permite registrar la transferencia y cambiar la custodia registrada.
- **Una condición comprobada en el flujo no se presupone al comenzar.** Tener autorización para iniciar transferencias no implica tener la custodia de cualquier evidencia; el sistema debe comprobar la relación con la evidencia concreta.
- **El registro histórico y el estado actual deben ser coherentes.** Una transferencia completada añade una entrada al historial y actualiza el custodio. Si falla el guardado, ninguno de esos cambios queda aplicado.

## Ejemplo 4. Redes sociales: publicar un álbum colaborativo

### 1. Contexto de la aplicación

Una red social permite publicar álbumes de fotografías con dos personas como autoras. La persona creadora prepara el álbum y elige su audiencia; la persona invitada debe revisar el contenido y aceptar aparecer como coautora antes de que se publique.

La invitación puede responderse en otro momento. Durante la espera, el álbum se conserva sin publicar. Los acuerdos siguientes definen el funcionamiento de esta aplicación ficticia.

### 2. Acta de acuerdos con el cliente

| Campo | Valor |
| --- | --- |
| Naturaleza | Acta ficticia elaborada para este ejemplo docente. |
| Funcionalidad | Publicación de un álbum de fotografías con una persona invitada como coautora. |
| Requisito de usuario | UR-01 · Una persona usuaria podrá publicar un álbum con otra persona como coautora, previa aceptación de esta, y elegir la audiencia que podrá verlo. |
| Finalidad | Concretar la preparación del álbum, la aceptación de la colaboración y los resultados de la publicación, la espera y el rechazo. |

#### 2.1. Participantes

| Rol | Participación |
| --- | --- |
| Representante de las personas creadoras | Preparación del álbum, elección de audiencia e invitación a una persona coautora. |
| Representante de las personas invitadas | Revisión del contenido y decisión sobre la participación como coautora. |
| Responsable de producto de la red social | Estados del álbum y condiciones para hacerlo visible a la audiencia. |
| Analista | Registro y organización de los acuerdos. |

#### 2.2. Alcance acordado

- Cada álbum colaborativo tendrá una persona creadora y una única persona invitada como coautora.
- La persona creadora deberá disponer de una cuenta, haber iniciado sesión y tener habilitada la publicación de álbumes.
- La persona invitada deberá disponer de una cuenta activa y ser distinta de la persona creadora.
- La persona invitada accederá a la invitación y responderá desde su propia sesión. No se requiere que tenga una sesión iniciada cuando se crea la invitación.
- Las invitaciones y los avisos se gestionarán dentro de la red social. El ejemplo no incluye correos electrónicos ni notificaciones mediante servicios externos.
- La confirmación de la persona creadora autorizará la publicación automática del álbum si la persona invitada acepta. No se solicitará una segunda confirmación a la creadora después de esa aceptación.

#### 2.3. Acuerdos confirmados

**Preparación del álbum y elección de audiencia**

- La persona creadora indicará un título, aportará al menos una fotografía e introducirá el identificador de la persona que desea invitar.
- Las fotografías deberán ser archivos JPEG o PNG que la aplicación pueda procesar. El título no podrá estar vacío.
- La persona creadora elegirá una de dos audiencias: «Público» o «Seguidores de la persona creadora».
- La audiencia «Público» permitirá ver el álbum a cualquier persona; la otra opción limitará su consulta a los seguidores de la creadora. Ambas autoras podrán acceder al álbum.
- La aceptación de la coautoría no ampliará la audiencia a los seguidores de la persona invitada.
- La aplicación comprobará los datos, las fotografías y las condiciones de la cuenta invitada antes de continuar.
- Si falta información, alguna fotografía no puede procesarse o la cuenta invitada no cumple las condiciones, la aplicación indicará el problema y permitirá corregirlo.

**Confirmación de la invitación**

- La aplicación mostrará a la persona creadora una vista previa con el título, las fotografías, la identidad de la persona invitada y la audiencia elegida.
- La vista previa indicará que, si la persona invitada acepta, el álbum se publicará automáticamente con ambas personas como autoras y para esa audiencia.
- La persona creadora podrá corregir la información o confirmar el envío de la invitación.
- Tras la confirmación, la aplicación guardará el álbum con un identificador único y el estado «Pendiente de aceptación», y creará la invitación como una notificación interna para la persona invitada.
- La aplicación mostrará a la persona creadora el identificador y el estado del álbum.
- Mientras esté pendiente, el álbum solo podrá ser consultado por la persona creadora y la persona invitada. La audiencia seleccionada todavía no podrá verlo.
- El título, las fotografías, la persona invitada y la audiencia quedarán fijados durante esta operación, para que la aceptación se refiera al contenido y a la audiencia que se han mostrado.
- La persona creadora podrá cancelar antes de confirmar el envío de la invitación. En ese caso, no se conservará un álbum nuevo ni se creará una invitación.

**Revisión y respuesta de la persona invitada**

- Al abrir la invitación desde su propia sesión, la persona invitada verá el álbum completo, la identidad de la creadora y la audiencia elegida.
- La aplicación indicará que aceptar supone autorizar la publicación de ese álbum para esa audiencia y aparecer como coautora.
- La persona invitada podrá aceptar o rechazar. La creadora no podrá responder en su nombre.
- Si no responde en ese momento, el álbum y la invitación se conservarán pendientes. La persona creadora podrá cerrar su sesión y la persona invitada podrá responder posteriormente.
- Si la persona invitada rechaza, la aplicación dejará el álbum en el estado «Colaboración rechazada», lo mantendrá sin publicar y lo dejará accesible únicamente para la creadora. La aplicación confirmará el rechazo a la persona invitada y avisará a la creadora mediante una notificación interna.

**Publicación y tratamiento de errores**

- Tras la aceptación, la aplicación registrará esa decisión y publicará el álbum para la audiencia acordada, mostrando a ambas personas como autoras.
- El álbum pasará al estado «Publicado». La publicación no modificará el título, las fotografías ni la audiencia revisados por la persona invitada.
- La aplicación mostrará a la persona invitada una confirmación con acceso al álbum y generará una notificación interna de publicación para la creadora, que podrá consultarla cuando acceda a su cuenta.
- Si falla el guardado del álbum y de la invitación inicial, no quedará ninguno de los dos registrado parcialmente. La aplicación informará a la creadora y sugerirá intentarlo más tarde.
- Si falla el registro de la aceptación o la publicación, la aplicación no aplicará ninguno de esos dos cambios: conservará el álbum y la invitación en estado pendiente, sin hacerlos visibles a la audiencia seleccionada.
- En ese caso, la aplicación informará a la persona invitada y avisará a la creadora mediante una notificación interna. La invitada podrá abrir de nuevo la misma invitación y repetir la aceptación más tarde, sin que la creadora tenga que preparar otro álbum.

#### 2.4. Límites del alcance

| Asunto | Acuerdo |
| --- | --- |
| Registro de cuentas, inicio de sesión y gestión de seguidores | Se realiza mediante otras funcionalidades. |
| Álbumes con más de una persona invitada | Quedan fuera del ejemplo. |
| Cambio de contenido o audiencia tras enviar la invitación | Queda fuera de esta operación; requeriría gestionar una nueva propuesta y su aceptación. |
| Retirada de invitaciones, caducidad automática y recordatorios | Quedan fuera del ejemplo; una invitación sin respuesta permanece pendiente. |
| Edición o eliminación de álbumes publicados | Se realiza mediante otras funcionalidades. |
| Reutilización de un álbum cuya colaboración fue rechazada | Queda fuera de este caso de uso. |

### 3. Requisitos derivados y relación con el caso de uso

#### 3.1. Requisito de usuario

| ID | Requisito de usuario |
| --- | --- |
| UR-01 | Una persona usuaria podrá publicar un álbum con otra persona como coautora, previa aceptación de esta, y elegir la audiencia que podrá verlo. |

#### 3.2. Requisitos funcionales

Todos los requisitos funcionales de esta tabla se derivan de los acuerdos del acta y están asociados a **UR-01**.

| ID | Requisito funcional |
| --- | --- |
| FR-001 | El sistema debe permitir introducir el título del álbum, aportar las fotografías, indicar la persona invitada y seleccionar la audiencia «Público» o «Seguidores de la persona creadora». |
| FR-002 | El sistema debe comprobar que el título no esté vacío, que se haya aportado al menos una fotografía, que todas las fotografías sean archivos JPEG o PNG que pueda procesar y que se haya elegido una audiencia válida, e indicar los problemas que deban corregirse. |
| FR-003 | El sistema debe comprobar que el identificador de la persona invitada corresponda a una cuenta activa distinta de la creadora, e informar cuando no se cumplan esas condiciones. |
| FR-004 | El sistema debe mostrar a la creadora una vista previa del álbum, la persona invitada y la audiencia, explicar que la aceptación permitirá publicarlo automáticamente y permitir corregir la información o confirmar la invitación. |
| FR-005 | El sistema debe guardar el álbum confirmado con un identificador único y el estado «Pendiente de aceptación», crear su invitación interna y mostrar el identificador y el estado a la creadora, manteniendo el álbum accesible solo para la creadora y la persona invitada. |
| FR-006 | El sistema debe permitir a la persona invitada abrir la invitación desde su propia sesión y consultar el álbum completo, la identidad de la creadora y la audiencia elegida. |
| FR-007 | El sistema debe permitir a la persona invitada aceptar o rechazar la colaboración, indicando que la aceptación autoriza la publicación del álbum para la audiencia mostrada y su identificación como coautora. |
| FR-008 | El sistema debe conservar el álbum y la invitación pendientes cuando la persona invitada no responda, permitiendo que acceda a la misma invitación y responda posteriormente. |
| FR-009 | El sistema debe mantener sin cambios el título, las fotografías, la persona invitada y la audiencia mientras se resuelve la invitación de esta operación. |
| FR-010 | El sistema debe registrar la aceptación y publicar el álbum con ambas personas como autoras, en estado «Publicado» y para la audiencia seleccionada, sin ampliarla por la coautoría y manteniendo el acceso de ambas autoras. |
| FR-011 | El sistema debe dejar el álbum en estado «Colaboración rechazada» y accesible solo para la creadora cuando la persona invitada rechace, confirmar el rechazo a la invitada y notificarlo internamente a la creadora. |
| FR-012 | El sistema debe mostrar a la persona invitada una confirmación de publicación con acceso al álbum y generar una notificación interna de publicación para la creadora. |
| FR-013 | El sistema debe permitir cancelar antes de confirmar la invitación, sin conservar un álbum nuevo ni crear una invitación. |
| FR-014 | El sistema debe evitar un registro parcial del álbum o de la invitación si falla su guardado inicial, e informar a la creadora de que la invitación no se ha creado y de que puede intentarlo más tarde. |
| FR-015 | El sistema debe conservar el álbum y la invitación pendientes, sin registrar la aceptación ni publicar el álbum, cuando falle esa operación; informar a la invitada, notificarlo internamente a la creadora y permitir repetir la aceptación desde la misma invitación. |

#### 3.3. Relación entre el caso de uso y los requisitos

| ID | Caso de uso | UR asociados | FR asociados |
| --- | --- | --- | --- |
| UC-01 | Publicar un álbum colaborativo | UR-01 | FR-001, FR-002, FR-003, FR-004, FR-005, FR-006, FR-007, FR-008, FR-009, FR-010, FR-011, FR-012, FR-013, FR-014, FR-015 |

### 4. Descripción detallada de UC-01 · Publicar un álbum colaborativo

#### Actor principal

Persona creadora del álbum.

#### Actores de apoyo

Persona invitada como coautora: revisa el álbum y acepta o rechaza la colaboración desde su propia sesión.

#### Precondiciones

- La persona creadora dispone de una cuenta, ha iniciado sesión y tiene habilitada la publicación de álbumes.

La persona invitada debe acceder desde una sesión propia cuando intervenga; no necesita tenerla iniciada al comenzar el caso de uso. La existencia y las condiciones de su cuenta, los datos del álbum y las fotografías se comprueban durante el flujo.

#### Postcondiciones

**Tras completar el caso de uso con éxito:**

- El álbum queda en estado «Publicado», con el identificador asignado al crear la invitación.
- La aceptación de la persona invitada queda registrada y ambas personas figuran como autoras.
- El título, las fotografías y la audiencia corresponden a la propuesta revisada y aceptada.
- El álbum puede ser consultado por la audiencia seleccionada y por ambas autoras. La coautoría no amplía la audiencia a los seguidores de la invitada.
- La persona invitada recibe una confirmación con acceso al álbum y la creadora dispone de una notificación interna de publicación.

**Mientras el caso de uso está en espera:**

- El álbum y la invitación se conservan en estado pendiente, con el contenido y la audiencia fijados.
- El álbum solo puede ser consultado por la creadora y la persona invitada; todavía no es visible para la audiencia seleccionada.
- La invitada puede responder posteriormente desde la misma invitación.

**En las situaciones alternativas y de excepción:**

- Si se cancela antes de confirmar la invitación o falla su guardado inicial, no se conserva un álbum nuevo ni queda una invitación creada parcialmente.
- Si se rechaza la colaboración, el álbum queda sin publicar, en estado «Colaboración rechazada» y accesible únicamente para la creadora; ambas personas reciben la información correspondiente.
- Si falla el registro de la aceptación o la publicación, se mantiene el estado pendiente sin aceptación registrada ni publicación, se informa a ambas personas y la invitada puede repetir el intento desde la misma invitación.

#### Escenario principal de éxito

1. La persona creadora inicia la preparación de un álbum colaborativo.
2. El sistema solicita el título, las fotografías, la persona invitada y la audiencia del álbum.
3. La persona creadora introduce el título, aporta las fotografías, indica el identificador de la persona invitada y selecciona la audiencia.
4. El sistema comprueba los datos del álbum, el formato y la posibilidad de procesar todas las fotografías y las condiciones de la cuenta invitada.
5. El sistema muestra la vista previa, identifica a la persona invitada y la audiencia y solicita confirmar la invitación, indicando que la aceptación permitirá publicar automáticamente el álbum.
6. La persona creadora confirma el envío de la invitación.
7. El sistema guarda el álbum con un identificador único y el estado «Pendiente de aceptación», crea la invitación como notificación interna y muestra el identificador y el estado a la creadora.
8. La persona invitada abre la invitación desde su propia sesión.
9. El sistema muestra el álbum completo, la identidad de la creadora y la audiencia, y solicita aceptar o rechazar, explicando los efectos de la aceptación.
10. La persona invitada acepta la colaboración y autoriza aparecer como coautora y publicar el álbum para la audiencia mostrada.
11. El sistema registra la aceptación y publica el álbum en estado «Publicado», con ambas personas como autoras y para la audiencia seleccionada.
12. El sistema muestra a la persona invitada una confirmación con acceso al álbum y genera una notificación interna de publicación para la creadora.

#### Extensiones

**4.a. Los datos o las fotografías no cumplen las condiciones:**

1. El sistema indica los problemas detectados: título vacío, ausencia de fotografías, formato no admitido, fotografía que no puede procesarse o audiencia no válida.
2. El flujo de eventos vuelve al paso 3 para corregir la información o sustituir las fotografías afectadas.

**4.b. La cuenta invitada no cumple las condiciones:**

1. El sistema informa de que el identificador no corresponde a una cuenta activa distinta de la creadora.
2. El flujo de eventos vuelve al paso 3 para indicar otra persona invitada.

**5.a. La persona creadora elige corregir la propuesta:**

1. El flujo de eventos vuelve al paso 3.

**\*.a. En cualquier momento antes de confirmar la invitación, la persona creadora cancela la operación:**

1. El sistema descarta los datos de la operación sin conservar un álbum nuevo ni crear una invitación.
2. El caso de uso finaliza.

**7.a. Se produce un error al guardar el álbum y crear la invitación:**

1. El sistema evita que quede un álbum o una invitación registrados parcialmente.
2. El sistema informa a la creadora de que la invitación no se ha creado debido a un error técnico y sugiere intentarlo de nuevo más tarde.
3. El caso de uso finaliza.

**8.a. La persona invitada no abre la invitación en ese momento:**

1. El sistema conserva el álbum y la invitación pendientes, sin mostrar el álbum a la audiencia seleccionada.
2. La persona creadora puede cerrar su sesión sin que se pierda la propuesta.
3. El caso de uso queda en espera. Cuando la persona invitada abra la invitación desde su propia sesión, el flujo de eventos continúa en el paso 8.

**10.a. La persona invitada rechaza la colaboración:**

1. El sistema deja el álbum en estado «Colaboración rechazada», sin publicar y accesible únicamente para la creadora.
2. El sistema confirma el rechazo a la invitada y genera una notificación interna para la creadora.
3. El caso de uso finaliza sin publicar el álbum.

**10.b. La persona invitada aplaza su decisión después de revisar el álbum:**

1. El sistema conserva el álbum y la invitación pendientes, sin publicar el álbum.
2. El caso de uso queda en espera. Cuando la persona invitada abra de nuevo la invitación, el flujo de eventos continúa en el paso 8 para revisar la propuesta y responder.

**11.a. Se produce un error al registrar la aceptación o publicar el álbum:**

1. El sistema conserva el álbum y la invitación en estado pendiente, sin registrar la aceptación ni publicar el álbum.
2. El sistema informa a la invitada de que el álbum no se ha publicado debido a un error técnico y de que puede repetir la aceptación más tarde desde la misma invitación.
3. El sistema genera una notificación interna para informar del error a la creadora.
4. El caso de uso queda pendiente de un nuevo intento. Cuando la invitada abra de nuevo la invitación, el flujo de eventos continúa en el paso 8.

### 5. Observaciones para interpretar el ejemplo

- **Un caso de uso puede desarrollarse en varios momentos.** La invitación conserva la información necesaria para que la persona invitada responda después; cerrar la sesión de la creadora no cancela la propuesta.
- **Un estado de espera no equivale a una postcondición de éxito.** El álbum pendiente todavía no cumple el objetivo de publicación. La descripción distingue el resultado final de lo que se conserva durante la espera.
- **La aceptación se refiere a una propuesta concreta.** Mantener el contenido y la audiencia fijados evita que se publique algo distinto de lo que la persona invitada ha revisado.
- **La audiencia y la coautoría son decisiones diferentes.** Aceptar aparecer como coautora no amplía por sí mismo las personas que pueden ver el álbum.
- **Las confirmaciones respetan la participación en momentos distintos.** La invitada recibe la confirmación al aceptar y la creadora dispone de una notificación interna, aunque ya haya cerrado su sesión.