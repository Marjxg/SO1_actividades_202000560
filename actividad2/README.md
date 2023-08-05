# Cron Job 

Para crear un cronjob se debe ejecutar el comando "crontab -e", dentro de este se debe escribir la siguiente instrucción:

````
*/5 * * * * /bin/sh actividad2.sh
````

* "\*/5" representa que el script se ejecutará cada 5 minutos.
* El resto de "\*" representan que se hará cualquier día, de cualquier mes.
* La ruta indica el script que se ejecutará.

Para guardar los cambios presionar Ctrl+o, para indicar el nombre del cronjob presionar enter y para salir presionar Ctrl+X.
Finalmente para verificar que se haya guardado el cronjob se hace escribiendo el comando "crontab -l", el cual lista los cronjobs existentes.

![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/8214f39e-92b4-4bfb-9f46-9ebd9b67a1d7)

# Script
Se muestra el código del script dentro de actividad2.sh.<br>
Se muestra la carpeta tmp con el directorio creado en la ejecución del script.<br>
Se muestra el log file en el que se almacenan las consultas, este muestra Null cuando no se leyó ningún usuario.<br>

![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/a0890ba3-73ed-4a21-9a71-7b9d310a2329)
