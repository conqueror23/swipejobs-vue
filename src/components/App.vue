<template>
  <div class="app">
    <NavBar/>
    <ContentWraper/>
  </div>
</template>

<script>
import NavBar from '@/components/Layouts/NavBar'
import ContentWraper from '@/components/Layouts/ContentWraper'
export default {
  name:'app',
  components: {
    NavBar,
    ContentWraper
  }
}
</script>

<style>
.app{
}
</style>
