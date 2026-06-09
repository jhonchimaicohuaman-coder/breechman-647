html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Automatización Contable - Planillas</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h2>Sistema de Automatización de Planillas Contables</h2>
        <p>Introduce los datos del colaborador para calcular el sueldo neto y aportes automáticos.</p>
        
        <form id="planillaForm">
            <div class="form-group">
                <label for="nombre">Nombre del Trabajador:</label>
                <input type="text" id="nombre" required placeholder="Ej. Juan Pérez">
            </div>
            
            <div class="form-group">
                <label for="sueldo">Sueldo Base (S/.):</label>
                <input type="number" id="sueldo" required min="0" placeholder="Ej. 1025">
            </div>
            
            <div class="form-group">
                <label for="afp">Régimen Pensionario:</label>
                <select id="afp">
                    <option value="onp">ONP (13%)</option>
                    <option value="afp">AFP (Aprox. 12%)</option>
                </select>
            </div>
            
            <button type="button" onclick="calcularPlanilla()">Calcular y Registrar</button>
        </form>

        <hr>

        <h3>Resumen de Planilla</h3>
        <table id="tablaResultados">
            <thead>
                <tr>
                    <th>Trabajador</th>
                    <th>Sueldo Base</th>
                    <th>Descuento Ley</th>
                    <th>Essalud (9%)</th>
                    <th>Neto a Pagar</th>
                </tr>
            </thead>
            <tbody>
                </tbody>
        </table>
    </div>
    <script src="script.js"></script>
</body>
</html>

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #f4f7f6;
    color: #333;
    padding: 20px;
}

.container {
    max-width: 650px;
    background: #ffffff;
    margin: 0 auto;
    padding: 30px;
    border-radius: 8px;
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
}

h2, h3 {
    color: #2c3e50;
    text-align: center;
}

.form-group {
    margin-bottom: 15px;
}

label {
    display: block;
    margin-bottom: 5px;
    font-weight: 600;
}

input, select {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}

button {
    width: 100%;
    padding: 12px;
    background-color: #27ae60;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 16px;
    cursor: pointer;
    font-weight: bold;
}

button:hover {
    background-color: #219150;
}

table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 20px;
}

th, td {
    padding: 12px;
    border: 1px solid #ddd;
    text-align: left;
}

th {
    background-color: #34495e;
    color: white;
}nction calcularPlanilla() {
    // Obtener los valores del formulario
    const nombre = document.getElementById('nombre').value;
    const sueldo = parseFloat(document.getElementById('sueldo').value);
    const regimen = document.getElementById('afp').value;

    // Validar que los campos no estén vacíos
    if (!nombre || isNaN(sueldo)) {
        alert("Por favor, complete todos los campos correctamente.");
        return;
    }

    // Lógica de automatización de cálculos de procesos contables
    let porcentajeDescuento = (regimen === 'onp') ? 0.13 : 0.12;
    let descuentoLey = sueldo * porcentajeDescuento;
    let essalud = sueldo * 0.09; // Aporte del empleador
    let netoPagar = sueldo - descuentoLey;

    // Obtener la tabla para insertar el nuevo registro
    const tabla = document.getElementById('tablaResultados').getElementsByTagName('tbody')[0];
    
    // Crear una nueva fila con los resultados automatizados
    const nuevaFila = tabla.insertRow();

    nuevaFila.innerHTML = `
        <td>${nombre}</td>
        <td>S/. ${sueldo.toFixed(2)}</td>
        <td>S/. ${descuentoLey.toFixed(2)}</td>
        <td>S/. ${essalud.toFixed(2)}</td>
        <th style="color: #27ae60;">S/. ${netoPagar.toFixed(2)}</th>
    `;

    // Limpiar el formulario para un nuevo ingreso
    document.getElementById('planillaForm').reset();
