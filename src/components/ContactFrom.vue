<template>
  <div class="contact">
      <h3>Contact</h3>
      <iframe id="iframe" name="dummyframe"></iframe>
    <form
    target="dummyframe"
      @submit="checkForm"
      action="https://relaxed-burnell.217-160-68-194.plesk.page/wp-json/contact-form-7/v1/contact-forms/18/feedback"
      method="post"
    >
      <p v-if="errors.length">
    <b>Vous ne pouvez pas envoyer ce messages car</b>
    <ul>
      <p :key="error.id" v-for="error in errors">{{ error }}</p>
    </ul>
  </p>
      <p>
        <label for="textname">Name  </label>
        <input id="textname" v-model="textname" type="text" name="textname" />
      </p>

      <p>
        <input type="submit" value="Submit" />
      </p>
      <p>{{message}}</p>
    </form>
  </div>
</template>

<script>
export default {
  name: "ContactForm",
  data() {
    return {
      textname: null,
      errors: [],
      message: "",
    };
  },
  methods: {
    checkForm: function (e) {
      if (this.textname) {
      this.send = !this.send;
      console.log(this.send)
      this.message = "message envoyer !";
        return true;
      }

      this.errors = [];

      if (!this.textname) {
        this.errors.push("Le nom est obligatoire");
      this.message = "";
      }
    
      e.preventDefault();
    },
  },
};
</script>

<style scoped>
#iframe {
  display: none;
}
</style>
