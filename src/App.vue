<template>
  <div class="calculator-container">
    <div class="calculator">
      <div class="display">
        <div class="display-text">{{ displayValue }}</div>
      </div>
      
      <div class="buttons">
        <!-- Première ligne -->
        <button class="btn btn-clear" @click="clearAll">AC</button>
        <button class="btn btn-clear" @click="clearEntry">C</button>
        <button class="btn btn-operator" @click="inputOperator('/')" :class="{ active: operator === '/' }">÷</button>
        <button class="btn btn-operator" @click="inputOperator('*')" :class="{ active: operator === '*' }">×</button>
        
        <!-- Deuxième ligne -->
        <button class="btn btn-number" @click="inputNumber('7')">7</button>
        <button class="btn btn-number" @click="inputNumber('8')">8</button>
        <button class="btn btn-number" @click="inputNumber('9')">9</button>
        <button class="btn btn-operator" @click="inputOperator('-')" :class="{ active: operator === '-' }">−</button>
        
        <!-- Troisième ligne -->
        <button class="btn btn-number" @click="inputNumber('4')">4</button>
        <button class="btn btn-number" @click="inputNumber('5')">5</button>
        <button class="btn btn-number" @click="inputNumber('6')">6</button>
        <button class="btn btn-operator" @click="inputOperator('+')" :class="{ active: operator === '+' }">+</button>
        
        <!-- Quatrième ligne -->
        <button class="btn btn-number" @click="inputNumber('1')">1</button>
        <button class="btn btn-number" @click="inputNumber('2')">2</button>
        <button class="btn btn-number" @click="inputNumber('3')">3</button>
        <button class="btn btn-equals" @click="calculate" rowspan="2">=</button>
        
        <!-- Cinquième ligne -->
        <button class="btn btn-number btn-zero" @click="inputNumber('0')">0</button>
        <button class="btn btn-number" @click="inputDecimal">.</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const currentValue = ref('0')
const previousValue = ref(null)
const operator = ref(null)
const waitingForNewValue = ref(false)

const displayValue = computed(() => {
  if (currentValue.value.length > 12) {
    return parseFloat(currentValue.value).toExponential(6)
  }
  return currentValue.value
})

function inputNumber(num) {
  if (waitingForNewValue.value) {
    currentValue.value = num
    waitingForNewValue.value = false
  } else {
    currentValue.value = currentValue.value === '0' ? num : currentValue.value + num
  }
}

function inputDecimal() {
  if (waitingForNewValue.value) {
    currentValue.value = '0.'
    waitingForNewValue.value = false
  } else if (currentValue.value.indexOf('.') === -1) {
    currentValue.value += '.'
  }
}

function inputOperator(nextOperator) {
  const inputValue = parseFloat(currentValue.value)

  if (previousValue.value === null) {
    previousValue.value = inputValue
  } else if (operator.value) {
    const currentResult = calculate()
    currentValue.value = String(currentResult)
    previousValue.value = currentResult
  }

  waitingForNewValue.value = true
  operator.value = nextOperator
}

function calculate() {
  const prev = parseFloat(previousValue.value)
  const current = parseFloat(currentValue.value)

  if (previousValue.value === null || operator.value === null) {
    return current
  }

  let result
  switch (operator.value) {
    case '+':
      result = prev + current
      break
    case '-':
      result = prev - current
      break
    case '*':
      result = prev * current
      break
    case '/':
      if (current === 0) {
        alert('Erreur: Division par zéro')
        clearAll()
        return 0
      }
      result = prev / current
      break
    default:
      return current
  }

  // Arrondir le résultat pour éviter les problèmes de précision JavaScript
  result = Math.round(result * 100000000) / 100000000

  currentValue.value = String(result)
  previousValue.value = null
  operator.value = null
  waitingForNewValue.value = true

  return result
}

function clearAll() {
  currentValue.value = '0'
  previousValue.value = null
  operator.value = null
  waitingForNewValue.value = false
}

function clearEntry() {
  currentValue.value = '0'
  waitingForNewValue.value = false
}
</script>

<style scoped>
.calculator-container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  padding: 1rem;
}

.calculator {
  background: #1a1a1a;
  border-radius: 20px;
  padding: 20px;
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
  border: 2px solid #333;
  max-width: 300px;
  width: 100%;
}

.display {
  background: #000;
  border: 3px inset #333;
  border-radius: 8px;
  padding: 15px 20px;
  margin-bottom: 20px;
  text-align: right;
  position: relative;
  overflow: hidden;
}

.display::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(45deg, transparent 30%, rgba(0, 255, 0, 0.03) 50%, transparent 70%);
  pointer-events: none;
}

.display-text {
  font-family: 'Courier New', monospace;
  font-size: 2rem;
  color: #00ff41;
  text-shadow: 0 0 10px #00ff41;
  font-weight: bold;
  letter-spacing: 2px;
  min-height: 40px;
  display: flex;
  align-items: center;
  justify-content: flex-end;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

.btn {
  height: 60px;
  border: none;
  border-radius: 10px;
  font-size: 1.2rem;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.2s ease;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  position: relative;
  overflow: hidden;
}

.btn::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  transition: width 0.3s, height 0.3s;
}

.btn:active::before {
  width: 100%;
  height: 100%;
}

.btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.4);
}

.btn:active {
  transform: translateY(0);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
}

.btn-number {
  background: linear-gradient(145deg, #4a4a4a, #2a2a2a);
  color: white;
  border: 1px solid #555;
}

.btn-number:hover {
  background: linear-gradient(145deg, #5a5a5a, #3a3a3a);
}

.btn-operator {
  background: linear-gradient(145deg, #ff9500, #e6850e);
  color: white;
  border: 1px solid #cc7a00;
}

.btn-operator:hover {
  background: linear-gradient(145deg, #ffad33, #ff9500);
}

.btn-operator.active {
  background: linear-gradient(145deg, #ffad33, #ff9500);
  box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.3);
}

.btn-equals {
  background: linear-gradient(145deg, #ff9500, #e6850e);
  color: white;
  border: 1px solid #cc7a00;
  grid-row: span 2;
  height: 130px;
}

.btn-equals:hover {
  background: linear-gradient(145deg, #ffad33, #ff9500);
}

.btn-clear {
  background: linear-gradient(145deg, #dc3545, #c82333);
  color: white;
  border: 1px solid #bd2130;
}

.btn-clear:hover {
  background: linear-gradient(145deg, #e85d6d, #dc3545);
}

.btn-zero {
  grid-column: span 2;
}

@media (max-width: 400px) {
  .calculator {
    padding: 15px;
    max-width: 280px;
  }
  
  .btn {
    height: 50px;
    font-size: 1rem;
  }
  
  .display-text {
    font-size: 1.5rem;
  }
  
  .btn-equals {
    height: 110px;
  }
}
</style>