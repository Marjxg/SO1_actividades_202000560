nn202000560 <br>
Marjorie Gissell Reyes Franco

# Parte1: Gestión de usuarios
### Crear usuarios
Crear usuario 1 <br>
```
adduser usuario1
```

Crear usuario 2 <br>
```
adduser usuario2
```

Crear usuario 3 <br>
```
adduser usuario3
```
### Cambiar contraseñas a los usuarios
Cambiar contraseña usuario 1 <br>
```
sudo passwd usuario1
```
Cambiar contraseña usuario 2 <br>
```
sudo passwd usuario2
```
Cambiar contraseña usuario 3 <br>
```
sudo passwd usuario3
```
### Mostrar información del usuario 1
```
id usuario1
```
![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/2ccc4f34-b0bd-4491-8071-8a97cd293c48)

### Eliminar usuario 3 conservando su directorio principal
```
sudo deluser usuario3
```
En cambio, para eliminar un usuario junto a su directorio se utiliza el comando: *sudo deluser --remove-home newuser*
# Parte 2: Gestión de grupos
### Creación de dos grupos llamados grupo1 y grupo2
Crear grupo 1 <br>
```
sudo groupadd grupo1
```
Crear grupo 2 <br>
```
sudo groupadd grupo2
```
### Agregar usuario1 a grupo1 y usuario2 a grupo2
Agregar usuario 1 a grupo 1
```
usermod -a -g grupo1 usuario1
```
Agregar usuario 2 a grupo 2
```
usermod -a -g grupo2 usuario2
```
En este comando -a significa append (agregar) y -g significa group (grupo) = añadir grupo secundario <br>
Si se omite el comando -a se coloca como grupo principal
### Verificar que los usuarios han sido agregados a los grupos utilizando el comando groups
Verificar a qué grupos pertenece el usuario 1
```
groups usuario1
```
![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/8a3d1e87-e534-4771-97cd-7832cdf58717)

Verificar a qué grupos pertenece el usuario 2
```
groups usuario2
```
![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/6adb1699-ed94-47e0-8a5b-7ac44c0e6252)

Por defecto, cuando un usuario es creado, se crea de igual manera un grupo con el mismo nombre y este les es asignado como principal.
### Eliminar grupo2
```
sudo deluser --group grupo2
```

# Parte 3: Gestión de permisos
### Creación de Archivos y Directorios:

- Creación de un archivo llamado `archivo1.txt` en el directorio principal de 'usuario1' y escribir algo en él.

Iniciar sesión en el usuario1 para acceder a los archivos
```
su -l usuario1
```
Crear archivo
```
touch archivo1.txt
```
Verificar la creación del archivo
```
ls
```

![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/e371c7b9-fd54-4c7e-a43e-2453688c41aa)

Escribir algo en el archivo
```
echo "Escribiendo..." >> archivo1.txt
echo "En archivo1.txt del directorio principal de usuario1" >> archivo.txt
```
Verificar el contenido del archivo
```
cat archivo1.txt
```
![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/363778d9-4b7d-4e40-926e-813c283c7119)

- Creación de un directorio llamado `directorio1` y dentro de ese directorio, un archivo llamado `archivo2.txt`.

Crear directorio
```
mkdir directorio1
```
Moverse a ese directorio
```
cd directorio1
```
Crear archivo
```
touch archivo2.txt
```

### Verificar Permisos
Verifica los permisos del archivo y directorio usando el comando `ls -l` y `ls -ld` respectivamente.
```
ls -l archivo1.txt
```
![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/935edb32-dd9e-4ce7-8624-1ac44faa61e2)

```
ls -ld directorio1
```
![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/5e38c5b3-9cab-4031-a828-eaa7e087f5ec)

```
cd directorio1
ls -l archivo2.txt
```
![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/6507fe11-fc4e-4ee1-a0a8-902e637aa6b6)

### Modificar Permisos usando `chmod` con Modo Numérico
Cambia los permisos del `archivo1.txt` para que sólo `usuario1` pueda leer y escribir (permisos `rw-`), el grupo pueda leer (permisos `r--`) y nadie más pueda hacer nada.
```
chmod 640 archivo1.txt
```
| Valor numérico | Permiso |
| --- | ---|
| 6 | rw- |
| 4 | r-- |
| 0 | --- |

![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/3925dee0-a501-4d7a-b86d-a8afeee43687)

### Modificar Permisos usando `chmod` con Modo Simbólico
Agrega permiso de ejecución al propietario del `archivo2.txt`
```
cd archivo2.txt
chmod u+x archivo2.txt
```
u significa que se quiere cambiar permiso al usuario propietario, + significa que se está agregando un permiso y x representa el permiso de ejecución.

![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/a37d31ae-7c57-426b-9502-7b58c26e3520)

### Cambiar el Grupo Propietario
Cambia el grupo propietario de `archivo2.txt` a `grupo1`.
```
cd archivo2.txt
chown usuario1:grupo1 archivo2.txt
```

![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/7200f469-e322-412f-a80c-00aab1d6aed9)

### Configurar Permisos de Directorio
Cambia los permisos del `directorio1` para que sólo el propietario pueda entrar (permisos `rwx`), el grupo pueda listar contenidos pero no entrar (permisos `r--`), y otros no puedan hacer nada.
```
chmod u=rwx directorio1
```
```
chmod g=r-- directorio1
```
```
chmod o=--- directorio1
```
![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/289cfc4d-0766-4aa6-bce8-a41c5ff1d27a)


### Comprobación de Acceso
Intenta acceder al `archivo1.txt` y `directorio1/archivo2.txt` como `usuario2`. Nota cómo el permiso de directorio afecta el acceso a los archivos dentro de él.

Iniciar sesión con el usuario2
```
su -l usuario2
```
```
cat /home/usuario1/archivo1.txt
```
![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/4bf0e052-adf6-494c-9fe6-2e86ce64e1d4)

```
cat /home/usuario1/directorio1/archivo2.txt
```
![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/268e7097-cd06-4a75-9c40-037cc9e110ee)

### Verificación Final
Verifica los permisos y propietario de los archivos y directorio nuevamente con `ls -l` y `ls -ld`.

Desde el usuario2 no hay permisos
![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/80c68889-1270-4c24-a463-1f4bee8cad2e)


Desde el usuario1
```
ls -l archivo1.txt
```

![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/02efa8e5-e1e4-4033-a8a0-a8b4b883678c)

```
ls -ld directorio1
```

![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/4bc18c61-7837-4dbb-a475-38193dba60b3)


```
cd directorio1
ls -l archivo2.txt
```
![imagen](https://github.com/Marjxg/SO1_actividades_202000560/assets/78390305/296aab04-ca02-4575-ab8f-813a1393398c)


# Reflexión
### ¿Por qué es importante gestionar correctamente los usuarios y permisos en un sistema operativo?
Al ser un sistema multiusuario, estos son de gran importancia para evitar que otros usuarios y grupos roben o malversen información de carpetas, archivos e incluso de los mismos usuarios. Además permiten tener una mejor organización y que los usuarios no interfieran entre sí.
### ¿Qué otros comandos o técnicas conocen para gestionar permisos en Linux?
Además del comando chmod para gestionar permisos de usuario y del comando chwon para gestionar permisos de archivos y directorios, existe el comando **chgrp** para cambiar grupos de archivos y directorio.
