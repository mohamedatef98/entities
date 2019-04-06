<template>
    <div>
        <v-layout row justify-center align-center v-if="edit == false" @dblclick="edit = true">
            <p v-if="bold == false">
                {{value}}
            </p>
            <h3 v-else>
                {{value}}
            </h3>
        </v-layout>
        <v-layout row justify-center align-center v-else>
            <v-text-field
                :label="label"

                :value="value"
                @input="$emit('change', $event)"
                
                @blur="edit = false"

                append-icon="cancel"
                @click:append="edit = false"
            ></v-text-field>
        </v-layout>
    </div>
</template>

<script>

//This Component will present a value in a p or h3 tag, if that value is pressed twice, the tag will be replaced with a text-field
export default {
    props: {

        //The Value itself
        value: {
            type: String
        },

        //The place holder
        label: {
            type: String
        },

        //switch between p tag or h3,
        //h3 if set to true
        //defaults to p tag
        bold: {
            type: Boolean,
            default: false
        }
    },
    data(){
        return {
            edit: false
        }
    },
    model: {
        prop: 'value',
        event: 'change'
    }
}
</script>

<style scoped>
    div{
        margin-right: 0.5rem;
    }
</style>
