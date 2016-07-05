###1.- Crear backup de nuestra web en Processwire con el módulo Export Site Profile.  
Le llamaremos **site**  

![](http://grabilla.com/06505-a0d1007f-4a56-4ab4-9b2b-d5d488938a91.png)  

###2.- Descargar la última versión (**MASTER**) de PW desde la [página oficial](https://processwire.com/download/)  

![](http://grabilla.com/06505-1606b8f9-6605-4428-b96a-07cf7110e371.png)  

Descomprimirla en nuestro escritorio.  

###3.- Copiamos nuestro site a la carpeta donde está descomprimido el Master PW.  
Eliminamos los otros site que contiene la carpeta Master PW para evitar conflictos.  

###4.- Lo volvemos a comprimir y lo subimos al Servidor.  

Para ello:  

- Instalar la copia de master.zip  
$ sudo ./creaPW.sh miweb dbpass https://aws-eu...../master.zip  
