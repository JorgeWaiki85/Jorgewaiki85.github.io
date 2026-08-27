<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulario de Informes</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        .tabs {
            display: flex;
            background-color: #333;
        }

        .tab-btn {
            padding: 15px 30px;
            border: none;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            color: white;
            background-color: #555;
            transition: background-color 0.3s;
        }

        .tab-btn:hover {
            background-color: #777;
        }

        .tab-btn.active {
            background-color: #fff;
            color: #333;
        }

        .tab-content {
            display: none;
            padding: 20px;
        }

        .tab-content.active {
            display: block;
        }

        .delitos-bg {
            background-color: #E0F7FA;
        }

        .accidentes-bg {
            background-color: #FFCDD2;
        }

        .form-section {
            background-color: white;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .form-section h2 {
            margin-bottom: 15px;
            color: #333;
            border-bottom: 2px solid #00796B;
            padding-bottom: 10px;
        }

        .accidentes-bg .form-section h2 {
            border-bottom-color: #C62828;
        }

        .form-row {
            display: flex;
            gap: 15px;
            margin-bottom: 15px;
        }

        .form-group {
            flex: 1;
            display: flex;
            flex-direction: column;
        }

        .form-group label {
            font-weight: bold;
            margin-bottom: 5px;
            color: #333;
        }

        .form-group input,
        .form-group textarea {
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 14px;
        }

        .form-group textarea {
            min-height: 100px;
            resize: vertical;
        }

        .checkbox-section {
            background-color: #f5f5f5;
            padding: 15px;
            border-radius: 8px;
            margin: 15px 0;
        }

        .checkbox-section label {
            display: flex;
            align-items: center;
            gap: 10px;
            font-weight: bold;
            font-size: 16px;
            cursor: pointer;
        }

        .checkbox-section input[type="checkbox"] {
            width: 20px;
            height: 20px;
            cursor: pointer;
        }

        .radio-group {
            display: flex;
            gap: 15px;
            margin-top: 5px;
        }

        .radio-group label {
            display: flex;
            align-items: center;
            gap: 5px;
            font-weight: normal;
        }

        .radio-group input[type="radio"] {
            width: 18px;
            height: 18px;
            cursor: pointer;
        }

        .checkbox-group {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            margin-top: 5px;
        }

        .checkbox-group label {
            display: flex;
            align-items: center;
            gap: 4px;
            font-weight: normal;
            cursor: pointer;
        }

        .checkbox-group input[type="checkbox"] {
            width: 18px;
            height: 18px;
            cursor: pointer;
        }

        .dynamic-section {
            margin-top: 15px;
            padding: 15px;
            background-color: #fff;
            border-radius: 8px;
            border: 1px dashed #999;
        }

        .dynamic-item {
            background-color: #f9f9f9;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 15px;
            position: relative;
            border: 1px solid #ddd;
        }

        .dynamic-item h4 {
            margin-bottom: 10px;
            color: #555;
        }

        .remove-btn {
            position: absolute;
            top: 10px;
            right: 10px;
            background-color: #f44336;
            color: white;
            border: none;
            border-radius: 50%;
            width: 30px;
            height: 30px;
            font-size: 18px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .remove-btn:hover {
            background-color: #d32f2f;
        }

        .add-btn {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            display: flex;
            align-items: center;
            gap: 8px;
            margin-top: 10px;
        }

        .add-btn:hover {
            background-color: #45a049;
        }

        .send-btn {
            background-color: #25D366;
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 10px;
            cursor: pointer;
            font-size: 18px;
            font-weight: bold;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            width: 100%;
            margin-top: 20px;
        }

        .send-btn:hover {
            background-color: #20BA5C;
        }

        .clear-btn {
            background-color: #f44336;
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 10px;
            cursor: pointer;
            font-size: 18px;
            font-weight: bold;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            width: 100%;
            margin-top: 20px;
        }

        .clear-btn:hover {
            background-color: #d32f2f;
        }

        .btn-container {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .btn-container button {
            flex: 1;
        }

        .hidden {
            display: none;
        }

        .personnel-section {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
        }

        @media (max-width: 768px) {
            .tabs {
                flex-direction: column;
            }

            .tab-btn {
                width: 100%;
                padding: 12px 20px;
            }

            .tab-content {
                padding: 10px;
            }

            .form-section {
                padding: 15px;
                margin-bottom: 15px;
            }

            .form-row {
                flex-direction: column;
                gap: 10px;
            }

            .form-group input,
            .form-group textarea {
                width: 100%;
                font-size: 16px;
            }

            .personnel-section {
                grid-template-columns: 1fr;
            }

            .btn-container {
                flex-direction: column;
            }

            .send-btn,
            .clear-btn {
                width: 100%;
                padding: 15px;
                font-size: 16px;
            }

            .dynamic-item {
                padding: 12px;
            }

            .checkbox-section label {
                font-size: 14px;
            }

            .add-btn {
                width: 100%;
                justify-content: center;
            }
        }

        @media (max-width: 480px) {
            .form-section h2 {
                font-size: 16px;
            }

            .form-group label {
                font-size: 13px;
            }

            .form-group input,
            .form-group textarea {
                font-size: 14px;
                padding: 8px;
            }

            .dynamic-item h4 {
                font-size: 14px;
            }

            .remove-btn {
                width: 28px;
                height: 28px;
                font-size: 16px;
            }
        }
    </style>
</head>
<body>
    <div class="tabs">
        <button class="tab-btn active" onclick="openTab('delitos')">DELITOS</button>
        <button class="tab-btn" onclick="openTab('accidentes')">ACCIDENTES</button>
    </div>

    <!-- PESTAÑA DELITOS -->
    <div id="delitos" class="tab-content active delitos-bg">
        <div class="form-section">
            <h2>PROCEDIMIENTO</h2>
            <div class="form-row">
                <div class="form-group">
                    <label>TIPO DE DELITO:</label>
                    <input type="text" id="del-tipo">
                </div>
            </div>
            <div class="form-row">
                <div class="form-group">
                    <label>FECHA:</label>
                    <input type="date" id="del-fecha">
                </div>
                <div class="form-group">
                    <label>HORA:</label>
                    <input type="time" id="del-hora">
                </div>
                <div class="form-group">
                    <label>LUGAR:</label>
                    <input type="text" id="del-lugar">
                </div>
            </div>
            <div class="form-row">
                <div class="form-group">
                    <label>CUADRANTE:</label>
                    <input type="text" id="del-cuadrante">
                </div>
                <div class="form-group">
                    <label>FUNCIONARIOS:</label>
                    <input type="text" id="del-funcionarios">
                </div>
            </div>
        </div>

        <div class="form-section">
            <h2>DATOS DE LA VICTIMA</h2>
            <div class="form-row">
                <div class="form-group">
                    <label>NOMBRE:</label>
                    <input type="text" id="del-victima-nombre">
                </div>
                <div class="form-group">
                    <label>RUN:</label>
                    <input type="text" id="del-victima-run">
                </div>
            </div>
            <div class="form-row">
                <div class="form-group">
                    <label>DOMICILIO:</label>
                    <input type="text" id="del-victima-domicilio">
                </div>
                <div class="form-group">
                    <label>FONO:</label>
                    <input type="tel" id="del-victima-fono">
                </div>
            </div>
            <div class="form-row">
                <div class="form-group">
                    <label>CORREO:</label>
                    <input type="email" id="del-victima-correo">
                </div>
            </div>
        </div>

        <div class="form-section">
            <h2>ESPECIES SUSTRAIDAS</h2>
            <div class="form-group">
                <textarea id="del-especies"></textarea>
            </div>
        </div>

        <div class="form-section">
            <h2>AVALUO</h2>
            <div class="form-group">
                <textarea id="del-avaluo"></textarea>
            </div>
        </div>

        <div class="form-section">
            <h2>DATOS DEL VEHICULO</h2>
            <div class="form-row">
                <div class="form-group">
                    <label>PPU:</label>
                    <input type="text" id="del-vehiculo-ppu">
                </div>
                <div class="form-group">
                    <label>MARCA:</label>
                    <input type="text" id="del-vehiculo-marca">
                </div>
            </div>
            <div class="form-row">
                <div class="form-group">
                    <label>MODELO:</label>
                    <input type="text" id="del-vehiculo-modelo">
                </div>
                <div class="form-group">
                    <label>COLOR:</label>
                    <input type="text" id="del-vehiculo-color">
                </div>
            </div>
        </div>

        <div class="form-section">
            <div class="checkbox-section">
                <label>
                    <input type="checkbox" id="del-detenido-check" onchange="toggleDetenidos()">
                    DETENIDO(S)
                </label>
            </div>
            <div id="del-detenidos-container" class="hidden">
                <div id="del-detenidos-list"></div>
                <button class="add-btn" onclick="addDetenido()">+ AGREGAR OTRO DETENIDO</button>
            </div>
        </div>

        <div class="form-section">
            <h2>HECHOS</h2>
            <div class="form-group">
                <textarea id="del-hechos"></textarea>
            </div>
        </div>

        <div class="form-section">
            <h2>PERSONAL</h2>
            <div class="personnel-section">
                <div class="form-group">
                    <label>PERSONAL BOMBEROS:</label>
                    <input type="text" id="del-bomberos">
                </div>
                <div class="form-group">
                    <label>PERSONAL DE SALUD:</label>
                    <input type="text" id="del-salud">
                </div>
                <div class="form-group">
                    <label>PERSONAL POLICIAL:</label>
                    <input type="text" id="del-policial">
                </div>
            </div>
        </div>

        <div class="btn-container">
            <button class="send-btn" onclick="sendWhatsApp('delitos')">
                ENVIAR POR WHATSAPP
            </button>
            <button class="clear-btn" onclick="clearForm('delitos')">
                LIMPIAR FORMULARIO
            </button>
        </div>
    </div>

    <!-- PESTAÑA ACCIDENTES -->
    <div id="accidentes" class="tab-content accidentes-bg">
        <div class="form-section">
            <h2>PROCEDIMIENTO</h2>
            <div class="form-row">
                <div class="form-group">
                    <label>TIPO DE ACCIDENTE:</label>
                    <input type="text" id="acc-tipo">
                </div>
            </div>
            <div class="form-row">
                <div class="form-group">
                    <label>FECHA:</label>
                    <input type="date" id="acc-fecha">
                </div>
                <div class="form-group">
                    <label>HORA:</label>
                    <input type="time" id="acc-hora">
                </div>
                <div class="form-group">
                    <label>LUGAR:</label>
                    <input type="text" id="acc-lugar">
                </div>
            </div>
            <div class="form-row">
                <div class="form-group">
                    <label>CUADRANTE:</label>
                    <input type="text" id="acc-cuadrante">
                </div>
                <div class="form-group">
                    <label>FUNCIONARIOS:</label>
                    <input type="text" id="acc-funcionarios">
                </div>
            </div>
        </div>

        <div class="form-section">
            <div class="checkbox-section">
                <label>
                    <input type="checkbox" id="acc-lesionado-check" onchange="toggleLesionados()">
                    DATOS DEL/LOS LESIONADO(S)
                </label>
            </div>
            <div id="acc-lesionados-container" class="hidden">
                <div id="acc-lesionados-list"></div>
                <button class="add-btn" onclick="addLesionado()">+ AGREGAR OTRO LESIONADO</button>
            </div>
        </div>

        <div class="form-section">
            <h2>ENFERMEDADES DE BASE</h2>
            <div class="form-group">
                <textarea id="acc-enfermedades"></textarea>
            </div>
        </div>

        <div class="form-section">
            <h2>MEDICAMENTOS</h2>
            <div class="form-group">
                <textarea id="acc-medicamentos"></textarea>
            </div>
        </div>

        <div class="form-section">
            <div class="checkbox-section">
                <label>
                    <input type="checkbox" id="acc-vehiculo-check" onchange="toggleVehiculos()">
                    DATOS DEL/LOS VEHICULO(S)
                </label>
            </div>
            <div id="acc-vehiculos-container" class="hidden">
                <div id="acc-vehiculos-list"></div>
                <button class="add-btn" onclick="addVehiculo()">+ AGREGAR OTRO VEHICULO</button>
            </div>
        </div>

        <div class="form-section">
            <h2>HECHOS</h2>
            <div class="form-group">
                <textarea id="acc-hechos"></textarea>
            </div>
        </div>

        <div class="form-section">
            <h2>PERSONAL</h2>
            <div class="personnel-section">
                <div class="form-group">
                    <label>PERSONAL BOMBEROS:</label>
                    <input type="text" id="acc-bomberos">
                </div>
                <div class="form-group">
                    <label>PERSONAL DE SALUD:</label>
                    <input type="text" id="acc-salud">
                </div>
                <div class="form-group">
                    <label>PERSONAL POLICIAL:</label>
                    <input type="text" id="acc-policial">
                </div>
            </div>
        </div>

        <div class="btn-container">
            <button class="send-btn" onclick="sendWhatsApp('accidentes')">
                ENVIAR POR WHATSAPP
            </button>
            <button class="clear-btn" onclick="clearForm('accidentes')">
                LIMPIAR FORMULARIO
            </button>
        </div>
    </div>

    <script>
        let detenidoCount = 0;
        let lesionadoCount = 0;
        let vehiculoCount = 0;

        function openTab(tabName) {
            document.querySelectorAll('.tab-content').forEach(tab => {
                tab.classList.remove('active');
            });
            document.querySelectorAll('.tab-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            document.getElementById(tabName).classList.add('active');
            event.target.classList.add('active');
        }

        function toggleDetenidos() {
            const container = document.getElementById('del-detenidos-container');
            const checkbox = document.getElementById('del-detenido-check');
            if (checkbox.checked) {
                container.classList.remove('hidden');
                if (detenidoCount === 0) addDetenido();
            } else {
                container.classList.add('hidden');
            }
        }

        function addDetenido() {
            detenidoCount++;
            const list = document.getElementById('del-detenidos-list');
            const div = document.createElement('div');
            div.className = 'dynamic-item';
            div.id = `detenido-${detenidoCount}`;
            div.innerHTML = `
                <button class="remove-btn" onclick="removeDetenido(${detenidoCount})">×</button>
                <h4>DETENIDO ${detenidoCount}</h4>
                <div class="form-row">
                    <div class="form-group">
                        <label>NOMBRE:</label>
                        <input type="text" id="del-det-nombre-${detenidoCount}">
                    </div>
                    <div class="form-group">
                        <label>RUN:</label>
                        <input type="text" id="del-det-run-${detenidoCount}">
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label>DOMICILIO:</label>
                        <input type="text" id="del-det-domicilio-${detenidoCount}">
                    </div>
                </div>
            `;
            list.appendChild(div);
        }

        function removeDetenido(id) {
            const item = document.getElementById(`detenido-${id}`);
            if (item) item.remove();
        }

        function toggleLesionados() {
            const container = document.getElementById('acc-lesionados-container');
            const checkbox = document.getElementById('acc-lesionado-check');
            if (checkbox.checked) {
                container.classList.remove('hidden');
                if (lesionadoCount === 0) addLesionado();
            } else {
                container.classList.add('hidden');
            }
        }

        function addLesionado() {
            lesionadoCount++;
            const list = document.getElementById('acc-lesionados-list');
            const div = document.createElement('div');
            div.className = 'dynamic-item';
            div.id = `lesionado-${lesionadoCount}`;
            div.innerHTML = `
                <button class="remove-btn" onclick="removeLesionado(${lesionadoCount})">×</button>
                <h4>LESIONADO ${lesionadoCount}</h4>
                <div class="form-row">
                    <div class="form-group">
                        <label>NOMBRE:</label>
                        <input type="text" id="acc-les-nombre-${lesionadoCount}">
                    </div>
                    <div class="form-group">
                        <label>RUN:</label>
                        <input type="text" id="acc-les-run-${lesionadoCount}">
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label>EDAD:</label>
                        <input type="number" id="acc-les-edad-${lesionadoCount}">
                    </div>
                    <div class="form-group">
                        <label>DOMICILIO:</label>
                        <input type="text" id="acc-les-domicilio-${lesionadoCount}">
                    </div>
                    <div class="form-group">
                        <label>FONO:</label>
                        <input type="tel" id="acc-les-fono-${lesionadoCount}">
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label>PA:</label>
                        <input type="text" id="acc-les-pa-${lesionadoCount}">
                    </div>
                    <div class="form-group">
                        <label>FC:</label>
                        <input type="text" id="acc-les-fc-${lesionadoCount}">
                    </div>
                    <div class="form-group">
                        <label>FR:</label>
                        <input type="text" id="acc-les-fr-${lesionadoCount}">
                    </div>
                    <div class="form-group">
                        <label>SAT:</label>
                        <input type="text" id="acc-les-sat-${lesionadoCount}">
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label>EGT:</label>
                        <input type="text" id="acc-les-egt-${lesionadoCount}">
                    </div>
                    <div class="form-group">
                        <label>T°:</label>
                        <input type="text" id="acc-les-temp-${lesionadoCount}">
                    </div>
                    <div class="form-group">
                        <label>EVA:</label>
                        <input type="text" id="acc-les-eva-${lesionadoCount}">
                    </div>
                    <div class="form-group">
                        <label>CINCINNATI:</label>
                        <input type="text" id="acc-les-cincinnati-${lesionadoCount}">
                    </div>
                </div>
            `;
            list.appendChild(div);
        }

        function removeLesionado(id) {
            const item = document.getElementById(`lesionado-${id}`);
            if (item) item.remove();
        }

        function toggleVehiculos() {
            const container = document.getElementById('acc-vehiculos-container');
            const checkbox = document.getElementById('acc-vehiculo-check');
            if (checkbox.checked) {
                container.classList.remove('hidden');
                if (vehiculoCount === 0) addVehiculo();
            } else {
                container.classList.add('hidden');
            }
        }

        function addVehiculo() {
            vehiculoCount++;
            const list = document.getElementById('acc-vehiculos-list');
            const div = document.createElement('div');
            div.className = 'dynamic-item';
            div.id = `vehiculo-acc-${vehiculoCount}`;
            div.innerHTML = `
                <button class="remove-btn" onclick="removeVehiculo(${vehiculoCount})">×</button>
                <h4>VEHICULO ${vehiculoCount}</h4>
                <div class="form-row">
                    <div class="form-group">
                        <label>PPU:</label>
                        <input type="text" id="acc-veh-ppu-${vehiculoCount}">
                    </div>
                    <div class="form-group">
                        <label>MARCA:</label>
                        <input type="text" id="acc-veh-marca-${vehiculoCount}">
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label>MODELO:</label>
                        <input type="text" id="acc-veh-modelo-${vehiculoCount}">
                    </div>
                    <div class="form-group">
                        <label>COLOR:</label>
                        <input type="text" id="acc-veh-color-${vehiculoCount}">
                    </div>
                </div>
                <h4>DATOS DEL CONDUCTOR</h4>
                <div class="form-row">
                    <div class="form-group">
                        <label>NOMBRE:</label>
                        <input type="text" id="acc-veh-cond-nombre-${vehiculoCount}">
                    </div>
                    <div class="form-group">
                        <label>RUN:</label>
                        <input type="text" id="acc-veh-cond-run-${vehiculoCount}">
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label>DOMICILIO:</label>
                        <input type="text" id="acc-veh-cond-domicilio-${vehiculoCount}">
                    </div>
                    <div class="form-group">
                        <label>FONO:</label>
                        <input type="tel" id="acc-veh-cond-fono-${vehiculoCount}">
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label>LICENCIA DE CONDUCIR CLASE:</label>
                        <div class="checkbox-group">
                            <label><input type="checkbox" name="lic-clase-${vehiculoCount}" value="A1"> A1</label>
                            <label><input type="checkbox" name="lic-clase-${vehiculoCount}" value="A2"> A2</label>
                            <label><input type="checkbox" name="lic-clase-${vehiculoCount}" value="A3"> A3</label>
                            <label><input type="checkbox" name="lic-clase-${vehiculoCount}" value="A4"> A4</label>
                            <label><input type="checkbox" name="lic-clase-${vehiculoCount}" value="A5"> A5</label>
                            <label><input type="checkbox" name="lic-clase-${vehiculoCount}" value="B"> B</label>
                            <label><input type="checkbox" name="lic-clase-${vehiculoCount}" value="C"> C</label>
                            <label><input type="checkbox" name="lic-clase-${vehiculoCount}" value="D"> D</label>
                            <label><input type="checkbox" name="lic-clase-${vehiculoCount}" value="F"> F</label>
                        </div>
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label>FECHA DE VENCIMIENTO:</label>
                        <input type="date" id="acc-veh-cond-vencimiento-${vehiculoCount}">
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label>DE LA COMUNA DE:</label>
                        <input type="text" id="acc-veh-cond-comuna-${vehiculoCount}">
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label>DOCUMENTACIÓN DEL VEHÍCULO AL DÍA:</label>
                        <div class="radio-group">
                            <label>
                                <input type="radio" name="doc-vehiculo-${vehiculoCount}" value="SI"> SI
                            </label>
                            <label>
                                <input type="radio" name="doc-vehiculo-${vehiculoCount}" value="NO"> NO
                            </label>
                        </div>
                    </div>
                </div>
            `;
            list.appendChild(div);
        }

        function removeVehiculo(id) {
            const item = document.getElementById(`vehiculo-acc-${id}`);
            if (item) item.remove();
        }

        function getValue(id) {
            const el = document.getElementById(id);
            return el ? el.value : '';
        }

        function sendWhatsApp(type) {
            let message = '';

            if (type === 'delitos') {
                const tipo = getValue('del-tipo');
                const fecha = getValue('del-fecha');
                const hora = getValue('del-hora');
                const lugar = getValue('del-lugar');
                const cuadrante = getValue('del-cuadrante');
                const funcionarios = getValue('del-funcionarios');

                const vn = getValue('del-victima-nombre');
                const vr = getValue('del-victima-run');
                const vd = getValue('del-victima-domicilio');
                const vf = getValue('del-victima-fono');
                const vc = getValue('del-victima-correo');

                const especies = getValue('del-especies');
                const avaluo = getValue('del-avaluo');

                const vp = getValue('del-vehiculo-ppu');
                const vm = getValue('del-vehiculo-marca');
                const vmol = getValue('del-vehiculo-modelo');
                const vco = getValue('del-vehiculo-color');

                const hechos = getValue('del-hechos');
                const bomberos = getValue('del-bomberos');
                const salud = getValue('del-salud');
                const policial = getValue('del-policial');

                message = `*INFORME DE DELITOS*\n\n`;

                if (tipo) message += `*TIPO DE DELITO:* ${tipo}\n\n`;

                if (fecha || hora || lugar || cuadrante || funcionarios) {
                    message += `*PROCEDIMIENTO:*\n`;
                    if (fecha) message += `*FECHA:* ${fecha}\n`;
                    if (hora) message += `*HORA:* ${hora}\n`;
                    if (lugar) message += `*LUGAR:* ${lugar}\n`;
                    if (cuadrante) message += `*CUADRANTE:* ${cuadrante}\n`;
                    if (funcionarios) message += `*FUNCIONARIOS:* ${funcionarios}\n`;
                    message += '\n';
                }

                if (vn || vr || vd || vf || vc) {
                    message += `*DATOS DE LA VICTIMA:*\n`;
                    if (vn) message += `*NOMBRE:* ${vn}\n`;
                    if (vr) message += `*RUN:* ${vr}\n`;
                    if (vd) message += `*DOMICILIO:* ${vd}\n`;
                    if (vf) message += `*FONO:* ${vf}\n`;
                    if (vc) message += `*CORREO:* ${vc}\n`;
                    message += '\n';
                }

                if (especies) message += `*ESPECIES SUSTRAIDAS:*\n${especies}\n\n`;
                if (avaluo) message += `*AVALUO:*\n${avaluo}\n\n`;

                if (vp || vm || vmol || vco) {
                    message += `*DATOS DEL VEHICULO:*\n`;
                    if (vp) message += `*PPU:* ${vp}\n`;
                    if (vm) message += `*MARCA:* ${vm}\n`;
                    if (vmol) message += `*MODELO:* ${vmol}\n`;
                    if (vco) message += `*COLOR:* ${vco}\n`;
                    message += '\n';
                }

                if (document.getElementById('del-detenido-check').checked) {
                    const items = document.querySelectorAll('#del-detenidos-list .dynamic-item');
                    if (items.length > 0) {
                        message += `*DETENIDOS:*\n`;
                        items.forEach((item, index) => {
                            const num = index + 1;
                            const nombre = getValue(`del-det-nombre-${num}`);
                            const run = getValue(`del-det-run-${num}`);
                            const domicilio = getValue(`del-det-domicilio-${num}`);
                            if (nombre || run || domicilio) {
                                message += `\n*DETENIDO ${num}:*\n`;
                                if (nombre) message += `*NOMBRE:* ${nombre}\n`;
                                if (run) message += `*RUN:* ${run}\n`;
                                if (domicilio) message += `*DOMICILIO:* ${domicilio}\n`;
                            }
                        });
                        message += '\n';
                    }
                }

                if (hechos) message += `*HECHOS:*\n${hechos}\n\n`;
                if (bomberos) message += `*PERSONAL BOMBEROS:* ${bomberos}\n`;
                if (salud) message += `*PERSONAL DE SALUD:* ${salud}\n`;
                if (policial) message += `*PERSONAL POLICIAL:* ${policial}\n`;

            } else if (type === 'accidentes') {
                const tipo = getValue('acc-tipo');
                const fecha = getValue('acc-fecha');
                const hora = getValue('acc-hora');
                const lugar = getValue('acc-lugar');
                const cuadrante = getValue('acc-cuadrante');
                const funcionarios = getValue('acc-funcionarios');

                const enfermedades = getValue('acc-enfermedades');
                const medicamentos = getValue('acc-medicamentos');
                const hechos = getValue('acc-hechos');
                const bomberos = getValue('acc-bomberos');
                const salud = getValue('acc-salud');
                const policial = getValue('acc-policial');

                message = `*INFORME DE ACCIDENTES*\n\n`;

                if (tipo) message += `*TIPO DE ACCIDENTE:* ${tipo}\n\n`;

                if (fecha || hora || lugar || cuadrante || funcionarios) {
                    message += `*PROCEDIMIENTO:*\n`;
                    if (fecha) message += `*FECHA:* ${fecha}\n`;
                    if (hora) message += `*HORA:* ${hora}\n`;
                    if (lugar) message += `*LUGAR:* ${lugar}\n`;
                    if (cuadrante) message += `*CUADRANTE:* ${cuadrante}\n`;
                    if (funcionarios) message += `*FUNCIONARIOS:* ${funcionarios}\n`;
                    message += '\n';
                }

                if (document.getElementById('acc-lesionado-check').checked) {
                    const items = document.querySelectorAll('#acc-lesionados-list .dynamic-item');
                    if (items.length > 0) {
                        message += `*LESIONADOS:*\n`;
                        items.forEach((item, index) => {
                            const num = index + 1;
                            const nombre = getValue(`acc-les-nombre-${num}`);
                            const run = getValue(`acc-les-run-${num}`);
                            const edad = getValue(`acc-les-edad-${num}`);
                            const domicilio = getValue(`acc-les-domicilio-${num}`);
                            const fono = getValue(`acc-les-fono-${num}`);
                            const pa = getValue(`acc-les-pa-${num}`);
                            const fc = getValue(`acc-les-fc-${num}`);
                            const fr = getValue(`acc-les-fr-${num}`);
                            const sat = getValue(`acc-les-sat-${num}`);
                            const egt = getValue(`acc-les-egt-${num}`);
                            const temp = getValue(`acc-les-temp-${num}`);
                            const eva = getValue(`acc-les-eva-${num}`);
                            const cincinnati = getValue(`acc-les-cincinnati-${num}`);

                            if (nombre || run || edad || domicilio || fono || pa || fc || fr || sat || egt || temp || eva || cincinnati) {
                                message += `\n*LESIONADO ${num}:*\n`;
                                if (nombre) message += `*NOMBRE:* ${nombre}\n`;
                                if (run) message += `*RUN:* ${run}\n`;
                                if (edad) message += `*EDAD:* ${edad}\n`;
                                if (domicilio) message += `*DOMICILIO:* ${domicilio}\n`;
                                if (fono) message += `*FONO:* ${fono}\n`;
                                if (pa) message += `*PA:* ${pa}\n`;
                                if (fc) message += `*FC:* ${fc}\n`;
                                if (fr) message += `*FR:* ${fr}\n`;
                                if (sat) message += `*SAT:* ${sat}\n`;
                                if (egt) message += `*EGT:* ${egt}\n`;
                                if (temp) message += `*T°:* ${temp}\n`;
                                if (eva) message += `*EVA:* ${eva}\n`;
                                if (cincinnati) message += `*CINCINNATI:* ${cincinnati}\n`;
                            }
                        });
                        message += '\n';
                    }
                }

                if (enfermedades) message += `*ENFERMEDADES DE BASE:*\n${enfermedades}\n\n`;
                if (medicamentos) message += `*MEDICAMENTOS:*\n${medicamentos}\n\n`;

                if (document.getElementById('acc-vehiculo-check').checked) {
                    const items = document.querySelectorAll('#acc-vehiculos-list .dynamic-item');
                    if (items.length > 0) {
                        message += `*VEHICULOS:*\n`;
                        items.forEach((item, index) => {
                            const num = index + 1;
                            const ppu = getValue(`acc-veh-ppu-${num}`);
                            const marca = getValue(`acc-veh-marca-${num}`);
                            const modelo = getValue(`acc-veh-modelo-${num}`);
                            const color = getValue(`acc-veh-color-${num}`);
                            const condNombre = getValue(`acc-veh-cond-nombre-${num}`);
                            const condRun = getValue(`acc-veh-cond-run-${num}`);
                            const condDomicilio = getValue(`acc-veh-cond-domicilio-${num}`);
                            const condFono = getValue(`acc-veh-cond-fono-${num}`);
                            const licCheckboxes = document.querySelectorAll(`input[name="lic-clase-${num}"]:checked`);
                            const condLicencia = Array.from(licCheckboxes).map(cb => cb.value).join(', ');
                            const condVencimiento = getValue(`acc-veh-cond-vencimiento-${num}`);
                            const condComuna = getValue(`acc-veh-cond-comuna-${num}`);
                            const docRadio = document.querySelector(`input[name="doc-vehiculo-${num}"]:checked`);
                            const docVehiculo = docRadio ? docRadio.value : '';

                            if (ppu || marca || modelo || color || condNombre || condRun || condDomicilio || condFono || condLicencia || condVencimiento || condComuna || docVehiculo) {
                                message += `\n*VEHICULO ${num}:*\n`;
                                if (ppu) message += `*PPU:* ${ppu}\n`;
                                if (marca) message += `*MARCA:* ${marca}\n`;
                                if (modelo) message += `*MODELO:* ${modelo}\n`;
                                if (color) message += `*COLOR:* ${color}\n`;
                                if (condNombre || condRun || condDomicilio || condFono || condLicencia || condVencimiento || condComuna || docVehiculo) {
                                    message += `*DATOS DEL CONDUCTOR:*\n`;
                                    if (condNombre) message += `*NOMBRE:* ${condNombre}\n`;
                                    if (condRun) message += `*RUN:* ${condRun}\n`;
                                    if (condDomicilio) message += `*DOMICILIO:* ${condDomicilio}\n`;
                                    if (condFono) message += `*FONO:* ${condFono}\n`;
                                    if (condLicencia) message += `*LICENCIA DE CONDUCIR CLASE:* ${condLicencia}\n`;
                                    if (condVencimiento) message += `*FECHA DE VENCIMIENTO:* ${condVencimiento}\n`;
                                    if (condComuna) message += `*DE LA COMUNA DE:* ${condComuna}\n`;
                                    if (docVehiculo) message += `*DOCUMENTACIÓN DEL VEHÍCULO AL DÍA:* ${docVehiculo}\n`;
                                }
                            }
                        });
                        message += '\n';
                    }
                }

                if (hechos) message += `*HECHOS:*\n${hechos}\n\n`;
                if (bomberos) message += `*PERSONAL BOMBEROS:* ${bomberos}\n`;
                if (salud) message += `*PERSONAL DE SALUD:* ${salud}\n`;
                if (policial) message += `*PERSONAL POLICIAL:* ${policial}\n`;
            }

            const encodedMessage = encodeURIComponent(message);
            const whatsappUrl = `https://wa.me/?text=${encodedMessage}`;
            window.open(whatsappUrl, '_blank');
        }

        function clearForm(type) {
            if (!confirm('¿Está seguro que desea limpiar todo el formulario?')) return;

            if (type === 'delitos') {
                document.getElementById('del-tipo').value = '';
                document.getElementById('del-fecha').value = '';
                document.getElementById('del-hora').value = '';
                document.getElementById('del-lugar').value = '';
                document.getElementById('del-cuadrante').value = '';
                document.getElementById('del-funcionarios').value = '';

                document.getElementById('del-victima-nombre').value = '';
                document.getElementById('del-victima-run').value = '';
                document.getElementById('del-victima-domicilio').value = '';
                document.getElementById('del-victima-fono').value = '';
                document.getElementById('del-victima-correo').value = '';

                document.getElementById('del-especies').value = '';
                document.getElementById('del-avaluo').value = '';

                document.getElementById('del-vehiculo-ppu').value = '';
                document.getElementById('del-vehiculo-marca').value = '';
                document.getElementById('del-vehiculo-modelo').value = '';
                document.getElementById('del-vehiculo-color').value = '';

                document.getElementById('del-detenido-check').checked = false;
                document.getElementById('del-detenidos-container').classList.add('hidden');
                document.getElementById('del-detenidos-list').innerHTML = '';
                detenidoCount = 0;

                document.getElementById('del-hechos').value = '';
                document.getElementById('del-bomberos').value = '';
                document.getElementById('del-salud').value = '';
                document.getElementById('del-policial').value = '';

            } else if (type === 'accidentes') {
                document.getElementById('acc-tipo').value = '';
                document.getElementById('acc-fecha').value = '';
                document.getElementById('acc-hora').value = '';
                document.getElementById('acc-lugar').value = '';
                document.getElementById('acc-cuadrante').value = '';
                document.getElementById('acc-funcionarios').value = '';

                document.getElementById('acc-lesionado-check').checked = false;
                document.getElementById('acc-lesionados-container').classList.add('hidden');
                document.getElementById('acc-lesionados-list').innerHTML = '';
                lesionadoCount = 0;

                document.getElementById('acc-enfermedades').value = '';
                document.getElementById('acc-medicamentos').value = '';

                document.getElementById('acc-vehiculo-check').checked = false;
                document.getElementById('acc-vehiculos-container').classList.add('hidden');
                document.getElementById('acc-vehiculos-list').innerHTML = '';
                vehiculoCount = 0;

                document.getElementById('acc-hechos').value = '';
                document.getElementById('acc-bomberos').value = '';
                document.getElementById('acc-salud').value = '';
                document.getElementById('acc-policial').value = '';
            }
        }
    </script>
</body>
</html>
