# Curso FHIR 2023, Recursos - Busquedas - Operaciones #

# Uso de Recursos FHIR #
## Caso de Uso ##

La paciente Olivia Herrera Andrade acude a una cita médica el día 06 de julio de 2023 con los resultados de exámenes de laboratorio solicitados en una cita médica anterior. 
La paciente se atiende con el doctor Franco Moreno Pineda y atiende dentro del Centro Médico Las Aguilas.
El médico inicia la consulta médica a las 17:15 hrs y en el proceso revisa los resultados de exámenes encontrando deficiencia de vitamina D. Con este resultado el médico registra en la ficha el diagnóstico de Deficiencia Vitamina D.
El médico concluye la atención prescribiendo un suplemento vitamínico y exposición solar.

Los datos que se manejan en el contexto de este caso de uso son:
* Olivia Herrera Andrade, RUN: 12.156.874-K, nacionalidad chilena, nacida el 25-01-1980. Reside en calle Los Volcanes, la Union, Región de los Ríos. Vive con su esposo Ismael Carrasco Isla, telefono de contacto +5696457364.
* El Centro Médico Las Águilas se ubica en Avenida Los Ríos 254,  Osorno, Región de los Lagos, teléfono de contacto +5664574900,
* El médico, RUN 11.548.625-8, acreditado en los registros de la Superintendencia de Salud bajo el identificador 112233
* El resultado del exámen 25-hidroxi vitamina D es: 30 nmol/L (12 ng/mL)
* El detalle de la prescripción médica indica 50.000UI colecalciferol, 1 sobre a la semana por 2 meses. El identificador del medicamento es 108943009 de la terminología SnomedCT.
* La codificación del diagnóstico se debe expresar usando la terminologías SnomedCT

# Objetivo: #
Consignar en el sistema informático la atención médica realizada.

## 1. Generar el conjunto mínimo de datos (CMD) ##

## 2. Identificar entidades en la narrativa y contrastar con la especificación ##

## 3. Generar el modelo de recursos ##

