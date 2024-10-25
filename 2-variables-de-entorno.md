# Variables de Entorno
### ¿Qué son las variables de entorno
# COMPLETAR
Las variables de entorno son cadenas que contienen información acerca del entorno para el sistema y el usuario que ha iniciado sesión en ese momento. Algunos programas de software usan la información para determinar dónde se colocan los archivos (como los archivos temporales).

### Para crear un contenedor con variables de entorno?

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.
```
docker run -d --name srv-web -e username=geovanny -e role=admin nginx:alpine
```

![Imagen](img/jenkins_entorno.png)

### Crear un contenedor con mysql:8 , mapear todos los puertos
# COMPLETAR
```
docker run -P -d --name Jenkins2 mysql:8
```

### ¿El contenedor se está ejecutando?
# COMPLETAR
No, este momento el servidor no.

### Identificar el problema
# COMPLETAR
Existe un fallo en la ejecucion, que dice en el estado: Exited(1)

### Eliminar el contenedor creado con mysql:8 
# COMPLETAR
```
docker rm Jenkins2
```

### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

Previo a esto es necesario crear el archivo y colocar las variables en un archivo, **.env** se ha convertido en una convención estándar, pero también es posible usar cualquier extensión como **.txt**.
```
docker run -d --name <nombre contenedor> --env-file=<nombreArchivo>.<extensión> <nombre imagen>
```
**Considerar**
Es necesario especificar la ruta absoluta del archivo si este se encuentra en una ubicación diferente a la que estás ejecutando el comando docker run.

### Crear un contenedor con mysql:8 , mapear todos los puertos y configurar las variables de entorno mediante un archivo
```
docker run -d --name Jenkins2 --env-file=C:\Users\HP\Documents\mysql-env-file.env -P mysql:8
```

![Imagen](img/jenkins2.png)

### ¿Qué bases de datos existen en el contenedor creado?
# COMPLETAR
```
docker exec -it Jenkins2 mysql -u mi_usuario -p
```
