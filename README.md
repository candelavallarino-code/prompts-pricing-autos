## 1. La Tarea Elegida
**Descripción de la tarea:** Redactar un procedimiento guía o instructivo breve para el equipo de Pricing enfocado en la homogenización y mapeo de versiones de vehículos dentro de un mismo modelo (por ejemplo, diferenciar versiones Base, Full, Sport o distintas motorizaciones) para comparar precios de mercado de manera precisa.

---

## 2. Prompt 1: Zero-shot
**Prompt utilizado:**  
Escribí una guía para mapear distintas versiones de autos de un mismo modelo para el área de pricing.

**Respuesta obtenida:**  
GUÍA DE MAPEO Y HOMOLOGACIÓN DE VERSIONES DE VEHÍCULOS (ÁREA DE PRICING)
METODOLOGÍA EN 4 PASOS
PASO 1: NORMALIZACIÓN DE NOMBRES (DATA CLEANSING)
- Estandarizar la nomenclatura mediante un ID o clave única:
  [Marca] + [Modelo] + [Motor] + [Transmisión] + [Nivel de Equipamiento]
- Regla de homologación: Ignorar denominaciones comerciales efímeras o ediciones especiales de bajo volumen, salvo que alteren drásticamente el equipamiento base.
PASO 2: SEGMENTACIÓN TÉCNICA Y TREN MOTRIZ (POWERTRAIN)
Dividir las versiones según componentes mecánicos clave antes de evaluar equipamiento:
- Tipo de Propulsión: Nafta/Gasolina, Diésel, MHEV, HEV, PHEV, EV.
- Rango de Potencia (CV / HP): Entrada (80–110 CV) | Medio (110–150 CV) | Alto (>150 CV).
- Transmisión: Manual vs. Automática (CVT, Convertidor de par, Doble embrague).
- Tracción: 4x2 (FWD/RWD) vs. 4x4 / AWD.
PASO 3: ÁRBOLES DE EQUIPAMIENTO (JERARQUÍA DE VERSIONES)
Evaluar la presencia de atributos clave agrupados en 3 pilares:
1. Seguridad:
   - Cantidad de Airbags (2, 6, 7+).
   - Control de Estabilidad (ESP/ESC).
   - Asistencias ADAS (Frenado autónomo, control crucero adaptativo, carril).
2. Confort y Tecnología:
   - Climatizador (Manual vs. Automático / Bi-zona).
   - Pantalla Multimedia y conectividad (CarPlay/Android Auto).
   - Tablero (Analógico vs. Digital/Virtual Cockpit).
   - Acceso/Arranque sin llave (Keyless).
