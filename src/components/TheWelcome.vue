<script setup>
import WelcomeItem from './WelcomeItem.vue'
import WeightClassIcon from './icons/IconWeightClass.vue'
import CurrentWeightIcon from './icons/IconCurrentWeight.vue'
import GiIcon from './icons/IconGi.vue'
import BeltIcon from './icons/IconBelt.vue'
import CalculatorIcon from './icons/IconCalculator.vue'
import GenderAndWeightClassSelector from './inputOut/GenderAndWeightClassSelector.vue'
import BodyWeightInput from './inputOut/BodyWeightInput.vue'
import GiWeightInput from './inputOut/GiWeightInput.vue'
import BeltWeightInput from './inputOut/BeltWeightInput.vue'
import CalcButton from './inputOut/CalcButton.vue'
</script>



<template>
  
  <WelcomeItem>
    <template #icon>
      <WeightClassIcon />
    </template>
    <template #heading>IBJJF Gi Weight Class</template>
    <GenderAndWeightClassSelector v-model="selectedWeightClass"></GenderAndWeightClassSelector>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <CurrentWeightIcon />
    </template>
    <template #heading>Current Body Weight</template>
    <BodyWeightInput v-model="bodyWeight" :placeholder="'Enter your current weight'"/>

  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <GiIcon />
    </template>
    <template #heading>GI Weight</template>
    <GiWeightInput v-model="giWeight" :placeholder="'Enter Gi weight'"/>

  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <BeltIcon />
    </template>
    <template #heading>Belt Weight</template>
    <BeltWeightInput v-model="beltWeight" :placeholder="'Enter Belt weight'"/>

  </WelcomeItem>
  
  <WelcomeItem>
    <template #icon>
      <CalculatorIcon />
    </template>
    <template #heading>Calculate</template>
    <CalcButton buttonText="Calculate" @clicked="handleButtonClicked" />
  </WelcomeItem>
  
  


</template>
