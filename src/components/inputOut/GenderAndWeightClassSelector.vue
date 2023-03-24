<template>
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
</template>

<script>
export default {
  name: 'GenderAndWeightClassSelector',
  data() {
    return {
      selectedGender: null,
      selectedWeightClass: null
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
  }
}
</script>


  
  