<template>
  <div>{{ hello }}</div>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator';
import { Context } from '@nuxt/types';

@Component({
  name: 'Index'
})
export default class Index extends Vue {
  private hello!: string;

  async asyncData({ $axios }: Context) {
    let hello;
    try {
      hello = await $axios.$get('/');
    } catch (e) {
      console.error(e);
    }

    return {
      hello
    };
  }
}
</script>
