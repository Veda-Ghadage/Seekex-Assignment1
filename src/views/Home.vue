<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <AddPerson/>
  </div>
</template>

<script>
// @ is an alias to /src
import AddPerson from '@/components/addperson.vue'

export default {
  name: 'Home',
  components: {
    AddPerson
  }
}
</script>
