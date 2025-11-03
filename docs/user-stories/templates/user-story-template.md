# [CÓDIGO]: [Título de la Historia de Usuario]

[El código debe seguir el formato: HU-XXX, donde XXX es un número secuencial de tres dígitos. Ejemplo: HU-002, HU-015]

[El título debe ser descriptivo y comenzar con un sustantivo que indique la funcionalidad principal. Ejemplo: "Navegación en el panel principal del estudiante", "Registro de nuevos usuarios"]

---

## Objetivo

[Describe la historia de usuario usando el formato "Como... Quiero... Para..."]

**Como** [rol del usuario - Ejemplo: estudiante que ha iniciado sesión en el sistema],  
**Quiero** [acción o funcionalidad deseada - Ejemplo: orientarme fácilmente al ingresar],  
**Para** [beneficio o valor que obtiene el usuario - Ejemplo: poder encontrar y acceder rápidamente a las funcionalidades principales del sistema sin confusión].

---

## Reglas de Negocio

[Las reglas de negocio definen la lógica, restricciones y comportamientos que rigen la funcionalidad. Cada regla debe tener un código único en formato RN-XXX. Estas reglas son independientes de los escenarios y describen "cómo funciona el sistema" en lugar de "cómo se prueba".]

### **RN-001:** [Nombre descriptivo de la regla]

[Descripción clara y concisa de la regla de negocio]

[Ejemplo: "Estados de una tarea"]

Los estados posibles de una tarea son:

- **ESTADO_1**: [Descripción - Ejemplo: SIN EMPEZAR - No tiene intentos registrados]
- **ESTADO_2**: [Descripción - Ejemplo: EN PROGRESO - Tiene al menos un intento activo]
- **ESTADO_3**: [Descripción - Ejemplo: COMPLETADA - Superó la nota mínima de aprobación]

### **RN-002:** [Nombre de la segunda regla]

[Ejemplo: "Cálculo de calificación final"]

La calificación final se calcula mediante:

- [Fórmula o criterio - Ejemplo: Promedio ponderado de todos los intentos aprobados]
- [Condición - Ejemplo: Si no hay intentos aprobados, la calificación es 0]
- [Restricción - Ejemplo: La calificación máxima es 100 puntos]

### **RN-003:** [Nombre de la tercera regla]

[Ejemplo: "Disponibilidad de funcionalidades según rol"]

| Rol           | Funcionalidad A | Funcionalidad B | Funcionalidad C |
| ------------- | --------------- | --------------- | --------------- |
| Estudiante    | ✓               | ✓               | ✗               |
| Docente       | ✓               | ✓               | ✓               |
| Administrador | ✓               | ✓               | ✓               |

### **RN-004:** [Nombre de regla condicional]

[Ejemplo: "Actualización automática de estados"]

Cuando [condición - Ejemplo: la fecha actual supera la fecha límite]:

- Si [condición A - Ejemplo: la tarea está COMPLETADA], entonces [resultado - Ejemplo: mantiene el estado COMPLETADA]
- Si [condición B - Ejemplo: no hay intentos registrados], entonces [resultado - Ejemplo: cambia a VENCIDA]
- Si [condición C - Ejemplo: hay intentos pero ninguno aprobado], entonces [resultado - Ejemplo: cambia a FALLIDA]

---

## Escenarios

[Los escenarios describen situaciones específicas de uso utilizando el formato Gherkin (Dado/Cuando/Entonces). Cada escenario debe tener un código único en formato [SC-XXX]]

### **Característica:** [Nombre de la característica principal]

[Describe la característica general que agrupa los escenarios. Ejemplo: "Navegación hacia las funcionalidades principales", "Validación de credenciales de acceso"]

#### **Antecedentes:**

[Describe el contexto inicial común para todos los escenarios. Usa el formato "Dado/Y" para establecer precondiciones]

