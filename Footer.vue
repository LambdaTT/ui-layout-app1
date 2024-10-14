<template>
  <q-footer elevated>
    <q-tabs v-model="currentTab" :indicator-color="themeColor" :active-color="themeColor"
      class="bg-white text-grey-8 shadow-2">
      <q-tab v-for="(Tab, idx) in Tabs" :key="idx" :name="Tab.name" :icon="Tab.icon" :label="Tab.label"
        @click="() => { $emit('main-tab-change', currentTab) }" />
    </q-tabs>
  </q-footer>
</template>

<script>
export default {
  name: 'ui-layoutapp1-footer',

  props: {
    Tabs: Array,
    DefaultTab: String
  },

  data() {
    return {
      currentTab: null
    }
  },

  computed: {
    themeColor() {
      return process.env.THEME_COLOR;
    }
  },

  mounted() {
    this.currentTab = this.DefaultTab
    this.$emit('main-tab-change', this.currentTab)
  }
}
</script>

<style scoped>
footer {
  position: fixed !important;
}
</style>
