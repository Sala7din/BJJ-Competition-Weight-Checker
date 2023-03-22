<template>
  <div>
    <label for="weight">Weight (kg):</label>
    <input type="number" id="weight" v-model="value" @input="onInput">
    <p v-if="invalidInput" style="color: red;">Please enter a valid weight in kilograms.</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: null,
      invalidInput: false,
    };
  },
  methods: {
    onInput() {
      if (isNaN(this.value) || this.value <= 0) {
        this.invalidInput = true;
        this.value = null;
      } else {
        this.invalidInput = false;
        this.value = Number(this.value.toFixed(2));
      }
    },
  },
};
</script>