*Dado* [contexto inicial - Ejemplo: un estudiante llamado "David"],  
*Y* [condición adicional - Ejemplo: David cursa la materia de "Introducción al Marketing I"],  
*Y* [condición adicional - Ejemplo: David está registrado en una clase],  
*Y* [condición adicional - Ejemplo: David ha iniciado sesión de manera exitosa en el sistema]

---

#### **Escenario [SC-001]** [Nombre descriptivo del escenario]

[Cada escenario debe tener un título que resuma claramente qué se está probando. Ejemplo: "Vista inicial al ingresar al sistema", "Validación de credenciales incorrectas"]

**Dado** [precondición específica del escenario - Ejemplo: que David ha iniciado sesión],  
**Cuando** [acción que ejecuta el usuario - Ejemplo: accede al sistema],  
**Entonces** [resultado esperado - Ejemplo: debería visualizar un banner con la siguiente información]:

- [Elemento 1 - Ejemplo: Nombre y NRC del curso al que pertenece David]
- [Elemento 2 - Ejemplo: Mensaje de saludo con su nombre completo]
- [Elemento 3 - Ejemplo: Opción para cerrar sesión]

**Y** [resultado adicional esperado - Ejemplo: debería ver accesos visibles a las demás funcionalidades principales]:

- [Funcionalidad 1 - Ejemplo: Evaluaciones]
- [Funcionalidad 2 - Ejemplo: Nueva partida]
- [Funcionalidad 3 - Ejemplo: Progreso]

**Y** [resultado adicional esperado - Ejemplo: debería visualizar la funcionalidad *"Tareas"* como vista por defecto]

---

#### **Escenario [SC-002]** [Nombre del segundo escenario]

[Considera incluir escenarios para:]

- [Casos de uso felices (camino exitoso)]
- [Casos de error o excepciones]
- [Validaciones de datos]
- [Estados de carga]
- [Manejo de errores]

**Dado** [precondición],  
**Y** [condición adicional si es necesaria],  
**Cuando** [acción del usuario],  
**Entonces** [resultado esperado],  
**Y** [resultado adicional si aplica]

---

## Dependencias

[Lista las dependencias necesarias para implementar esta historia de usuario]

### Historias de Usuario Relacionadas

- [HU-XXX: Nombre de la historia - Ejemplo: HU-001: Autenticación de usuarios]
- [HU-XXX: Nombre de la historia - Ejemplo: HU-005: Gestión de perfiles de estudiante]

### Sistemas Externos o APIs

- [Nombre del sistema/API - Endpoint/Versión - Propósito]
    - [Ejemplo: API de Autenticación - /api/v1/auth - Validación de credenciales JWT]
    - [Ejemplo: Servicio de Base de Datos - PostgreSQL 14+ - Almacenamiento de información de estudiantes]

### Infraestructura Requerida

- [Componente de infraestructura necesario]
    - [Ejemplo: Servidor web con soporte HTTPS]
    - [Ejemplo: Redis para gestión de sesiones]
    - [Ejemplo: CDN para recursos estáticos]

---

## Consideraciones Generales

### Consideraciones técnicas

#### [Título de la consideración técnica - Ejemplo: Protección de datos sensibles del estudiante]

**[Categoría de datos]:** [Ejemplo: Información del estudiante]

- [Dato sensible 1 - Ejemplo: Nombre completo]
- [Dato sensible 2 - Ejemplo: NRC (Número de Referencia de Curso)]

**[Categoría de datos]:** [Ejemplo: Información de la asignatura]

- [Dato 1 - Ejemplo: Nombre del curso: "Introducción al Marketing I"]
- [Dato 2 - Ejemplo: Semestre académico actual (ejemplo: 2025-20)]

Para cumplir con [normativa aplicable - Ejemplo: la Ley Orgánica de Protección de Datos Personales del Ecuador (2021)], [describe las medidas técnicas - Ejemplo: Se utilizará protocolo HTTPS y JSON Web Token para la comunicación entre cliente y servidor, garantizando la confidencialidad de la información desde su captura hasta su almacenamiento. Adicionalmente la sesión se cerrará automáticamente después de cinco minutos de inactividad.]

