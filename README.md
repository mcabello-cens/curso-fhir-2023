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


# Desarrollo: #

## 1. Generar el conjunto mínimo de datos (CMD) ##


<details><summary>Hacer click para ver el CMD</summary>

|	N°	|	Atributo	|	"Requerido Opcional"	|	Descripción	|	Ejemplo	|
|	---	|	---	|	---	|	---	|	---	|
|	1	|	RUN del Paciente	|	R	|	Identificador Nacional de Personas en Chile. El formato se debe especificar con puntos y guion.	|	12.156.874-K	|
|	2	|	Nombre del Paciente	|	R	|	Nombres del Paciente	|	Olivia	|
|	3	|	Apellido Paterno del Paciente	|	R	|	Apellido paterno del paciente	|	Herrera	|
|	4	|	Apellido Materno del Paciente	|	O	|	Apellido materno del paciente, si lo tiene.	|	Andrade	|
|	5	|	Nacionalidad	|	R	|	Nacionalidad de origen del paciente	|	Chilena	|
|	6	|	Fecha nacimiento	|	R	|	Corresponde a fecha de nacimiento que se indica en el certificado de nacimiento. Y el formato sería: YYYY-MM-DD	|	25-01-1980	|
|	7	|	Sexo	|	R	|	Corresponde al sexo que figura en su documento de identificación nacional	|	femenino	|
|	8	|	Dirección	|	R	|	La concatenación completa de la dirección siguiendo el orden Calle, Nro, Comuna, Región	|	Calle Los Volcanes, La Union, Región de Los Ríos	|
|	9	|	Comuna	|	R	|	La comuna en donde reside el paciente	|	La Unión	|
|	10	|	Region	|	R	|	La región asociada a la comuna	|	Región de Los Lagos	|
|	11	|	Contacto de la pareja	|	O	|	Un dato de contacto para contactar al paciente en caso de no lograrlo.	|	Ismael Carrasco Isla, su esposo, Telefono +5696457364	|
|	12	|	Nombre Centro Medico	|	R	|	El nombre del Centro Médico	|		|
|	13	|	Direccion Cento Medico	|	R	|	La concatenación completa de la dirección siguiendo el orden Calle, Nro, Comuna, Región	|	Avenida Los Ríos 254, Osorno, Región de Los Lagos	|
|	14	|	Telefono Centro Médico	|	R	|	Telefono de contacto del Centro Médico	|	5664574900	|
|	15	|	Nombre del Medico	|	R	|	Nombre del Médico	|	Franco	|
|	16	|	Apellido Paterno	|	R	|	Apellido paterno del médico	|	Moreno	|
|	17	|	Apellido Materno	|	O	|	Apellido materno del médico, si lo tiene	|	Pineda	|
|	18	|	Run Medico	|	R	|	Identificador Nacional de Personas en Chile. El formato se debe especificar con puntos y guion.	|	11.548.625-8	|
|	19	|	N° Registro SIS	|	R	|	Identificador de Prestador Individual otorgado por la Superintendencia de Salud	|	112233	|
|	20	|	Fecha atención medica	|	R	|	La fecha en que ocurre la atención médica	|	06-06-2023 17:15	|
|	21	|	Diagnóstico realizado	|	R	|	Glosa del diagnostico. Corresponde a que el médico escribe de puño y letra	|		|
|	22	|	Diagnostico SnomedCT	|	R	|	Codigo y glosa Snomed del diagnostico 	|		|
|	23	|	Nombre de/los examen/es	|	R	|		|		|
|	24	|	Resultados	|	R	|		|		|
|	25	|	Prescripción medicamentos	|	R	|	Codigo y Glosa Snomed del medicamento	|	Colecalciferol 50.000 UI	|
|	26	|	Dosis y vía de administración	|	R	|	Cantidad diaría y por cuanto tiempo se debe ingerir el medicamento y la vía de administración	|	"1 sobre a la semana durante dos meses. 
Vía oral"	|
|	27	|	Otras indicaciones	|	O	|	Otras indicaciones que no requieren medicamentos, por ejemplo, hidratación, masajes, aplicación de algún dispositivo	|	Exposición controlada a rayos UV. 30 mins diarios por la mañana.	|
|	28	|	Fecha de la prescripcion	|	R	|	Fecha en que se emite la prescripción	|		|
|	29	|	Médico que prescribe	|	R	|		|	Franco Moreno Pineda	|

</details>



<details><summary>Mapeo de recursos FHIR</summary>


|	Name	|	Card.	|	Valor	|
|	---	|	---	|	---	|
|	 Patient	|		|		|
|	 identifier	|	1..1	|		|
|	identifier.use	|	1..1	|	official	|
|	identifier.value	|	1..1	|	12.156.874-K	|
|	identifier.system	|	1..1	|	http://registrocivil.cl/personas	|
|	 active	|	1..1	|	true	|
|	 name	|	0..*	|		|
|	name.given	|	1..2	|	Olivia	|
|	name.family	|	1..1	|		|
|	name.extension.fatherFamily	|	1..1	|	Herrera	|
|	name.extension.motherFamily	|	0..1	|	Andrade	|
|	 telecom	|		|		|
|	 gender	|	1..1	|	female	|
|	 birthDate	|	1..1	|	25-01-1980	|
|	 deceased[x]	|		|		|
|	 address	|	1..1	|		|
|	address.use	|	1..1	|	home	|
|	address.type	|	1..1	|	physical	|
|	address.line	|	1..1	|	Los Volcanes 886, La Unión, Región de Los Ríos	|
|	address.city	|	1..1	|	Osorno	|
|	address.district	|		|		|
|	address.state	|	1..1	|	Región de Los Lagos	|
|	 maritalStatus	|		|		|
|	maritalStatus.coding.code	|	1..1	|	M	|
|	maritalStatus.coding.display	|	1..1	|	Married	|
|	maritalStatus.coding.system	|	1..1	|	http://terminology.hl7.org/CodeSystem/v3-MaritalStatus	|
|	 ~~photo~~	|		|		|
|	 contact	|	0..*	|		|
|	contact.relationship.coding.code	|	1..1	|	CP	|
|	contact.relationship.coding.display	|	1..1	|	Contact Person	|
|	contact.relationship.coding.system	|	1..1	|	http://terminology.hl7.org/CodeSystem/v2-0131	|
|	contact.relationship.use	|	1..1	|	official	|
|	contact.name.given	|	1..1	|	Ismael	|
|	contact.name.extension.fatherFamily	|	1..1	|	Carrasco	|
|	contact.name.extension.motherFamily	|	1..1	|	Isla	|
|	contact.telecom.use	|	1..1	|	home	|
|	contact.telecom.system	|	1..1	|	phone	|
|	contact.telecom.value	|	1..1	|	+5696457364	|
|	~~communication~~	|		|		|
|	~~link~~	|		|		|




</details>


## 2. Identificar entidades en la narrativa y contrastar con la especificación ##

* Patient
* Practitioner
* Location
* Encounter
* DiagnosticReport
* Observation
* Bundle de Tipo Transaction


## 3. Generar el modelo de recursos ##

![Modelo de Recursos](https://github.com/mcabello-cens/curso-fhir-2023/blob/main/modelo-clinfhir.png)
