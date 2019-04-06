<template>
   <v-card>
        <v-card-title primary-title>
            <v-layout row justify-space-between>
                <label-and-input label="Entity Name" v-model="entity.name" bold/>
                <v-icon @click="$emit('deleted')">cancel</v-icon>
            </v-layout>
        </v-card-title>
        <v-card-text class="text-center">
            <attribute v-model="entity.attributes[index]" v-for="(attribute, index) in entity.attributes" :key="index" @deleted="remove_attribute(index)"/>
            <v-btn @click="add_attribute"><v-icon>add</v-icon></v-btn>
        </v-card-text>
    </v-card>
</template>

<script>
  import Attribute from './Attribute'
  import LabelAndInput from './LabelAndInput'
  export default {
    components: {
        Attribute,
        LabelAndInput
    },
    props: {
        entity: {
            /* 
                The Object Representing the Entity
                {
                    name: "entity name",
                    attributes: [
                        "array of attributes"
                    ]
                } 
            */
            type: Object
        }
    },
    model: {
        prop: 'entity',
        event: 'change'
    },
    methods: {
        add_attribute(){
            let new_attributes = this.entity.attributes.concat("New Attribute");
            let new_entity = {...this.entity, attributes: new_attributes};
            this.$emit('change', new_entity);
        },
        remove_attribute(index){
            let new_attributes = this.entity.attributes.slice();
            new_attributes.splice(index, 1);
            let new_entity = {...this.entity, attributes: new_attributes};
            this.$emit('change', new_entity);
        }
    }
  }
</script>

<style scoped>
    .text-center{
        text-align: center;
    }
</style>
