# 📄 Ejercicio – Gestión de Entradas para Micro-Eventos

- **Proyecto:** Gestión de Entradas para Micro-Eventos
- **Integrantes:** Javiera Osorio – Muryel
- **Curso:** Pruebas de Software
- **Profesor(a):** Oscar Reyes
- **Fecha de entrega:** 10/09/2025
- 📎 **Organización en GitHub:** [https://github.com/Pruebas-de-Software-Tareas](https://github.com/Pruebas-de-Software-Tareas)

## 2. Especificación de Requerimientos (Validación)
El enunciado inicial presentaba requisitos generales. Para evitar ambigüedades, definimos lo siguiente:

- **Eventos:** nombre, descripción, fecha, categoría (Charla, Taller, Show), precio de entrada (entero) y cupos disponibles (entero).
- **CRUD:** crear, editar, listar y eliminar eventos.
- **Autenticación:** solo usuarios autenticados pueden gestionar eventos y registrar ventas/devoluciones.
- **Filtrado y búsqueda:** por categoría, nombre o fecha.
- **Reportes:** deben mostrar:
  - Total de eventos registrados
  - Total de cupos disponibles
  - Eventos agotados
- **Ventas y devoluciones:** venta disminuye en 1 los cupos, devolución aumenta en 1.

---

## 3. Aseguramiento del Requerimiento (Verificación)
Para verificar que el sistema cumple lo anterior, aplicamos:
- **Pruebas funcionales manuales** (casos de prueba documentados).
- **Evidencias:** capturas de pantalla del frontend y del flujo de trabajo en GitHub.
- **Ciclos de prueba:** individuales y en conjunto, siguiendo la metodología solicitada.

---

## 4. Organización y Flujo de Trabajo
- **Repositorios:**
  - Frontend (React): [enlace repo frontend]
  - Backend (Java/Python): [enlace repo backend]
  - Ambos bajo una organización en GitHub.

- **Administración de código:**
  - Rama `main` protegida, requiriendo al menos una revisión para hacer merge.
  - El desarrollo se realiza en ramas de features (`feature/nombre-funcionalidad`).
  - Se utilizan Pull Requests (PRs) revisados por el compañero antes de integrar a la rama `develop` o `main`.
  - Notificaciones de commits y PRs integradas con un canal de Slack.

- **Evidencia:**
  - *Ver sección de Anexos para capturas de configuración de ramas, Pull Requests y la integración con Slack.*

---

## 5. Problemas Encontrados y Soluciones
- **Problema 1:** Fallo de conexión entre frontend y backend debido a políticas de origen cruzado.
  - *Solución:* Habilitar CORS (Cross-Origin Resource Sharing) en la configuración del backend.
- **Problema 2:** El filtrado de eventos no actualizaba la vista dinámicamente al cambiar la selección.
  - *Solución:* Implementación correcta de los hooks de estado en React (`useState` y `useEffect`) para que el componente se renderice nuevamente cuando cambien los filtros.
- **Problema 3:** La fecha se guardaba en un formato incorrecto en la base de datos.
  - *Solución:* Estandarizar el formato de fecha (YYYY-MM-DD) tanto en el frontend como en el backend antes de la inserción.

---

## 6. Resumen de Pruebas Realizadas
A continuación, se presenta un resumen de los casos de prueba ejecutados. La evidencia detallada para cada uno se encuentra en la sección de Anexos.

| Id_Test | Caso de Prueba | Resultado Esperado | Veredicto | Evidencia Detallada |
| :--- | :--- | :--- | :--- | :--- |
| **T-01** | Crear un evento con datos válidos | El evento aparece en la lista con un mensaje de éxito. | ✅ Éxito | [Ver Anexo T-01](#T01) |
| **T-02** | Cargar datos de un evento para editarlo | El formulario se llena con la información del evento. | ✅ Éxito | [Ver Anexo T-02](#T02) |
| **T-03** | Actualizar un evento existente | Los cambios se reflejan en la lista con mensaje de éxito. | ✅ Éxito | [Ver Anexo T-03](#T03) |
| **T-04** | Eliminar un evento (confirmando la acción) | El evento desaparece de la lista con mensaje de éxito. | ✅ Éxito | [Ver Anexo T-04](#T04) |
| **T-05** | Intentar crear un evento con un campo obligatorio vacío | El sistema muestra un error y no permite la creación. | ✅ Éxito | [Ver Anexo T-05](#T05) |
| **T-06** | Flujo de trabajo en GitHub (Pull Request y Revisión) | Se sigue el flujo definido de revisión y aprobación. | ✅ Éxito | [Ver Anexo T-06](#T06) |

---

## 7. Conclusiones
- El sistema implementa correctamente los requisitos funcionales definidos para el CRUD de eventos.
- Las validaciones de formulario y el flujo de trabajo colaborativo mediante GitHub y Slack fueron implementados con éxito, asegurando la calidad del código y un desarrollo ordenado.
- El proceso de pruebas manuales permitió identificar y corregir errores críticos antes de una entrega final.
- Trabajo futuro: integrar un framework de pruebas automáticas (ej. Jest para frontend) y configurar un pipeline de CI/CD.

---

## 8. Anexos: Evidencia Detallada

### <a name="T01"></a>Anexo T-01: Creación de Evento
- **Entrada:** Usuario completa todos los campos del formulario con datos válidos y presiona "Crear Evento".
- **Resultados Obtenidos (Evidencia):**
  1. **Formulario Lleno:**
     ![Formulario para crear evento](Pruebas/T1/T1-1.png)
  2. **Resultado Exitoso:**
     ![Evento creado correctamente](Pruebas/T1/T1-2.png)
- **Comentario:** El sistema muestra el mensaje "Evento creado correctamente" y el nuevo evento aparece en la tabla.

### <a name="T02"></a>Anexo T-02: Carga de datos para Edición
- **Entrada:** Usuario hace clic en el botón "Editar" de un evento existente.
- **Resultados Obtenidos (Evidencia):**
  1. **Lista de Eventos:**
     ![Lista antes de editar](Pruebas/T2/T2-1.png)
  2. **Formulario Cargado para Editar:**
     ![Formulario con datos cargados](Pruebas/T2/T2-2.png)
- **Comentario:** El formulario superior se rellena con los datos del evento seleccionado y el botón principal cambia a "Actualizar Evento".

### <a name="T03"></a>Anexo T-03: Actualización de Evento
- **Entrada:** Usuario modifica los datos en el formulario y presiona "Actualizar Evento".
- **Resultados Obtenidos (Evidencia):**
  ![Actualización Exitosa](Pruebas/T3/T3-1.png) 
- **Comentario:** El sistema muestra "Evento actualizado correctamente" y los cambios se reflejan en la tabla.

### <a name="T04"></a>Anexo T-04: Eliminación de Evento
- **Entrada:** Usuario presiona "Eliminar" y luego confirma en el diálogo emergente.
- **Resultados Obtenidos (Evidencia):**
  1. **Diálogo de Confirmación:**
     ![Confirmación de Borrado](Pruebas/T4/T4-1.png)
  2. **Resultado Final:**
     ![Eliminación Exitosa](Pruebas/T4/T4-2.png)
- **Comentario:** El flujo completo funciona, protegiendo contra eliminaciones accidentales y confirmando el éxito de la operación.

### <a name="T05"></a>Anexo T-05: Validación de Campo Obligatorio
- **Entrada:** Usuario intenta crear un evento sin rellenar un campo requerido.
- **Resultado Obtenido (Evidencia):**
  ![Error de Validación](Pruebas/T5/T5-1.png)
- **Comentario:** El navegador impide el envío del formulario y muestra un aviso en el campo requerido, como se esperaba.

### <a name="T06"></a>Anexo T-06: Evidencia de Flujo de Trabajo en GitHub
- **Revisión y Merge de Pull Request:**
  ![Pull Request con Revisión](Pruebas/T6/T6-1-PullRequest.png)
- **Configuración de Protección de Rama `main`:**
  ![Protección de Rama](Pruebas/T6/T6-2-BranchProtection.png)
- **Integración con Slack:**
  ![Notificación en Slack](Pruebas/T6/T6-3-Slack.png)
- **Comentario:** Se evidencia el uso de Pull Requests con revisores asignados, la configuración de ramas protegidas y la notificación automática de acciones en Slack. *(Nota: Deberás agregar tus propias capturas para T6 en una carpeta `Pruebas/T6/`)*.