<template>
    <button @click="checkWeight">Check Weight</button>
  </template>
  
  <script>
  export default {
    name: 'WeightButton',
    props: {
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
      }
    },
    methods: {
      checkWeight() {
        const totalWeight = this.userWeight + this.giWeight + this.beltWeight;
        if (totalWeight <= this.weightClass) {
          alert('You are within the weight limit!');
        } else {
          alert('You are over the weight limit!');
        }
      }
    }
  }
  </script>
  