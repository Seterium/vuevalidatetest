<script>
export default {
  name: 'ValidateComponent',
  props: {
    id: {
      type: Number,
      default: () => null,
      required: true
    }
  },
  methods: {
    validate() {
      console.log(`Validate method run, component ID: ${this.id}`)

      this.childrenValidate(this.$children)
    },
    childrenValidate(collection) {
      collection.forEach(component => {
        if (component.$options.name === 'ValidateComponent') {
          component.validate()
        } else if (component.$children.length) {
          this.childrenValidate(component.$children)
        }
      })
    }
  },
}
</script>
<template>
  <div class="validate-component">
    <slot />
  </div>
</template>