# Actividad 4
## Crear Script
En la carpeta del usuario en home:
```
sudo vim actividad4.sh
```
Presionar "i" para Insertar texto, escribir el script
```
#!/bin/bash
echo "¡Hola! La fecha es: $(date +%Y-%m-%d)"
```
Presionar ESC para salir, y ":wq" para guardar

Modificar permisos del Script
```
sudo chmod +x actividad4.sh
```

## Crear servicio
Navegar a la siguiente carpeta
```
cd /etc/systemd/system
```
Crear el servicio
```
sudo vim actividad4.service
```
Presionar "i" para Insertar texto, escribir el script
```
[Unit]
Description=Print Hello and Date
[Service]
ExecStart=/home/marjorie/actividad4.sh
Type=oneshot
RemainAfterExit=true
[Install]
WantedBy=multi-user.target
```
Presionar ESC para salir, y ":wq" para guardar

Cambiar los permisos del servicios
```
sudo chmod 777 actividad4.service
```
Habilitar el servicio con el siguiente comando:
```
systemctl enable actividad4.service
```
Iniciar el servicio con el siguiente comando:
```
systemctl start actividad4.service
```
Verificar el estado del servicio con el siguiente comando:
```
sudo systemctl status actividad4.service
```
