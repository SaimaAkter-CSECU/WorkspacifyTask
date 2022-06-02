<template>
    <div
        class="white ma-4 rounded pa-6"
    >
        <userNameSection />
        <SummarySection />
        <ChartSection />
        <RentalDetailSection />
    </div>
</template>

<script>
    import userNameSection from './userNameSection.vue'
    import SummarySection from './SummarySection.vue'
    import ChartSection from './ChartSection.vue'
    import RentalDetailSection from './RentalDetailSection.vue'
    export default {
        components: {
            userNameSection, SummarySection, ChartSection, RentalDetailSection, 
        },
    }
</script>