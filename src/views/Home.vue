<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <TestDataImporting />
    <ContactFrom />
  </div>
</template>

<script>
// @ is an alias to /src
import TestDataImporting from '@/components/TestDataImporting.vue'
import ContactFrom from '@/components/ContactFrom.vue'

export default {
  name: 'Home',
  components: {
    TestDataImporting,
    ContactFrom
  }
}
</script>
