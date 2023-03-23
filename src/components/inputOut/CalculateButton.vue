<template>
    <button @click="handleClick">{{ buttonText }}</button>
  </template>
  
  <script>
  export default {
    props: {
      buttonText: {
        type: String,
        default: 'Click me!'
      }
    },
    methods: {
      handleClick() {
        this.$emit('clicked');
      }
    }
  };
  </script>