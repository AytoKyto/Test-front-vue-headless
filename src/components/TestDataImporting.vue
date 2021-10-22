<template>
  <div class="hello">
    <div v-for="text of posts.edges" :key="text.id">
      {{ text.node.composant.custom }}
    </div>
    <br />
    <br />
    <br />
    {{ this.alignementCustom }}
    <br />
    <br />
    <p :style="textStyle">
      loredsm ipsudsm dodslor sidst amdset, consectdsetur,lordsem ipsdsum
      dosdlor sit am
    </p>
  </div>
</template>

<script>
import gql from "graphql-tag";

export default {
  name: "TestDataImporting",
  data() {
    return {
      posts: [],
      alignementCustom: null,
    };
  },
  methods: {},
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
  computed: {
    textStyle() {
      return {
        textAlign: this.alignementCustom,
      };
    },
  },
  updated() {
    console.log("creat");
    var i;
    for (i = 0; i < this.posts.edges.length; i++) {
      this.alignementCustom =
        this.posts.edges[i].node.composant.custom[0].alignement;
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