3. Estética y Acabados:
   - Tapizados (Tela vs. Cuero/Ecocuero).
   - Llantas (Chapa vs. Aleación 16", 17", 18").
   - Luces (Halógenas vs. LED / Matrix LED).
   - Techo solar / panorámico.
PASO 4: TAXONOMÍA Y NIVELES DE HOMOLOGACIÓN (TRIM LEVEL TAXONOMY)
Clasificar cada versión en uno de los 4 niveles ordinales estándar:

---

## 3. Prompt 2: Role Prompting
**Prompt utilizado:**  
Actúa como un Especialista Senior en Data & Pricing Automotriz. Redactá un instructivo claro, profesional y estructurado para que los analistas del equipo de Pricing puedan mapear y clasificar correctamente las distintas versiones dentro de un mismo modelo de vehículo (nivel de equipamiento, transmisión, motorización, año-modelo), garantizando un cruce de precios de mercado homogéneo y preciso.

**Respuesta obtenida:**  
1. Estructura de Nomenclatura ÚnicaAsegurate de que cada versión registrada siga este formato:[MARCA] [MODELO] | [MOTOR] | [TRANSMISIÓN/TRACCIÓN] | [TRIM] | [AÑO-MODELO]
Ejemplo: Toyota Hilux | 2.8 TDI | AT6 4x4 | SRX | MY20232.
2. Tabla de Clasificación de Equipamiento (Trims)
Asigná la categoría según el nivel de equipamiento dominante:
   Nivel Estándar     |     Ejemplos de Nombre Comercial      |               Equipamiento Clave
   Entry (Base)       |        XL,Live, Trendline, Sense      |   Llantas de chapa, aire manual, pantalla básica
  Mid (Intermedio)    |    XLS, Feel, Comfortline, Advance    |    Llantas aleación, pantalla táctil, sensores
  High (Gama Alta)    |    SRX, Shine, Highline, Exclusive    |        Cuero, ADAS, faros LED, techo solar
    Top / Sport       |    GR-Sport, GTI, Premier, Overland   |  Kit deportivo, máxima potencia, tracción integral

3. Reglas Operativas Rápidas
Transmisión y Tracción: No mezcles versiones manuales con automáticas (+5% a +10% valor) ni 4x2 con 4x4 (+12% a +18% valor).
Año-Modelo (MY) vs. Patentamiento: Mapeá siempre por el Año-Modelo de la ficha técnica (MY), no por la fecha de patentamiento del auto.
Accesorios Postventa: Ignorá agregados de concesionario/usuario (polarizados, estribos, etc.). No cambian la versión.Filtro de Precios: Elimina de la muestra cualquier precio publicado que se desvíe más de un ±15% de la mediana del grupo.
4. Checklist Exprès antes de Validar:
- ¿Están separados los modelos Manuales de los Automáticos?
- ¿Están separadas las versiones 4x2 de las 4x4?
- ¿Asignaste el nivel de Trim correcto según el equipamiento?
- ¿El año corresponde al Año-Modelo (MY) y no solo al patentamiento?
---

## 4. Prompt 3: Chain of Thought
**Prompt utilizado:**  
Razona paso a paso antes de responder: ¿Qué complejidades surgen al diferenciar versiones dentro de un mismo modelo de auto para análisis de precios y qué pasos metodológicos se deben seguir para resolverlo? A partir de ese razonamiento, redacta un instructivo de mapeo para el equipo de pricing. Razona paso a paso antes de responder.

**Respuesta obtenida:**  
ANALISIS INICIAL Y RAZONAMIENTO METODOLOGICO
1- Complejidades al diferenciar versiones dentro de un mismo modelo
Diferenciar versiones (trims, niveles de equipamiento o motorizaciones) dentro de un mismo modelo de vehiculo presenta un reto analitico significativo por las siguientes razones:
- Heterogeneidad en la nomenclatura del fabricante y del mercado: Un mismo vehiculo puede denominarse comercialmente de distintas formas segun el mercado, anio o canal de venta (ejemplo: Highline, TSI, 1.0 Turbo, Automatic). Las fuentes de datos no estructuradas (clasificados, scraping) suelen incluir erratas o abreviaturas inconsistentes.
- Volatilidad del valor por equipamiento y motorizacion: Dos vehiculos del mismo anio y modelo pueden tener un valor de mercado con variaciones significativas (hasta un 30% a 40%) segun el tipo de transmision, motorizacion, traccion (4x2 vs 4x4) o paquetes opcionales (sunroof, asistentes de conduccion, tapizados).
- Inconsistencia en la captura de datos (Ruido): Las publicaciones de vendedores particulares o concesionarios a menudo omiten la version exacta o seleccionan la opcion por defecto en las plataformas, lo que genera contaminacion de datos en la muestra de analisis.
- Cambios de especificacion a lo largo del ciclo de vida (Facelifts y Model Year): Una version X del anio 2020 puede no incluir las mismas prestaciones que la version X del anio 2023, impactando el precio residual y la depreciacion.

2- Pasos metodologicos para resolver la diferenciacion
- Definicion de una Taxonomia Estandar (Jerarquia de Producto):
Establecer una estructura jerarquica clara: Marca -> Modelo -> Generacion/Anios -> Version Estandar -> Motor/Transmision/Traccion.
- Identificacion de Atributos Clave (Diferenciadores de Valor):
Determinar los atributos de mayor elasticidad en precio dentro del segmento (Cilindrada/Motor, Transmision, Tipo de Combustible, Traccion, Nivel de Seguridad/Lujo).
- Proceso de Normalizacion y Limpieza de Texto (Data Cleaning):
Desarrollar algoritmos de coincidencia o reglas de limpieza para estandarizar cadenas de texto (ejemplo: convertir Aut, AT, Automatica en AT).
- Matriz de Imputacion y Fallback:
Crear reglas de negocio para tratar casos con informacion incompleta, asignando versiones probabilisticas basadas en combinacion de motor/transmision o creando una categoria Base/Sin Especificar diferenciada.
- Validacion Cruzada con Datos Oficiales:
Contrastar la base estandarizada con catalogos oficiales del mercado (ejemplo: bases de patentes, camaras automotrices, guias de precios de referencia) para asegurar consistencia.

INSTRUCTIVO DE MAPEO Y ESTANDARIZACION DE VERSIONES
Dirigido a: Equipo de Pricing / Analytics
Objetivo: Establecer un procedimiento sistematico para homogenizar la captura, procesamiento y categorizacion de versiones de vehiculos, asegurando la precision en los modelos de fijacion de precios y valoracion.

ESTRUCTURA JERARQUICA DEL DATO
Todo registro de vehiculo en la base de datos de pricing debe encajar estrictamente en la siguiente estructura:
- Marca: Denominacion oficial (ejemplo: Volkswagen).
- Modelo: Nombre comercial de la linea (ejemplo: Golf).
- Generacion / Ventana temporal: Periodo de fabricacion que comparte plataforma (ejemplo: Golf VII 2015-2020).
- Version Canonica (Standard Trim): Denominacion estandarizada segun catalogo (ejemplo: 1.4 TSI Highline).
- Atributos Tecnicos Esenciales:
     Transmision: Manual (MT) / Automatica (AT).
     Traccion: 4x2 / 4x4 / AWD.
     Combustible / Motorizacion: Nafta, Diesel, Hibrido, Electrico / Cilindrada / Potencia (CV).

PROCEDIMIENTO METODOLOGICO DE MAPEO (PASO A PASO)
Flujo general:
[Datos Brutos / Scraping] -> [Paso 1: Normalizacion de Texto] -> [Paso 2: Extraccion de Atributos] -> [Paso 3: Coincidencia con Catalogo] -> [Paso 4: Control de Calidad / Outliers]

Paso 1: Normalizacion de Texto y Limpieza
- Eliminar caracteres especiales, espacios dobles y convertir todo a mayusculas.
- Aplicar diccionario de sinonimia para atributos comunes:
- Transmision: AUT, AUTOMATICO, AT6, DSG, CVT -> AT
- Transmision: MAN, MANUAL, MT5, MT6 -> MT
- Motor: 1.6L, 1600, 1.6 16V -> 1.6

Paso 2: Extraccion de Atributos Clave
Si la version publicada es ambigua o imprecisa (por ejemplo: "Volkswagen Golf muy bueno"):
- Buscar en la descripcion o en la ficha tecnica los datos de Motor, Caja y Anio.
- Asignar el atributo tecnico correspondiente de forma independiente antes de nombrar la version.
- Separar y estandarizar los tres campos principales:
Motor: Cilindrada y tecnologia (Ejemplo: 1.4 TSI, 1.6, 2.0 TDI).
Transmision: Tipo de caja (Ejemplo: Manual / MT, Automatica / AT).
Traccion: Tipo de traccion (Ejemplo: 4x2, 4x4, AWD).

Paso 3: Regla de Mapeo y Coincidencia con Catalogo Master
- Coincidencia Exacta (Level 1): Si el texto limpio coincide 1:1 con la base master de versiones aprobadas.
- Coincidencia por Regla Logica (Level 2): Si el texto no coincide directamente, reconstruir la version utilizando los atributos extraidos:
- Version Canonica = Motor + Traccion + Nivel de Equipamiento + Caja
- Categorizacion de Incompletos (Level 3 - Fallback): Si faltan datos clave y no pueden inferirse, asignar a la version Base del modelo para ese anio especifico y marcar el registro con Flag de Baja Confianza.

Paso 4: Validacion y Deteccion de Anomalias de Precio
- Analisis de Dispersion: Para un mismo Modelo + Anio + Version Mapeada, calcular la mediana y la desviacion estandar del precio.
- Alertas de Desviacion: Cualquier vehiculo cuyo precio se aleje mas de 2.5 desviaciones estandar de la mediana del grupo de su version asignada debe enviarse a revision manual, ya que podria estar mal mapeado (ejemplo: un modelo de entrada mapeado como tope de gama).

MATRIZ DE DECISIONES RAPIDAS PARA EL ANALISTA
Situacion 1: Version no especificada (ejemplo: "Toyota Corolla 2021")
- Riesgo en Pricing: Infravalorar o sobrevalorar al promediar.
- Accion Requerida: Asignar la version mas vendida (volumen) de ese anio y aplicar flag de incertidumbre.

Situacion 2: Siglas opcionales / Packs (ejemplo: "Pack Premium")
- Riesgo en Pricing: Mapeo duplicado de versiones.
- Accion Requerida: Verificar si el pack modifica el valor en mas del 5%; si no, agrupar dentro de la version canonica mas cercana.

Situacion 3: Nombres comerciales cambiantes (ejemplo: Trendline pasa a Comfort)
- Riesgo en Pricing: Ruptura en series de tiempo de precios.
- Accion Requerida: Mapear contra la jerarquia de equipamiento (Entrada / Medio / Alto) para mantener la continuidad analitica.

---

## 5. Análisis de Resultados
Para la tarea de mapeo y homologación de versiones de autos, la técnica que funcionó mejor fue Chain of Thought (Prompt 3). Al solicitarle al modelo que razonara paso a paso sobre las complejidades del mercado (como la dispersión de precios, la inconsistencia en las nomenclaturas de publicaciones y el ruido en los datos), la respuesta no solo entregó un instructivo estructurado, sino también reglas operativas de limpieza de datos (Data Cleaning), niveles de coincidencia con el catálogo master, validación matemática de outliers y una matriz de decisión ante datos faltantes. Mientras que Role Prompting dio un resumen muy práctico y Zero-shot quedó incompleto, Chain of Thought generó la metodología de pricing más completa, técnica y aplicable al entorno real.
