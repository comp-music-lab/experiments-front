<template lang="pug">
.about
  h1
    | Copyright Experiment
  .routes
    a.route(v-for="route in routes", :href="route.src")
      | {{ $t(route.title) }}
</template>
</template>

<script lang='ts'>
import { Component, Vue } from 'vue-property-decorator';

interface RouteDefinition {
  title: string;
  label: string;
  src: string;
  active: boolean;
}

@Component({
  name: 'Home',
})
export default class Copyright extends Vue {
  private routes: RouteDefinition[] = [
    {
      title: 'copyrightWorkshop',
      src: '/experiments/copyright/workshop',
      label: 'Copyright Workshop',
      active: false,
    },
    {
      title: 'copyrightFull',
      src: '/experiments/copyright/full',
      label: 'Copyright Full',
      active: false,
    },
    {
      title: 'copyrightNewWorkshop',
      src: '/experiments/copyright/new_workshop',
      label: 'Copyright New Workshop',
      active: false,
    },
  ];

  private setActive(route: number) {
    this.routes[route].active = !this.routes[route].active;
  }
}
</script>

<style lang="stylus" scoped>
.about
    text-align center
  h1
    font-size 3rem
    margin-bottom 1rem
  .routes
    text-align center
    display flex
    flex-direciton row
    min-width 400px
    max-width 800px
    margin 0 auto
    flex-wrap wrap
    a.route
        display block
        margin 40px 0
        text-transform uppercase
        width 40%
        font-size 24px
        color white
        text-decoration none
        padding 3rem 1rem
        background-color #42b983
        border-radius 5px
        border 1px solid #42b983
        height 10rem
        margin 5px
    a.route:hover
        background-color white
        color #42b983
</style>
