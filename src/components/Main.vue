<template>
  <v-container>
    <v-tooltip bottom>
      <template v-slot:activator="{ on }">
       <v-btn
          absolute
          dark
          fab
          top
          right
          color="pink"
          v-on="on"
          @click="add_entity"
        >
          <v-icon>add</v-icon>
        </v-btn>
      </template>
      <span>Add new Entity</span>
    </v-tooltip>
    <v-layout row wrap justify-center align-center>
      <v-flex xs3 v-for="(entity, index) in entities" :key="index">
        <entity class="entity" v-model="entities[index]" @deleted="remove_entity(index)"/>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  import Entity from './Entity'

  export default {

    components: {
      Entity
    },

    data: () => ({
      entities: []
    }),

    methods: {

      add_entity(){
        this.entities.push({
            'name': "New Entity",
            'attributes' : []
          });
      },

      remove_entity(index){
        console.log(index);
        this.entities.splice(index, 1);
      }


    }
  }
</script>

<style scoped>
  .entity{
    margin: 1rem;
  }
</style>
