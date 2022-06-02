<template>
    <div class="py-5">
        <v-row >
            <v-col
                cols="12"
                xs="12"
                sm="7"
                md="9"
            > 
                <v-card
                    outlined
                    class="rounded-lg" 
                >
                    <v-card-text>
                        <div class="d-flex align-center">
                            <div class="text-h6 font-weight-medium">
                                Rentals
                            </div>
                            <v-spacer></v-spacer>
                            <div class="text-h6 font-weight-medium">
                                {{dateDisplay }}
                            </div>
                        </div>
                        <div class="rental-info">
                            <div v-if="filtered_data.length > 0">
                                <v-card 
                                    class="pt-3 pb-4 rental-card"
                                    v-for="i in filtered_data" :key="i.id"
                                    elevation="0"
                                >
                                    <v-card-text>
                                        <v-row>
                                            <v-col
                                                cols="12"
                                                xs="12"
                                                sm="2"
                                            >
                                                <v-img
                                                    
                                                    max-height="110px"
                                                    :src="i.url"
                                                ></v-img>
                                            </v-col>
                                            <v-col
                                                cols="12"
                                                xs="12"
                                                sm="2"
                                            >
                                                <div class="text-h6 font-weight-medium pb-2">
                                                    {{i.carName}}
                                                </div>
                                                <div class="text-subtitle-1 font-weight-normal pb-2">
                                                    {{i.carModel}}
                                                </div>
                                                <div class="text-subtitle-2 font-weight-light pb-2">
                                                    {{i.customerName}}
                                                </div>
                                            </v-col>
                                            <v-col
                                                cols="12"
                                                xs="12"
                                                sm="4"
                                            >
                                                <div class="text-subtitle-2 font-weight-light pb-2">
                                                    {{i.status}}
                                                </div>
                                                <div>
                                                    <span class="text-h6 font-weight-medium pe-2">
                                                        {{i.time}} 
                                                    </span>
                                                    <span class="text-subtitle-1 font-weight-normal">
                                                        {{dateDisplay}}
                                                    </span>
                                                </div>
                                            </v-col>
                                            <v-col
                                                cols="12"
                                                xs="12"
                                                sm="4"
                                                class="text-right"
                                            >
                                                <div class="text-h6 font-weight-normal pb-3">
                                                    ID {{i.id}}
                                                </div>
                                                <v-btn
                                                    :color="i.type == 'Rented' ? 'yellow lighten-5' : 'indigo lighten-5' "
                                                    elevation="1"
                                                    style="pointer-events: none"
                                                    :class="i.type == 'Rented' ? 'yellow--text lighten-5' : 'indigo--text lighten-5' "
                                                >
                                                    {{i.type}}
                                                </v-btn>
                                            </v-col>
                                        </v-row>
                                    </v-card-text>
                                </v-card>
                            </div>
                            <div v-else>
                                <v-card 
                                    class="pt-3 pb-4 "
                                    elevation="0"
                                >
                                    <v-card-text class="text-subtitle-1 font-weight-medium ">
                                        <div>No Record Found.</div>
                                    </v-card-text>
                                </v-card>
                            </div>
                        </div>
                    </v-card-text>
                </v-card>
           </v-col>
           <v-col
                cols="12"
                xs="12"
                sm="5"
                md="3"
                class="pt-xs-3"
                right
            > 
                <v-card
                    outlined 
                    class="rounded-lg"
                >
                    <v-card-text>
                        <div class="text-h6 font-weight-medium">
                            Calendar
                        </div>
                        <v-date-picker
                            v-model="picker"
                            flat
                            @change="getRentalInfo"
                            max-width="100%"
                        ></v-date-picker>
                    </v-card-text>
                </v-card>
                
           </v-col>
        </v-row>
    </div>
</template>

<script>
    import '../assets/style.css'
    export default {
        data: () => ({
            dateDisplay: '',
            filter_date: '',
            filtered_data: [],
            picker: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
            rentalItems: [
                {
                    i: 1,
                    id: '#4500',
                    status: 'Return',
                    date: '2022-06-01',
                    time: '08:43 PM',
                    type: 'Rented',
                    carName: 'BMW GH2890',
                    carModel: 'HHAD 4576',
                    customerName: 'Mr. Joe Jackkos',
                    url: 'https://images.unsplash.com/photo-1523983388277-336a66bf9bcd?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MXx8Ym13JTIwY2Fyc3xlbnwwfHwwfHw%3D&w=1000&q=80',
                },
                {
                    i: 2,
                    id: '#8930',
                    status: 'Handover',
                    date: '2022-06-02',
                    time: '11:43 AM',
                    type: 'Rented',
                    carName: 'BMW GH2890',
                    carModel: 'HHAD 4576',
                    customerName: 'Mrs. Jiah ihuj',
                    url: 'https://images.unsplash.com/photo-1523983388277-336a66bf9bcd?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MXx8Ym13JTIwY2Fyc3xlbnwwfHwwfHw%3D&w=1000&q=80',
                },
                {
                    i: 3,
                    id: '#4501',
                    status: 'Handover',
                    date: '2022-06-02',
                    time: '06:00 AM',
                    type: 'Reserved',
                    carName: 'BMW GH2890',
                    carModel: 'HHAD 4576',
                    customerName: 'Mrs. Jiah ihuj',
                    url: 'https://images.unsplash.com/photo-1523983388277-336a66bf9bcd?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MXx8Ym13JTIwY2Fyc3xlbnwwfHwwfHw%3D&w=1000&q=80',
                },
                {
                    i: 4,
                    id: '#8930',
                    status: 'Handover',
                    date: '2022-06-03',
                    time: '11:43 AM',
                    type: 'Rented',
                    carName: 'BMW GH2890',
                    carModel: 'HHAD 4576',
                    customerName: 'Mrs. Jiah ihuj',
                    url: 'https://images.unsplash.com/photo-1523983388277-336a66bf9bcd?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MXx8Ym13JTIwY2Fyc3xlbnwwfHwwfHw%3D&w=1000&q=80',
                },
                {
                    i: 5,
                    id: '#4501',
                    status: 'Handover',
                    date: '2022-06-03',
                    time: '06:00 AM',
                    type: 'Reserved',
                    carName: 'BMW GH2890',
                    carModel: 'HHAD 4576',
                    customerName: 'Mrs. Jiah ihuj',
                    url: 'https://images.unsplash.com/photo-1523983388277-336a66bf9bcd?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MXx8Ym13JTIwY2Fyc3xlbnwwfHwwfHw%3D&w=1000&q=80',
                }
            ],
        }),
        methods:{
            getRentalInfo(){
                this.dateDisplay = new Date(this.picker).toDateString().split(' ').slice(1).join(' ');
                this.filter_date = this.picker ; 
                this.filtered_data = (this.rentalItems).filter(x=> x.date == this.filter_date );
                // console.log(this.filtered_data)
            }
        },
        mounted(){
            this.filter_date = this.picker; 
            this.getRentalInfo() ;
        }
    }
</script>