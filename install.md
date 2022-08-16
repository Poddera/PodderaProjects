La versión 3.x de Poddera Software corre en Tomcat9.

## Resumen de la instalación

Para instalar Poddera Software puede seguir los siguientes pasos:

1 - instale la ultima versión liberada de Open JDK 11<br/>
2 - descargue e instale la última versión liberada de Tomcat 9<br/>
3 - instale u obtenga los datos de conexión para **MySQL 8.x**.<br/>
4 - instale Poddera V3.x.<br/>
5 - consiga las claves de activación y configure los accesos<br/>
6 - compruebe que la versión está operativa.<br/>
<br/>

## 1 - Versión de Java:
Sugerimos ejecutar en producción con la última versión de [OpenJDK 11](https://jdk.java.net/java-se-ri/11). <br/>
( aquí el link para descargar [11+28](https://download.java.net/openjdk/jdk11/ri/openjdk-11+28_linux-x64_bin.tar.gz) para Linux )<br/>
<br/>
Si lo desea puede utilizar Oracle JDK 11.<br>
<br/>
Para Ubuntu server puede instalar el jdk con la instrucción:<br>
`sudo apt install default-jdk`<br/>
Compruebe que la versión instalada está operativa:<br/>
`$ java -version`
<br/>
<br>
## 2 - Tomcat 9:
Puede ir a la página de [Apache Tomcat](https://tomcat.apache.org/download-90.cgi) para descargar tomcat9 para su sistema operativo.<br/>
Una vez descargado y deszipeado, sugerimos borre todas las aplicaciones que vienen por defecto (carpeta webapps)<br/>
<br/>
Por razones de seguridad, Tomcat se debe ejecutar con un usuario sin privilegios de administrador. Para crear un usuario adecuado, puede hacerlo con la siguiente instrucción:<br>
`sudo useradd -m -d /opt/tomcat -U -s /bin/false tomcat`<br/>
<br/>
## 3 - MySQL
La vesión sugerida de MySQL es la 8.x. Descargue la versión community mas nueva.<br/>
<br/>
Cree un usuario y un password y una base de datos. Puede ponerle el nombre que le resulte mas conveniente pero utilice solamente letras sin acentos y guión bajo.<br/>
<br/>
Importante: el default charset aconsejamos ponerlo en utf8mb4.<br/>
<br/>
## 4 - Instalación de Poddera Grants
Junto con su factura se le habrá entregado un número de cliente, una clave de instalación y un link para la descarga de la última versión de Poddera Grants y los diferentes módulos adquiridos.<br/>
<br/>
La aplicación es un zip que deberá descomprimir y colocar en la carpeta webaapps de Tomcat 9.<br/>
<br/>
### Configuración del esquema de datos
Edite el fichero persistence-mysql-PRODUCCION.properties que encontrará en la carpeta WEB-INF/classes y coloque allí los datos para la configuración de su MySQL:<br/>
- Puerto<br/>
- Nombre del esquema<br/>
- Zona horaria (recomendamos UTC para evitar problemas con los cambios de verano)<br/>
- usuario y password<br/>
<br/>
Si tiene un cliente mysql o desde la misma terminal puede comprobar las claves de conexión<br/>
<br/>
### Configuración de la aplicación
La aplicación tiene varias propiedades que identifican la URI de la aplicación instalada tanto para navegaciones automáticas, como para armar los email y notificaciones automáticas, y otra operativa.<br/>
Todas estas propiedades debera dejarlas con el nombre correcto de la aplicación.<br/>
A continuación se listan las mismas:<br/>
<br/>

application.public.url=http://192.168.1.34:8080/p3_web<br/>
application.customer.url=http://localhost:8080/p3_web<br/>
application.internal.url=http://localhost:8080/p3_web<br/>
application.name=p3_web<br/>
<br/>
ws.task.remote.access.url=http://localhost:8080/p3_web/tws<br/>

## datos del WS de login
ws.dao.url=http://localhost:8080/p3_web/ws/rt/<br/>
ws.default.login=login/<br/>
<br/>
## url para consumir WS de task
ws.sp.remote.access.url=http://localhost:8080/p3_web/gws<br/>

## url para consumir WS de forms
ws.form.remote.access.url=http://localhost:8080/sp_form_web/fws<br/>

## URL para llamar a los WebServices de beebpm para realizar los procesos de workflow
ws.beebpm.remote.access.url=http://localhost:8080/bee_bpm_web/rest<br/>

ws.notification.remote.access.url=http://localhost:8080/p3_web/wss<br/>

ws.spring.sp.remote.access.url=http://localhost:8080/p3_web/wss<br/>
ws.portal.nt.remote.access.url=http://pendienteConfigurar<br/>
ws.portal.attachment.remote.access.url=http://pendienteConfigurar<br/>


### editores rich text - interno
ckeditor.url.path=http://localhost:8080/p3_web/resources/webeditor/<br/>

### configuración de Beeblos (si se usa)
beeblos.repository.protocol=http<br/>
beeblos.repository.ip=beeblossp.poddera.com<br/>
beeblos.repository.port=80<br/>

## 6 - Comprobar que la aplicación está operativa
Compruebe que ha dado al tomcar como mínimo 4gb de memoria para funcionar<br/>
<br/>
Arranque tomcat y compruebe la consola. Si todo va bien y no se lanzan excepciones, abra un navegador y navege a la URL que ha definido / aplicación.<br/>
<br/>
Deería aparecerle la pantalla de login.<br/>
Pruebe a ingresar con el usuario usrgeneric / Z3n0t32012 (usuario y clave por defecto para comprobar el funcionamiento)<br/>
<br/>
Si ingresa, todo estará correcto. Si no ingresa, por favor contacte a soporte técnico de Poddera: support@poddera.com<br/>
<br/>
<br/>
