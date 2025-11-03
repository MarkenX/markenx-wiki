# HU-004: Historial de Intentos de Tarea

---

## Objetivo

**Como** estudiante que ha iniciado sesión en el sistema,  
**Quiero** visualizar el historial completo de intentos realizados en una tarea específica,  
**Para** revisar mi desempeño, analizar mi progreso y consultar estadísticas detalladas de cada intento.

---

## Reglas de Negocio

### **RN-001:** Estados de un intento

Los estados posibles de un intento son:

- **APROBADO**: El intento alcanzó o superó la nota mínima de aprobación configurada para la tarea
- **REPROBADO**: El intento no alcanzó la nota mínima de aprobación

### **RN-002:** Cálculo de duración del intento

La duración de un intento se calcula como:

- Tiempo transcurrido desde el inicio hasta la finalización del intento
- Se muestra en formato HH:MM (horas:minutos)
- Ejemplo: 01:35 representa 1 hora y 35 minutos

### **RN-003:** Información mostrada por intento

Cada intento en el historial debe mostrar:

- Número de intento (secuencial)
- Puntuación obtenida
- Fecha de realización en formato dd/mm/yyyy
- Estado (APROBADO o REPROBADO según RN-001)
- Duración en formato HH:MM
- Acción de ESTADÍSTICAS disponible

### **RN-004:** Ordenamiento de intentos

Los intentos se ordenan por fecha de realización del más reciente al más antiguo (descendente).

### **RN-005:** Cálculo de intentos restantes

- Intentos restantes = Intentos máximos - Intentos realizados
- Si quedan 0 intentos: no se muestra información especial
- Si queda exactamente 1 intento: se debe destacar visualmente esta información

### **RN-006:** Acceso al historial

El historial solo está disponible para tareas que tienen al menos un intento registrado.

---

## Escenarios

### **Antecedentes comunes:**

*Dado* un estudiante llamado David,  
*Y* está registrado en al menos una clase,  
*Y* ha iniciado sesión de manera exitosa en el sistema,  
*Y* ha accedido al panel de Tareas

---

### **Característica:** Visualización básica del historial

#### **Escenario [SC-001]** Acceso al historial desde el panel de tareas

**Dado** que existe una tarea llamada "Introducción al Marketing" con 3 intentos registrados,  
**Cuando** el estudiante presiona el botón "HISTORIAL" de la tarea,  
**Entonces** debería ser redirigido a una nueva página de historial de intentos  
**Y** la URL debería cambiar para reflejar el contexto de la tarea

---

#### **Escenario [SC-002]** Visualización del encabezado de la página

**Dado** que el estudiante accedió al historial de la tarea "Introducción al Marketing",  
**Y** la descripción de la tarea es "Análisis de mercado y estrategias de ventas",  
**Cuando** se carga la página de historial,  
**Entonces** debería visualizar el título "Introducción al Marketing"  
**Y** debería visualizar la descripción "Análisis de mercado y estrategias de ventas"

---

#### **Escenario [SC-003]** Visualización de la tabla de intentos

**Dado** que el estudiante está en la página de historial,  
**Cuando** se carga la página,  
**Entonces** debería ver una tabla con las siguientes columnas:

- Número de intento
- Puntuación
- Fecha
- Estado
- Duración
- Acciones

---

#### **Escenario [SC-004]** Listado de intentos realizados

**Dado** que la tarea tiene 5 intentos registrados,  
**Cuando** se carga el historial,  
**Entonces** debería visualizar los 5 intentos en la tabla  
**Y** cada intento debería mostrar toda la información según RN-003

---

#### **Escenario [SC-005]** Ordenamiento de intentos del más nuevo al más viejo

**Dado** que existen intentos con las siguientes fechas:

- Intento 1: 01/11/2025
- Intento 2: 05/11/2025
- Intento 3: 03/11/2025

**Cuando** se carga el historial,  
**Entonces** los intentos deberían aparecer en el orden: Intento 2, Intento 3, Intento 1

---

#### **Escenario [SC-006]** Visualización de estado APROBADO

**Dado** que un intento obtuvo 85 puntos,  
**Y** la nota mínima de aprobación es 70 puntos,  
**Cuando** se visualiza el intento en el historial,  
**Entonces** el estado debería mostrarse como "APROBADO"

---

#### **Escenario [SC-007]** Visualización de estado REPROBADO

