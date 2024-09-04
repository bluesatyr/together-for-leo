<script setup>
import PageSection from './components/PageSection.vue';
import CallToActionButton from './components/CallToActionButton.vue';
import CallToActionSection from './components/CallToActionSection.vue';
import CallToActionListItem from './components/CallToActionListItem.vue';
import Modal from './components/Modal.vue';
import { ref } from 'vue';
const bgColors = ['bg-gray-100', 'bg-gray-200'];

const callToAction = ref();
const helpClicked = ref(false);

const scrollToElement = () => {
  callToAction.value.$el.scrollIntoView({ behavior: "smooth" });
  helpClicked.value = true;
};

const modalContent = ref('');
const isModalVisible = ref(false);

const openModal = (data) => {
  modalContent.value = data.content;
  isModalVisible.value = true;
};


const paymentOptions = [
  { id: 1, 
    title: "Option 1: Interac e-Transfer", 
    subtitle: "(for transfers from Canadian bank accounts)", 
    description: "If you are located in Canada, our first preference is to transfer via Interac e-transfer or EFT (see option 3) to minimize payment processing fees (2.9% on GoFundMe).", 
    content: 
      `<div>
        <h3 class="text-center">Interac e-Transfer in Canada</h3>
        <p class="my-4">Please use the following email adddress for Interac transfers within Canada:</p>
        <div class="text-blue-500 text-center mt-2">leomedicalcare@gmail.com</div>
      </div>` 
  },  
  { id: 2, 
    title: "Option 2: Bank transfer to Indian bank account", 
    subtitle: null, 
    description: "If you are located in India, our preference is to transfer funds directly into Leo’s bank account", 
    content: 
      `<div>
        <h3 class="text-center">Indian Bank Transfer</h3>
        <p class="my-4">Please use the following bank information to transfer funds to Leo's Account:</p>
        <div>
          <ul>
            <li><strong>Account holder:</strong> Arun Kapoor</li>
            <li><strong>Bank:</strong> HDFC Bank</li>
            <li><strong>Account number:</strong> 02021750000131</li>
            <li><strong>IFSC code:</strong> HDFC0000202</li>
            <li><strong>Branch:</strong> SHOP NO. 1 & 2COSMOS TOWERS, NEAR GOVERNMENT BUILDING COMPLEX, MAPUSA, GOA, 403507</li>
          </ul>
        </div>
      </div>` 
  },
  { id: 3, 
    title: "Option 3: Bank transfer to Canadian bank account", 
    subtitle: null, 
    description: null, 
    content: 
      `<div>
        <h3 class="text-center">Bank Transfer to Canadian Bank</h3>
        <p class="my-4">Please use the following bank information to transfer funds to our Canadian Account:</p>
        <div>
          <ul>
            <li><strong>Account Holder or Beneficiary Name:</strong> Denise Fernandes</li>
            <li><strong>Bank Name:</strong> TD Canada Trust</li>
            <li><strong>Institution Number:</strong> 004</li>
            <li><strong>Transit Number:</strong> 02352</li>
            <li><strong>Account Number:</strong> 6448166</li>
          </ul>
        </div>
      </div>` 
  },
  { id: 4, 
    title: "Option 4: GoFundMe", 
    subtitle: "(accepts Google Pay, Debit and Credit Card payments)", 
    description: "For all other contributors located outside of India or Canada, or if your preference is to donate via credit card or Google Pay", 
    content: 
      `<div>
        <h3 class="text-center">Leo's GoFundMe Campaign</h3>
        <p class="my-4">Please follow this link to donate to the GoFundMe Campaign we've set up:</p>
        <div class="text-center">
          <a href="https://www.gofundme.com/f/LeosRoadtoRecovery">Leo's GoFundMe Page</a>
        </div>
      </div>` 
  } 
]
</script>