---

### Consideraciones UI/UX

#### Responsividad

[Ejemplo: La interfaz debe ser adaptable y ajustarse a: Escritorio (≥1025px), Tableta (768px-1024px), Móvil (≤767px)]

#### Textos y ayudas

- [Elemento de UI]: "[Texto del tooltip - Ejemplo: Modo Tutorial: 'Aprende el funcionamiento básico del videojuego con un escenario que abarca el tema de conducta del consumidor con guías paso a paso.']"
- [Elemento de UI]: "[Texto del tooltip - Ejemplo: Modo Normal: 'Practica libremente en escenarios aleatorios de mercado.']"

#### Navegadores compatibles

- [Navegador 1 - Ejemplo: Google Chrome (versión 120 o superior)]
- [Navegador 2 - Ejemplo: Mozilla Firefox (versión 115 o superior)]
- [Navegador 3 - Ejemplo: Microsoft Edge (versión 120 o superior)]
- [Navegador 4 - Ejemplo: Safari (versión 17 o superior)]

#### Accesibilidad

- [Ejemplo: Cumplimiento con WCAG 2.1 nivel AA]
- [Ejemplo: Soporte para lectores de pantalla]
- [Ejemplo: Navegación completa por teclado]

#### Escalabilidad

[Ejemplo: La funcionalidad debe soportar hasta 90 usuarios concurrentes.]

#### Rendimiento

[Ejemplo: El tiempo de carga de la página no debe exceder los 3 segundos, y las respuestas de la API no deben superar los 10 segundos.]

#### Referencias de diseño

[Ejemplo: [Enlace a Figma](https://www.figma.com/...)]

---

## Definición de Hecho

Define los criterios específicos que deben cumplirse para considerar esta historia de usuario como completada y lista para producción. Los criterios varían según la complejidad y naturaleza de cada historia. Organiza los criterios en categorías relevantes (Desarrollo, Pruebas, Calidad, Documentación, Despliegue, etc.) y utiliza checkboxes para facilitar el seguimiento.

### [Categoría 1 - Ejemplo: Desarrollo]

- [ ] [Criterio específico - Ejemplo: Código completado y cumple con los estándares del equipo]
- [ ] [Criterio específico - Ejemplo: Revisión de código completada y aprobada]
- [ ] [Criterio específico - Ejemplo: Sin deuda técnica crítica introducida]

### [Categoría 2 - Ejemplo: Pruebas]

- [ ] [Criterio específico - Ejemplo: Pruebas unitarias escritas y pasando (cobertura mínima: 80%)]
- [ ] [Criterio específico - Ejemplo: Pruebas de integración pasando]
- [ ] [Criterio específico - Ejemplo: Casos de prueba manuales ejecutados y documentados]

### [Categoría 3 - Ejemplo: Calidad]

- [ ] [Criterio específico - Ejemplo: Sin errores críticos o bloqueantes]
- [ ] [Criterio específico - Ejemplo: Cumple con todos los criterios de aceptación definidos en los escenarios]

### [Categoría 4 - Ejemplo: Documentación]

- [ ] [Criterio específico - Ejemplo: Documentación técnica actualizada]
- [ ] [Criterio específico - Ejemplo: README actualizado con nuevas funcionalidades]

### [Categoría 5 - Ejemplo: Despliegue]

- [ ] [Criterio específico - Ejemplo: Desplegado en ambiente de staging]
- [ ] [Criterio específico - Ejemplo: Validación completada por Product Owner]

---

## Comentarios

[Ejemplo: "Se decidió usar WebSockets en lugar de polling para mejorar el rendimiento en tiempo real"]
[Ejemplo: "Pendiente definir el comportamiento cuando el usuario tiene múltiples roles"]
[Si no hay comentarios: "N/A"]
