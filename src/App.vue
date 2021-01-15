<script>
import ValidateComponent from '@/components/ValidateComponent'
import SomeComponent from '@/components/SomeComponent'

export default {
  name: 'App',
  components: {
    ValidateComponent,
    SomeComponent
  },
  methods: {
    validate(id) {
      this.$refs[`validate${id}`].validate()
    }
  },
}
</script>
<template>
  <div class="app">
    <button @click="validate(1)">Validate 1</button>
    <button @click="validate(2)">Validate 2</button>
    <button @click="validate(3)">Validate 3</button>
    <button @click="validate(4)">Validate 4</button>
    <button @click="validate(5)">Validate 5</button>

    <validate-component
      ref="validate1"
      :id="1"
    >
      <some-component>
        <validate-component
          ref="validate2"
          :id="2"
        />
      </some-component>
      <some-component>
        <validate-component
          ref="validate3"
          :id="3"
        >
            <validate-component
              ref="validate4"
              :id="4"
            />
        </validate-component>
      </some-component>
      <validate-component
        ref="validate5"
        :id="5"
      />
    </validate-component>
  </div>
</template>