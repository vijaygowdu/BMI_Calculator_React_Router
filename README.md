# Ex06 BMI Calculator

## AIM:
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
  const [message, setMessage] = useState('');

  const calculateBMI = () => {
    if (weight && height) {
      const heightInMeters = height / 100;
      const calculatedBMI = (weight / (heightInMeters * heightInMeters)).toFixed(2);
      setBmi(calculatedBMI);
      getBMICategory(calculatedBMI);
    } else {
      alert('Please enter valid height and weight.');
    }
  };

  const getBMICategory = (bmi) => {
    if (bmi < 18.5) setMessage('Underweight');
    else if (bmi >= 18.5 && bmi < 24.9) setMessage('Normal weight');
    else if (bmi >= 25 && bmi < 29.9) setMessage('Overweight');
    else setMessage('Obese');
  };

  const resetFields = () => {
    setWeight('');
    setHeight('');
    setBmi(null);
    setMessage('');
  };

  return (
    <div className="container">
      <h1>BMI Calculator</h1>
      <div className="input-group">
        <label>Weight (kg):</label>
        <input
          type="number"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
          placeholder="Enter weight"
        />
      </div>
      <div className="input-group">
        <label>Height (cm):</label>
        <input
          type="number"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
          placeholder="Enter height"
        />
      </div>
      <button onClick={calculateBMI}>Calculate</button>
      <button className="reset" onClick={resetFields}>Reset</button>
      
      {bmi && (
        <div className="result">
          <h2>Your BMI: {bmi}</h2>
          <p className="message">{message}</p>
        </div>
      
      )}
      <div>
        <footer> Done By:Vijay K 212223040236</footer>
      </div>
    </div>
  );
}

export default App;
```
## APP.CSS
```
body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f0f4f8;
  margin: 0;
  padding: 0;
}

.container {
  max-width: 400px;
  margin: 100px auto;
  padding: 30px;
  background-color: rgb(185, 203, 244);
  border-radius: 12px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
  text-align: center;
}

h1 {
  margin-bottom: 20px;
  color: #333;
}

.input-group {
  margin-bottom: 20px;
  text-align: left;
}

.input-group label {
  display: block;
  margin-bottom: 5px;
  font-weight: 500;
}

.input-group input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border: 2px solid #ddd;
  border-radius: 8px;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  margin: 10px 5px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  background-color: #094c93;
  color: white;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #002e5e;
}

button.reset {
  background-color: #6c757d;
}

button.reset:hover {
  background-color: #5a6268;
}

.result {
  margin-top: 30px;
  padding: 20px;
  border-radius: 8px;
  background-color: #f8f9fa;
}

.message {
  font-size: 18px;
  font-weight: bold;
  color: #444;
}
```



## OUTPUT
![WhatsApp Image 2025-05-30 at 20 57 26_5d914ca0](https://github.com/user-attachments/assets/5206a5f7-b70a-4cc3-afb4-f811bb1e3cff)





## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
