<script setup>
import PageSection from './components/PageSection.vue';
import CallToActionButton from './components/CallToActionButton.vue';
import CallToActionSection from './components/CallToActionSection.vue';
import CallToActionListItem from './components/CallToActionListItem.vue';
import { ref } from 'vue';
const bgColors = ['bg-gray-100', 'bg-gray-200'];

const callToAction = ref();

const scrollToElement = () => {
  callToAction.value.$el.scrollIntoView({ behavior: "smooth" });
};
</script>

<template>
  <div class="container mx-auto">
    <header class="text-center py-8 px-2">
      <h1 class="text-3xl font-bold">Together For Leo</h1>
      <p class="text-gray-500 text-lg">Join Us in Supporting Leo Through His Medical Crisis</p>
    </header>
    <PageSection 
      :bgColor="bgColors[0]"
      title="My Uncle Leo"
      content="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam lobortis tincidunt nulla, sed dapibus tellus tristique bibendum. Vivamus tortor lectus, cursus quis ultrices sit amet, luctus eu Leo."
      ></PageSection>
    <PageSection :bgColor="bgColors[1]"
      title="What Happened..."
      content="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam lobortis tincidunt nulla, sed dapibus tellus tristique bibendum. Vivamus tortor lectus, cursus quis ultrices sit amet, luctus eu Leo."
      >
      </PageSection>
    <PageSection :bgColor="bgColors[0]"
      content="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam lobortis tincidunt nulla, sed dapibus tellus tristique bibendum. Vivamus tortor lectus, cursus quis ultrices sit amet, luctus eu Leo."
      >
      </PageSection>
    <PageSection :bgColor="bgColors[1]"
      content="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam lobortis tincidunt nulla, sed dapibus tellus tristique bibendum. Vivamus tortor lectus, cursus quis ultrices sit amet, luctus eu Leo."
      >
      </PageSection>
      <PageSection 
      :bgColor="bgColors[0]"
      content="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam lobortis tincidunt nulla, sed dapibus tellus tristique bibendum. Vivamus tortor lectus, cursus quis ultrices sit amet, luctus eu Leo."
      >
      </PageSection>
    <PageSection :bgColor="bgColors[1]"
      content="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam lobortis tincidunt nulla, sed dapibus tellus tristique bibendum. Vivamus tortor lectus, cursus quis ultrices sit amet, luctus eu Leo."
      >
    </PageSection>
    <CallToActionSection ref="callToAction">
      <ul>
        <CallToActionListItem
          title="Option 1: Interac e-Transfer"
          subtitle="(for transfers from Canadian bank accounts)"
        >
        </CallToActionListItem>
        <CallToActionListItem
          title="Option 2: Bank transfer to Indian bank account"
        >
        </CallToActionListItem>
        <CallToActionListItem
          title="Option 3: Bank transfer to Canadian bank account"
        >
        </CallToActionListItem>
        <CallToActionListItem
          title="Option 4: GoFundMe"
          subtitle="(accepts Google Pay, Debit and Credit Card payments)"
        >
        </CallToActionListItem>
      </ul>
    </CallToActionSection>
    <CallToActionButton @click="scrollToElement"/>
  </div>
</template>

<style scoped>

</style>
