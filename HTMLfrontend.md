<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Lung Screening Form — Requested Format</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg: #363636;
      --card: #ffffff;
      --ink: black;
      --muted: black;
      --brand: #009FFC;
      --brand-ink: #0b6ea7;
      --ring: rgba(14,165,233,0.35);
    }
    * { box-sizing: border-box; }
    body {
      margin: 0; padding: 24px; font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      background: var(--bg); color: var(--ink);
    }
    .wrap { max-width: 980px; margin: 0 auto; }
    .title {
      background: linear-gradient(135deg, #0ea5e9, #22c55e);
      color: white; padding: 18px 22px; border-radius: 16px; box-shadow: 0 8px 24px rgba(2, 132, 199, 0.25);
      margin-bottom: 18px;
    }
    .title h1 { margin: 0 0 4px; font-size: clamp(22px, 3vw, 30px); }
    .title small { opacity: .9; }

    .grid { display: grid; grid-template-columns: 1fr; gap: 16px; }
    @media (min-width: 860px){ .grid { grid-template-columns: 1fr 1fr; } }

    .card { background: var(--card); border-radius: 14px; padding: 16px; box-shadow: 0 6px 18px rgba(0,0,0,.06); }
    .card h2 { margin: 0 0 8px; font-size: 18px; }

    label { font-size: 13px; color: var(--muted); display: block; margin-bottom: 6px; }
    input[type="text"], input[type="tel"], input[type="number"], select, textarea {
      width: 100%; padding: 10px 12px; border-radius: 10px; border: 1px solid #e5e7eb; background: #fff;
      outline: none; transition: box-shadow .2s, border-color .2s; font-size: 14px;
    }
    textarea { 
      min-height: 2px; 
      font-size: 12px;
      resize: none;}
    input:focus, select:focus, textarea:focus { border-color: var(--brand); box-shadow: 0 0 0 4px var(--ring); }
    
    .row { display: grid; grid-template-columns: 1fr; gap: 12px; }
    @media (min-width: 640px){ .row.two { grid-template-columns: repeat(2, 1fr);} }
    @media (min-width: 860px){ .row.three { grid-template-columns: repeat(3, 1fr);} }

    .checklist { display: grid; gap: 8px; margin-top: 6px; }
    .check { display: flex; align-items: start; gap: 8px; }
    .check input { margin-top: 2px; }

    .note { font-size: 12px; color: var(--muted); }

    .actions { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 14px; }
    button {
      appearance: none; border: none; border-radius: 12px; padding: 10px 14px; cursor: pointer; font-weight: 600; font-size: 14px;
      display: inline-flex; align-items: center; gap: 8px;
    }
    .primary { background: var(--brand); color: #fff; }
    .primary:hover { background: var(--brand-ink); }
    .ghost { background: white; color: black; }
    .soft { background: #e5e7eb; color: #111827; }

    .summary { white-space: pre-wrap; font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace; }
    .hr { height: 1px; background: #eef2f7; margin: 8px 0 8px; }
 
    #pumaOut { 
      color: red;
      width: 100%;
      flex: 1;            /* Take remaining space */
      font-size: 1.5em; /* Bigger */
      font-weight: bold; /* Optional */
      margin-top: 8px;   /* Spacing */
    }
    
    #smoking-card {
      background: #F75F59;  /* bright red background */
      color: white;         /* white text for contrast */
      border: 2px solid #b30000;
      box-shadow: 0 0 12px rgba(255, 0, 0, 0.6);
    }
    #smoking-card h2 {
      color: white; /* make sure the title stays readable */
    }
  
    #lungCancerAlert {
      font-size: 1.5em; /* Bigger */
      font-weight: bold; /* Optional */
      grid-column: 1 / -1; /* spans all columns */
    }
    
     #spinner {
      display: none;
      border: 3px solid #f3f3f3;
      border-top: 3px solid #fff;
      border-radius: 50%;
      width: 16px;
      height: 16px;
      animation: spin 1s linear infinite;
    }
    @keyframes spin {
       0% { transform: rotate(0deg); }
       100% { transform: rotate(360deg); }
    }
    
  </style>
