# PRACTICA-7



A través del formato de ficheros docker-compose.yml, como ya se ha realizado con anterioridad , se configura una estructura servidor-cliente del tipo _BIND9-Alpine Linux_.
De esta forma generaremos un entorno en el cual el servidor puede gestionar consultas de resolución de nombres , bien respondiéndolas o redirigiéndolas a servidores externos mediante la actividad de forwarders.


Los campos que utilizamos a al hora de definir los diferentes servicios son los básicos ya utilizados (_image_, _restart_, _container_ _name_). Destacar en este caso la creación de un subred interna entre los dos contenedores, junto con  la asignación de una dirección IP fija tanto para el cliente como para el servidor . 


En referecia al mapeo de los puertos , tanto para el protocolo UDP como para TCP se concreta en 54:53 (siendo el primero el referenciado al host).


Se generará un volumen vinculando los directorios del huésped con los del contenedor BIND9. De esta manera se solventa el problema de la la falta de permanencia en cuanto a la modificación de los archivos de configuración.


     
     ` - ./bind9:/etc/bind `
     


El directorio bind9 perteneciente el servidor almacena los archivos de  forwarders y de zona entre otros .

Será necesario modificar los dichos archivos  para concretar el entorno según los requisitos.

Especificamos los servidores de consultas externas para el caso de que la consulta al consultante principal no  tenga éxito.Modificamos consecuentemente el archivo _named.conf.options_.

Finalmente se delimitan los  parámetros de zona el _db·example.com_ (siendo el nombre de dominio que se esté utilizando)

Entre otros aspectos se enumeran los registros de los que se quiere obtener información en las consultas al sistema de nombres.



- Con el **SOA**  se define la autoridad del dominio 

- El registro **NS** especifica los servidores encargados de zona 

- Como registro **A** se entiende el que realiza la vinculación con la IP concreta.












     


