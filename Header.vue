<template>
  <q-header elevated class="bg-white">
    <q-toolbar class="q-pa-sm text-grey-9">
      <!-- Main logo -->
      <q-toolbar-title>
        <a href="/">
          <img class="main-logo vertical-middle" alt="Logo Principal" :src="MainLogoSrc" />
        </a>
      </q-toolbar-title>

      <div v-for="(section, name) in $slots" :key="name">
        <div v-if="name != 'default'">
          <slot :name="name"></slot>
        </div>
      </div>

      <q-btn v-if="!!ActionsBtnIcon && !ActionsBtnImg" class="q-pa-md" flat round :icon="ActionsBtnIcon" size="md">
        <q-menu>
          <q-list class="q-pa-sm text-grey-8">
            <q-item v-for="(a, i) in Actions" :key="i" v-close-popup clickable :disable="a.disable" @click="a.fn">
              <q-item-section side>
                <q-icon size="sm" :name="a.icon" />
              </q-item-section>
              <q-item-section>{{ a.title }}</q-item-section>
            </q-item>
          </q-list>
        </q-menu>
      </q-btn>

      <q-btn v-else class="q-pa-md" flat round size="md">
        <q-avatar>
          <img :src="ActionsBtnImg" />
        </q-avatar>
        <q-menu>
          <q-list class="q-pa-sm text-grey-8">
            <q-item v-for="(a, i) in Actions" :key="i" v-close-popup clickable :disable="a.disable" @click="a.fn">
              <q-item-section side>
                <q-icon size="sm" :name="a.icon" />
              </q-item-section>
              <q-item-section>{{ a.title }}</q-item-section>
            </q-item>
          </q-list>
        </q-menu>
      </q-btn>
    </q-toolbar>
  </q-header>
</template>

<script>


export default {
  name: 'ui-layoutapp1-header',

  props: {
    MainLogoSrc: String,
    Actions: Array,
    ActionsBtnIcon: String,
    ActionsBtnImg: String
  },
}
</script>

<style scoped>
.main-logo {
  max-width: 155px;
}
</style>
