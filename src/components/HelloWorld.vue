<template>
  <div class="hello">
    <div v-for="todo of toasters.edges" :key="todo.id">
      {{ todo.node.title }}
    </div>
    <button @click="test">test</button>
    <p>
      {{ this.toasters }}
    </p>
  </div>
</template>

<script>
import gql from "graphql-tag";

export default {
  name: "HelloWorld",
  data() {
    return {
      toasters: [],
      queryData: null,
      ddata: null,
    };
  },
  methods: {
    test: function () {
      this.queryData = this.toasters.edges;
      // Set var i
      var i;
      // Create for
      for (i = 0; i < this.queryData.length; i++) {
        // add your script
        this.ddata = this.queryData[i].node;
        console.log(this.ddata);
      }
    },
  },
  apollo: {
    toasters: gql`
      query {
        pages(where: { title: "card" }) {
          edges {
            node {
              title
              id
              cardCustom {
                couleur
                sousTitre
                fieldGroupName
                titre
              }
            }
          }
        }
        toasters {
          edges {
            node {
              title
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
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
