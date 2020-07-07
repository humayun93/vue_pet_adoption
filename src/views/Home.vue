<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <button class="btn btn-primary" @click="togglePetForm" >Add new button</button>

    <b-form @submit.prevent="onSubmit" v-if="showPetForm">
        <b-form-group
          id="input-group-1"
          label="Name:"
          label-for="name"
          description="Name"
        >
        <b-form-input
          id="name"
          v-model="formData.name"
          type="text"
          required
          placeholder="Name"
        ></b-form-input>
      </b-form-group>

      <b-form-group
          id="input-group-1"
          label="Age:"
          label-for="age"
          description="Age"
        >
        <b-form-input
          id="age"
          v-model="formData.age"
          type="number"
          required
          placeholder="Age"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Species:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="formData.species"
          :options="['cats', 'dogs']"
          required
        ></b-form-select>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
  </div>

</template>

<script>
import { mapActions } from 'vuex'
// @ is an alias to /src
export default {
  name: 'Home',
  data () {
    return {
      showPetForm: false,
      formData: {
        name: '',
        species: '',
        age: 0
      }
    }
  },
  methods: {
    ...mapActions(['addPet']),
    togglePetForm () {
      this.showPetForm = !this.showPetForm
    },
    onSubmit () {
      const { species, age, name } = this.formData
      const payload = {
        species,
        pet: {
          name,
          age
        }
      }
      this.formData = {
        name: '',
        species: '',
        age: 0
      }
      this.addPet(payload)
    }
  }
}
</script>
