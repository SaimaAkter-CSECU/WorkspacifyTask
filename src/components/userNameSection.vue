<template>
    <div
        class="py-5"
    >
        <v-row >
           <v-col
                cols="12"
                xs="12"
                sm="8"
                md="9"
            > 
                <div class="font-weight-bold text-xs-h6 text-sm-h5 text-md-h4"> Good Morning, {{name}}</div>
           </v-col>
           <v-col
                cols="12"
                xs="12"
                sm="4"
                md="3"
                class="pt-xs-3 text-right"
            > 
                <v-btn
                    tile
                    color="black"
                    class="white--text pa-6"
                    Large
                >
                <v-icon 
                    left
                    class="font-weight-light pe-3"
                >
                    mdi-calendar
                </v-icon>
                    Add Reservation
                </v-btn>
           </v-col>
        </v-row>
    </div>
</template>

<script>
    export default {
        data: () => ({
            name: 'John Doe', 
        }),
    }
</script>