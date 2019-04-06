<template>
   <v-layout row justify-space-between>
       <v-text-field
            label="Attribute Name"
            :value="attribute"
            @input="$emit('change', $event)"
        ></v-text-field>
        <v-icon @click="$emit('deleted')">cancel</v-icon>
   </v-layout>
</template>

<script>
  export default {
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
  }
</script>

<style scoped>
</style>
