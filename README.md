<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>MediScan AI - Advanced Disease Prediction</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    :root {
      --primary: #4361ee;
      --secondary: #3f37c9;
      --accent: #4895ef;
      --light: #f8f9fa;
      --dark: #212529;
      --danger: #ef233c;
      --success: #4cc9f0;
      --warning: #f8961e;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      color: var(--dark);
      overflow-x: hidden;
    }

    .particles {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -1;
    }

    .container {
      width: 90%;
      max-width: 1000px;
      margin: 2rem auto;
      perspective: 1000px;
    }

    .card {
      background: rgba(255, 255, 255, 0.95);
      border-radius: 20px;
      box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1), 0 5px 15px rgba(0, 0, 0, 0.07);
      padding: 2.5rem;
      transform-style: preserve-3d;
      transition: all 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
      position: relative;
      overflow: hidden;
      backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 255, 255, 0.2);
    }

    .card:hover {
      transform: translateY(-5px) rotateX(2deg) rotateY(2deg);
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15), 0 10px 20px rgba(0, 0, 0, 0.1);
    }

    .card::before {
      content: '';
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: linear-gradient(45deg, transparent, rgba(67, 97, 238, 0.1), transparent);
      transform: rotate(45deg);
      animation: shine 3s infinite;
    }

    @keyframes shine {
      0% { left: -50%; }
      100% { left: 150%; }
    }

    .header {
      text-align: center;
      margin-bottom: 2.5rem;
      position: relative;
    }

    .header h1 {
      font-size: 2.5rem;
      color: var(--primary);
      margin-bottom: 0.5rem;
      font-weight: 700;
      background: linear-gradient(to right, #4361ee, #4895ef);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      position: relative;
      display: inline-block;
    }

    .header h1::after {
      content: '';
      position: absolute;
      bottom: -10px;
      left: 50%;
      transform: translateX(-50%);
      width: 80px;
      height: 4px;
      background: linear-gradient(to right, #4361ee, #4895ef);
      border-radius: 2px;
    }

    .header p {
      color: #6c757d;
      font-size: 1.1rem;
    }

    .form-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 1.5rem;
    }

    .form-group {
      margin-bottom: 1.5rem;
      position: relative;
    }

    .form-group label {
      display: block;
      margin-bottom: 0.5rem;
      font-weight: 600;
      color: var(--dark);
      font-size: 0.95rem;
    }

    .form-control {
      width: 100%;
      padding: 0.8rem 1rem;
      font-size: 1rem;
      border: 2px solid #e9ecef;
      border-radius: 10px;
      transition: all 0.3s ease;
      background-color: #f8f9fa;
      color: var(--dark);
    }

    .form-control:focus {
      outline: none;
      border-color: var(--accent);
      box-shadow: 0 0 0 3px rgba(72, 149, 239, 0.2);
      background-color: white;
    }

    select.form-control {
      appearance: none;
      background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='currentColor' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3e%3cpolyline points='6 9 12 15 18 9'%3e%3c/polyline%3e%3c/svg%3e");
      background-repeat: no-repeat;
      background-position: right 1rem center;
      background-size: 1em;
    }

    .btn {
      display: inline-block;
      padding: 0.9rem 2rem;
      font-size: 1rem;
      font-weight: 600;
      text-align: center;
      text-decoration: none;
      border-radius: 10px;
      cursor: pointer;
      transition: all 0.3s ease;
      border: none;
      color: white;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
      position: relative;
      overflow: hidden;
      margin-top: 1rem;
      width: 100%;
    }

    .btn-primary {
      background: linear-gradient(135deg, var(--primary), var(--accent));
    }

    .btn-primary:hover {
      background: linear-gradient(135deg, var(--secondary), var(--primary));
    }

    .btn-secondary {
      background: linear-gradient(135deg, #6c757d, #495057);
    }

    .btn-secondary:hover {
      background: linear-gradient(135deg, #495057, #343a40);
    }

    .btn:active {
      transform: translateY(0);
    }

    .btn::after {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, rgba(255, 255, 255, 0.2), transparent);
      transform: translateX(-100%);
      transition: transform 0.6s ease;
    }

    .btn:hover::after {
      transform: translateX(100%);
    }

    .button-group {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1rem;
      margin-top: 1.5rem;
    }

    .result-container {
      margin-top: 2rem;
      padding: 1.5rem;
      border-radius: 15px;
      background: rgba(248, 249, 250, 0.7);
      border: 1px solid rgba(0, 0, 0, 0.05);
      animation: fadeIn 0.5s ease-out;
      display: none;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .result-header {
      display: flex;
      align-items: center;
      margin-bottom: 1rem;
    }

    .result-header i {
      font-size: 1.8rem;
      color: var(--primary);
      margin-right: 1rem;
    }

    .result-header h2 {
      font-size: 1.5rem;
      color: var(--dark);
      margin: 0;
    }

    .disease-list {
      list-style: none;
    }

    .disease-item {
      padding: 1rem;
      margin-bottom: 0.75rem;
      border-radius: 10px;
      background: white;
      box-shadow: 0 3px 10px rgba(0, 0, 0, 0.05);
      display: flex;
      justify-content: space-between;
      align-items: center;
      transition: all 0.3s ease;
      border-left: 4px solid var(--primary);
    }

    .disease-item:hover {
      transform: translateX(5px);
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    }

    .disease-name {
      font-weight: 600;
      font-size: 1.1rem;
    }

    .probability {
      padding: 0.3rem 0.8rem;
      border-radius: 20px;
      font-weight: 600;
      font-size: 0.85rem;
    }

    .high {
      background-color: rgba(239, 35, 60, 0.1);
      color: var(--danger);
    }

    .moderate {
      background-color: rgba(248, 150, 30, 0.1);
      color: var(--warning);
    }

    .low {
      background-color: rgba(76, 201, 240, 0.1);
      color: var(--success);
    }

    .disclaimer {
      margin-top: 1.5rem;
      padding: 1rem;
      background-color: rgba(248, 150, 30, 0.1);
      border-radius: 10px;
      border-left: 4px solid var(--warning);
      font-size: 0.9rem;
      color: #6c757d;
    }

    .pulse {
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.05); }
      100% { transform: scale(1); }
    }

    .floating {
      animation: floating 6s ease-in-out infinite;
    }

    @keyframes floating {
      0% { transform: translateY(0px); }
      50% { transform: translateY(-15px); }
      100% { transform: translateY(0px); }
    }

    @media (max-width: 768px) {
      .card {
        padding: 1.5rem;
      }
      
      .header h1 {
        font-size: 2rem;
      }
      
      .form-grid {
        grid-template-columns: 1fr;
      }
      
      .button-group {
        grid-template-columns: 1fr;
      }
    }

    /* Animated background elements */
    .circle {
      position: absolute;
      border-radius: 50%;
      background: rgba(72, 149, 239, 0.1);
      z-index: -1;
    }

    .circle-1 {
      width: 300px;
      height: 300px;
      top: -100px;
      right: -100px;
      animation: floating 8s ease-in-out infinite;
    }

    .circle-2 {
      width: 200px;
      height: 200px;
      bottom: -50px;
      left: -50px;
      animation: floating 10s ease-in-out infinite reverse;
    }

    /* Loading spinner */
    .spinner {
      display: none;
      width: 50px;
      height: 50px;
      margin: 20px auto;
      border: 5px solid rgba(67, 97, 238, 0.2);
      border-radius: 50%;
      border-top-color: var(--primary);
      animation: spin 1s ease-in-out infinite;
    }

    @keyframes spin {
      to { transform: rotate(360deg); }
    }
    
    /* Prediction history */
    .history-container {
      margin-top: 2rem;
      display: none;
    }
    
    .history-item {
      background: white;
      border-radius: 10px;
      padding: 1rem;
      margin-bottom: 1rem;
      box-shadow: 0 3px 10px rgba(0, 0, 0, 0.05);
      border-left: 4px solid var(--accent);
      animation: fadeIn 0.5s ease-out;
    }
    
    .history-header {
      display: flex;
      justify-content: space-between;
      margin-bottom: 0.5rem;
    }
    
    .history-date {
      font-size: 0.8rem;
      color: #6c757d;
    }
    
    .history-symptoms {
      font-size: 0.9rem;
      color: #495057;
      margin-bottom: 0.5rem;
    }
    
    .history-diseases {
      list-style: none;
    }
    
    .history-disease {
      display: flex;
      justify-content: space-between;
      padding: 0.5rem 0;
      border-bottom: 1px solid #e9ecef;
    }
    
    .history-disease:last-child {
      border-bottom: none;
    }
  </style>
</head>
<body>
  <!-- Animated background elements -->
  <div class="circle circle-1"></div>
  <div class="circle circle-2"></div>

  <div class="container">
    <div class="card animate__animated animate__fadeInUp">
      <div class="header">
        <h1 class="animate__animated animate__fadeInDown">MediScan AI</h1>
        <p class="animate__animated animate__fadeIn animate__delay-1s">Advanced Disease Prediction System</p>
      </div>

      <div class="form-grid">
        <div class="form-group animate__animated animate__fadeInLeft">
          <label for="age"><i class="fas fa-birthday-cake"></i> Age</label>
          <input type="number" id="age" class="form-control" placeholder="Enter your age" min="1" max="120">
        </div>

        <div class="form-group animate__animated animate__fadeInRight">
          <label for="gender"><i class="fas fa-venus-mars"></i> Gender</label>
          <select id="gender" class="form-control">
            <option value="male">Male</option>
            <option value="female">Female</option>
            <option value="other">Other</option>
          </select>
        </div>

        <div class="form-group animate__animated animate__fadeInLeft animate__delay-1s">
          <label for="fever"><i class="fas fa-thermometer-half"></i> Fever</label>
          <select id="fever" class="form-control">
            <option value="none">No fever</option>
            <option value="low">Low grade (37.2°C - 38.3°C)</option>
            <option value="high">High fever (>38.3°C)</option>
          </select>
        </div>

        <div class="form-group animate__animated animate__fadeInRight animate__delay-1s">
          <label for="cough"><i class="fas fa-lungs"></i> Cough Type</label>
          <select id="cough" class="form-control">
            <option value="none">No cough</option>
            <option value="dry">Dry cough</option>
            <option value="productive">Productive cough (with phlegm)</option>
          </select>
        </div>

        <div class="form-group animate__animated animate__fadeInLeft animate__delay-2s">
          <label for="pain"><i class="fas fa-pain"></i> Pain Location</label>
          <select id="pain" class="form-control">
            <option value="none">No pain</option>
            <option value="head">Headache</option>
            <option value="chest">Chest pain</option>
            <option value="abdominal">Abdominal pain</option>
            <option value="joint">Joint pain</option>
          </select>
        </div>

        <div class="form-group animate__animated animate__fadeInRight animate__delay-2s">
          <label for="fatigue"><i class="fas fa-tired"></i> Fatigue Level</label>
          <select id="fatigue" class="form-control">
            <option value="none">No fatigue</option>
            <option value="mild">Mild fatigue</option>
            <option value="severe">Severe fatigue</option>
          </select>
        </div>

        <div class="form-group animate__animated animate__fadeInLeft animate__delay-3s">
          <label for="breathing"><i class="fas fa-wind"></i> Breathing Difficulty</label>
          <select id="breathing" class="form-control">
            <option value="none">No difficulty</option>
            <option value="mild">Mild difficulty</option>
            <option value="severe">Severe difficulty</option>
          </select>
        </div>

        <div class="form-group animate__animated animate__fadeInRight animate__delay-3s">
          <label for="appetite"><i class="fas fa-utensils"></i> Appetite Change</label>
          <select id="appetite" class="form-control">
            <option value="normal">Normal</option>
            <option value="increased">Increased</option>
            <option value="decreased">Decreased</option>
          </select>
        </div>

        <div class="form-group animate__animated animate__fadeInLeft animate__delay-4s">
          <label for="duration"><i class="fas fa-clock"></i> Symptom Duration (days)</label>
          <input type="number" id="duration" class="form-control" placeholder="How long have you had symptoms?" min="1" max="365">
        </div>
      </div>

      <div class="button-group">
        <button id="predict-btn" class="btn btn-primary animate__animated animate__fadeInUp animate__delay-4s pulse">
          <i class="fas fa-diagnoses"></i> Predict Disease
        </button>
        <button id="reset-btn" class="btn btn-secondary animate__animated animate__fadeInUp animate__delay-4s">
          <i class="fas fa-redo"></i> Reset Form
        </button>
      </div>

      <div class="spinner" id="spinner"></div>

      <div class="result-container" id="result-container">
        <div class="result-header">
          <i class="fas fa-clipboard-list"></i>
          <h2>Possible Conditions</h2>
        </div>
        <ul class="disease-list" id="disease-list">
          <!-- Results will be inserted here -->
        </ul>
        <div class="disclaimer">
          <i class="fas fa-exclamation-triangle"></i> <strong>Important:</strong> This is not a medical diagnosis. 
          Please consult a healthcare professional for accurate assessment.
        </div>
      </div>
      
      <div class="history-container" id="history-container">
        <h3><i class="fas fa-history"></i> Prediction History</h3>
        <div id="history-items">
          <!-- History items will be added here -->
        </div>
      </div>
    </div>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/particles.js@2.0.0/particles.min.js"></script>
  <script>
    // Initialize particles.js
    document.addEventListener('DOMContentLoaded', function() {
      particlesJS('particles', {
        "particles": {
          "number": {
            "value": 80,
            "density": {
              "enable": true,
              "value_area": 800
            }
          },
          "color": {
            "value": "#4361ee"
          },
          "shape": {
            "type": "circle",
            "stroke": {
              "width": 0,
              "color": "#000000"
            },
            "polygon": {
              "nb_sides": 5
            }
          },
          "opacity": {
            "value": 0.3,
            "random": false,
            "anim": {
              "enable": false,
              "speed": 1,
              "opacity_min": 0.1,
              "sync": false
            }
          },
          "size": {
            "value": 3,
            "random": true,
            "anim": {
              "enable": false,
              "speed": 40,
              "size_min": 0.1,
              "sync": false
            }
          },
          "line_linked": {
            "enable": true,
            "distance": 150,
            "color": "#4361ee",
            "opacity": 0.2,
            "width": 1
          },
          "move": {
            "enable": true,
            "speed": 2,
            "direction": "none",
            "random": false,
            "straight": false,
            "out_mode": "out",
            "bounce": false,
            "attract": {
              "enable": false,
              "rotateX": 600,
              "rotateY": 1200
            }
          }
        },
        "interactivity": {
          "detect_on": "canvas",
          "events": {
            "onhover": {
              "enable": true,
              "mode": "grab"
            },
            "onclick": {
              "enable": true,
              "mode": "push"
            },
            "resize": true
          },
          "modes": {
            "grab": {
              "distance": 140,
              "line_linked": {
                "opacity": 1
              }
            },
            "bubble": {
              "distance": 400,
              "size": 40,
              "duration": 2,
              "opacity": 8,
              "speed": 3
            },
            "repulse": {
              "distance": 200,
              "duration": 0.4
            },
            "push": {
              "particles_nb": 4
            },
            "remove": {
              "particles_nb": 2
            }
          }
        },
        "retina_detect": true
      });
      
      // Load any saved history from localStorage
      loadHistory();
    });

    // Event listeners
    document.getElementById('predict-btn').addEventListener('click', predictDisease);
    document.getElementById('reset-btn').addEventListener('click', resetForm);

    function predictDisease() {
      // Show loading spinner
      document.getElementById('spinner').style.display = 'block';
      document.getElementById('result-container').style.display = 'none';
      
      // Get input values
      const age = parseInt(document.getElementById('age').value);
      const gender = document.getElementById('gender').value;
      const fever = document.getElementById('fever').value;
      const cough = document.getElementById('cough').value;
      const pain = document.getElementById('pain').value;
      const fatigue = document.getElementById('fatigue').value;
      const breathing = document.getElementById('breathing').value;
      const appetite = document.getElementById('appetite').value;
      const duration = parseInt(document.getElementById('duration').value);
      
      // Validate inputs
      if (isNaN(age) || isNaN(duration)) {
        showError("Please enter valid age and symptom duration");
        return;
      }
      
      // Simulate API call delay
      setTimeout(() => {
        // Disease prediction logic
        let possibleDiseases = analyzeSymptoms(age, gender, fever, cough, pain, fatigue, breathing, appetite, duration);
        
        // Display results
        displayResults(possibleDiseases);
        
        // Save to history
        addToHistory(age, gender, fever, cough, pain, fatigue, breathing, appetite, duration, possibleDiseases);
        
        // Hide spinner
        document.getElementById('spinner').style.display = 'none';
      }, 1500); // Simulate 1.5 second delay for "processing"
    }

    function analyzeSymptoms(age, gender, fever, cough, pain, fatigue, breathing, appetite, duration) {
      let possibleDiseases = [];
      
      // Respiratory conditions
      if ((cough === "dry" || cough === "productive") && (fever === "low" || fever === "high")) {
        if (breathing === "severe") {
          possibleDiseases.push({name: "Pneumonia", probability: "high"});
          possibleDiseases.push({name: "COVID-19", probability: "moderate"});
        } else if (duration < 7) {
          possibleDiseases.push({name: "Common Cold", probability: "high"});
          possibleDiseases.push({name: "Influenza (Flu)", probability: "moderate"});
        } else {
          possibleDiseases.push({name: "Bronchitis", probability: "moderate"});
        }
      }
      
      // Gastrointestinal conditions
      if (pain === "abdominal" && (appetite === "decreased" || appetite === "increased")) {
        possibleDiseases.push({name: "Gastritis", probability: "moderate"});
        if (fever === "high") {
          possibleDiseases.push({name: "Gastroenteritis", probability: "high"});
        }
        if (appetite === "increased" && duration > 30) {
          possibleDiseases.push({name: "Hyperthyroidism", probability: "low"});
        }
      }
      
      // Cardiovascular conditions
      if (pain === "chest" && (breathing === "mild" || breathing === "severe") && age > 40) {
        possibleDiseases.push({name: "Angina", probability: "high"});
        if (fatigue === "severe") {
          possibleDiseases.push({name: "Heart Disease", probability: "moderate"});
        }
      }
      
      // Neurological conditions
      if (pain === "head" && fatigue === "severe" && duration > 14) {
        possibleDiseases.push({name: "Migraine", probability: "moderate"});
        if (fever === "high") {
          possibleDiseases.push({name: "Meningitis", probability: "high"});
        }
      }
      
      // Metabolic conditions
      if (fatigue === "severe" && appetite === "increased" && duration > 30) {
        possibleDiseases.push({name: "Diabetes", probability: "moderate"});
        possibleDiseases.push({name: "Hyperthyroidism", probability: "low"});
      }
      
      // Autoimmune conditions
      if (pain === "joint" && fatigue === "severe" && duration > 90) {
        possibleDiseases.push({name: "Rheumatoid Arthritis", probability: "moderate"});
        possibleDiseases.push({name: "Lupus", probability: "low"});
      }
      
      // Gender-specific conditions
      if (gender === "female" && pain === "abdominal" && age >= 15 && age <= 45) {
        possibleDiseases.push({name: "Endometriosis", probability: "moderate"});
        possibleDiseases.push({name: "Ovarian Cysts", probability: "low"});
      }
      
      // If no matches found
      if (possibleDiseases.length === 0) {
        possibleDiseases.push({name: "No specific condition identified", probability: "none"});
      }
      
      return possibleDiseases;
    }

    function displayResults(diseases) {
      const diseaseList = document.getElementById('disease-list');
      diseaseList.innerHTML = '';
      
      diseases.forEach(disease => {
        const li = document.createElement('li');
        li.className = 'disease-item animate__animated animate__fadeInUp';
        
        let probabilityClass = '';
        let probabilityText = '';
        
        switch(disease.probability) {
          case 'high':
            probabilityClass = 'high';
            probabilityText = 'High Probability';
            break;
          case 'moderate':
            probabilityClass = 'moderate';
            probabilityText = 'Moderate Probability';
            break;
          case 'low':
            probabilityClass = 'low';
            probabilityText = 'Low Probability';
            break;
          default:
            probabilityClass = '';
            probabilityText = '';
        }
        
        li.innerHTML = `
          <span class="disease-name">${disease.name}</span>
          ${probabilityText ? `<span class="probability ${probabilityClass}">${probabilityText}</span>` : ''}
        `;
        
        diseaseList.appendChild(li);
      });
      
      // Show results with animation
      const resultContainer = document.getElementById('result-container');
      resultContainer.style.display = 'block';
      resultContainer.classList.add('animate__animated', 'animate__fadeIn');
      
      // Show history container if it's not empty
      const historyContainer = document.getElementById('history-container');
      const historyItems = document.getElementById('history-items');
      if (historyItems.children.length > 0) {
        historyContainer.style.display = 'block';
      }
      
      // Scroll to results
      setTimeout(() => {
        resultContainer.scrollIntoView({ behavior: 'smooth' });
      }, 100);
    }

    function showError(message) {
      const diseaseList = document.getElementById('disease-list');
      diseaseList.innerHTML = `
        <li class="disease-item animate__animated animate__shakeX" style="color: var(--danger);">
          <i class="fas fa-exclamation-circle"></i> ${message}
        </li>
      `;
      
      document.getElementById('spinner').style.display = 'none';
      document.getElementById('result-container').style.display = 'block';
    }

    function resetForm() {
      // Reset all form fields
      document.getElementById('age').value = '';
      document.getElementById('gender').value = 'male';
      document.getElementById('fever').value = 'none';
      document.getElementById('cough').value = 'none';
      document.getElementById('pain').value = 'none';
      document.getElementById('fatigue').value = 'none';
      document.getElementById('breathing').value = 'none';
      document.getElementById('appetite').value = 'normal';
      document.getElementById('duration').value = '';
      
      // Hide results
      document.getElementById('result-container').style.display = 'none';
      
      // Add animation to reset button
      const resetBtn = document.getElementById('reset-btn');
      resetBtn.classList.add('animate__animated', 'animate__rubberBand');
      setTimeout(() => {
        resetBtn.classList.remove('animate__animated', 'animate__rubberBand');
      }, 1000);
    }

    function addToHistory(age, gender, fever, cough, pain, fatigue, breathing, appetite, duration, diseases) {
      // Get current history or initialize empty array
      let history = JSON.parse(localStorage.getItem('predictionHistory')) || [];
      
      // Create new history item
      const newItem = {
        date: new Date().toLocaleString(),
        symptoms: {
          age, gender, fever, cough, pain, fatigue, breathing, appetite, duration
        },
        diseases: diseases
      };
      
      // Add to beginning of array (newest first)
      history.unshift(newItem);
      
      // Keep only last 5 items
      if (history.length > 5) {
        history = history.slice(0, 5);
      }
      
      // Save to localStorage
      localStorage.setItem('predictionHistory', JSON.stringify(history));
      
      // Update UI
      updateHistoryUI(history);
    }

    function loadHistory() {
      const history = JSON.parse(localStorage.getItem('predictionHistory')) || [];
      updateHistoryUI(history);
    }

    function updateHistoryUI(history) {
      const historyItems = document.getElementById('history-items');
      historyItems.innerHTML = '';
      
      if (history.length === 0) {
        document.getElementById('history-container').style.display = 'none';
        return;
      }
      
      document.getElementById('history-container').style.display = 'block';
      
      history.forEach((item, index) => {
        const historyItem = document.createElement('div');
        historyItem.className = 'history-item';
        
        // Format symptoms text
        const symptomsText = [
          `Age: ${item.symptoms.age}`,
          `Gender: ${item.symptoms.gender}`,
          `Fever: ${item.symptoms.fever}`,
          `Cough: ${item.symptoms.cough}`,
          `Pain: ${item.symptoms.pain}`,
          `Fatigue: ${item.symptoms.fatigue}`,
          `Duration: ${item.symptoms.duration} days`
        ].join(' • ');
        
        // Create diseases list
        let diseasesList = '';
        item.diseases.forEach(disease => {
          let probabilityClass = '';
          switch(disease.probability) {
            case 'high': probabilityClass = 'high'; break;
            case 'moderate': probabilityClass = 'moderate'; break;
            case 'low': probabilityClass = 'low'; break;
          }
          
          diseasesList += `
            <div class="history-disease">
              <span>${disease.name}</span>
              ${disease.probability !== 'none' ? 
                `<span class="probability ${probabilityClass}">${disease.probability.charAt(0).toUpperCase() + disease.probability.slice(1)}</span>` : ''}
            </div>
          `;
        });
        
        historyItem.innerHTML = `
          <div class="history-header">
            <strong>Prediction #${index + 1}</strong>
            <span class="history-date">${item.date}</span>
          </div>
          <div class="history-symptoms">${symptomsText}</div>
          <div class="history-diseases">${diseasesList}</div>
        `;
        
        historyItems.appendChild(historyItem);
      });
    }
  </script>
</body>
</html>
