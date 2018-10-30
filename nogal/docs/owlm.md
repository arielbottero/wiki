# owlm
Owl Manager es la herramienta por medio de la cual se crea y mantiene la estructura de base de datos (para MySQSL) del objeto [owl](https://github.com/arielbottero/wiki/blob/master/nogal/docs/owl.md)
___

## Variables
|Argumento|Tipo|Descripción|
|---|---|---|
|**$owl**|private|Objeto [owl](https://github.com/arielbottero/wiki/blob/master/nogal/docs/owl.md)|
|**$aTypes**|private|Tipos de campos predefinidos|
|**$bUpdate**|private|Indicador de modificación|
|**$aAdd**|private|Array de datos de agregado de la siguiente actualización|
|**$bAlterField**|private|Indicador de modificación de campo|
|**$aAlterTable**|private|Array de tablas que seran modificadas|
|**$aAlterField**|private|Array de campos que seran modificados|

## Argumentos
|Argumento|Tipo|Default|Descripción|
|---|---|---|---|
|**after**|boolean|true|Nombre del campo después del cual se agregará el nuevo campo. Usar true para agregar al final|
|**core**|boolean|false|Indica si se deben agregar las sentencias para las creación de las tablas de control|
|**db**|string|null|Objeto [mysql](https://github.com/arielbottero/wiki/blob/master/nogal/docs/mysql.md)|
|**structure**|string|null|Estructura owl en formato JSON o Array|
|**newname**|string|null|Nombre de la nueva tabla|
|**select**|string|null|Selecciona el objeto como activo|
|**preset**|string|null|Añade un objeto preseteado a la estructura|
|**type**|mixed|null|Define el tipo de campo que se quiere agregar|
|**field**|string|null|Nombre del campo que se quiere agregar|
|**entity**|string|null|Chequea si el valor es una tabla o view de la estructura|
|**title**|string|null|Define el título de una tabla visible en la interfaz gráfica|
|**fields**|string|null|Array de campos de una nueva tabla o view|
|**run**|boolean|false|Indica si el método [generate](#generate) debe ejecutar las sentencias en la base|

# Métodos
|Método|Descripción|
|---|---|
|[add](#add)|Añade un campo al objeto actual|
|[alter](#alter)|xxx|
|[check](#check)|xxx|
|[chtitle](#chtitle)|xxx|
|[create](#create)|xxx|
|[describe](#describe)|xxx|
|[describeall](#describeall)|xxx|
|[drop](#drop)|xxx|
|[duplicate](#duplicate)|xxx|
|[generate](#generate)|xxx|
|[load](#load)|xxx|
|[join](#join)|xxx|
|[presets](#presets)|xxx|
|[rem](#rem)|xxx|
|[rename](#rename)|xxx|
|[save](#save)|xxx|
|[types](#types)|xxx|
|[view](#view)|xxx|
|Internos||
|[CheckJoins](#checkjoins)|xxx|
|[CreateStructure](#createstructure)|xxx|
|[DefJoins](#defjoins)|xxx|
|[DescribeColumns](#describecolumns)|xxx|
|[FieldDef](#fielddef)|xxx|
|[MakePreset](#makepreset)|xxx|
|[SetObject](#setobject)|xxx|

# Definición de Campo
Cuando se agreguen o modifique campos, los mismos deberán estar definidos según:

- **type** = Tipo de campo
	- BIGINT
	- BINARY
	- BIT
	- BLOB
	- BOOL
	- CHAR
	- DATE
	- DATETIME
	- DECIMAL
	- DOUBLE
	- ENUM
	- FLOAT
	- INT
	- LONGBLOB
	- LONGTEXT
	- MEDIUMBLOB
	- MEDIUMINT
	- MEDIUMTEXT
	- SET
	- SMALLINT
	- TEXT
	- TIME
	- TIMESTAMP
	- TINYBLOB
	- TINYINT
	- TINYTEXT
	- VARBINARY
	- VARCHAR
	- YEAR
- **length** = longuitud del campo, puede estar vacio para los tipo INT ó set de datos entecomillados para los tipos SET y ENUM
- **default** = valor por defecto
	- VALOR
	- NONE
	- NULL
	- CURRENT_TIMESTAMP
- **attrs** = atributos especiales segun el tipo de campo
    - -- (vacio)
    - BINARY
	- UNSIGNED
	- UNSIGNED ZEROFILL
	- ON UPDATE CURRENT_TIMESTAMP
- **index** = indica que el campo es índice y de que tipo
	- -- (no es índice)
    - INDEX
	- UNIQUE
	- FULLTEXT
- **null** = indica si el campo acepta datos NULL
	- TRUE
	- FALSE

&nbsp;

## add
> Añade un campo al objeto actual

**[$this]** =  *public* function ( *string* $sField, *mixed* $mType, *string* $sAfter );  

|Argumento|Tipo|Default|Descripción|
|---|---|---|---|
|**$sField**|string|*arg::field*|Nombre del campo|
|**$mType**|mixed|*arg::type*|Define el tipo de campo:  
<ul>
	<li>**array** = con los parámetros del campo</li>
</ul>
|
|**$sAfter**|string|*arg::after*|Nombre del campo después del cual se agregará el nuevo campo. Usar **true** para agregar al final|
### Ejemplos
Chequea los siguientes permisos sobre el usuario
```php
$chks = $alvin->analize("BUYING.DELETE,BUYING.ADD,BUYING.EDIT,USER.EDIT");
print_r($chks);

#retornará
Array (
	[BUYING.DELETE] => false
	[BUYING.ADD] => true
	[BUYING.EDIT] => true
	[USER.EDIT] => false
);
```

&nbsp;
___
&nbsp;

# Internos
## MakeGroup
> Auxiliar de [grants](#grants). Crea los grupos y perfiles

**[array]** =  *public* function ( *array* $aData, *string* $sType );  

|Argumento|Tipo|Default|Descripción|
|---|---|---|---|
|**$aData**|array||Array de permisos|

&nbsp;
___
<sub><b>nogal</b> - <em>the most simple PHP Framework</em></sub><br />
<sup>&copy; 2018 by <a href="http://hytcom.net/nogal">hytcom.net/nogal</a> - <a href="https://github.com/arielbottero">@arielbottero</a></sup><br />