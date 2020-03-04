<template>

        <v-app>
            <vue-headful title="Horoskapp"/>
        <v-container class="pa-0 ma-0" max-width="100vw">
            <v-card     class="mx-auto"
                        max-width="100vw"
                        height="100vh">
                <v-img class="white--text align-end"
                       height="200px"
                       src="https://cdn.vuetifyjs.com/images/cards/docks.jpg">

                </v-img>
                <v-card-title>{{ sign }}</v-card-title>
                <v-card-text>Lucky number: {{ data.lucky_number }}</v-card-text>
                <v-card-text>Lucky color: {{ data.color }}</v-card-text>
                <v-card-text>{{ data.description }}</v-card-text>

                <v-card-text>
                    <span class="subheading">Select your sign</span>

                    <v-chip-group
                            active-class="deep-purple--text text--accent-4"
                            mandatory

                    >
                        <v-chip v-for="(sign, i) in signs" :key="i"
                        @click="getSign(sign)"
                        >{{ sign }} </v-chip>
                    </v-chip-group>
                </v-card-text>

            </v-card>





<!--        <ul id="aztro">
            <li>Current Date: {{data.current_date}}</li>
            <li>Compatibility: {{data.compatibility}}</li>
            <li>Lucky Number: {{data.lucky_number}}</li>
            <li>Lucky Time: {{data.lucky_time}}</li>
            <li>Color: {{data.color}}</li>
            <li>Date Range: {{data.date_range}}</li>
            <li>Mood: {{data.mood}}</li>
            <li>Description: {{data.description}}</li>
        </ul>-->
        </v-container>
        </v-app>
</template>

<script>
    import axios from 'axios';
    //const API_URL = 'https://aztro.sameerkumar.website/?sign=aries' + this.sign + '&day=today';
    export default {
        name: "Test",
        data: () => ({
                data: {},
                axiosData: {},
                signs: ['Aquarius', 'Pisces', 'Aries', 'Taurus', 'Gemini', 'Cancer', 'Leo', 'Virgo', 'Libra', 'Scorpio',
                'Sagittarius', 'Capricorn'
                ],
            sign: '',
            cancer: 'cancer'
        }),
        methods: {
            getSign: function (value) {
                //const buttonValue = e.target.value;
                console.log(value)
                var API_URL = 'https://aztro.sameerkumar.website/?sign=' + value + '&day=today';
                axios.post(API_URL).then((response) => {
                    this.data = response.data
                })
                this.sign = value
            },

/*            gotSign: function (value) {
                if(localStorage.value){

                }*/

    },
        created() {
/*            axios.post(API_URL).then((response) => {
                this.data = response.data
            })*/
            },
        mounted() {

        }
    }

</script>

<style scoped>
 .v-btn {
     display: inline-block;
 }
</style>