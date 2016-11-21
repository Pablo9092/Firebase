##BASE DE DATOS DOCUMENTACIÓN DE FIREBASE##

**¿Como se estructuran los datos?**

Todos los datos de Firebase Realtime Databaseson almacenados en un árbol JSON el cual esta alojado en la nube.  
Aqui no existen tablas y registros, al agregar un dato este se convierte en un nodo de la estructura JSON existente.  

Se recomienda evitar la anidación ya que cuando tu le das permisos de lectura y escritura a alguien, estas almismo  
tiempo dandole permiso de los decendientes de ese nodo, Firebase restringe esto hasta 32 niveles de profundidad para  
evitar problemas. Compactar ayuda a evitar este tipo de problemas, consiste en manejar datos por separados.  

**Creación de datos que escalan**

Para crear apps, se recomienda descargar un subconjunto de una lista para evitar problemas, mas si se manejan registros  
de miles de elementos. y si la lista es muy grande es mejor anidar. Esto se puede hacer desnormalizando una consulta  
para generar un conjunto de datos.   

**GUARDAR DATOS EN LA WEB**

Métodos para escribir datos en Firebase:


Método | Usos comunes
-- | --
set() | Escribe o reemplaza datos en un ruta de acceso.
push() | Realiza adiciones a una lista de datos. 
update() | Actualiza algunas de las claves de una ruta de acceso de definida sin reemplazar todos los datos.
transaction() | Actualiza datos complejos que pueden dañarse.



Set puede ser usada para guardar datos es una referencíaespecificada. Push nos permite agregar datos a una lista app  
de varios usuarios.  Update nos permite actualizar información inmediatamente. Para eliminar registros se puede hacer  
con remove o especificando el valor null para set y update.  

FirbaseNos permite sincronizar la pp con la nube, ayudando a que incluso sin red el usuario tenga acceso a sus datos.  



**Recupera datos en la Web**

Los datos de Firebase se recuperan adjuntando un receptor asincrónico a una firebase.database.Reference. El receptor se  
activa una vez para el estado inicial de los datos y nuevamente cuando se cambian estos.  

Puedes detectar estos tipos de eventos que recuperan datos:

Evento | Uso típico
-- | --
value |	Lectura y detección de cambios en el contenido de una ruta de acceso.
child_added |	Recuperación de elementos o detección de adiciones en una lista de estos. Se sugiere su uso con child_changed y child_removed para realizar un seguimiento de cambios en las listas.
child_changed |	Detección de cambios en los elementos de una lista. Se usa con child_added ychild_removed para realizar un seguimiento de cambios en las listas.
child_removed 	| Detección de elementos quitados de una lista. Se usa con child_added ychild_changed para realizar un seguimiento de cambios en las listas.
child_moved |	Se usa con datos ordenados para detectar cambios en la prioridad de un elemento




