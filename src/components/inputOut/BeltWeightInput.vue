<template>
  <div>
    <input type="number" id="beltWeight" v-model="value" @input="onInput" :placeholder="placeholder"><label for="beltWeight"> kg</label>
    <p v-if="invalidInput" style="color: red;">Please enter a valid weight in kilograms.</p>
  </div>
</template>

<script>
export default {
  props: {
    placeholder: {
      type: String,
      default: 'Enter weight in kilograms'
    }
  },
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
        this.value = Number(this.value.toFixed(3));
      }
    },
  },
};
</script>