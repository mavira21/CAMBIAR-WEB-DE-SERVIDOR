### 1.- Hacer backup de nuestra web  

* En el Administrador de ProcessWire instalar el módulo [ProcessExportProfile](http://modules.processwire.com/modules/process-export-profile/)  

* Ir a  
_CONFIGURACIÓN_ -> Export Site Profile -> _NAME_(site) -> _START EXPORT_ -> _CONTINUE_-> _DOWNLOAD_-> _REMOVE_  

Ir a descargas y guardar nuestro backup.  

### 2.- Desde Putty:  

* Desde home/bitnami poner:  

```
$ sudo ./creaPW.sh miweb dbpass  (dbpass es tu contraseña de bitnami)
```  

### 3.- Desde Cyberduck:  

* Nueva conexión-> conexión segura sftp -> resto de datos para conectar.  
* Ir a home>bitnami>apps>miweb>htdocs>  
* Borrar la _site_ que haya para sustituirlo por el nuestro (backup que acabamos de descargar con el módulo _site profile_)  
* Para ello, arrastrar nuestro site.zip al servidor a la carpeta _htdocs_  
* Descomprimirlo  
* Borrar la copia zip de nuestro site  
* Renombrarlo a site  

### 4.- Ir al Navegador y poner nano.bitnamiapp.com/miweb  

* Aparece el mensaje _GET STARTED_  
* Configurarlo con los datos que nos da Putty después de crear "miweb"  
* **DB Name** miweb  
  **DB User** miweb  
  **DB Pass** la que nos da putty  
  **Default time** EU-Madrid  
  **DB Directories** 755  
  **DB Files** 644  
  **mavira.bitnamiapp.com**  
* _CONTINUE_  
  **Admin Login Url** Admin  
  **User** mavira  
  **Pass** exclusive  
  **Email** gmail  
* _CONTINUE_  
  Dará un error:  _remove.php_  
  Ir a Putty (home->ls->cd..->ls)  
  Desde $apps/miweb/htdocs poner  

```
  sudo rm install.php
```  

* Volver al navegador y poner url  
  nano.bitnamiapp.com/miweb/admin  
y comprobar que ya no da error.  

### 4.- Resolver conflictos  

* Instalar los módulos que no se hayan importado con el site  
  - FieldtypeCropImage  
  - Pages2JSON  

* Configurar el archivo _sftp-config.json_  
  - host: nano.bitnami.com  
  - file_permissions: 644  
  - dir_permissions: 755  

* Revisar archivo _factories.js_(situado en scripts)  
  Cambiar la url: "http://nano.bitnamiapp.com/miweb/web-service/"  

```
angular.module('factories', [])


.factory('pw', function($http) {

	var webService = "http://nano.bitnamiapp.com/miweb/web-service/";

	return {

		busca: function(query){ 
			return $http.post( webService + "busca/", {'query':query} ).then(function(response){
				return response.data;
			});
		}

	}
})
```  

Por esta otra:  

```
angular.module('factories', [])


.factory('pw', function($http, $location) {

	var webService = "http://"+$location.$$host+"/web-service/";

	return {

		busca: function(query){ 
			return $http.post( webService + "busca/", {'query':query} ).then(function(response){
				return response.data;
			});
		},

	}
})
```
  
### 5.- Sublime Text  

* Crear en escritorio carpeta vacia con el nombre de la nueva web.  
* Arrastrarla a Sublime Text  
* Sftp-> map to remote  
* Configurar sftp-config.json  

  

[MAS INFO](http://moodle.indinet.es/mod/page/view.php?id=121)  