**Dado** que un intento obtuvo 60 puntos,  
**Y** la nota mínima de aprobación es 70 puntos,  
**Cuando** se visualiza el intento en el historial,  
**Entonces** el estado debería mostrarse como "REPROBADO"

---

#### **Escenario [SC-008]** Formato de fecha en tabla

**Dado** que un intento se realizó el 2025-11-15,  
**Cuando** se visualiza en el historial,  
**Entonces** la fecha debería mostrarse como "15/11/2025"

---

#### **Escenario [SC-009]** Formato de duración en tabla

**Dado** que un intento duró 95 minutos,  
**Cuando** se visualiza en el historial,  
**Entonces** la duración debería mostrarse como "01:35"

---

### **Característica:** Contador de intentos restantes

#### **Escenario [SC-010]** Visualización de intentos restantes - Múltiples intentos disponibles

**Dado** que la tarea permite 5 intentos máximos,  
**Y** se han realizado 3 intentos,  
**Cuando** se carga el historial,  
**Entonces** debería visualizar el texto "Intentos restantes: 2"

---

#### **Escenario [SC-011]** Destacado visual cuando queda un solo intento

**Dado** que la tarea permite 5 intentos máximos,  
**Y** se han realizado 4 intentos,  
**Cuando** se carga el historial,  
**Entonces** debería visualizar el texto "Intentos restantes: 1"  
**Y** el texto debería estar destacado visualmente (por ejemplo, en color rojo o con un ícono de advertencia)

---

#### **Escenario [SC-012]** Sin intentos restantes

**Dado** que la tarea permite 5 intentos máximos,  
**Y** se han realizado 5 intentos,  
**Cuando** se carga el historial,  
**Entonces** debería visualizar el texto "Intentos restantes: 0"  
**Y** NO debería haber ningún destacado visual especial

---

### **Característica:** Filtrado de intentos

#### **Escenario [SC-013]** Filtro por estado - APROBADO

**Dado** que existen los siguientes intentos:

- Intento 1: REPROBADO
- Intento 2: APROBADO
- Intento 3: APROBADO
- Intento 4: REPROBADO

**Cuando** el estudiante aplica el filtro de estado "APROBADO",  
**Entonces** debería visualizar únicamente los intentos 2 y 3

---

#### **Escenario [SC-014]** Filtro por estado - REPROBADO

**Dado** que existen los siguientes intentos:

- Intento 1: REPROBADO
- Intento 2: APROBADO
- Intento 3: REPROBADO

**Cuando** el estudiante aplica el filtro de estado "REPROBADO",  
**Entonces** debería visualizar únicamente los intentos 1 y 3

---

#### **Escenario [SC-015]** Filtro por rango de fechas

**Dado** que existen intentos realizados entre 01/11/2025 y 30/11/2025,  
**Cuando** el estudiante filtra por rango de fechas del 10/11/2025 al 20/11/2025,  
**Entonces** debería visualizar únicamente los intentos cuya fecha de realización esté dentro de ese rango

---

#### **Escenario [SC-016]** Combinación de filtros

**Dado** que existen múltiples intentos con diferentes estados y fechas,  
**Cuando** el estudiante aplica filtro de estado "APROBADO" Y rango de fechas del 01/11/2025 al 15/11/2025,  
**Entonces** debería visualizar únicamente los intentos APROBADOS realizados dentro del rango de fechas especificado

---

#### **Escenario [SC-017]** Resultado vacío en filtros

**Dado** que no existen intentos que cumplan los criterios de filtrado,  
**Cuando** el estudiante aplica un filtro,  
**Entonces** debería visualizar un mensaje indicando "No se encontraron intentos con los criterios seleccionados"

---

#### **Escenario [SC-018]** Limpieza de filtros

**Dado** que el estudiante tiene filtros aplicados,  
**Y** está visualizando resultados filtrados,  
**Cuando** el estudiante limpia o resetea los filtros,  
**Entonces** debería visualizar todos los intentos nuevamente

---

### **Característica:** Paginación

#### **Escenario [SC-019]** Paginación con más de 10 intentos

**Dado** que la tarea tiene 25 intentos registrados,  
**Cuando** se carga el historial,  
**Entonces** debería visualizar los primeros 10 intentos en la página 1  
**Y** debería ver un control de paginación indicando "Página 1 de 3"

---

