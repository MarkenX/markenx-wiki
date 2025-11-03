# HU-003: Gestión de Tareas del Estudiante

---

## Objetivo

**Como** estudiante que ha iniciado sesión en el sistema,  
**Quiero** visualizar y gestionar mis tareas de manera clara y ordenada,  
**Para** poder conocer el estado de cada tarea, iniciar intentos y revisar mi progreso fácilmente.

---

## Reglas de Negocio

### **RN-001:** Estados de tareas

Los estados posibles de una tarea son:

- **SIN EMPEZAR**: No tiene intentos registrados
- **EN PROGRESO**: Tiene al menos un intento sin completar o sin superar la nota mínima y no ha vencido
- **COMPLETADA**: Al menos un intento superó la nota mínima de aprobación
- **FALLIDA**: La fecha límite venció y ningún intento superó la nota mínima
- **VENCIDA**: La fecha límite venció sin intentos registrados

### **RN-002:** Actualización automática de estados por vencimiento

Cuando la fecha actual supera la fecha límite de una tarea:

- Si la tarea está **COMPLETADA**, mantiene el estado COMPLETADA
- Si no hay intentos registrados, cambia a **VENCIDA**
- Si hay intentos pero ninguno superó la nota mínima, cambia a **FALLIDA**

### **RN-003:** Disponibilidad de intentos

- Una tarea tiene un número máximo de intentos configurado
- El contador de "intento activo" indica cuántos intentos se han utilizado
- Se pueden crear nuevos intentos mientras:
  - No se haya alcanzado el número máximo de intentos, Y
  - No se haya superado la fecha límite

### **RN-004:** Acciones disponibles según estado

| Estado      | JUGAR | NUEVO INTENTO | HISTORIAL |
| ----------- | ----- | ------------- | --------- |
| SIN EMPEZAR | ✓     | ✗             | ✗         |
| EN PROGRESO | ✗     | ✓*            | ✓         |
| COMPLETADA  | ✗     | ✓*            | ✓         |
| FALLIDA     | ✗     | ✗             | ✓         |
| VENCIDA     | ✗     | ✗             | ✓**       |

*Solo si quedan intentos disponibles  
**Solo si existen intentos registrados

### **RN-005:** Ordenamiento predeterminado

Las tareas se ordenan por fecha límite de la más reciente a la más antigua (descendente).

### **RN-006:** Información de tareas

Cada tarea debe mostrar:

- Título (máximo 100 caracteres)
- Resumen/Descripción
- Estado actual
- Número de intentos máximos permitidos
- Intento activo (intentos utilizados)
- Fecha límite

---

## Escenarios

### **Antecedentes comunes:**

*Dado* un estudiante llamado David,  
*Y* está registrado en al menos una clase,  
*Y* ha iniciado sesión de manera exitosa en el sistema,  
*Y* ha accedido al panel de *Tareas* desde el menú principal

---

### **Característica:** Visualización básica del panel de tareas

#### **Escenario [SC-001]** Visualización del título y estructura básica

**Dado** que el estudiante ha accedido al panel de Tareas,  
**Cuando** se carga la página,  
**Entonces** debería visualizar un título con el texto "Tareas"  
**Y** debería ver una tabla con columnas para: Título, Resumen, Estado, Intentos Máximos, Intento Activo, Fecha Límite y Acciones

---

#### **Escenario [SC-002]** Listado de tareas asignadas

**Dado** que el estudiante tiene 5 tareas asignadas,  
**Cuando** se carga el panel de Tareas,  
**Entonces** debería ver las 5 tareas listadas en la tabla  
**Y** cada tarea debería mostrar toda su información según RN-006

---

#### **Escenario [SC-003]** Ordenamiento predeterminado por fecha límite

**Dado** que existen tareas con las siguientes fechas límite:

- Tarea A: 2025-11-15
- Tarea B: 2025-11-10
- Tarea C: 2025-11-20

**Cuando** se carga el panel de Tareas,  
**Entonces** las tareas deberían aparecer en el orden: Tarea C, Tarea A, Tarea B

---

### **Característica:** Filtrado de tareas

#### **Escenario [SC-004]** Filtro por estado - Un estado seleccionado

**Dado** que existen tareas en diferentes estados:

