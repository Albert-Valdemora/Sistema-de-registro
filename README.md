<h1> Sistema de Registro</h1>

- Estado del proyecto: En construcción.

Para ejecutar el sistema, debes poner: 

```npm install react```

Sistema de Registro 2



- Excel

 ``` function agregarFormatoGuiones() {
  var hoja = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var filaSeleccionada = hoja.getActiveRange().getRow();
  
  var valor = hoja.getRange("M" + filaSeleccionada).getValue().toString();
  
  // Eliminar todos los guiones existentes
  valor = valor.replace(/-/g, "");

  // Verificar la longitud después de eliminar guiones
  if (valor.length == 11) {
    // Si tiene 11 caracteres (número de cédula), aplicar el formato con dos guiones al final
    hoja.getRange("M" + filaSeleccionada).setValue(valor.substr(0, 9) + valor.substr(9) + "--");
  } else if (valor.length == 9) {
    // Si tiene 9 caracteres (RNC), aplicar el formato con tres guiones al final
    hoja.getRange("M" + filaSeleccionada).setValue(valor.substr(0, 9) + "---");
  } else {
    // Si no cumple con ninguna longitud válida conocida, manejar según sea necesario
    // Por ejemplo, aquí podrías agregar lógica para manejar otros formatos o mostrar un mensaje de error
    hoja.getRange("M" + filaSeleccionada).setValue("Formato no reconocido");
  }
}```

```function agregarColor(){
  var hoja = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var filaSeleccionada = hoja.getActiveRange().getRow();

  var ultimaColumna = hoja.getLastColumn(); 
  
  var rangoFila = hoja.getRange(filaSeleccionada, 1, 1, ultimaColumna); 

  rangoFila.setBackground('#c9daf8')

}```


```function onOpen() {
  var ui = SpreadsheetApp.getUi();
  ui.createMenu('Mi Función Personalizada')
    .addItem('Agregar Formato con Guiones', 'agregarFormatoGuiones')
    .addItem('Agregar color', 'agregarColor')
    .addToUi();
}```
