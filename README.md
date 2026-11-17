# Folio — Inventario de productos

Actividad 4.4 de Aplicaciones Web. El proyecto conserva las tres páginas de la práctica anterior y agrega la administración del inventario con JavaScript.

## Diseño y uso

La interfaz usa negro carbón, blanco cálido y rojo. El menú está en la parte superior. Los campos tienen letra de 16 px y las acciones de producto incluyen texto y un área de al menos 44 px de alto.

En computadoras se muestra una tabla. En tabletas y celulares los productos se acomodan en tarjetas con los botones Editar y Eliminar visibles. El formulario y las confirmaciones también se ajustan al ancho disponible. Se respeta la preferencia de reducir movimiento del navegador.

## Funciones

- Agregar productos con nombre, categoría, cantidad y descripción opcional.
- Modificar un registro conservando su ID.
- Eliminar con confirmación y deshacer la última eliminación.
- Buscar por nombre, categoría o ID y filtrar por existencias.
- Descargar todo el inventario en un archivo Excel `.xlsx`.
- Conservar los registros al recargar y al volver a abrir el navegador.

## Cómo abrirlo

En XAMPP, copia la carpeta del proyecto como `C:\xampp\htdocs\inventario-web`, inicia Apache y visita `http://localhost/inventario-web/`.

En GitHub Pages, coloca los archivos en la raíz de `main`. Selecciona `Settings > Pages > Deploy from a branch > main > /(root)`.

## Dónde se guardan los datos

Se usa `localStorage`. Cada navegador y dirección de la página tiene sus propios registros. Los cambios de una computadora no se sincronizan con otro dispositivo. No se necesita instalar una base de datos para esta versión.

Si borras los datos del navegador, también se borra el inventario de ese navegador. En modo incógnito los datos pueden desaparecer al cerrar la sesión. Usa la exportación para conservar una copia de consulta en Excel.

La primera visita carga los cuatro productos de la práctica. Si eliminas todos, el inventario permanece vacío; los ejemplos no se vuelven a insertar al recargar.

## Casos alternos contemplados

Se rechazan nombres o categorías vacíos, cantidades negativas, decimales o mayores de 999999 y productos repetidos en una misma categoría. Se permite cantidad 0. Una edición no puede sobrescribir un registro modificado o eliminado desde otra pestaña. Los errores de almacenamiento se muestran sin anunciar un guardado que no ocurrió. Los datos dañados no se sustituyen automáticamente.

## Archivos

`index.html` contiene el resumen; `productos.html`, la tabla; `agregar.html`, el formulario de altas y cambios. `style.css` controla el diseño. `app-core.js` contiene las reglas y el almacenamiento; `app.js`, la interfaz; `export-excel.js`, la descarga de Excel.

El reporte incluye todos los productos, aunque haya filtros aplicados. Las cantidades son celdas numéricas y los nombres se exportan como texto, incluso si comienzan con `=`.

## Pruebas de las reglas

Con Node.js: `node --test tests/inventario.test.cjs`.
