# Planificación - Tarea 1: Creación y manejo de VLANs

**Curso:** 0975 - Redes de Computadoras 2  
**Duración estimada indicada:** 2 horas  
**Fecha de asignación:** 25-07-2026  
**Fecha de entrega:** 31-07-2026  
**Entregables:** archivo `.pkt` funcional y reporte `.pdf`, sin comprimir

---

## 1. Propósito de la planificación

Esta guía organiza la actividad en fases secuenciales para reducir errores, facilitar la validación y asegurar que cada criterio de la rúbrica tenga evidencia en el reporte. La planificación separa el diseño, la implementación, la verificación y la documentación porque cada etapa depende de la anterior.

La solución se construirá primero en papel o en una tabla, luego en Cisco Packet Tracer y finalmente se documentará. Esta secuencia evita configurar puertos sin una distribución definida y evita redactar un reporte antes de conocer los resultados reales.

## 2. Resultado esperado

Al finalizar se contará con:

- Una topología funcional con un switch y seis PCs.
- Tres VLANs: Administración, Ventas y Soporte.
- Dos equipos finales por VLAN.
- Puertos de acceso correctamente asignados.
- Direccionamiento IP coherente con cada departamento.
- Evidencias de comandos de verificación.
- Pings exitosos dentro de cada VLAN.
- Evidencia de aislamiento entre VLANs.
- Un archivo `.pkt` funcional.
- Un reporte final convertido a PDF.

## 3. Decisiones técnicas previas

| Decisión | Selección | Razón |
|---|---|---|
| Cantidad de switches | 1 switch Cisco 2960 | Cumple el mínimo solicitado y concentra la práctica en creación de VLANs y puertos de acceso |
| Cantidad de PCs | 6, dos por departamento | Permite comprobar conectividad real dentro de cada VLAN |
| VLAN de Administración | VLAN 10 | Número fácil de identificar y documentar |
| VLAN de Ventas | VLAN 20 | Mantiene una secuencia clara y escalable |
| VLAN de Soporte | VLAN 30 | Mantiene una secuencia clara y escalable |
| Redes IPv4 | `192.168.10.0/24`, `192.168.20.0/24`, `192.168.30.0/24` | Relacionan visualmente cada red con su número de VLAN |
| Enrutamiento inter-VLAN | No incluido | No es un requisito mínimo y permitiría ocultar errores de segmentación si se configura prematuramente |
| Evidencias | Capturas después de validar cada etapa | Evita documentar una configuración incompleta o incorrecta |

## 4. Fases de trabajo

### Fase 1 - Lectura y extracción de requisitos

**Tiempo estimado:** 10 minutos  
**Objetivo:** identificar todos los elementos obligatorios antes de abrir Packet Tracer.

#### Actividades

1. Confirmar los tres departamentos requeridos: Administración, Ventas y Soporte.
2. Identificar los entregables obligatorios: `.pkt` y reporte en PDF.
3. Identificar las evidencias requeridas: topología, tabla de VLANs, puertos, comandos y pings.
4. Revisar la convención obligatoria de nombres.
5. Revisar la rúbrica y convertir cada criterio en una verificación concreta.

#### ¿Por qué se hace primero?

La rúbrica no evalúa únicamente que la red funcione; también evalúa la documentación y el formato de entrega. Extraer estos requisitos al inicio evita terminar una topología funcional pero perder puntos por falta de capturas, tablas o nombres incorrectos.

#### Producto de la fase

- Lista de requisitos.
- Lista de evidencias pendientes.
- Convención de nombres confirmada.

#### Criterio de salida

No avanzar hasta poder responder qué se debe configurar, qué se debe capturar y qué archivos deben entregarse.

---

### Fase 2 - Diseño lógico de la red

**Tiempo estimado:** 15 minutos  
**Objetivo:** definir VLANs, dispositivos, redes IP y puertos antes de implementar.

#### Actividades

