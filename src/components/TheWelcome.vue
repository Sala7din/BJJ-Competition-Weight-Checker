<script setup>
import WelcomeItem from './WelcomeItem.vue'
import GenderIcon from './icons/IconGender.vue'
import WeightClassIcon from './icons/IconWeightClass.vue'
import CurrentWeightIcon from './icons/IconCurrentWeight.vue'
import GiIcon from './icons/IconGi.vue'
import BeltIcon from './icons/IconBelt.vue'
</script>


<!-- TODO: Replace standard input elements with Vue input components to practice Vue Framework   -->
<template>
  <WelcomeItem>
    <template #icon>
      <GenderIcon />
    </template>
    <template #heading>Gender</template>

    <input type="radio" id="gender" value="male"  />
	  <label for="male">Male</label>

	  <input type="radio" id="gender" value="female"/>
	  <label for="female">Female</label>
    
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <WeightClassIcon />
    </template>
    <template #heading>IBJJF Gi Weight Class</template>
        <select id="weightClass">
            <option value="" disabled selected>Choose your IBJJF Gi Weight Class</option>
            <option value="1">Rooster – under 57.5 kg (under 127 lbs)</option>
            <option value="2">Light feather – above 57.5 kg and under 64 kg (127 – 141.6 lbs)</option>
            <option value="3">Feather – above 64kg and under 70 kg (141.6 – 154.6 lbs)</option>
            <option value="4">Light – above 70kg and under 76 kg (154.6 – 168 lbs)</option>
            <option value="1">Middle – above 76 kg and under 82.3 kg (168 – 181.6 lbs)</option>
            <option value="2">Medium heavy – above 82.3 kg and under 88.3 kg (181.6 – 195 lbs)</option>
            <option value="3">Heavy – above 88.3 kg and under 94.3 kg (195 – 208 lbs)</option>
            <option value="4">Super heavy – above 94.3 kg and under 100.5 kg (208 – 222 lbs)</option>
            <option value="4">Ultra heavy – above 100.5 kg, no upper limit (222 lbs and up)</option>
        </select>
    <!-- TODO: add drop-down for female weight classes and only render when female radio button is selected -->
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <CurrentWeightIcon />
    </template>
    <template #heading>Current Body Weight</template>
    <input type="text" id="currentWeight" name="Current Weight" />
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <GiIcon />
    </template>
    <template #heading>GI Weight</template>
    <input type="text" id="giWeight" name="Gi Weight" />
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <BeltIcon />
    </template>
    <template #heading>Belt Weight</template>
    <input type="text" id="beltWeight" name="Belt Weight" />
  </WelcomeItem>

  <input type="submit" >


</template>
