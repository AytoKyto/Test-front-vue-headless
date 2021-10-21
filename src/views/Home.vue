<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld />
    <ContactFrom />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import ContactFrom from '@/components/ContactFrom.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld,
    ContactFrom
  }
}
</script>