1. Definir VLAN 10 para Administración.
2. Definir VLAN 20 para Ventas.
3. Definir VLAN 30 para Soporte.
4. Asignar dos PCs a cada departamento.
5. Crear el plan de direccionamiento IP.
6. Crear la tabla de asignación de puertos.

#### Distribución aprobada

| VLAN | Nombre | Red | Puertos | Equipos |
|---:|---|---|---|---|
| 10 | ADMINISTRACION | `192.168.10.0/24` | `Fa0/1-Fa0/2` | PC-ADMIN-01, PC-ADMIN-02 |
| 20 | VENTAS | `192.168.20.0/24` | `Fa0/3-Fa0/4` | PC-VENTAS-01, PC-VENTAS-02 |
| 30 | SOPORTE | `192.168.30.0/24` | `Fa0/5-Fa0/6` | PC-SOPORTE-01, PC-SOPORTE-02 |

#### ¿Por qué se hace antes de configurar?

La configuración de una VLAN depende del número, nombre, puertos y dispositivos definidos. Diseñar primero reduce comandos repetidos, evita mezclar departamentos y hace que las tablas del reporte coincidan con la topología real.

#### Producto de la fase

- Tabla de VLANs.
- Plan de direccionamiento.
- Tabla de puertos.
- Nombres de dispositivos.

#### Criterio de salida

Cada PC debe tener una VLAN, un puerto, una dirección IP y un nombre únicos.

---

### Fase 3 - Construcción de la topología física

**Tiempo estimado:** 15 minutos  
**Objetivo:** representar en Packet Tracer la estructura diseñada.

#### Actividades

1. Agregar un switch Cisco 2960.
2. Agregar seis PCs.
3. Renombrar el switch como `SW1`.
4. Renombrar las PCs según el departamento.
5. Conectar las PCs con cable de cobre directo.
6. Respetar los puertos definidos en la tabla.
7. Esperar a que todos los enlaces estén activos.

#### ¿Por qué se construye antes de configurar?

La configuración de puertos debe corresponder con conexiones físicas reales. Construir la topología primero permite confirmar que `Fa0/1` realmente conecta con el primer equipo de Administración y evita validar un puerto distinto al esperado.

#### Producto de la fase

- Topología física completa.
- Captura preliminar de la topología.

#### Criterio de salida

Todos los dispositivos deben estar conectados y los enlaces deben mostrarse activos.

---

### Fase 4 - Configuración de dispositivos finales

**Tiempo estimado:** 10 minutos  
**Objetivo:** asignar direccionamiento IP coherente con cada VLAN.

#### Actividades

1. Configurar `192.168.10.11/24` y `192.168.10.12/24` en Administración.
2. Configurar `192.168.20.11/24` y `192.168.20.12/24` en Ventas.
3. Configurar `192.168.30.11/24` y `192.168.30.12/24` en Soporte.
4. Dejar la puerta de enlace vacía.
5. Capturar al menos una configuración IP representativa por departamento.

#### ¿Por qué no se configura puerta de enlace?

La topología base no incluye router ni switch de capa 3. Ingresar una puerta de enlace inexistente no habilitaría comunicación entre VLANs y podría confundir el análisis. La validación se enfoca en comunicación local dentro de cada VLAN.

#### Producto de la fase

- Seis PCs con IP estática.
- Tres capturas de configuración IP.

#### Criterio de salida

No debe existir ninguna IP duplicada y cada equipo debe usar la subred correspondiente a su VLAN.

---

### Fase 5 - Creación de VLANs y asignación de puertos

**Tiempo estimado:** 20 minutos  
**Objetivo:** implementar la segmentación lógica en el switch.

#### Actividades

1. Cambiar el nombre del switch a `SW1`.
2. Crear las VLANs 10, 20 y 30.
3. Asignar nombres descriptivos.
4. Configurar los puertos `Fa0/1-Fa0/6` en modo de acceso.
5. Asignar cada rango de puertos a su VLAN.
6. Activar `spanning-tree portfast` en los puertos de usuario.
7. Guardar la configuración.

