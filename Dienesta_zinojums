<!DOCTYPE html>
<html lang="lv">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dienesta ziņojuma aizpildīšana</title>
    <style>
        body {
            font-family: 'Times New Roman', serif;
            margin: 0;
            padding: 0;
            color: black;
            background-color: #f9f9f9;
        }
        .form-container {
            max-width: 800px;
            margin: 20px auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
            background-color: white;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 5px;
        }
        input[type="text"], input[type="date"], textarea, select {
            width: 100%;
            padding: 8px;
            border: 1px solid #ddd;
            border-radius: 4px;
            box-sizing: border-box;
            font-family: 'Times New Roman', serif;
        }
        button {
            color: white;
            padding: 10px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            font-family: 'Times New Roman', serif;
            margin-right: 10px;
            margin-bottom: 10px;
        }
        button:hover {
            opacity: 0.9;
        }
        .document-container {
            width: 210mm;
            min-height: 297mm;
            margin: 10px auto;
            padding: 15mm;
            background-color: white;
            position: relative;
            box-shadow: 0 0 5px rgba(0,0,0,0.1);
            font-family: 'Times New Roman', serif;
            font-size: 12pt;
            display: none;
        }
        .document-container p {
            margin: 0;
            padding: 0;
            line-height: 1.5;
        }
        .hidden {
            display: none;
        }
        .action-buttons {
            text-align: center;
            margin: 20px auto;
            max-width: 800px;
            display: none;
        }
        @media print {
            .form-container, .action-buttons, button {
                display: none !important;
            }
            .document-container {
                display: block !important;
                box-shadow: none;
                margin: 0;
                padding: 15mm;
                page-break-after: always;
            }
            body {
                background: white;
            }
        }
        .employee-group {
            margin-bottom: 15px;
            border-bottom: 1px dashed #ccc;
            padding-bottom: 10px;
        }
        .signature-line {
            border-top: 1px solid black;
            width: 150px;
            display: inline-block;
            margin-left: 10px;
        }
        .bold-data {
            font-weight: bold;
            text-decoration: underline;
        }
        .common-fields {
            background-color: #f0f0f0;
            padding: 10px;
            margin-bottom: 15px;
            border-radius: 4px;
        }
        .employee-position-input {
            margin-top: 5px;
        }
        .employee-row {
            display: flex;
            margin-bottom: 15px;
            width: 100%;
        }
        .employee-name {
            width: 40%;
            text-align: left;
            padding-right: 20mm;
        }
        .employee-position {
            width: 60%;
            text-align: left;
        }
        #employeesList {
            margin-top: 2cm;
            margin-bottom: 2cm;
        }
        .underlined {
            text-decoration: underline;
            display: inline-block;
            padding-bottom: 1px;
        }
        .button-print {
            background-color: #2196F3;
        }
        .button-edit {
            background-color: #ff9800;
        }
        .button-pdf {
            background-color: #f44336;
        }
        #formContainer button[type="submit"] {
            background-color: #4CAF50;
        }
        #addEmployee {
            background-color: #4CAF50; /* Zaļa krāsa */
        }
    </style>
