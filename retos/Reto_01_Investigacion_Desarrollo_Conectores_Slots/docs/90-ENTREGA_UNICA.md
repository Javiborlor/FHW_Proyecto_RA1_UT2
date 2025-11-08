# ENTREGA ÚNICA - Reto 01

> Borrueco_Lorite_Javier_FHW01_Tarea

## Índice

- [Portada](#portada)
- [1. Introducción](#1-introduccion)
- [2. Conectores internos (energía)](#2-conectores-internos-energia)
- [3. Conectores de datos](#3-conectores-de-datos)
- [4. Slots de expansión](#4-slots-de-expansion)
- [5. Conectores externos](#5-conectores-externos)
- [6. Bibliografía](#6-bibliografia)

<a id="portada"></a>

## Portada

# Reto 1 — Investigación_Desarrollo_Conectores_Slots

**Módulo:** Fundamentos de Hardware (ASIR)
**Alumno/a:** Javier Borrueco Lorite
**Curso:** 2025/26

![Portada](../assets/img/00-portada/portada.png "Portada")

<a id="1-introduccion"></a>

## 1. Introducción

Piensa el PC como una **ciudad**:

- **Conectores** = **carreteras y puentes** (energía y datos).
- **Slots** = **parcelas** para ampliar (tarjetas).

Objetivo del reto: **identificar** y **explicar** conectores/slots **actuales** y, si procede, **legacy** aún en uso.

<a id="2-conectores-internos-energia"></a>

## 2. Conectores internos (energía)

# Conector: PCIe 6/8p

**Descripción breve:** Conector auxiliar de alimentación para tarjetas gráficas con interfaz PCI Express que requieren más de la potencia que ofrece la ranura.
**Pines/Carriles/Voltajes/Velocidad:** 6 pines · +12 V (≈ 75 W) / 8 pines · +12 V (≈ 150 W)
**Uso principal:** Suministro extra de energía a tarjetas gráficas de elevado consumo.
**Compatibilidad actual:** Muy alta; muchas fuentes modernas tienen conectores 6+2 para cubrir 6 y 8 pines.

## Identificación física

- Conector rectangular de 6 u 8 contactos (normalmente 6 pines + 2 suplementarios) con clip de sujección; se conecta al cable de la fuente y a la tarjeta gráfica.

## Notas técnicas

- En el conector de 8 pines se utilizan pines de “sense” que informan a la tarjeta gráfica de la disponibilidad del conector completo.
- El estándar indica que el de 6 pines entrega hasta ~75 W y el de 8 pines ~150 W; conectar un 6 pines en un zócalo adecuando la tarjeta necesita los 150 W puede ser inadecuado.

## Fotos

![](assets/20251108_154339_8p.png)

# Conector: 12VHPWR / 12V‑2x6

**Descripción breve:** Conector de alimentación de alta potencia para tarjetas gráficas modernas, capaz de entregar hasta ~600 W por conector.
**Pines/Carriles/Voltajes/Velocidad:** 16 pines (12 de potencia + 4 de señales) · +12 V principal · hasta ~55 A (~600 W).
**Uso principal:** Suministro dedicado de energía a GPUs de gama alta que requieren más de lo que un conector PCIe tradicional 8‑pines puede proporcionar.
**Compatibilidad actual:** Muy alta en GPUs modernas compatibles con el estándar PCI‑SIG / ATX 3.0 / PCIe 5.0, aunque debe comprobarse que la fuente y cable están certificados para esta potencia.

## Identificación física

- Conector rectangular de 16 contactos en dos filas (12 pines para potencia + 4 pines “sense”/señal) en el lado del dispositivo, con clip de fijación. La variante 12V‑2x6 modifica la versión anterior para mayor fiabilidad.

## Notas técnicas

- El estándar 12VHPWR introdujo “pines de sentido” para que la GPU detecte la capacidad de la fuente y limite el consumo.
- La revisión 12V‑2x6 reduce la longitud de los pines de señal (“sense pins”) y alarga los de potencia para mejorar el acoplamiento y prevenir conexiones parciales que pueden conllevar sobrecalentamiento.

## Fotos

![](assets/20251108_154351_Conector_12VHPWR12V2x6.jpg)

# Conector: ATX de 24 pines

**Descripción breve:** Conector principal que alimenta la placa base en sistemas ATX/ATX12V.
**Pines/Carriles/Voltajes/Velocidad:** 24 pines · +3.3V, +5V, +12V
**Uso principal:** Alimentación de la placa base
**Compatibilidad actual:** Alta

## Identificación física

- Bloque rectangular de 24 pines con clip, situado en el borde de la placa base.

## Notas técnicas

- Estándar ATX12V 2.x. No confundir con el EPS de CPU (4/8 pines).

## Fotos

![](assets/20251108_154427_24p.jpeg)

# Conector: EPS de 8 pines (4+4)

**Descripción breve:** Conector auxiliar de 12 V para alimentar la CPU en fuentes de alimentación tipo EPS12V/ATX12V.
**Pines/Carriles/Voltajes/Velocidad:** 8 pines · +12 V (todos los pines suministran +12 V o parte de ellos)
**Uso principal:** Alimentación dedicada de la CPU en placas base de alto rendimiento o servidores.
**Compatibilidad actual:** Alta, especialmente en placas modernas que requieren >144 W para CPU; soporta también versión 4+4 para compatibilidad con conector de 4 pines.

## Identificación física

- Conector rectangular de 8 pines, a menudo dividido en dos bloques de 4 pines (“4+4”) para compatibilidad; usualmente cerca del zócalo CPU en la placa base.

## Notas técnicas

- Estándar EPS12V (ha evolucionado desde ATX12V) y permite mayor corriente al rail de +12 V.
- Los bloques 4+4 permiten uso en placas con conector de 4 pines cuando no se necesita toda la capacidad.

## Fotos

![](assets/20251108_154438_EPS.jpg)

# Conector: SATA Power

**Descripción breve:** Conector de alimentación para unidades de almacenamiento SATA (HDD/SSD/ópticas).
**Pines/Carriles/Voltajes/Velocidad:** 15 pines · +3,3 V, +5 V, +12 V
**Uso principal:** Alimentación de discos y unidades ópticas con interfaz SATA.
**Compatibilidad actual:** Muy alta en sistemas modernos; reemplaza al conector Molex de 4 pines para dispositivos internos SATA.

## Identificación física

- Conector alargado de 15 contactos, tipo «wafer», normalmente unido al cable de alimentación de la fuente, se conecta a la unidad SATA.

## Notas técnicas

- Cada voltaje (+3,3 V, +5 V, +12 V) tiene varios pines en paralelo para mayor corriente; uno de los pines puede usarse para la función PWDIS (Power Disable) en la revisión SATA 3.3.
- Aunque se incluye la línea de +3,3 V, muchos dispositivos SATA no la usan, y adaptadores Molex→SATA que no tienen +3,3 V siguen siendo muy comunes.

## Fotos

![](assets/20251108_154447_SATA_Power.jpg)

<a id="3-conectores-de-datos"></a>

## 3. Conectores de datos

# Conector de datos: SATA

**Descripción breve:** Interfaz de datos en serie para conectar HDD/SSD/unidades ópticas.
**Pines/Carriles/Voltajes/Velocidad:** 7 pines · 1,5/3/6 Gbps (SATA I/II/III)
**Uso principal:** Conexión de almacenamiento interno común.
**Compatibilidad actual:** Alta

## Identificación física

- Conector plano en forma de L; cable delgado de hasta ~1 m de longitud típico.

## Notas técnicas

- Utiliza señal diferencial (dos pares de datos + tres tierras) para menor interferencia.{index=1}
- No lleva alimentación; la unidad obtiene energía a través del conector de alimentación SATA.

## Fotos

![](assets/20251108_155532_SATA.jpg)

# Conector de datos: M.2 (NVMe/SATA)

**Descripción breve:** Formato compacto de conectividad para módulos SSD internos, que puede usar la interfaz SATA o PCIe (NVMe).
**Pines/Carriles/Voltajes/Velocidad:** 67 pines (depende del socket) · soporta SATA hasta ~6 Gbps o PCIe (x2, x4) con velocidades mucho mayores.
**Uso principal:** Conexión de unidades de estado sólido de alto rendimiento en formato pequeño (portátiles, placas base modernas).
**Compatibilidad actual:** Muy alta en equipos recientes; asegurarse de que la ranura soporta SATA o PCIe según el módulo.

## Identificación física

- Tarjeta‑módulo delgada (normalmente 22 mm de ancho), insertada en ranura M.2 en la placa base, con “notch” (muesca) de clave B, M o B+M para indicar compatibilidad.

## Notas técnicas

- El mismo conector M.2 puede soportar diferentes protocolos (SATA, PCIe/NVMe) dependiendo de la ranura.
- Los módulos SATA suelen usar clave B o B+M; los que sólo soportan PCIe/NVMe usan clave M.

## Fotos


![](assets/20251108_155545_M.2.jpg)

<a id="4-slots-de-expansion"></a>

## 4. Slots de expansión

(Pega aquí las fichas finales de esta sección)

<a id="5-conectores-externos"></a>

## 5. Conectores externos

(Pega aquí las fichas finales de esta sección)

<a id="6-bibliografia"></a>

## 6. Bibliografía

(Pega aquí la bibliografía consolidada)
