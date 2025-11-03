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

### Desarrollo

- [ ] Código completado y cumple con los estándares del equipo
- [ ] Revisión de código completada y aprobada
- [ ] Sin deuda técnica crítica
- [ ] Código versionado correctamente en el repositorio

### Pruebas

- [ ] Pruebas unitarias escritas y pasando
- [ ] Pruebas de integración pasando
- [ ] Pruebas de extremo a extremo pasando
- [ ] Casos de prueba manuales documentados
- [ ] Pruebas de regresión pasando

### Calidad

- [ ] Sin errores críticos
- [ ] Cumple con los criterios de aceptación
- [ ] Validaciones de seguridad completadas
- [ ] Rendimiento validado
- [ ] Accesibilidad validada

### Documentación

- [ ] Documentación técnica actualizada
- [ ] Documentación de usuario actualizada
- [ ] Comentarios en código agregados
- [ ] README actualizado
- [ ] Changelog actualizado

### Despliegue

- [ ] Desplegado en ambiente de desarrollo
- [ ] Desplegado en ambiente de pruebas
- [ ] Validación en pruebas completada
- [ ] Scripts de migración probados
- [ ] Plan de reversión documentado

### Aceptación

- [ ] Product Owner ha validado la funcionalidad
- [ ] Criterios de aceptación aprobados por stakeholders
- [ ] Aprobación final para producción

---

## Comentarios

[Ejemplo: "Se decidió usar WebSockets en lugar de polling para mejorar el rendimiento en tiempo real"]
[Ejemplo: "Pendiente definir el comportamiento cuando el usuario tiene múltiples roles"]
[Si no hay comentarios: "N/A"]
