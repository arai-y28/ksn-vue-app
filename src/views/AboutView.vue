<template>
  <div class="about">
    <!--h1>This is an about page</h1-->
    <CountUpDown msg="Vue開発画面です"/>
  </div>
</template>
<script>
// @ is an alias to /src
import CountUpDown from '../components/CountUpDown.vue'

export default {
  name: 'AboutView',
  components: {
    CountUpDown
  }
}
</script>