# Prueba Técnica Full Stack - Cliente Service

## Descripción del Proyecto
Este proyecto implementa una solución Full Stack para consultar información básica de clientes, cumpliendo con los requisitos especificados en la prueba técnica. Consta de:

- **Backend**: Servicio REST en Spring Boot que valida y retorna datos mockeados de clientes
- **Frontend**: Aplicación Angular con formulario de búsqueda y pantalla de resultados

## Estructura del Proyecto

### Backend (Spring Boot)
backend/
├── src/
│   ├── main/
│   │   ├── java/ntt/ClientService/
│   │   │   ├── config/                  # Configuración CORS
│   │   │   ├── controller/              # Controlador REST
│   │   │   ├── dto/                     # Objetos de transferencia de datos
│   │   │   ├── exception/               # Manejo de excepciones
│   │   │   └── ClientServiceApplication.java # Punto de entrada
│   │   └── resources/
│   │       ├── application.properties   # Configuración de la app
│   │       └── logback-spring.xml       # Configuración de logs
└── pom.xml                              # Dependencias Maven

### Frontend (Angular)
frontend/
├── src/
│   ├── app/
│   │   ├── components/                  # Componentes principales
│   │   │   ├── consulta/                # Formulario de búsqueda
│   │   │   └── resumen/                 # Pantalla de resultados
│   │   ├── models/                      # Modelos de datos
│   │   ├── services/                    # Servicio para API
│   │   └── archivos de configuración    # Rutas y config general
│   ├── assets/data/                     # Datos mock (JSON)
│   └── styles.css                       # Estilos globales
├── angular.json                         # Config Angular CLI
└── package.json                         # Dependencias Node

## Tecnologías Utilizadas

### Backend
- Java 17
- Spring Boot
- Maven
- Lombok
- Logback

### Frontend
- Angular 20
- TypeScript 
- Bootstrap
- RxJS
- HTML5/CSS3

## Instalación y Ejecución

### Requisitos Previos
- JDK
- Node.js
- Angular CLI
- Maven

### Backend
cd backend
mvn clean install
java -jar target/client-service-0.0.1-SNAPSHOT.jar
El servicio estará disponible en: http://localhost:8090/api/clientes

### Frontend
cd frontend
npm install
ng serve
La aplicación estará disponible en: http://localhost:4200

## Endpoints del Backend

### Consultar Cliente
GET /api/clientes
Parámetros:
- tipoDocumento (C|P)
- numeroDocumento (23445322 para mock)
  
Respuestas:
200 OK: Datos del cliente encontrado
400 Bad Request: Validación fallida
404 Not Found: Cliente no existe
500 Internal Server Error: Error inesperado

### Validaciones Implementadas

#### Backend
Tipo documento: Solo 'C' (Cédula) o 'P' (Pasaporte)
Ambos campos obligatorios
Mock solo para cédula 23445322

#### Frontend
Tipo documento: Selección obligatoria
Número documento:
8-11 caracteres
Solo números
Validación en tiempo real
Botón buscar se habilita solo con campos válidos

#### Mock de Datos
El backend retorna información mockeada solo para:
Tipo documento: C
Número documento: 23445322
Ejemplo de respuesta:
{
  "primerNombre": "Duvan",
  "segundoNombre": "Andres",
  "primerApellido": "Galvis",
  "segundoApellido": "Brito",
  "telefono": "3101234567",
  "direccion": "Calle 123 #45-67",
  "ciudadResidencia": "Bogotá"
}

### Interfaz de Usuario (Frontend)

#### Vista General
La aplicación presenta una interfaz limpia y funcional con las siguientes características:

##### Identificación Visual:

Logo corporativo visible en la pestaña del navegador
<img width="127" height="42" alt="image" src="https://github.com/user-attachments/assets/b3ad8f33-f9eb-40c0-ada1-f16bbc9d8756" />

##### Pantalla Principal:

Formulario de búsqueda con campos para:

Selección del tipo de documento (desplegable)

Ingreso del número de documento (campo numérico)
<img width="651" height="537" alt="image" src="https://github.com/user-attachments/assets/0bcf0655-c99d-4a10-bff5-5a3c1a8df957" />

###### Validaciones Implementadas
El sistema realiza las siguientes validaciones en tiempo real:

Tipo de documento obligatorio

Número de documento:

Longitud entre 8-11 caracteres

Solo acepta valores numéricos

Formato adecuado según el tipo de documento

##### Ejemplos de mensajes de validación:
<img width="642" height="548" alt="image" src="https://github.com/user-attachments/assets/1acba7f6-66b2-48dd-b63d-b22f74541539" />
<img width="652" height="556" alt="image" src="https://github.com/user-attachments/assets/d3e876c1-219a-435d-8002-30dd2f1a44e2" />
<img width="649" height="555" alt="image" src="https://github.com/user-attachments/assets/d7804f61-1339-4226-b83c-2c51e1ac03ce" />
<img width="653" height="577" alt="image" src="https://github.com/user-attachments/assets/22b4ddb3-403a-4a64-a28b-74b02a9a8a4e" />
<img width="650" height="612" alt="image" src="https://github.com/user-attachments/assets/603498b5-63aa-4408-905b-e4a635846d18" />
<img width="649" height="555" alt="image" src="https://github.com/user-attachments/assets/611681fc-0016-413f-8e05-203c41e45e5a" />
<img width="653" height="556" alt="image" src="https://github.com/user-attachments/assets/2a69ce4e-c199-4aec-8c96-9017719d9f88" />

##### Flujo de Búsqueda Exitosa
Al ingresar datos válidos correspondientes al mock (Cédula: 23445322), la aplicación muestra:

#### Transición automática al componente de resumen

Visualización detallada de la información del cliente
<img width="480" height="912" alt="image" src="https://github.com/user-attachments/assets/93917716-12ae-439d-9ddf-469614bc863e" />

### Ejecución del Backend (Opción Pre-empaquetada)
Para facilitar las pruebas, el proyecto incluye un archivo JAR ejecutable del backend:

#### Ubicación:
Prueba_Tecnica\backend\target\ClientService-0.0.1-SNAPSHOT.jar

#### Comando de ejecución:

cd "\Prueba_Tecnica\backend\target"
java -jar ClientService-0.0.1-SNAPSHOT.jar

#### Acceso al servicio:
El backend estará disponible en http://localhost:8090/api/clientes

