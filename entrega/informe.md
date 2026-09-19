# Informe Técnico del Taller

## Nombre del Taller
[Taller 6 Normatividad](https://github.com/Esteban7108/AREM-Taller_6_Normatividad)

## Integrantes del equipo
- Esteban Díaz
- Juliana Moreno

## Descripción general del trabajo

El objetivo del taller fue verificar el cumplimiento normativo del sistema del cliente (GobData, un portal estatal de trámites ciudadanos) frente a los marcos de Habeas Data (Ley 1581 de 2012), ISO/IEC 27001, protección contra fugas de datos, y consentimiento/auditoría/roles de acceso. El equipo siguió la metodología de 5 pasos propuesta en la guía del taller: identificar datos sensibles, construir el checklist por categoría, evaluar el cumplimiento de cada ítem, documentar el riesgo de cada brecha detectada y priorizar las recomendaciones correctivas.

## Proceso de desarrollo

Empezamos con la plantilla oficial en blanco (`plantilla_checklist.xlsx`), manteniendo la misma estructura. Primero se listaron los datos y procesos que maneja GobData (identificación, historial clínico, dirección, certificados digitales, trámites) y se asoció cada uno con la normativa que le aplica. Con esa base se construyeron 12 criterios de cumplimiento agrupados en seis categorías, y cada uno se evaluó como **Cumple** o **Parcial**, siempre respaldado por evidencia concreta observada en el sistema (por ejemplo, existencia de política de TI basada en ISO/IEC 27001:2013, o cifrado HTTPS/TLS en tránsito y reposo).

Los 5 ítems marcados como Parcial se llevaron a la hoja de Brechas Identificadas, donde a cada uno se le asignó un nivel de riesgo (Alto, Medio o Bajo) según el impacto de no corregirlo, y una recomendación prioritaria con su nivel de prioridad (Alta o Media). El equipo evitó el error común de confundir "Parcial" con "Brecha": el checklist solo registra el nivel de cumplimiento por ítem, mientras que la hoja de Brechas documenta el riesgo derivado de cada incumplimiento real.

## Análisis del modelo propuesto

El checklist entregado (`checklist-cliente.xlsx`) se estructura en dos hojas complementarias:

- **Checklist General**: 12 criterios de cumplimiento distribuidos en las categorías Consentimiento, Seguridad (ISO 27001), Protección de Datos, Prevención de Fugas, Retención, y Roles y Responsabilidades. De estos, 7 ítems están en estado Cumple y 5 en Parcial.
- **Brechas Identificadas**: las 5 brechas derivadas de los ítems Parcial, con su riesgo y recomendación prioritaria. Dos de ellas (falta de plan de continuidad BCP/DRP y ausencia de controles DLP para exportaciones) quedaron catalogadas como riesgo Alto y prioridad Alta, por lo que deberían atenderse primero.

El modelo representa razonablemente las necesidades de un sistema estatal que procesa datos sensibles de ciudadanos: cubre tanto obligaciones legales directas (Ley 1581, derechos ARCO) como controles técnicos de seguridad de la información (ISO/IEC 27001). Se asumió que GobData ya cuenta con controles básicos de seguridad y protección de datos implementados parcial o totalmente (política de TI, DPO asignado, logs de auditoría), y que las brechas identificadas corresponden a procesos que existen pero no están completamente automatizados o formalizados, más que a ausencias totales de control.


## Tabla de actores, entidades o componentes (si aplica)

| Nombre del elemento | Tipo | Descripción | Responsable |
|---------------------|------|-------------|-------------|
| Ciudadano | Actor | Usuario que realiza trámites de identidad, salud, impuestos y derechos civiles en GobData | Cliente |
| Oficial de Protección de Datos (DPO) | Actor | Responsable de supervisar el cumplimiento de la Ley 1581 dentro del sistema | Cliente |
| Portal de Trámites Ciudadanos | Componente de aplicación | Sistema que procesa datos personales y sensibles de los ciudadanos | Cliente |
| Mecanismo de revocatoria del consentimiento | Constraint (ArchiMate) | Restricción derivada de la Ley 1581 sobre el registro de usuario | Equipo del taller |

## Investigación complementaria

### Tema investigado:
Normativas sectoriales aplicables a un portal estatal de trámites ciudadanos, adicionales a la Ley 1581 e ISO/IEC 27001.

### Resumen:
Además del régimen general de protección de datos personales (Ley 1581 de 2012) y su decreto reglamentario (Decreto 1377 de 2013, que define el procedimiento para ejercer los derechos ARCO), un sistema como GobData que maneja historial clínico ciudadano debe considerar la normativa sectorial de salud vigilada por el Ministerio de Salud y la Superintendencia Nacional de Salud, dado que ese dato tiene tratamiento reforzado por tratarse de un dato sensible.

La Superintendencia de Industria y Comercio (SIC) es la autoridad nacional de protección de datos en Colombia: investiga y sanciona los incumplimientos de la Ley 1581, por lo que cualquier brecha relacionada con consentimiento, revocatoria o anonimización de datos (como las identificadas en este checklist) representa una exposición directa ante esa entidad. En un sistema estatal, además, suele aplicar la normativa del Ministerio de Tecnologías de la Información y las Comunicaciones (MinTIC) sobre gobierno digital y seguridad de la información en entidades públicas, lo cual refuerza la exigencia de una política formal de seguridad basada en ISO/IEC 27001.

## Referencias

Ver [`referencias.md`](referencias.md) para el listado completo de fuentes consultadas.

---

_Este documento hace parte de la entrega del Taller 6 del curso AREM (Arquitectura Empresarial) - Universidad de La Sabana._
