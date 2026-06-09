<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gestión de Estudiantes</title>

    <link rel="stylesheet" href="styles.css">

    <link rel="stylesheet"
        href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
</head>
<body>

    <div class="container">

        <header>
            <h1><i class="fa-solid fa-user-graduate"></i> Gestión de Estudiantes</h1>
            <button id="btnNuevo">
                <i class="fa-solid fa-plus"></i> Nuevo Estudiante
            </button>
        </header>

        <div class="tabla-container">
            <table id="tablaEstudiantes">
                <thead>
                    <tr>
                        <th>DNI</th>
                        <th>Nombres</th>
                        <th>Apellidos</th>
                        <th>Edad</th>
                        <th>Género</th>
                        <th>Teléfono</th>
                        <th>Acciones</th>
                    </tr>
                </thead>
                <tbody>

                </tbody>
            </table>
        </div>

    </div>

    <!-- Modal -->
    <div class="modal" id="modal">
        <div class="modal-content">

            <h2 id="tituloModal">Nuevo Estudiante</h2>

            <form id="formEstudiante">

                <input type="hidden" id="indice">

                <div class="grupo">
                    <label>DNI</label>
                    <input type="text" id="dni" required>
                </div>

                <div class="grupo">
                    <label>Nombres</label>
                    <input type="text" id="nombres" required>
                </div>

                <div class="grupo">
                    <label>Apellidos</label>
                    <input type="text" id="apellidos" required>
                </div>

                <div class="grupo">
                    <label>Edad</label>
                    <input type="number" id="edad" required>
                </div>

                <div class="grupo">
                    <label>Género</label>
                    <select id="genero">
                        <option>Masculino</option>
                        <option>Femenino</option>
                    </select>
                </div>

                <div class="grupo">
                    <label>Teléfono</label>
                    <input type="text" id="telefono" required>
                </div>

                <div class="acciones">
                    <button type="submit">Guardar</button>
                    <button type="button" id="cerrar">Cancelar</button>
                </div>

            </form>

        </div>
    </div>

    <script src="script.js"></script>

</body>
</html>*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:'Segoe UI',sans-serif;
}

body{
    background:linear-gradient(135deg,#0f172a,#1e293b);
    min-height:100vh;
    padding:30px;
}

.container{
    max-width:1400px;
    margin:auto;
}

header{
    display:flex;
    justify-content:space-between;
    align-items:center;
    margin-bottom:25px;
}

header h1{
    color:white;
}

#btnNuevo{
    background:#22c55e;
    color:white;
    border:none;
    padding:12px 20px;
    border-radius:10px;
    cursor:pointer;
    font-size:15px;
}

#btnNuevo:hover{
    background:#16a34a;
}

.tabla-container{
    background:white;
    border-radius:15px;
    overflow:hidden;
    box-shadow:0 10px 30px rgba(0,0,0,.3);
}

table{
    width:100%;
    border-collapse:collapse;
}

thead{
    background:#2563eb;
    color:white;
}

th,td{
    padding:15px;
    text-align:center;
}

tbody tr:nth-child(even){
    background:#f5f5f5;
}

tbody tr:hover{
    background:#dbeafe;
}

.btnEditar{
    background:#f59e0b;
    color:white;
    border:none;
    padding:8px 12px;
    border-radius:8px;
    cursor:pointer;
    margin-right:5px;
}

.btnEliminar{
    background:#ef4444;
    color:white;
    border:none;
    padding:8px 12px;
    border-radius:8px;
    cursor:pointer;
}

.modal{
    position:fixed;
    inset:0;
    background:rgba(0,0,0,.6);
    display:none;
    justify-content:center;
    align-items:center;
}

.modal-content{
    background:white;
    width:500px;
    padding:25px;
    border-radius:15px;
}

.modal-content h2{
    margin-bottom:20px;
}

.grupo{
    display:flex;
    flex-direction:column;
    margin-bottom:12px;
}

.grupo label{
    margin-bottom:5px;
    font-weight:600;
}

.grupo input,
.grupo select{
    padding:10px;
    border:1px solid #ccc;
    border-radius:8px;
}

.acciones{
    display:flex;
    gap:10px;
    margin-top:15px;
}

.acciones button{
    flex:1;
    padding:12px;
    border:none;
    border-radius:8px;
    cursor:pointer;
}

.acciones button[type="submit"]{
    background:#2563eb;
    color:white;
}

