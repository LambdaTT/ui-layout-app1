<template>
  <q-dialog :persistent="persistent" v-model="show" @update:model-value="(v) => $emit('update:model-value', v)"
    @hide="HideFn">
    <q-card>
      <q-toolbar :class="`bg-${themeColor} text-white`">
        <q-avatar v-if="Icon">
          <q-icon :name="Icon"></q-icon>
        </q-avatar>

        <q-toolbar-title v-if="Title">{{ Title }}</q-toolbar-title>

        <q-btn flat round dense icon="close" v-close-popup />
      </q-toolbar>

      <!-- Sections -->
      <div v-for="(section, name) in $slots" :key="name">
        <q-card-section v-if="name != 'default' && name.includes('section')" class="q-pa-md">
          <slot :name="name"></slot>
        </q-card-section>
      </div>

      <q-card-actions class="row justify-center q-px-md q-pb-md q-pt-none" v-if="!!Actions && Actions.length > 0">
        <q-btn class="col" label="Cancelar" color="grey-8" icon="close" v-close-popup></q-btn>
        <q-btn class="col" v-for="(a, i) in Actions" :disable="isLoading" :loading="isLoading" :key="i" :label="a.label" :color="a.color" :icon="a.icon"
          @click="a.fn()"></q-btn>
      </q-card-actions>
    </q-card>
  </q-dialog>
</template>

<script>
export default {
  name: 'ui-layoutapp1-modal',

  props: {
    isLoading: Boolean,
    HideFn: Function,
    Icon: String,
    Title: String,
    Actions: Array,
    modelValue: Boolean,
    persistent: Boolean
  },

  data() {
    return {
      show: false
    }
  },

  watch: {
    modelValue(v) {
      this.show = v;
    }
  },

  computed: {
    themeColor() {
      return process.env.THEME_COLOR;
    }
  },
}
</script>