- 2 tareas SIN EMPEZAR
- 3 tareas EN PROGRESO
- 1 tarea COMPLETADA

**Cuando** el estudiante aplica el filtro de estado "EN PROGRESO",  
**Entonces** debería visualizar únicamente las 3 tareas EN PROGRESO

---

#### **Escenario [SC-005]** Filtro por rango de fechas

**Dado** que existen tareas con fechas límite entre 2025-11-01 y 2025-11-30,  
**Cuando** el estudiante filtra por rango de fechas del 2025-11-10 al 2025-11-20,  
**Entonces** debería visualizar únicamente las tareas cuya fecha límite esté dentro de ese rango

---

#### **Escenario [SC-006]** Combinación de filtros

**Dado** que existen múltiples tareas con diferentes estados y fechas,  
**Cuando** el estudiante aplica filtro de estado "COMPLETADA" Y rango de fechas del 2025-11-01 al 2025-11-15,  
**Entonces** debería visualizar únicamente las tareas COMPLETADAS con fecha límite dentro del rango especificado

---

#### **Escenario [SC-007]** Resultado vacío en filtros

**Dado** que no existen tareas que cumplan los criterios de filtrado,  
**Cuando** el estudiante aplica un filtro,  
**Entonces** debería visualizar un mensaje indicando "No se encontraron tareas con los criterios seleccionados"

---

### **Característica:** Paginación

#### **Escenario [SC-008]** Paginación con más de 10 tareas

**Dado** que el estudiante tiene 25 tareas asignadas,  
**Cuando** se carga el panel de Tareas,  
**Entonces** debería visualizar las primeras 10 tareas en la página 1  
**Y** debería ver un control de paginación indicando "Página 1 de 3"

---

#### **Escenario [SC-009]** Navegación entre páginas

**Dado** que el estudiante está en la página 1 con 25 tareas totales,  
**Cuando** el estudiante hace clic en "Siguiente" o selecciona la página 2,  
**Entonces** debería visualizar las tareas de la 11 a la 20  
**Y** el indicador debería mostrar "Página 2 de 3"

---

### **Característica:** Acciones sobre tareas

#### **Escenario [SC-010]** Botón JUGAR visible en tarea sin empezar

**Dado** que existe una tarea en estado SIN EMPEZAR,  
**Cuando** el estudiante visualiza la tarea en la tabla,  
**Entonces** debería ver únicamente el botón "JUGAR" en la columna de acciones  
**Y** NO debería ver los botones "NUEVO INTENTO" ni "HISTORIAL"

---

#### **Escenario [SC-011]** Inicio del primer intento

**Dado** que una tarea está en estado SIN EMPEZAR con 0 intentos activos,  
**Cuando** el estudiante presiona el botón "JUGAR",  
**Entonces** se debería crear un nuevo intento activo  
**Y** el estado de la tarea debería cambiar a EN PROGRESO  
**Y** el contador de intento activo debería mostrar 1

---

#### **Escenario [SC-012]** Botones visibles en tarea en progreso con intentos disponibles

**Dado** que existe una tarea en estado EN PROGRESO,  
**Y** el intento activo es 2 de 5 intentos máximos,  
**Cuando** el estudiante visualiza la tarea,  
**Entonces** debería ver los botones "NUEVO INTENTO" y "HISTORIAL"  
**Y** NO debería ver el botón "JUGAR"

---

#### **Escenario [SC-013]** Inicio de intento adicional

**Dado** que una tarea está EN PROGRESO con 2 intentos utilizados de 5 máximos,  
**Cuando** el estudiante presiona "NUEVO INTENTO",  
**Entonces** se debería crear un nuevo intento  
**Y** el contador de intento activo debería incrementarse a 3

---

#### **Escenario [SC-014]** Botón NUEVO INTENTO oculto cuando se agotan intentos

**Dado** que una tarea está EN PROGRESO con 5 intentos utilizados de 5 máximos,  
**Cuando** el estudiante visualiza la tarea,  
**Entonces** NO debería ver el botón "NUEVO INTENTO"  
**Y** debería ver únicamente el botón "HISTORIAL"

---

#### **Escenario [SC-015]** Botones en tarea completada con intentos disponibles

