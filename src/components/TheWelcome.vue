<script setup>
// TODO: #1 Update icons with suitable icons by using a CDN
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

    Click inside this field and type in your weight in pounds or kilograms .
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <ToolingIcon />
    </template>
    <template #heading>GI</template>

    Select either "Gi" or "No Gi" if you won't be wearing a Gi. If you plan to compete in a Gi Competition, choose the brand and size of your gi from the drop-down menu.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <EcosystemIcon />
    </template>
    <template #heading>Belt</template>

   Click on the drop-down menu and select the brand and size of your belt.
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
