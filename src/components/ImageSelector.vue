<template>
    <!-- <v-select :items="items" label="Standard">
        <template v-slot:selection="{ item, index }">
            <img :src="item.image">{{ item.name }}
        </template>
        <template v-slot:item="{ item }">
            <img :src="item.image">{{ item.name }}
        </template>
    </v-select> -->
    <!-- <p>image selected</p> -->
    <label for="file">
        Select an image
        <input type="file" id="file" accept="image/gif, image/jpeg, image/png" @change="fileChanged">
        <div class="preview">
            <img v-if="image" :src="image" />
        </div>
        <p> Board size:</p>
        <v-container class="grey lighten-5">
            <v-row no-gutters>
                <v-col>
                    <v-card class="pa-2" outlined tile>
                        <v-text-field label="Enter Horizontal" type="number" min="2" max="10"
                            v-model.number="size.horizontal" />
                    </v-card>
                </v-col>
                <v-col>
                    <v-card class="pa-2" outlined tile>
                        <v-text-field label="Enter Vertical" type="number" min="2" max="10"
                            v-model.number="size.vertical" />
                    </v-card>
                </v-col>
            </v-row>
        </v-container>
        <button class="btn-start" v-if="image" v-on:click="start">Start</button>
    </label>
</template>

<script>
export default {
    data() {
        return {
            image: null,
            size: {
                horizontal: 3,
                vertical: 3
            }
        }
    },
    methods: {
        fileChanged(e) {
            //console.log(this.size)

            // //console.log(e.target.files[0]);
            // const file = e.target.files[0];
            // this.image = URL.createObjectURL(file);
            if (!e.target.files.length) {
                this.image = null
                return
            } else {
                // //console.log(e.target.files);
                const file = e.target.files[0];
                this.image = URL.createObjectURL(file);
            }
        },
        start() {
            // //console.log("suhdjgdhg");
            //console.log("child 2", this.image, this.size);
            this.$emit('gameStartTwo', {
                image: this.image,
                size: this.size
            })
        },
    }
}
</script>
<style >
.preview {
    display: flex;
    justify-content: center;
    align-items: center;
}

.preview img {
    max-width: 600px;
    max-height: 500px;
}

.btn-start {
    padding: 6px 12px;
    background: #1ca76a;
    color: #fff;
    border-radius: 3px;
    border: 0;
    font-size: 14px;
    cursor: pointer;
    margin-top: 10px;
}
</style>