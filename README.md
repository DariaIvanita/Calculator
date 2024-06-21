const dinersInput = document.getElementById('diners');
const mealCostInput = document.getElementById('mealCost');
const tipPercentSelect = document.getElementById('tipPercent');
const provinceSelect = document.getElementById('province');

const totalBillDisplay = document.getElementById('totalBill');
const totalTipDisplay = document.getElementById('totalTip');
const tipPercentDisplay = document.getElementById('tipPercentDisplay');
const totalTaxDisplay = document.getElementById('totalTax');
const costPerDinerDisplay = document.getElementById('costPerDiner');

function calculateBill() {
    const diners = parseInt(dinersInput.value);
    const mealCost = parseFloat(mealCostInput.value);
    const tipPercent = parseFloat(tipPercentSelect.value);
    const taxRate = parseFloat(provinceSelect.value);

    const preTaxTotal = mealCost;
    const totalTip = preTaxTotal * tipPercent;
    const totalTax = preTaxTotal * taxRate;
    const totalBill = preTaxTotal + totalTip + totalTax;
    const costPerDiner = totalBill / diners;

    totalBillDisplay.textContent = totalBill.toFixed(2);
    totalTipDisplay.textContent = totalTip.toFixed(2);
    tipPercentDisplay.textContent = (tipPercent * 100).toFixed(0) + '%';
    totalTaxDisplay.textContent = totalTax.toFixed(2);
    costPerDinerDisplay.textContent = costPerDiner.toFixed(2);
}

dinersInput.addEventListener('input', calculateBill);
mealCostInput.addEventListener('input', calculateBill);
tipPercentSelect.addEventListener('change', calculateBill);
provinceSelect.addEventListener('change', calculateBill);

calculateBill(); // Initial calculation on page load

body {
    font-family: sans-serif;
    margin: 0;
    padding: 0;
    background-color: #068a13;
}

.container {
    max-width: 600px;
    margin: 50px auto;
    padding: 20px;
    background-color: #6bae3b;
    border-radius: 5px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
    color: #333;
    margin-bottom: 20px;
}

.form-group {
    margin-bottom: 15px;
}

label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
}

input[type="number"], select {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 3px;
    box-sizing: border-box;
}

.results {
    margin-top: 20px;
    text-align: center;
}

.results p {
    margin-bottom: 10px;
}

@media (max-width: 500px) {
    .container {
        margin: 20px;
    }
}
