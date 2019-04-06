<template>
   <v-layout row justify-space-between>
        <label-and-input label="Attribute Name" v-model="computed_attribute"/>
        <v-icon @click="$emit('deleted')">cancel</v-icon>
   </v-layout>
</template>

<script>
  import LabelAndInput from './LabelAndInput'
  
  export default {

    components: {
        LabelAndInput
    },

    props: {
        attribute: {
            /* 
                The String for attribute name
            */
            type: String
        }
    },

    model: {
        prop: 'attribute',
        event: 'change'
    },

    computed: {

        //Work around for custom v-model inside custom v-model
        computed_attribute: {
            get(){
                return this.attribute
            },
            set(v){
                this.$emit('change', v)
            }
        }
    }

  }
</script>

<style scoped>
</style>
