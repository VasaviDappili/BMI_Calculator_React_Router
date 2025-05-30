# Ex06 BMI Calculator
## Date: 28-05-2025

## AIM
To develop a responsive and interactive Body Mass Index (BMI) Calculator using React that allows users to input their height and weight, and calculates their BMI to categorize their health status (e.g., Underweight, Normal, Overweight, Obese).

## DESIGN STEPS

### STEP 1: Initialize React Project

<li>Create a new React app using create-react-app.</li>
<li>Install React Router using:</li>
npm install react-router-dom

### STEP 2: Set Up Routing

Create routing structure with react-router-dom:

<li>Home route (/) – Intro or Navigation</li>

<li>BMI Calculator route (/bmi)</li>

<li>Result route (/result)</li>

### STEP 3: Design the BMI Form Page

<li>Create a form to accept Height (in cm or m) and Weight (in kg).</li>

<li>On form submit, navigate to the result page with entered values via URL query params or context/state.</li>

## STEP 4: Handle Input Validation

<li>Check if height and weight are valid numbers.</li>

<li>Optionally, show error messages for invalid inputs.</li>

### STEP 5: Perform BMI Calculation

<li>In the result component:

<li>Extract height and weight from the route (URL or passed state).</li>

<li>Apply the BMI formula:</li>

![image](https://github.com/user-attachments/assets/ec785506-c96b-489e-8783-fb1a5d36101a)
​
 
<li>Convert height from cm to m if needed.</li></li>

### STEP 6: Display Result

<li>Show calculated BMI.</li>

<li>Show category based on BMI range:

<li>Underweight, Normal, Overweight, Obese, etc.</li></li>

### STEP 7: Navigation Options

<li>Provide a button to go back to the BMI form to calculate again.</li>

### STEP 8: Enhancements

<li>Add styling using CSS or Tailwind.</li>

## PROGRAM
## APP.JS
```
import React, { useState } from 'react';
import './App.css';

function App() {
  const [weight, setWeight] = useState('');
  const [height, setHeight] = useState('');
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState('');

  const calculateBMI = () => {
    if (height && weight) {
      const heightInMeters = height / 100;
      const calculatedBMI = (weight / (heightInMeters * heightInMeters)).toFixed(1);
      setBmi(calculatedBMI);
      setCategory(getCategory(calculatedBMI));
    } else {
      alert('Please enter both height and weight.');
    }
  };

  const getCategory = (bmi) => {
    if (bmi < 18.5) return '⚠️ Underweight';
    if (bmi < 25) return '✅ Normal';
    if (bmi < 30) return '⚠️ Overweight';
    return '🔴 Obese';
  };

  const reset = () => {
    setHeight('');
    setWeight('');
    setBmi(null);
    setCategory('');
  };

  return (
    <div className="main-wrapper">
      <div className="card">
        <h1>💪 BMI Calculator</h1>
        <div className="form-section">
          <input
            type="number"
            placeholder="Enter weight (kg)"
            value={weight}
            onChange={(e) => setWeight(e.target.value)}
          />
          <input
            type="number"
            placeholder="Enter height (cm)"
            value={height}
            onChange={(e) => setHeight(e.target.value)}
          />
          <div className="button-group">
            <button onClick={calculateBMI}>Calculate</button>
            <button onClick={reset} className="secondary">Reset</button>
          </div>
        </div>
        {bmi && (
          <div className="output-section">
            <h2>Your BMI: <span>{bmi}</span></h2>
            <p className="category">{category}</p>
          </div>
        )}
        <footer>
        <p>Created by : DAPPILI VASAVI</p>
        <p>Register Number : 212223040030</p>
      </footer>
      </div>
    </div>
  );
}

export default App;

```
## APP.CSS
```
body {
  margin: 0;
  padding: 0;
  font-family: 'Poppins', sans-serif;
  background: linear-gradient(to right, #74ebd5, #acb6e5);
}

.main-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.card {
  background: white;
  padding: 40px;
  border-radius: 16px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
  text-align: center;
  width: 350px;
}

h1 {
  margin-bottom: 25px;
  color: #1e1e2f;
}

.form-section input {
  width: 100%;
  padding: 12px;
  margin: 10px 0;
  font-size: 16px;
  border: 2px solid #ddd;
  border-radius: 8px;
  outline: none;
}

.button-group {
  display: flex;
  justify-content: space-between;
  margin-top: 20px;
}

button {
  padding: 10px 20px;
  font-size: 15px;
  background-color: #4a90e2;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #357ABD;
}

button.secondary {
  background-color: #888;
}

button.secondary:hover {
  background-color: #666;
}

.output-section {
  margin-top: 30px;
  background-color: #f7f9fc;
  padding: 20px;
  border-radius: 12px;
}

.output-section h2 span {
  color: #4a90e2;
}

.category {
  font-weight: bold;
  font-size: 18px;
  margin-top: 10px;
}

.footer {
  margin-top: 30px;
  font-size: 14px;
  color: #777;
}

```



## OUTPUT

![Screenshot (276)](https://github.com/user-attachments/assets/13435687-7931-4f21-a975-b41b2db676bd)

![Screenshot (278)](https://github.com/user-attachments/assets/4f22f1de-3ab3-48ff-a2f2-47928d5a5eb7)






## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
