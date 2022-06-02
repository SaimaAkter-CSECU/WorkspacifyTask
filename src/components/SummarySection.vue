<template>
    <div 
        class="py-5"
    >
        <v-row>
           <v-col
                v-for="item in total_summary_item" :key="item.i"
                cols="12"
                xs="12"
                sm="6"
                md="3"
            > 
                <v-card
                    outlined
                    class="px-6 py-4 rounded-lg"
                >
                    <div 
                        class="d-flex flex-row align-center"
                    >
                        <v-btn
                            :color="item.shade? `${item.shade} lighten-5` : '' "
                            elevation="2"
                            fab
                            small
                            style="pointer-events: none"
                        >
                            <v-icon :color="item.shade? `${item.shade} lighten-2` : '' ">{{item.icon}}</v-icon>
                        </v-btn>
                        <span class="text-h6 font-weight-medium ps-4">{{item.title}}</span>
                    </div>
                    <div 
                        class="text-xs-h6 text-sm-h5 text-md-h4 font-weight-bold text-center pt-3"
                    >
                        <span v-show="item.currency">$</span>
                        {{item.total_amount.toLocaleString()}}
                    </div>
                </v-card>
           </v-col>
           <!-- <v-col
                cols="12"
                xs="6"
                sm="3"
                md="3"
            > 
                <v-card
                    outlined
                    class="px-6 py-4 rounded-lg"
                >
                    <div 
                        class="d-flex flex-row align-center"
                    >
                        <v-btn
                            color="pink lighten-5"
                            elevation="2"
                            fab
                            small
                        >
                            <v-icon color="pink lighten-2">mdi-currency-usd</v-icon>
                        </v-btn>
                        <span class="text-h6 font-weight-medium ps-4">Total Revenue</span>
                    </div>
                    <div 
                        class="text-xs-h6 text-sm-h5 text-md-h4 font-weight-bold text-center pt-3"
                    >
                        {{total_revenue.toLocaleString()}}
                    </div>
                </v-card>
           </v-col>
           <v-col
                cols="12"
                xs="6"
                sm="3"
                md="3"
            > 
                <v-card
                    outlined
                    class="px-6 py-4 rounded-lg"
                >
                    <div 
                        class="d-flex flex-row align-center"
                    >
                        <v-btn
                            color="green lighten-5"
                            elevation="2"
                            fab
                            small
                        >
                            <v-icon color="green lighten-2">mdi-car</v-icon>
                        </v-btn>
                        <span class="text-h6 font-weight-medium ps-4">Total Cars</span>
                    </div>
                    <div 
                        class="text-xs-h6 text-sm-h5 text-md-h4 font-weight-bold text-center pt-3"
                    >
                        {{total_car.toLocaleString()}}
                    </div>
                </v-card>
           </v-col>
           <v-col
                cols="12"
                xs="6"
                sm="3"
                md="3"
            > 
                <v-card
                    outlined
                    class="px-6 py-4 rounded-lg"
                >
                    <div 
                        class="d-flex flex-row align-center"
                    >
                        <v-btn
                            color="blue lighten-5"
                            elevation="2"
                            fab
                            small
                        >
                            <v-icon color="blue lighten-2">mdi-account-multiple-outline</v-icon>
                        </v-btn>
                        <span class="text-h6 font-weight-medium ps-4">Total Customer</span>
                    </div>
                    <div 
                        class="text-xs-h6 text-sm-h5 text-md-h4 font-weight-bold text-center pt-3"
                    >
                        {{total_customer.toLocaleString()}}
                    </div>
                </v-card>
           </v-col> -->
        </v-row>
    </div>
</template>

<script>
    export default {
        data: () => ({
            total_summary_item: [
                {
                    id: 1,
                    title: 'Total Reserve',
                    total_amount: 4500,
                    icon: 'mdi-calendar-clock-outline',
                    shade: 'purple',
                    currency: false,
                },
                {
                    id: 2,
                    title: 'Total Revenue',
                    total_amount: 13008,
                    icon: 'mdi-currency-usd',
                    shade: 'pink',
                    currency: true,
                },
                {
                    id: 1,
                    title: 'Total Cars',
                    total_amount: 110,
                    icon: 'mdi-car',
                    shade: 'green',
                    currency: false,
                },
                {
                    id: 1,
                    title: 'Total Customers',
                    total_amount: 200,
                    icon: 'mdi-account-multiple-outline',
                    shade: 'purple',
                    currency: false,
                }
            ],
        }),
    }
</script>