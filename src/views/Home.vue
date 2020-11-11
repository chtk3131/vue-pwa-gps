<template>
  <div class="home">
    <GPS />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
import GPS from '@/components/GPS.vue';

@Options({
  components: {
    GPS,
  },
})
export default class Home extends Vue {}
</script>