**Dado** que una tarea está en estado COMPLETADA,  
**Y** el intento activo es 2 de 5 intentos máximos,  
**Cuando** el estudiante visualiza la tarea,  
**Entonces** debería ver los botones "NUEVO INTENTO" y "HISTORIAL"

---

#### **Escenario [SC-016]** Visualización del historial de intentos

**Dado** que una tarea tiene 3 intentos registrados con las siguientes calificaciones:

- Intento 1: 60 puntos, fecha 2025-11-01, estado: Reprobado
- Intento 2: 75 puntos, fecha 2025-11-05, estado: Aprobado
- Intento 3: 85 puntos, fecha 2025-11-08, estado: Aprobado

**Cuando** el estudiante presiona el botón "HISTORIAL",  
**Entonces** debería visualizar un listado con los 3 intentos ordenados del más reciente al más antiguo  
**Y** cada intento debería mostrar: número de intento, calificación, fecha y estado

---

### **Característica:** Actualización automática de estados

#### **Escenario [SC-017]** Tarea vencida sin intentos

**Dado** que una tarea está en estado SIN EMPEZAR con fecha límite 2025-11-01,  
**Cuando** la fecha actual es 2025-11-02 y se actualiza el sistema,  
**Entonces** el estado de la tarea debería cambiar automáticamente a VENCIDA

---

#### **Escenario [SC-018]** Tarea fallida por vencimiento

**Dado** que una tarea está EN PROGRESO con fecha límite 2025-11-01,  
**Y** tiene 2 intentos registrados sin superar la nota mínima de aprobación,  
**Cuando** la fecha actual es 2025-11-02 y se actualiza el sistema,  
**Entonces** el estado de la tarea debería cambiar automáticamente a FALLIDA

---

#### **Escenario [SC-019]** Tarea completada mantiene su estado tras vencimiento

**Dado** que una tarea está en estado COMPLETADA con fecha límite 2025-11-01,  
**Cuando** la fecha actual es 2025-11-02 y se actualiza el sistema,  
**Entonces** el estado de la tarea debería permanecer como COMPLETADA

---

#### **Escenario [SC-020]** Botón HISTORIAL visible en tarea vencida con intentos

**Dado** que una tarea cambió a estado VENCIDA y tiene 2 intentos registrados,  
**Cuando** el estudiante visualiza la tarea,  
**Entonces** debería ver únicamente el botón "HISTORIAL"  
**Y** NO debería ver los botones "JUGAR" ni "NUEVO INTENTO"

---

#### **Escenario [SC-021]** Sin acciones disponibles en tarea vencida sin intentos

**Dado** que una tarea cambió a estado VENCIDA sin intentos registrados,  
**Cuando** el estudiante visualiza la tarea,  
**Entonces** NO debería ver ningún botón de acción en la columna de acciones

---

## Dependencias

### Historias de Usuario Relacionadas

- HU-002: Navegación en el panel principal del estudiante

### Sistemas Externos o APIs

- Servicio de Base de Datos - MySQL - Almacenamiento de información de tareas y registros de intentos

### Infraestructura Requerida

N/A

---

## Consideraciones Generales

### Consideraciones técnicas

N/A

---

### Consideraciones UI/UX

#### Responsividad

La interfaz se adaptará a pantallas de escritorio (≥1025px)

#### Textos y ayudas

- **JUGAR**: "Inicia el primer intento de la tarea"
- **NUEVO INTENTO**: "Inicia un nuevo intento si hay intentos disponibles"
- **HISTORIAL**: "Ver registro de intentos realizados"

#### Navegadores compatibles

- Google Chrome (versión 120 o superior)
- Mozilla Firefox (versión 115 o superior)
- Microsoft Edge (versión 120 o superior)
- Safari (versión 17 o superior)

#### Accesibilidad

- Cumplimiento con WCAG 2.1 nivel AA
- Soporte para lectores de pantalla
- Navegación completa por teclado

#### Escalabilidad

La funcionalidad debe soportar hasta 90 usuarios concurrentes

#### Rendimiento

- Tiempo de carga de la página ≤ 3 segundos
- Respuesta de API ≤ 10 segundos

#### Referencias de diseño

N/A

---

## Definición de Hecho

### Desarrollo

N/A

### Pruebas

N/A

### Calidad

N/A

### Documentación

N/A

### Despliegue

N/A

---

## Comentarios

N/A
