<template>
  <DefaultField
    :field="field"
    :errors="errors"
    :show-help-text="showHelpText"
    :full-width-content="fullWidthContent"
  >
    <template #field>
      <input
        :id="field.attribute"
        type="text"
        class="w-full form-control form-input form-input-bordered"
        :class="errorClasses"
        :placeholder="field.name"
        :max="field.maxLength"
        v-model="value"
      />

        <p class="my-2 text-light" :class="{ warning: (field.maxLength - value.length) < 0,  good: (field.maxLength - value.length) > 0 }">
            ostáva {{ (field.maxLength - value.length)}}  znakov
        </p>

    </template>
  </DefaultField>
</template>

<style scoped>
.warning{
    color:red
}
.good{
    color:green
}
</style>

<script>
import { FormField, HandlesValidationErrors } from 'laravel-nova'

export default {
  mixins: [FormField, HandlesValidationErrors],

  props: ['resourceName', 'resourceId', 'field'],

    data(){
      return {
          //maxLenght: 50
      }
    },

  methods: {
    /*
     * Set the initial, internal value for the field.
     */
    setInitialValue() {
      this.value = this.field.value || ''
    },

    /**
     * Fill the given FormData object with the field's internal value.
     */
    fill(formData) {
      formData.append(this.field.attribute, this.value || '')
    },
  },
}
</script>
