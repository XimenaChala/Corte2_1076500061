# Sistema de Gestión de Información de Automóviles y Calificaciones
Este sistema está diseñado para ayudarte a administrar eficientemente una flota de automóviles, permitiéndote realizar un seguimiento detallado del rendimiento de cada vehículo y garantizar su mantenimiento óptimo. Algunas características clave incluyen : `Automóviles de Pasajeros` `Vehículos Comerciales` `Vehículos Utilitarios Deportivos (SUV)` `Vehículos Ecológicos`


## Análisis: Definición de Requerimientos autos 
* Automóviles de Pasajeros: Esta categoría incluye vehículos diseñados principalmente para el transporte de personas en su vida cotidiana. Ejemplos comunes son sedanes, hatchbacks y cupés.
* Vehículos Comerciales: Engloba una variedad de vehículos utilizados para el transporte de mercancías o equipos con fines comerciales. Esto incluye camiones de carga, furgonetas de reparto, camiones de remolque, entre otros.
* Vehículos Utilitarios Deportivos (SUV): Estos vehículos combinan características de automóviles de pasajeros y camionetas, ofreciendo versatilidad y espacio. Ejemplos comunes son los SUV compactos, medianos y de tamaño completo.
* Vehículos Ecológicos: Incluye vehículos que utilizan tecnologías alternativas para reducir su impacto ambiental, como vehículos eléctricos, híbridos y de hidrógeno. Esto puede incluir modelos como el Tesla Model S, Toyota Prius y Honda Clarity.

#### Diseñar Base de Datos
Datos a tener en cuenta autos 
`Autos`
| AutomovilID | CategoriaAutoID |    Marca    |   Modelo   | AnioFabricacion | NumeroSerie | TipoCombustible | EstadoVehiculo |
|-------------|------------------|-------------|------------|-----------------|-------------|-----------------|----------------|
|      1      |        1         |   Toyota    |   Corolla  |      2019       |  JT12345678 |     Gasolina    |     Nuevo      |
|      2      |        1         |   Honda     |   Civic    |      2018       |  HC98765432 |     Gasolina    |     Usado      |
|      3      |        2         |   Ford      |  Transit   |      2020       |  FT56789123 |     Diésel      |     Usado      |
|      4      |        3         |   Chevrolet |    Tahoe   |      2021       |  CT24681357 |     Gasolina    |     Nuevo      |
|      5      |        4         |   Tesla     |   Model S  |      2022       |  TS97531846 |   Eléctrico     |     Nuevo      |


 Esta tabla representa información básica sobre algunos automóviles, incluyendo su identificador, la categoría a la que pertenecen, marca, modelo, año de fabricación, número de serie, tipo de combustible y estado del vehículo. Puedes agregar más filas a la tabla para incluir información adicional sobre otros automóviles.

En este sentido, se procede a normarlizar de la siguiente manera. 

* La clasificación de los AutosPersonas, estos son individuales. 
 `AutosPersonas`

| PersonaID |   Nombre   | NumeroIdentificacion |   Contacto   |
|-----------|------------|----------------------|--------------|
|     1     |   Juan     |       123456789      | 555-123-4567 |
|     2     |   Maria    |       987654321      | 555-987-6543 |
|     3     |   Carlos   |       456789123      | 555-456-7890 |
|     4     |   Laura    |       789123456      | 555-789-1234 |


Esta tabla representa información básica sobre algunas personas asociadas con automóviles, incluyendo su identificador, nombre, número de identificación y contacto. Puedes agregar más filas a la tabla para incluir información adicional sobre otras personas.

* La clasificación de los Personas, estos son individuales. 
`Persona`

| PersonaID |   Nombre   | NumeroIdentificacion |   Contacto   | AutomovilID |
|-----------|------------|----------------------|--------------|-------------|
|     1     |   Juan     |       123456789      | 555-123-4567 |      1      |
|     2     |   Maria    |       987654321      | 555-987-6543 |      1      |
|     3     |   Carlos   |       456789123      | 555-456-7890 |      2      |
|     4     |   Laura    |       789123456      | 555-789-1234 |      3      |

> Ver
![Modelo relacional del ejercicio](corte2/imagen.png)


> Script de la base de datos
```sql
    DROP DATABASE IF EXISTS autos;
    CREATE DATABASE autos;

    USE autos;

    CREATE TABLE Personas (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(100) NOT NULL,
    telefono VARCHAR(20),
    correo VARCHAR(100)
   );


    CREATE TABLE Autospersonas (
    id INT PRIMARY KEY AUTO_INCREMENT,
    marca VARCHAR(100) NOT NULL,
    modelo VARCHAR(100) NOT NULL,
    color VARCHAR(50),
    anio_fabricacion INT,
    placa VARCHAR(20) UNIQUE,
    persona_id INT,
    FOREIGN KEY (persona_id) REFERENCES Personas(id)
   );
```

