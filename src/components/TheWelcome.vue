<script setup>
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconCurrentWeight.vue'
import ToolingIcon from './icons/IconGi.vue'
import EcosystemIcon from './icons/IconBelt.vue'
import CommunityIcon from './icons/IconCompetition.vue'
import SupportIcon from './icons/IconWeightClass.vue'
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>Current Weight</template>

    <input type="radio" id="lb" value="Pound"  />
	  <label for="gi">kg</label>

	  <input type="radio" id="kg" value="Kilograms"/>
	  <label for="no gi">lb</label>
    <br>
    <input type="text" placeholder="Type in your current weight">
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <ToolingIcon />
    </template>
    <template #heading>Gi or No Gi</template>
    
    

	  
    
    Select either "Gi" or "No Gi" if you won't be wearing a Gi. If you plan to compete in a Gi Competition, choose the brand and size of your gi from the drop-down menu.
    <br>
    
    <input type="radio" id="gi" value="Gi"/>
	  <label for="gi">Gi</label>

	  <input type="radio" id="no gi" value="No Gi"/>
	  <label for="no gi">No Gi</label>
    <br>
    <!-- TODO: #3 Dropdown menu should only appear if the "Gi" radio button is selected -->
    <select></select> <select></select>
    
    
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <EcosystemIcon />
    </template>
    <template #heading>Belt</template>
    Click on the drop-down menu and select the brand and size of your belt.
    <br>
    <select></select> <select></select>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <CommunityIcon />
    </template>
    <template #heading>Competition</template>
    Click on the drop-down menu and select the BJJ competition you plan to participate in.
    <br>
    <select></select>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <SupportIcon />
    </template>
    <template #heading>Weight Class</template>
    Click on the drop-down menu and select the weight class you plan to compete in. The weight classes are based on the current BJJ tournaments.
    <br>
    <select></select>
  </WelcomeItem>

  <input type="submit" >


</template>
