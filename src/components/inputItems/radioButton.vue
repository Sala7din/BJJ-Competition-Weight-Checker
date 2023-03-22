<template>
	<div>{{ picked }}</div>

	<input type="radio" id="male" value="Male" v-model="picked" />
	<label for="male"><span>&#9794;</span></label>

	<input type="radio" id="female" value="Female" v-model="picked" />
	<label for="female"><span>&#9792;</span></label>
</template>

<script>
export default {
  data() {
    return {
      picked: 'Male'
    }
  }
}
</script>
  