#cerrar{
    background:#ef4444;
    color:white;
}const estudiantes = [

{
dni:"74581236",
nombres:"Luis Alberto",
apellidos:"García Torres",
edad:18,
genero:"Masculino",
telefono:"987654321"
},
{
dni:"72145698",
nombres:"María Fernanda",
apellidos:"Quispe Huamán",
edad:19,
genero:"Femenino",
telefono:"965874123"
},
{
dni:"73458921",
nombres:"José Miguel",
apellidos:"Pérez Rojas",
edad:20,
genero:"Masculino",
telefono:"954321678"
},
{
dni:"75896321",
nombres:"Ana Lucía",
apellidos:"Mendoza Flores",
edad:18,
genero:"Femenino",
telefono:"978456321"
},
{
dni:"76985214",
nombres:"Carlos Andrés",
apellidos:"Sánchez Díaz",
edad:21,
genero:"Masculino",
telefono:"912345678"
},
{
dni:"74123698",
nombres:"Rosa Elena",
apellidos:"Vargas Castillo",
edad:19,
genero:"Femenino",
telefono:"923456789"
},
{
dni:"75632147",
nombres:"Juan Diego",
apellidos:"Ramírez Salas",
edad:20,
genero:"Masculino",
telefono:"934567891"
},
{
dni:"73214589",
nombres:"Daniela Sofía",
apellidos:"Huerta León",
edad:18,
genero:"Femenino",
telefono:"945678912"
},
{
dni:"74859632",
nombres:"Pedro Antonio",
apellidos:"Chávez Gómez",
edad:22,
genero:"Masculino",
telefono:"956789123"
},
{
dni:"75963214",
nombres:"Camila Andrea",
apellidos:"Navarro Paredes",
edad:19,
genero:"Femenino",
telefono:"967891234"
},
{
dni:"72369854",
nombres:"Miguel Ángel",
apellidos:"Flores Vega",
edad:20,
genero:"Masculino",
telefono:"978912345"
},
{
dni:"73698521",
nombres:"Valeria Isabel",
apellidos:"Torres Silva",
edad:18,
genero:"Femenino",
telefono:"989123456"
},
{
dni:"75412369",
nombres:"Diego Fernando",
apellidos:"Cruz Herrera",
edad:21,
genero:"Masculino",
telefono:"991234567"
},
{
dni:"72985634",
nombres:"Andrea Milagros",
apellidos:"Ríos Cárdenas",
edad:19,
genero:"Femenino",
telefono:"992345678"
},
{
dni:"74236985",
nombres:"Kevin Alexander",
apellidos:"López Medina",
edad:20,
genero:"Masculino",
telefono:"993456789"
},
{
dni:"76854123",
nombres:"Paola Jimena",
apellidos:"Castillo Ramos",
edad:18,
genero:"Femenino",
telefono:"994567891"
},
{
dni:"73125489",
nombres:"Jorge Luis",
apellidos:"Morales Peña",
edad:22,
genero:"Masculino",
telefono:"995678912"
},
{
dni:"75789632",
nombres:"Fiorella Cristina",
apellidos:"Aguilar Soto",
edad:19,
genero:"Femenino",
telefono:"996789123"
},
{
dni:"72458963",
nombres:"Ricardo Martín",
apellidos:"Espinoza Vega",
edad:21,
genero:"Masculino",
telefono:"997891234"
},
{
dni:"73965214",
nombres:"Karen Nicole",
apellidos:"Paredes Luna",
edad:20,
genero:"Femenino",
telefono:"998912345"
}

];

const tbody = document.querySelector("tbody");
const modal = document.getElementById("modal");
const form = document.getElementById("formEstudiante");

function listar(){

tbody.innerHTML="";

estudiantes.forEach((e,index)=>{

tbody.innerHTML += `
<tr>
<td>${e.dni}</td>
<td>${e.nombres}</td>
<td>${e.apellidos}</td>
<td>${e.edad}</td>
<td>${e.genero}</td>
<td>${e.telefono}</td>
<td>
<button class="btnEditar" onclick="editar(${index})">
Editar
</button>

<button class="btnEliminar" onclick="eliminar(${index})">
Eliminar
</button>
</td>
</tr>
`;

});

}

listar();

document.getElementById("btnNuevo").onclick=()=>{
form.reset();
indice.value="";
modal.style.display="flex";
};

cerrar.onclick=()=>{
modal.style.display="none";
};

form.addEventListener("submit",(e)=>{

e.preventDefault();

const estudiante = {

dni:dni.value,
nombres:nombres.value,
apellidos:apellidos.value,
edad:edad.value,
genero:genero.value,
telefono:telefono.value

};

if(indice.value===""){
estudiantes.push(estudiante);
}else{
estudiantes[indice.value]=estudiante;
}

listar();

modal.style.display="none";

});

function editar(i){

const e = estudiantes[i];

indice.value=i;
dni.value=e.dni;
nombres.value=e.nombres;
apellidos.value=e.apellidos;
edad.value=e.edad;
genero.value=e.genero;
telefono.value=e.telefono;

modal.style.display="flex";

}

function eliminar(i){

if(confirm("¿Desea eliminar el estudiante?")){

estudiantes.splice(i,1);

listar();

}

}