#### Orden de configuración

```text
Crear VLANs
      ↓
Configurar rangos de interfaces
      ↓
Definir modo access
      ↓
Asignar VLAN de acceso
      ↓
Guardar configuración
```

#### ¿Por qué se crean primero las VLANs?

Aunque IOS puede aceptar algunos comandos en otro orden, crear primero las VLANs garantiza que existan antes de asociar los puertos. Esto hace la configuración más clara, reduce mensajes inesperados y facilita la revisión con `show vlan brief`.

#### Producto de la fase

- VLANs creadas y nombradas.
- Puertos asociados correctamente.
- Configuración guardada.
- Capturas de los comandos relevantes.

#### Criterio de salida

`show vlan brief` debe mostrar las VLANs 10, 20 y 30 con los puertos esperados.

---

### Fase 6 - Verificación técnica

**Tiempo estimado:** 20 minutos  
**Objetivo:** demostrar que la configuración coincide con el diseño.

#### Actividades

1. Ejecutar `show vlan brief`.
2. Ejecutar `show interfaces status`.
3. Validar al menos un puerto por VLAN con `show interfaces ... switchport`.
4. Ejecutar pings dentro de cada VLAN.
5. Ejecutar al menos un ping entre VLANs.
6. Ejecutar `show mac address-table dynamic` después de generar tráfico.
7. Corregir cualquier diferencia antes de tomar las capturas finales.

#### Orden recomendado de pruebas

1. Verificación de VLANs.
2. Verificación de puertos.
3. Verificación de IPs.
4. Ping dentro de Administración.
5. Ping dentro de Ventas.
6. Ping dentro de Soporte.
7. Ping entre departamentos.
8. Tabla MAC.

#### ¿Por qué se valida en este orden?

Los pings dependen de una configuración correcta de capa 1, capa 2 y capa 3. Revisar primero VLANs y puertos permite detectar errores de segmentación antes de interpretar un fallo de conectividad. La tabla MAC se revisa al final porque necesita tráfico previo para aprender direcciones dinámicas.

#### Resultado esperado

| Validación | Resultado |
|---|---|
| `show vlan brief` | VLANs y puertos correctos |
| `show interfaces status` | `Fa0/1-Fa0/6` conectados |
| Ping dentro de cada VLAN | Exitoso |
| Ping entre VLANs | Fallido por ausencia de enrutamiento |
| Tabla MAC | Entradas dinámicas por VLAN y puerto |

#### Producto de la fase

- Capturas definitivas de comandos.
- Capturas de pings.
- Matriz de resultados completada.

#### Criterio de salida

Todas las pruebas deben coincidir con el resultado esperado o contar con una explicación y corrección documentada.

---

### Fase 7 - Documentación del informe

**Tiempo estimado:** 20 minutos  
**Objetivo:** convertir el trabajo técnico en un reporte verificable y alineado con la rúbrica.

#### Actividades

1. Completar nombre, carné y fecha en `ManualTecnico.md`.
2. Sustituir cada espacio de evidencia con una captura real.
3. Completar la columna de resultados obtenidos.
4. Ajustar el análisis según el comportamiento observado.
5. Verificar que las conclusiones correspondan con las pruebas.
6. Revisar ortografía, títulos y numeración.
7. Convertir el documento a PDF.

#### ¿Por qué se documenta después de validar?

Las capturas y conclusiones deben representar la configuración final. Documentar antes de terminar genera evidencias obsoletas y puede producir diferencias entre las tablas, el archivo `.pkt` y el reporte.

#### Producto de la fase

- Reporte completo con evidencias reales.
- PDF listo para entregar.

#### Criterio de salida

Cada criterio de la rúbrica debe apuntar a una sección o captura del informe.

