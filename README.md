# UMA Restaurante - Backend API (Spring Boot)

Sistema integral de gestión gastronómica diseñado para optimizar el flujo operativo de un restaurante, unificando la experiencia del cliente (reservaciones inteligentes, autenticación segura y catálogo digital) con el control gerencial (punto de venta, gestión de mesas, despacho en cocina y control de inventario).

Esta versión representa la evolución arquitectónica del sistema hacia un entorno empresarial robusto y fuertemente tipado utilizando **Java** y el ecosistema **Spring Boot**.

---

## ️Stack Tecnológico y Dependencias

El proyecto fue inicializado mediante **Spring Initializr** bajo las siguientes especificaciones técnicas:

* **Lenguaje:** Java 17
* **Framework:** Spring Boot 4.2.0
* **Gestor de Dependencias:** Maven (`Jar`)
* **Persistencia y Bases de Datos:** 
  * **Spring Data JPA:** Mapeo objeto-relacional (ORM) mediante Hibernate.
  * **MySQL Driver:** Conexión a base de datos relacional en producción (`uma_restaurante`).
  * **H2 Database:** Base de datos en memoria para pruebas rápidas y desarrollo local.
* **Web & API:** **Spring Web** (Arquitectura RESTful sobre servidor embebido Apache Tomcat).
* **Productividad:** **Lombok** (Reducción de código *boilerplate* mediante anotaciones).

---

## Arquitectura Inicial del Proyecto

El sistema sigue el patrón de **Arquitectura en Capas (N-Tier Architecture)** estándar de Spring Boot, separando estrictamente las responsabilidades del negocio, el acceso a datos y la exposición de endpoints HTTP:

```text
com.example.demo
├── model          # Entidades JPA (@Entity) que mapean las tablas de MySQL (Cliente, Mesa, Pedido, Producto, Reservacion)
├── repository     # Interfaces que extienden de JpaRepository para operaciones CRUD y consultas personalizadas
├── service        # Lógica de negocio, reglas financieras (recargos por domicilio/empaque) y validaciones
├── controller     # Controladores REST (@RestController) que exponen los endpoints y gestionan peticiones HTTP
└── DemoApplication.java  # Punto de entrada principal de la aplicación Spring Boot