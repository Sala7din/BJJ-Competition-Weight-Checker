<template>
  <!--TODO: Rename Components-->
  <WelcomeItem>
    <template #icon>
      <WeightClassIcon />
    </template>
    <template #heading>IBJJF Gi Weight Class</template>
    <div>
      <input type="radio" id="kg" value="kg" v-model="selectedWeightUnit">
      <label for="kg">kg</label>
      <input type="radio" id="lbs" value="lbs" v-model="selectedWeightUnit">
      <label for="lbs">lbs</label>
      <br>
    </div>
    <div>
      <input type="radio" id="male" value="male" v-model="selectedGender">
      <label for="male">Male</label>
      <input type="radio" id="female" value="female" v-model="selectedGender">
      <label for="female">Female</label>
      <br>
      <select v-model="selectedWeightClass">
        <option value="" disabled selected>Choose your Weight Class</option>
        <option v-for="weightClass in weightClasses" :key="weightClass.value" :value="weightClass.value">
          {{ weightClass.name }}
        </option>
      </select>
      <!--TODO: Add funny phrase(like "Maybe you should try Sumo") that is shown to user if "Super heavy" is selected-->
      <p v-if="selectedWeightClass === 'Ultra Heavy (No maximum)' || selectedWeightClass === 'Super Heavy (No maximum)'">
        Maybe you should try Sumo!
      </p>
    </div>
  </WelcomeItem>
  <WelcomeItem>
    <template #icon>
      <CurrentWeightIcon />
    </template>
    <template #heading>Current Body Weight</template>
    <div>
      <input type="number" id="bodyWeight" v-model.number="bodyWeight" @input="onInput"
        placeholder="Enter your Body Weight" min="0">
      <label for="bodyWeight">{{ weightUnitLabel }}</label>
      <p v-if="invalidInput" style="color: red;">Please enter a valid weight in kilograms.</p>
    </div>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <GiIcon />
    </template>
    <template #heading>GI Weight</template>
    <div>
      <input type="number" id="giWeight" v-model.number="giWeight" @input="onInput" placeholder="Enter Gi Weight" min="0">
      <label for="giWeight">{{ weightUnitLabel }}</label>
      <p v-if="invalidInput" style="color: red;">Please enter a valid weight in kilograms.</p>
    </div>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <BeltIcon />
    </template>
    <template #heading>Belt Weight</template>
    <div>
      <input type="number" id="beltWeight" v-model.number="beltWeight" @input="onInput" placeholder="Enter Belt Weight"
        min="0">
      <label for="beltWeight">{{ weightUnitLabel }}</label>
      <p v-if="invalidInput" style="color: red;">Please enter a valid weight in kilograms.</p>
    </div>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <CalculatorIcon />
    </template>
    <template #heading>Calculate</template>
    <button @click="checkWeight">Check Weight</button>
    <button v-if="result" @click="reset">Reset</button>
    <p v-if="result" v-html="result"></p>
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
  data() {
    return {
      bodyWeight: 0,
      giWeight: 0,
      beltWeight: 0,
      selectedWeightClass: 0,
      selectedWeightUnit: 'kg',
      selectedGender: 'male',
      value: null,
      invalidInput: false,
      result: '',
    }
  },
  watch: {
    selectedWeightUnit(newValue, oldValue) {
      if (newValue !== oldValue) {
        this.selectedGender = null;
        this.selectedWeightClass = null;
      }
    },
  },
  computed: {
    isGenderFemale() {
      return this.selectedGender === 'female'
    },
    isWeightUnitKg() {
      return this.selectedWeightUnit === 'kg'
    },
    weightUnitLabel() {
      return this.isWeightUnitKg ? ' kg' : ' lbs'
    },
    weightClasses() {
      if (!this.isGenderFemale  && !this.isWeightUnitKg) {
        return [
          { name: 'Rooster (127lbs)', value: 127 },
          { name: 'Light Feather (141lbs)', value: 141 },
          { name: 'Feather (154lbs)', value: 154 },
          { name: 'Light (168lbs)', value: 168 },
          { name: 'Middle (181lbs)', value: 181 },
          { name: 'Medium Heavy (194.5lbs)', value: 194.5 },
          { name: 'Heavy (208lbs)', value: 208 },
          { name: 'Super Heavy (221lbs)', value: 221 },
          { name: 'Ultra Heavy (No maximum)', value: -1 },
        ];
      } else if (this.isGenderFemale  && this.isWeightUnitKg) {
        return [
          { name: 'Rooster (48.5kg)', value: 48.5 },
          { name: 'Light Feather (53.5kg)', value: 53.5 },
          { name: 'Feather (58.5kg)', value: 58.5 },
          { name: 'Light (64kg)', value: 64 },
          { name: 'Middle (69kg)', value: 69 },
          { name: 'Medium Heavy (74kg)', value: 74 },
          { name: 'Heavy (79kg)', value: 79 },
          { name: 'Super Heavy (No maximum)', value: -1 },
        ];
      } else if (this.isGenderFemale || !this.isWeightUnitKg) {
        return [
          { name: 'Rooster (107lbs)', value: 107 },
          { name: 'Light Feather (115lbs)', value: 115 },
          { name: 'Feather (125.5lbs)', value: 125.5 },
          { name: 'Light (138.5lbs)', value: 138.5 },
          { name: 'Middle (152lbs)', value: 152 },
          { name: 'Medium Heavy (167.5lbs)', value: 167.5 },
          { name: 'Heavy (181.5lbs)', value: 181.5 },
          { name: 'Super Heavy (No maximum)', value: 9999 }
        ];
      }
      return [
        { name: 'Rooster (57.5kg)', value: 57.5 },
        { name: 'Light Feather (64kg)', value: 64 },
        { name: 'Feather (70kg)', value: 70 },
        { name: 'Light (76kg)', value: 76 },
        { name: 'Middle (82.3kg)', value: 82.3 },
        { name: 'Medium Heavy (88.3kg)', value: 88.3 },
        { name: 'Heavy (94.3kg)', value: 94.3 },
        { name: 'Super Heavy (100.5kg)', value: 100.5 },
        { name: 'Ultra Heavy (No maximum)', value: -1 },
      ];

    }
  },
  // FIXME: input validation. Shows me "You are above the weight limit and need to lose NaN{{ }}" when I ONLY select the weight class and calculate

  methods: {
    checkWeight() {
      if (!this.selectedWeightUnit || !this.selectedGender || !this.selectedWeightClass || !this.bodyWeight || !this.giWeight || !this.beltWeight) {
        this.result = "Please enter all values.";
        return;
      }

      const totalWeight = this.bodyWeight + this.giWeight + this.beltWeight;
      if (totalWeight <= this.selectedWeightClass) {
        const difference = this.selectedWeightClass - totalWeight;
        this.result = `<span style='color:green'>You are under the weight limit by ${difference}${this.weightUnitLabel}.</span>`;
      } else {
        const difference = totalWeight - this.selectedWeightClass;
        this.result = `<span style='color:red'>You are above the weight limit and need to lose ${difference}${this.weightUnitLabel}.</span>`;
      }
    },
    // TODO: Add weight conversion
    onInput() {
      this.bodyWeight = parseFloat(this.bodyWeight.toFixed(3));
      this.giWeight = parseFloat(this.giWeight.toFixed(3));
      this.beltWeight = parseFloat(this.beltWeight.toFixed(3));
      this.invalidInput = false;
      if (this.bodyWeight < 0 || this.giWeight < 0 || this.beltWeight < 0) {
        this.invalidInput = true;
      } else {
        this.invalidInput = false;
      }
    },
    reset() {
      this.result = ''
      this.bodyWeight = 0
      this.giWeight = 0
      this.beltWeight = 0
      this.selectedWeightClass = 0
      this.selectedWeightUnit = 'kg'
      this.selectedGender = 'male'
      this.value = null
      this.invalidInput = false
      this.result = ''
    },
  }

}
</script>