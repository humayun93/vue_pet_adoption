<template>
  <div>
    <h1> {{animal.name}} ({{$route.params.type}}) </h1>
    <p> {{animal.age}} years old</p>
    <p> Breed: {{animal.breed}} </p>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  data () {
    return {
      animal: {}
    }
  },
  computed: {
    ...mapState(['cats', 'dogs'])
  },
  mounted () {
    const animal = this[this.$route.params.type][this.$route.params.id]
    this.animal = animal
  }
}
</script>
