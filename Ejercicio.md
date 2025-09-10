
# 📄 Ejercicio – Gestión de Entradas para Micro-Eventos

## 1. Portada
- **Proyecto:** Gestión de Entradas para Micro-Eventos  
- **Integrantes:** Nombre Apellido – Nombre Apellido  
- **Curso:** [Nombre curso]  
- **Profesor(a):** [Nombre profesor]  
- **Fecha:** [dd/mm/2025]  
- 📎 **Repositorio GitHub:** [Enlace al repo](https://github.com/tu-org/tu-repo)  

---

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
- **Evidencias:** capturas de frontend (navegador) y backend (Postman).  
- **Ciclos de prueba:** individuales y en conjunto, siguiendo la metodología solicitada.  

---

## 4. Organización y Flujo de Trabajo
- **Repositorios:**  
  - Frontend (React): [enlace repo frontend]  
  - Backend (Java/Python): [enlace repo backend]  
  - Ambos bajo una organización en GitHub.  

- **Administración de código:**  
  - Rama `main` protegida, rama `dev` para desarrollo.  
  - Pull requests revisadas por compañero antes de mergear.  
  - Notificaciones de commits y PRs integradas con Slack.  

- **Evidencia:**  
  - Capturas de configuración de ramas.  
  - Captura de integración GitHub–Slack.  

---

## 5. Problemas Encontrados y Soluciones
- **Problema 1:** Fallo de conexión entre frontend y backend.  
  - *Solución:* habilitar CORS en backend.  
- **Problema 2:** Reporte mostraba cupos incorrectos.  
  - *Solución:* ajuste en la consulta SQL/ORM.  
- **Problema 3:** El filtrado no actualizaba dinámicamente.  
  - *Solución:* uso de hooks en React con `useState` y `useEffect`.  

---

## 6. Pruebas Realizadas

| Id_Test | Entrada al sistema | Resultado esperado | Resultado obtenido | Éxito/Fallo | Comentario |
|---------|-------------------|--------------------|--------------------|-------------|------------|
| T1 | Iniciar sesión con credenciales válidas (`admin/1234`) | Acceso permitido → pantalla principal | Acceso exitoso | ✅ Éxito | Evidencia: screenshot |
| T2 | Iniciar sesión con credenciales incorrectas (`admin/xxxx`) | Sistema debe rechazar con mensaje de error | Se muestra mensaje de error | ✅ Éxito | Captura con error |
| T3 | Registrar evento (Charla IA, 20 cupos, $5000) | Evento se muestra en el listado | Evento aparece en lista | ✅ Éxito | Captura evento nuevo |
| T4 | Modificar evento (precio a $6000) | Se actualiza correctamente | Precio actualizado | ✅ Éxito | Captura detalle actualizado |
| T5 | Eliminar evento existente | Evento ya no aparece en lista | Evento eliminado | ✅ Éxito | Captura lista sin evento |
| T6 | Filtrar por categoría “Taller” | Se listan solo talleres | Lista filtrada correctamente | ✅ Éxito | Captura filtro aplicado |
| T7 | Vender entrada en evento con cupos | Cupos disminuyen en 1 | Cupos actualizados | ✅ Éxito | Captura antes/después |
| T8 | Devolver entrada previamente vendida | Cupos aumentan en 1 | Cupos actualizados | ✅ Éxito | Captura antes/después |
| T9 | Generar reporte con varios eventos | Reporte muestra totales y agotados | Reporte generado correctamente | ✅ Éxito | Captura pantalla reporte |
| T10 | Crear evento con cupos = 0 | Evento debe marcarse como “Agotado” | Aparece como agotado | ✅ Éxito | Captura evento agotado |

---

## 7. Conclusiones
- El sistema implementa correctamente los requisitos definidos.  
- Se validaron los flujos principales: login, CRUD de eventos, filtros, reportes, ventas y devoluciones.  
- El control de versiones con GitHub y Slack permitió un flujo ordenado.  
- Trabajo futuro: integrar pruebas automáticas (Jest/Pytest) y despliegue en la nube.  

---

## 8. Anexos
- Screenshots de cada prueba (T1–T10).  
- Evidencias de GitHub (ramas, PRs, commits).  
- Registro de pruebas en **Greentest.ai**.  

---
