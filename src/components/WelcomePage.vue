<template>
    <span>
        <v-card>
            <v-card-text>
                <p class="text-md-center">Welcome to Slider Puzzle Game</p>
            </v-card-text>
        </v-card>
        <v-container class="grey lighten-5">
            <v-row no-gutters>
                <v-col>
                    <v-card class="pa-2" outlined tile>
                        <BoardGame ref="BoardGame" v-show="playing" @restart="restart" />
                        <IntoPageGridOne @gameStart="start" msg="Welcome to Your Vue.js App" v-show="!playing" />
                    </v-card>
                </v-col>
                <!-- <v-col>
                    <v-card class="pa-2" outlined tile>
                        <IntoPageGridTwo msg="Welcome" />
                    </v-card>
                </v-col> -->
            </v-row>
        </v-container>
    </span>
</template>
  
<script>
import IntoPageGridOne from './IntoPageGridOne.vue'
import BoardGame from './BoardGame.vue'
// import IntoPageGridTwo from './IntoPageGridTwo.vue'

export default {
    name: 'WelcomePage',
    components: {
        IntoPageGridOne,
        BoardGame
        // IntoPageGridTwo
    },

    data() {
        return {
            playing: false
        }
    },
    methods: {
        start(...args) {
            // //console.log("args")
            // //console.log(args)
            //console.log("parent", args);
            this.playing = true
            this.$refs.BoardGame.start(...args)
        },

        restart() {
            this.playing = false
            this.$refs.optionsPane.reset()
        }
    }
}
</script>