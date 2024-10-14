<template>
  <q-page class="flex q-pa-sm text-center">
    <!--Page Header -->
    <q-card>
      <q-card-section>
        <!-- Overline -->
        <div v-if="!!$slots.overline" class="text-overline">
          <slot name="overline"></slot>
        </div>

        <!-- Page's Title and Icon -->
        <div class="text-h5 q-mt-sm q-mb-xs">
          <q-icon v-if="Icon" :name="Icon" size="sm"></q-icon>
          &nbsp;
          <span v-if="Title">{{ Title }}</span>
        </div>

        <!-- Caption -->
        <div v-if="!!$slots.caption" class="text-caption text-grey">
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
  }
}
</script>
<style scoped>
.q-page {
  display: block;
}
</style>