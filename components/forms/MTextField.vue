<template>
  <div id="m-text-field">
    <v-text-field
      v-bind="$attrs"
      solo
      flat
      light
      dense
      :placeholder="placeholder"
      :hide-details="hideDetails"
      v-on="$listeners"
    />
  </div>
</template>
<script>
export default {
  props: {
    placeholder: {
      type: String,
      default: () => 'Placeholder',
    },
    hideDetails: {
      type: Boolean,
      default: () => true,
    },
  },
}
</script>
<style lang="scss">
#m-text-field {
  .v-input {
    font-size: 12px !important;
    border-radius: 12px !important;
  }
  .v-input__slot {
    padding: 0 14px !important;
  }
}
</style>
