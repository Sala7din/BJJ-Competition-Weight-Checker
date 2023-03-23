<script setup>
import WelcomeItem from './WelcomeItem.vue'
import GenderIcon from './icons/IconGender.vue'
import WeightClassIcon from './icons/IconWeightClass.vue'
import CurrentWeightIcon from './icons/IconCurrentWeight.vue'
import GiIcon from './icons/IconGi.vue'
import BeltIcon from './icons/IconBelt.vue'
import WeightInput from './inputItems/WeightInput.vue'
import GenderAndWeightClassSelector from './inputItems/GenderAndWeightClassSelector.vue'
</script>



<template>
  <WelcomeItem>
    <template #icon>
      <GenderIcon />
    </template>
    <template #heading>Gender</template>
    <gender-and-weight-class-selector></gender-and-weight-class-selector>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <WeightClassIcon />
    </template>
    <template #heading>IBJJF Gi Weight Class</template>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <CurrentWeightIcon />
    </template>
    <template #heading>Current Body Weight</template>
    <WeightInput v-model="weight" :placeholder="'Enter your current weight'"/>

  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <GiIcon />
    </template>
    <template #heading>GI Weight</template>
    <WeightInput v-model="weight" :placeholder="'Enter Gi weight'"/>

  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <BeltIcon />
    </template>
    <template #heading>Belt Weight</template>
    <WeightInput v-model="weight" :placeholderText="'Enter Belt weight'"/>

  </WelcomeItem>
  <!-- TODO: Replace select element with component -->
  <button onclick="calculate()">Click to calculate</button>


</template>
