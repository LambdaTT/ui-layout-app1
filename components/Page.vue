<template>
  <q-page class="flex q-pa-sm text-center">
    <!--Page Header -->
    <q-card>
      <q-card-section :class="`bg-${themeBgColor} text-${themeTextColor}`">
        <!-- Overline -->
        <div v-if="!!$slots.overline" class="text-overline">
          <slot name="overline"></slot>
        </div>

        <!-- Page's Title and Icon -->
        <div class="text-h5 q-my-sm row flex-center" style="gap:10px">
          <q-icon v-if="Icon" :name="Icon" size="sm"></q-icon>
          <span v-if="Title">{{ Title }}</span>
        </div>

        <!-- Caption -->
        <div v-if="!!$slots.caption" class="text-caption q-mt-md">
          <slot name="caption"></slot>
        </div>

      </q-card-section>
    </q-card>

    <q-separator></q-separator>

    <div class="full-width text-left">
      <q-card>
        <!-- Default Content -->
        <slot></slot>

        <!--Secondary Sections-->
        <div v-for="(section, name) in $slots" :key="name">
          <q-card-section v-if="name != 'default' && name.includes('section')">
            <slot :name="name"></slot>
          </q-card-section>
        </div>

        <!--Page Actions -->
        <q-card-actions class="justify-center" v-if="!!$slots.pageactions">
          <slot name="pageactions"></slot>
        </q-card-actions>

      </q-card>
    </div>

  </q-page>
</template>

<script>

export default {
  name: 'ui-layoutapp1-page',

  props: {
    Icon: String,
    Title: String,
  },

  computed: {
    themeBgColor() {
      return process.env.THEME_COLOR;
    },
    themeTextColor() {
      return process.env.THEME_TEXT_COLOR;
    }
  }
}


</script>
<style scoped>
.q-page {
  display: block;
}
</style>
