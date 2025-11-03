# HU-002: Navegación en el panel principal del estudiante

---

## **Objetivo**

**Como** estudiante que ha iniciado sesión en el sistema,  
**Quiero** orientarme fácilmente al ingresar,  
**Para** poder encontrar y acceder rápidamente a las funcionalidades principales del sistema sin confusión.

---

## **Escenarios**

- [**Característica:** Navegación hacia las funcionalidades principales](#característica-navegación-hacia-las-funcionalidades-principales)
    - [**Escenario \[SC-001\]** Vista inicial al ingresar al sistema](#escenario-sc-001-vista-inicial-al-ingresar-al-sistema)
    - [**Escenario \[SC-002\]** Navegación hacia la ventana de tareas](#escenario-sc-002-navegación-hacia-la-ventana-de-tareas)
    - [**Escenario \[SC-003\]** Navegación hacia la ventana de evaluaciones](#escenario-sc-003-navegación-hacia-la-ventana-de-evaluaciones)
    - [**Escenario \[SC-004\]** Navegación hacia la funcionalidad *"Progreso"*](#escenario-sc-004-navegación-hacia-la-funcionalidad-progreso)
- [**Característica:** Gestión de partidas](#caracteristica-gestion-de-partidas)
    - [**Escenario \[SC-005\]** Visualización de las subopciones dentro de la opción *"Nueva partida"*](#escenario-sc-005-visualización-de-las-subopciones-dentro-de-la-opción-nueva-partida)
    - [**Escenario \[SC-006\]** Inicio de una nueva *"Partida normal"*](#escenario-sc-006-inicio-de-una-nueva-partida-normal)
    - [**Escenario \[SC-007\]** Inicio del *"Tutorial"*](#escenario-sc-007-inicio-del-tutorial)
- [**Característica:** Manejo de estados del sistema](#caracteristica-manejo-de-estados-del-sistema)
    - [**Escenario \[SC-008\]** Visualización del loader mientras se carga la información](#escenario-sc-008-visualización-del-loader-mientras-se-carga-la-información)
    - [**Escenario \[SC-009\]** Manejo de error cuando no se carga la información](#escenario-sc-009-manejo-de-error-cuando-no-se-carga-la-información)
- [**Característica:** Gestión de sesión de usuario](#caracteristica-gestion-de-sesion-de-usuario)
    - [**Escenario \[SC-010\]** Cerrar sesión](#escenario-sc-010-cerrar-sesión)

---

### **Antecedentes:**

*Dado* un estudiante de la *Universidad de las Américas*,  
*Y* el estudiante cursa la materia de *Introducción al Marketing I*,  
*Y* el estudiante está registrado en un curso,  
*Y* el estudiante ha iniciado sesión de manera exitosa en el sistema

---

### **Característica:** Navegación hacia las funcionalidades principales

---

#### **Escenario [SC-001]** Vista inicial al ingresar al sistema

**Dado** que el estudiante ha iniciado sesión,  
**Cuando** accede al sistema,  
**Entonces** debería visualizar un banner con la siguiente información:

- Logo de la Universidad de las Américas
- Nombre y NRC del curso al que pertenece
- Mensaje de saludo con su nombre completo
- Opción para cerrar sesión  

**Y** debería ver accesos visibles a las funcionalidades principales en el menú principal:

- **Asignaciones**
    - [Tareas](US-003-display-student-tasks)
    - [Evaluaciones](US-004-display-student-lessons)
- **Nueva partida**
    - [Normal](US-005-display-game-loader)
    - [Tutorial](US-005-display-game-loader)
- [**Progreso**](US-006-display-attempt-stats)  

**Y** debería visualizar la ventana de tareas como vista por defecto

---

#### **Escenario [SC-002]** Navegación hacia la ventana de tareas

**Dado** que el estudiante ha accedido al sistema,  
**Cuando** selecciona la opción [Tareas](US-003-display-student-tasks) en el menú principal,  
**Entonces** debería ser redirigido a la pantalla de tareas

---

#### **Escenario [SC-003]** Navegación hacia la ventana de evaluaciones

**Dado** que David ha accedido al sistema,  
**Cuando** selecciona la opción *"Evaluaciones"*,  
**Entonces** debería ser redirigido a la pantalla de evaluaciones

---

#### **Escenario [SC-004]** Navegación hacia la funcionalidad *"Progreso"*

**Dado** que David ha accedido al sistema,  
**Cuando** selecciona la opción *"Progreso"*,  
**Entonces** debería ser redirigido a la pantalla de progreso

---

#### **Escenario [SC-005]** Visualización de las subopciones dentro de la opción *"Nueva partida"*

**Dado** que David ha accedido al sistema,  
**Cuando** selecciona la opción *"Nueva partida"*,  
**Entonces** debería visualizar las opciones:

- Normal
- Tutorial

---

#### **Escenario [SC-006]** Inicio de una nueva *"Partida normal"*

**Dado** que David ha accedido al sistema,  
**Y** ha seleccionado la funcionalidad *"Nueva partida"*,  
**Cuando** selecciona la opción *"Normal"*,  
**Entonces** debería ser redirigido a la pantalla de inicio de partida normal

---

#### **Escenario [SC-007]** Inicio del *"Tutorial"*

**Dado** que David ha accedido al sistema,  
**Y** ha seleccionado la funcionalidad *"Nueva partida"*,  
**Cuando** selecciona la opción *"Tutorial"*,  
**Entonces** debería ser redirigido a la pantalla de tutorial

---

#### **Escenario [SC-008]** Visualización del loader mientras se carga la información

**Dado** que David ha accedido al sistema,  
**Cuando** el sistema está cargando la información necesaria,  
**Entonces** debería visualizar un indicador de carga (loader)

---

#### **Escenario [SC-009]** Manejo de error cuando no se carga la información

**Dado** que David ha accedido al sistema,  
**Y** ocurre un error al cargar la información,  
**Cuando** el sistema intenta mostrar la información,  
**Entonces** debería visualizar un mensaje de error claro al usuario,  
**Y** debería ofrecer opciones para reintentar la carga o cerrar sesión

---

#### **Escenario [SC-010]** Cerrar sesión

**Dado** que David ha iniciado sesión en el sistema,  
**Cuando** selecciona la opción *"Cerrar sesión"*,  
**Entonces** debería ser desconectado del sistema,  
**Y** debería ser redirigido a la página de inicio de sesión,  
**Y** no debería poder acceder a las funcionalidades sin iniciar sesión nuevamente

---

## Dependencias

### Historias de Usuario Relacionadas

N/A

### Sistemas Externos o APIs

N/A

### Infraestructura Requerida

N/A

---

## Consideraciones Generales

### Consideraciones técnicas

#### Protección de datos sensibles del estudiante

**Información del estudiante:**

- Nombre completo
- NRC (Número de Referencia de Curso)

**Información de la asignatura:**

- Nombre del curso: "Introducción al Marketing I"
- Semestre académico actual (ejemplo: 2025-20)

Para cumplir con la Ley Orgánica de Protección de Datos Personales del Ecuador (2021), Se utilizará protocolo HTTPS y JSON Web Token para la comunicación entre cliente y servidor, garantizando la confidencialidad de la información desde su captura hasta su almacenamiento. Adicionalmente la sesión se cerrará automáticamente después de cinco minutos de inactividad.

---

### Consideraciones UI/UX

#### Responsividad

La interfaz se adaptará a pantallas de escritorio con un ancho mínimo de 1025px.

#### Textos y ayudas

- Modo Tutorial: "Aprende el funcionamiento básico del videojuego con un escenario que abarca el tema de conducta del consumidor con guías paso a paso."
- Modo Normal: "Practica libremente en escenarios aleatorios de mercado."
- Asignaciones: "Completa tareas personalizadas asignadas por tu docente."
- Evaluaciones: "Demuestra tu conocimiento en evaluaciones con un solo intento."
- Progreso: "Revisa tu historial de partidas y tendencias de aprendizaje."

#### Navegadores compatibles

<!-- TODO: Revisar si esto hay que corregir -->

- Google Chrome (versión 120 o superior)
- Mozilla Firefox (versión 115 o superior)
- Microsoft Edge (versión 120 o superior)
- Safari (versión 17 o superior)

#### Accesibilidad

N/A

#### Escalabilidad

La funcionalidad debe soportar hasta 90 usuarios concurrentes.

#### Rendimiento

El tiempo de carga de la página no debe exceder los 3 segundos, y las respuestas de la API no deben superar los 10 segundos.

#### Referencias de diseño

[Enlace a Figma](https://www.figma.com/design/EtoLWsngop0Z2B179Mah36/MarkenX?node-id=0-1&p=f&t=goa0pm7wX0M8Lh1N-0)

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
