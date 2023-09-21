<!DOCTYPE html>
<html>

<body>

  <h1>Establecer Propiedades de Tabla en Google Docs usando Google Apps Script <br> (Para cambiar el color de celdas)</h1>

  <p>Este script de Google Apps contiene una función llamada <code>setTableProperties</code> que establece propiedades
    específicas para una tabla en un documento de Google Docs.</p>

  <h2>Descripción de la Función</h2>

  <p>La función <code>setTableProperties</code> realiza lo siguiente:</p>

  <ol>
    <li>Recupera un documento de Google Docs utilizando su identificador único.</li>
    <li>Itera sobre todas las tablas en el documento.</li>
    <li>Para cada tabla, recorre sus filas y celdas.</li>
    <li>Verifica si una celda tiene un color de fondo verde y lo cambia a blanco.</li>
  </ol>

  <h2>Uso</h2>

  <p>Para utilizar esta función:</p>

  <ol>
    <li>Reemplaza el identificador del documento en la función <code>DocumentApp.openById</code> con tu propio identificador
      de documento de Google Docs.</li>
    <li>Ejecuta la función <code>setTableProperties</code> para actualizar las propiedades de la tabla en el documento de
      Google Docs especificado.</li>
  </ol>

  <h2>Ejemplo</h2>

  <pre><code>
// Reemplaza el identificador del documento con tu propio identificador de documento de Google Docs
var doc = DocumentApp.openById("TU_IDENTIFICADOR_DE_DOCUMENTO");

function setTableProperties() {
  var tables = doc.getBody().getTables();
  tables.forEach((table) => {
    for (let r = 0; r &lt; table.getNumRows(); r++) {
      row = table.getRow(r);
      for (let c = 0; c &lt; row.getNumChildren(); c++) {
        if (table.getCell(r, c).getBackgroundColor() == null) {
          Logger.log('Se encontró una celda verde');
          table.getCell(r, c).setBackgroundColor('#FFFFFF');
          Logger.log('Cambiada a blanco');
        }
      }
    }
  });
}

// Ejecuta la función para establecer las propiedades de la tabla
setTableProperties();
  </code></pre>

  <p>Reemplaza <code>"TU_IDENTIFICADOR_DE_DOCUMENTO"</code> con el identificador real de tu documento de Google Docs.
    Ejecuta la función <code>setTableProperties</code> para establecer las propiedades de la tabla según sea
    necesario.</p>

</body>

</html>
