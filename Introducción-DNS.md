  DNS
Es una base de datos distribuidos con informacion sobre hosts y servicios. que permite un control local de los segmentos de la base de datos y cada segmento es accesible a toda la red a traves de un esquema 
cliente-servidor. Para la mejora del sistema en robustez y rendimineto se consigue  a traves de caching y replcacion.

Cuando un usuario intenta acceder a un sitio web:
- el navegador busca en la cache si hay una ip que coincide con la busquesda del usuario
-	el servidor DNS puede ser autoritativo o recursivo.
Cuando un usuario registra un dominio, se crea una entrada WHOIS en el registro correspondiente y queda almacenada en el DNS como un resource record.

El ciclo del DNS
usuario quiere visitar una página web
Servidor puede tener o no la ip de la web, si es que no
Recibe otro servidor DNS, y así hasta que un servidor tenga en caché. Y todos los anteriores servidores se van a ir guardando la ip por si mas adelante alguien quiere vovler acceder. (recursivo).

Modelo OSI se encuentra en aplicación, capa 4
Se aplica en UDP utilizando en el puerto 53, no hay comprobación de entrega de los paquetes por lo tanto es más rápido.

Tipos de Servidores
Solucionadores recursivos:
Servidores nombres raíz:
Servidores de nombres TLD:  .com .net .edu es una calificacion por cada uno de los dominio
Servidores de nombres autoritativos: SOA sirve para consultar la definicion de un nombre especifico.

Peticiones de los DNS -->

Recursiva:
El servidor DNS que la recibe siempre devuelve la respuesta.
Si es necesario, hace consultas a otros servidores, que pueden ser recursivas o no.
Para el cliente es muy bueno porque se queda esperando mientras que el servidor recorre todo el árbol DNS.
Para el servidor es malo, porque son costosas y el servidor puede negarse a aceptar ese tipo de consultas.

Iterativa:
El servidor que recibe una petición proporciona la info si la conoce, en caso contrario, indica en qué otro servidor se puede encontrar, o sea, envía una referencia con un RR de
tipo NS con la identidad de otro servidor de nombres “más cercano” a la respuesta. El cliente tendrá que seguir las referencias que, en su caso, le dé el servidor