</head>
<body>
    <div class="form-container" id="formContainer">
        <h1>Dienesta ziņojuma aizpildīšana</h1>
        <form id="reportForm">
            <div class="form-group">
                <label for="date">Datums (sagatavošanas):</label>
                <input type="date" id="date" name="date" required>
            </div>
            
            <div class="form-group">
                <label for="fromDate">Komandēt no (diena/mēnesis/gads):</label>
                <input type="date" id="fromDate" name="fromDate" required>
            </div>
            
            <div class="form-group">
                <label for="toDate">Līdz (diena/mēnesis/gads):</label>
                <input type="date" id="toDate" name="toDate" required>
            </div>
            
            <div class="form-group">
                <label for="destination">Uz (komandējuma vieta):</label>
                <input type="text" id="destination" name="destination" required>
            </div>
            
            <div class="form-group">
                <label for="carUsed">Vai izmantosiet automašīnu?</label>
                <select id="carUsed" name="carUsed">
                    <option value="no">Nē</option>
                    <option value="yes">Jā</option>
                </select>
            </div>
            
            <div class="form-group" id="carDetailsGroup" style="display: none;">
                <label for="carDetails">Automašīnas marka un reģistrācijas numurs:</label>
                <input type="text" id="carDetails" name="carDetails">
            </div>
            
            <div class="form-group common-fields">
                <label for="employeeDept">Struktūrvienības nosaukums (kopīgs visiem darbiniekiem):</label>
                <input type="text" id="employeeDept" name="employeeDept" required>
            </div>
            
            <div class="form-group">
                <label>Darbinieki:</label>
                <div id="employeesContainer">
                    <div class="employee-group">
                        <label for="employee1">1. darbinieks - Vārds, Uzvārds:</label>
                        <input type="text" id="employee1" name="employee1" required>
                        <div class="employee-position-input">
                            <label for="employeePosition1">Amats:</label>
                            <input type="text" id="employeePosition1" name="employeePosition1" required>
                        </div>
                    </div>
                </div>
                <button type="button" id="addEmployee">Pievienot kolēģi</button>
            </div>
            
            <div class="form-group">
                <label for="workPurpose">lai veiktu sekojošus darbus/piedalītos:</label>
                <textarea id="workPurpose" name="workPurpose" rows="4" required></textarea>
            </div>
            
            <div class="form-group">
                <label for="funding">Finansējums:</label>
                <input type="text" id="funding" name="funding" required>
            </div>
            
            <div class="form-group">
                <label for="accommodation">Apmešanās vieta:</label>
                <input type="text" id="accommodation" name="accommodation" required>
            </div>
            
            <div class="form-group">
                <label for="preparedBy">Sagatavoja (Vārds, Uzvārds):</label>
                <input type="text" id="preparedBy" name="preparedBy" required>
            </div>
            
            <button type="submit">Ģenerēt dokumentu</button>
        </form>
    </div>
    
    <div id="documentContainer" class="document-container">
        <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
            <span id="documentDate" class="">datums</span>
            <span>Latvijas Vides, ģeoloģijas un meteoroloģijas centra</span>
        </div>
        <div style="text-align: right;">
            <p>Valdei</p>
        </div>
        
        <h2 style="text-align: center; margin-top: 50mm;"><strong>Dienesta ziņojums</strong></h2>
        
        <div style="margin-top: 30mm; text-align: left;">
            <p>
                Lūdzu Jūsu atļauju komandēt no
                <span style="display: inline-block; min-width: 80px; text-align: center;" class="bold-data underlined" id="fromDateCell"></span>
                līdz
                <span style="display: inline-block; min-width: 80px; text-align: center;" class="bold-data underlined" id="toDateCell"></span>
                uz:
            </p>
            <div style="margin-bottom: 20px;">
                <span style="display: inline-block; width: 186px;"></span>
                <span style="display: inline-block; min-width: 80px; font-size: 8pt; text-align: center;">diena/mēnesis/gads</span>
                <span style="display: inline-block; width: 36px;"></span>
                <span style="display: inline-block; min-width: 80px; font-size: 8pt; text-align: center;">diena/mēnesis/gads</span>
            </div>
        </div>

        <p style="text-align: center;"> <span class="bold-data underlined" id="destinationCell"></span></p>
        <p>
            Ar automašīnu:
            <span style="display: inline-block; min-width: 200px; text-align: center;" class="bold-data underlined" id="carDetailsCell"></span>
        </p>
        <div style="margin-bottom: 20px;">
            <span style="display: inline-block; width: 80px;"></span>
            <span style="display: inline-block; min-width: 200px; font-size: 8pt; text-align: center;">a/m marka, reģ. numurs</span>
        </div>

        <div style="position: relative; height: 1.5em; font-size: 12pt; margin-bottom: 5px; width: 100%;">
            <span style="position: absolute; left: 0;">sekojošus:</span>
            <span class="bold-data underlined" id="employeeDeptCell"
                style="position: absolute; left: calc(5cm + 100px); white-space: nowrap;">
            </span>
            <span style="position: absolute; left: calc(5cm + 100px); top: 5mm; font-size: 8pt;">
                struktūrvienības nosaukums
            </span>
            <span style="position: absolute; left: calc(10cm + 200px); white-space: nowrap;">
                darbinieku / us
            </span>
        </div>
        <div id="employeesList">
            <!-- Employee data will be inserted here -->
        </div>

        <p>Darba mērķis (ko veiksiet/piedalīsieties):</p>
        <p><span class="bold-data underlined" id="workPurposeCell"></span></p>
        
        <p>Finansējums: <span class="bold-data underlined" id="fundingCell"></span></p>
        <p>Apmešanās vieta: <span class="bold-data underlined" id="accommodationCell"></span></p>
        
        <div style="margin-top: 30px;">
            <p>NTDNN vadītājs</p>
            <p style="text-align: right;">Roberts Berovskis <span class="signature-line"></span></p>
            <p style="text-align: right;"> <span style="margin-left: 40px;"></span></p>
            
            <p>ITD Vadītājs</p>
            <p style="text-align: right;">Juris Braučs <span class="signature-line"></span></p>
            <p style="text-align: right;"> <span style="margin-left: 40px;"></span></p>
            
            <p>Sagatavoja:</p>
            <p style="text-align: right;"><span class="" id="preparedByCell"></span> <span class="signature-line"></span></p>
            <p style="text-align: right;"> <span style="margin-left: 40px;"></span></p>
        </div>
    </div>
    
    <div class="action-buttons hidden" id="actionButtons">
        <button onclick="window.print()" class="button-print">Printēt</button>
        <button id="editDocument" class="button-edit">Labot</button>
    </div>
    
    <script>
        // Globāli mainīgie formā ievadītajiem datiem
        let formData = {};
        let employees = [];
        let employeeCount = 1;
        
        document.getElementById('carUsed').addEventListener('change', function() {
            const carDetailsGroup = document.getElementById('carDetailsGroup');
            if (this.value === 'yes') {
                carDetailsGroup.style.display = 'block';
                document.getElementById('carDetails').required = true;
            } else {
                carDetailsGroup.style.display = 'none';
                document.getElementById('carDetails').required = false;
            }
        });
        
        document.getElementById('addEmployee').addEventListener('click', function() {
            if (employeeCount >= 5) return;
            
            employeeCount++;
            const container = document.getElementById('employeesContainer');
            const newGroup = document.createElement('div');
            newGroup.className = 'employee-group';
            newGroup.innerHTML = `
                <label for="employee${employeeCount}">${employeeCount}. darbinieks - Vārds, Uzvārds:</label>
                <input type="text" id="employee${employeeCount}" name="employee${employeeCount}" required>
                <div class="employee-position-input">
                    <label for="employeePosition${employeeCount}">Amats:</label>
                    <input type="text" id="employeePosition${employeeCount}" name="employeePosition${employeeCount}" required>
                </div>
            `;
            container.appendChild(newGroup);
        });
        
        document.getElementById('reportForm').addEventListener('submit', function(e) {
            e.preventDefault();
            generateDocument();
        });
        
        function formatDate(dateString) {
            if (!dateString) return '';
            const date = new Date(dateString);
            const day = String(date.getDate()).padStart(2, '0');
            const month = String(date.getMonth() + 1).padStart(2, '0');
            const year = date.getFullYear();
            return `${day}.${month}.${year}`;
        }
        
        function generateDocument() {
            // Saglabājam formā ievadītos datus globālajos mainīgajos
            formData = {
                date: document.getElementById('date').value,
                formattedDate: formatDate(document.getElementById('date').value),
                fromDate: document.getElementById('fromDate').value,
                formattedFromDate: formatDate(document.getElementById('fromDate').value),
                toDate: document.getElementById('toDate').value,
                formattedToDate: formatDate(document.getElementById('toDate').value),
                destination: document.getElementById('destination').value,
                carUsed: document.getElementById('carUsed').value,
                carDetails: document.getElementById('carUsed').value === 'yes' ? document.getElementById('carDetails').value : 'Nē',
                workPurpose: document.getElementById('workPurpose').value,
                funding: document.getElementById('funding').value,
                accommodation: document.getElementById('accommodation').value,
                preparedBy: document.getElementById('preparedBy').value,
                employeeDept: document.getElementById('employeeDept').value
            };
            
            // Saglabājam darbinieku datus
            employees = [];
            for (let i = 1; i <= employeeCount; i++) {
                const name = document.getElementById(`employee${i}`)?.value;
                const position = document.getElementById(`employeePosition${i}`)?.value;
                if (name) employees.push({name, position});
            }
            
            // Aizpildām dokumentu
            document.getElementById('documentDate').textContent = formData.formattedDate;
            document.getElementById('fromDateCell').textContent = formData.formattedFromDate;
            document.getElementById('toDateCell').textContent = formData.formattedToDate;
            document.getElementById('destinationCell').textContent = formData.destination;
            document.getElementById('carDetailsCell').textContent = formData.carDetails;
            document.getElementById('workPurposeCell').textContent = formData.workPurpose;
            document.getElementById('fundingCell').textContent = formData.funding;
            document.getElementById('accommodationCell').textContent = formData.accommodation;
            document.getElementById('preparedByCell').textContent = formData.preparedBy;
            document.getElementById('employeeDeptCell').textContent = formData.employeeDept;
            
            // Aizpildām darbinieku sarakstu
            const employeesList = document.getElementById('employeesList');
            employeesList.innerHTML = '';
            
            employees.forEach(employee => {
                const employeeRow = document.createElement('div');
                employeeRow.className = 'employee-row';
                
                const nameDiv = document.createElement('div');
                nameDiv.className = 'employee-name bold-data underlined';
                nameDiv.textContent = employee.name;
                
                const positionDiv = document.createElement('div');
                positionDiv.className = 'employee-position bold-data underlined';
                positionDiv.textContent = employee.position;
                
                employeeRow.appendChild(nameDiv);
                employeeRow.appendChild(positionDiv);
                employeesList.appendChild(employeeRow);
            });
            
            // Parādām dokumentu un darbību pogas
            document.getElementById('documentContainer').style.display = 'block';
            document.getElementById('actionButtons').style.display = 'block';
            document.getElementById('actionButtons').classList.remove('hidden');
            document.getElementById('formContainer').classList.add('hidden');
            
            // Ritinām uz dokumentu
            document.getElementById('documentContainer').scrollIntoView({ behavior: 'smooth' });
        }
        
        // Labošanas funkcija
        document.getElementById('editDocument').addEventListener('click', function() {
            document.getElementById('formContainer').classList.remove('hidden');
            document.getElementById('documentContainer').style.display = 'none';
            document.getElementById('actionButtons').classList.add('hidden');
            
            // Atjaunojam formu ar saglabātajiem datiem
            document.getElementById('date').value = formData.date;
            document.getElementById('fromDate').value = formData.fromDate;
            document.getElementById('toDate').value = formData.toDate;
            document.getElementById('destination').value = formData.destination;
            document.getElementById('carUsed').value = formData.carUsed;
            if (formData.carUsed === 'yes') {
                document.getElementById('carDetails').value = formData.carDetails;
                document.getElementById('carDetailsGroup').style.display = 'block';
            }
            document.getElementById('workPurpose').value = formData.workPurpose;
            document.getElementById('funding').value = formData.funding;
            document.getElementById('accommodation').value = formData.accommodation;
            document.getElementById('preparedBy').value = formData.preparedBy;
            document.getElementById('employeeDept').value = formData.employeeDept;
            
            // Atjaunojam darbinieku sarakstu
            const employeesContainer = document.getElementById('employeesContainer');
            employeesContainer.innerHTML = '';
            
            employeeCount = employees.length;
            employees.forEach((employee, index) => {
                const i = index + 1;
                const newGroup = document.createElement('div');
                newGroup.className = 'employee-group';
                newGroup.innerHTML = `
                    <label for="employee${i}">${i}. darbinieks - Vārds, Uzvārds:</label>
                    <input type="text" id="employee${i}" name="employee${i}" value="${employee.name}" required>
                    <div class="employee-position-input">
                        <label for="employeePosition${i}">Amats:</label>
                        <input type="text" id="employeePosition${i}" name="employeePosition${i}" value="${employee.position}" required>
                    </div>
                `;
                employeesContainer.appendChild(newGroup);
            });
        });
    </script>
</body>
</html>
