# Requisitos
- Tener una base de datos activa de MySQL
- Si preferis, podeis levantar un container mapeando los puertos
   - Usar MySQL
      - ```docker run -d --name NOMBRE -e MYSQL_ROOT_PASSWORD=password -p 3306:3308 mariadb:latest```
   - Usar MaiaDB
      - ```docker run -d --name NOMBRE -e MYSQL_ROOT_PASSWORD=password -p 3306:3308 mysql:latest```

Deberemos tener una base de datos creada. Aquí teneis un ejemplo de como hacerlo en el contenedor
- Si usais MySQL:
   - ```docker exec -it NOMBRE mysql -u root -p -e <SQL_SENTENCE>```
- Si usais MariaDB
   - ```docker exec -it NOMBRE mariadb -u root -p -e <SQL_SENTENCE>```
# Instrucciones de instalación
1. Clona este repositorio haciendo uso de git clone
   >```git clone https://github.com/MiquelMontero02/FlaskDemoDockerApp```
2. Crear un entorno virtual dentro de la carpeta del repositorio
   >```py -m venv NOMBRE_ENTORNO```
3. Activar el entorno
   >```NOMBRE_ENTORNO\Scripts\activate```
4. Instalar dependencias
   > ```pip install -r requirements.txt```
5. Crear un archivo .env similar al siguiente
   >```yaml
   >DATABASE_HOST=localhost
   >DATABASE_PORT=3306 #Puede que tengais el 3307!
   >DATABASE_NAME=test_db # Indicadle aquí el nombre de vuestra base de datos
   >DATABASE_USER=root
   >DATABASE_PASSWORD=12345678
   >```

# Manual de usuario
1. Activar servidor flask
   > ```flask run --debug```
2. Una vez activado, se podrá acceder a 3 rutas desde la dirección `localhost:5000`
   - [localhost:5000](localhost:5000) o [localhost:5000/](localhost:5000/): Landing route
   - [localhost:5000/insert](localhost:5000/insert): realiza un insert de un Customer
   - [localhost:5000/customers](localhost:5000/customers): Realiza una consulta para visualizar todos los customers

# Objetivo del proyecto
1. Configurar un Dockerfile para levantar una aplicación Flask
2. Crear una imagen a partir de este Dockerfile, con el tag `v1.0`
3. Levantar un contenedor con la nueva imagen creada
4. Acceder a la aplicación hosteada por nuestro docker