<template>
  <div class="container mx-auto">
    <header class="text-center py-8 px-2">
      <h1 class="text-3xl font-bold">Together For Leo</h1>
      <p class="text-gray-500 text-lg">Join Us in Supporting Leo Through His Medical Crisis</p>
      <p class="text-left">
        My name is Denise Fernandes and I am raising funds for my uncle’s medical bills and ongoing medical care. My uncle, Leo Arun Kapoor, had a cardiac arrest which resulted in anoxic brain injury. He is in need of continuing medical care and needs financial support.
      </p>
    </header>
    <PageSection 
      :bgColor="bgColors[0]"
      title="How Your Funds Will Be Used"
      >
      <div class="pt-2">Your contribution will help us cover the following expenses:
        <ul class="list-disc ml-5">
          <li><strong>$195,437 CAD</strong> - Hospital bills for 23 days in Montreal</li>
          <li><strong>$81,351 CAD</strong> - Evacuation cost from Montreal to Goa which included medical escorts on a commercial flight from Montreal to Mumbai and then an air ambulance from Mumbai to Goa.</li>
        </ul>
      </div>
      <div class="py-2">Any funds over and above our fundraising goal will help cover ongoing care for Leo:
        <ul class="list-disc ml-5">
          <li><strong>Medical equipment and supplies</strong></li>
          <li><strong>24-hour home nurse</strong> (₹39,000 INR per month)</li>
        </ul>
      </div>
      </PageSection>
    <CallToActionSection ref="callToAction">
      <div class="mb-2">
        Our first priority is to pay the medical evacuation costs and then the Montreal hospital bills, both of which were incurred in Canadian dollars.
      </div>
      <div class="mb-2">
        If you wish to contribute <strong>click on one of the 4 options below</strong> to transfer funds to cover Leo’s medical bills:
      </div>
      <ul>
        <CallToActionListItem
          v-for="item in paymentOptions"
          :key="item.id"
          :title="item.title"
          :subtitle="item.subtitle"
          :description="item.description"
          :content="item.content"
          @showModal="openModal"
        />
        <Modal :content="modalContent" :isVisible="isModalVisible" @close="isModalVisible = false" />
      </ul>
      <div>
        Thank you so much for your support! It means so much to Leo and our family.
      </div>
    </CallToActionSection>
    <PageSection 
      :bgColor="bgColors[0]"
      title="Leo's Story"
      imageUrl="/src/assets/img/leo.png"
    >
    <div class="my-1">My aunt and uncle, Lourdes and Leo Kapoor, travelled from India to Canada in June to visit relatives and to take some of the ashes of my late aunt Dorothy back to India.</div>
    <div class="my-1">It was their first time visiting Canada. They initially applied for a visit visa to attend the funeral of my aunt Dorothy Soares, who passed away from cancer in February 2024. However, they were unable to get the Canada visa in time for the funeral.</div>
    <div class="my-1">Leo and Lourdes arrived in Canada on June 4 and spent the next five weeks visiting and sightseeing with relatives.</div>

    </PageSection>
    
    <PageSection :bgColor="bgColors[1]"
      title="The Medical Crisis"
      content="On July 11, I drove from Mississauga to Montreal with my parents and Leo and Lourdes for a short trip with the intention of visiting the Notre-Dame Basilica in Montreal. On July 12, I drove to Maison Smith after breakfast and as I pulled into the parking lot, Leo suffered an unexpected cardiac arrest while seated in the car. I called 911 and got the assistance of an employee from Maison Smith that knew CPR and had a defibrillator. The firefighters and ambulance arrived on the scene and the paramedics continued CPR until Leo was resuscitated. He was then rushed to Jewish General Hospital in Montreal, where he was admitted to the ICU. He remained in ICU until July 27 and was then moved to the cardiac unit until August 4."
      >
      </PageSection>
    <PageSection :bgColor="bgColors[0]"
      title="Transporting Leo to Goa, India"
      content="Our intention was to transport Leo back to India after the first week in hospital when the doctors in Montreal had cleared him for travel. We were advised of two primary options - air ambulance services or medical escort services.
1. Air ambulance services: This is a small chartered plane that includes two medical team members to care for the patient during the flight. We received 5 quotes ranging from $250,000 to $450,000 CAD.
2. Medical Escort services: The patient is transported on a commercial airline with two medical team members to care for the patient during the flight. In this case, a few rows of seats are removed or folded to accommodate a stretcher and medical equipment. We received quotes ranging from $67,000 to $90,000 CAD.

Since the quotes we received for air ambulance services were prohibitively expensive, we first explored medical escort services. I had checked with the insurer and was advised that medical evacuation costs were covered in the policy. We had hoped that the policy would reimburse these costs.

Unfortunately, we hit stumbling blocks and had difficulties getting approval to fly on a commercial airline. Several airlines turned down our application due to Leo’s heart condition. By the time we were able to secure a flight to India on August 4, Leo had already been at the hospital for 23 days and had exceeded his insurance policy coverage."
      >
      </PageSection>
    <PageSection :bgColor="bgColors[1]"
      title="Travel Insurance"  
      content="Leo did have a travel insurance policy for the equivalent of $135,000 CAD. After nearly 6 weeks back and forth with the insurer sending emails, making calls, sending forms and documents, they advised us on August 21, 2024, that Leo will not be reimbursed for any expenses under the exclusion of pre-existing conditions. The pre-existing condition is that Leo has coronary artery disease and had two stents installed in 2008, even though he did not have a cardiac event in the last 15 years. This news was very distressing for the family when we are already dealing with an extremely difficult and stressful situation. We have appealed this decision with the insurer but have now decided to reach out to family and friends for financial support."      >
      </PageSection>
      
    <PageSection :bgColor="bgColors[1]"
      title="Leo’s Progress and Current Medical Condition"
      content="For the first 3 days in the ICU, Leo was comatose and intubated. By Day 4, Leo opened his eyes but did not show awareness or recognition. The neurologist requested an MRI and EEG which unfortunately showed brain damage due to the brain being starved of oxygen during the cardiac arrest. By week 2 and 3 in Canada, Leo showed improvement by moving his mouth and slight head movements. But in week 4, he was not as responsive after his arrival in Goa. However, he has shown improvement over the past 2 weeks.

Leo is currently at home in Goa with a 24-hour nurse since August 9, 2024. He is breathing on his own and his heart is beating on its own. There is an oxygen concentrator as a backup whenever his oxygen levels dip. He had a tracheostomy in Montreal and was also fitted with a PEG feeding tube (stomach port). He is fed a liquid diet by the nurse via the stomach port every 2 hours from 6 am to midnight. He is also provided heart medications via the stomach port. His position in the bed is moved every 2 hours to prevent bedsores. Caring for Leo is a full-time job for his loving wife Lourdes.

Overall, Leo has demonstrated slow but gradual improvement – eyes opening, ability to track movement with his eyes, responding to name cues, movements of the head, arm and shoulders. These are encouraging signs but his road to recovery is a long one and he will need support throughout this journey.
"
    >
    </PageSection>
    
    <CallToActionButton v-if="!isModalVisible" @click="scrollToElement"/>
  </div>
</template>

<style scoped>

</style>
