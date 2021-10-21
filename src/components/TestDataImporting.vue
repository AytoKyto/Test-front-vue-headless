<template>
  <div @click="log" class="hello">
    <div v-for="text of posts.edges" :key="text.id">
      {{ text.node.composant.custom }}
    </div>
  </div>
</template>

<script>
import gql from "graphql-tag";

export default {
  name: "TestDataImporting",
  data() {
    return {
      posts: null,
      dataOne: null,
      dataTwo: null,
      mapp: null,
      mapUse: null,
      result: null,
    };
  },
  methods: {
    log: function () {
      //console.log(this.posts);
      this.mapp = this.posts.edges
      // Set var i
      var i;
      // Create for
      for (i = 0; i < this.posts.edges.length; i++) {
        // add your script
        this.dataOne = this.posts.edges[i].node.composant.custom;
        console.log(this.dataOne);
          this.dataTwo = this.dataOne[0].alignement;
          this.result = this.dataOne[0].titre;
          console.log(this.dataTwo);
          console.log(this.result);
        }
    },
  },
  apollo: {
    posts: gql`
      query {
        posts {
          edges {
            node {
              title
              composant {
                custom {
                  ... on Post_Composant_Custom_Titre {
                    alignement
                    titre
                  }
                }
              }
            }
          }
        }
      }
    `,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
