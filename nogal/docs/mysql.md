# Nogal v1.0
*the most simple PHP Framework* by hytcom.net
___
  

# mysql
## nglDBMySQL *extends* nglStd [instanciable] [20160201]
Gestiona conexciones con bases de datos MySQL
  
## Variables
`private` $link = Puntero  
`private` $vModes = Modos de INSERT y UPDATE  

## Argumentos
|Argumento|Tipo|Default|Descripción|
|---|---|---|---|
|**autoconn**|boolean|false|Cuando es TRUE, ejecuta el método connect luego de crear el objeto. Sólo usar en TRUE cuando se utilicen archivos .conf|
|**base**|string|null|Nombre de la base de datos|
|**charset**|string|utf8|Juego de caracteres con el que se ejecutarán las consultas|
|**check_colnames**|boolean|true|Activa el chequeo de los nombre de las columnas en la tabla activa|
|**debug**|boolean|false|Cuando es TRUE el método retorna la sentencia SQL en lugar de ejecutarla|
|**do**|boolean|false|Cuando es TRUE el método query ejecuta la sentencia pero no retorna resultado|
|**error_description**|boolean|false|Ante un error mostrará la descripción del mismo|
|**error_query**|boolean|false|Ante un error mostrará la consulta que le dió origen|
|**host**|string|127.0.0.1|Puede ser o un nombre de host o una dirección IP. Pasando el valor NULL o la cadena "localhost" se asumirá el host local|
|**insert_mode**|string|INSERT|tipo de modo INSERT. Valores admitidos:<ul><li>**INSERT** =  inserta nuevos registros</li><li>**REPLACE** =  si el nuevo registro duplica un valor PRIMARY KEY o UNIQUE, el antiguo registro es eliminado</li><li>**IGNORE** =  el comando no aborta incluso si ocurren errores durante la ejecución</li></ul>|
|**jsql**|mixed|null|Sentencia SQL en formato JSON o Array:<ul><li>columns</li><li>tables</li><li>where</li><li>group</li><li>having</li><li>order</li><li>offset</li><li>limit</li></ul>|
|**jsql_eol**|string||Salto de linea luego de cada parte de la sentencia|
|**pass**|string||Contraseña para acceder a la base de datos|
|**port**|int|null|Puerto donde escucha el servidor MySQL|
|**socket**|string|null|Especifica el socket o la tubería con nombre que debería usarse|
|**sql**|string|null|Ultima sentencia SQL ejecutada o próxima a ejecutarse|
|**table**|string|null|Nombre de la tabla activa en los métodos INSERT y UPDATE|
|**update_mode**|string|UPDATE|tipo de modo UPDATE. Valores admitidos:<ul><li>**UPDATE** =  actualiza los registros especificados</li><li>**REPLACE** =  crea un nuevo registro en caso de no hallar el registro especificados</li><li>**IGNORE** =  el comando no aborta incluso si ocurren errores durante la ejecución</li></ul>|
|**user**|string|root|Nombre de usuario para acceder a la base de datos|
|**values**|string|null|Datos enviados a los métodos INSERT y UPDATE. Valores admitidos:<ul><li>**array asociativo** =  donde cada clave es el nombre del campo en la tabla</li><li>**cadena de variables** =  con el mismo formato que las pasadas por medio de una URL. El valor será analizado utilizando **parse_str**</li></ul>|
|**where**|string|null|Cadena que representa una condición SQL WHERE|

  
&nbsp;