---

### Fase 8 - Control de calidad y entrega

**Tiempo estimado:** 10 minutos  
**Objetivo:** evitar una pérdida total o parcial de la nota por errores de archivo o formato.

#### Actividades

1. Cerrar y volver a abrir el archivo `.pkt`.
2. Confirmar que la configuración permanece guardada.
3. Abrir el PDF y comprobar que todas las capturas sean legibles.
4. Confirmar que no haya marcadores `[COMPLETAR]` pendientes.
5. Aplicar la convención de nombres requerida.
6. Confirmar que ambos archivos se entreguen por separado.
7. No crear un archivo comprimido.

#### ¿Por qué es una fase independiente?

La guía establece que ambos archivos son obligatorios y que el incumplimiento de la forma de entrega puede impedir la calificación. Una revisión final separada reduce el riesgo de subir una versión incompleta, dañada o mal nombrada.

#### Producto de la fase

- `Tarea1_[CARNÉ]_[NOMBRE].pkt`
- `Tarea1_[CARNÉ]_[NOMBRE].pdf`

#### Criterio de salida

Ambos archivos abren correctamente, tienen el nombre correcto y están listos para subirse sin comprimir.

## 5. Cronograma resumido de dos horas

| Minutos | Fase | Actividad principal | Evidencia o producto |
|---:|---|---|---|
| 0-10 | 1 | Revisar requisitos y rúbrica | Lista de control |
| 10-25 | 2 | Diseñar VLANs, IPs y puertos | Tablas de diseño |
| 25-40 | 3 | Construir la topología | Captura de topología |
| 40-50 | 4 | Configurar IPs | Capturas de IP |
| 50-70 | 5 | Configurar switch y VLANs | Configuración guardada |
| 70-90 | 6 | Ejecutar verificaciones y pings | Capturas finales |
| 90-110 | 7 | Completar el reporte | Documento listo |
| 110-120 | 8 | Revisar nombres y archivos | Entregables finales |

## 6. Dependencias entre fases

```text
Requisitos
    ↓
Diseño lógico
    ↓
Topología física
    ↓
IPs de las PCs
    ↓
VLANs y puertos del switch
    ↓
Validación técnica
    ↓
Documentación
    ↓
Control de calidad y entrega
```

No se recomienda cambiar el orden porque:

- La topología depende del diseño de puertos.
- La validación depende de la configuración.
- Las capturas dependen de una validación exitosa.
- El PDF final depende de capturas y resultados reales.

## 7. Estrategia de captura de evidencias

Para evitar repetir trabajo, las capturas se tomarán únicamente después de comprobar que la configuración es correcta.

| Captura | Momento | Contenido mínimo |
|---:|---|---|
| 1 | Después de construir | Topología completa y nombres de equipos |
| 2-4 | Después de configurar PCs | Una IP por departamento |
| 5 | Durante configuración del switch | Creación y nombres de VLANs |
| 6 | Durante configuración del switch | Asignación de puertos de acceso |
| 7 | Después de configurar | `show vlan brief` |
| 8 | Después de configurar | `show interfaces status` |
| 9 | Después de configurar | Validación de un puerto por VLAN |
| 10 | Después de los pings | Tabla MAC dinámica |
| 11-13 | Durante pruebas | Ping exitoso por departamento |
| 14 | Durante pruebas | Ping fallido entre VLANs |

Cada captura debe mostrar suficiente contexto para identificar el dispositivo, el comando y el resultado. Deben evitarse recortes que oculten la línea del comando o los puertos evaluados.

## 8. Gestión de riesgos

