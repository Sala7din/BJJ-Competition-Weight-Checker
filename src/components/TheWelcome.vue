<template> 
  <WelcomeItem>
    <template #icon>
      <WeightClassIcon />
    </template>
    <template #heading>IBJJF Gi Weight Class</template>
    <div>
    <input type="radio" id="male" value="male" v-model="selectedGender">
    <label for="male">Male</label>
    <input type="radio" id="female" value="female" v-model="selectedGender">
    <label for="female">Female</label>
    <br>
    <select v-if="selectedGender === 'male' || selectedGender === 'female'" v-model="selectedWeightClass">
      <option value="" disabled selected>Choose your Weight Class</option>
      <option v-for="weightClass in weightClasses" :key="weightClass.value" :value="weightClass.value">{{ weightClass.name }}</option>
    </select>
  </div>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <CurrentWeightIcon />
    </template>
    <template #heading>Current Body Weight</template>
    <div>
      <input type="number" id="bodyWeight" v-model="bodyWeight" @input="onInput" placeholder="Enter your Body Weight"><label for="bodyWeight"> kg</label>
      <p v-if="invalidInput" style="color: red;">Please enter a valid weight in kilograms.</p>
  </div>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <GiIcon />
    </template>
    <template #heading>GI Weight</template>
    <div>
      <input type="number" id="giWeight" v-model="giWeight" @input="onInput" placeholder="Enter Gi Weight"><label for="giWeight"> kg</label>
      <p v-if="invalidInput" style="color: red;">Please enter a valid weight in kilograms.</p>
  </div>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <BeltIcon />
    </template>
    <template #heading>Belt Weight</template>
    <div>
      <input type="number" id="beltWeight" v-model="beltWeight" @input="onInput" placeholder="Enter Belt Weight"><label for="beltWeight"> kg</label>
      <p v-if="invalidInput" style="color: red;">Please enter a valid weight in kilograms.</p>
    </div>
  </WelcomeItem>
  
  <WelcomeItem>
    <template #icon>
      <CalculatorIcon />
    </template>
    <template #heading>Calculate</template>
    <button @click="checkWeight">Check Weight</button>
    <p v-if="result"> {{result}} </p>
  </WelcomeItem>
</template>

<script>
import WelcomeItem from './WelcomeItem.vue'
import WeightClassIcon from './icons/IconWeightClass.vue'
import CurrentWeightIcon from './icons/IconCurrentWeight.vue'
import GiIcon from './icons/IconGi.vue'
import BeltIcon from './icons/IconBelt.vue'
import CalculatorIcon from './icons/IconCalculator.vue'


export default {
    name: 'TheWelcome',
    components:
    {
      WelcomeItem,
      WeightClassIcon,
      CurrentWeightIcon,
      GiIcon,
      BeltIcon,
      CalculatorIcon,
    },
    data(){
      return {
        bodyWeight: {
        type: Number,
        default: 0
      },
      giWeight: {
        type: Number,
        default: 0
      },
      beltWeight: {
        type: Number,
        default: 0
      },
      selectedWeightClass: {
        type: Number,
        default: 0
      },
      selectedGender: null,
      selectedWeightClass: null,
      value: null,
      invalidInput: false,
      result: '',
    }

    },
    computed: {
    weightClasses() {
      if (this.selectedGender === 'male') {
        return [
          { name: 'Rooster (57.5kg/126.5lbs)', value: 57.5 },
          { name: 'Light Feather (64kg/141lbs)', value: 64 },
          { name: 'Feather (70kg/154lbs)', value: 70 },
          { name: 'Light (76kg/167lbs)', value: 76 },
          { name: 'Middle (82.3kg/181lbs)', value: 82.3 },
          { name: 'Medium Heavy (88.3kg/195lbs)', value: 88.3 },
          { name: 'Heavy (94.3kg/208lbs)', value: 94.3 },
          { name: 'Super Heavy (97.5kg/215lbs)', value: 97.5 },
          { name: 'Ultra Heavy (No maximum)', value: null }
        ]
      } else if (this.selectedGender === 'female') {
        return [
          { name: 'Rooster (47.5kg/107lbs)', value: 47.5 },
          { name: 'Light Feather (52.2kg/115lbs)', value: 52.2 },
          { name: 'Feather (57kg/125.5lbs)', value: 57 },
          { name: 'Light (62.8kg/138.5lbs)', value: 62.8 },
          { name: 'Middle (69.1kg/152lbs)', value: 69.1 },
          { name: 'Medium Heavy (76.1kg/167.5lbs)', value: 76.1 },
          { name: 'Heavy (82.3kg/181.5lbs)', value: 82.3 },
          { name: 'Super Heavy (No maximum)', value: null }
        ]
      } else {
        return []
      }
    }
  },
    methods: {
      checkWeight() {
        const totalWeight = this.bodyWeight + this.giWeight + this.beltWeight;
        if (totalWeight <= this.selectedWeightClass) {
          const difference = this.selectedWeightClass - totalWeight
          this.result = `You are within the weight limit and have ${difference} kg tolerance`;
        } else {
          const difference = totalWeight - this.selectedWeightClass
          this.result = `You are above the weight limit and need to loose ${difference} kg`;
        }
      },
      onInput() {
      if (isNaN(this.value) || this.value <= 0) {
        this.invalidInput = true;
        this.value = null;
      } else {
        this.invalidInput = false;
        this.value = parseFloat(this.value.toFixed(3));
      }
    }
    }
  }
</script>