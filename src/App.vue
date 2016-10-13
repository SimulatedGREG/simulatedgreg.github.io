<template>
  <div id="app" class="container">
    <heading></heading>
    <resume></resume>
  </div>
</template>

<script>
import Heading from 'components/Heading'
import Resume from 'components/Resume'

export default {
  components: {
    Heading,
    Resume
  }
}
</script>

<style lang="scss">
  #app {
    margin: 60px auto;
    max-width: 650px !important;
    padding: 20px;
  }
</style>
