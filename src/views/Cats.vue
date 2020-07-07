<template>
  <div>
    <PetTable species='cats' :pets="cats" />
  </div>
</template>

<script>
import { mapState } from 'vuex'
import PetTable from '@/components/PetTable.vue'

export default {
  computed: {
    ...mapState(['cats'])
  },
  components: {
    PetTable
  }
}
</script>
