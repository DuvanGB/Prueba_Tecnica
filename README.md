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
