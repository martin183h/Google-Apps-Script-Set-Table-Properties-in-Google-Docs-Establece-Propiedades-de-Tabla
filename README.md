<!DOCTYPE html>
<html>

<body>

  <h1>Set Table Properties in Google Docs using Google Apps Script <br>(To change cell colors)</h1>

  <p>This Google Apps Script contains a function named <code>setTableProperties</code> that sets specific properties
    for a table in a Google Docs document.</p>

  <h2>Function Description</h2>

  <p>The <code>setTableProperties</code> function does the following:</p>

  <ol>
    <li>Retrieves a Google Docs document using its unique identifier.</li>
    <li>Loops through all the tables in the document.</li>
    <li>For each table, it iterates through its rows and cells.</li>
    <li>Checks if a cell has a green background color and changes it to white.</li>
  </ol>

  <h2>Usage</h2>

  <p>To use this function:</p>

  <ol>
    <li>Replace the document identifier in the <code>DocumentApp.openById</code> function with your own Google Docs
      document identifier.</li>
    <li>Run the <code>setTableProperties</code> function to update the table properties in the specified Google Docs
      document.</li>
  </ol>

  <h2>Example</h2>

  <pre><code>
// Replace the document identifier with your own Google Docs document identifier
var doc = DocumentApp.openById("YOUR_DOCUMENT_ID");

function setTableProperties() {
  var tables = doc.getBody().getTables();
  tables.forEach((table) => {
    for (let r = 0; r &lt; table.getNumRows(); r++) {
      row = table.getRow(r);
      for (let c = 0; c &lt; row.getNumChildren(); c++) {
        if (table.getCell(r, c).getBackgroundColor() == null) {
          Logger.log('Found a green cell');
          table.getCell(r, c).setBackgroundColor('#FFFFFF');
          Logger.log('Changed to white');
        }
      }
    }
  });
}

// Run the function to set table properties
setTableProperties();
  </code></pre>

  <p>Replace <code>"YOUR_DOCUMENT_ID"</code> with the actual identifier of your Google Docs document. Run the
    <code>setTableProperties</code> function to set the table properties accordingly.</p>

</body>

</html>
