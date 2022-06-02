<template>
    <v-card
        outlined
        class="rounded-lg"
    >
        <v-card-text>
            <v-tabs class="align-center">
                
                    <div 
                        class="text-h6 font-weight-medium black--text"
                        color="black"
                    >
                        Statistics
                    </div>
                    <v-spacer></v-spacer>
                    <v-tab>Daily</v-tab>
                    <v-tab>Weekly</v-tab>
                    <v-tab>Monthly</v-tab>
                
            
                <v-tab-item class="mt-3">
                    <v-card flat>
                        <line-chart :data="chartData1" :curve="false"></line-chart>
                    </v-card>
                </v-tab-item>
                <v-tab-item class="mt-3">
                    <v-card flat>
                        <line-chart :data="chartData2" :curve="false"></line-chart>
                    </v-card>
                </v-tab-item>
                <v-tab-item class="mt-3">
                    <v-card flat>
                        <line-chart :data="chartData3" :curve="false"></line-chart>
                    </v-card>
                </v-tab-item>

            </v-tabs>
        </v-card-text>
    </v-card>
</template>

<script>
    // import line-chart from 'vue-chartkick';
    export default {
        data: () => ({
            chartData1: [['Sun', 1500], ['Mon', 2000], ['Tue', 800], ['Wed',1000], ['Thu',1500]],
            chartData2: [['Sun', 100], ['Mon', 3000], ['Tue', 800], ['Wed',5000], ['Thu',1500]],
            chartData3: [['Sun', 1500], ['Mon', 2000], ['Tue', 800], ['Wed',1000], ['Thu',1500]],

        }),
    }
</script>