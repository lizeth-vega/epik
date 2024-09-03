
# EpikApiPersona

Este proyecto es una API RESTful básica creada con .NET Core que permite realizar operaciones CRUD (Crear, Leer, Actualizar, Eliminar) sobre una entidad `Persona`. La API incluye validaciones y rutas adicionales para filtrar y actualizar datos específicos.

## Requisitos previos

Antes de empezar, asegúrate de tener lo siguiente instalado en tu máquina:

- [Visual Studio 2022 o superior](https://visualstudio.microsoft.com/) con la carga de trabajo de desarrollo ASP.NET y desarrollo web.
- [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads) o SQL Server Express.
- [.NET SDK 6.0](https://dotnet.microsoft.com/download/dotnet/6.0) o superior.
- [Postman](https://www.postman.com/) para probar la API (opcional).

## Configuración del Proyecto

### 1. Clonar y descomprimir el proyecto

El proyecto esta en un archivo .zip, descomprime el contenido en un directorio de tu elección.

### 2. Configurar la base de datos

El proyecto está configurado para usar Entity Framework Core con SQL Server. Antes de ejecutar el proyecto, asegúrate de que la cadena de conexión en `appsettings.json` apunte a tu instancia de SQL Server. Puedes modificar este archivo para reflejar tus credenciales y nombre de la base de datos.

```json
"ConnectionStrings": {
  "DefaultConnection": "Server=(localdb)\mssqllocaldb;Database=EpikApiPersonaDb;Trusted_Connection=True;MultipleActiveResultSets=true"
}
```

### 3. Aplicar migraciones de base de datos

Abre la consola de administrador de paquetes en Visual Studio y navega a la carpeta del proyecto. Luego, ejecuta los siguientes comandos para aplicar las migraciones y crear la base de datos:

```sh
Update-Database
```

### 4. Ejecutar el proyecto

Para ejecutar el proyecto en modo de desarrollo:

1. Abre el proyecto en Visual Studio.
2. Selecciona `IIS Express` en la barra superior de Visual Studio.
3. Presiona `F5` o haz clic en el botón "Iniciar" para ejecutar la API.

### 5. Uso de Swagger

Una vez que el proyecto esté en ejecución, Swagger estará disponible para interactuar con la API. Swagger se abrira en el navegador automaticamente o puedes acceder a la interfaz visitando la siguiente URL en tu navegador:

```
http://localhost:25807/swagger/index.html
```

Swagger te permitirá probar todas las rutas de la API directamente desde el navegador.

### 6. Probar la API con Postman

También puedes probar la API usando Postman. A continuación, te proporcionamos ejemplos de cómo consumir los endpoints principales:

- **Obtener todas las personas:**  
  `GET http://localhost:[tu-puerto]/api/Personas`

- **Obtener una persona por ID:**  
  `GET http://localhost:[tu-puerto]/api/Personas/{id}`

- **Crear una nueva persona:**  
  `POST http://localhost:[tu-puerto]/api/Personas`  
  Cuerpo de la solicitud (JSON):
  ```json
  {
    "Identificacion": 123,
    "Nombres": "Juan",
    "Apellidos": "Pérez",
    "Edad": 30,
    "Genero": "Masculino"
  }
  ```

- **Actualizar la edad de una persona:**  
  `PUT http://localhost:[tu-puerto]/api/Personas/{id}/edad`  
  Cuerpo de la solicitud (JSON):
  ```json
  {
    "nuevaEdad": 31
  }
  ```

- **Eliminar una persona:**  
  `DELETE http://localhost:[tu-puerto]/api/Personas/{id}`

## Consideraciones adicionales

- Asegúrate de que tu SQL Server esté en funcionamiento y que el proyecto pueda conectarse a la base de datos correctamente.
- Si deseas cambiar el puerto en el que se ejecuta la API, puedes hacerlo en el archivo `launchSettings.json` dentro de la carpeta `Properties`.

## Problemas conocidos

Si encuentras algún problema al intentar ejecutar el proyecto o al aplicar migraciones, asegúrate de que todos los paquetes de NuGet estén restaurados y que la cadena de conexión esté configurada correctamente.
