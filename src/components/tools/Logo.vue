<template>
  <div class="logo">
    <router-link :to="{name:'dashboard'}">
      <LogoSvg alt="logo" />
      <h1 v-if="showTitle"><TitleSvg alt="title"  style="height:40px;width:140px;margin-top:-4px;"/></h1>
    </router-link>
  </div>
</template>

<script>
import LogoSvg from '@/assets/logo.svg?inline'
import TitleSvg from '@/assets/title.svg?inline'

export default {
  name: 'Logo',
  components: {
    LogoSvg,
    TitleSvg
  },
  props: {
    title: {
      type: String,
      default: '商家工作台',
      required: false
    },
    showTitle: {
      type: Boolean,
      default: true,
      required: false
    }
  }
}
</script>