#### **Escenario [SC-020]** Navegación entre páginas

**Dado** que el estudiante está en la página 1 con 25 intentos totales,  
**Cuando** el estudiante hace clic en "Siguiente" o selecciona la página 2,  
**Entonces** debería visualizar los intentos del 11 al 20  
**Y** el indicador debería mostrar "Página 2 de 3"

---

#### **Escenario [SC-021]** Paginación con menos de 10 intentos

**Dado** que la tarea tiene 8 intentos registrados,  
**Cuando** se carga el historial,  
**Entonces** debería visualizar los 8 intentos en una única página  
**Y** NO debería mostrar controles de paginación

---

#### **Escenario [SC-022]** Paginación después de aplicar filtros

**Dado** que el estudiante aplicó filtros que resultaron en 15 intentos,  
**Cuando** se muestran los resultados filtrados,  
**Entonces** debería ver los primeros 10 intentos en la página 1  
**Y** debería poder navegar a la página 2 para ver los 5 intentos restantes

---

### **Característica:** Acceso a estadísticas

#### **Escenario [SC-023]** Botón ESTADÍSTICAS visible en todos los intentos

**Dado** que existen múltiples intentos en el historial,  
**Cuando** el estudiante visualiza la tabla,  
**Entonces** cada intento debería tener un botón "ESTADÍSTICAS" o "STATS" en la columna de acciones

---

#### **Escenario [SC-024]** Acceso a estadísticas de un intento específico

**Dado** que el estudiante está visualizando el historial,  
**Cuando** presiona el botón "ESTADÍSTICAS" del intento número 3,  
**Entonces** debería ser redirigido a la página de estadísticas de ese intento específico

---

### **Característica:** Navegación y retorno

#### **Escenario [SC-025]** Botón de retorno al panel de tareas

**Dado** que el estudiante está en la página de historial,  
**Cuando** presiona el botón de "Volver" o el botón de navegación hacia atrás,  
**Entonces** debería regresar al panel de Tareas  
**Y** debería mantener el estado de filtros y paginación que tenía antes

---

## Dependencias

### Historias de Usuario Relacionadas

- HU-010: Gestión de Tareas del Estudiante

### Sistemas Externos o APIs

- Servicio de Base de Datos - MySQL - Consulta de intentos y datos relacionados con tareas

### Infraestructura Requerida

N/A

---

## Consideraciones Generales

### Consideraciones técnicas

#### Protección de datos del estudiante

**Información del intento:**

- Puntuación obtenida
- Fecha y hora de realización
- Duración del intento
- Estado del intento

**Información de la tarea:**

- Título de la tarea
- Descripción de la tarea
- Configuración de intentos máximos

Para cumplir con la Ley Orgánica de Protección de Datos Personales del Ecuador (2021), se utilizará protocolo HTTPS para todas las comunicaciones. Los datos del historial son privados y solo accesibles por el estudiante propietario. La sesión se cerrará automáticamente después de cinco minutos de inactividad.

---

### Consideraciones UI/UX

#### Responsividad

La interfaz se adaptará a pantallas de escritorio (≥1025px)

#### Textos y ayudas

- **ESTADÍSTICAS/STATS**: "Ver estadísticas detalladas de desempeño de este intento"
- **Intentos restantes (cuando queda 1)**: "¡Atención! Solo te queda 1 intento disponible"
- **Filtro por estado**: "Filtra los intentos por su resultado (Aprobado o Reprobado)"
- **Filtro por fecha**: "Selecciona un rango de fechas para ver intentos realizados en ese período"

#### Navegadores compatibles

- Google Chrome (versión 120 o superior)
- Mozilla Firefox (versión 115 o superior)
- Microsoft Edge (versión 120 o superior)
- Safari (versión 17 o superior)

#### Accesibilidad

- Cumplimiento con WCAG 2.1 nivel AA
- Soporte para lectores de pantalla
- Navegación completa por teclado
- Contraste adecuado para el texto de advertencia de "1 intento restante"

#### Escalabilidad

La funcionalidad debe soportar hasta 90 usuarios concurrentes

#### Rendimiento

- Tiempo de carga de la página ≤ 3 segundos
- Respuesta de API para consulta de intentos ≤ 10 segundos
- Carga optimizada de intentos mediante paginación

#### Referencias de diseño

N/A

---

## Definición de Hecho

N/A

---

## Comentarios

N/A