| Riesgo | Impacto | Prevención | Acción correctiva |
|---|---|---|---|
| Puertos asignados a VLAN incorrecta | Pérdida de conectividad y puntos | Usar tabla de puertos y `interface range` | Reasignar y validar con `show vlan brief` |
| IP duplicada | Ping inconsistente | Registrar IPs antes de configurar | Corregir la IP y limpiar/repetir pruebas |
| Capturas incompletas | Reporte no verificable | Usar lista numerada de evidencias | Repetir la captura con comando visible |
| Configuración no guardada | Archivo falla al reabrir | Ejecutar `copy running-config startup-config` | Reconfigurar y volver a guardar |
| Primer ping falla | Interpretación errónea | Repetir el ping por resolución ARP | Capturar el segundo intento |
| Comunicación entre VLANs no funciona | Puede confundirse con error | Definir desde el inicio que no hay enrutamiento | Explicar el aislamiento como resultado esperado |
| Archivo mal nombrado | Puede impedir calificación | Aplicar nombre final en la fase 8 | Renombrar antes de subir |
| Entrega comprimida | Incumplimiento explícito | Subir ambos archivos por separado | Eliminar ZIP y cargar archivos individuales |

## 9. Criterios de aceptación

La tarea se considera terminada únicamente cuando se cumplen todos los puntos siguientes:

- [ ] Existe un switch y al menos seis dispositivos finales.
- [ ] Se representan los tres departamentos solicitados.
- [ ] Las VLANs tienen número y nombre correctos.
- [ ] Cada PC está conectada al puerto planificado.
- [ ] Cada puerto es de acceso y pertenece a la VLAN correcta.
- [ ] Cada PC tiene una IP única en su subred.
- [ ] Los pings internos son exitosos.
- [ ] El aislamiento entre VLANs está comprobado y explicado.
- [ ] Los comandos de verificación están documentados.
- [ ] La tabla MAC contiene entradas dinámicas.
- [ ] El `.pkt` fue guardado y reabierto.
- [ ] El reporte fue convertido a PDF.
- [ ] El PDF incluye todas las capturas requeridas.
- [ ] Los nombres de los archivos cumplen el formato.
- [ ] Los dos archivos se entregarán sin comprimir.

## 10. Relación entre planificación y rúbrica

| Criterio de rúbrica | Fases que lo garantizan | Control principal |
|---|---|---|
| Diseño de topología | 2 y 3 | Tabla de diseño y captura completa |
| Configuración de VLANs | 5 y 6 | `show vlan brief` |
| Asignación de puertos | 2, 5 y 6 | Tabla de puertos y validación de interfaces |
| Verificación | 6 | Comandos y pings |
| Reporte y entrega | 7 y 8 | Lista de evidencias y control de archivos |

## 11. Registro de avance

| Fase | Estado | Hora de inicio | Hora de fin | Observaciones |
|---|---|---|---|---|
| 1. Requisitos | `[Pendiente/En proceso/Completa]` |  |  |  |
| 2. Diseño lógico | `[Pendiente/En proceso/Completa]` |  |  |  |
| 3. Topología física | `[Pendiente/En proceso/Completa]` |  |  |  |
| 4. IPs de las PCs | `[Pendiente/En proceso/Completa]` |  |  |  |
| 5. VLANs y puertos | `[Pendiente/En proceso/Completa]` |  |  |  |
| 6. Verificación | `[Pendiente/En proceso/Completa]` |  |  |  |
| 7. Documentación | `[Pendiente/En proceso/Completa]` |  |  |  |
| 8. Entrega | `[Pendiente/En proceso/Completa]` |  |  |  |

## 12. Convención final de entrega

Reemplazar los marcadores con los datos reales, evitando espacios y caracteres especiales que puedan causar problemas:

```text
Tarea1_[CARNÉ]_[NOMBRE].pkt
Tarea1_[CARNÉ]_[NOMBRE].pdf
```

Ejemplo de estructura, únicamente como referencia:

```text
Tarea1_202600000_NombreApellido.pkt
Tarea1_202600000_NombreApellido.pdf
```

Los archivos deben subirse individualmente, sin empaquetarlos en `.zip`, `.rar` u otro formato comprimido.
