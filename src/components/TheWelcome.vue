<script setup>
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>Current Weight</template>

    The first field in the form is labeled "Weight (in lbs/kg)." Click inside this field and type in your weight in pounds or kilograms .
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <ToolingIcon />
    </template>
    <template #heading>GI</template>

    The next field is labeled "Gi." Click on the drop-down menu and select either "Yes" if you plan to wear a gi or "No" if you won't be wearing a gi. If you plan to wear a gi, you can also choose the brand of your gi from a separate drop-down menu.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <EcosystemIcon />
    </template>
    <template #heading>Belt</template>

    The third field is labeled "Belt." Click on the drop-down menu and select the color and brand of your belt.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <CommunityIcon />
    </template>
    <template #heading>Competition</template>

    Click on the drop-down menu and select the BJJ competition you plan to participate in.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <SupportIcon />
    </template>
    <template #heading>Weight Class</template>

     Click on the drop-down menu and select the weight class you plan to compete in. The weight classes are based on the current BJJ tournaments.
  </WelcomeItem>

  <input type="submit" >


</template>
