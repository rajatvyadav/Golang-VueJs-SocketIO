<template>
<div>
  <div v-if="traderLogin" class="center">
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group id="input-group-2" label="Your Name:" label-for="input-2" description="Use admin">
        <b-form-input
          id="input-2"
          v-model="form.name"
          placeholder="Enter name"
          required
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-2" label="Your password:" label-for="input-2" description="Use admin">
        <b-form-input
          id="input-2"
          v-model="form.password"
          placeholder="Enter password"
          required
        ></b-form-input>
      </b-form-group>
      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
  </div>
  <div v-else>
      <operator>
  </div>
  </div>
</template>

<script>
import Operator from './Operator.vue'
  export default {
  components: { Operator },
    data() {
      return {
        form: {
          name: '',
          password: ''
        },
        show: true,
        traderLogin: true
      }
    },
    methods: {
      onSubmit(event) {
        event.preventDefault()
        this.traderLogin = false
        this.$socket.emit("/adminLogedIn", {userName: this.name, role: 'admin'})
      },
      onReset(event) {
        event.preventDefault()
        // Reset our form values
        this.form.password = ''
        this.form.name = ''
        // Trick to reset/clear native browser form validation state
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      }
    }
  }
</script>
<style scoped>
.center{
    margin: 1px 38%;
}
</style>