</head>
<body>
  <div class="wrap">
    <!-- TITLE -->
    <div class="title">
      <h1>SARINGAN KESIHATAN PARU-PARU</h1>
      <small>KLINIK KESIHATAN BATU 9, CHERAS</small>
    </div>

    <form id="form">
      <!-- PATIENT information -->
      <div class="card">
        <h2>Patient Information</h2>
        <div class="row two">
          <div>
            <label>Name</label>
            <input type="text" id="name" name="name" required style="text-transform: uppercase;" />
          </div>
          <div>
            <label>NRIC</label>
            <input type="text" id="nric"name="nric" required style="text-transform: uppercase" />
          </div>
          <div>
            <label>Age</label>
            <input type="number" id="age" name="age" min="0" max="120" required/>
          </div>
          <div>
            <label>Gender</label>
            <select id="gender" name="gender" required>
              <option value="">Select</option>
              <option>Male</option>
              <option>Female</option>
            </select>
          </div>
          <div>
            <label>Phone no</label>
            <input type="tel" name="phone" id="phone" style="text-transform: uppercase" required/>
          </div>
          <div>
            <label>Status</label>
            <select id="status" name="status" required>
              <option value="">Select</option>
              <option>Symptomatic</option>
              <option>Asymptomatic</option>
            </select>
          </div>
        </div>
      </div>

      <!-- RISK FACTOR -->
      <div class="grid" style="margin-top: 16px;">       
        <div class="card" id="smoking-card">
          <h2>Smoking status</h2>
          <div class="checklist">
            <label class="check"><input required type="radio" id="smoke_active" name="smoke_status" value="Active smoker"> Active smoker</label>
            <label class="check"><input type="radio" id="smoke_exlt15" name="smoke_status" value="Ex-smoker <15 years"> Ex-smoker &lt; 15 years duration</label>
            <div class="row two">
              <div>
                <label>Pack year smoking</label>
                <label>Cigarettes per day:</label>
                <input type="number" id="cig_per_day" required >
                <label>Years smoked:</label>
                <input type="number" id="years_smoked" required >
                <label>Pack years:</label><input type="number" id="pack_year" required readonly>
                <small>(Pack years = (Cigarettes/day ÷ 20) × Years smoked)</small>
              </div>
            </div>
	    <label class="check"><input type="radio" id="smoke_exgt15" name="smoke_status" value="Ex-smoker >15 years"> Ex-smoker &gt; 15 years duration</label>
	    <label class="check"><input type="radio" id="smoke_never" name="smoke_status" value="Never smoke"> Never smoke</label>
          </div>
        </div>
       
        <div class="card">
          <h2>Medical risk factor</h2>
          <div class="checklist">
            <label class="check"><input type="checkbox" id="med_viral" name="medical" value="Viral infection"> Viral respiratory infections</label>
            <label class="check"><input type="checkbox" id="med_obesity" name="medical" value="Obesity"> Obesity</label>
            <label class="check"><input type="checkbox" id="med_diabetes" name="medical" value="Diabetes"> Diabetes mellitus</label>
            <label class="check"><input type="checkbox" id="med_esrf" name="medical" value="ESRF"> ESRF on dialysis</label>
            <label class="check"><input type="checkbox" id="med_copd" name="medical" value="COPD"> COPD</label>
            <label class="check"><input type="checkbox" id="med_allergies" name="medical" value="Allergies"> Allergies</label>
            <label class="check"><input type="checkbox" id="med_lung" name="medical" value="Lung condition"> History of Lung disease such as Pneumonia, TB</label>
            <label class="check"><input type="checkbox" id="med_hiv" name="medical" value="People living with HIV"> People living with HIV</label>
            <label class="check"><input type="checkbox" id="med_transplant" name="medical" value="Transplant"> Transplant patient</label>
            <label class="check"><input type="checkbox" id="med_immuno" name="medical" value="Immunocompromised"> Patient on pre-biologic, anti-TNF, cancer and steroid</label>
            <label class="check"><input type="checkbox" id="med_methadone" name="medical" value="Methadone"> Clients of methadone replacement therapy and substance abuse clinic</label>
            <label class="check"><input type="checkbox" id="med_alpha1" name="medical" value="Alpha-1 antitrypsin deficiency"> Have a rare genetic condition: Alpha-1 antitrypsin deficiency</label>
          </div>
        </div>  
      </div>

      <div class="grid" style="margin-top: 16px;">
        <div class="card">
          <h2>Personal risk factor</h2>
          <div class="checklist">
            <label class="check"><input type="checkbox" id="personal_asthma" name="personal" value="Asthma"> Family history of asthma</label>
            <label class="check"><input type="checkbox" id="personal_lungcancer" name="personal" value="Lung cancer"> Family history of lung cancer</label>
            <label class="check"><input type="checkbox" id="personal_hcw" name="personal" value="Health care worker"> Health care worker (HCW)</label>
            <label class="check"><input type="checkbox" id="personal_inmates" name="personal" value="Institutional inmates"> Institutional inmates</label>
            <label class="check"><input type="checkbox" id="personal_vulnerable" name="personal" value="Vulnerable group"> Vulnerable group such as indigenous people Orang Asli, homeless</label>
          </div>
        </div>

        <div class="card">
          <h2>Exposure risk factor</h2>
          <div class="checklist">
            <label class="check"><input type="checkbox" id="exposure_secondhand" name="exposure" value="Second hand smoker"> Second hand smoker</label>
            <label class="check"><input type="checkbox" id="exposure_tb" name="exposure" value="Contact of TB case"> Contact of Index case TB</label>
            <label class="check"><input type="checkbox" id="exposure_irritants" name="exposure" value="Long term exposure to irritants"> Long term exposure to lung irritants such as air pollution, chemical fumes, or dust from the environment or workplace</label>
            <label class="check"><input type="checkbox" id="exposure_radiation" name="exposure" value="Ionizing radiation"> Ionizing radiation (residential radon)</label>
            <label class="check"><input type="checkbox" id="exposure_occupational" name="exposure" value="Occupational Exposure"> Occupational Exposure (asbestos, silica, diesel engine exhaust, working as painter, radon, mineral oils, arsenic, working as a welder)</label>
          </div>
        </div>       
      </div>

      <div class="grid" style="margin-top: 16px;">        
        <div class="card">
          <h2>PUMA Score</h2>
          <div class="row two">
            <div>
              <label>Dyspnea</label>
              <select id="puma_dysp">
                <option value="0">No</option>
                <option value="1">Yes</option>
              </select>
            </div>
            <div>
              <label>Chronic phlegm (≥3 months)</label>
              <select id="puma_phlegm">
                <option value="0">No</option>
                <option value="1">Yes</option>
              </select>
            </div>
            <div>
              <label>Chronic cough</label>
              <select id="puma_cough">
                <option value="0">No</option>
                <option value="1">Yes</option>
              </select>
            </div>
            <div>
              <label>Advised spirometry before</label>
              <select id="puma_advice">
                <option value="0">No</option>
                <option value="1">Yes</option>
              </select>
            </div>
          </div>
          <div class="actions">
            <button type="button" class="primary" id="btnPuma" style= "width:100%; justify-content:center;">Calculate PUMA score</button>
            <div id="pumaOut" class="note"></div>
          </div>
        </div> 
        
        <div class="card">
        <h2>Risk assessment</h2>
        <div class="row two">
          <div>
            <label>Lung cancer</label>
            <textarea readonly id="assess_lc"></textarea>
          </div>
          <div>
            <label>Pulmonary TB</label>
            <textarea readonly id="assess_tb"></textarea>
          </div>
          <div>
            <label>COPD</label>
            <textarea readonly id="assess_copd"></textarea>
          </div>
          <div>
            <label>Asthma</label>
            <textarea readonly id="assess_asthma"></textarea>
          </div>
          
          <div id="lungCancerAlert" 
               style="display: none; background-color: #ffcccc; color: red; font-weight: bold; 
            margin-top: 5px; border: 2px solid red; border-radius: 6px; text-align: center; grid-column: 1/ -1">
            HIGH RISK LUNG CANCER GROUP
            <div style="font-weight: normal; color: darkred; margin-top: 4px; font-size: 0.7em;">
              Please discuss with FMS and councel patient regarding LD-CT
            </div>
          </div>
          
        </div>
       </div>
      </div>

      <!-- Ordered by -->
      <div class="card" style="margin-top: 16px;">
        <h2>Ordered by</h2>
        <input type="text" id="ordered" name="Ordered" required style="font-weight: bold; text-transform: capitalize;" placeholder="Eg: Dr Nor Hazlin Binti Talib">
      </div>
      
      <div class="card" style="margin-top: 10px;">
        <h2>Working Diagnosis</h2>
        <label for="workingDiagnosis" style="color:red; font-style: italic;">Newly added for data collection - will not be included in summary</label>
        <select id="workingDiagnosis" name="workingDiagnosis" required>
          <option value="">-- Select --</option>
          <option value="Screening">Screening (Contact TB, Medical Checkup, LHI Screening, etc)</option>
          <option value="Pneumonia">Pneumonia</option>
          <option value="Tuberculosis">Tuberculosis</option>
          <option value="Asthma">Asthma</option>
          <option value="COPD">COPD</option>
          <option value="Trauma">Trauma/ MVA</option>
          <option value="TRO Lung Cancer">TRO Lung Cancer</option>
          <option value="Other">Lain-lain</option>
        </select>

        <!-- Hidden input for 'Other' -->
        <div id="otherDiagnosis" style="display: none; margin-top: 8px;">
          <input type="text" id="otherInput" name="otherDiagnosis" placeholder="Sila nyatakan diagnosis lain">
        </div>
      </div>
      
      <!-- Note -->
      <div class="card" style="margin-top: 16px;">
        <h2>Remarks / Relevant clinical note</h2>
        <textarea name="suggestion" id="suggestion" placeholder="Example: Screening CXR, known PTB or refused intervention"></textarea>
      </div>

      <div id="summaryCard" style="display:none;">
        <textarea id="summary" readonly style="width:100%; margin-top: 10px; height:300px; resize:none; font-family:monospace; white-space:pre-wrap;">
        </textarea>
      </div>
      
      <div class="actions" style="margin-top: 10px; display: flex; gap: 5px; ">
        <button type="button" class="ghost" id="btnSummary" style="flex: 1; justify-content: center; text-align: center;">Summary</button>
        <button type="submit" class="primary" id="btnSubmit" style="flex: 1; justify-content: center; text-align: center;">Submit
          <div id="spinner"></div></button>
        <button type="button" class="soft" id="btnClear" style="flex: 1; justify-content: center; text-align: center;">Clear result</button>
      </div>

    </form>
     <div id="spinner"></div>
  </div>

  <script>
    // Calculate Pack Year
    function calcPackYear() {
      const cigPerDay = parseFloat(document.getElementById('cig_per_day').value) || 0;
      const yearsSmoked = parseFloat(document.getElementById('years_smoked').value) || 0;
      const packYear = (cigPerDay / 20) * yearsSmoked;
      document.getElementById('pack_year').value = packYear.toFixed(1);
    }
    // 🔹 Update fields when smoke status changes
    // 🔹 Reset inputs when Ex-smoker >15 or Never is chosen
    document.querySelectorAll('input[name="smoke_status"]').forEach(el => {
      el.addEventListener('change', () => {
        if (el.id === 'smoke_exgt15' || el.id === 'smoke_never') {
          document.getElementById('cig_per_day').value = 0;
          document.getElementById('years_smoked').value = 0;
          document.getElementById('pack_year').value = 0;
        }       
        calcPackYear();        
        checkLungCancerRiskDynamic();
        clearPumaResult();
        });
      });
   
    // 🔹 Auto-update pack years when inputs change
    ['cig_per_day', 'years_smoked'].forEach(id => {document.getElementById(id).addEventListener('input', () => {
      calcPackYear();clearPumaResult();});});

    // 🔹 Clear PUMA result when inputs change    
    function clearPumaResult() {
      const outDiv = document.getElementById('pumaOut');
      outDiv.textContent = '';           
      outDiv.style.backgroundColor = 'transparent';
      outDiv.style.padding = '0';
    }
    document.querySelectorAll('[name="age"], [name="gender"], #cig_per_day, #years_smoked, input[name="smoke_status"], #puma_dysp, #puma_phlegm, #puma_cough, #puma_advice')
    .forEach(el => {    
      el.addEventListener('input', clearPumaResult);
      el.addEventListener('change', clearPumaResult);
    });
    
    // PUMA score calculation
    function calcPuma() {
      const age = parseInt(document.querySelector('[name="age"]').value) || 0;
      const gender = (document.querySelector('[name="gender"]').value || '').toLowerCase();
      const packYear = parseFloat(document.getElementById('pack_year').value) || 0;
      const dyspnea = parseInt(document.getElementById('puma_dysp').value) || 0;
      const phlegm = parseInt(document.getElementById('puma_phlegm').value) || 0;
      const cough = parseInt(document.getElementById('puma_cough').value) || 0;
      const advice = parseInt(document.getElementById('puma_advice').value) || 0;

    let score = 0;
    if (gender === 'male') score += 1;
    if (age >= 50 && age <= 59) score += 1;
    else if (age >= 60 && age <= 69) score += 2;
    if (packYear >= 20 && packYear <= 30) score += 1;    
      else if (packYear > 30) score += 2;
      else if (packYear < 20) score += 0; 
    if (advice === 1) score += 1;
    if (dyspnea === 1) score += 1;
    if (phlegm === 1) score += 1;
    if (cough === 1) score += 1;

    let msg = `PUMA score: ${score} → `;
    msg += (score >= 5)
      ? "High risk for COPD. Suggest for spirometry"
      : "Low to moderate risk";

    return { score, msg };
  }

     // Helpers for PUMA button calculation (radio + checkbox)
        function checkedValues(name) {
        return Array.from(document.querySelectorAll(`[name="${name}"]:checked`)).map(x => x.value);
      }
        function radioValue(name) {
          const el = document.querySelector(`[name="${name}"]:checked`);
          return el ? el.value : '';
        }
        let currentPuma = { score: 0, msg: '' };    
    
      // Modify the PUMA button click to store result once
      const btnPuma = document.getElementById('btnPuma');
      btnPuma.addEventListener('click', () => {
        const ageInput = document.querySelector('[name="age"]');
        const genderInput = document.querySelector('[name="gender"]');
        const ciggDay = document.getElementById('cig_per_day');
        const ciggyear = document.getElementById('years_smoked');
        const packyear   = document.getElementById('pack_year');

        let valid = true;
        [ciggDay, ciggyear, packyear].forEach(el => {
          if (el.value === '') {
            el.reportValidity();
            valid = false;
          }
        });

        // Must not be empty (and 0 is not allowed here)
        [ageInput, genderInput].forEach(el => {
          if (!el.value) {
            el.reportValidity();
            valid = false;
          }
        });
        if (!valid) return;

        // Store the PUMA result once
        currentPuma = calcPuma();
        const outDiv = document.getElementById('pumaOut');
        outDiv.textContent = currentPuma.msg;

        if (currentPuma.score >= 5) {
          outDiv.style.color = 'white';
          outDiv.style.backgroundColor = '#F54927';
          outDiv.style.padding = '6px';
          outDiv.style.borderRadius = '6px';
        } else {
          outDiv.style.color = 'black';
          outDiv.style.backgroundColor = 'transparent';
          outDiv.style.padding = '0';
        }
      });
    
    
    // Mapping of checkbox IDs to textareas for risk categorization
    const riskMap = {
      med_viral: ['assess_asthma'],
      med_obesity: ['assess_asthma'],
      med_diabetes: ['assess_tb'],
      med_esrf: ['assess_tb'],
      med_copd: ['assess_tb', 'assess_lc'],
      med_allergies: ['assess_asthma'],
      med_lung: ['assess_lc'],
      med_hiv: ['assess_tb'],
      med_transplant: ['assess_tb'],
      med_immuno: ['assess_tb'],
      med_methadone: ['assess_tb'],
      med_alpha1: ['assess_copd'],    
      
      personal_asthma: ['assess_asthma'],
      personal_lungcancer: ['assess_lc'],
      personal_hcw: ['assess_tb'],
      personal_inmates: ['assess_tb'],
      personal_vulnerable: ['assess_tb'],
           
      exposure_tb: ['assess_tb'],
      exposure_secondhand: ['assess_lc'],
      exposure_irritants: ['assess_copd', 'assess_lc'],
      exposure_radiation: ['assess_copd', 'assess_lc'],
      exposure_occupational: ['assess_copd', 'assess_asthma', 'assess_lc' ],
      
      smoke_active: ['assess_copd', 'assess_asthma', 'assess_lc'],
      smoke_exlt15: ['assess_copd', 'assess_asthma', 'assess_lc'],
      smoke_exgt15: ['assess_copd', 'assess_asthma', 'assess_lc']  
    }; 
    // Update user selection into textareas based on selection
    function updateRiskAssessment() {
      const textareas = ['assess_lc', 'assess_tb', 'assess_copd', 'assess_asthma'];
      textareas.forEach(id => document.getElementById(id).value = '');     
      

      // Loop through mapped checkboxes
      Object.keys(riskMap).forEach(id => {
        const el = document.getElementById(id);
        if (el && el.checked) {
          riskMap[id].forEach(textareaId => {
            const ta = document.getElementById(textareaId);
            if (ta.value) ta.value += ', ';
            ta.value += el.value;
          });
        }
      });
    }
    // Bind change events to include in textarea for risk factor
    document.querySelectorAll('input[type="radio"], input[type="checkbox"]').forEach(el => {
      el.addEventListener('change', updateRiskAssessment);
    });   
    // call function to display high risk for lung cancer group
    function checkLungCancerRiskDynamic() {
      const age = parseInt(document.querySelector('[name="age"]').value) || 0;
      const packYear = parseFloat(document.getElementById('pack_year').value) || 0;

      const smokerId = ['smoke_active', 'smoke_exlt15'];
      const isSmoker = smokerId.some(id => document.getElementById(id).checked);

      const exposureSelected = Array.from(document.querySelectorAll('input[name="exposure"]:checked')).length > 0;

      const familyHistory = document.getElementById('personal_lungcancer').checked;
      const lungHistory = document.getElementById('med_lung').checked;
      const copd = document.getElementById('med_copd').checked;

      const A = age >= 50 && age <= 70;
      const B_and_C = isSmoker && packYear >= 20;
      const D = exposureSelected; 
      const E = familyHistory;
      const F = lungHistory;
      const G = copd;

      const highRisk = (A && B_and_C) || (A && D && (E||F||G));

      const alertBox = document.getElementById("lungCancerAlert");
      alertBox.style.display = highRisk ? "block" : "none";
    }
    // Bind events for all relevant inputs to be displayed lung cancer dynamic
    const inputs = [
      '[name="age"]', 
      '#pack_year', 
      '#smoke_active', '#smoke_exlt15', '#smoke_exgt15', '#smoke_never',
      'input[name="exposure"]',
      '#personal_lungcancer',
      '#med_copd',
      '#med_lung'
    ];
    // based on user selection of risk factor, for automatic display of lung cancer dynamic
    inputs.forEach(selector => {
      document.querySelectorAll(selector).forEach(el => el.addEventListener('change', checkLungCancerRiskDynamic));
    });
    // Also for lung cancer dynamic, to identify high risk group based on smoking status 
    document.getElementById('cig_per_day').addEventListener('input', () => {
      calcPackYear();
      checkLungCancerRiskDynamic();
    });
    document.getElementById('years_smoked').addEventListener('input', () => {
      calcPackYear();
      checkLungCancerRiskDynamic();
    });    
    
    // Summary builder - patch data to create summary template
    document.getElementById('btnSummary').addEventListener('click', () => {
      const f = document.getElementById('form');
      const personal = checkedValues('personal');
      const exposure = checkedValues('exposure');
      const medical = checkedValues('medical');
      const lungRisk = document.getElementById('lungCancerAlert').style.display === 'block' 
  ? '⚠️ High Risk for Lung Cancer⚠️'
  : '';

    const lines = [
    `SARINGAN KESIHATAN PARU-PARU`,'',
     lungRisk,
    `Name: ${f.name.value || ''}`,
    `NRIC: ${f.nric.value || ''}`,
    `Age: ${f.age.value || ''}`,
    `Gender: ${f.gender.value || ''}`,
    `Phone no: ${f.phone.value || ''}`,
    `Status: ${f.status.value || ''}`,
    '',
    `Smoking status: ${radioValue('smoke_status') || ''}`,
    `Pack year smoking: ${f.pack_year.value || ''}`,
     currentPuma.msg,
    `Personal risk factor: ${personal.join(', ') || ''}`,
    `Exposure risk factor: ${exposure.join(', ') || ''}`,
    `Medical risk factor: ${medical.join(', ') || ''}`,
    '',
    `Remarks: ${f.suggestion.value || ''}`,
    
    ].join('\n');

      document.getElementById('summary').value = lines;
      document.getElementById('summaryCard').style.display = 'block';
    });


    // Clear Button event listener
    document.getElementById('btnClear').addEventListener('click', () => {
      document.getElementById('form').reset();
      
      // Reset PUMA output
      const pumaDiv = document.getElementById('pumaOut');
      pumaDiv.textContent = '';
      pumaDiv.style.color = 'black';
      pumaDiv.style.backgroundColor = 'transparent';
      pumaDiv.style.padding = '0';
      pumaDiv.style.borderRadius = '0';

      document.getElementById('pumaOut').textContent = '';
      document.getElementById('lungCancerAlert').style.display = 'none';
      document.getElementById('summary').textContent = '';
      document.getElementById('summaryCard').style.display = 'none';
    });

    // 🔹 Working Diagnosis show/hide logic
      const workingDiagnosis = document.getElementById("workingDiagnosis");
      const otherDiagnosisDiv = document.getElementById("otherDiagnosis");
      const otherInput = document.getElementById("otherInput");

      workingDiagnosis.addEventListener("change", function () {
        if (this.value === "Other") {
          otherDiagnosisDiv.style.display = "block";
        } else {
          otherDiagnosisDiv.style.display = "none";
          otherInput.value = ""; // reset if not used
        }
      });   
    
    // Preparation for submit button eventlistener
    // wrap it in button submit listener
    // call an object for payload
    const form = document.getElementById('form');
    const spinner = document.getElementById('spinner');

    form.addEventListener('submit', function(e) {
      // Use native validation first
      if (!form.checkValidity()) {
        // Trigger browser built-in "Please fill out this field" messages
        form.reportValidity();
        e.preventDefault();
        return;
      }

      e.preventDefault(); // Only run if form is valid
      spinner.style.display = 'inline-block';

      const payload = {
        name: form.name.value.toUpperCase(),
        nric: form.nric.value,
        phone: form.phone.value,
        status: form.status.value,
        suggestion: form.suggestion ? form.suggestion.value : '',
        age: form.age.value,
        gender: form.gender.value,
        smoke_status: radioValue('smoke_status'),
        pack_year: form.pack_year ? form.pack_year.value : '',
        puma_score: currentPuma ? currentPuma.score : '',
        assess_lc: document.getElementById('assess_lc') ? document.getElementById('assess_lc').value : '',
        assess_tb: document.getElementById('assess_tb') ? document.getElementById('assess_tb').value : '',
        assess_copd: document.getElementById('assess_copd') ? document.getElementById('assess_copd').value : '',
        assess_asthma: document.getElementById('assess_asthma') ? document.getElementById('assess_asthma').value : '',
        high_risk_note: document.getElementById('lungCancerAlert') && document.getElementById('lungCancerAlert').style.display === 'block' ? 'High Risk' : 'Low Risk',
        Ordered: form.ordered.value.toUpperCase(),
        workingDiagnosis: (workingDiagnosis.value === "Other" && otherInput.value.trim() !== "")
          ? otherInput.value.trim()
          : workingDiagnosis.value
      };

      fetch('https://script.google.com/macros/s/AKfycbyv1LVmQ6prD0-YhIzlUb29SAT4tu-xTN72RQ1CHZ6i7Fxc-yNSRraHs_NF3xyIs76qSw/exec', {
        method: 'POST',
        mode: 'no-cors',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(payload)
      })
      .then(() => {
        spinner.style.display = 'none';
        alert('Maklumat berjaya dihantar!');
        form.reset();
        document.getElementById('summaryCard').style.display = 'none';
        document.getElementById('pumaOut').style.display = '';
        document.getElementById('lungCancerAlert').style.display = 'none';
        document.getElementById('summary').textContent = '';
        document.getElementById('workingDiagnosis').style.display = '';
        document.getElementById('otherDiagnosis').style.display = 'none';
        document.getElementById('otherInput').value = "";
      })
      .catch(err => {
        spinner.style.display = 'none';
        console.error('Submission error:', err);
        alert('Ralat semasa penghantaran. Sila cuba semula.');
      });
    });

    function radioValue(name) {
      const checked = document.querySelector(`input[name="${name}"]:checked`);
      return checked ? checked.value : '';
    }
</script>

</body>
</html>
