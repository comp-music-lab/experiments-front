<template lang="pug">
#app
  #nav
    router-link(to='/')
      | {{ $t("about") }}
    router-link(to='/india')
      | {{ $t("india experiment") }}
    router-link(to='/copyright')
      | {{ $t("copyright") }}
    el-select.select(placeholder="🌐 Select Language", v-model="lang", @change="onLanguageChange")
      el-option(label="English", value="en-us")
      // el-option(label="हिंदी (WIP)", value="hi-in")
      el-option(label="日本語", value="ja-jp")
      // el-option(label="简体中文", value="zh-cn")
      // el-option(label="繁體中文", value="zh-tw")
  router-view
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import { Select, Option } from 'element-ui';

@Component({
  name: 'App',
  components: {
    'el-select': Select,
    'el-option': Option,
  },
})
export default class App extends Vue {
  private lang: string = '';

  private onLanguageChange() {
    this.$i18n.locale = this.lang;
    window.localStorage.setItem('language', this.lang);
  }
}
</script>

<style lang="stylus">
body
  font-family 'Avenir', "Helvetica Neue", Helvetica, "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", "微软雅黑", Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  color #2c3e50

#nav
  padding 1rem
  a
    font-weight bold
    font-size 1.8rem
    text-transform uppercase
    text-decoration none
    color #2c3e50
    margin-right 1rem
    &.router-link-exact-active
      color #BD1E1E

.select
  margin 0 auto
  float none
  @media screen and (min-width: 600px)
    float right 

</style>