# Métodos
- [Error](#Error)
- [PrepareValues](#PrepareValues)
- [close](#close)
- [connect](#connect)
- [destroy](#destroy)
- [escape](#escape)
- [exec](#exec)
- [insert](#insert)
- [jsqlParser](#jsqlParser)
- [mexec](#mexec)
- [mquery](#mquery)
- [query](#query)
- [update](#update)

  
&nbsp;


## close
Finaliza la conexión con la base de datos  

**[boolean]** =  *public* function ( );
  

&nbsp;
___
&nbsp;

## connect
Establece la conexión con la base de datos  

**[$this]** =  *public* function ( *string* \$sBase, *string* \$sPass, *string* \$nFlags );  

|Argumento|Tipo|Default|Descripción|
|---|---|---|---|
|**\$sBase**|string|null|Nombre de la base de datos|
|**\$sPass**|string||Contraseña para acceder a la base de datos|
|**\$nFlags**|string|argument::flags||

&nbsp;
___
&nbsp;

## destroy
Cierra la conexión y destruye el objeto  

**[boolean]** =  *public* function ( );
  

&nbsp;
___
&nbsp;

## Error
Muestra el mensaje de Error generado por el fallo más reciente  

**[mixed]** =  *private* function ( );
  

&nbsp;
___
&nbsp;

## escape
Escapa un valor para ser incluído de manera segura en una sentencia SQL  

**[mixed]** =  *public* function ( *string* \$mValues );  

|Argumento|Tipo|Default|Descripción|
|---|---|---|---|
|**\$mValues**|string|null|Datos enviados a los métodos INSERT y UPDATE. Valores admitidos:<ul><li>**array asociativo** =  donde cada clave es el nombre del campo en la tabla</li><li>**cadena de variables** =  con el mismo formato que las pasadas por medio de una URL. El valor será analizado utilizando **parse_str**</li></ul>|

&nbsp;
___
&nbsp;

## exec
Ejecuta una sentencia SQL y retorna un objecto **mysqli_result**  

**[mysqli_result object]** =  *public* function ( *string* \$sQuery );  

|Argumento|Tipo|Default|Descripción|
|---|---|---|---|
|**\$sQuery**|string|null|Ultima sentencia SQL ejecutada o próxima a ejecutarse|

&nbsp;
___
&nbsp;

## insert
Inserta un nuevo registro en una tabla  

**[nglDBMySQLQuery object]** =  *public* function ( *string* \$sTable, *string* \$mValues, *string* \$sMode, *boolean* \$bCheckColumns, *boolean* \$bDO );  

|Argumento|Tipo|Default|Descripción|
|---|---|---|---|
|**\$sTable**|string|null|Nombre de la tabla activa en los métodos INSERT y UPDATE|
|**\$mValues**|string|null|Datos enviados a los métodos INSERT y UPDATE. Valores admitidos:<ul><li>**array asociativo** =  donde cada clave es el nombre del campo en la tabla</li><li>**cadena de variables** =  con el mismo formato que las pasadas por medio de una URL. El valor será analizado utilizando **parse_str**</li></ul>|
|**\$sMode**|string|INSERT|tipo de modo INSERT. Valores admitidos:<ul><li>**INSERT** =  inserta nuevos registros</li><li>**REPLACE** =  si el nuevo registro duplica un valor PRIMARY KEY o UNIQUE, el antiguo registro es eliminado</li><li>**IGNORE** =  el comando no aborta incluso si ocurren errores durante la ejecución</li></ul>|
|**\$bCheckColumns**|boolean|true|Activa el chequeo de los nombre de las columnas en la tabla activa|
|**\$bDO**|boolean|false|Cuando es TRUE el método query ejecuta la sentencia pero no retorna resultado|
### Ejemplos  
#### datos en array  
```php
$foo = $ngl("mysql.foobar");
$foo->base = "test";
$foo->connect();

$data = array("foo"=>"foovalue", "bar"=>"barvalue");
$foo->insert("tablename", $data);
```
#### datos como cadena de variables  
```php
$foo = $ngl("mysql.foobar");
$foo->base = "test";
$foo->connect();

$data="foobar&bar=barvalue"
$foo->insert("tablename", $data, "replace");
```

&nbsp;
___
&nbsp;

## jsqlParser
Convierte una sentencia JSQL y retorna una sentencia SQL  

**[string]** =  *public* function ( *mixed* \$mJSQL, *string* \$sEOL );  

|Argumento|Tipo|Default|Descripción|
|---|---|---|---|
|**\$mJSQL**|mixed|null|Sentencia SQL en formato JSON o Array:<ul><li>columns</li><li>tables</li><li>where</li><li>group</li><li>having</li><li>order</li><li>offset</li><li>limit</li></ul>|
|**\$sEOL**|string||Salto de linea luego de cada parte de la sentencia|

&nbsp;
___
&nbsp;

## mexec
Ejecuta varias sentencias SQL separadas por ; y retorna un array de objectos **mysqli_result**  

**[array]** =  *public* function ( *string* \$sQuery );  

|Argumento|Tipo|Default|Descripción|
|---|---|---|---|
|**\$sQuery**|string|null|Ultima sentencia SQL ejecutada o próxima a ejecutarse|

&nbsp;
___
&nbsp;

## mquery
Ejecuta varias sentencias SQL separadas por ; y retorna un array de objectos **nglDBMySQLQuery**, o TRUE cuando DO esta activo  

**[array OR true]** =  *public* function ( *string* \$sQuery, *boolean* \$bDO );  

|Argumento|Tipo|Default|Descripción|
|---|---|---|---|
|**\$sQuery**|string|null|Ultima sentencia SQL ejecutada o próxima a ejecutarse|
|**\$bDO**|boolean|false|Cuando es TRUE el método query ejecuta la sentencia pero no retorna resultado|

&nbsp;
___
&nbsp;

## PrepareValues
Auxiliar de los métodos **insert** y **update**.
Prepara el **array asociativo** o la **cadena de variables** para ser utilizados en las sentencias.
Cuando los valores sean pasados como una **cadena de variables** estos serán tratados con **escape** para garantizar la seguridad del comando SQL.  

**[mysqli_result object]** =  *private* function ( *string* \$sType, *string* \$sTable, *mixed* \$mValues, *boolean* \$bCheckColumns );  

|Argumento|Tipo|Default|Descripción|
|---|---|---|---|
|**\$sType**|string||Tipo de operación, INSERT o UPDATE|
|**\$sTable**|string||Nombre de la tabla|
|**\$mValues**|mixed||Datos en forma de array asociativo o cadena de variables|
|**\$bCheckColumns**|boolean|true|Activa el chequeo de columnas en la tabla|

&nbsp;
___
&nbsp;

## query
Ejecuta una sentencia SQL y retorna un objecto **nglDBMySQLQuery**  

**[nglDBMySQLQuery object]** =  *public* function ( *string* \$sQuery, *boolean* \$bDO );  

|Argumento|Tipo|Default|Descripción|
|---|---|---|---|
|**\$sQuery**|string|null|Ultima sentencia SQL ejecutada o próxima a ejecutarse|
|**\$bDO**|boolean|false|Cuando es TRUE el método query ejecuta la sentencia pero no retorna resultado|
### Ejemplos  
#### conexión  
```php
$foo = $ngl("mysql.foobar");
$foo->base = "test";
$foo->connect();
$bar = $foo->query("SELECT * FROM `users`");
```

&nbsp;
___
&nbsp;

## update
Actualiza todos los registros que cumplan con la condición **\$sWhere**  

**[nglDBMySQLQuery object]** =  *public* function ( *string* \$sTable, *string* \$mValues, *string* \$sWhere, *string* \$sMode, *boolean* \$bCheckColumns, *boolean* \$bDO );  

|Argumento|Tipo|Default|Descripción|
|---|---|---|---|
|**\$sTable**|string|null|Nombre de la tabla activa en los métodos INSERT y UPDATE|
|**\$mValues**|string|null|Datos enviados a los métodos INSERT y UPDATE. Valores admitidos:<ul><li>**array asociativo** =  donde cada clave es el nombre del campo en la tabla</li><li>**cadena de variables** =  con el mismo formato que las pasadas por medio de una URL. El valor será analizado utilizando **parse_str**</li></ul>|
|**\$sWhere**|string|null|Cadena que representa una condición SQL WHERE|
|**\$sMode**|string|UPDATE|tipo de modo UPDATE. Valores admitidos:<ul><li>**UPDATE** =  actualiza los registros especificados</li><li>**REPLACE** =  crea un nuevo registro en caso de no hallar el registro especificados</li><li>**IGNORE** =  el comando no aborta incluso si ocurren errores durante la ejecución</li></ul>|
|**\$bCheckColumns**|boolean|true|Activa el chequeo de los nombre de las columnas en la tabla activa|
|**\$bDO**|boolean|false|Cuando es TRUE el método query ejecuta la sentencia pero no retorna resultado|
### Ejemplos  
#### datos en array  
```php
$foo = $ngl("mysql.foobar");
$foo->base = "test";
$foo->connect();

$data = array("foo"=>"foovalue", "bar"=>"barvalue");
$foo->update("tablename", $data, "`id`='7'");
```
#### datos como cadena de variables  
```php
$foo = $ngl("mysql.foobar");
$foo->base = "test";
$foo->connect();

$data="foobar&bar=barvalue"
$foo->update("tablename", $data, "`id`='7'", "ignore");
```

&nbsp;
___
&nbsp;