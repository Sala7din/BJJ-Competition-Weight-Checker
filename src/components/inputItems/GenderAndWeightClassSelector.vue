<template>
  <div>
    <input type="radio" id="male" value="male" v-model="selectedGender">
    <label for="male">Male</label>
    <input type="radio" id="female" value="female" v-model="selectedGender">
    <label for="female">Female</label>
    <br>
    <select v-if="selectedGender === 'male' || selectedGender === 'female'">
      <option value="" disabled selected>Choose your Weight Class</option>
      <option v-for="weightClass in weightClasses" :key="weightClass">{{ weightClass }}</option>
    </select>
  </div>
</template>

  
<script>
  export default {
    name: 'GenderAndWeightClassSelector',
    data() {
      return {
        selectedGender: null
      }
    },
    computed: {
      weightClasses() {
        if (this.selectedGender === 'male') {
          return ['Rooster (57.5kg/126.5lbs)', 'Light Feather (64kg/141lbs)', 'Feather (70kg/154lbs)', 'Light (76kg/167lbs)', 'Middle (82.3kg/181lbs)', 'Medium Heavy (88.3kg/195lbs)', 'Heavy (94.3kg/208lbs)', 'Super Heavy (97.5kg/215lbs)', 'Ultra Heavy (No maximum)']
        } else if (this.selectedGender === 'female') {
          return ['Rooster (47.5kg/107lbs)', 'Light Feather (52.2kg/115lbs)', 'Feather (57kg/125.5lbs)', 'Light (62.8kg/138.5lbs)', 'Middle (69.1kg/152lbs)', 'Medium Heavy (76.1kg/167.5lbs)', 'Heavy (82.3kg/181.5lbs)', 'Super Heavy (No maximum)']
        } else {
          return []
        }
      }
    }
  }
</script>
  
  