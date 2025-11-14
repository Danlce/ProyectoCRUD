📘 README.md – Laboratorio CRUD con Fetch + PHP OOP + MySQL

Estudiante: William Concepción — Grupo 1SF131
Materia: Ingeniería Web
Instructor: Ing. Irina Fong
Fecha: II Semestre 2025

🧪 Laboratorio: CRUD + API Fetch + PHP OOP + MySQL

(Guardar, Editar, Buscar productos usando formulario dinámico)

Este laboratorio implementa un CRUD completo utilizando JavaScript (fetch + FormData) con PHP orientado a objetos y una base de datos MySQL, cumpliendo con la estructura indicada en la guía.
Se utilizan técnicas modernas de consumo de APIs, validación de datos, PDO (seguro contra SQL injection), SweetAlert2 y Bootstrap para la interfaz.

📌 Índice del README

Requisitos previos

Estructura del proyecto

Configuración de la base de datos

Explicación de cada archivo

Flujo de funcionamiento (Fetch → PHP → JSON)

Pruebas realizadas

Dificultades encontradas y soluciones

Capturas recomendadas

Conclusiones

✔ 1. Requisitos previos

Antes de ejecutar el proyecto, se necesita:

Servidor local

XAMPP o WAMP

PHP 7.4+ (para PDO)

MySQL

Navegador actualizado

Editor como VS Code

Extensión SweetAlert2

Bootstrap (via CDN)

✔ 2. Estructura del Proyecto
/ProyectoCRUD
│── index.html
│── script.js
│── registrar.php
│
└── Modelo/
     ├── conexion.php
     └── Productos.php

✔ 3. Configuración de la Base de Datos

Ejecutar en phpMyAdmin o MySQL Workbench:

CREATE DATABASE productosdb;

USE productosdb;

CREATE TABLE productos (
  id INT AUTO_INCREMENT PRIMARY KEY,
  codigo   VARCHAR(20) NOT NULL,
  producto VARCHAR(100) NOT NULL,
  precio   DECIMAL(10,2) NOT NULL,
  cantidad INT NOT NULL
);

✔ 4. Explicación de Cada Archivo
📁 Modelo/conexion.php

Clase encargada de crear conexión PDO y ejecutar métodos seguros para insertar, actualizar y consultar.

Incluye:

Manejo de errores con try/catch

Métodos insertSeguro, updateSeguro, query

📁 Modelo/Productos.php

Clase orientada a objetos que contiene:

✔ Propiedades del producto
✔ Validación de datos
✔ Métodos: guardar(), editar(), buscar(), listar()
✔ Uso de PDO y parámetros preparados

Todo centrado en el modelo como se exige en la guía.

📁 registrar.php

Controlador principal del proyecto:

✔ Recibe peticiones vía fetch (POST)
✔ Determina la acción usando switch($_POST["Accion"])
✔ Devuelve siempre JSON con:

{ "success": true/false, "message": "", "errors": [] }


Acciones:

Guardar

Modificar

Buscar

Listar

🌐 index.html

Formulario en Bootstrap que contiene:

Campos: Código, Producto, Precio, Cantidad

Botones: Guardar, Modificar, Buscar

Tabla dinámica de productos

SweetAlert2 para alertas bonitas

🎯 script.js

Pieza clave del laboratorio:

✔ Maneja botón por botón
✔ Usa fetch + FormData
✔ Recibe JSON desde PHP
✔ Muestra alertas con SweetAlert2
✔ Recarga la tabla automáticamente (ListarProductos)

Incluye switch interno según la acción enviada.

✔ 5. Flujo de Funcionamiento

El usuario llena el formulario en index.html

JS captura el clic → crea objeto FormData

Se envía con fetch() hacia registrar.php

PHP valida y ejecuta la acción mediante switch

Se retorna JSON

JS interpreta JSON y muestra mensajes con SweetAlert2

La tabla se refresca automáticamente

Este ciclo implementa un CRUD dinámico, sin recargar la página.

✔ 6. Pruebas Realizadas
🔹 Guardar Producto

Se ingresaron datos válidos → SweetAlert2 confirmó guardado.

Se verificó en la base de datos.

🔹 Editar Producto

Se buscó un producto por código.

Los campos se cargaron automáticamente.

Se actualizó correctamente.

🔹 Buscar Producto

Devuelve JSON del producto correcto.

Muestra alertas si no existe.

🔹 Listar Productos

Tabla se recarga después de cada operación.

🔹 Validaciones

Se probaron campos vacíos → mensajes de error funcionando.

✔ 7. Dificultades Encontradas y Soluciones
Dificultad	Solución
Fetch devolvía error porque PHP imprimía espacios	Se eliminaron echos y espacios externos (solo json_encode)
Error de CORS local	Ejecutar desde servidor local (no abrir archivo HTML desde el disco)
Validaciones no detectaban campos vacíos	Se creó método validar() en el modelo
Actualización no funcionaba	Se agregó campo oculto id en index.html
✔ 8. Capturas Recomendadas para Subir al Repositorio

Incluye:

📸 Formulario funcionando
📸 Producto guardado
📸 Buscar producto
📸 Editar producto
📸 Tabla de listado
📸 JSON mostrado desde registrar.php (en console)
📸 Estructura de carpetas

(Si quieres, me mandas capturas y te hago el README con las imágenes incrustadas).

✔ 9. Conclusiones

✔ Se implementó un CRUD completo utilizando buenas prácticas de PHP OOP, PDO, fetch, y SweetAlert2.
✔ Se cumplió con todos los requisitos de la guía, incluyendo validaciones, mensajes JSON y uso de Bootstrap.
✔ El uso de fetch permite una aplicación fluida sin recargas.
✔ La arquitectura Modelo–Controlador asegura un código limpio y escalable.
✔ Este laboratorio sienta las bases para desarrollar APIs modernas con PHP.
